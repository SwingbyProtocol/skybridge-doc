# Leaderless consensus

### **Parameter consensus**

Nodes need to agree on the TSS parameters they wish to use when creating the addresses.  The key parameters from the TSS protocol are:

* n - the total number of parties in the group who is able to partially sign a transaction, and
* t - the threshold \(minimum\) number of parties who need to collaboratively sign the transaction.

Nodes would agree t and n out of band, then broadcast their intention to use them. Nodes will only attempt form groups with other nodes that use the same parameters.

In our first implementation we will use n = 100 and t = 60.  That is, a group will be created where 100 parties will be needed to create the TSS public key, and where 60 of those 100  parties will need to come together to sign transactions.

### Transaction Signing

When do transactions need to be signed?  Here are two scenarios:

* Some 3rd party wants BTC.S \(BinanceChain\).  He uses the Swingby website and enters the amount of BTC.S \(BinanceChain\) he wants, and his address on Binance Chain where he wants to receive it.  The website tells him how much BTC to send from his Bitcoin address to the TSS Group’s custodial BTC address. This requires the TSS Group to create BTC.S \(BinanceChain\) in its custodial Binance Chain address and send it to the 3rd party’s Binance Chain address.
* Some 3rd party wants to redeem his BTC.S \(BinanceChain\) for real BTC on Bitcoin.  He sends BTC.S \(BinanceChain\) to the TSS Group’s custodial Binance Chain address. The TSS Group must send BTC from their custodial Bitcoin address to the 3rd party’s bitcoin address.

Each of the TSS nodes monitors the two custodial addresses on the two blockchains they are building a bridge between.  In our first implementation, this is Bitcoin and Binance Chain.

### **Peer blocking**

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

If this gets to a point that we are unable to meet the threshold, we must wait until a **Regroup** \(see "Peer communication"\) ****happens or force it through a governance feature.

