# Sifchain Consensus

Sifchain’s consensus mechanism includes Tendermint’s consensus engine with reasonable parameters to secure on-chain trading.

Sifchain validators stake their own Rowan, and Rowan delegated to them by other Rowan holders. Sifchain’s consensus set consists of the top 100 validators with the highest quantity of Rowan staked. This set changes from time to time as validators willingly leave the consensus set or are forced out. If they are forced out, it may be because they’ve been slashed or because they are no longer among the n highest staking validators \(where n is a threshold set by governance\). At network launch, n will be set to 100

Sifchain will routinely check the relative amount of Rowan staked among all validators and reset the top n validators. This could happen as frequently as every block, depending on the performance costs. Sifchain must also be able to readily remove any validator from the consensus set as a part of [slashing](https://docs.cosmos.network/master/modules/staking/02_state_transitions.html#slashing) it \(this is called “jailing”\). See also [tombstoning](https://docs.cosmos.network/master/modules/slashing/07_tombstone.html).

For up-to-date information on all settings and configurations, please reference the [Validators section](https://docs.sifchain.finance/roles/validators) within the Roles area of our document site.

