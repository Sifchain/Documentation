---
description: FAQ and troubleshooting on validators
---

# Troubleshooting

## Jailing / Un-Jailing

**If I want to unjail or execute other commands would I use the --node flag from my local machine's sifnodecli or is there a way to execute through kubectl without having to log into the pod directly?**   
 No need to log into the pod, as with the mnemonic you can drive your node from anywhere.

**Any solutions to the jailing problem even when the node is running?**   
 If you don't save the validator key, then it can't sign blocks and will be jailed all the time. You should always backup this key ~/.sifnoded/config/priv\_validator\_key.json if you already created a validator.

**After UnJail: "jailed": false, "status":1. So I can't see my Validator Node in Dashboard**   
 It normally takes a few minutes for the block explorer to see the updates.

**failed to get from fields: The specified item could not be found in the keyring.** Try adding --keyring-backend=file to that command.

**How can I unjail my validator?**   
 Please make reference to the documentation: [https://docs.sifchain.finance/roles/validators/validator-cli-commands\#slashing](https://docs.sifchain.finance/roles/validators/validator-cli-commands#slashing)

## Validator

**I have created a validator but I’m not showing on the validator list. Any ideas?**   
 Looks like you didn't stake much to be a validator? I'd try staking with a minimum of 10 rowan at this stage, so: 10000000000000000000rowan Also, make sure your node is fully synced

**Could you elaborate on what a double-sign infraction is?**   
 \([https://docs.sifchain.finance/roles/validators\#future-additions](https://docs.sifchain.finance/roles/validators#future-additions)\).

\*\*How to increase the stake to my validator?   
 You can use the [Delegator CLI commands](https://docs.sifchain.finance/roles/delegators/delegator-cli-commands) to delegate additional ROWAN to your validator

**I can't create a validator because the validator address exists. How can I change the validator address? Or do I need to recreate the account?**   
 You need to delegate more funds to the validator with the `sifnodecli tx staking delegate` command

**Trying to revive an existing validator from imported mnemonic**   
 You'd need to undelegate first, before you can re-create, from memory [https://docs.sifchain.finance/roles/validators/validator-cli-commands\#unbonding](https://docs.sifchain.finance/roles/validators/validator-cli-commands#unbonding) You should unbond, and then re-create.

**If I start from scratch but import an existing mnemonic I need to replace the priv\_validator\_key.json from my existing validator in the ~/.sifnoded/config/ directory?**   
 If a validator has already been created for your import wallet, then yes.

**So to become a validator part you need to be inside the container?**   
 No, the only thing you need to extract from the validator is the public key.

**How can I unbound my old validator?**   
 sifnodecli tx staking un-bond  990000000000000000rowan --fees 100000rowan --from BwareLabs --keyring-backend=file --chain-id=sifchain

**What will happen with the old validator? I don't want to appear un-jail. I don’t to appear on the unjail**   
 It'll sit in the unbonding state for 3 weeks, before it's removed \(default cosmos unbonding period setting\).

**Error when calling the command "sifnodecli q tender mint-validator-set"**   
 Add the flag --trust-node

**Do we need any tokens for validator status?**   
 The top 100 validators \(by amount bonded: staked & delegated\) determines who is in consensus and in return who earns rewards. In order to set up a node, you need to stake at least 1 Rowan.

**What validator is good to stake ? How to choose it?**   
 Check the top 100 in the [https://wallet.keplr.app/\#/sifchain/stake](https://wallet.keplr.app/#/sifchain/stake).

**I am going to close out my validator. How do I do that without getting slashed?**   
 [https://docs.sifchain.finance/roles/validators/validator-cli-commands\#unbonding](https://docs.sifchain.finance/roles/validators/validator-cli-commands#unbonding)

## Standalone

**With a standalone setup, to upgrade the docker image without having downtime I imagine I'd need to deploy and run a secondary instance, have it synced and signed \(i.e. running in parallel at this point\), then docker-compose pull docker-compose restart the primary. Does this sound reasonable?**   
 Yes, this is why we really recommend people use EKS for running their validators, as upgrades are automated and it reduces the possibility of being slashed.

**Is there a way to get notified of updates for those of us who use standalone \(not k8s\) installs?**   
 This is a process we'll put together soon. Even running standalone it should auto-upgrade.

**Once block height is achieved, do people have a time window to make the upgrade?**   
 Since most of the validators on the network are using cosmovisor \(by design\), there's very little time to make the upgrade before you get jailed. This is why we really don't want people compiling from source.

## Kubernetes

**Deployed k8s and started to index, after the node is full synced I should unjail my validator? I used the same mnemonic as for standalone solution**   
 You should create a new validator. The reason why is because the validator public key would have changed. Un-bond your old validator and then bond the new, with the new public key.

**Can i make changes in the sifnoded configuration within the AWS solution and connect again to the POD?**   
 Upgrades are all automated, so there won't need to make any changes if using k8s. As for making custom changes and restarting the pod - you can make all the changes you like to the config files. Then, to restart your pod just run: kubectl scale deployment sifnode --replicas=0 -n sifnode that will then shut the pod down, and once terminated, you bring it back up with: kubectl scale deployment sifnode --replicas=1 -n sifnode

**I noticed that the control plane SG did not open the p2p ports, unless I was missing something?** The p2p ports are available via the provisioned load balancer for the service.

**No pods can be found. For aws cli, I executed the aws configure configuration**   
 You'll also need to ensure that the security group assigned to the load balancer you set up for that port allows port 26660.

**How much time does it take for deploying the eks cluster with rake?**   
 ~20-25M to set up the cluster. Another few minutes to deploy the sifnode pod, which should then take about an hour to sync.

**Amazon EKS automatically detects and replaces unhealthy instances, but isn't this prune to double signing when a new instance is started to provide the HA ?**   
 1\) Auto-scaling of pods is disabled by default and 2\) we use the Recreate strategy, whereby a pod will be terminated before a new one is started.

**rake "keys:import\[moniker\]" .../sifnode$ sifnodecli keys show  --keyring-backend file sifnodecli: command not found**   
 You'd need to run make clean install to build sifnodecli

## Delegator

**What’s the delegation unbonding time?**   
 "The unbonding period is currently set to 21 days, during which time the tokens will not be usable and will still be susceptible to slashing. After the unbonding period the tokens will be fully released to the source address." You can read it here: [https://docs.sifchain.finance/roles/delegators](https://docs.sifchain.finance/roles/delegators)

**Is it possible to cancel an undelegated request after it was successfully completed so that a redelegate request can be done instead?**   
 1\) You can simply re-delegate your delegation from one validator to another without having to wait the 21 day unbonding period. 2\) If you are wanting to 'transfer tokens from 1 of your addresses to another address that is already staked/delegated', you cannot do that. You will need to undelegated and then move these to your new account and then restake/redelegate.

**If someone wanted to redelegate to my validator node but they made the mistake to undelegated instead and was wondering if it's any way possible to redelegate while in the 21 days undelegated period.**   
 No, I don't believe it is possible.

**What are the benefits of delegating tokens to a validator? I see 5% commission, anything i can read about it?**   
 Please read here: [https://docs.sifchain.finance/roles/delegators](https://docs.sifchain.finance/roles/delegators)

**Got this error in the block explorer: staking: validator already exist for this operator address; must use new validator operator address: failed to execute message; message index: 0**    
 Try delegating more using the command: sifnodecli tx staking delegate -- .Run it with -h to see the options.

## Rewards

**Where can I see my rewards?**   
 For LPs: You can see your current claimable amount here: [https://dex.sifchain.finance/\#/rewards](https://dex.sifchain.finance/#/rewards) as well as other important fields about your reward position. You can also see even more details here: cryptoeconomics.sifchain.finance

**How to calculate block rewards?**   
 When the validator is the proposer of the round, that validator \(and their delegators\) receives between 1% and 5% of fee rewards, the reserve community tax is then charged, then the remainder is distributed proportionally by voting power to all bonded validators independent of whether they voted \(social distribution\). So every block, fees are collected, then the proposer bonus is taken out, then the fees are divided between the validators proportionally with their stake. From there, within each validator, the rewards are divided proportionally to each delegator minus the commission rate. HOWEVER! inflation to block rewards is coming VERY soon \(meaning that these returns will be much higher\). But in the meantime, our validator subsidies \(ie the liquidity mining program\) will be more than enough to cover the lack of high block rewards at the moment

**What would be the proper format to check outstanding rewards?**   
 '''sifnodecli query distribution validator-outstanding-rewards    --node "://localhost:26657" '''

## General

**What are the differences between eks and standalone nodes?**   
 EKS is "heavier" than running a standalone node, but it's our preferred way and is far more reliable. Not only that, but as more and more services are added to the network, there will likely be additional nodes that validators will need to run and EKS provides the ability to seamlessly and easily deploy and manage those services.

**What are the Sifchain validator nodes? Does it make sense to delegate my tokens to them?**   
 The Sifchain nodes are Alice, Jenna, Lisa, Mary, Sophie, Ambre, Elizabeth, and jane. All block rewards earned by these nodes will be distributed to other nodes. We recommend against delegating to our nodes

**Is there any command I can run to query slashing rules \(so to see time period of downtime, max number of blocks that one must miss etc\)**   
 slashing subcommands `sifnodecli q slashing -h`

**Can you give me a example on how to change commision to 1%**   
 It'd probably be something like: sifnodecli tx staking edit-validator --commission-rate 1 --from  --keyring-backend file --node tcp://:26657 \(obviously replacing  with the name of your moniker in your keyring\). You can also add the flag --dry-run before running it, to test what it will do.

**How do you import your mnemonic locally?**   
 `rake keys: import[<moniker>]`

**Could we replace and restart the node before the height?**   
 No way. That will cause all sorts of issues. This is exactly why we recommend Kubernetes and if you must, the Docker \(standalone\) release. Compiling directly is problematic.

**Regarding node security, which tcp port should be open on firewall for the validator \(any other port besides 26656\)?**   
 26656 is the minimum. You can open 26657, but maybe restrict who can access that.

**Expose public key**   
 `rake "validator:expose:pub_key[<cluster>,<provider>,<namespace>]"`

**How to run a node with a completely new mnemonic?**   
 Delete your pod rake "cluster:namespace:destroy\[,aws,sifnode,true\]" Generate a new mnemonic Redeploy sifnode with your new mnemonic.

**Which branch to checkout for betanet to make clean install?**   
 step 1: `git clone https://github.com/Sifchain/sifnode` step 2: `git checkout master && git pull` step 3 is then the install command

**Trying to turn "prometheus" on I need to get prometheus and grafana working for my monitoring and alerts. What are you guys using?**   
 We use several, DataDog and are exploring public solutions based on Prometheus/Grafana etc. To enable prometheus: 1. Log into the pod: `kubectl exec --stdin --tty <pod name> -n sifnode -- /bin/sh` 2. Edit the file `/root/.sifnoded/config/config.toml` 3. Log out of the pod, and restart it: `Kubectl scale deployment Sifnode --replicas=0 -n sifnode` and then once it's terminated: `kubectl scale deployment sifnode --replicas=1 -n sifnode`

**I have Rowan at my Keplr wallet, how do I transfer it to the validatir wallet ?**   
 Once you have the address for the wallet you simply do a send transaction from within Keplr. You can also import the wallet into keplr.

**Is there any way to change commission-max-rate or commission-max-change-rate after the validator is created? I noticed there are no options for this in** _**sifnodecli tx staking edit-validator**_   
 You can pass docker compose flags to your instance....for example, you could provide a flag of '-d'and it would run the container in detached mode. \(It's a new, undocumented option, that we're testing.\)

**How to get Rowans and use the DEX?**   
 You can purchase from the DEX via the following steps. You will need ETH for ethereum transaction fees and also you can Peg one of the supported tokens within the dex:

* You would first transfer your ETH to your Metamask Wallet. 
* Go to [https://dex.sifchain.finance/\#/peg](https://dex.sifchain.finance/#/peg) and PEG your ETH to cETH: [https://docs.sifchain.finance/resources/sifchain-dex-ui\#pegging-assets](https://docs.sifchain.finance/resources/sifchain-dex-ui#pegging-assets). Quick video showing how to Peg: [https://youtu.be/tyM9hPNvzW4](https://youtu.be/tyM9hPNvzW4) 
* Ask an Admin to send you 1 ROWAN to pay the SWAP gas fee. 
* Click the SWAP tab within the DEX and swap your cETH for ROWAN. Quick video showing how to SWAP: [https://www.youtube.com/watch?v=jG1BExJt\_Bk](https://www.youtube.com/watch?v=jG1BExJt_Bk) 
* Go to [https://wallet.keplr.app/\#/sifchain/stake](https://wallet.keplr.app/#/sifchain/stake) and select one or more validators to stake with. Quick video showing how to Stake/Delegate: [https://youtu.be/\_\_Us35-Dt3w](https://youtu.be/__Us35-Dt3w)

**How to stake?**   
 These docs explain how to peg from eROWAN to ROWAN: [https://docs.sifchain.finance/resources/sifchain-dex-ui\#pegging-assets](https://docs.sifchain.finance/resources/sifchain-dex-ui#pegging-assets) as well as this video [https://www.youtube.com/watch?v=tyM9hPNvzW4&list=PLj5x\_t273CNiBvcH6GjI9gBPzMFm9BlCL&index=2](https://www.youtube.com/watch?v=tyM9hPNvzW4&list=PLj5x_t273CNiBvcH6GjI9gBPzMFm9BlCL&index=2). Afterwards, using your ROWAN you can stake \(delegate\), by referring to [https://www.youtube.com/watch?v=\_\_Us35-Dt3w](https://www.youtube.com/watch?v=__Us35-Dt3w).

**I pegged my erowan but i don’t see any rowan, what could be the problem?**   
 Pegging requires 50 blocks time

**Why Rewards on Keplr are so low?**   
 When the validator is the proposer of the round, that validator \(and their delegators\) receives between 1% and 5% of fee rewards, the reserve community tax is then charged, then the remainder is distributed proportionally by voting power to all bonded validators independent of whether they voted \(social distribution\). So every block, fees are collected, then the proposer bonus is taken out, then the fees are divided between the validators proportionally with their stake. From there, within each validator, the rewards are divided proportionally to each delegator minus the commission rate. HOWEVER! inflation to block rewards is coming VERY soon \(meaning that these returns will be much higher\). But in the meantime, our validator subsidies \(ie the liquidity mining program\) will be more than enough to cover the lack of high block rewards at the moment

**error ERROR: unknown address: account sif... does not exist**   
 Make sure that:

* You have funds \(you can take them from the faucet\) 
* Your node is fully synced

  Verify that docker container is running: -`cd deploy/docker/mainnet; docker-compose exec sifnode sh` \(open a shell in docker container\)

* `sifnoded tendermint show-validator`
* `docker-compose down`
* `rake "genesis:sifnode:boot[mainnet,<moniker>,'<mnemonic>',<gas_price>,<bind_ip_address>,'<flags>']"`     \(boot node again\)

**cETH fees are very high when pegging / unpegging transactions.**   
 There are few ways we are working on to reduce cETH fees when pegging / unpegging tokens:

* We’re currently working on a gas oracle which will allow us to dynamically estimate gas costs. 
* For multi-pegging/unpegging, we want to batch transactions by user. So if a user wants to peg/unpeg multiple currencies on the same chain, they’ll save. 
* We are also planning batch transactions across multiple users for further gas savings.

**What is the staking APY?**   
 [https://dex.sifchain.finance/\#/rewards](https://dex.sifchain.finance/#/rewards)

**How to get involved into Sifchain / How to Stake / How to start:**   
 when it comes to staking you can either:

* Set up your own validator\([https://github.com/Sifchain/sifnode](https://github.com/Sifchain/sifnode)\)
* Delegate your ROWAN to validators \([https://docs.sifchain.finance/core-concepts/liquidity-pool](https://docs.sifchain.finance/core-concepts/liquidity-pool)\). This solution allows you to stake without setting up a validator \(and paying a commission to the validator you delegate to\)

  If you are setting up your own validator, we highly recommend to do it on k8s \(and try it on the testnet before, so you make sure everything runs smoothly\)

  -When it comes to providing liquidity, take a look on our docs and understand the risks of asymmetric pooling adds \(compared to symmetric adds\) \(you can look into our docs here: [https://docs.sifchain.finance/core-concepts/liquidity-pool](https://docs.sifchain.finance/core-concepts/liquidity-pool)\)

  Here you can find articles on the Sifchain ecosystem, aims and relevant concepts: [https://medium.com/sifchain-finance](https://medium.com/sifchain-finance)

  -Also in the youtube channel [youtube channel](https://www.youtube.com/channel/UCybJH9xaQx0cemM9_S8ZInA) you will be able to see a lot of tutorials

**“Unkown failure” when LP or Pegging / Unpegging**   


* Check if you have enough ROWAN to pay the fees
* Increase the Gas Limit

**Is Thorchain a Sifchain competitor? What are the differences between Thorchain and Sifchain?**   


* [https://discord.com/channels/769209144515100693/775951939426320414/827838067426852874](https://discord.com/channels/769209144515100693/775951939426320414/827838067426852874)
* [https://medium.com/sifchain-finance/key-differences-sifchain-thorchain-db6c47127706](https://medium.com/sifchain-finance/key-differences-sifchain-thorchain-db6c47127706)

**Error :- no required module provides package github.com/belitre/gotpl;**   
 run go get github.com/belitre/gotpl in the root sifnode repo directory

**How to change moniker**   
 sifnodecli tx staking edit-validator --moniker  moniker is also stored in ~/.sifnoded/config/config.toml file I guess easy to find as it says moniker in the config file

**Instance deployed with 3 nodes running m5.2xlarge instances. Can this be changed?**   
 You can set the setting the variable cluster\_size in the sifnode block. An t2.large should be enough. Also: If you're familiar with Terraform, you can change the instance\_type config option, in the sifchain block, in the file .live//main.tf \(which will be where ever you cloned the repository to\) and re-run Terraform to apply the changes \(it will take your cluster down for ~15 minutes while it's re-sized, but this shouldn't be an issue with the recent changes to slashing we made\)

**Enter keyring passphrase: ERROR: ABCIQuery: Post failed: Post "**[http://localhost:26657/](http://localhost:26657/)**": dial tcp :26657: connect: connection refused'**   
 Add the flag: `--node tcp://<IP Address>:26657`

**ERROR: unknown address: Account does not exist**   


* Do you have ROWANS in the wallet?

  -Is your node is fully synced?

**Failed to get from fields: The specified item could not be found in the keyring**   
 Add the flag: `--recover --keyring-backend file` Or run: `make clean install` Make sure you have the necessary pre-requisites installed: [https://github.com/Sifchain/sifnode/blob/74726d45e9f2dfbf20068cf7d827e2177d017f98/docs/chainOps/standalone/tutorials/betanet.md\#prerequisites--dependencies](https://github.com/Sifchain/sifnode/blob/74726d45e9f2dfbf20068cf7d827e2177d017f98/docs/chainOps/standalone/tutorials/betanet.md#prerequisites--dependencies) and run\`sifnodecli keys add  -i --recover --keyring-backend file Also: you can generate, sign and broadcast a transaction from anywhere. It does not have to be on the node itself \(that's why there's a --node flag\). That's one of the nice things about the Cosmos SDK. So, we recommend just importing the key locally and running sifnodecli from there, whenever you need to generate/sign/broadcast a transaction. Just make sure your node is fully synchronised before trying to become a validator.

**Incorrect phassprase**   
 Delete the key ring \(in `$HOME/.sifnodecli`\), and then re-import it by running r`ake “keys:import[<moniker>]”` Or In your `~/.sifnodecli` directory there will be a sub-directory named keyring-sifchain \(or something to that effect\). You can delete this and then run: sifnodecli keys add  -i --recover --keyring-backend file \(replace  with what your moniker is\).But only do the above if you have your mnemonic saved somewhere.. Or this command inside the container- sifnodecli keys add  -i --recover --keyring-backend file

**--node flag, rpc endpoints**   
 --node flag is the RPC endpoint on the network you will broadcast to. For BetaNet this is tcp://rpc.sifchain.finance:80. For TestNet it's tcp://rpc-testnet.sifchain.finance:80.

**Which commands run inside the container?**   
 You don't really need to run any commands from inside the container \(apart from obtaining the validator's public key\). You can import the mnemonic outisde of it and run the various staking etc commands from there.

**rawlog: 'insufficient fee: insufficient fees; got: required: 100000rowan'** Add the flag `--fees 100000rowan` when launching the command

## Error

\*\* I have the following problem on syncing: sifnoded\[..\]: panic: Failed to process committed block \(66880:5812B75425A312DF5C639A8C273E93D6D85987B385BB3342D25271D415D42F14\): wrong Block.Header.AppHash. Expected F2BC265B95B215   
 If you want to compile your own, then you need to checkout tags/mainnet-genesis. In addition to that, you'll need to download Cosmovisor and set that up to run sifnode [https://github.com/cosmos/cosmos-sdk/tree/master/cosmovisor](https://github.com/cosmos/cosmos-sdk/tree/master/cosmovisor) Cosmovisor handles auto-upgrading. However note it's a non-standard approach to running a sifnode.

**I imported locally and got an address and public key. The public key I got after the import is different then what's running in the container \(i don't know if this matters\). Now when i run the validator create cmd I get 'failed to get from fields: The specified item could not be found in the keyring' here is my cmd:**  `sifnodecli tx staking create-validator \ --commission-max-change-rate="0.1" \ --commission-max-rate="0.1" \ --commission-rate="0.1" \ --amount="1rowan" \ --pubkey=sif...\ (output of 'docker exec -it 825fde6c1e10 sifnoded tendermint show-validator' not output of rake keys:import[<**moniker>]) --moniker=<moniker> \ --chain-id=sifchain \ --min-self-delegation="1" \ --gas-prices="0.5rowan" \ --from=<moniker> \ --node tcp://<IP ADDRESS>:26657 <br>` You must use the public key generated by sifnoded tendermint show-validator Also, add `--keyring-backend=file` to the above command. The amount is also too low. It should be at least 1000000000000000000rowan as amounts are expressed with the of 1e18.

**I get an error when running this - ERROR: invalid Bech32 prefix; expected sifvaloper, got sifvalcons**   
 You need to use the node operator address. you can get it from the explorer as you can see you provide the wrong address sifvalcons and sifnodecli is expecting sifvaloper you can go on your validator and get the operator address from there.

**rake aborted! Errno::ENOENT: No such file or directory - sifgen**   
 Launch in your shell: `export GOPATH=~/go` and `export PATH=$PATH:$GOPATH/bin` . If you did that, run: `make clean install`

## General steps or Outline

**Jailing issue**   
 `sifnodecli tx slashing unjail --gas-prices 0.5rowan --from validatorAddr --node sifchain` you can try something like this, this is the normal command on tendermint

**Un-Jailing general command:**   
 `sifnodecli tx slashing unjail`

### Missing blocks: 

1. Ensure that your validator is reachable on TCP ports 26656 and 26657, and that these ports are not blocked by your firewall. 
2. Update your sifnode config.toml \(found in /root/.sifnoded/config/config.toml on the container\) and set a value for external\_address, in the \[p2p\] section. 

   For example, if your public IPv4 address is 1.2.3.4, then that line in the config would look like: external\_address = "1.2.3.4:26656"

3. Or, move to AWS EKS \(k8s\). This is our preferred stack and as the network matures, there will be additional services you're going to have to run on your validators.

Also try: 1. Stop the container so that the sifnoded service is no longer running. 2. Go back into the container \(just open up a shell\) and delete the file /root/.sifnoded/config/addrbook.json 3. Start the container back up again.

Also try: 1. Stop your sifnode container. 2. Log into your container \(but don't start sifnoded\) and run sifnoded unsafe-reset-all 3. Start your container up and let it resync state from genesis. This shouldn't take long at all.

Also: Be sure that if the private key is sitting outside the container, copy it to inside the container and it fixed the problem.

If nothing worked so far: 1\)backup your private key file before running this. If it is missing all the blocks try to Copy private key to inside container `sudo cp /root/.sifnoded/config/ priv_validator_key.json /usr/local/sifnode/deploy/docker/mainnet/.sifnoded/config/` considering you deployed the sifchain at `/usr/local` otherwise replace this path to whatever your path is .Please **MAKE SURE YOU BACKUP priv\_validator\_key.json** at destination before doing that just in case you need to restore the private key file again. It just worked for me when my node was missing all the block.

### For standalone docker version: 

1. To find docker container ID: docker ps
2. To safely restart your node: docker restart 
3. To unjail a node `sifnodecli tx slashing unjail --keyring-backend file --from <Moniker> --gas-adjustment=”1.5” --gas=”200000” --fees 5000000rowan --chain-id sifchain`
4. To delegate more rowan tokens to your node `sifnodecli tx staking delegate YOUR_VALIDATOR_ADDR <amount*10^18>rowan --gas-prices=”0.5rowan” --from=YOUR_MONIKER --keyring-backend=file --chain-id=sifchain --node tcp://YOUR_IP_ADDR:26657`
5. To check if you are up to date with current block heights / check if node is synced `curl -Ss $(hostname):26657/status | jq -er ‘.result.sync_info’`
