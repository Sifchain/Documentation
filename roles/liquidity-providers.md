# Liquidity Providers

Liquidity providers provide assets to the Sifchain liquidity pools. They are compensated with swap fees and system rewards. Compensation is affected by a number of factors related to the pool and the state of the network.

Liquidity providers are able to deposit any token Sifchian supports to the appropriate pool. Due to Sifchain liquidity pools being asymmetrically, users can add either Rowan or the token \(TKN\) the pool comprises of. This is as opposed to Uniswap where users must add equal values of the settlement token \(ETH/UNI\) and the other token \(TKN\).  Liquidity providers are able to add or remove liquidity whenever they choose. 

LP\(Liquidity Provider\) income is decided by the following factors 

## 1.\) Amount of Liquidity Provided

#### Pool Ownership calculation

Below is the formula used to calculate the units owned by a user when they add Rowan or another asset to the liquidity pool.

$$
slipAdjustment = 1 - |\frac{Ra-rA}{(2R + r)*(a +A)}|
$$

$$
units = \frac{P(rA+Ra)}{2RA}*slipAdjustment
$$

```text
Where
r = rowan deposited‌
a = asset deposited‌
R = Rowan Balance (before)‌
A = Asset Balance (before)‌
P = Existing Pool Units‌
```

The liquidity provider is allocated a portion of the fees collected from swappers proportional to their ownership of the pool. For example, If the liquidity provider owns 2% of the pool, they are allocated 2% of the fees collected.

## 2.\) Time

 Length of time a liquidity provider keeps their liquidity in a pool

## **3.\)** Fee Revenue

#### Swap Fees

LPs also get a share of the swap fees in a pool. Pools with higher daily volume generate more swap fees.

**Price Slippage**

Swappers who are in a hurry to exchange assets will tend to make larger swaps. Larger swaps lead to greater price slips and therefore higher fees.

## 4.\) Liquidity Mining Rewards

The amount of liquidity mining rewards given to a liquidity provider as a bonus for participating in the network in its early stages 

