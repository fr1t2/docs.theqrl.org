---
title: Ledger Nano S
categories: wallet
description: The QRL Ledger Nano-S Wallet documentation
tags: [wallet, ledger, nano]
---

The QRL development team has added some new features with the latest release we are very excited about. 

* Support for Nano S and Nano X
* Multi-Tree support
* Plausible Deniability 


The QRL developers have worked to trim bits and bytes to get the XMSS trees to fit on the ledger. After the latest optimizations in the latest firmware one can now load multiple trees and store more than one wallet on the Ledger nano-s. 



### Multi-Tree Support

This new feature adds the ability to store multiple XMSS trees on your Ledger Nano. Each tree is limited still to 256 keys to user for transactions. 

![MultiTree Support](/assets/wallet/web/ledger-nano-s/keyspace-small.png)

This feature will allow you to store 2 QRL addresses with 256 available transactions each on your ledger. When you reach the end of your first address OTS key pool, you have the opportunity to send all funds to the second address and continue using the ledger. Once both trees have been consumed you will have to transfer funds away, and re-initialize the ledger to generate new keys. But don't worry too much, the wallet will warn you when your keys are running out. 


### Plausible Deniability

One of the most exciting features to roll out with this latest release is the ability to secure your funds from the *"$5 wrench attack"*. This new feature creates a secondary passphrase to open your ledger device with. 

This second account space allows another 2 QRL XMSS trees (Addresses) to be created on the Ledger. To access the new account space on your ledger you will enter the new passphrase you setup when you first power up the ledger. 

This will add an additional word to the 24 word mnemonic phrase, creating 2 word lists. THe first being the typical 24 word ledger recovery key, the second being the same 24 word phrase plus the additional word setup during configuration.


![MultiTree Support](/assets/wallet/web/ledger-nano-s/keyspace2.png)


To read more on the setup and configuration of the second account space see [this article from the Ledger team](https://support.ledger.com/hc/en-us/articles/115005214529-Advanced-passphrase-security)


> This feature is optional and there is no way to tell from the ledger if you have configured this extra space. Plausibly deniable and fully recoverable secure funds!


##### This guide will walk you through

* Installing the QRL App
* Initializing XMSS trees in the QRL App 
* Accessing your QRL Wallets with the Ledger Nano S
* Receiving a transaction over the network - *(Receive QRL)*
* Sending a transaction over the network - *(Send QRL)*
* Checking transaction details on the QRL Explorer, including your current wallet balance
* Manually setting the OTS Key Index on your Ledger Nano S device.

Being Quantum Resistant comes with some inherent challenges. Before using the QRL Ledger Nano S app for your wallet, there are a few quirks worth noting about QRL. 
 
### OTS Key Index

When you create a new wallet you create an XMSS tree, which is comprised of many one time use signatures. Every signature is referenced as your OTS index or [One Time Signature](/developers/ots) key index. The ledger will now hold 2 XMSS trees (QRL Addresses) in it's memory space. 

**The OTS key index is limited.** 

You can only use each key **ONCE**. When you've used your _last_ key, you will no longer be able to sign transactions. ~This cannot be stressed enough!~

{: .info}

Your Ledger Nano S will keep track of OTS keys for you, however if you ever lose the device and need to reinstall on a new device, you will have to reset your XMSS index inside the [QRL Web Wallet](https://wallet.theqrl.org/). You can rely on the state of the node you're communicating with; however this will not keep track of failed transactions where a signature was broadcast to the network and subsequently failed. It is best to track all OTS key usage elsewhere to ensure you never reuse the same OTS key.

> **NOTE** With your last key you must empty your wallet. If you use all of your OTS Key Indexes with funds in the wallet, these funds will be **lost FOREVER** (Don't worry, there are plenty of warnings along the way.) The [QRL Web Wallet](https://wallet.theqrl.org/) will provide ample warnings you are running low on OTS Keys (<=50) to ensure you have plenty of time to move your coins to a new address. It is up to you to move them, however!

### Ledger Nano S Specific Quirks

* Track all OTS Keys used in a spreadsheet
* Store your Ledger Device seed (mnemonic) somewhere safe, in an encrypted manner if possible (Recommended you have this information stored in multiple physical locations)
* Currently the QRL Ledger Nano S app does not support the creation and sending of QR Tokens on the QRL Network. Only native Quanta (QRL) transfers and Message Transaction types and derivatives of are currently supported. A future release of the QRL Ledger Nano S app will support token creation, sending and slave transaction functionality.

## Installing the QRL Ledger Nano S Application

Using the [Ledger Live](https://www.ledger.com/pages/ledger-live) application, follow these instructions:

1. Open the **Manager** in Ledger Live
2. Connect and unlock your Ledger Nano S
3. Allow the Manager on your Ledger Nano S device by pressing the right button if asked
4. Search the App catalog for **QRL**, and click the **Install** button next to the QRL app.
	- An installation window will appear, and your device will display **Processing...**
	- The QRL App installation has completed on your Ledger Nano S

## Initialising the QRL App

Before you can use the QRL Ledger Nano S App, it must first be initialised. The initialisation process will generate an XMSS tree on your Ledger Nano S device, which is a unique aspect of the QRL Network's signature scheme. This process only has to be completed once on your Ledger Nano S device. Please allow up to 45 minutes for this process to complete for each tree. 

To initialise your Ledger Nano S device for use with the QRL App, follow these instructions:

1. Make sure your Ledger Nano S device is powered on and unlocked.
2. Open the **QRL** app on your Ledger Nano S
3. Your Ledger Nano S device will show **QRL (Tree 1) not ready**. Scroll down and press both buttons on the **Init Device** menu option.
4. Your Ledger Nano S device will show **QRL (Tree 1) keygen: 001/256**. This will slowly progress until all 256 keys have been generated.
5. When this process has completed, your Ledger Nano S device will show **QRL (Tree 1) READY rem:256** - indicating your device has finished generating tree 1 OTS keys, and you have 256 OTS Keys remaining in this Tree.
6. Scroll down in the menu and chose **Switch Tree** with both buttons. You will now see **QRL (Tree 2) Not Ready**
7. Initialize Tree 2 following the same steps above. Again this process will take about 45 minuets to complete.

> ![Initializing Tree 1](/assets/wallet/web/ledger-nano-s/init-crop.gif) Generating XMSS Tree 1 on the ledger. This will take a while, have patience.

Your Ledger Nano S device has been initialised for the QRL app, and contains 2 addresses (XMSS Trees) ready to deposit funds to. 2 addresses contain 256 OTS keys each which can be used to sign transactions on the QRL network.


| QRL_Tree | OTS_Keys | Address |
|-----|--|:--| 
| QRL (Tree 1) | 256 OTS | Q00040043096f536b68eb366425fec3c74414b9a9d345368e7554923b67cbbcaafe577d33e78f3c |
| QRL (Tree 2) | 256 OTS | Q000400c722c2198837153a6979ff3ddcc385fd9956e9a49ce8696829e2a2f38a5ee40365da6ee2 |



## Accessing your QRL Wallet with the Ledger Nano S

> **NOTE** If you are a Firefox user, ensure you have enabled **u2f** before proceeding. [Enabling U2F support in Mozilla Firefox](https://support.yubico.com/support/solutions/articles/15000017511-enabling-u2f-support-in-mozilla-firefox)
**Chrome Users** Please note there is a bug with chrome that will not allow the ledger to work. Please use another application or download the [qrl wallet](https://theqrl.org)
{: .info}

1. Make sure your Ledger Nano S device is powered on, unlocked and the QRL App is open.
2. Select the tree you wish to open by scrolling to **Switch Tree** in the QRL menu and selecting with both buttons
3. Visit [https://wallet.theqrl.org/](https://wallet.theqrl.org/) in your browser.
4. Click **Open Wallet** on the left hand menu.
5. On the right hand side, select **Ledger Nano S** in the drop down menu.
6. Click the **Open Ledger Nano S** button.

![Open QRL Ledger Nano S Wallet](/assets/wallet/web/ledger-nano-s/openWallet.png)

THis will present you with the opened QRL wallet ready to send or receive as seen below.

![Opened QRL Ledger Nano S Wallet](/assets/wallet/web/ledger-nano-s/opened.png)

## Receive QRL

You should **always** verify the address shown in the [QRL Web Wallet](https://wallet.theqrl.org/) matches the address shown on your Ledger Nano S device. To confirm your address, click the **Click to Verify** button on the receive tab of the wallet. 


![Address Verification Ledger Nano S Wallet](/assets/wallet/web/ledger-nano-s/AddressVerification.png)

Your QRL address will appear on your computer, and on your Ledger Nano S device.

![Address Verification Ledger Nano S Wallet](/assets/wallet/web/ledger-nano-s/verify.gif)


Once you've confirmed your address on both devices, you can send your QRL address to whomever you are receiving coins from.

> **NOTE** In the event you find the addresses do not match, you should immediately reach out to the QRL Team to report the issue - [security@theqrl.org](mailto://security@theqrl.org) This could occur in the event a malicious actor has taken control of the QRL Web Wallet. 
{: .info}

![QRL Receive](/assets/wallet/web/ledger-nano-s/receive.png)

## Send QRL

With the wallet unlocked, you can now send QRL.

![QRL Send](/assets/wallet/web/ledger-nano-s/send.png)

To send QRL there are four fields you need to fill in:

| Field |  Description  |
|:-----|:--| 
| **Recipient Address** | A valid QRL address |
| **Amount** | How much QRL to send |
| **Fee** | How much you are paying to make this transaction |
| **OTS Key Index** | Enter an unused OTS Key |

Make sure everything is correct and click the confirm button. You will get another confirmation of your transaction details.

![QRL Confirm Transaction](/assets/wallet/web/ledger-nano-s/confirm-txn.png)

If you are happy with the transaction details, click the **Sign with Ledger** Button.

A window will appear prompting you to confirm the transaction details on your Ledger Nano S device.

![QRL Ledger Nano Confirm Transaction](/assets/wallet/web/ledger-nano-s/SendQuanta.png)

On your Ledger Nano S device, you can press **View transaction** to verify the From and To addresses, Amount(s) and Fee.

![QRL Ledger Nano View Transaction](/assets/wallet/web/ledger-nano-s/sendQuantaSigned.png)

When you've confirmed these details, proceed to press **Sign transaction**.


![QRL Ledger Nano Sign Transaction](/assets/wallet/web/ledger-nano-s/sign.gif)


Signing will take a few seconds. When complete, you will see the following back on the QRL Wallet.

![QRL Ledger Send Transaction](/assets/wallet/web/ledger-nano-s/ledger-send-txn.png)

To complete the transaction into the QRL Network, click the **Send transaction** button.

You will see a progress tracker while your transaction is mined into a block.

![QRL Ledger Awaiting Block](/assets/wallet/web/ledger-nano-s/ledger-await-block.png)

When the transaction is confirmed in the network, your Transaction History will automatically update to reflect your transaction.

![QRL Ledger Transaction Complete](/assets/wallet/web/ledger-nano-s/ledger-txn-complete.png)


## Check Wallet Balance

With the wallet opened you can see the balance in the main screen of the web wallet. You can also check your wallet balance without opening the wallet by browsing to the [QRL Explorer](https://explorer.theqrl.org) and entering your address into the search field.

![QRL Explorer](/assets/explorer/explorerFull.png)

You will see all of the transactions the address has as well as the balance of quanta and any tokens held by the wallet.

## Manually Set the XMSS Index on your Ledger Nano S device

In the event you lose your Ledger Nano S device, or simply need to initialise or maintain the state of a second Ledger Nano S device, you can manually set the XMSS Index state on your Ledger Nano S device.

> **NOTE** If you are a Firefox user, ensure you have enabled **u2f** before proceeding. [Enabling U2F support in Mozilla Firefox](https://support.yubico.com/support/solutions/articles/15000017511-enabling-u2f-support-in-mozilla-firefox)
{: .info}

1. Make sure your Ledger Nano S device is powered on, unlocked and the QRL App is open.
2. Visit [https://wallet.theqrl.org/](https://wallet.theqrl.org/) in your browser.
3. Click **Open Wallet** on the left hand menu.
4. On the right hand side, select **Ledger Nano S** in the drop down menu.
5. Click the **Open Ledger Nano S** button.
6. Click **Tools** on the left hand menu.
7. Click **Set XMSS Index**.
8. Carefully read the on screen instructions and completely the form accordingly.
9. Click **Save New XMSS Index**. A confirmation window will appear, and your Ledger Nano S will ask you for confirmation.
10. Your Ledger Nano S device will show **WARNING Set XMSS Index New Value XX** where _XX_ is the XMSS Index you entered.
11. Press the right button on your Ledger Nano S to confirm, or left button to reject the update.

![QRL Ledger Transaction Complete](/assets/wallet/web/ledger-nano-s/toolsTab.png)


## QRL Ledger Nano S Video Demonstration

> Click the image below to watch the video demonstration.
{: .info}

[![The QRL - Ledger Nano Release Candidate Demo
](http://img.youtube.com/vi/NL_u9biLy1g/0.jpg)](http://www.youtube.com/watch?v=NL_u9biLy1g)
