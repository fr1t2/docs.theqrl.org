---
title: Multi Signature Address
categories: wallet
description: The QRL Multisig address documentation
tags: wallet
---


With the latest Hard Fork XXXX, creation of "Multisig" addresses is now possible. This creates the possibility for multiple parties to control and approve spending funds in an shared address.

## What is a MultiSig address?

A multisig address is a transaction ID or TX_ID consisting of multiple QRL addresses combined into a single address that can accept funds, but requires multiple signatures to transfer from the address. 

Only those addresses identified during the creation of the multisig address are allowed to vote, and depending on the weight assigned to each address some or all of the identified addresses are required to approve. 



## Creating a MultiSig Address

From the QRL wallet software, browse to the Tools section and select the "MultiSig" option.


- **Signatory** - Requires a QRL address allowed to vote on a spend transaction and a weight of the address voting power. Multiple addresses can be entered by selecting the *Add Another Signatory* button
- **Threshold to spend** - The total of all signatories required to approve the transaction. This must be equal or less than all of thresholds so it may be achieved.
- **Fee** - QRL transaction fee used to create the multisig address
- **OTS Key Index** - the OTS key to be used for the multisig create transaction


> Note: the there is a limit of 100 addresses that can be a part of any multisig transaction
{: .info}

Once all of the information is entered confirm the transaction and broadcast to the network to create the multisig address. 

The new multisig address is shown on the top of the confirmation screen and will now show up under all of the signatories "Spend" and "Vote" tabs.

> This address is different from a traditional QRL address as it is created from the transaction hash and is not an XMSS tree by its self. 
{: .info}

Transfer funds to be used by this group to the new address like any typical transaction from a funded wallet. Any funds sent here will need approval by the group to transfer out later.


## Spend

Any member of the multisig address can initiate a "Spend" transaction, requesting that some funds be spent from the multisig address. This will use an PTS key of the address requesting the spend.

Once this transaction is posted to the blockchain, the other members can vote to approve or reject the spend.

To create the spend transaction browse to the Tools section --> Multisig and select the **Spend** tab.

Once here select the multisig address you wish to spend from using the "Select Address" button. A single wallet may be a part of multiple multisig addresses, they will be shown in a list here.

You are presented with a screen to enter the transaction details.

- **Recipient** - Address to transfer funds to
- **Amount** - How much to send from the multisig address
- **Expiry block number** - If this block number is reached without enough votes, the transaction will not be spent.
- **Fee (In Quanta)** - For the spend transaction to be broadcast to the network
- **OTS Key Index** - OTS used to sign the spend transaction.

Enter the details for the transaction and send to the blockchain. Now the other members of the multisig group can vote on the spend transaction. 


## Vote

Once a spend transaction has been created and broadcast to the network all members are allowed to vote. 

To vote on the spend transaction browse to the Tools section --> Multisig and select the **Vote** tab.

Again you will need to select the multisig address you wish to vote on a transaction for.

Once selected any available spend transactions that have been relayed to the network will show in the list presented. 

Select the transaction to vote on and a window will be presented for you to vote, select approve or reject. 
