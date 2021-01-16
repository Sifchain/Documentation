---
description: >-
  Use this page to learn about delegations, why to delegate, and how to
  delegate.
---

# Delegators

## **Introduction**

Delegation is a great way to earn validator income without running your own validator.  If you want to support ROWAN’s crypto-economic security but cannot run your own validator, you can delegate your capital to a validator. Delegators earn validator tokens, minus a commission rate retained by the validator.

The commission fee is used by the validator to sponsor technical improvements to Sifchain. Validators are encouraged to offer reports about their contributions to Sifchain’s technical infrastructure. Delegators are encouraged to select validators based on their ability to support Sifchain’s technology innovations.

## **Delegation Overview**

Any Sifchain user can delegate their tokens to any number of validators on the network. Delegating to a validator entitles the delagator to a share of that validator’s block rewards based on the commission rate \(see below\) set by the validator. Delegating to a validator does not give that validator direct control over the delegator’s funds. However, the delegator does assume the risk of being slashed if the validator misbehaves. 

When performing a delegation, we recommend you do due diligence on the following:

1. Ensure the node validator you are delegating to is one that you trust and have faith to not get slashed. Remember, if you delegate to them and they get slashed, then your delegation will also get slashed.
2. Check these 3 rates of the node validator: 
   1. Commission Rate - This represents the percentage of delegator’s rewards retained by the validator in exchange for providing access to Sifchain’s staking system. For example, if this rate is set to 25%, then you as the delegator will get 75% of the reward while the node validator will get 25%.
   2. Maximum Commission Rate - The node validator can change their commission rate at any time and that change will be represented in 24 hours. The maximum amount they can set their commission rate to is indicated here. For example, if the node validator's maximum rate is set to 100%, then they are able to change their commission rate to 100% at any time.
   3. Maximum Commission Rate Change - This is the maximum daily increase possible. For example, if this is set to 5% then the most a node validator can change their rate by in a single 24 hour period is 5%.
3. The top 100 node validator list and their staked/delegated amounts. It's important to do this because you want the node you are delegating to, to be a part of the network to ensure you are also earning rewards.
4. We recommend that you continuously monitor your delegation and the node validators that you have delegated to.

Below contains a list of commands that you can use to get this information.

## **How to Delegate** 

The delegation process is the same for both validators and delegators; whereas a validator delegating to itself is called a self-delegation. Follow the below steps when executing a delegation:

### Prerequisites  

* You have a Sifchain address. To get a Sifchain address, you can do one of the below two options:
  * Access the Sifchain-Dex-UI \(coming soon!\) and create a new address through the Keplr Wallet Integration. 
  * Run Command `sifnodecli keys add <name>` .  This command will give you your: address, public key, and mnemonic phrase. 
* You have ROWAN to delegate. 

### Delegate

* 1\) In order to execute a delegation, you will need to do get the node validator address you are wanting to delegate to. You can do this by simply reaching out to your desired Node Operator and asking for their address, or you can query the network to get a list of all node validators by running the following command:
  * `sifnodecli query staking validators`
    * This will return a list of all validators \(whether or not they are included in the top 100\). 
* 2\) Now you can  delegate tokens, run the following command:
  * `sifnodecli tx staking delegate <validator-address> <amount> --from <address>`
    * You’ll need to specify the address of the validator you’re delegating to, the amount you are delegating, and the address holding the tokens.
* 2\) After submitting a delegation transaction you can check your delegation with:
  * `sifnodecli query staking delegation <delegator-address> <validator-address>`
    * Using this command with the validator address you used in the delegate command will show you information for your delegation to that validator.

### Consolidated list of Commands

* See a list of the top 100 staked validators:  `sifnodecli query tendermint-validator-set`
* See a list of all validators and their commission rates:  `sifnodecli query staking validators`
  * The validators in this list with the status '2' means they are in the top 100.
* Execute a new delegation: `sifnodecli tx staking delegate <validator-address> <amount> --from <address>`
* See the status of a previous delegation: `sifnodecli query staking delegation <delegator-address> <validator-address>`
* See a list of all delegations associated with your address: ****`sifnodecli query staking delegations <delegator-address>`

##  **Unbond an existing delegation**

If you want to unbond an existing delegation, you can follow the below steps:

* 1\) Submit an unbond transaction:
  * `sifnodecli tx staking unbond <validator-address> <amount> --from <address>` 
    * Specify the validator you want to unbond from, the amount to unbond, and your delegator address. If the validator is currently in the active validator set and not jailed, successful submission of this transaction will put the specified amount of the delegation into an unbonding period. The unbonding period is currently set to 21 days, during which time the tokens will not be usable and will still be susceptible to slashing. After the unbonding period the tokens will be fully released to the source address.
  * 2\) Check the status of an existing unbond transaction:
    * `sifnodecli query staking unbonding-delegation <delegator-address> <validator-address>`

**Additional Notes:**

* If a validator recently left the active validator set they will be in their own unbonding period. If a delegator unbonds their delegations at this time they will only have to wait as long as the remaining time in the validator’s unbonding period. To view this information about the validator, execute the following command:
  * `sifnodecli query staking validator <validator-address>.`
* If the validator is not in the active set of validatores and is not in an unbonding period, delegators will receive their tokens immediately after submitting an unbond transaction.

## **Redelegate**

Delegators can move an existing delegation from one validator to another without waiting through an unbonding period. To do this, execute the following command:

* `sifnodecli tx staking redelegate <src-validator-address> <dst-validator-address> <amount> --from <key>`
  * This will immediately move the specified amount from one validator to another.



