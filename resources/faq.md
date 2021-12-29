# FAQ

## What is ROWAN and what is eROWAN?

**ROWAN** will be the functional token of the Sifchain network. Sifchain derives its internal asset price from CLPs and uses ROWAN as the settlement token. Traders must directly or indirectly purchase Rowan in order to execute trades against CLPs. For example, the USDC:BTC internal price is calculated using the USDC:RWN and RWN:BTC CLPs. ROWAN can be used for a variety of different actions within the Sifchain ecosystem, including:

* To stake a node and earn block rewards
* To delegate to a staked node and earn a commission of block rewards.
* To execute a swap from one token to another. Swaps will cost fees, of which are paid via ROWAN.
* To add liquidity to a pool and earn swap fees accrued within that pool.&#x20;

For more details on the usage of ROWAN, please refer [here](https://medium.com/sifchain-finance/uses-for-rowan-the-polyvalent-token-for-omni-chain-decentralized-exchange-dex-3207e7f70f02).

**eROWAN** is the equivalent token of ROWAN on the Ethereum network. Users are able to transfer their ROWAN to eROWAN between the Ethereum and Sifchain networks via Peggy.

**\*\*\*BE CAREFUL OF FAKE TOKENS\*\*\* The official eROWAN token contract address is:** [**https://etherscan.io/token/0x07bac35846e5ed502aa91adf6a9e7aa210f2dcbe**](https://etherscan.io/token/0x07bac35846e5ed502aa91adf6a9e7aa210f2dcbe)

## How can I acquire ROWAN and/or eROWAN

In order to hold ROWAN/eROWAN you will first need a wallet to custody the tokens. See [Wallet](faq.md#what-wallets-support-rowan-erowan) section below for more on wallets.

When the Sifchain network is live you will be able to buy ROWAN/eROWAN on decentralized exchanges (DEXs) and centralized exchanges (CEXs).

Here is a list of known exchanges that support ROWAN/eROWAN:

ROWAN:

* [Sifchain DEX](https://dex.sifchain.finance) — _live now_
* __[_AscendEX_](https://ascendex.com/en/cashtrade-spottrading/usdt/rowan) _- live now_

eROWAN:

* [QuickSwap: QUICK <> eROWAN](https://info.quickswap.exchange/pair/0x631f39d22430e889a3cfbea4fd73ed101059075f) **** - _live now_
* [QuickSwap: ATOM <> eROWAN](https://info.quickswap.exchange/pair/0x7051810a53030171f01d89e9aebd8a599de1b530) - _live now_
* [QuickSwap: REGEN <> eROWAN](https://info.quickswap.exchange/pair/0x66c37a00e426a613b188180198aac12b0b4ae4d4) - _live now_
* [QuickSwap: AKT <> eROWAN](https://info.quickswap.exchange/pair/0xa651ef83fa6a90e76206de4e79a5c69f80994556) - _live now_
* [QuickSwap: XPRT <> eROWAN](https://info.quickswap.exchange/pair/0xf366df119532b2e0f4e416c81d6ff7728a60fe7d) - _live now_
* [QuickSwap: IRIS <> eROWAN](https://info.quickswap.exchange/pair/0x58ffb271c6f3d92f03c49e08e2887810f65b8cd6) - _live now_
* [Uniswap](https://app.uniswap.org/#/swap?outputCurrency=0x07bac35846e5ed502aa91adf6a9e7aa210f2dcbe) v2 and v3 (DEX) — _live now, only use official_ [_eRowan contract address_](https://app.uniswap.org/#/swap?outputCurrency=0x07bac35846e5ed502aa91adf6a9e7aa210f2dcbe) \_\_
* [AEX](https://www.aex.com/page/trade.html#/?symbol=EROWAN\_USDT) - _live now_

**\*\*\*BE CAREFUL OF FAKE TOKENS\*\*\* The official eROWAN token contract address is:** [**https://etherscan.io/token/0x07bac35846e5ed502aa91adf6a9e7aa210f2dcbe**](https://etherscan.io/token/0x07bac35846e5ed502aa91adf6a9e7aa210f2dcbe)

For users who need a small amount of ROWAN to execute their first transaction (for example, to acquire more ROWAN via swap), then you can use our Betanet coin faucet. If your new account's ROWAN balance within the Sifchain DEX is 0 following your first token import, then you should see a "Get Rowan" modal on the DEX interface. Follow the steps and you will receive enough Rowan to pay the gas fee to execute your first swap.

## What wallets support ROWAN/eROWAN?

**ROWAN** is a token that exists within the Sifchain ecosystem, therefore you will need a Sifchain address to hold these tokens. Since Sifchain is built with the Cosmos SDK, you can use the Keplr wallet to generate a Sifchain address and custody your ROWAN. Reference our instructions on how to setup your Keplr Wallet [here](https://docs.sifchain.finance/resources/sifchain-dex-ui#setup-or-integrate-your-sifchain-address-via-keplr-wallet-integration).

**eROWAN** is an ERC-20 token that exists within the Ethereum ecosystem, therefore you will need an Ethereum address to hold these tokens. At the moment, we are supporting [MetaMask](https://metamask.io/download.html).

## How can I setup a Sifchain address in order to acquire ROWAN and use the Sifchain-DEX?

There are a few different ways you can setup a Sifchain address. This address is needed to be able to custody ROWAN and all pegged tokens in the Sifchain ecosystem. In order to get a Sifchain address, you can do one of the following:

1. (Easiest) Use the [Sifchain DEX](https://dex.sifchain.finance) and use our Keplr Wallet integration to setup a new Sifchain address. For directions on this, please refer to our instructions [here](https://docs.sifchain.finance/resources/sifchain-dex-ui#setup-or-integrate-your-sifchain-address-via-keplr-wallet-integration).
2. If running on K8s, Use [ruby](https://www.ruby-lang.org/en/documentation/installation/) to run the below two commands:
   1. `rake "keys:generate:mnemonic"` - This will generate a mnemonic for you.
      1. **Important:** write this mnemonic phrase in a safe place. It is the only way to recover your account if you ever forget your password.
   2. Take this generated key and run: `rake "keys:import[<moniker>]"`
      1. This will give you your newly generate Sifchain address.
3. If running locally, run Command `sifnodecli keys add <name>`.  This command will give you your: address, public key, and mnemonic phrase.&#x20;

## How can I view my eROWAN in my MetaMask Wallet?

Since eROWAN is a new token, it will not appear in the default list of tokens displayed by MetaMask. There is an easy way to fix this in 3 steps:

1. From the main view in MetaMask, scroll down on the “Assets” tab and select “Add Token”

![](<../.gitbook/assets/Screen Shot 2021-01-19 at 1.53.56 PM.png>)

1. Select the “Custom Token” tab and input the Token Contract Address for eROWAN — `0x07baC35846e5eD502aA91AdF6A9e7aA210F2DcbE` then select Next.

![](<../.gitbook/assets/Screen Shot 2021-02-10 at 10.28.20 AM.png>)

1. Confirm the token by selecting “Add Tokens” on this final screen.

![](<../.gitbook/assets/Screen Shot 2021-02-10 at 10.28.36 AM.png>)

Once the eROWAN token has been successfully added, you should see a screen similar to the one shown here.

![](../.gitbook/assets/Complete.png)

## How can I convert my eROWAN to ROWAN?

In order to convert your eROWAN to ROWAN, you will use the Sifchain DEX. For step-by-step directions on how to convert eROWAN to ROWAN, as well as move other Ethereum assets into our low-fee network, read the section "[Pegging Assets into Sifchain](sifchain-dex-ui.md#peg-assets-into-sifchain-tutorial)" in the Sifchain DEX User Guide.
