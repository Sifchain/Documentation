# Sifnode

**sifnode** is a command line blockchain application for running sifchain nodes and validators. It is built using Cosmos SDK and Tendermint and generated with [Starport](https://github.com/tendermint/starport).

{% embed url="https://github.com/Sifchain/sifnode" %}

## Command Line Interface

`sifnoded` is for launching the node and manipulating node related files, e.g. adding accounts into `genesis.json`.

Chain data, consensus key, node key and configuration files will be stored in `.sifnoded` folder, default location is `$HOME/.sifnoded`

`sifnoded init` Initialize private validator, p2p, genesis, and application configuration files 

`sifnoded collect-gentxs` Collect genesis txs and output a genesis.json file

`sifnoded migrate` migrate Migrate genesis to a specified target version 

`sifnoded gentx`gentx Generate a genesis tx carrying a self delegation 

`sifnoded validate-genesis`validate-genesis validates the genesis file at the default location or at the location passed as an arg 

`sifnoded add-genesis-account` Add a genesis account to genesis.json 

`sifnoded debug`Tool for helping with debugging your application 

`sifnoded start`Runs the full node 

`sifnoded unsafe-reset-all` Resets the blockchain database, removes address book files, and resets `priv_validator.json` to the genesis state

`sifnoded tendermind` Tendermint subcommands for export state to JSON

`sifnoded version` Print the current version of sifnoded 

