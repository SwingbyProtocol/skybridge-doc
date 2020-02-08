---
description: A brief overview of the Skybridge technology stack
---

# Summary

## Overview

**Swingby Skybridge** is a proof of stake based decentralized ephemeral custodian protocol for moving assets between blockchains. It enables fast trust-free bridges between BTC, Ethereum, Binance Chain and other blockchains.

At its core, Swingby Skybridge uses technology derived from the paper entitled _Fast Multiparty Threshold ECDSA with Fast Trustless Setup_ by Rosario Gennaro and Steven Goldfeder, describing a threshold ECDSA signature scheme protocol that supports multiparty signatures with efficient, dealer-less key generation.

On top of this, Skybridge leverages a novel layer 2 proof-of-stake consensus and networking protocol to facilitate inter-blockchain swaps using the TSS technology.

#### Decentralized Token Bridge

Swingby Skybridge's basic approach is to manage one decentralized wallet using TSS technology to form one multiparty signature wallet and use this to facilitate token swaps.

By using TSS, tokenization of BTC to other chains, which was difficult until now, can be realized simply and securely. This is because traditional wallets such as BTC were unable to scale the wallet by the number of signatures. But by using TSS, an unspecified number of participants can manage a single wallet.

![BTC token on the binance chain](.gitbook/assets/img_skybridge.png)

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





