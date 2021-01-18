# Validator Security

Each validator candidate is encouraged to run its operations independently, as diverse setups increase the resilience of the network. Validator candidates should commence their setup phase now in order to be on time for launch.

### Key Management - HSM <a id="key-management-hsm"></a>

It is mission critical that an attacker cannot steal a validator's key. If this is possible, it puts the entire stake delegated to the compromised validator at risk. Hardware security modules are an important strategy for mitigating this risk.

Recommended hardware for storing private keys Yubikey and Ledger Nano \(support coming soon\)

We will update this page when more key storage solutions become available.

### Sentry Nodes \(DDOS Protection\) <a id="sentry-nodes-ddos-protection"></a>

Validators are responsible for ensuring that the network can sustain denial of service attacks.

One recommended way to mitigate these risks is for validators to carefully structure their network topology in a so-called sentry node architecture.

Validator nodes should only connect to full-nodes they trust because they operate them themselves or are run by other validators they know socially. A validator node will typically run in a data center. Most data centers provide direct links the networks of major cloud providers. The validator can use those links to connect to sentry nodes in the cloud. This shifts the burden of denial-of-service from the validator's node directly to its sentry nodes, and may require new sentry nodes be spun up or activated to mitigate attacks on existing ones.

Sentry nodes can be quickly spun up or change their IP addresses. Because the links to the sentry nodes are in private IP space, an internet based attacked cannot disturb them directly. This will ensure validator block proposals and votes always make it to the rest of the network.



