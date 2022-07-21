# Peggy

## Introduction

The Ethereum network has been plagued with slow transactions and high fees for a long time. Swappers would prefer to swap on a platform like Sifchain, which runs on the Cosmos network, a substantially more performant blockchain. In order to move value from Ethereum tokens to a Cosmos network blockchain like Sifchain, users must use cross-chain software.

Our solution for this problem is Peggy.

In order for Sifchain to allow for cross-chain support and free movement of assets between chains, we have implemented a concept named 'Peggy'. Simply put, Peggy will allow people to freely move assets that exist on one chain to another, use those assets in that chain, and then allow the user to move those assets back to the source chain. You can think of this as importing tokens into Sifchain to use them within Sifchain, and then exporting those tokens to a different chain once you want to move them out of Sifchain.

We see Peggy’s deployment as a hallmark moment for growth of the Cosmos Network. With Peggy and IBC, Ethereum users will be able to use their ETH and ERC20 tokens on Cosmos SDK platforms such as Kava, Akash, Terra, e-Money, IRIS, Secret Network, and of course, the Cosmos Hub. Cosmos Network users will also be able to use their tokens on Ethereum and take advantage of its dapp network. Cryptocurrency holders on both sides will be able to take advantage of the benefits of one chain while holding a position on a token native to another, bringing us one step closer to Sifchain’s mission of connecting liquidity on all blockchains.

## **Intro to Peggy’s Architecture**

Peggy is a CosmosSDK application for moving assets on and off of EVM based, POW chains.

Peggy is the starting point for cross-chain value transfers from the Ethereum blockchain to Cosmos-SDK based blockchains as part of the Ethereum Cosmos Bridge project. Our approach to Peggy allows users of ETH and ERC-20 tokens on Ethereum to create pegged tokens on a Cosmos Network chain (in our case, on Sifchain). These pegged tokens can then be used within the Sifchain ecosystem, via pooling or swaps. When a user is done with these pegged assets, they may use Peggy to then transfer the assets back to an external address.

The system accepts incoming transfers of Ethereum tokens on an Ethereum smart contract, locking them while the transaction is validated and equitable funds issued to the intended recipient on the Cosmos bridge chain. The system supports value transfers from Cosmos-SDK based blockchains to the Ethereum blockchain as well through a reverse process.

![](<../.gitbook/assets/Screen Shot 2021-01-14 at 12.55.57 PM.png>)

An Ethereum user can send tokens from their Ethereum wallet to a Peggy smart contract running on Ethereum. Peggy validators observing the Peggy smart contract keep those Ethereum tokens in a lockup group and mint a corresponding allocation of pegged tokens to a user’s Cosmos Network wallet address.

At maturity, Sifchain will utilize IBC and use a Peggy deployment with a separate peg-zone blockchain in which Peggy-specific validators stake collateral specifically used to secure the bridge. These peg-zone validators are subject to slashing as per Tendermint consensus rules on both the Cosmos SDK peg zone chain and the Ethereum smart contract side of that bridge. This solves crypto-economic security issues on the bridge. In exchange for being subject to this new slashing requirement, validators will earn a service rate.

At BetaNet launch, Sifchain's initial Peggy design will be slightly different than this due to the immaturity of IBC. At BetaNet launch, Peggy and Sifnode will co-exist together within Sifnode. This allows Sifchain to support cross-chain transfers, adding & removing of liquidity, and token swaps from day 1 without the reliance on IBC. Once IBC has matured and is production-ready, we will shift to this model to realize its scalability benefits.

Find additional details about current Peggy's architecture here:

* [Peggy Architecture with IBC](https://github.com/Sifchain/peggy/blob/develop/docs/sifchain-peggy-architecture.md)
* [Peggy Architecture without IBC](https://github.com/Sifchain/peggy/blob/develop/docs/sifchain-peggy-architecture-no-ibc.md)&#x20;

\


## Peggy 2.0

Sifchain is actively working on the next iteration of the Peggy bridge, called [Peggy 2.0](https://peggy.sifchain.finance/#/) !\
Peggy 2.0 is designed to increase its scalability and being able to handle import and exports across different chains. Peggy 2.0 is sometimes called the Omni-EVM bridge, as it is very straightforward to tune it in order to integrate all the EVM chains. Regardless of the easiness to integrate EVM chains, Peggy 2.0's architecture is designed to handle every chain
