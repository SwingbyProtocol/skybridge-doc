---
description: A brief overview of the Skybridge technology stack
---

# Summary

## Overview

**Swingby Skybridge** is a proof-of-stake based decentralized ephemeral custodian protocol for the cross-chain movement of crypto assets. It enables fast trust-free bridges between BTC, Ethereum, Binance Chain and other blockchains.

At its core, Swingby Skybridge uses technology derived from the paper entitled _Fast Multiparty Threshold ECDSA with Fast Trustless Setup_ by Rosario Gennaro and Steven Goldfeder which describes a threshold ECDSA signature scheme protocol that supports efficient, dealer-less key generation and distributed computation of digital signatures.

On top of this, Skybridge leverages a novel layer 2 proof-of-stake consensus and networking protocol to facilitate inter-blockchain swaps using this technology.

#### Decentralized Token Bridge

Swingby Skybridge's approach is to manage one decentralized wallet using threshold signatures \(TSS\) technology to form one multiparty signature wallet and use it to facilitate token swaps.

By using threshold signatures, the tokenization of BTC on other chains, an ambition that has proven difficult to achieve with prior technologies, can be realized simply and securely. Traditional approaches to this problem have used complex multi-signature transactions and script op-code methods like Hash Time-Lock Contracts \(HTLCs\) which require bespoke wallet apps and are not widely supported. 

Swingby Skybridge aims to deploy modern cryptography, applied, to solve real problems in the DeFi ecosystem.

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





