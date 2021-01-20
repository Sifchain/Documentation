---
description: >-
  Reference this document for getting Sifnode setup and starting the process to
  becoming a validator in the Sifchain Network
---

# Running Sifnode & Becoming a Validator

## Prerequisites <a id="9cbf"></a>

* Make sure your provisioned EC2 machine meets the following requirements:
  * **Hardware:**
    * Minimum**:** 2 vCPU, 4 GB RAM
    * Recommended: 4vCPU, 8 GB RAM
  * **Storage**:
    * Minimum: 50GB SSD
    * Recommended: &gt;= 100 GB SSD. 200GB to be on the safer side.
    * Notes:
      * An archival node \(pruning = "nothing" \) grows at a rate of ~50 GB per month
      * A fully pruning node \(pruning = "everything" \) grows at a rate of ~10 GB per month
      * A default pruning node \(\`pruning = “default”\) grows at a rate of ~20 GB per month

_This tutorial assumes that you have at least a basic understanding of setting up AWS and configuring your access keys accordingly, so that you may interact with AWS via the CLI Tool._

**What is Kubernetes? \(k8s\)**

[Kubernetes](https://kubernetes.io/) is a portable, extensible, open-source platform for managing containerized workloads and services, that facilitates both declarative configuration and automation. It has a large, rapidly growing ecosystem. Kubernetes services, support, and tools are widely available.

Here's the rough breakdown of the overall cost of running a node :

* $73 per month for the EKS Control Plane
* $137 per month for a t2.xlarge instance
* $70 in load balancer costs
* $100 in disk costs

**Install Dependencies:**

* [Ruby 2.7.x](https://www.ruby-lang.org/en/documentation/installation)
* [Golang](https://golang.org/doc/install)
* [JQ JSON Processor](https://stedolan.github.io/jq/)
* [AWS CLI Tool](https://aws.amazon.com/cli/)
* [kubectl](https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html)
* [Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli)
* [Helm](https://helm.sh/docs/intro/install/)

**Configure AWS CLI Tool:**

We are going to be using the Amazon Elastic Kubernetes Service \(Amazon EKS\) for this tutorial. make sure you have admin access to a AWS account before starting this tutorial. After installing the [AWS CLI tool](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html) locally on your machine, next you need to add some AWS account credentials to complete the installation.

Head over to the AWS IAM console and create a new User with the following permission settings

![](../../../.gitbook/assets/screen-shot-2021-01-05-at-4.46.21-am.png)

![](../../../.gitbook/assets/screen-shot-2021-01-05-at-4.52.15-am.png)

Proceed to review and create the user. In the next screen you will be shown some credentials \(Access Key and secret\). Keep these handy as we'll be using them in the next step.

```text
aws configure
AWS Access Key ID [None]: <ENTER YOUR ACCESS KEY>
AWS Secret Access Key [None]: <ENTER YOUR ACCESS SECRET KEY>
Default region name [None]: us-west-2
Default output format [None]: json
```

#### Configure kubectl tool

Amazon EKS uses IAM to provide authentication to your Kubernetes cluster through the [AWS IAM authenticator for Kubernetes](https://github.com/kubernetes-sigs/aws-iam-authenticator). You can configure the stock `kubectl` client to work with Amazon EKS by installing the AWS IAM authenticator for Kubernetes and modifying your `kubectl` configuration file to use it for authentication.

Complete kubectl installation by installing aws-iam-authentication tool

[https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html](https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html)

### Network and Node Setup

Please refer to this [link](https://github.com/Sifchain/sifnode/blob/develop/docs/chainOps/k8s.md) for the most up to date and accurate directions on how to finish this setup.

### Stake your Node:

Now that you have your node up and running and you have ROWAN to stake with, you must now execute the following command:

* `sifnodecli tx staking create-validator` 
  * In order to execute this command, there are several decisions that must be made in relation to your node. Some of these settings will not be editable after creation \(pointed out below\), so please be sure about the values you are setting:
    * **commission-max-change-rate &lt;max-rate-change&gt;**
      * This is the most that you will be able to change your commission rate at a time. This value IS NOT editable after validator creation. Commission rates can be changed only once every 24 hours.
    * **commission-max-rate &lt;max-rate&gt;**
      * This is the highest rate that your validator node will be able to charge. This value IS NOT editable after validator creation.
    * **commission-rate &lt;rate&gt;**
      * This is the starting commission rate that your validator node will charge its delegators. This value IS editable after validator creation.
    * **amount &lt;amount&gt;** 
      * This is the amount of your starting self-delegation. This can be both unbonded and added to later.
    * **pubkey $\(sifnoded tendermint show-validator\)** 
      * This is the public validator key associated with your node.
    * **moniker &lt;moniker&gt;**
      * This is the publicly viewable name of your node.
    * **chain-id &lt;chain-id&gt;**
      *  This is the identifier of the network the node is connecting to.
    * **min-self-delegation 1** 
      * This is the minimum number of tokens that the node must delegate to itself.
    * **gas auto** 
      *  ****This is the amount of gas submitted for the create validator transaction.
    * **from &lt;moniker&gt;** 
      * This is a reference to the signer of this transaction \(your validator address/moniker\).
    * **keyring-backend file**
      * This specifies the location of your node’s keyring.
* Next, you can verify that this was executed correctly by running this command: `sifnodecli query staking validator <validator-address> .` This will return information about your validator.

After you have setup your node and successfully staked it with ROWAN, you are now considered eligible to be a part of Sifchain's validator set. Please reference our [guide on being a Validator here for additional information](https://docs.sifchain.finance/roles/validators).   


