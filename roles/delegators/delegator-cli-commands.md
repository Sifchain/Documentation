---
description: This contains a summarized list of all relevant CLI commands for delegators
---

# Delegator CLI commands

## Delegate

* 1\) In order to execute a delegation, you will need to do get the node validator address you are wanting to delegate to. You can do this by simply reaching out to your desired Node Operator and asking for their address, or you can query the network to get a list of all node validators by running the following command:
  * `sifnoded query staking validators`
    * This will return a list of all validators \(whether or not they are included in the top 100\). 
* 2\) Now you can  delegate tokens, run the following command:
  * `sifnoded tx staking delegate <validator-address> <amount> --from <address>`
    * You’ll need to specify the address of the validator you’re delegating to, the amount you are delegating, and the address holding the tokens.
* 2\) After submitting a delegation transaction you can check your delegation with:
  * `sifnoded query staking delegation <delegator-address> <validator-address>`
    * Using this command with the validator address you used in the delegate command will show you information for your delegation to that validator.

### Consolidated list of Commands

* See a list of the top 100 staked validators:  `sifnoded query tendermint-validator-set`
* See a list of all validators and their commission rates:  `sifnoded query staking validators`
  * The validators in this list with the status '2' means they are in the top 100.
* Execute a new delegation: `sifnoded tx staking delegate <validator-address> <amount> --from <address>`
* See the status of a previous delegation: `sifnoded query staking delegation <delegator-address> <validator-address>`
* See a list of all delegations associated with your address: ****`sifnoded query staking delegations <delegator-address>`

## **Rewards**

### **View**

* Delegators can view their unclaimed rewards with the following commands: 
  * `sifnoded query distribution rewards <delegator-address>` 
  * `sifnoded query distribution rewards <delegator-address> <validator-address>`
    * The first command will show all rewards for the specified delegator. The second will show only delegation rewards from the specified validator.

### Withdraw

* Rewards must be claimed manually. The following command will withdraw rewards from a delegation to the specified validator:
  * `sifnoded tx distribution withdraw-rewards <validator-address> --from <address>` 
* Delegators can also withdraw **all** outstanding rewards from **all** of their delegations with the following command:
  * `sifnoded tx distribution withdraw-all-rewards --from <address>`
* By default, reward withdrawals will be sent to the source address. This default can be modified with the following command:
  * `sifnoded tx distribution set-withdraw-addr <address> --from <address>`

## **Unbond an existing delegation**

If you want to unbond an existing delegation, you can follow the below steps:

* 1\) Submit an unbond transaction:
  * `sifnoded tx staking unbond <validator-address> <amount> --from <address>` 
    * Specify the validator you want to unbond from, the amount to unbond, and your delegator address. If the validator is currently in the active validator set and not jailed, successful submission of this transaction will put the specified amount of the delegation into an unbonding period. The unbonding period is currently set to 21 days, during which time the tokens will not be usable and will still be susceptible to slashing. After the unbonding period the tokens will be fully released to the source address.
  * 2\) Check the status of an existing unbond transaction:
    * `sifnoded query staking unbonding-delegation <delegator-address> <validator-address>`

**Additional Notes:**

* If a validator recently left the active validator set they will be in their own unbonding period. If a delegator unbonds their delegations at this time they will only have to wait as long as the remaining time in the validator’s unbonding period. To view this information about the validator, execute the following command:
  * `sifnoded query staking validator <validator-address>.`
* If the validator is not in the active set of validators and is not in an unbonding period, delegators will receive their tokens immediately after submitting an unbond transaction.

## **Redelegate**

Delegators can move an existing delegation from one validator to another without waiting through an unbonding period. To do this, execute the following command:

* `sifnoded tx staking redelegate <src-validator-address> <dst-validator-address> <amount> --from <key>`
  * This will immediately move the specified amount from one validator to another.



