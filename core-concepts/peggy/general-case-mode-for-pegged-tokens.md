# Pegged Tokens \(General Case\)

## **Overview**

This document explains the cryptoeconomic security model for pegged tokens on the Cosmos Network.  We will begin with a general case model for basic token conversion and define key terms.  This general case is then extended to deal with implementation-based nuances, including market related elements, such as overcollateralization for exchange rate risk and the existence of an on-chain price oracle.  These elements are foundational for pegged tokens to implement so that they can reach widespread use by market participants.    
****

Wherever we use the terms “TKN” and “Atom” we are referring more broadly to native external tokens and native Cosmos tokens, respectively.  When we use the terms “cTKN” and “eAtom” we are referring more broadly to pegged external tokens and pegged Cosmos tokens, respectively.  In examples, we often use the minting and burning of cTKN, but the examples work just as well for the minting and burning of any pegged asset.

## **General Case Model**

### **Token Conversion Process** 

Here is the basic token conversion process: \(Various terms are shown in bold. They are explicitly defined in a later section\)

* Source Token to Pegged Token
  * Alice wants to move her source tokens from a source chain to a pegged chain. 
  * She sends those tokens to a lockup group on the source chain, which custodies the tokens. A lock event is generated.
  * The pegged chain is informed of this event through a relay process. It then interprets this event to create and mint new pegged tokens and assign them to Alice.
  * Alice now custodies those pegged tokens, which are an equivalent representation of the source tokens.
* Pegged Token to Source Token
  * Bob wants to get back source tokens, so he burns his pegged tokens, removing them from the pegged chain. A burn event is generated.
  * Through a relay process, the original source chain is informed of the burn event. It then interprets this event to remove an equivalent amount of those source tokens from the lockup group, sending them to Bob.
  * Bob now custodies source tokens native to the source chain.

Note that the source chain can be either an external chain or Cosmos.  Likewise for the pegged chain.

### **Definitions**

Source Chain - The blockchain where the tokens being considered were originally created and tracked. The chain which contains the canonical ledger for those tokens, their ownership, and supply. 

Source Tokens - The original tokens on this source chain

Lockup Group - A smart contract on ethereum that holds tokens or a transaction on sifchain that locks tokens on the source chain. The only way they can be removed from lockup is through interpreting a burn event that has come from the pegged chain through some relay process. 

Lock Event - An event message that is generated on the source chain whenever an amount of source tokens are locked up in the lockup group on their source chain

Pegged Chain - The second blockchain, where the value of the source tokens are being sent to

Pegged Tokens - A new type of token that is minted on the pegged chain that represents equivalent tokens on the source chain

Burn Event - An event message that is generated on the pegged chain whenever an amount of pegged tokens are burned on the pegged chain

Relay Process - A verifiably correct process that results in event messages being passed from one chain to another chain, and results in the second chain verifying that it now correctly knows the state of the first chain. 

### **Objective**

The core objective of this system is to create these pegged tokens, and to have users consider them as equivalent assets to their source tokens, that can be used and traded freely without worry. Our core definition of equivalence in this context is for the following claim to hold:  


At any point in time, any user can quickly and easily convert between pegged tokens and source tokens, with verifiably correct guarantees on availability, security, reliability, and censorship resistance for this process.

### **Trusted Peg**

Definition: A Trusted Peg is one for which the following hold for a relay process:

* Availability: The process will run as expected by them when needed to, ie., be available
* Security: The process will not run unless the expected conditions \(eg: lock event/burn event\) have occured correctly
* Reliability: The process will run correctly, ie, the correct messages/events will be relayed and minting/burning will happen correctly in accordance with the details of those mint/burn events. 
* Censorship Resistance: The process will be resistant to censorship

