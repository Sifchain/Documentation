---
description: This contains a summarized list of all relevant CLI commands for validators
---

# Validator CLI Commands

### **Validator Set**

* To query the current list of active validators with the following command: `sifnodecli query tendermint-validator-set`
  * This query will show information about all validators in the validator set. Once your validator’s total delegated tokens is higher than the lowest staked validator in this set, your validator will enter the set. 
* You can view your validator’s current staked tokens with: `sifnodecli query staking validator <validator-address>`

### **Delegation**

* Validators can view all unclaimed commission charged to their delegators with the following command: `sifnodecli query distribution commission <validator-address>`

### Block Rewards

* Validators can view all of their unclaimed rewards with the following command:`sifnodecli query distribution validator-outstanding-rewards <validator-address>`

### Claiming & Restaking Block Rewards

* To withdraw rewards, execute one of the below commands:
  * `sifnodecli tx distribution withdraw-rewards <validator-address> --from <address>` 
  * `sifnodecli tx distribution withdraw-rewards <validator-address> --from <address> --commission`
    * Adding the --commission flag will also withdraw all of your commissions as well.
* By default, reward withdrawals will be sent to the source address. This default can be modified with the following command:
  * `sifnodecli tx distribution set-withdraw-address <address> --from <address>`

### **Unbonding**

* In order to execute an unbonding transaction, you will need to run the below command:
  * `sifnodecli tx staking unbond <validator-address> <amount> --from <address>`
    * Specify the validator you want to unbond from \(in this case, your valiadator address\), the amount to unbond, and your address. 
    * If the validator is currently in the active validator set and not jailed, successful submission of this transaction will put the specified amount into the above mentioned unbonding period.
    * You can check the status of an unbonding delegation with the following command:
      * `sifnodecli query staking unbonding-delegation <delegator-address> <validator-address>`

### Slashing

* To see the jailing status in the standard staking validator query: `sifnodecli query staking validator <validator-address>` 
* In order to rejoin the validator set, you must run this transaction: `sifnodecli tx slashing unjail --from <moniker>`
  * After submitting this transaction, simply query your validator information again to see that you have been unjailed.

### Editing your Validator

* There are a few commands that can be run to edit the various details about your validator. These include:
  * `sifnodecli tx staking edit-validator --commission-rate <rate>`
    * Submits a transaction to change a validator’s commission rate. Rate change cannot exceed 'Rate Change Maximum' established at time of validator creation.
  * `sifnodecli tx distribution set-withdraw-address <address> --from <address>`
    * Submits a transaction to change the default recipient address for reward withdrawals

### Other Helpful Queries

* Query Account Balance:
  * `sifnodecli query account <address>`
  * Queries balance for specified account.
* Query Outstanding Validator Rewards:
  * `sifnodecli query distribution validator-outstanding-rewards <validator-address>`
  * Queries all unclaimed rewards for a validator.
* Query Validator Commission:
  * `sifnodecli query distribution commission <validator-address>`
  * Queries all unclaimed commissions charged by a validator.
* Query Delegation Information:
  * `sifnodecli query staking delegation <delegator-address> <validator-address>`
  * Queries info about a delegation between specified delegator and validator.
* Query All Validators:
  * `sifnodecli query staking validators`
  * Queries info for all validators on the chain.
* Querying Delegations to a Validator:
  * `sifnodecli query staking delegations-to <validator-address>`
  * Queries info about all delegations made to a specific validator.

