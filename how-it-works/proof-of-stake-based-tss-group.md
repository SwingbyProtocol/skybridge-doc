---
description: A core protocol construct that powers Swingby Skybridge
---

# Proof-of-Stake node groups

![](https://docs.swingby.network/assets/TSS.png)

The Swingby Network is a permissionless \(ie, anyone can join by downloading and running the Swingby node software\), peer-to-peer \(ie, all nodes are equal and there is no leader\) network of nodes who run the Swingby node software to communicate with one another.

The network exists to create and operate decentralised custodians. TSS groups form on the network, which runs two main processes.  First, the keygen process which is the collaborative creation of a public key, from which custodial cryptocurrency addresses on both blockchains are derived.  This is an initial set-up phase and is done once per “bridge” between two blockchains. Second, the transaction signing process which is the collaborative signing of cryptocurrency transactions for making payments from those custodial addresses.  Both processes are implemented using TSS protocols. TSS groups can reform as nodes leave and join the network. This is known as dynamic re-grouping.

### **Staking eligibility**

Each Swingby Node operator needs to own and stake SWINGBY tokens for their Swingby Node to be considered eligible to:

1. Participate in the creation of custodial addresses
2. Sign transactions

The staking of SWINGBY tokens itself is done on the Binance chain, where SWINGBY exists.  The staking is then announced on the Swingby network as follows.

Each node’s eligibility is signalled by broadcasting a signed message over the Swingby Network which includes a transaction hash from Binance Chain \(this is known as the “Ping” message\).  The transaction hash is that of a transaction on Binance Chain that stakes at least the minimum amount of SWINGBY for at least the minimum amount of time \(72 hours in our first implementation\).  The broadcasted message should include a signature of the staking address on Binance Chain as proof that the Swingby node operator also controls the staking address on Binance Chain.

### **Dynamic re-grouping**

We expect some amount of network churn in the Swingby network.  If many peers leave, leaving fewer than t peers left to sign transactions, the TSS group has effectively lost control over the custodial wallets. This is a scenario that we want to avoid.

Dynamic regrouping allows for parties to enter and leave the TSS group, without affecting the group’s ability to sign transactions.

For example, in a group of 100 nodes with threshold 60 \(n = 100, t = 60\), up to 40 parties can leave the group. In first instance, nodes that leave, go offline, or send malicious data, shall be replaced by new nodes in queue to uphold n = 100. The remaining parties, so long as there are the threshold number of them, can re-create a new group. This may be necessary if there are insufficient nodes in queue and active nodes are close to t during a longer time period, in effect risking to impact availability.

Say that the secret key x is currently shared by a set of players P\_1,…,P\_n with a threshold of t. This group can transfer ownership to a new set of players P\_1,…,P\_n with a new threshold of t.

This allows the network to rotate in new nodes as network churn happens, without loss of control over the custodial wallets. Old nodes do however still possess a secret share which could potentially be exploitable if network nodes fluctuates a lot. This needs to be mitigated by running keygen from time to time.  
  
  


