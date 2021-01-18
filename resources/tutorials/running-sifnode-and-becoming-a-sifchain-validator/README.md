# Running Sifnode and becoming a Validator

## Sifchain Validator Tutorial

There are multiple ways to get started with Sifnode and to become a validator of the network:

* 1\) On your Ubuntu server \(EC2/Digital Ocean or local\).
* 2\) Via [Kubernetes](https://docs.sifchain.finance/resources/tutorials/running-sifchain-validator-on-kubernetes) \(**recommended** for validators and node operators\).

### Pre-requisites:

* Make sure your provisioned EC2 machine meets the following requirements:
  * **Hardware:**
    * Minimum**:** 2 vCPU, 4 GB RAM
    * Recommended: 4vCPU, 8 GB RAM
  * **Storage**:
    * Minimum: 50GB SSD
    * Recommended: &gt;= 100 GB SSD. 200GB to be on the safer side.
    * Notes:
      * An archival node \(pruning = "nothing" \) grows at a rate of ~50 GB per month
      * A fully pruning node \(pruning = "everything" \) grows at a rate of ~10 GB per month\
      * A default pruning node \(\`pruning = “default”\) grows at a rate of ~20 GB per month



### Video Tutorial

{% embed url="https://www.youtube.com/watch?v=1kjdjCEcYak&feature=emb\_title" %}



