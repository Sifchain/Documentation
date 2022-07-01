---
description: >-
  Liquidity pools enable you to buy or sell an asset for another asset on a
  crypto-currency exchange. This page highlights how Sifchain uses this concept.
---

# Sifchain Liquidity Pools

A liquidity pool is a primitive for many decentralized cryptocurrency trading platforms including [Uniswap](https://docs.ethhub.io/guides/graphical-guide-for-understanding-uniswap), [Sushiswap](https://boxmining.com/sushi/), [Balancer](https://docs.balancer.finance/getting-started/faq#balancer-pools), Mooniswap (from 1inch), MCDEX, [Thorchain](https://docs.thorchain.org/how-it-works/continuous-liquidity-pools), Perpetual Protocol, [Curve](https://www.curve.fi/stableswap-paper.pdf), [Bancor](https://support.bancor.network/hc/en-us/articles/360000472072-What-Are-Bancor-Liquidity-Pools-) and more. Centralized exchanges have even created a liquidity pool swap program because the returns are so lucrative.‌

Sifchain's liquidity pools are based on Sushiswap with extensibility in mind for potential updates. Rowan will be the settlement token for each pool, meaning each pool will contain Rowan as one asset and an external asset as the other. Sifchain’s swap UI will support swaps between external assets (for example, cMKR:cCOMP) but such transactions will actually require two swaps between two different liquidity pools (for example, cMKR:ROWAN and then ROWAN:cCOMP).‌

Liquidity providers will be able to add liquidity into Sifchain’s liquidity pools where they can earn income. They will be able to add liqudity [asymmetrically](https://medium.com/thorchain/asymmetric-withdrawals-on-bepswap-a6924ed2f28b), meaning they can add only Rowan or only TKN for any token. This is as opposed to Uniswap where users must add equal values of the settlement token (ETH) and the other token (TKN). Liquidity providers will be able to add or remove liquidity whenever they choose.‌

Sifchain allows swappers to send a transaction to a liquidity pool with the amount of tokens they want to give up in exchange for tokens on the other side of the pool. Sifchain uses both an order book and a CLP for trade completion.‌

## Asymmetric Liquidity Pool‌ <a href="#asymmetric-liquidity-pool" id="asymmetric-liquidity-pool"></a>

In many decentralized exchanges, users can add liquidity to liquidity pools and earn a portion of the transaction fees charged to other users who want to swap tokens in the pool. The constraint that most liquidity pools put on liquidity providers is that they must put in an equal value of each token pair. For example, in the ETH/DAI liquidity pool in Uniswap, a user is required to add 2.64 ETH for every 1,000 DAI that is added at the time of this writing. And then based on the amount the user puts into the pool, they then receive a proportionate amount of the fees charged.‌

With Sifchain, users who want to add liquidity to a pool can add any amount of either or both tokens. This is known as adding liquidity asymmetrically, which gives users ultimate flexibility. Based on the amount of tokens in the pool and the amount that the user adds, they will then own a percentage of the entire pool. Sifchain will initially use the same formula to calculate ownership as BEPSwap.

{% hint style="info" %}
**Important Notes** on adding liquidity asymmetrically vs. symmetrically:

The way the Sifchain pooling logic works is that it incentivizes LPs to deposit symmetrically. HOWEVER: LPs should deposit asymmetrically if the pool is already imbalanced.&#x20;

**Asymmetrical** deposits are when a user deposits an unequal value of the two assets to a pool. So for example, let's say a user deposits $1000 of ETH and $0 of ROWAN to the already-balanced ETH/ROWAN pool. The user is given a % ownership of the pool that takes into account the **slip** created in the price. Because of this, the liquidity provider will end up with less than $500 in ETH and less than $500 in ROWAN. The deeper the pool, the closer to a total of $1000 the LP will own.

This means that LPs can get into a situation where they have 'less' than what they added. The ways that LPs can end up with "less" tokens are either through:

1. Them doing asymmetric adds&#x20;
2. From Rowan price shifts

If an LP adds **symmetrically** their ownership is really just going to fluctuate with the price of Rowan and the balance of the pool they're in. These fluctuations should be proportional on each side. For example, if their cUSDT balance is going down, their Rowan balance should be going up and vice versa&#x20;
{% endhint %}

{% hint style="success" %}
In order to help user's with the above asymetrical vs. symmetrical adding of liqudity, we have implemented the following:

* 'Pool Equally' slider: If this is turned on (it is on by default), then we will automatically calculate the non-filled in 'Input' field for you as to where the slipAdjustment = 0% (i.e the amounts added will be done some in a symmetrical way).&#x20;
* A user may choose to turn this 'Pool Equally' slider off. In this case, the user is free to input ANY amount in either field and we will not do any automatic calculations. However, we do want to inform users of cases where the amounts input are causing a significant slip. The rule we are following here is:
*
  * If greater than 20% = Red
  * If between 20% and 10% = Orange
  * If between 1% and 10% = Yellow
  * If less than 1% = No color
* Please see below for a screenshot of this coloring and informational icon.
{% endhint %}

![](<../.gitbook/assets/Screen Shot 2021-08-02 at 3.22.29 PM (1).png>)

### **How does the system ensure that there’s enough liquidity in a pool, if users only have to add one token in the pool and not both?**

The interesting thing about the formula that Sifchain uses to calculate ownership, is that it creates an economic incentive for users to balance the pool. If the pool gets too oversubscribed on one side, the formula gives users an incentive to add liquidity to the other side by giving them a higher ownership % to add to the side that needs more units to balance the pool.

See additional information [here](https://medium.com/sifchain-finance/sifchain-technical-introduction-advantages-of-an-asymmetric-liquidity-pool-93bedae3986c) about the advantages of asymmetric liquidity pools.

## Liquidity Provider Income Determination

The amount of income that liquidity providers can earn is dependent on the below-identified factors.

### 1.) Amount of Liquidity Provided

#### Pool Ownership calculation

Below is the formula used to calculate the units owned by a user when they add Rowan or another asset to the liquidity pool. The Liquidity Provider is then able to withdraw that amount of ownership at any time across either token within the pool.

$$
slipAdjustment = 1 - |\frac{Ra-rA}{(R + r)*(a +A)}|
$$

$$
units = \frac{P(rA+Ra)}{2RA}*slipAdjustment
$$

Definitions:

* r = ROWAN deposited
* a = Asset deposited
* R = ROWAN Balance (before)
* A = Asset Balance (before)
* P = Existing Pool Units

### 2.) Time

This is the length of time a liquidity provider keeps their liquidity in a pool. We reward liquidity providers that keep their liquidity in the pool for longer durations of time.

### **3.)** Fee Revenue

#### Swap Fees

Liquidity Providers also get a share of the swap fees accrued for their contributions to the pool. Pools with higher daily volume generate more swap fees. Sifchain uses Thorchain's slip-based Continuous Liquidity Pool model to calculate trade slip, liquidity fee, and resulting swap.

The liquidity provider is allocated a portion of the fees collected from swappers proportional to their ownership of the pool. For example, If the liquidity provider owns 2% of the pool, they are allocated 2% of the fees collected.

**Potential Price Slippage**

Swappers who are in a hurry to exchange assets will tend to make larger swaps. Larger swaps lead to greater price slips and therefore higher fees.

### Generalized Model of Liquidity Allocation

Sifchain’s [Automated Marker Maker(AMM) Specification](https://hackmd.io/6VK2LSYjRTyeNCoHpVt2hg) is based on a derivation of liquidity pool architecture from first principles. It is important to us that we don’t enforce any formula on users. At launch, Sifchain will use [Thorchain’s slip based fee formula](https://docs.thorchain.org/how-it-works/continuous-liquidity-pools#slip-based-fee-model-clp). In the future, we’re going to update this to allow [governance to control the liquidity pool formula](https://twitter.com/sifchain/status/1319358940090560512?s=20) by voting with their Rowan [on a per liquidity pool basis](https://twitter.com/sifchain/status/1319361777616838659?s=20).

We are currently extending this model to derive the optimum balance between [rewards to validators and rewards to liquidity providers](https://twitter.com/sifchain/status/1320954306632118272?s=20), especially in a regime where we deploy temporary validator subsidy & liquidity mining rewards. So far, our [rebalancing policy](https://hackmd.io/@shrutiappiah/r1itFRrPv) is a vectorized extension of Thorchain’s [Incentive Pendulum](https://docs.thorchain.org/how-it-works/incentive-pendulum) but this is under active research.

#### Rebalancing mechanism for system rewards distribution

Inspired by Thorchain’s incentive pendulum, Sifchain combines liquidity provider rewards and validator block rewards into **system income**. This incentive pendulum keeps the network in a balanced state. It stops the network from becoming unsafe or inefficient by changing the distribution of rewards to both node operators and liquidity.

In comparison, Thorchain’s incentive pendulum uses a scalar to define the ratio of total system income given to each subsystem. This means it is limited to two subsystems (validator subsystem and liquidity provider subsystem). On the other hand, Sifchain uses a vector in which each element is a weight on its subsystem’s income. This means it is extensible to more than two subsystems (for example, Sifchain validator subsystem, Sifchain liquidity provider subsystem, peg zone validator subsystem, an external chain’s liquidity provider subsystem, etc.). Near-term this will be immaterial, but as IBC develops and Sifchain becomes more composable, it will be useful for allowing Sifchain to dynamically change rewards in its two subsystems in response to on-chain activity from other blockchains.

![](<../.gitbook/assets/Screen Shot 2021-01-20 at 12.08.55 PM.png>)

## Liquidity Pools Resources <a href="#liquidity-pools-architecture" id="liquidity-pools-architecture"></a>

While the general Liquidity Pools architecture [documentation can be found here](https://github.com/Sifchain/sifnode/blob/develop/docs/clp/Liquidity%20Pools%20Architecture.md), Sifchain is constantly innovating by releasing new cryptoeconomics feature. For further information on how [PMTP](https://docs.sifchain.finance/project/pmtp) release affects Liquidity Pools, please make sure to check  the [PMTP technical specs](https://hackmd.io/vrCeYGvURZio4yWc-ChYzA).\
\
If you are interested on the technical details, make sure to [check the implementation](https://github.com/Sifchain/sifnode/blob/cff2ed4cfdd55f84d296b5e46d7b63dfa55768e3/x/clp/keeper/calculations.go#L283-L289)
