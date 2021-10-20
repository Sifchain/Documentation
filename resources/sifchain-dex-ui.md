---
description: >-
  Reference this page for all things related to Sichain's decentralized
  exchange.
---

# Sifchain DEX User Guide

## Welcome

Welcome to the [Sifchain DEX](https://dex.sifchain.finance)! This is your portal to interact with the Sifchain system and enjoy all of the great features it has to offer. Read below for helpful 'how-to' guides for anything and everything you can do through this portal.&#x20;

## Getting Started

In order to take full advantage of the Sifchain DEX, you must have a Keplr wallet for managing assets on Sifchain and a MetaMask Wallet for managing assets on Ethereum.

### Create or Import a Sifchain Address with Keplr Wallet&#x20;

Keplr is the official wallet for ROWAN and is required to perform Swaps, Pooling and Pegging on the Sifchain DEX. We recommend you use Google Chrome or Brave Browser from this point forward.&#x20;

1. Install the [Keplr Browser Extension](https://chrome.google.com/webstore/detail/keplr/dmkamcknogkgcdfhhbddcghachkejeap)&#x20;
2. Open Keplr to add a Sifchain address to your wallet in one of the following ways:
   1. Create new account
      1. Within Keplr click on 'Create new account'
      2. On the next screen, we suggest that you choose a 24 word mnemonic for security purposes. Ensure you write down this 24 word mnemonic you've been given.&#x20;
      3. Give your account a new account name.&#x20;
      4. Add a password. Then click "Next".
      5. Now you will need to re-enter your 24 word mnemonic.&#x20;
   2. Import existing account
      1. Within Keplr click on the 'Import existing account'
      2. On the next screen, input your mnemonic and your account name.
   3. Import ledger
      1. Within Keplr click on the 'Import ledger'
      2. On the next screen, enter in your account name and click 'Next'&#x20;
      3. Connect your ledger and open the Cosmos app.
         1. For additional directions on ledger app setup, please see [directions here](https://stakingfac.medium.com/cosmos-keplr-guide-ledger-d71e9dded29d).
3. Next, navigate to the Sifchain DEX and click on 'Connect Wallet'. Then click on 'Keplr'&#x20;
4. Keplr should jump forward asking for you to Approve the 'Chain Add Request'. If you do not see this, please make sure the extension is enabled by clicking on the Keplr icon in upper right-hand corner. You may have to reload the page.
5. Approve the "Chain Add Request"
6. Approve the "Requesting Connection"
7. Success!

Your Sifchain address is now secured by the Keplr wallet which is now connected to the Sifchain DEX. You can now interact with Sifchain DEX. If you want to move assets between Sifchain and any of th Cosmos-based networks (ie: Cosmos, Akash, Iris, Sentinel, Persistance, Osmosis, Regen, Crypto-org), then you will also be interacting with the Keplr wallet, but via those chain connections. You can see your various addresses, and balances within those address, within your keplr wallet by clicking on the Keplr extension, and clicking on the dropdown option of the network:&#x20;

![](<../.gitbook/assets/Screen Shot 2021-08-02 at 12.45.54 PM.png>)

To see additional information about your account, click on the Keplr browser extension, select Sifchain in the dropdown chain options. This will show your Sifchain account name, your address, and your balances. You can also add additional accounts here, or simply switch accounts if you have multiple Sifchain addresses.

### Connect your MetaMask Wallet

In order to use our Peggy feature and to move assets from the Ethereum blockchain over to the Sifchain blockchain (and vice-versa), you will need to connect to your MetaMask wallet:

1. Navigate to the Sifchain DEX and click on 'Connect Wallet'. Then click on 'MetaMask'
2. Similar to Keplr, follow the MetaMask prompts to connect your Metamask wallet.&#x20;

Once you have connected both of your Metamask and Keplr wallets, you are now ready to peg liquidity into Sifchain and use all of the features Sifchain DEX has to offer!

## Importing/Exporting Assets

In order to move assets between Sifchain and an external Blockchain, you will use the 'Import' feature, as possible through our implementation of Peggy and IBC.  We use Peggy when importing and exporting between Sifchain and Ethereum, and we use IBC when importing and exporting between Sifchain and other Cosmos-based blockchains. A few key things to understand about these features:

#### Peggy

* **Gas Fees with Peggy**
  * 1\) In order to import assets from Ethereum to Sifchain, you will need some ETH in order to pay for the gas fees to execute this transaction.
  * 2\) In order to export assets from Sifchain back to Ethereum, you will need Sifchain ETH in order to pay for the transaction fees. You will also need a very small amount of ROWAN to pay the gas fees to execute this transaction.
* **Time it takes to execute a transaction with Peggy**
  * In order for an import transaction from Ethereum to Sifchain to be recognized, it needs to go through 50 Ethereum confirmations. This means that this transaction can take anywhere between 10 and 20 minutes to be recognized on Sifchain.
  * Exporting assets from Sifchain back into Ethereum requires significantly fewer confirmations and should only take \~1 minute to be recognized on Ethereum.

#### IBC

* **Gas Fees with IBC**
  * 1\) In order to import assets from Cosmos-blockchains to Sifchain, you will need some of the source-chain token in order to pay for the gas fees to execute this transaction. For example, if importing from CosmosHub, you will pay gas in ATOM.
  * 2\) In order to export assets from Sifchain back to a Cosmos-based blockchain, you will need a very small amount of ROWAN to pay the gas fees to execute this transaction.
* **Time it takes to execute a transaction with IBC**
  * Most IBC transactions are processed in under 10 mintues. However, some can take upwards of 60 minutes to be fully processed.

### Importing Assets into Sifchain - Tutorial

After connecting your Keplr and MetaMask wallets, you are now ready to move assets between external chains and Sifchain. Users are able to import assets from Cosmos and assets from Ethereum into Sifchain. Sifchain has a [list of allowable tokens](list-of-allowable-tokens-in-sifchain.md) that can be transferred into Sifchain. We will continuously add new tokens based on user feedback and market conditions. In order to move any of these allowable Ethereum or Cosmos assets into the Sifchain network, please follow the below steps.

* Once in the Sifchain DEX, go to the 'Balances' feature

![](<../.gitbook/assets/Screen Shot 2021-08-02 at 1.04.12 PM.png>)

* This balances tab will show you a list of ALL allowable tokens to be imported into Sifchain. If you do not see a token you are desiring to import, please reach out to the Sifchain team on [Discord](https://discord.gg/bGxWngDAvw). &#x20;
* Within this balances tab, you can see your associated Sifchain token balances with each of the tokens. This represents the amount of that token a user has **already** imported into Sifchain.
* Click on the 'Import' button next to the token you want to move into Sifchain. This will bring you to the next screen:

![](<../.gitbook/assets/Screen Shot 2021-07-28 at 2.11.45 PM (1).png>)

* Here, you can select from which network you want to import from. Once you choose your network and the associated token, it will call in your balance of that token from that network. So for example, if you have ETH in Ethereum, it will call in your balance of ETH that currently exists in your MetaMask wallet in Ethereum. If you have ETH that you have exported into Cosmos and you select Cosmos in your network dropdown, it will call in your balance of ETH that currently exists in your Keplr wallet in Cosmos.
* Input the amount of that token you want to import. Feel free to use the 'Max' button which will auto-fill the amount with the maximum amount of that token you have to import (minus an amount to cover estimated fees). We have automatically called in your Sifchain address as the recipient address of these pegged tokens.
* Next, click 'Import'. This will bring up another confirmation screen:

![](<../.gitbook/assets/Screen Shot 2021-07-28 at 2.31.12 PM.png>)

* Once you confirm the details are correct, you can confirm the import. Please note that importing an asset from Ethereum into Sifchain needs to go through 50 Ethereum block confirmations. For this reason, this action can take upwards of 20 minutes. Please be patient. You should see the amount you want to import be deducted from your Ethereum address shortly after you execute the transaction. But you will not see the amount appear in your Sifchain wallet until it has gone through all 50 confirmations. As for importing from Cosmos-based chains, this can take, on average, 10 mintues to be fully processed. However, some transactions may take up to 60 mintues.

You are now free to use your newly imported tokens via swaps, or by providing liquidity!

[Demo Video: Move Tokens into Sifchain](https://www.youtube.com/watch?v=okuEndeGRHA\&list=PLj5x\_t273CNiBvcH6GjI9gBPzMFm9BlCL\&index=5)

### Export Assets from Sifchain - Tutorial

* You are free to export your Sifchain assets into Ethereum or Cosmos at any time. To do this, go to the 'Balances' screen, click on the 3 dots, and click on the 'Export' button. This button will only be clickable on those tokens you have a Sifchain Balance to export:

![](<../.gitbook/assets/Screen Shot 2021-07-28 at 2.35.43 PM.png>)

* Click on the 'Export' button next to the token you want to export out of Sifchain. This will bring you to the export modal:

![](<../.gitbook/assets/Screen Shot 2021-07-28 at 2.41.22 PM.png>)

* Now you can input the amount of that token you want to export. Feel free to use the 'Max' button which will auto-fill the amount with the maximum amount of that token you have to export (minus any ROWAN to cover for estimated fees). We will automatically call in your external address as the recipient address of these exported tokens. Once you input an amount, it will display the associated transaction fee. Ensure you have enough of that token in your Sifchain wallet to pay for this fee.
* Next, click 'Export'. This will bring up another confirmation screen:

![](<../.gitbook/assets/Screen Shot 2021-07-28 at 2.42.18 PM.png>)

* Once you click confirm, you will need to sign the transaction via your Keplr wallet. After this, you can see the adjusted token amounts within a minute in your wallets and within the 'Balances' screen.

[Demo Video: Export Tokens out of Sifchain](https://www.youtube.com/watch?v=XPf57h4QfWg\&list=PLj5x\_t273CNiBvcH6GjI9gBPzMFm9BlCL\&index=3)

## Pooling Assets

Users can add any of their tokens to a liquidity pool and earn rewards for doing so. To learn more about the core concept of liquidity pools, how we at Sifchain use them, and details around why one would want to provide liquidity, please refer to our documentation here on [Sifchain Liquidity Pools](https://docs.sifchain.finance/core-concepts/liquidity-pool) and [Liquidity Providers](https://docs.sifchain.finance/roles/liquidity-providers).

### Adding Liquidity

After connecting your Keplr and MetaMask wallets, and you have assets within Sifchain, you are now ready to add liquidity to our liquidity pools. Sifchain has a [list of allowable tokens](list-of-allowable-tokens-in-sifchain.md) that can be used within Sifchain. This list will be ever-evolving as we will continuously add new tokens based on user feedback and market conditions.

* To begin the 'add liquidity' process, navigate to the 'Pool' option within the Sifchain DEX. Here you will see a screen that looks like the one shown here:

![](<../.gitbook/assets/Screen Shot 2021-08-02 at 1.24.21 PM.png>)

* This screen shows the following:
  * A list of all pools within Sifchain.
  * A list of liquidity pools that you currently have liquidity in brought to the top of this list. For pools you have liquidity in, you will easily be able to see your gain/loss from providing liquditiy to that pool, as well as your pool share percentage.
  * The ability to expand each pool and see additional details about it. This will show you the total amount in that pool from everyone in the network, the price of the non-Rowan token, the arbitrage opportunity of that pool, the pool depth, and the pool trade volume in the last 24 hours. It will also give you the ability to add/remove liquidity from that pool.

![](<../.gitbook/assets/Screen Shot 2021-08-02 at 1.27.48 PM.png>)

* To add liquidity to a pool, click 'Add Liquidity'. This will take you here:

![](<../.gitbook/assets/Screen Shot 2021-08-02 at 1.29.28 PM.png>)

* Here you will want to select which token you will want to add liquidity with. You can only add liquidity with a Sifchain Token and Rowan. Click on the token dropdown to see a list of allowable tokensand your associated balances.
* Once you select the token with which you want to pool, you will now see your available balance. You may input any amount or click the 'Max' button which will automatically call in your total balance of that token.&#x20;

{% hint style="info" %}
IMPORTANT NOTE: Please ensure you have enough ROWAN to cover the gas fees. This means that if you type in your total amount of current ROWAN, the transaction may fail as you do not have additional ROWAN to cover the gas fees.
{% endhint %}

* IF the pool you are adding liquidity to already exists, then you do NOT need to add both your selected token and ROWAN. You may choose to add asymmetrically to the pool if you desire. You can also choose to add both your selected token and ROWAN to the pool as well if you desire.&#x20;
* IF the pool does not exist yet, then you must put some amount of the selected token AND ROWAN to initiate the pool. This will set the initial prices of the pool.
* Once you input your desired amounts, you will see some displayed statistics on the pool:

![](<../.gitbook/assets/Screen Shot 2021-08-02 at 1.29.28 PM (1).png>)

* The 'Pool Token Prices' display the prices of the tokens as they are in the pool at this very moment.
* The 'Est. prices after pooling & Pool Share' display what those prices will be IF you were to execute your adding of liquidity. This will also show you the percentage of the pool you will own if you execute the add.
* You can also turn on/off the 'Pool Equally' function. When turned on, it will automatically calculate the 'other' token for you so you are adding in a symmetric way. If you turn this feature off, then you are free to input any amount in either field manually. Please be aware of this feature by reading more [here](https://docs.sifchain.finance/core-concepts/liquidity-pool#asymmetric-liquidity-pool).
* Now you can click 'Add Liquidity' and see another confirmation screen:

![](<../.gitbook/assets/Screen Shot 2021-08-05 at 2.05.05 PM.png>)

* Once you 'Confirm', this will initiate your Keplr wallet for you to sign the transaction. Once successful, you will now see this listed pool jump to the top of the Pools listing, and will indicate your % ownership of the pool as well as your net gain/loss. This may take a few moments to be recognized

[Demo Video: Add Liquidity to a Pool in Sifchain DEX](https://www.youtube.com/watch?v=Z5\_w\_RnUPIY\&list=PLj5x\_t273CNiBvcH6GjI9gBPzMFm9BlCL\&index=5)

### Liquidity Pools: Additional Details

The below details are included for each liqudity pool. If you have liquidity in a pool, you will see additional details on it as well specific to your position in the pool:

![](<../.gitbook/assets/Screen Shot 2021-08-02 at 1.43.51 PM.png>)

* The 'Pool APY' displays the APY a user can earn from providing liquidity to this specific pool.&#x20;
* The 'Gain/Loss' shows you the total net gain/loss (in USDT) from providing liquidity to this pool from the beginning of time. This is your total net gain/loss based on earnings from swap fees and any gains or losses associated with changes in the tokens' prices from the moment you ever added liquidity to this pool.
* The 'Your pool share' shows the percentage of that pool that you 'own' and can withdraw at any time.&#x20;
* The 'Network Pooled' displays the **total** amount of those tokens that exist in the pool.&#x20;
  * This 'Network Pooled' will contain the fees and rewards collected for this pool in real-time. This is so liquidity providers 'own' their percentage of these amounts and can withdraw them at any time.&#x20;
* You can use the above amounts to determine the value of the pool that you own.&#x20;
* From here, you can add additional liquidity to the pool by clicking 'Add Liquidity'. For directions around this action, please see the 'Adding Liquidity' section above.
* You can also choose to 'Remove Liquidity' which we will discuss below.

### Remove Liquidity

* If you click on the 'Remove Liquidity' button, you will be taken to a screen that looks like the one here:

![](<../.gitbook/assets/Screen Shot 2021-08-05 at 2.06.46 PM.png>)

* Here you will identify two different amounts:
  * 1\) The percentage of your ownership you want to withdraw.
  * 2\) In which asset you want to withdraw that ownership in.
* For example, you can choose to withdraw all 100% of your ownership in equal parts ROWAN and other Token.&#x20;
* In the 'You will receive' section, this will display the amount of each token you will receive based upon the two amounts you selected.

![](<../.gitbook/assets/Screen Shot 2021-08-05 at 2.07.38 PM.png>)

* You can finalize this withdrawal by clicking on the 'Remove Liquidity'. This will trigger you to sign the transaction via your Keplr wallet. Once finalized, you will now see these amounts in your wallet and your liquidity pool share and amounts adjusted accordingly. &#x20;

[Demo Video: Remove Liquidity from a Pool in Sifchain DEX](https://www.youtube.com/watch?v=c\_BiSXQlnyg\&list=PLj5x\_t273CNiBvcH6GjI9gBPzMFm9BlCL\&index=3)

## Swapping Assets

In Sifchain, users can swap any asset to any other asset (given there is liquidity pooled for those assets) via the 'swap' functionality. After connecting your Keplr and MetaMask wallets, and you have assets within Sifchain, you are now ready to use the swap functionality.&#x20;

* Navigate to the 'Swap' option. Here you will see a screen that looks like the one shown here:

![](<../.gitbook/assets/Screen Shot 2021-08-02 at 3.22.29 PM.png>)

* This is where you can select what token you want to swap for another token.&#x20;
  * The 'From' field is the token you will be providing via the swap.
  * The 'To' field is what token you will be receiving via the swap.&#x20;
* Once you select a token you want to swap 'From' and 'To,' you will see your current balances of these tokens.&#x20;
* As you input and change the number in the 'From' field, the 'To' field is automatically calculated based on the prices of those tokens as determined by the liquidity pools.&#x20;
  * You can also adjust the number in the 'To' field to represent how much of that you want to receive and the number in the 'From' field will be automatically calculated.
* Slippage tolerance:
  * This is the amount of change in price you are willing to accept while still allowing the transaction to execute. Slippage occurs when other users' transactions are processed in between the time you submit a transaction and the time it is confirmed on the blockchain.

{% hint style="info" %}
IMPORTANT NOTE: Please ensure you have enough ROWAN to cover the gas fees. This means that if you type in your total amount of current ROWAN, the transaction may fail as you do not have additional ROWAN to cover the gas fees.
{% endhint %}

* Once you input your desired amount, you will see additional information and details regarding the swap:

![](<../.gitbook/assets/Screen Shot 2021-08-02 at 3.29.30 PM.png>)

* Price:
  * This will show you at what price you are receiving the token you are swapping for.
* Minimum Received:
  * This shows you the minimum amount that you will receive of the 'To' token based upon the slippage tolerance you have accepted.
* Price Impact:
  * This is the percentage impact to the amount of the 'To' token in the liquidity pool based upon how much you are swapping for.
* &#x20;Liquidity Provider Fee:
  * This represents the fee that is retained in the liquidity pool to be paid to the liquidity providers.
* Once you click 'Swap', you will see a confirmation screen:

![](<../.gitbook/assets/Screen Shot 2021-08-05 at 2.09.02 PM.png>)

* You can now confirm the swap, sign the transaction via your Keplr wallet and see the amounts adjusted in your wallet.

[Demo Video: Token Swap in Sifchain DEX](https://www.youtube.com/watch?v=WNamL5oX9Jw\&list=PLj5x\_t273CNiBvcH6GjI9gBPzMFm9BlCL\&index=1)
