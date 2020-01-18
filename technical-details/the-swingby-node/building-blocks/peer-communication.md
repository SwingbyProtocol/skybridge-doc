# Peer communication

Each "round" of the protocol lasts for 10 minutes. There are 6 of these per hour. Each "round" has a unique identifier _round\_num: floor\(epoch\_time\_secs / \(60 \* 10\)\)._

* **Peer Discovery \(mins. 1-2, \*6 each hour\)** - send ping messages every 5s, build peer list, check stakes, ensure bad nodes are blocked. Ping message: peer ok, state, stake tx, proof of TSS share. Correct ping trigger stake check \(balance must have been staked for at least 72 hours and never moved\) och each peer, each adds peer to its peer list.
* **Blackout \(mins. 2-10, \*6 each hour\)** - no ping messages sent, but still acknowledged until one of the states below. Only sync K/V for future rounds. Clears the network chatter to following may take place:
* **Sign List Building \(mins. 2-4, \*6 each hour\)** - All peers look at **incoming** address for **new** tokens, put them in list, build tx. Incoming tokens must be in confirmed transactions and exist in unconfirmed K/V. Tx contains: tx inputs and outputs, reward distribution, refunds \(multi-send\). Each peer broadcasts a _sign proposal_ \(max. one per peer\): _&lt;sha512\_256\(tx\_sign\_doc\), sha512\_256\(peer\_id + tx\_sign\_doc\), tss\_proof&gt;_ Each peer: _m\[0\] == own\[0\], m\[1\] == sha512\_256\(peer\_id + our\_sign\_doc\), ok\(tss\_proof\)_ Peers that pass are added to own _signing set_, which each peer will broadcast. Peers that broadcast _signing sets_ that do not meet the threshold are ignored by other peers.
* **Sign List Voting \(mins. 4-5, \*6 each hour\) \(1\)** - The minimal subset of _signing sets_ shared across at least _t_ peers is selected by each peer \(all must be visible by each other\). Subsets are selected repeatedly until one that meets the full threshold is found. This solves an issue whereby two nodes each broadcasting a _signing list_ that is _t_ in size but contain different peers. Of the list, peers are ordered by seniority and peers with any non-unique _tss\_proofs_ are pruned from bottom-up to form the _threshold set_. Each peer in this list broadcasts a checksum of its _threshold set_ to prepare for signing. If any of these do not match up, outliers are blocked and we must wait until the next round; this one aborts.
* **TSS TX Signing** __**\(mins. 6-10, \*6 each hour\)** - All peers pick the agreed upon unsigned tx and start signing, then the signed tx is sent. Any peers that send bad data or cause a timeout are temporarily blocked. 
* **No New Requests \(mins. 9-10, \*6 each hour\)** - Peers do not accept requests for the next round at this time as it will start soon. The peers list is **wiped** at this point as it will be rebuilt when next round starts.

\(1\): Each peer selects a candidate tx which contains the most valid transfers \(exact match or closest intersection\) with correct reward distribution output in view. Must contain at least one transfer or round is skipped. TX includes participant peer table checksum, also verified.

**Peer blocking**

There are two cases to protect the network against:

* A peer is suddenly not responding due to network issues or downtime.
* A peer is being actively malicious \(sending bad data to the network or targeted peers\)

Since each peer is considered to have an equal voice, we follow a similar model to Bitcoin to _keep it simple_. Each peer maintains a "block list" of peers that it has blocked and the time that an entry exist in this list is configurable by each peer \(by default, 72 hours\).

A peer takes a risk by blocking another peer. Since the _sign set_ becomes smaller, it is selected to perform more work \(which consumes more power\) due to the following algorithm.

