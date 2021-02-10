# Swappers & Traders

## Introduction

Sifchain allows its users to swap any asset on any bridged chain \(like Ethereum\) for any other assets. Rowan is the settlement token for all of Sifchain’s liquidity pools. Therefore, all liquidity pools contain an external asset like 'ETH' or 'MKR' and Rowan. Swaps between two external assets require two swaps against two liquidity pools. This means that people who perform a swap for two external assets, will be charged two swap fees. Traders can thus save on swap fees by denominating their holdings in Rowan as a sign of long term faith in the Sifchain project. The network aims to give users access to:

* A large variety of assets through cross-chain compatibility and simple asset listing
* Superior user experience through open finance protocols and permissionless access
* 1-transaction access to fast chains \(BinanceChain\), smart chains \(Ethereum\), censorship-resistant chains \(Bitcoin\) and private chains \(Monero\).

Like any marketplace, the prices on Sifchain are maintained by profit-seeking traders. Traders exploit arbitrage opportunities in markets. They buy assets on markets with low prices and sell them on markets with high prices. This earns them a profit.

Traders compare the exchange rates on Sifchain with the rates on external markets. If they find the price is lower on Sifchain they can buy here and sell on an external market. If they find the price is lower on external markets they can buy there and sell on Sifchain. This process is repeated at high-frequency. Over time, price information propagates and Sifchain settles with external markets.

## Why Swap?

Users can swap for any number of reasons. A few of these are listed below:

* 1\) Users may want to switch between tokens that have different utility, for example, switching from a social token supporting their favorite artist to a decentralized finance \(DeFi\) token expected to accrue value to a stable coin used for fiat tax obligations. 
* 2\) Users may want to swap in order to take advantage of arbitrage opportunities. 
* 3\) Users may want to execute a momentum trading strategy based on their expectations about the future price of one or more tokens. 
* 4\) Users may want to diversify their portfolio to consist of multiple assets, thus reducing risk of loss.

## How to Swap?

For clear directions on how to execute a swap, refer to our [Sifchain-DEX-UI guide](https://docs.sifchain.finance/resources/sifchain-dex-ui#swapping-assets). 

## Swap Fees

In order to pay Liquidity Providers for their contribution to the liquidity pool, swap fees are charged during the swapping process. Sifchain uses Thorchain's slip-based Continuous Liquidity Pool model to calculate trade slip, liquidity fee, and the resulting swap. For additional information on these formulas, please reference our [documentation here](https://github.com/Sifchain/sifnode/blob/develop/docs/clp/Liquidity%20Pools%20Architecture.md).

