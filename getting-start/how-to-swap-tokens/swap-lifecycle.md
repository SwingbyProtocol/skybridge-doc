---
description: What is the lifecycle of a swap transaction?
---

# Swap lifecycle

### Swap status flow diagram

The following diagram shows the decision tree used by the Skybridge nodes to decide which states that a swap moves through during processing.

![](../../.gitbook/assets/status.png)

### Why was my transaction refunded?

A transaction may refund for several reasons.

* Timeout.
* Lack of liquidity in the float pools.
* Miscellaneous risk prevention in the node software.

