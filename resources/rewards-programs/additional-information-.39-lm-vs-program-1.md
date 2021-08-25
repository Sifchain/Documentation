# Additional Information: .39 LM/VS Program

### Liquidity Mining and Validator Subsidy Rewards on Sifchain

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

