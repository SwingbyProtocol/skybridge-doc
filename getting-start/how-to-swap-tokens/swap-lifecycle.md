---
description: Status flows for users to understand and troubleshoot swaps
---

# Swap lifecycle

### Swap status flow diagram

The following diagram shows the decision tree used by the Skybridge nodes to decide which states that a swap moves through during processing.

![](../../.gitbook/assets/status.png)

### Why was my transaction refunded?

A transaction may refund for several reasons.

* Lack of a 'memo' when one was required.
* Timeout.
* Miscellaneous risk prevention in the node software.

