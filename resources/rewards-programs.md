---
description: >-
  Reference this page for all current reward programs that we are running at
  Sifchain!
---

# Rewards Programs

## Special Programs

### Liquidity Mining and Validator Subsidy Rewards on Sifchain

Sifchain uses the Token Geyser mechanism to calculate liquidity mining \(LM\) rewards for liquidity providers and validator subsidy \(VS\) rewards for validators \(stakers\) and delegators. The model is based on [Ampleforth’s Token Geyser model](https://www.ampltalk.org/app/forum/ampl-geyser-19/topic/about-the-geyser-21/).

Liquidity mining rewards are rewards given for adding liquidity in the Sifchain [liquidity pool subsystem](https://docs.sifchain.finance/roles/liquidity-providers), whereas validator subsidy rewards are provided for staking or [delegating](https://docs.sifchain.finance/roles/delegators) to the [validator subsystem](https://docs.sifchain.finance/roles/validators).

* Liquidity Mining rewards are given to users who provide liquidity to liquidity pools. Liquidity pools offer capital for users to swap with. They include ROWAN and other assets \(e.g. ETH, wBTC, USDT, etc.\). Tokens added to a liquidity pool can be removed at any time.
* Validator Subsidy rewards are given to users who stake or delegate liquidity to the validator subsystem. Validators secure all transactions on Sifchain via [Tendermint Consensus](https://docs.sifchain.finance/core-concepts/sifchain-consensus). Only ROWAN can be staked or delegated in this subsystem. Tokens added to the validator subsystem can be removed only after an [unbonding period](https://docs.sifchain.finance/roles/validators#unbonding).

The amount of rewards accumulated is correlated to `user_pooling_token_time / global_pooling_token_time` for LM, or `user_staking_token_time / global_staking_token_time` for VS.

For example, imagine there are two users in the system, Alice and Bob. Alice has staked 10 ROWAN for 1 day, Bob has staked 5 ROWAN for 3 days.

`Alice_token_time = 10 tokens * 1 days = 10` 

`Bob_token_time = 5 * tokens * 3 days = 15`  


`global_token_time = Alice_token_time + Bob_token_time = 25 token_days`  


`Alice earns (10 / 25) = 40% of the rewards`

`Bob earns (15 / 25) = 60% of the rewards`  


There are a couple of important fields we should define.  Everything below applies to LM and VS rewards:

* **Reward Multiplier**: This is the multiplier that will be used to calculate the amount of rewards a user has earned. The max multiplier is 4. 
* **Daily Incremented Reserved Reward**: This is the incremental amount of reward that is reserved for a user per day.  This amount is continuously increased until a user claims and withdraws, or the user gets the maximum 4x multiplier.
* **Reserved Reward**: This is the total amount of reward that has been reserved for a user \(based on the daily incremented reserved reward\). 
* **Claimable Percentage**: This is the percentage of the reserved reward that is claimable at any given time by the user. When the multiplier is 1x, the user has a claimable percentage of 25%. This percentage will also increase linearly until it gets to 100% at the 4x multiplier. This means that if you keep all of your liquidity/stake/delegate in for 4 months, on the last day, the claimable percentage would be 100%.
* **Claimable Reward**: This is the reserved reward multiplied by the claimable percentage. This is the amount of reward that a user can actually claim at any given time. This will be displayed to the user in the UI.

Users can get a maximum multiplier of 4x after 4 months of holding their liquidity/stake/delegate. The multiplier is in place to encourage long-term liquidity provision.  Any liquidity removal or unstaking or undelegating would reset the multiplier. For example:

`1. On 02/19/2021, Alice adds $200 worth of liquidity in a liquidity pool. Her reward multiplier starts at 1x and increases linearly over time. The $200 worth of liquidity earns rewards based on this multiplier and will do so as it increases.`  


`2. On 03/30/2021, when her multiplier is ~2x, Alice adds another $50 worth of liquidity to a liquidity pool. Her multiplier remains unaffected, and continues to increase over time. The newly added $50 worth of liquidity will earn rewards right away based on the ~2x multiplier.`  


`3. On 5/20/2021, when her multiplier is at 3x, Alice removes $20 worth of liquidity. At this point, Alice has a ‘Reserved Reward’ and her ‘Claimable Reward’ amount is ~75.21% of this amount. Her multiplier will reset to 1x and will again begin to increase over time, applied to her remaining liquidity.`

Redelegating does NOT reset the multiplier

Only liquidity/stake/delegate added during the program eligibility window of 02/19/21-05/14/21 will be eligible for the multiplier.  Users can enter the program on the last day \(May 14\) and then hold their liquidity from 4 months thereafter to the max 4x multiplier if they claim their tokens in September.

The LM rewards displayed on our statistics page and the VS rewards displayed on the rewards page are based on the assumption that users hold their liquidity for 4 months and therefore receive a maximum 4x multiplier for their rewards.

Users who delegate to validators can earn their share of the validator subsidy rewards depending on the commission rate charged by their validator. For example, if a validator charges 10% commission from delegators, its delegators would earn 90% of the validator subsidy rewards allocated to their delegated liquidity, whereas the validator would receive the remaining 10% as a commission fee.

For both LM rewards and VS rewards, a user must claim their rewards in order to receive them. Claiming rewards would stop them from continuing to accumulate even if a user has kept their tokens in the subsystem. Therefore, we encourage users NOT to claim their rewards until they are ready to withdraw liquidity.

* Note that claiming rewards is not yet possible in our UI, but it will soon be available. For now, all LM and VS rewards are still being accumulated since the start of both programs on Feb 19.

Up to 30M ROWAN tokens are allocated to each LM rewards and VS rewards \(60M ROWAN in total\). This total amount of rewards would only be given away if all users left their tokens in the system unclaimed for long enough to receive the maximum multiplier \(4x\).

* Note that the liquidity mining rewards and the validator subsidy rewards are separate, as we encourage people to contribute to both programs as they provide different utilities for the system.

When an LM or VS award is claimed by a user, it will be dispersed at the end of the week it is claimed.

### FAQ for LM and VS Rewards Programs

* During which time periods can I add liquidity/stake/delegate and earn rewards?
  * During the program eligibility dates of 02/19/2021 - 05/14/2021. We highly recommend that you add as much as you can during this time period to both our liquidity pools and stake/delegate to earn maximum rewards across both programs. 
* If I add an amount on the very first date of the eligibility period and then add more on the very last date of eligibility, will I have two different 4 month multipliers happening?
  * No. You will have one 4-month multiplier happening as based on your first add. When you add the 2nd amount, it will start earning rewards based on the current multiplier that it is the day of the add.  
* Can I claim just a portion of my rewards?
  * No, a user when claiming their Liquidity Mining rewards will be forced to claim all of them. A user claiming their Validator Subsidy rewards must claim all of them as well. 
* When can I claim my rewards?
  * Once we have the mechanism in place in our UI \(coming soon!\), you are free to initiate a claim at any time. Claims will be processed on a weekly basis. But again, please be aware that claiming rewards before the 4x multiplier is realized will impact your rewards earned, as mentioned above.
* If I remove my liquidity/stake/delegate, will it automatically claim my rewards for me as well?
  * No, you will still need to go to Sifchain's BetaNet and claim your rewards manually.
* If I claim rewards and remove liquidity, can I re-add liquidity and gain more rewards
  * Yes, so long as you re-add liquidity between 02/19/2021 - 05/14/2021
* Where can I see my rewards? Is the amount that is shown in the DEX, is this my current claimable amount or my reserved amount?
  * You can see your current claimable amount here: [https://dex.sifchain.finance/\#/rewards](https://dex.sifchain.finance/#/rewards). This is your current **claimable** amount. 
  * We are currently working on building in the ability to claim these rewards. While claiming, we will show you your multiplier date and your current multiplier while you do a final confirmation on your claim.

![](../.gitbook/assets/screen-shot-2021-04-08-at-4.57.13-pm.png)

{% hint style="info" %}
\*\*\*\*[**Example Calculator for Liquidity Providers and Validators**](https://docs.google.com/spreadsheets/d/13d9ioNjr8LLN48LqKOhtBn87zch8dodzARUMlsxU6os/edit?usp=sharing)\*\*\*\*

These sample scenarios are provided as-is to showcase simple examples and do not consider some externalities such as fees, price fluctuations, or other users also adding and removing liquidity.
{% endhint %}

### Community Token Giveaway

The eligibility for our [Community Token Giveaway](%20https://medium.com/sifchain-finance/community-distribution-tokens-5dc4b184948e) is now closed, but have not been distributed yet. Please refer back here for updates on distribution status. 

## Ongoing Programs

### Block Rewards

Block rewards are earned and distributed to Validators and delegators to existing validators in real-time as blocks are processed. To earn these rewards, you must be a validator and acting member in consensus, OR a delegator to a validator and acting member in consensus. For more information on this, please refer [here](https://docs.sifchain.finance/roles/validators#block-rewards).

### Pool Rewards

Pool rewards are given to liquidity providers as a way to incentivize users to add liquidity to our system. They are earned each time a user swaps in/out of the associated pool. You must have liquidity in a pool and for swap activity to be occurring in that pool to earn pool rewards. For more information, please refer [here](https://docs.sifchain.finance/core-concepts/liquidity-pool#liquidity-provider-income-determination).

