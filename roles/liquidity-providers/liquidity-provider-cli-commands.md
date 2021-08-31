---
description: >-
  This contains a summarized list of all relevant CLI commands for Liquidity
  Providers
---

# Liquidity Provider CLI Commands

## Adding Liquidity

Reference the below list of commands if you decide to use a CLI tool to add liquidity to a pool. 

* **Creating a Liquidity Pool:** `sifnoded tx clp create-pool --from <key> --symbol <external-asset-symbol> --nativeAmount <amount> --externalAmount <amount>`
  * --symbol refers to the new asset the pool is being created for, 
  * --nativeAmount is the amount of Rowan that will be added to the newly created pool, 
  * --externalAmount is the amount of the asset specified by symbol that will be added to the newly created pool. 
  * Both amounts specified will be deducted from the address specified by --from. 
  * A successful submission of this transaction will create a new pool for the specified asset and amounts.
  * View newly created pool with the following command: `sifnoded query clp pool <external-asset-symbol>` 
    * &lt;external-asset-symbol&gt; will be the symbol for the asset specified during pool creation.
* **View share of pool & token balances**: Creating a pool will also create a new Liquidity Provider object for the creator of the pool. This object contains information about your share of the liquidity pool and token balances in the pool. Liquidity Provider objects can be queried with the following command: `sifnoded query clp lp <external-asset-symbol> <lpAddress>`
  * &lt;external-asset-symbol&gt; is the symbol for the liquidity pool and &lt;lpAddress&gt; is the address that provided the tokens to the pool.
* **Adding Liquidity to a Pool**: `sifnoded tx clp add-liquidity --from <key> --symbol <external-asset-symbol> --nativeAmount <amount> --externalAmount <amount>`
  * --symbol refers to the asset pool that the liquidity will be added to
  * --nativeAmount is the amount of Rowan that will be added to the pool, and 
  * --externalAmount is the amount of the asset specified by symbol that will be added to the pool. 
  * Both amounts specified will be deducted from the address specified by --from. 
  * A successful submission of this transaction will update the pool for the specified asset and amounts.
    * View updated pool with the following command: `sifnoded query clp lp <external-asset-symbol> <lpAddress>`
      * &lt;external-asset-symbol&gt; will be the symbol for the asset specified during pool creation.
      * &lt;lpAddress&gt; is the address that provided the tokens to the pool. 

## **Removing Liquidity**

Reference the below list of commands if you decide to use a CLI tool to remove liquidity from a pool. 

* **Remove Liquidity for a Pool:** `sifnoded tx clp remove-liquidity --from <key> --symbol <external-asset-symbol> --wBasis <basis points> --asymmetry <basis-points-range>`
  * --from is the address that provided tokens to the liquidity pool  
  * --symbol is the asset symbol for the liquidity pool 
  * --wBasis is the percentage of your share in the liquidity pool to be withdrawn expressed in basis points from 0 to 10000, 0 being 0% and 10000 being 100%
  * --asymmetry determines the ratio of each token that will be withdrawn expressed in either negative or positive basis points from -10000 to 10000. An --asymmetry value of -10000 will result in a withdrawal of 100% Rowan, 0 will result in a withdrawal of 50% Rowan and 50% external asset, and 10000 will result in a withdrawal of 100% external asset.
  * After successfully submitting a withdrawal transaction you can verify that the changes are reflected in the corresponding Liquidity Provider object by querying it with the following command:
    * `sifnoded query clp lp <external-asset-symbol> <lpAddress>` 
      * &lt;external-asset-symbol&gt; is the symbol for the liquidity pool 
      * &lt;lpAddress&gt; is the address that provided the tokens to the pool 
      * If the withdrawal removed all of your shares from the pool \(10000 basis points\), the Liquidity Provider object will be deleted and this query will return nothing.
  * You can also check that the tokens have been added back to the original address by querying the address’s balance with: 
    * `sifnoded query account <address>` 

