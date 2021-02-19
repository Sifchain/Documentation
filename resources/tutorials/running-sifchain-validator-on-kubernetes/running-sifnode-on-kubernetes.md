---
description: Your guide for setting up Sifnode and becoming a validator on the K8s network
---

# Running Sifnode on Kubernetes

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
  * Add export GOPATH=~/go to your shell
  * Add export PATH=$PATH:$GOPATH/bin to your shell
* [JQ JSON Processor](https://stedolan.github.io/jq/)
* [AWS CLI Tool](https://aws.amazon.com/cli/)
* [kubectl](https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html)
* [Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli)
* [Helm](https://helm.sh/docs/intro/install/)

**Configure AWS CLI Tool:**

Please ensure you setup the AWS CLI as per the tutorial [here](https://aws.amazon.com/cli/).

#### Configure kubectl tool

Amazon EKS uses IAM to provide authentication to your Kubernetes cluster through the [AWS IAM authenticator for Kubernetes](https://github.com/kubernetes-sigs/aws-iam-authenticator). You can configure the stock `kubectl` client to work with Amazon EKS by installing the AWS IAM authenticator for Kubernetes and modifying your `kubectl` configuration file to use it for authentication.

Complete kubectl installation by installing aws-iam-authentication tool

[https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html](https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html)

### Network and Node Setup

Please refer to this [link](https://github.com/Sifchain/sifnode/tree/master/docs/chainOps/k8s) for the most up to date and accurate directions on how to finish this setup.

### Stake your Node:

Once you are done with the network and node setup, refer back to our [parent page on how to stake your node ](https://docs.sifchain.finance/resources/tutorials/running-sifchain-validator-on-kubernetes#stake-your-node)to become a validator in our validator set.

