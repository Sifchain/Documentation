---
description: >-
  Reference this page for all current reward programs that we are running at
  Sifchain!
---

# Rewards Programs

## Special Programs

### Liquidity Mining and Validator Subsidy Rewards on Sifchain

Liquidity mining rewards are rewards given for adding liquidity in the Sifchain [liquidity pool subsystem](https://docs.sifchain.finance/roles/liquidity-providers), whereas validator subsidy rewards are provided for staking or [delegating](https://docs.sifchain.finance/roles/delegators) to the [validator subsystem](https://docs.sifchain.finance/roles/validators).

#### Liquidity Mining Rewards Introduction

Sifchain is running a liquidity mining program. There are 45 million ROWAN being initially allocated to this current rewards program. The eligibility window for the program started on Feb 19, 2021 and is set to end on June 30, 2021. All liquidity that is added to Sifchain during the eligibility window will be eligible for LM Rewards. Rewards will continue to accrue up until August 4th, 2021 \(regardless if a user has added liquidity early or late\).

The total rewards in the program are split between different liquidity providers based on the proportion of total liquidity in the system that they have been providing over the duration of the program. Their total possible reward grows the longer they keep their liquidity in the system, up to a maximum of 4 months.

#### Global bucket

* There can be multiple global reward buckets that each contain ROWAN to be rewarded across a 4-month time period. Initially, we will start with one bucket, but we may periodically top up with additional buckets as the program continues or is extended.
* Reward ROWAN starts off in its global bucket, and as the program progresses will be moved over to individual users as they earn their rewards.
* Participants will generate rewards through their behavior. By the end of each bucket's 4-month drain, its entire ROWAN reward will be drained into user rewards.

#### Liquidity-Deposit Tickets

* Each time a user deposits liquidity to a liquidity pool during the program, they create an amount of liquidity-deposit tickets equal to the ROWAN value of the deposit made. Users will create new tickets each time they deposit liquidity.

**Ticket Multiplier**

* Tickets are non-fungible. Each ticket has a multiplier that grows over time up from 25% to 100%.

**Reward Generation**

* Each time period, each ticket generates rewards from each global bucket on the basis of 1 share per ticket. The rewards are attached to the ticket.

**Claiming rewards**

* Users can claim their rewards at any time by resetting their tickets. Whenever a ticket is reset, it will release its rewards to the user based on its current multiplier. Reset tickets then start empty with a 25% multiplier again.

**Withdrawing Liquidity**

* Whenever a user withdraws their liquidity, they will automatically burn an equivalent amount of tickets to cover the withdrawal. Tickets associated with these rewards will be automatically reset. Again, whenever a ticket is reset, it will release its rewards to the user based on its current multiplier. Reset tickets then start empty with a 25% multiplier again. Tickets will be burned in order from lowest multiplier to highest in order to preserve a user's best tickets with highest multipliers.
* When a user withdraws their liquidity, it will not automatically submit a claim for the associated rewards. While it will reset those reward tickets, a user will still need to go into the DEX and manually submit a claim transaction to fully claim those rewards.

#### Calculations

For each user, at any point in time, we will calculate the following and display in the DEX:

* **Claimable Rewards**: The immediate current claimable reward.
* **Dispensed Rewards**: The amount of rewards that have been paid out to that user already.
* **Projected Full Amount**: The projected total reward at maturity at the end of the program, assuming the amount of tickets across all users stays as is. This number takes into consideration projected future rewards, and already claimed/disbursed previous rewards for that user.
* **Projected Full Amount Maturity Date**: This displays the date the user will need to a\) keep their current liquidity positions in and b\) not claim their rewards until to realize the full projected amount. 

We will also be calculating the following and displaying these in cryptoeconomics.sifchain.finance as additional pieces of information to assist our users:

* **Reward Buckets**:
  * **Rowan -** Amount of ROWAN still left to be rewarded in this bucket.
  * **Initial Rowan** - This is the total amount of the ROWAN reward pool for the LM program in this bucket.
  * **Duration -** The amount of epochs this bucket will be rewarded over.
* **Total Tickets:** Our implementation groups together tickets with the same multiplier.
  * **Amount** - This is the number of tickets in this group the user has.
  * **Multiplier** - This is the current multiplier of all of the tickets in this group.
  * **Reward** - This is the current **claimable** reward generated by all of the tickets in this group.
  * **Timestamp** - This represents the timestamp of when the user was awarded these tickets.
* **Claimed** - This is the current reward amount that has already been ‘claimed’ due to previous liquidity removals and/or claims made. This is a total amount across all ticket groups for that user.
* **Dispensed** - This is the total amount of rewards that have been disbursed to the user from previous claims.
* **Forfeited** - This is the amount of reward that was forfeited due to early liquidity removals and early reward claims.
* **ClaimableRewards** - This is the total **cumulative** amount of claimable rewards for a user. This raw number does include already claimed amounts.
* **Total Tickets** - The total amount of tickets the user has.
* **Total Reward at Maturity** - This is a user's estimated projected full reward amount that will be earned over the entire program if they were to leave their current liquidity positions in place to the 'maturity date'. This number can fluctuate due to other market conditions and this number is a representation of the current market as it is in this very moment.
* **Maturity Date** - This is the date that all rewards will hit full maturity. 
* **Future Reward** - This is the amount the user should expect to receive once the program has ended and full multiplier is achieved. This does NOT include any past earned rewards.
* **Current Yield on Tickets** - This is the yield the user will get in the future based on amount of tickets the user has \(which is the amount of liquidity they have provided, excluding impermanent loss\).
* **Next Reward Projected APY on tickets** - This is the current APY the user is receiving based on their tickets \(excluding impermanent loss\).

#### Process for claiming rewards

For both LM rewards and VS rewards, a user must claim their rewards in order to receive them. Claiming rewards would stop them from continuing to accumulate even if a user has kept their tokens in the subsystem. Therefore, we encourage users NOT to claim their rewards until they are ready to withdraw liquidity.

Users need to burn or reset their tickets to claim their rewards. This can happen on: removal of liquidity and/or manually claiming of rewards through the DEX.

Each week users can go into the DEX and submit a claim transaction to claim their rewards. These transactions will be gathered at the end of each week and then at the end of the week, we will process those claims by calculating each user's earned reward amounts. This calculation of determining the amount is done at the end of the week. However, because we burn the tickets at time of claim submission, it is beneficial to the user to wait until Friday to submit a claim transaction. Then, we will generate a list of users and their reward payouts, which will be sent to the dispensation module to trigger the start of the distribution process.

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

