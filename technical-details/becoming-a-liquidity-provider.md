---
description: Discover how to become a liquidity provider on Skybridge with Float Staking.
---

# Becoming a liquidity provider

Liquidity providers are one of the main stakeholders of the Skybridge protocol and are rewarded to do so by receiving part of the transaction fees from users swapping BTC to WBTC \(and vice versa\).

In Swingby Skybridge, liquidity provision is also called **'Float Staking'**. 

The system is built around a LP token, issued as **Swingby BTC \("sbBTC"\)** that represent a stake in the total liquidity of the protocol. This token runs on Ethereum as an ERC20 compliant token that can be incorporated and traded in other DeFi protocols.

### How to add liquidity?

Unlike many other DeFi protocols like Uniswap or Balancer, the liquidity provision is unilateral and one-sided. Participants wishing to lock their BTC/WBTC tokens need to deposit their tokens in a specific address by interacting with a contract that has been deployed on Ethereum.

When a liquidity provider deposits BTC or WBTC in the float pools, a sbLP token is minted to their Ethereum wallet based on the price of the LP relative to BTC. It represents a stake of the total liquidity available in the pool.

### How to remove liquidity?

When a liquidity provider withdraws BTC or WBTC from the float pools, the sbLP token is burnt from their Ethereum wallet and the matching quantities are received based on the price of the LP relative to BTC.

### How much of the total transaction fee do I receive?

Liquidity providers receive **33.3%** of each swap fee \(excluding network fees like gas\). This percentage is shared proportionally based on the respective stakes for each liquidity providers. 

The distribution of the transaction fee is done through the LP mechanism that is described in [SWIP-020](https://github.com/SwingbyProtocol/swips/blob/cleanup/swips/SWIP-020.md). The fee payment is implicit \(i.e., no direct send transaction\) and is compounded at each new swap. 

### What are the risks?

Since assets bridged are expected to be constant in value, some of the existing risks like impermanent loss is inexistant in Skybridge. However, the protocol itself may have some risks that all liquidity providers should understand before deciding to deposit liquidity onto a Skybridge.

* **Lack of liquidity to withdraw assets —** since the ratio of the float pools is not expected to be equal to 50%, it is possible that the liquidity provider may not withdraw the preferred asset. For instance, if someone deposits 4 BTC and wants to redeem 4.25 BTC 3 months later while the float quantity on the Bitcoin network is less than 4.25BTC, the liquidity provider would only be able to withdraw to WBTC.
* **Cost of opportunity relative to other lending platforms and other DeFi protocols —** since fees are paid from transaction fees, the revenue for liquidity providers fluctuate based on market demand for Skybridge. Thus, it is possible that the yield on their assets may not always be in line with user expectations. Conversely, the opposite can occur and the greater the market demand to swap assets, the higher is the return on their bitcoins.

