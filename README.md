# What is Swingby Skybridge

## Overview

**Swingby Skybridge** is a Proof of Stake based decentralized custodian protocol for moving assets between blockchains.

Swingby Skybridge provides trust-free BTC bridge for Ethereum and Binance and other blockchains using threshold-signature-scheme\(TSS\).

Swingby Skybridge based on [**GG18**](https://eprint.iacr.org/2019/114.pdf) paper that 2018 paper entitled _Fast Multiparty Threshold ECDSA with Fast Trustless Setup_ by Rosario Gennaro and Steven Goldfeder described the first threshold ECDSA signature scheme protocol that supports multiparty signatures with efficient, dealer-less key generation.

#### Decentralized Token bridge

Swingby Skybridge's basic approach is to manage one huge **decentralized** wallet by using TSS to form one huge multiparty signature wallet.

By using TSS, **tokenization of BTC** to other chains, which was difficult until now, can be realized simply and securely. This is because traditional wallets such as BTC were unable to scale the wallet by the number of signatures, but by using TSS, an unspecified number of participants can manage a single wallet.

![BTC to BTC Token on the binance chain](.gitbook/assets/img_skybridge.png)

## Contents

{% page-ref page="how-it-works/" %}

{% page-ref page="getting-started/how-to-swap-tokens/btc-move-to-btc-token.md" %}

{% page-ref page="getting-started/how-to-swap-tokens/btc-token-move-to-btc.md" %}

{% page-ref page="supporting-chains.md" %}

{% page-ref page="technical-details/token-mechanism.md" %}

{% page-ref page="fees.md" %}



