# Liquidity Providers

## Introduction

Liquidity Providers \(LPs\) creating and adding to liquidity pools is what allows Sifchain to provide swapping functionality to take place. LPs provide assets that can then be swapped for other assets by other users. For example, a LP can come along and say they want to contribute to a Liquidity Pool of Token A &lt;&gt; ROWAN. So they would provide an amount/s of Token A and/or ROWAN to the pool for other people to swap for. 

The LPs are then compensated with swap fees and system rewards. Compensation is affected by a number of factors related to the pool and the state of the network.

Liquidity providers are able to deposit any token Sifchian supports to the appropriate pool. Anyone can create a liquidity pool by pooling Rowan and a new token into a pool initialization transaction. The price of the new token is set based on the amount of Rowan pooled. Sifchain enforces a minimum CLP size but multiple depositors can contribute to the creation of a single CLP.

If users are simply adding to an already existing liquidity pool, they may do so asymmetrically. This means users can add either Rowan or the token \(TKN\) the pool comprises of. This is as opposed to Uniswap where users must add equal values of the settlement token \(ETH/UNI\) and the other token \(TKN\).  Liquidity providers are able to add or remove liquidity whenever they choose. Please refer to our [Core Concept Documentation on Liquidity Pools ](https://docs.sifchain.finance/core-concepts/liquidity-pool)for additional details around these concepts.

## Why provide liquidity to a pool?

Liquidity pools are important in[ **decentralized finance \(DeFi\)**](https://www.coindesk.com/what-is-defi) ****— particularly decentralized exchanges \(DEX\). Because Sifchain is the world’s first omni-chain DEX, this technology is fundamental to our vision. 

Sifchain enables liquidity providers to add liquidity into pools where they can earn income without constraints endemic to other exchanges. Liquidity providers can deposit any token Sifchain supports to the appropriate pool. They can add liquidity asymmetrically, meaning they can add only Rowan or only TKN for any token.

Sifchain rewards users who provide liquidity with various forms of income. To learn more about what types of income you can expect to earn as a liquidity provider, please reference [here](https://docs.sifchain.finance/core-concepts/liquidity-pool).

## Liquidity Mining Rewards

Sifchain will run a 12-week liquidity mining program for poolers, in order to incentivize early adopters. Rewards are subject to change based on evaluations of the network from the Sifchain core team, community feedback, and governance over time.

To learn more about this program and what you can expect to earn as part of this program, reference our announcement article [here, section 'Liquidity Mining for Poolers'.](https://medium.com/sifchain-finance/uses-for-rowan-the-polyvalent-token-for-omni-chain-decentralized-exchange-dex-3207e7f70f02)

## Liquidity Provider Fees

Liquidity providers will only need to pay gas fees when adding liquidity to a pool. There is a potential loss of value for a liquidity provider depending on how much slip is created in the pool's price with an asymmetric deposit. This slip calculation can be found [here](https://github.com/Sifchain/sifnode/blob/develop/docs/clp/clp-adr.md). 

## Liquidity Pool Ownership Calculation

Below is the formula used to calculate the units owned by a user when they add Rowan or another asset to the liquidity pool.

![](../.gitbook/assets/screen-shot-2021-01-24-at-4.39.26-pm.png)

## Adding Liquidity

There are a few ways you can add liquidity to a pool:

* 1\) Sifchain-DEX-UI: You can use our user-friendly portal to add liquidity to an existing pool, or to create a brand new liquidity pool \(in the case where one does not exist yet\). Please refer to our [Sifchain-DEX-UI Resource](https://docs.sifchain.finance/resources/sifchain-dex-ui) for clear instructions on how to perform these actions.
* 2\) Manually by running commands. Please refer to the list below for these commands:
  * **Creating a Liquidity Pool:** `sifnodecli tx clp create-pool --from <key> --symbol <external-asset-symbol> --nativeAmount <amount> --externalAmount <amount>`
    * --symbol refers to the new asset the pool is being created for, 
    * --nativeAmount is the amount of Rowan that will be added to the newly created pool, 
    * --externalAmount is the amount of the asset specified by symbol that will be added to the newly created pool. 
    * Both amounts specified will be deducted from the address specified by --from. 
    * A successful submission of this transaction will create a new pool for the specified asset and amounts.
    * View newly created pool with the following command: `sifnodecli query clp pool <external-asset-symbol>` 
      * &lt;external-asset-symbol&gt; will be the symbol for the asset specified during pool creation.
  * **View share of pool & token balances**: Creating a pool will also create a new Liquidity Provider object for the creator of the pool. This object contains information about your share of the liquidity pool and token balances in the pool. Liquidity Provider objects can be queried with the following command: `sifnodecli query clp lp <external-asset-symbol> <lpAddress>`
    * &lt;external-asset-symbol&gt; is the symbol for the liquidity pool and &lt;lpAddress&gt; is the address that provided the tokens to the pool.
  * **Adding Liquidity to a Pool**: `sifnodecli tx clp add-liquidity --from <key> --symbol <external-asset-symbol> --nativeAmount <amount> --externalAmount <amount>`
    * --symbol refers to the asset pool that the liquidity will be added to
    * --nativeAmount is the amount of Rowan that will be added to the pool, and 
    * --externalAmount is the amount of the asset specified by symbol that will be added to the pool. 
    * Both amounts specified will be deducted from the address specified by --from. 
    * A successful submission of this transaction will update the pool for the specified asset and amounts.
      * View updated pool with the following command: `sifnodecli query clp lp <external-asset-symbol> <lpAddress>`
        * &lt;external-asset-symbol&gt; will be the symbol for the asset specified during pool creation.
        * &lt;lpAddress&gt; is the address that provided the tokens to the pool. 

## **Removing Liquidity**

When removing liquidity in our asymmetric liquidity pool design, since users are allowed to stake one side or the other, they are also allowed to withdraw one side or the other. Because the system calculates the user’s overall ownership at the time they added liquidity, it can now use that ownership % to calculate the amount\(s\) to withdraw. 

For example:

* Liquidity Pool: ROWAN &lt;&gt; Token A
* A user will identify what percentage of their ownership they want to withdraw. They can select anywhere from 1%-100%.
* Next, the user will specify how much of each token in the pool they want to withdraw. The user can specify any amount between 100% ROWAN to 100% of Token A.

By using these two different values, the system gives LPs a very high level of precision in specifying exactly how much to withdraw from each side of the pool. This differs from other symmetric liquidity pools, where LPs must withdraw equal value from both sides.

There are a few ways you can remove liquidity to a pool:

* 1\) Sifchain-DEX-UI: You can use our user-friendly portal to remove liquidity at any time. Please refer to our [Sifchain-DEX-UI Resource](https://docs.sifchain.finance/resources/sifchain-dex-ui) for clear instructions on how to perform these actions.
* 2\) Manually by running commands. Please refer to the list below for these commands:
* **Remove Liquidity for a Pool:** `sifnodecli tx clp remove-liquidity --from <key> --symbol <external-asset-symbol> --wBasis <basis points> --asymmetry <basis-points-range>`
  * --from is the address that provided tokens to the liquidity pool  
  * --symbol is the asset symbol for the liquidity pool 
  * --wBasis is the percentage of your share in the liquidity pool to be withdrawn expressed in basis points from 0 to 10000, 0 being 0% and 10000 being 100%
  * --asymmetry determines the ratio of each token that will be withdrawn expressed in either negative or positive basis points from -10000 to 10000. An --asymmetry value of -10000 will result in a withdrawal of 100% Rowan, 0 will result in a withdrawal of 50% Rowan and 50% external asset, and 10000 will result in a withdrawal of 100% external asset.
  * After successfully submitting a withdrawal transaction you can verify that the changes are reflected in the corresponding Liquidity Provider object by querying it with the following command:
    * `sifnodecli query clp lp <external-asset-symbol> <lpAddress>` 
      * &lt;external-asset-symbol&gt; is the symbol for the liquidity pool 
      * &lt;lpAddress&gt; is the address that provided the tokens to the pool 
      * If the withdrawal removed all of your shares from the pool \(10000 basis points\), the Liquidity Provider object will be deleted and this query will return nothing.
  * You can also check that the tokens have been added back to the original address by querying the address’s balance with: 
    * `sifnodecli query account <address>`  

