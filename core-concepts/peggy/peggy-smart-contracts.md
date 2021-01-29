---
description: A brief overview to the various Peggy Smart Contracts
---

# Peggy Smart Contracts

### BridgeToken Contract

The BridgeToken Contract is an ERC20 token that the BridgeBank creates when a Sifchain native asset gets transferred to Ethereum for the first time. BridgeTokens are minted by the BridgeBank whenever a user transfers a Sifchain native asset to Ethereum. BridgeTokens are burned when a user transfers their BridgeTokens back to Sifchain.

### Valset Contract

The Valset Contract maintains a list of allowable validator addresses as well as their respective voting power. These addresses are then allowed to submit and sign off on prophecy claims. The CosmosBridge contract will call this contract to check if a user is in the active validator set.

### Oracle Contract

The Oracle Contract Maintains all prophecy claims as well as how many validators have signed off on them. When enough validators sign off on a prophecy, the oracle contract will let you know that the prophecy has become valid. Validators are used to call the oracle contract directly, but now they will call the newProphecyClaim\(\) function on CosmosBridge to both sign-off on and create the prophecy.

### BridgeBank Contract

The BridgeBank Contract stores all tokens that get locked in peggy to move across the bridge. Bridgebank will also unlock tokens that are coming from Sifchain to Ethereum. Bridgebank has admin roles to mint tokens that are Sifchain native. Bridgebank will also burn Sifchain native tokens that are moving from Ethereum back to Sifchain. BridgeBank will only unlock or mint at the command of the CosmosBridge contract. Only allowable Ethereum native tokens are allowed to move across the bridge. Four functions on Bridgebank control the flow of assets to and from Sifchain.

The below two functions deal with giving users tokens on Ethereum in exchange for their Sifchain assets or pegged assets:

```text
mint(
    address payable _intendedRecipient, // address of the user receiving tokens
    uint256 _amount // amount of tokens they will receive
)

unlock(
    address payable _recipient, // address where tokens will be sent
    string memory _symbol, // symbol of the token to be sent
    uint256 _amount // amount of tokens to send
)
```

The below two functions handle moving assets from Sifchain to Ethereum. The 'burn' function is called for cosmos native assets, and the 'lock' function is called for Ethereum native assets. Cosmos native assets are burned because the token will have certain interfaces implemented to burn other tokens with their approvals and this token is essentially just an IOU for an asset on Sifchain. This token that gets burned was minted by the BridgeBank contract calling the BridgeToken contract. Ethereum native assets are locked as our contracts do not have the ability to mint tokens such as DAI. These locked Ethereum assets then generate IOU's on Sifchain so that the user can trade on our DEX.

Before making a call to either burn or lock, you will have to call the token contract \(except when locking eth\) and approve the BridgeBank contract to spend the amount of tokens that you are transferring over the bridge. If eth is being transferred over the bridge, there is no approval to make, simply send the eth with the lock transaction and make sure that the amount of eth in wei exactly matches the '\_amount' you pass into the function. If the amount of eth does not match the '\_amount' variable, the function will revert.

```text
burn(
    bytes memory _recipient, // sifaddress
    address _token, // token address
    uint256 _amount uint256
)

lock(
    bytes memory _recipient, // sifaddress
    address _token, // token address, 0x if ethereum
    uint256 _amount // amount of tokens 
)
```

The BridgeBank Contract will maintain a list of both Sifchain native ERC20 tokens and Ethereum native ERC20 tokens that are allowable. The reason that this list needs to exist is because the relayer broadcasts transactions based off of token symbols in the ERC20. This created a condition where an attacker could spin up a new ERC20 token, give it a name of a token that was already in existence on Sifchain, lock the token in the BridgeBank, then receive that asset on Sifchain. Once they had that Sifchain asset, they would transfer it across the bridge back to Ethereum where they would receive real tokens and not the fake ones that they had locked up. The list removes the possibility of this behavior from occuring.

### CosmosBridge Contract

The CosmosBridge Contract creates and stores new prophecies, but delegates the signing off on prophecies to the Oracle contract. Once the oracle contract says that the prophecy claim has been signed off on, then the CosmosBridge makes a call to the bridgebank to unlock or mint the funds. Only Ethereum addresses that are allowable in the Valset contract will be able to create new Prophecies and sign off on them.

### Admin API

While designing Peggy, there were some unique design challenges that were faced. The main one being that the ERC20 token, `erowan`, that represented a claim to ROWAN on Sifchain, was going to be created before peggy and Sifchain being deployed to Mainnet. Because of this, a solution needed to be implemented to make eROWAN a cosmos native token that the BridgeBank controlled without using the `createNewBridgeToken` function as the token would already exist. To remedy this, an Admin API was built to wire in eROWAN as a Sifchain native even though the BridgeBank did not create the token. This led to the creation of the function `addExistingBridgeToken`, where an admin can wire in eROWAN as a Sifchain native asset. Only the admin can call this function. Calling this function adds the token to the cosmos native token allowable list so that it can be burned.

Additionally, a script was created to call this admin api and wire in eROWAN to the bridgebank. This script is called `setup_eRowan.js` and resides inside the scripts folder in the smart-contracts directory. There are instructions on how to use this script inside of the Deployment.md file.

## Smart contract Architecture

Currently, the smart contracts are upgradeable which allows us to fix them should any bugs arise. In time, the control of these smart contracts will be handed over to SifDAO for control or the admin abilities completely removed for full decentralization.  


