---
description: >-
  Use this page to learn about delegations, why to delegate, and how to
  delegate.
---

# Delegators

## **Introduction**

Delegators are considered to be a secondary set of actors in the validator subsystem economy. Delegators earn shares of claims to rewards with their delegated stake tokens. Delegators incur a slashing risk depending upon their choice of validator.

Delegation is a great way to earn validator income without running your own validator.  If you want to support ROWAN’s crypto-economic security but cannot run your own validator, you can delegate your capital to a validator. Delegators earn validator tokens, minus a commission rate retained by the validator.

The commission fee is used by the validator to sponsor technical improvements to Sifchain. Validators are encouraged to offer reports about their contributions to Sifchain’s technical infrastructure. Delegators are encouraged to select validators based on their ability to support Sifchain’s technology innovations.

## **Delegation Overview**

Any Sifchain user can delegate their tokens to any number of validators on the network. Delegating to a validator entitles the delagator to a share of that validator’s block rewards based on the commission rate (see below) set by the validator. Delegating to a validator does not give that validator direct control over the delegator’s funds. However, the delegator does assume the risk of being slashed if the validator misbehaves.&#x20;

When performing a delegation, we recommend you do due diligence on the following:

1. Ensure the node validator you are delegating to is one that you trust and have faith to not get slashed. Remember, if you delegate to them and they get slashed, then your delegation will also get slashed.
2. Check these 3 rates of the node validator:&#x20;
   1. Commission Rate - This represents the percentage of delegator’s rewards retained by the validator in exchange for providing access to Sifchain’s staking system. For example, if this rate is set to 25%, then you as the delegator will get 75% of the reward while the node validator will get 25%.
   2. Maximum Commission Rate - The node validator can change their commission rate at any time and that change will be represented in 24 hours. The maximum amount they can set their commission rate to is indicated here. For example, if the node validator's maximum rate is set to 100%, then they are able to change their commission rate to 100% at any time.
   3. Maximum Commission Rate Change - This is the maximum daily increase possible. For example, if this is set to 5% then the most a node validator can change their rate by in a single 24 hour period is 5%.
3. The top 100 node validator list and their staked/delegated amounts. It's important to do this because you want the node you are delegating to, to be a part of the network to ensure you are also earning rewards.
4. We recommend that you continuously monitor your delegation and the node validators that you have delegated to.

Below contains a list of commands that you can use to get this information.

## **How to Delegate**&#x20;

The delegation process is the same for both validators and delegators; whereas a validator delegating to itself is called a self-delegation. Follow the below steps when executing a delegation:

### Prerequisites &#x20;

* You have a Sifchain address. To get a Sifchain address, you can do one of the below options:
  1. Use the Sifchain-DEX-UI and use our Keplr Wallet integration to setup a new Sifchain address. For directions on this, please refer to our instructions [here](https://docs.sifchain.finance/resources/sifchain-dex-ui#create-or-import-a-sifchain-address-with-keplr-wallet).
  2. You have ROWAN to delegate.&#x20;

### Ways to Delegate &#x20;

* Go to the [Keplr Dashboard](https://wallet.keplr.app/#/dashboard), select Sifchain on the left hand side navigation bar, and click 'Stake'. This will take you to the list of validators in our network. Click on the 'manage' link beside any of them you are interested in delegating to (or managing your existing delegations with). From here you can manage your delegations accordingly.
* Have a look at the Delegator CLI commands page for all relevant commands that can be run in order to execute and manage a delegation.

After you have successfully submitted a delegation there are several actions that you are able to do:

* **Claim your earned Rewards**: Rewards must be claimed manually.
* **Unbond your delegation:** If the validator is currently in the active validator set and not jailed, successful submission of this transaction will put the specified amount of the delegation into an unbonding period. The unbonding period is currently set to 21 days, during which time the tokens will not be usable and will still be susceptible to slashing. After the unbonding period the tokens will be fully released to the source address.
* **Redelegate your existing delegation to a different node operator**: Delegators can move an existing delegation from one validator to another without waiting through an unbonding period.&#x20;

