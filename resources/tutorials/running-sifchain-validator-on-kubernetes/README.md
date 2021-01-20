---
description: >-
  Reference this document for getting Sifnode setup and starting the process to
  becoming a validator in the Sifchain Network
---

# Running Sifnode & Becoming a Validator

## Prerequisites <a id="9cbf"></a>

* Make sure your provisioned EC2 machine meets the following requirements:
  * **Hardware:**
    * Minimum**:** 2 vCPU, 4 GB RAM
    * Recommended: 4vCPU, 8 GB RAM
  * **Storage**:
    * Minimum: 50GB SSD
    * Recommended: &gt;= 100 GB SSD. 200GB to be on the safer side.
    * Notes:
      * An archival node \(pruning = "nothing" \) grows at a rate of ~50 GB per month
      * A fully pruning node \(pruning = "everything" \) grows at a rate of ~10 GB per month
      * A default pruning node \(\`pruning = “default”\) grows at a rate of ~20 GB per month

### Setting up your node

Please reference on of the two sub-pages for guides on how to setup the Sifchain network and your node:

* [Running Sifnode on your Ubuntu server ](https://docs.sifchain.finance/resources/tutorials/running-sifchain-validator-on-kubernetes/running-sifnode-on-your-ubuntu-server)\(EC2/Digital Ocean or local\)
* [Running Sifnode on Kubernetes ](https://docs.sifchain.finance/resources/tutorials/running-sifchain-validator-on-kubernetes/running-sifnode-on-kubernetes)\(**recommended**\)

### Stake your Node:

Now that you have your node up and running and you have ROWAN to stake with, you must now execute the following command:

* `sifnodecli tx staking create-validator` 
  * In order to execute this command, there are several decisions that must be made in relation to your node. Some of these settings will not be editable after creation \(pointed out below\), so please be sure about the values you are setting:
    * **commission-max-change-rate &lt;max-rate-change&gt;**
      * This is the most that you will be able to change your commission rate at a time. This value IS NOT editable after validator creation. Commission rates can be changed only once every 24 hours.
    * **commission-max-rate &lt;max-rate&gt;**
      * This is the highest rate that your validator node will be able to charge. This value IS NOT editable after validator creation.
    * **commission-rate &lt;rate&gt;**
      * This is the starting commission rate that your validator node will charge its delegators. This value IS editable after validator creation.
    * **amount &lt;amount&gt;** 
      * This is the amount of your starting self-delegation. This can be both unbonded and added to later.
    * **pubkey $\(sifnoded tendermint show-validator\)** 
      * This is the public validator key associated with your node.
    * **moniker &lt;moniker&gt;**
      * This is the publicly viewable name of your node.
    * **chain-id &lt;chain-id&gt;**
      *  This is the identifier of the network the node is connecting to.
    * **min-self-delegation 1** 
      * This is the minimum number of tokens that the node must delegate to itself.
    * **gas auto** 
      *  ****This is the amount of gas submitted for the create validator transaction.
    * **from &lt;moniker&gt;** 
      * This is a reference to the signer of this transaction \(your validator address/moniker\).
    * **keyring-backend file**
      * This specifies the location of your node’s keyring.
* Next, you can verify that this was executed correctly by running this command: `sifnodecli query staking validator <validator-address> .` This will return information about your validator.

After you have setup your node and successfully staked it with ROWAN, you are now considered eligible to be a part of Sifchain's validator set. Please reference our [guide on being a Validator here for additional information](https://docs.sifchain.finance/roles/validators).   


