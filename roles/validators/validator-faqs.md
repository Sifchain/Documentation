---
description: Frequently asked questions about being a validator in Sifchain
---

# Validator FAQs

## What are the approximate costs of setting up a Validator?

The cost of being a validator is around $100-$200/month. The expected time commitment is around 5-10  hours/month. 

## What is the benefit of using Kubernetes over non-Kubernetes infrastructure, if any?

Kubernetes is best for cluster management. It's possible to do makeshift cluster management on your own, although Kubernetes is now a standard for cluster orchestration among DevOps engineers. We recommend using Kubernetes infrastructure.

## As a Validator, for storage, which kind of node type should I run? \(Archival node \| Fully pruning node \| Default pruning node\)

At Sifchain we believe that the Archival is most complete, but feel free to make a different choice based on personal preferences.

## How are Validators paid?

Validators are paid via Block Rewards. Please find additional information [here](https://docs.sifchain.finance/roles/validators#block-rewards). Validators will also earn additional rewards via our Validator Subsidy Program, which is referenced [here](https://docs.sifchain.finance/roles/validators#liquidity-mining-rewards).

The calculation for this is as follows:

* **Validator & Delegation Rewards** = \[30M Rowan / \(total\_rowan\_staked\_and\_delegated - total\_rowan\_staked\_by\_sifchain\] + Block Rewards \(Variable\).

## Are rewards subject to any locking periods?

Some rewards earned by Validators are subject to lock-up periods. We're currently designing this and will provide more information later.

## Is there a risk of my stake being slashed? If yes, where can we read more on this?

Yes, Validators are held accountable for their proper participation in our network and are therefore eligible to be slashed for misbehavior. For slashable conditions, please refer to additional information [here](https://docs.sifchain.finance/roles/validators#slashing).

## Are there un-bonding periods that I am held to when I decide to un-stake my Validator node?

Our un-bonding period is currently set to 21 days. More information can be found [here](https://docs.sifchain.finance/roles/validators#unbonding). 

## Will node operators be able to stake their unvested tokens to become a Validator?

This is currently in discussion by our team. We will provide additional information around this once we have it.

