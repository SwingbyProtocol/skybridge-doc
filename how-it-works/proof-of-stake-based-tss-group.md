---
description: >-
  Proof of Stake and node groups are at the core of the Swingby Skybridge
  protocol.
---

# Proof-of-Stake node groups

![](https://docs.swingby.network/assets/TSS.png)

The Swingby Network is a permissionless \(i.e, anyone can join by downloading and running the Swingby node software\), peer-to-peer \(i.e, all nodes are equal and there is no leader\) network of nodes who run the Swingby node software to communicate with one another.

The network exists to create and operate **decentralized custodians**. 

TSS groups form on the network that runs two main processes. 

1.  **The keygen process** — It is the collaborative creation of a public key, from which custodial cryptocurrency addresses on both blockchains are derived. This is an initial set-up phase and is done once per “bridge” between two blockchains. 
2. **The transaction signing process** — It is the collaborative signing of cryptocurrency transactions for making payments from those custodial addresses. 

Both processes are implemented using TSS protocols. TSS groups can reform as nodes leave and join the network. This is known as **dynamic re-grouping**.

### **Staking eligibility**

Each Swingby node operator needs to own and stake SWINGBY tokens for their metanodes to be considered eligible to:

1. Participate in the creation of custodial addresses
2. Sign transactions

The staking of SWINGBY tokens itself is done on the Binance Chain where the SWINGBY token exists. Once it is done, the staking is used on the Swingby network as follows.

Each node’s eligibility is signaled by broadcasting a signed message over the Swingby Network that includes a transaction hash from Binance Chain \(also known as the **“Ping” message**\). 

The transaction hash comes from a transaction on Binance Chain that stakes **at least the minimum amount of SWINGBY** \(50,000+ SWINGBY\) for at least the minimum amount of time \(72 hours\).  

In addition, the broadcasted message should include **a signature of the staking address** on Binance Chain as proof that the Swingby node operator also controls the staking address on Binance Chain.

### **Dynamic re-grouping**

We expect some amount of network churn in the Swingby network. If many peers leave, leaving fewer than _t_ peers left to sign transactions, the TSS group has effectively lost control over the custodial wallets. This is a scenario that we want to avoid.

**Dynamic re-grouping** allows for parties to enter and leave the TSS group, without affecting the group’s ability to sign transactions.

For example, in a group of 100 nodes with threshold 60 \(_n = 100, t = 60_\), up to 40 parties can leave the group. In first instance, nodes that leave, go offline, or send malicious data, shall be replaced by new nodes in queue to uphold _n = 100_. The remaining parties, so long as there are the threshold number of them, can re-create a new group. This may be necessary if there are insufficient nodes in queue and active nodes are close to _t_ during a longer time period, in effect risking to impact availability.

Say that the secret key _x_ is currently shared by a set of players _P\_1,…,P\_n_ with a threshold of _t._ This group can transfer ownership to a new set of players _P\_1,…,P\_n_ with a new threshold of _t_.

This allows the network to rotate in new nodes as network churn happens, without loss of control over the custodial wallets. However, old nodes still possess a secret share, which could potentially be exploitable if network nodes fluctuates a lot. This needs to be mitigated by running **keygen** from time to time.

