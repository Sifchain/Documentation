# Peggy ethBridge Tutorial

First install dependencies:

```text

INFURA_PROJECT_ID="abcdebeedabcdebeed"

ETHEREUM_PRIVATE_KEY="0x00000000000000000000000000000000000000"

git clone https://github.com/Sifchain/sifnode

cd sifnode/smart-contracts

echo -e "ETHEREUM_PRIVATE_KEY=$ETHEREUM_PRIVATE_KEY\r\nINFURA_PROJECT_ID=$INFURA_PROJECT_ID" > .env

curl -sL https://deb.nodesource.com/setup_14.x | sudo bash -

sudo apt install nodejs

sudo npm install -g truffle

npm install dotenv

```

## Sifchain - Peggy/ethBridge Demo <a id="sifchain---peggyethbridge-demo"></a>

Peggy is a cross-chain ethereum bridge for cosmos-sdk based chains such as sifchain. This enables the pegging of ethereum assets that can then be used within the sifchain and ecosystem.

**Setup**

1. Follow the `readme.md` and make sure your `sifnoded` is running and synced [https://github.com/Sifchain/sifnode](https://github.com/Sifchain/sifnode)
2. Create a MetaMask ethereum address on the ropsten network and fund from a faucet [https://faucet.metamask.io/](https://faucet.metamask.io/)
3. Create a `./smart-contracts/.env` file
4. Export and Add your `ETHEREUM_PRIVATE_KEY=""` to the `.env` file
5. Setup an `infura.io` account and add your project id `INFURA_PROJECT_ID=""` to the`.env` file
6. Check your local `sifnoded` has synced with the latest block height; \` curl [http://35.166.247.98:26657/block](http://35.166.247.98:26657/block) \| jq .result.block.header.height



**Send eth into SifChain/Peggy address**

1. In a new terminal, query for your local address `sifnodecli keys list` and copy the address field
2. Change into the smart-contacts directory `cd ./smart-contracts`
3. Execute the sendLockTx.js script \(Send funds from your metaMask wallet into SifChain/Peggy\) \`truffle exec scripts/sendLockTx.js --network ropsten sif130ak88ylwxd6krketcsvurgydyva5wjp3ueunl eth 500000000000000000

`Note; uUpdate this command with your local address. Numbers are in wei.` Use [an ethereum](https://converter.murkin.me/) converter if needed.

1. Check sifchain address for the now pegged ethereum called `ceth`: `sifnodecli q account sif130ak88ylwxd6krketcsvurgydyva5wjp3ueunl` Note: again, update with your local address

**Send ceth back to your MetaMask address**

1. Execute a ethbridge burn tx \(un-peg funds\) `sifnodecli tx ethbridge burn sif130ak88ylwxd6krketcsvurgydyva5wjp3ueunl 0xdA6Df58317E6bf25F9B707E1BA27E41689e2229F 500000000000000000 ceth --ethereum-chain-id=3 --from=withered-sky --yes` Note: Update with your local sif address and ethereum receiver address
2. Check account balance has been reduced `sifnodecli q account sif130ak88ylwxd6krketcsvurgydyva5wjp3ueunl`
3. Wait about 5mins. Check account balance: `https://ropsten.etherscan.io/address/...` Note: update with your address.

Transfer 3 ETH -&gt; cETH \(Sifchain\)

`truffle exec scripts/sendLockTx.js --network ropsten sif14tm9600fx088jw55gypcwkwh04j34e9jp68t8r eth 3000000000000000000`

Check balance

`sifnodecli q account sif14tm9600fx088jw55gypcwkwh04j34e9jp68t8r | jq`

Transfer 2 cETH \(Sifchain\) -&gt; ETH

`sifnodecli tx ethbridge burn sif14tm9600fx088jw55gypcwkwh04j34e9jp68t8r 0x36d976254Ac9e0aEbe75a952daE46f4BcE9041e6 2000000000000000000 ceth --ethereum-chain-id=3 --from user -y`



### Video Tutorial

{% embed url="https://www.youtube.com/watch?v=z1EZcetmDMI&t=2s" %}



