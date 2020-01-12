# Introduction

The current blockchain ecosystem has evolved rapidly since Bitcoin's creation in 2009, but it still faces two major issues: **scalability and cross-chain interoperability**. By scalability we mean the number of transactions per second that any particular blockchain network can handle before degrading in performance, and by interoperability we mean the secure movement of assets from one blockchain onto another. We have been mainly researching interoperability. 

Trusted custodians are specific trusted business intermediaries who control coins on one chain and issue new “depository receipts” for those coins on another chain.The custodian functions as an escrow agent and acts as an administrator. But there are centralization challenges inherent in both of these solutions: Relay mechanisms rely on block headers created by trusted server operators. Custodians need to be trusted. Wherever trusted entities exist, they can fail, compromised either by an external or internal malicious actor. 

Swingby Skybridge, described in this document, can provide a technical custodian with **decentralized** control. This technical custodian is effectively a cryptocurrency address where a subset of a large community is needed to create a valid signature. based custodians, and it can be used to move cryptocurrencies across different blockchains, taking advantage of all they have to offer.

### Bitcoin all the chains!

In recent years there has been an increase in applications that use public blockchains and smart contract platforms.  However, many of these blockchains have a fundamental liquidity problem - that is, there is not enough value being recorded on them. Even with compelling decentralized applications \(Dapps\) such as decentralized exchanges \(DEXes\), an application or blockchain might not work well without liquidity.

Where is the value and liquidity today?  Bitcoin. Bitcoin has a large number of users, a large total asset value, and is liquid. If we were able to make Bitcoin available and transferable to other blockchains, we could ignite activity on the other chains.  This is especially true if we are able to move the value of Bitcoin onto other blockchains without needing to trust a specific intermediary.

By being able to create a “Bitcoin Token” on other blockchains, the following advantages are created for bitcoin holders and for the other blockchains:

* Bitcoin users can use Dapps, DEXes, and other services on other blockchains without needing to convert their BTC into the native tokens of the other blockchains
* Bitcoin users can take advantage of the innovative characteristics of the other chains, such as settlement speed, lower transaction fees, and anonymity, etc - whilst remaining invested in the underlying BTC
* Bitcoin's scalability is improved by offloading some Bitcoin transactions to other chains
* Users of other chains would benefit from a new wave of liquidity and users from Bitcoin
* Decentralized exchanges running on blockchains such as Binance Chain  and Ethereum could allow trading of Bitcoin tokens, increasing the liquidity and utility of Bitcoin tokens

**The creation of Bitcoin tokens on non-Bitcoin chains without needing to trust specific actors would be a milestone in the history of cryptocurrencies**, and will help to accelerate Dapps such as decentralized exchanges.

### What is a Cross-chain bridge?

A cross-chain bridge is a concept used to allow tokens to be swapped from their native blockchain to a token on another blockchain. This allow more flexible usage of tokens, for example use BTC on Binance DEX, use BTC on Smart Contract platforms, or swap native MainNet tokens into a BEP-2 / ERC-20 to reduce technical complexity with exchange listings.

There are many technical possibilities to implement such a bridge, ranging from completely centralized to somewhat decentralized solutions. The challenges with current bridges are that the fast and user friendly solutions are too centralized, whereas the decentralized solutions are too slow and not user friendly.

Swingby Skybridge aims to build fast, decentralized, and user friendly swaps for ECDSA-based blockchains \(Bitcoin + all forks, Ethereum, Binance Chain, EOS, Tron, TomoChain, VeChain, etc.\) by using Threshold-Signature-Scheme \(TSS\).

{% hint style="danger" %}
Users need to consider the custodial aspect of bridge implementations. A compromised bridge may potentially "lock" the tokens on the non-native chain, i.e. not allowing users to swap back to the native chain.
{% endhint %}

### **What is a Decentralized Custodian?**

Businesses that hold assets on behalf of other parties can be described as custodians.  Custodians store their clients’ assets in addresses that they \(the custodians\) control by virtue of knowing the linked private key\(s\) to those addresses.

But those custodians bear the risks of private key loss or theft, which in both cases lead to loss of control of their clients’ funds.  So today, custodians typically store the majority of their clients’ assets in multi-signature addresses, and they store the controlling private keys offline.  Although this is more secure than having private keys stored on internet-connected devices, the tradeoff is that it is inconvenient, and creates operational complexities for parties acting as custodians.

The industry has long needed a solution to the apparent trade off between security and convenience.

Swingby Skybridge based on [**GG18**](https://eprint.iacr.org/2019/114.pdf) paper that 2018 paper entitled _Fast Multiparty Threshold ECDSA with Fast Trustless Setup_ by Rosario Gennaro and Steven Goldfeder described the first threshold ECDSA signature scheme protocol that supports multiparty signatures with efficient, dealer-less key generation.

Using the ideas outlined in the paper, it is now possible to construct ECDSA addresses \(used in Bitcoin, Ethereum and many other blockchains\) using efficient, dealer-less key generation and arbitrary number of parties, some predetermined threshold number of whom jointly have the power to create a valid signature.

**Note that this is not a multi-sig address as only one signature is created at the end of the multiparty signing process**.  Additionally, the private key shares held by each party are created without having to rely on a trusted dealer to create and distribute the key shares \(a dealer would be a single point of failure for the system\).

This is the basis of a decentralized custodian.

