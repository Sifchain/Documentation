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

![](../../.gitbook/assets/screen-shot-2021-01-05-at-4.46.21-am.png)

![](../../.gitbook/assets/screen-shot-2021-01-05-at-4.52.15-am.png)

Proceed to review and create the user. In the next screen you will be showing some credentials \(Access Key and secret\) Keeps these handy as we'll be using them in the next step.

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

## Network and Node Setup

Please refer to this [link](https://github.com/Sifchain/sifnode/blob/develop/docs/chainOps/k8s.md) for the most up to date and accurate directions on how to finish this setup.  This documentation also includes demo videos to easily follow.





