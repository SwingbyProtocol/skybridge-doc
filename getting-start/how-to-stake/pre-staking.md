---
description: >-
  How to participate in the pre-staking event before the official main network
  launch
---

# Pre-staking

To set the direction of Swingby development, anyone interested in the Swingby ecosystem will have the option to stake their Swingby tokens and vote for the next chain that should be integrated. The staked tokens will be rewarded with 1% interest distributed on a weekly basis, and these rewards will reduced with each development milestone achieved:

| Milestone | Reward per week |
| :--- | :--- |
| Until BTC mainnet launch | 1% |
| Until second swap pair | 0.75% |
| Until third swap pair | 0.5% |
| Until fourth swap pair | 0.25% |
| After fourth swap pair | No reward |

The gradual reduction of pre-stake rewards is to ease the transition from pre-staking to to node staking.

#### How to stake

1. Choose a wallet that supports transactions with MEMO.
2. Unlock your wallet with an address that holds SWINGBY tokens.
3. Find the latest pre-stake MEMO on the official Telegram, Twitter, and website.
4. Send any amount of SWINGBY tokens either back to the same address \(self-send\) or to any other address that you want to use as your staking address. The transaction need a MEMO in following format: “XXXXXXXX YYYYYY” where: XXXXXXXX = 8 digit alphanumeric weekly staking code \(**changed every week, make sure you have the correct staking code by double-checking on official website / Twitter / Telegram\)**. **** YYYYYY = Optional token ticker symbol to vote for the next chain to integrate. _**Example:** NEO_
5. The amount of SWINGBY tokens sent will be counted as "pre-staked". 
6. Do not send any SWINGBY tokens from the staking address for the rest of the week. **Sending any amount of SWINGBY tokens from a pre-staked address to any other address will cancel the whole stake for that week.**
7. At the end of the week, all pre-staked addresses will receive reward using following formula:

   $$
   reward = (amountOfStakedTokens * (stakedTime / stakePeriod)) * weeklyRewardPercentage
   $$

   Example:  
   Assuming 100 tokens, held for 50% of the week, 1% weekly staking reward.  
   _\(100\*\(50/100\)\)\*0.01\) = 0.5_  SWINGBY tokens received as distribution.

8. Re-stake with the new MEMO released every week for continuous rewards.

