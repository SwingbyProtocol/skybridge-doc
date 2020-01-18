# Peer communication

Each "round" of the protocol lasts for 10 minutes. There are 6 of these per hour. Each "round" has a unique identifier _round\_num: floor\(epoch\_time\_secs / \(60 \* 10\)\)._

* **Continuous Pings** - send ping messages every 3s, build peer list, check stakes, ensure bad nodes are blocked. Ping message: peer ok, state, stake tx, proof of TSS share. Correct ping trigger stake check \(balance must have been staked for at least 72 hours and never moved\) och each peer, each adds peer to its peer list. 
* **Continuous Signing** - All peers look at **incoming** address for **new** tokens, put them in list, build tx. Incoming tokens must be in confirmed transactions and exist in unconfirmed K/V. Tx contains: tx inputs and outputs, reward distribution, refunds \(multi-send\). Each peer broadcasts a _sign proposal_ \(max. one per peer\): _&lt;sha512\_256\(tx\_sign\_doc\), sha512\_256\(peer\_id + tx\_sign\_doc\), tss\_proof&gt;_ Each peer: _m\[0\] == own\[0\], m\[1\] == sha512\_256\(peer\_id + our\_sign\_doc\), ok\(tss\_proof\)_ Peers that pass are added to own _signing set_, which each peer will broadcast. Peers that broadcast _signing sets_ that do not meet the threshold are ignored by other peers.  The minimal subset of _signing sets_ shared across at least _t_ peers is selected by each peer \(all must be visible by each other\). Subsets are selected repeatedly until one that meets the full threshold is found \(\*\). This solves an issue whereby two nodes each broadcasting a _signing list_ that is _t_ in size but contain different peers. Of this list, peers are ordered by seniority and peers with any non-unique _tss\_proofs_ are pruned from bottom-up to form the _threshold set_. Each peer in this list broadcasts a checksum of its _threshold set_ to prepare for signing. If any of these do not match up, outliers are blocked and we must wait until the next round; this one aborts.   To prevent double signs, peers will enter Cooldown state if they see &gt;= t+1 peers in the signing state already.  Entering the signing state is aligned to 1 minute intervals so that peer lists can be regularly cleared ****
* **Cooldown -** Peers do not participate in signing until the next round epoch once they finish signing and the transaction\(s\) are broadcasted. 
* **Keygen** \(Replaces “Signing” when in Keygen mode \(time &lt; keygen\_until\) ****- Each peer has the same “keygen until” time set in config. Keygen runs repeatedly aligned to 5 minute intervals until this time is reached. The in/out addresses will change until a certain block when it becomes “locked in” and permanent.The mainnet network needs to spend some time repeatedly generating the TSS shares for about 1 week to prove that no individuals know the full private key. ****
* **Regroup** - The TSS algorithm can support reassigning shares among peers to prune out peers that have gone offline or are bad. This will happen every night at 00:00 UTC to bring in new peers and maintain the peer pool. Peers are sorted by seniority in descending order. If anyone misbehaves during this process, the keygen attempt is skipped and each node records this event and the culprits that caused it. If this happens repeatedly, a software update must be issued to address the problem. Meanwhile, the protocol can continue using the old shares.  **Important**: We must not allow peers to block each other from this process. This can be dangerous \(a cartel can enter the network and attempt a takeover\).

\(\*\): Each peer selects a candidate tx which contains the most valid transfers \(exact match or closest intersection\) with correct reward distribution output in view. Must contain at least one transfer or round is skipped. TX includes participant peer table checksum, also verified.  


**Peer blocking**

There are two cases to protect the network against:

* A peer is suddenly not responding due to network issues or downtime.
* A peer is being actively malicious \(sending bad data to the network or targeted peers\)

Since each peer is considered to have an equal voice, we follow a similar model to Bitcoin to _keep it simple_. Each peer maintains a "block list" of peers that it has blocked and the time that an entry exist in this list is configurable by each peer \(by default, 72 hours\).

A peer takes a risk by blocking another peer. Since the _sign set_ becomes smaller, it is selected to perform more work \(which consumes more power\) due to the following algorithm.

For example, with a threshold of 2, when a single peer \(3\) decides to block a peer:

1. Peer 1 - 10 other peers advertised in its sign set
2. Peer 2 - 10 other peers advertised in its sign set
3. Peer 3 - 9 other peers advertised in its sign set

In an alternate example, where more nodes are being individually blocked by peers:

1. Peer 1 - 9 other peers advertised in its sign set
2. Peer 2 - 5 other peers advertised in its sign set
3. Peer 3 - 8 other peers advertised in its sign set

The highlight shows which peers are included in the threshold list for the signing round.

The minimal subset of shared peers in all sign sets meeting the threshold is chosen deterministically by each peer. If a peer advertises a sign set that does not meet the threshold, it is ignored.

If this gets to a point that we are unable to meet the threshold, we must wait until a **Regroup** happens or force it through a governance feature.  


