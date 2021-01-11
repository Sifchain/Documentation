# Validators

### **Validators, Delegators, and Staking**

#### **Validator Set**

Sifchain’s active validator set consists of the 100 top by stake validator nodes. The calculated stake includes both the validator’s individual stake and all of its delegations. This validator set is refreshed every block, so changes to a validator’s total stake that would shift it in or out of the validator set will be reflected in consensus immediately. There is no explicit minimum stake amount required to be a validator on Sifchain. The amount staked by the lowest validator in the set serves as an implicit minimum.

#### **Delegation**

Any Sifchain user can delegate their tokens to any number of validators on the network. Delegating to a validator entitles the user to a share of that validator’s block rewards based on the commission rate \(see below\) set by the validator. Delegating to a validator does not give that validator direct control over the delegator’s funds. However, the delegator does assume the risk of being slashed \(see below\) if the validator misbehaves. ****

When performing a delegation, we recommend you do due diligence on the following:

1. Ensure the node validator you are delegating to is one that you trust and have faith to not get slashed. Remember, if you delegate to them and they get slashed, then your delegation will also get slashed.
2. Check these 3 rates of the node validator: 
   1. Commission Rate - This represents the percentage of delegator’s rewards retained by the validator in exchange for providing access to Sifchain’s staking system. For example, if this rate is set to 25%, then you as the delegator will get 75% of the reward while the node validator will get 25%.
   2. Maximum Commission Rate - The node validator can change their commission rate at any time and that change will be represented in 24 hours. The maximum amount they can set their commission rate to is indicated here. For example, if the node validator's maximum rate is set to 100%, then they are able to change their commission rate to 100% at any time.
   3. Maximum Commission Rate Change - This is the maximum daily increase possible. For example, if this is set to 5% then the most a node validator can change their rate by in a single 24 hour period is 5%.
3. The top 100 node validator list and their staked/delegated amounts. It's important to do this because you want the node you are delegating to, to be a part of the network to ensure you are also earning rewards.
4. We recommend that you continuously monitor your delegation and the node validators that you have delegated to.

#### **Fees**

Validators are responsible for setting their own minimum fee price. This price is the minimum fee amount that the validator’s node will accept when receiving a transaction or adding a transaction to a block for proposal.

#### Block Rewards

Validator block rewards consist of network fees from transactions. These fees are pooled globally and distributed to validators proportionally based on voting power \(i.e. stake\). The validator that proposed a particular block also receives a bonus between 1% and 5% of the fees collected in that block. Fees are collected and added to the reward pool every block.

#### Claiming & Restaking Block Rewards

Validators and delegators must manually submit a transaction to withdraw their rewards from the reward pool. Because of this, automatic redelegation of rewards is not possible on-chain. Validators and delegators are therefore responsible for withdrawing and redelegating their rewards manually when desired.  
  
When withdrawing, all of the claimant’s available rewards are withdrawn from the reward pool. Delegators can, however, withdraw only the rewards from a particular validator if they choose.

#### **Unbonding**

Validators and delegators can submit an unbonding transaction to remove their staked tokens. Once the transaction is processed the staked tokens will enter an unbonding period of 3 days. During the unbonding period the staked tokens are still susceptible to slashing penalties. After the unbonding period the tokens will be fully released to the user.

#### Slashing

Sifchain currently only penalizes validators for downtime. If a validator misses more than 50 blocks in any 100 block window they will be slashed and jailed. The slash penalty for downtime is 1% of the validator’s total stake including delegations; these tokens will be burned. The offending validator will be jailed for 10 minutes. While the validator is jailed they are removed from the validator set and cannot participate in consensus and thus will not receive block rewards. After the 10 minute jail period is over the validator must submit a transaction to unjail, at which point they will rejoin consensus.

#### Future Additions

* **Double Sign Slashing:** We plan to add functionality to slash validators for double sign infractions. The penalty for a double sign infraction will be a 5% slash of the offender’s stake and a permanent jail and tombstone. This means that the validator will be unable to ever rejoin the validator set.
* **Inflationary Block Rewards:** Inflationary block rewards will be minted per block based on a schedule set by governance. These rewards will be added to and distributed by the same global reward pool as fee rewards.
* **Governance**: In the future, validators will be able to participate in governance proposals and votes that will alter the functionality of the chain.
* **Dynamic Rebalancing Policy:** We plan to add a system that will dynamically rebalance rewards between the validator system outlined above and Sifchain’s liquidity pool system rewards. The goal of the policy is to prevent one system’s rewards from becoming more profitable than the other, which would over-incentivize users to participate in that system and lead to an imbalance in the chain.

