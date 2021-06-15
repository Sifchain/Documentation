---
description: >-
  Reference this page for all current reward programs that we are running at
  Sifchain!
---

# Rewards Programs

## Special Programs

### Liquidity Mining and Validator Subsidy Rewards on Sifchain

Liquidity mining rewards are rewards given for adding liquidity in the Sifchain [liquidity pool subsystem](https://docs.sifchain.finance/roles/liquidity-providers), whereas validator subsidy rewards are provided for staking or [delegating](https://docs.sifchain.finance/roles/delegators) to the [validator subsystem](https://docs.sifchain.finance/roles/validators).

#### Liquidity Mining & Validator Subsidy Rewards Introduction

Sifchain is running a liquidity mining program. There are 45 million ROWAN being initially allocated to this current rewards program. The eligibility window for the program started on Feb 19, 2021 and is set to end on June 30, 2021. All liquidity and stake that is added to Sifchain during the eligibility window will be eligible for LM and VS Rewards. Rewards will continue to accrue up until August 4th, 2021 \(regardless if a user has added liquidity early or late\).

For LM rewards, the total rewards in the program are split between the different liquidity providers based on the proportion of total liquidity in the system that they have been providing over the duration of the program. For VS rewards, the total rewards in the program are split between the different users who have provided stake or delegations. Their total possible reward grows the longer they keep their liquidity in the system, up to a maximum of 4 months.

#### Global bucket

* There can be multiple global reward buckets that each contain ROWAN to be rewarded across a 4-month time period. Initially, we will start with one bucket, but we may periodically top up with additional buckets as the program continues or is extended.
* Reward ROWAN starts off in its global bucket, and as the program progresses will be moved over to individual users as they earn their rewards.
* Participants will generate rewards through their behavior. By the end of each bucket's 4-month drain, its entire ROWAN reward will be drained into user rewards.

#### Tickets

* For the duration of the program, each time a user deposits to a liquidity pool or stakes with validator, a corresponding “ticket” is made. This ticket stores the total ROWAN value of the deposit/stake made, which in turn determines how much ROWAN they will be rewarded. A new ticket is created each time a user pools liquidity or provides stake. Likewise, a proportional amount of tickets are burned each time a user withdraws their liquidity or removes their stake.

**Ticket Multiplier**

* Tickets are non-fungible. Each ticket has a multiplier that grows over time up from 25% to 100%.

**Reward Generation**

* Each time period, each ticket generates rewards from each global bucket on the basis of 1 share per ticket. The rewards are attached to the ticket.

#### Validator Subsidy Rewards: Handling of Delegations

* Any users who provide stake are eligible to earn VS rewards. This includes users who stake and run their own node, as well as users who delegate to a node operator. 
* When staking your own node, users will earn 100% of the rewards that are associated with the staked amounts. 
* When delegating to an existing node, users will earn rewards based on the commission rate that the node operator is charging \(similar to how block rewards work\). As an example: If I am delegating to a node operator that charges 10% commission, all VS rewards that are earned based on my delegation: 90% of those rewards will go to me and 10% of those rewards will go to the node operator.
* For node validators that have earned rewards based on delegations, these rewards have the following stipulations associated with them:
  * These rewards only become claimable when either: a\) the delegators claim their portion of these rewards or b\) those rewards for those delegators reach full maturity. Once one of these actions happen, these rewards will be considered claimable by the node operator.

**Claiming rewards**

* Users can claim their rewards at any time but doing so will reset all of their tickets. Whenever a ticket is reset, it will release its rewards to the user based on its current multiplier. Reset tickets then start empty with a 25% multiplier again.

**Withdrawing Liquidity or Stake**

* Whenever a user withdraws their liquidity or stake, they will automatically burn an equivalent amount of tickets to cover the withdrawal. Tickets associated with these rewards will be automatically reset. Again, whenever a ticket is reset, it will release its rewards to the user based on its current multiplier. Reset tickets then start empty with a 25% multiplier again. Tickets will be burned in order from lowest multiplier to highest in order to preserve a user's best tickets with highest multipliers.
* When a user withdraws their liquidity or their stake, it will not automatically submit a claim for the associated rewards. While it will reset those reward tickets, a user will still need to go into the DEX and manually submit a claim transaction to fully claim those rewards.

#### Calculations

For each user, at any point in time, we will calculate the following and display in the DEX:

For LM rewards:

* **Claimable Rewards**: The immediate current claimable reward.
* **Pending Dispensation**: This is the amount that will be dispensed on Friday. Any new claimable amounts will need to be claimed after the next dispensation is processed.
* **Dispensed Rewards**: The amount of rewards that have been paid out to that user already.
* **Projected Full Amount**: The projected total reward at maturity at the end of the program, assuming the amount of tickets across all users stays as is. This number takes into consideration projected future rewards, but does NOT include already claimed/disbursed previous rewards for that user.
* **Projected Full Amount Maturity Date**: This displays the date the user will need to a\) keep their current liquidity positions in and b\) not claim their rewards until to realize the full projected amount. 

For VS Rewards:

* **Claimable Rewards**: The immediate current claimable reward.
* **Pending Dispensation**: This is the amount that will be dispensed on Friday. Any new claimable amounts will need to be claimed after the next dispensation is processed.
* **Reserved Commission Rewards**: These are rewards that a node validator has earned from their delegators, but are not yet claimable due to either: a\) the delegators not claiming their portion of these rewards yet or b\) those rewards for those delegators not reaching full maturity yet. Once one of these actions happen, these rewards will be considered claimable.
* **Dispensed Rewards**: The amount of rewards that have been paid out to that user already.
* **Projected Full Amount**: The projected total reward at maturity at the end of the program, assuming the amount of tickets across all users stays as is. This number takes into consideration projected future rewards, and already claimed/disbursed previous rewards for that user.
* **Projected Full Amount Maturity Date**: This displays the date the user will need to a\) keep their current liquidity positions in and b\) not claim their rewards until to realize the full projected amount. 

#### Process for claiming rewards

For both LM rewards and VS rewards, a user must claim their rewards in order to receive them. Claiming rewards would stop them from continuing to accumulate even if a user has kept their tokens in the subsystem. Therefore, we encourage users NOT to claim their rewards until they are ready to withdraw liquidity.

Users need to burn or reset their tickets to claim their rewards. This can happen on: removal of liquidity/stake and/or manually claiming of rewards through the DEX.

Each week users can go into the DEX and submit a claim transaction to claim their rewards. These transactions will be gathered at the end of each week and then at the end of the week, we will process those claims and disburse them. The calculation of determining the amount that will be disbursed is done at time of claim submission. Because we burn the tickets at time of claim submission, it is beneficial to the user to wait until Friday to submit a claim transaction. At week end, we will generate a list of users and their reward payouts, which will be sent to the dispensation module to trigger the start of the distribution process.

#### Impermanent Loss Mitigation

We have implemented an Impermanent Loss \(IL\) Mitigation. If a user realizes IL, the user will continue to earn rewards based on the realized IL amount. These values are based on the Rowan value of a user’s add.

For example, imagine a user deposits 50K Rowan and 50K Rowan worth of USDT for a total of 100K Rowan worth of assets into a Sifchain liquidity pool. Let’s say this amount drops to 80K worth of Rowan due to price fluctuations. The user removes all 80K Rowan worth of assets. That user will continue to earn LM rewards based off of the 20K Rowan worth of assets that was lost due to IL \(the 20k here is called the ‘IL amount’\). The IL amount ONLY comes into play if a user removes their liquidity and realizes IL. If that user were to add additional liquidity after realizing this IL, their LM Reward eligibility amount would be the sum of their IL amount + any added liquidity amounts.

#### FAQ for LM and VS Rewards Programs

* How much ROWAN has been allocated to each program?
  * 45M ROWAN tokens are allocated to each LM rewards and VS rewards \(90M ROWAN in total\). Note that the liquidity mining rewards and the validator subsidy rewards are separate, as we encourage people to contribute to both programs as they provide different utilities for the system.
* During which time periods can I add liquidity/stake/delegate and earn rewards?
  * During the program eligibility dates of 02/19/2021 - 06/30/2021. We highly recommend that you add as much as you can during this time period to both our liquidity pools and stake/delegate to earn maximum rewards across both programs. 
* If I add an amount on the very first date of the eligibility period and then add more on the very last date of eligibility, will I have two different 4 month multipliers happening?
  * Yes. You will receive different multipliers based on your different adds.
* Can I claim just a portion of my rewards?
  * No. A user will need to go to the rewards page in the DEX and submit a claim transaction which will claim ALL of their accumulated rewards. A user claiming their Validator Subsidy rewards must claim all of them as well. 
* When can I claim my rewards?
  * Once we have the mechanism in place in our UI \(coming soon!\), you are free to initiate a claim at any time. Claims will be processed on a weekly basis. But again, please be aware that claiming rewards before the 4x multiplier is realized will impact your rewards earned, as mentioned above.
* Does it matter if I submit my claim on a Monday vs. a Friday since the dispensation will only happen once a week on Friday or Saturday?
  * Yes it does. Because, at the time of claim submission, the associated tickets for a user's rewards would be reset. However, the final payout amount isn't determined until the dispensation module is run. So, if you were to submit a claim on Monday, your multiplier would be reset and your rewards would continue to earn based on that reset-multiplier until Friday/Saturday \(when the dispensation module is run\). However, if you wait until Friday to submit a claim, then your rewards would continue to earn at higher multiplier up until that point in time. 
* If I remove my liquidity/stake/delegate, will it automatically claim my rewards for me as well?
  * Not fully. It will reset tickets associated with the rewards earned from the liquidity/stake/delegate, but it will NOT fully claim those rewards for you. You still need to go into the DEX and submit a claim transaction to claim your rewards. 
* If I claim rewards and remove liquidity, can I re-add liquidity and gain more rewards?
  * Yes, so long as you re-add liquidity between 02/19/2021 - 06/30/2021
* For the VS program, will redelegating reset my multiplier?
  * Redelegating does NOT reset the multiplier.
* How does a validator's commission rate come into play when determining earned reward amounts for the VS program?
  * Users who delegate to validators can earn their share of the validator subsidy rewards depending on the commission rate charged by their validator. For example, if a validator charges 10% commission from delegators, its delegators would earn 90% of the validator subsidy rewards allocated to their delegated liquidity, whereas the validator would receive the remaining 10% as a commission fee.
  * Each validator commission is allocated at the same time as its delegator reward. So, if a validator increases their commission rate today, it won't change yesterday's rewards, but it will change today & tomorrow's rewards unless they redelegate. If a user redelegates, their current rewards and current multiplier will continue to accrue where they left off. Past commissions allocated to the former validator will stay with the former validator, and future commissions with the new validator will accrue with the new validator. Validator commissions are subject to the same multipliers as their respective delegator rewards. These multipliers are applied at the time of reward distribution. Validator commissions are distributed when delegators claim their respective rewards.
* When a validator claims their claimable rewards based on commission, does it affect their un-claimable rewards based on commission?
  * No, it does not. Even if a node operator claims their rewards based on their own stake or based on commissions that have since become claimable, it will have NO effect on the rewards that they have earned, but are not yet claimable. 
* Where can I see my rewards? 
  * You can see your current claimable amount here: [https://dex.sifchain.finance/\#/rewards](https://dex.sifchain.finance/#/rewards) as well as other important fields about your reward position.
  * You can also see even more details here: cryptoeconomics.sifchain.finance

{% hint style="info" %}
Past, Present, and Projected LM and VS Rewards Tool

We created [this tool](https://cryptoeconomics.sifchain.finance/) to allow users to see how their rewards have accumulated overtime, and how they are projected to accumulate into the future.
{% endhint %}

### Community Token Giveaway

The eligibility for our Community Token Giveaway is now closed. The first 1/4 of tokens have bee disbursed. Please refer back here for updates on distribution status.

## Ongoing Programs

### Block Rewards

Block rewards are earned and distributed to Validators and delegators to existing validators in real-time as blocks are processed. To earn these rewards, you must be a validator and acting member in consensus, OR a delegator to a validator and acting member in consensus. For more information on this, please refer [here](https://docs.sifchain.finance/roles/validators#block-rewards).

### Pool Rewards

Pool rewards are given to liquidity providers as a way to incentivize users to add liquidity to our system. They are earned each time a user swaps in/out of the associated pool. You must have liquidity in a pool and for swap activity to be occurring in that pool to earn pool rewards. For more information, please refer [here](https://docs.sifchain.finance/core-concepts/liquidity-pool#liquidity-provider-income-determination).

