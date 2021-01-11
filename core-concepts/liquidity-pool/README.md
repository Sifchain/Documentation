# Sifchain Liquidity Pools

A liquidity pool is a primitive for many decentralized cryptocurrency trading platforms including [Uniswap](https://docs.ethhub.io/guides/graphical-guide-for-understanding-uniswap), [Sushiswap](https://boxmining.com/sushi/), [Balancer](https://docs.balancer.finance/getting-started/faq#balancer-pools), Mooniswap \(from 1inch\), MCDEX, [Thorchain](https://docs.thorchain.org/how-it-works/continuous-liquidity-pools), Perpetual Protocol, [Curve](https://www.curve.fi/stableswap-paper.pdf), [Bancor](https://support.bancor.network/hc/en-us/articles/360000472072-What-Are-Bancor-Liquidity-Pools-#:~:text=Liquidity%20pools%20perform%20autonomous%2C%20peer,holding%20its%20%E2%80%9Cpool%20token%E2%80%9D.%29) and more. Binance has even created a liquidity pool swap program on its centralized exchange because the returns are so lucrative.‌

Sifchain's liquidity pools are based on Sushiswap with extensibility in mind for potential updates. Rowan will be the settlement token for each pool, meaning each pool will contain Rowan as one asset and an external asset as the other. Sifchain’s swap UI will support swaps between external assets \(for example, cMKR:cCOMP\) but such transactions will actually require two swaps between two different liquidity pools \(for example, cMKR:ROWAN and then ROWAN:cCOMP\).‌

Liquidity providers need to be able to add liquidity into Sifchain’s liquidity pools where they can earn income. Liquidity providers should be able to deposit any token Sifchian supports to the appropriate pool. They should be able to add [asymmetrically](https://medium.com/thorchain/asymmetric-withdrawals-on-bepswap-a6924ed2f28b), meaning they can add only Rowan or only TKN for any token. This is as opposed to Uniswap where users must add equal values of the settlement token \(ETH\) and the other token \(TKN\). Liquidity providers should be able to add or remove liquidity whenever they choose.‌

Sifchain allows swappers to send a transaction to a liquidity pool with the amount of tokens they want to give up in exchange for tokens on the other side of the pool. Sifchain uses both an order book and a CLP for trade completion.‌

## Asymmetric Liquidity Pool‌ <a id="asymmetric-liquidity-pool"></a>

In many decentralized exchanges, users can add liquidity to liquidity pools and earn a portion of the transaction fees charged to other users who want to swap tokens in the pool. The constraint that most liquidity pools put on liquidity providers is that they must put in an equal value of each token pair. For example, in the ETH/DAI liquidity pool in Uniswap, a user is required to add 2.64 ETH for every 1,000 DAI that is added at the time of this writing. And then based on the amount the user puts into the pool, they then receive a proportionate amount of the fees charged.‌

With Sifchain, users who want to add liquidity to a pool can add any amount of either or both tokens. This is known as adding liquidity asymmetrically, which gives users ultimate flexibility. Based on the amount of tokens in the pool and the amount that the user adds, they will then own a percentage of the entire pool. Sifchain will initially use the same formula to calculate ownership as BEPSwap.‌

**When a user only puts in one side of the pool, how is their ownership percentage calculated?**‌

The formula that is used to calculate ownership % is designed to incentivize users to keep the liquidity pool balanced. As one side of the pool increases, users can gain a higher % of the overall pool by adding tokens to the other side.‌

Below is the formula used to calculate the units owned by a user when they add Rowan or another asset to the liquidity pool.

$$
slipAdjustment = 1 - |\frac{Ra-rA}{(2R + r)*(a +A)}|
$$

$$
units = \frac{P(rA+Ra)}{2RA}*slipAdjustment
$$

where‌

r = rowan deposited‌

a = asset deposited‌

R = Rowan Balance \(before\)‌

A = Asset Balance \(before\)‌

P = Existing Pool Units‌

The liquidity provider is allocated a portion of the fees collected from swappers proportional to their ownership of the pool. For example, If the liquidity provider owns 2% of the pool, they are allocated 2% of the fees collected. Learn more about asymmetric liquidity pools here‌

​[https://medium.com/sifchain-finance/sifchain-technical-introduction-advantages-of-an-asymmetric-liquidity-pool-93bedae3986c](https://medium.com/sifchain-finance/sifchain-technical-introduction-advantages-of-an-asymmetric-liquidity-pool-93bedae3986c)‌

### Validator Subsystem <a id="validator-subsystem"></a>

Validators stake tokens to earn ROWAN.‌

Variables‌

* inflation rate
* percentage of tokens staked
* delegation rates

Revenue source‌s

* minting policy
* slashing rate

![](https://gblobscdn.gitbook.com/assets%2F-MMWSB3Kf9g5504mhpLn%2F-MMaQQ83RZCKP6CGkn0C%2F-MMa_csi70arcERz7d_l%2FScreen%20Shot%202020-11-20%20at%2010.27.03%20PM.png?alt=media&token=37c7f386-a86e-4ec8-b0d0-de6bdd0561aa)

### Liquidity Provider Subsystem <a id="liquidity-provider-subsystem"></a>

Participants provide liquidity to sifchain's CLP and earn rewards in ROWAN tokens.‌

Variables‌

* Rowan \(settlement\) token price
* swap volumes
* number of unique liquidity providers

Revenue sources‌

* Liquidity fee policy
* Swapping activity

‌

![](https://gblobscdn.gitbook.com/assets%2F-MMWSB3Kf9g5504mhpLn%2F-MMaQQ83RZCKP6CGkn0C%2F-MMa_j1HaVo5d4moISEQ%2FScreen%20Shot%202020-11-20%20at%2010.27.28%20PM.png?alt=media&token=99830407-dc84-4af3-9448-62f94ad5a7cd)

### Rebalancing Policy <a id="rebalancing-policy"></a>

The incentive Pendulum keeps the network in a balanced state. It stops the network from becoming unsafe or inefficient by changing the distribution of rewards to node operators and liquidity

![](https://gblobscdn.gitbook.com/assets%2F-MMWSB3Kf9g5504mhpLn%2F-MMaQQ83RZCKP6CGkn0C%2F-MMa_sTnDeac6bjKxxfr%2FScreen%20Shot%202020-11-20%20at%2010.28.08%20PM.png?alt=media&token=1a63d547-b125-4f90-a259-ec6df0e50e51)

### Sifchain Liquidity pool features <a id="sifchain-liquidity-pool-features"></a>

* Slip based fee model inspired by Thorchain
* Rowan as settlement token for all pools
* Asymmetric deposits and withdraws

## Liquidity Pools Architecture‌ <a id="liquidity-pools-architecture"></a>

​[https://github.com/Sifchain/sifnode/blob/develop/docs/4.Liquidity%20Pools%20Architecture.md](https://github.com/Sifchain/sifnode/blob/develop/docs/4.Liquidity%20Pools%20Architecture.md)

