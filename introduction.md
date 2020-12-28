---
description: Find out the reasons why we decided to build Swingby Skybridge.
---

# Motivations

The current blockchain ecosystem has evolved rapidly since Bitcoin's creation in 2009. Unfortunately, it still faces two major issues: **scalability and cross-chain interoperability**. Scalability ties to the number of transactions per second that any particular blockchain can handle without any performance issue. On the other hand, interoperability refers to the secure movement of assets from one blockchain to another and how networks communicate with each other.

Swingby offers a **unique proposition for blockchain interoperability,** which also offers significant benefits in scalability in the future.

The Swingby protocol works as a **custodian with decentralized control**: it consists of a set of cryptocurrency addresses where a subset of a large distributed number of parties are needed to create a valid signature.

Swingby's main product is a bridging solution named **Skybridge** that offers users a simple way to move their bitcoins to other blockchains \(and back and forth\) without any central trust intermediary. 

### Bitcoin on all the chains!

There has been an increase in applications that use public blockchains and smart contract platforms in recent years. However, many of these blockchains face a fundamental liquidity problem: there are not enough valuable assets running on their networks. Even with compelling applications \(dApps\) or high scalability, an application or blockchain will not work well without liquidity. 

Where are the value & liquidity today? **One word: Bitcoin**. Bitcoin has the most users, the greatest total asset value, and one of the world's most liquid assets. Making bitcoins available and transferable to other blockchains can ignite activity on the other blockchains without trusting a specific intermediary.

With “BTC tokens” on blockchains, many advantages are unlocked for both bitcoin holders and these blockchains:

* Bitcoin users can use dApps, DEXs, and other services on other blockchains without converting their BTCs onto the native tokens of the other blockchains.
* Bitcoin users can take advantage of the other chains' innovative characteristics, such as **settlement speed, lower transaction fees, and anonymity,** whilst remaining invested in the underlying BTC.
* Bitcoin's scalability can be improved by offloading some BTC transactions to other blockchains.
* Users of other chains can benefit from a new wave of liquidity and users from the Bitcoin ecosystem.
* Decentralized exchanges running on blockchains like Ethereum \(e.g., Uniswap, SushiSwap, Balancer, Curve\) can allow trading of BTC tokens, increasing both the liquidity and utility of BTC as an asset class.

Skybridge offers a **non-custodial cross-chain bridge for BTCs** \(on the Bitcoin blockchain\) with pegged tokens on Ethereum \(e.g., WBTC\) but its scope will be increased in the future to include primary issuances on additional blockchains.

### What is a cross-chain bridge?

A cross-chain bridge is a concept used to allow tokens to be swapped from their native blockchain to a token on another blockchain. This allows more flexible usage of tokens such as using bitcoins on programmable networks or swap native assets into wrapped utility tokens, offering benefits like a reduced technical complexity with exchange listings or new use cases outside of their respective networks like lending. ‌

There are many technical possibilities to implement such a bridge, ranging from a completely centralized offering \(like Binance Bridge\) to somewhat decentralized solutions. ‌

Swingby Skybridge aims to **build fast, decentralized, and user-friendly swaps** for ECDSA-based blockchains \(e.g., Bitcoin, Ethereum, Binance Chain, EOS, Tron, TomoChain, VeChain\) by using Threshold Signature Scheme \(TSS\).

{% hint style="danger" %}
Users should consider the custodial aspect of centralized bridge implementations. A compromised bridge may potentially "lock" the tokens on the non-native chain, such as not allowing users to swap back to the native chain. Swingby Skybridge strives to be as _decentralized_ as possible, involving the risk being spread across all nodes running the financially committed network by posting a bond.
{% endhint %}

### **What is the problem with centralized custodians?**

Businesses that hold assets on behalf of other parties can be described as custodians. Custodians store their clients’ assets in addresses that they \(the custodians\) control by knowing the linked private key\(s\) to those addresses.

In the cryptocurrency ecosystem, trusted custodians are business intermediaries who control assets on one chain and issue new “depository receipts” for those coins on another network. These custodians function as escrow agents but also act as administrators. However, there are centralization challenges inherent in both of these solutions: relay mechanisms rely on trusted server operators' block headers. Wherever trusted entities exist, they can fail, compromised either by external or internal malicious actors. **Centralized custodians need to be trusted**.

Yet, these custodians bear the risks of private key loss or theft, which in both cases lead to loss of control of their clients’ funds. Today, custodians typically store the majority of their clients’ assets in multi-signature addresses, and they store the controlling private keys offline. Although this is more secure than having private keys stored on internet-connected devices, the trade-off is inconvenient and creates operational complexities for parties acting as custodians.

### **The alternative: Swingby as a decentralized custodian**

The industry has long needed a solution to the apparent trade-off between security and convenience.

Swingby Skybridge uses **technology based on world-class research to create** the first threshold ECDSA/EdDSA signature scheme protocol that supports multiparty signatures with efficient and dealer-less key generation.

[Using the ideas outlined in this paper,](https://eprint.iacr.org/2019/114.pdf) it has become possible to construct ECDSA/EdDSA addresses \(used in Bitcoin, Ethereum, and most other blockchains\) using an efficient dealer-less key generation with an arbitrary number of parties where some predetermined threshold number of whom jointly have the power to create a valid signature.

{% hint style="danger" %}
Note that this is not a multi-signature address as **only one signature is created** at the end of the multiparty signing process.
{% endhint %}

Additionally, the private key shares held by each party are created without having to rely on a trusted dealer to create and distribute the key shares \(a dealer would be a single point of failure for the system\).

This forms the basis of a modern decentralized custodian solution. 

Welcome to Swingby and Skybridge.

