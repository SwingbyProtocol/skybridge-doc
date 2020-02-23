---
description: A brief overview of the Skybridge technology stack
---

# Summary

## Overview

_Swingby Skybridge_ is a proof-of-stake based decentralized ephemeral custodian protocol for the cross-chain movement of crypto assets. It enables fast trust-free bridges between BTC, Ethereum, Binance Chain and other blockchains.

At its core, _Swingby Skybridge_ uses technology derived from the paper entitled _Fast Multiparty Threshold ECDSA with Fast Trustless Setup_ by _Rosario Gennaro_ and _Steven Goldfeder_ which describes a threshold ECDSA signature scheme protocol that supports efficient, dealer-less key generation and distributed computation of digital signatures.

On top of this, _Swingby Skybridge_ leverages a novel layer 2 proof-of-stake consensus and networking protocol to facilitate inter-blockchain swaps using this technology.

### Decentralized Token Bridges

The approach adopted by _Swingby Skybridge_ is to use clusters of nodes to manage decentralized wallets using threshold signatures \(TSS\) technology to form multiparty signature wallets and use them to facilitate token swaps.

### **Modern Cryptography, Applied**

By utilizing recent developments in cryptographic research, the tokenization of BTC on other chains, an ambition that has proven difficult to achieve with prior technologies, can be realized simply and securely.

Traditional approaches to this problem have used complex multi-signature transactions and script op-code methods like Hash Time-Lock Contracts \(HTLCs\) which require bespoke wallet apps and are not widely supported. 

_Swingby Skybridge_ aims to apply modern cryptography for the real world to address gaps in the cross-chain DeFi ecosystem.

![BTC token on the Binance Chain](.gitbook/assets/img_skybridge.png)

## Contents

{% page-ref page="introduction.md" %}

{% page-ref page="how-it-works/" %}

{% page-ref page="supporting-chains.md" %}

{% page-ref page="fees.md" %}

### Getting Started

{% page-ref page="getting-start/how-to-swap-tokens/" %}

{% page-ref page="getting-start/how-to-stake/" %}

{% page-ref page="getting-start/how-to-setup-your-swingby-node.md" %}

### Technical Details

{% page-ref page="technical-details/the-swingby-node/" %}

{% page-ref page="technical-details/token-mechanism.md" %}





