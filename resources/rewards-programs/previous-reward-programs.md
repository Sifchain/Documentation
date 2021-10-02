---
description: >-
  The below programs are fully completed at this point. Please use this as a
  simple reference on previously run programs
---

# Previous Reward Programs

## .39 Liquidity Mining and Validator Subsidy Rewards on Sifchain

Liquidity mining rewards are rewards given for adding liquidity in the Sifchain [liquidity pool subsystem](https://docs.sifchain.finance/roles/liquidity-providers), whereas validator subsidy rewards are provided for staking or [delegating](https://docs.sifchain.finance/roles/delegators) to the [validator subsystem](https://docs.sifchain.finance/roles/validators).

#### Liquidity Mining & Validator Subsidy Rewards Introduction

Sifchain is running a liquidity mining program. There are 45 million ROWAN being initially allocated to this current rewards program. The eligibility window for the program started on Feb 19, 2021 and is set to end on June 30, 2021. All liquidity and stake that is added to Sifchain during the eligibility window will be eligible for LM and VS Rewards. Rewards will continue to accrue up until August 4th, 2021 \(regardless if a user has added liquidity early or late\).

For LM rewards, the total rewards in the program are split between the different liquidity providers based on the proportion of total liquidity in the system that they have been providing over the duration of the program. For VS rewards, the total rewards in the program are split between the different users who have provided stake or delegations. Their total possible reward grows the longer they keep their liquidity in the system, up to a maximum of 4 months.

#### Updates to our LM and VS Program, valid as of July 27, 2021

* On the very last block of .39 before we migrate to .42, we will take a snapshot of the current state of participants within the LM/VS program. This snapshot will include:
  * Reward Type: LM or VS
  * Each participant's total claimable amount as of August 4th
  * Each participant's total fully projected amount as of August 4th
  * Each participant's full maturation date
    * Significance of the August 4th date: This is the date when rewards stop accruing. So by choosing this date for the claimable and fully projected amount, we ensure that all users have the ability to be paid out in full.
* We will use this information to determine a payment schedule for each participant.
* First, we determine each participant's **Payment Schedule dates**. We will have 3 various 'Payout Schedules' that a participant can fall into, as determined based on their full maturation date. Those payout schedules are as follows:
  * Payout Schedule \#1: Full Maturation Date falls before September 1. Payout Dates:
    * August 6
    * August 13
  * Payout Schedule \#2: Full Maturation Date falls between: September 1 - October 1. Payout Dates:
    * August 6
    * August 13
    * August 20
    * August 27
    * September 3
    * September 10
  * Payout Schedule \#3: Full Maturation Date falls between October 1 - End of the program. 12 Payout Dates:
    * August 6
    * August 13
    * August 20
    * August 27
    * September 3
    * September 10
    * September 17
    * September 24
    * October 1
    * October 8
    * October 15
* Next, we will determine how much should be paid out to each participant on those dates. To do this, we take the:
  * a\) claimable amount as of August 4th \(ie: CurrentClaimable\) and
  * b\) your current outstanding previously claimed amount \(ie ClaimedRewardsSinceFinalDispensation\) and 
  * c\) total fully projected amount as of August 4th \(ie: MaturatedRewardsTotal\),

And we create a payment schedule using the following logic:

* MaturatedRewardsTotal - CurrentClaimable = Weekly Regular Distribution Total \(wrdTotal\).
* We take the wrdTotal and divide that by the number of payment dates to get a per week distribution amount.

We take this per week distribution amount and create a payment schedule as such:

* First payment schedule date = CurrentClaimable + ClaimedRewardsSinceFinalDispensation +

   per week distribution amount.

* Remaining payment schedule dates = per week distribution amount.
* To illustrate the above logic with a few examples:
  * Example Scenario A, Payment Schedule \#1:
    * User: sif123
    * Full maturation date = August 20
    * MaturatedRewardsTotal: 125
    * CurrentClaimable: 25
    * WRDTotal: 100
      * Math is MaturatedRewardsTotal - currentClaimable = wrdTotal
    * Payout dates and amounts:
      * August 6 = 25\(current claimable amount\) + 50\(100/2 weeks of WRD\)
      * August 13 = 50
  * Example Scenario B, Payment Schedule \#2:
    * User: sif456
    * Full maturation date = September 20
    * MaturatedRewardsTotal: 100000
    * CurrentClaimable: 30000
    * WRDTotal: 70000
      * Math is MaturatedRewardsTotal - currentClaimable = wrdTotal
    * Payout dates and amounts:
      * August 6 = 30000\(current claimable amount\) + 11666\(70000/6 weeks of WRD\)
      * August 13 = 11666
      * August 20 = 11666
      * August 27 = 11666
      * September 3 = 11666
      * September 10 = 11666
  * Example Scenario C, Payment Schedule \#3:
    * User: sif789
    * Full maturation date = October 20
    * MaturatedRewardsTotal: 200000
    * CurrentClaimable: 80000
    * WRDTotal: 120000
      * Math is MaturatedRewardsTotal - currentClaimable = wrdTotal
    * Payout dates and amounts:
      * August 6 = 80000\(current claimable amount\) + 10909\(120000/11 weeks of WRD\)
      * August 13 = 10909
      * August 20 = 10909
      * August 27 = 10909
      * September 3 = 10909
      * September 10 = 10909
      * September 17 = 10909
      * September 24 = 10909
      * October 1 = 10909
      * October 8 = 10909
      * October 15 = 10909
* In order to maintain eligibility for this new program and for each payout week, participants must follow the below rules:
  * For LM, a user cannot remove any liquidity at any point before their final payment date.
  * For VS, a user cannot remove any of their stake or undelegate their stake before their final payment date.
  * If a participant does any of the above actions, they have disqualified themselves from future payouts. Participants, if disqualified, will not be eligible to earn any additional payouts from that point forward.
* With these new rules, there will be no need to 'manually claim' any amounts. The distributions will happen automatically on the specified payment schedule dates.
* For additional specific details on exact payout amounts, please reference this [google sheet](https://docs.google.com/spreadsheets/d/1f-ibZyx5O2f1wsNxvi56Kg8fkdys_DVmwhf7mjKDrDU/edit?usp=sharing) where you can filter by your address and see your specific payout schedule details.
  * Additional help on columns:
    * **Address** - Your sifchain address
    * **reward\_type** - The reward type \(either LM or VS\)
    * **claimablerewardstotal** - claimable amount as of August 4th
    * **maturatedrewardstotal** - total fully projected amount as of August 4th
    * **maturitydate** - Full maturation date 
    * **weekly\_regular\_distribution\_total** - MaturatedRewardsTotal - CurrentClaimable = Weekly Regular Distribution Total
    * **per\_week\_distribution\_amount** - Weekly Regular Distribution Total / num\_weeks
    * **num\_weeks** - Number of payment dates as determined by user's maturity date
    * **distribution\_date** - Your determined Payment schedule \(see above for these schedules\)
    * **claimedrewardssincefinaldispensation** - Your current outstanding previously claimed amount
    * **firstweekdistribution\_amount** - The amount that will be paid out on your first reward distribution date. This is CurrentClaimable + ClaimedRewardsSinceFinalDispensation +

       per week distribution amount.

The below covers how we determined the amounts that were used for user's LM and VS rewards prior to the July 27th 2021 adjustment in our program. Please use the below as additional reference material to help understand the entirety of the .39 LM/VS program.

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

* Users could claim their rewards at any time by resetting their tickets. Whenever a ticket is reset, it will release its rewards to the user based on its current multiplier. Reset tickets then start empty with a 25% multiplier again.

**Withdrawing Liquidity or Stake**

* Whenever a user withdraws their liquidity or stake, they will automatically burn an equivalent amount of tickets to cover the withdrawal. Tickets associated with these rewards will be automatically reset. Again, whenever a ticket is reset, it will release its rewards to the user based on its current multiplier. Reset tickets then start empty with a 25% multiplier again. Tickets will be burned in order from lowest multiplier to highest in order to preserve a user's best tickets with highest multipliers.
* When a user withdraws their liquidity or their stake, it will not automatically submit a claim for the associated rewards. While it will reset those reward tickets, a user will still need to go into the DEX and manually submit a claim transaction to fully claim those rewards.

#### Impermanent Loss Mitigation

We have implemented an Impermanent Loss \(IL\) Mitigation. If a user realizes IL, the user will continue to earn rewards based on the realized IL amount. These values are based on the Rowan value of a user’s add.

For example, imagine a user deposits 50K Rowan and 50K Rowan worth of USDT for a total of 100K Rowan worth of assets into a Sifchain liquidity pool. Let’s say this amount drops to 80K worth of Rowan due to price fluctuations. The user removes all 80K Rowan worth of assets. That user will continue to earn LM rewards based off of the 20K Rowan worth of assets that was lost due to IL \(the 20k here is called the ‘IL amount’\). The IL amount ONLY comes into play if a user removes their liquidity and realizes IL. If that user were to add additional liquidity after realizing this IL, their LM Reward eligibility amount would be the sum of their IL amount + any added liquidity amounts.

#### FAQ for LM and VS Rewards Programs

* How much ROWAN has been allocated to each program?
  * 45M ROWAN tokens are allocated to each LM rewards and VS rewards \(90M ROWAN in total\). Note that the liquidity mining rewards and the validator subsidy rewards are separate, as we encourage people to contribute to both programs as they provide different utilities for the system.
* During which time periods can I add liquidity/stake/delegate and earn rewards?
  * During the program eligibility dates of 02/19/2021 - 06/30/2021. We highly recommend that you add as much as you can during this time period to both our liquidity pools and stake/delegate to earn maximum rewards across both programs. 
* Can I claim just a portion of my rewards?
  * No. The rewards are automatically disbursed on the set payment dates.
* When can I claim my rewards?
  * No need to claim any rewards! We will dispense them automatically.
* How can I get disqualified?
  * For LM, a user cannot remove any liquidity at any point before their final payment date.
  * For VS, a user cannot remove any of their stake or undelegate their stake before their final payment date.
    * If a participant does any of the above actions, they have disqualified themselves from future payouts. Participants, if disqualified, will not be eligible to earn any additional payouts from that point forward.
* Where can I see my payment schedule? 
  * You can see details on this [google sheet](https://docs.google.com/spreadsheets/d/1f-ibZyx5O2f1wsNxvi56Kg8fkdys_DVmwhf7mjKDrDU/edit?usp=sharing).
* How are commission-based rewards handled in this new payout schedule?
  * For validator subsidy rewards that are based on the commission of their delegations: we are assuming that ALL delegators allow their rewards to fully mature, which means that all validators will receive their associated VS rewards based on the assumption that these delegators wait their time \(which maximizes the benefit to validators\). This will be paid out in a\) their 1st week \(as a claimable amount if it is considered claimable at this time\), and b\) will also be split among their future payment schedule.

### 

