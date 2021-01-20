# Liquidity Providers

## Introduction

Liquidity providers provide assets to the Sifchain liquidity pools. They are compensated with swap fees and system rewards. Compensation is affected by a number of factors related to the pool and the state of the network.

Liquidity providers are able to deposit any token Sifchian supports to the appropriate pool. Anyone can create a CLP by pooling Rowan and a new token into a pool initialization transaction. The price of the new token is set based on the amount of Rowan pooled. Sifchain enforces a minimum CLP size but multiple depositors can contribute to the creation of a single CLP.

If users are simply adding to an already existing liquidity pool, they may do so asymmetrically. This means users can add either Rowan or the token \(TKN\) the pool comprises of. This is as opposed to Uniswap where users must add equal values of the settlement token \(ETH/UNI\) and the other token \(TKN\).  Liquidity providers are able to add or remove liquidity whenever they choose. 

## Liquidity Provider Income Determination

### 1.\) Amount of Liquidity Provided

#### Pool Ownership calculation

Below is the formula used to calculate the units owned by a user when they add Rowan or another asset to the liquidity pool.

$$
slipAdjustment = 1 - |\frac{Ra-rA}{(2R + r)*(a +A)}|
$$

$$
units = \frac{P(rA+Ra)}{2RA}*slipAdjustment
$$

Definitions:

* r = ROWAN deposited
* a = Asset deposited
* R = ROWAN Balance \(before\)
* A = Asset Balance \(before\)
* P = Existing Pool Units

The liquidity provider is allocated a portion of the fees collected from swappers proportional to their ownership of the pool. For example, If the liquidity provider owns 2% of the pool, they are allocated 2% of the fees collected.

### 2.\) Time

 Length of time a liquidity provider keeps their liquidity in a pool.

### **3.\)** Fee Revenue

#### Swap Fees

Liquidity Providers also get a share of the swap fees accrued for their contributed to pool. Pools with higher daily volume generate more swap fees. Sifchain uses Thorchain's slip-based Continuous Liquidity Pool model to calculate trade slip, liquidity fee, and resulting swap.

**Potential Price Slippage**

Swappers who are in a hurry to exchange assets will tend to make larger swaps. Larger swaps lead to greater price slips and therefore higher fees.

## Liquidity Mining Rewards

Sifchain will run a 12-week liquidity mining program for poolers, in order to incentivize early adopters. Rewards are subject to change based on evaluations of the network from the Sifchain core team, community feedback, and governance over time.

To learn more about this program and what you can expect to earn as part of this program, reference our announcement article [here, section 'Liquidity Mining for Poolers'.](https://medium.com/sifchain-finance/uses-for-rowan-the-polyvalent-token-for-omni-chain-decentralized-exchange-dex-3207e7f70f02)

