# Running Sifnode and becoming a Sifchain validator

## Sifchain Validator Tutorial

There are multiple ways to run sifnoded. You can either run it on your Ubuntu server \(EC2/Digital Ocean or local\) or via [Kubernetes](https://docs.sifchain.finance/resources/tutorials/running-sifchain-validator-on-kubernetes) \(recommended for validators and node operators\).

If you wish to setup without Kubernetes stack, please follow the tutorial mentioned in the sifnoded project README \(linked below\)

Make sure your provisioned EC2 machine meets the following requirements

**Hardware**

Recommend: 4vCPU, 8 GB RAM

Minimal: 2 vCPU, 4 GB RAM

**Storage**

Recommended**:** &gt;= 100 GB SSD \(200GB to be on the safer side\)

Minimal: 50GB SSD

An archival node \(pruning = "nothing" \) grows at a rate of ~50 GB per month

A fully pruning node \(pruning = "everything" \) grows at a rate of ~10 GB per month

A default pruning node \(\`pruning = “default”\) grows at a rate of ~20 GB per month  
 

{% embed url="https://github.com/Sifchain/sifnode" %}



### Video Tutorial

{% embed url="https://www.youtube.com/watch?v=1kjdjCEcYak&feature=emb\_title" %}



