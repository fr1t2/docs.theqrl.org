---
title: QRL Node
categories: node
description: The QRL Node documentation
tags: node
---

Running a QRL node strengthens the network, supports the decentralization and further verifies transactions on the network. This is an essential function of the decentralized architecture QRL relies on.

This allows you to run a private secure node to communicate with the QRL blockchain. 

You can use the node to connect the explorer, wallet, and ephemeral messaging features to the gRPC QRL functions. 

> There are various options available for connecting to the API and setup options for the node can be configured through a user set configuration file.
{: .info}


### Requirements

You can run QRL on most operating systems, though Ubuntu 16.04 is recommended.
{: .info}

- Support for AES-NI
- Support for avx2 (Used by keccak library for hashing functions)
- HDD with enough storage for the blockchain as it grows
- Reliable network connection 
- Python3.6
- 64 bit processor


### tl;dr

Abridged instructions for installing QRL on Ubuntu:

```bash
# Update and Upgrade packages
sudo apt update && sudo apt upgrade -y

# Install Required dependencies
{{ layout.v.qrlCommands.qrlRequirementsUbuntu }}

## Install CMAKE version 3.10.3 manually
{{ layout.v.qrlCommands.cmakeInstall }}

# Make sure setuptools is the latest
pip3 install -U setuptools

# Install QRL
{{ layout.v.qrlCommands.qrlInstall }}
```


If things worked correctly you will now find the `{{ layout.v.qrlCommands.startQRL }}
` package and the `qrl` package. Adding the `--help` flag to each will print the various function details.



## Getting Started


Installing QRL is simple, and is possible on most modern operating systems. The install relies on `python3.5` or newer and the `pip3` python package install system. 

__Update and Dependencies__

You will need to start with a fully updated system. You will also need a few additional packages depending on your setup. See the correct section for your OS and install all of the requirements.

### Ubuntu

Update your system ensuring you have the latest packages:

```bash
# Issue the following command to update software
sudo apt update && sudo apt upgrade -y
```

Now install all the required dependencies:

```bash
# Install the required packages for QRL
{{ layout.v.qrlCommands.qrlRequirementsUbuntu }}
```

QRL requires `cmake v3.10.3` to be installed. Ubuntu repositories will install an incompatible version. Please install manually as shown below. If you already have `cmake` installed, please uninstall first.

```bash
# Install the required packages for QRL
{{ layout.v.qrlCommands.cmakeInstall }}
```

### Redhat/fedora

Update:

```bash
# Update
dnf update 
```

Dependencies: 

```bash
# Install required packages
{{ layout.v.qrlCommands.qrlRequirementsRedhat }}
```

You will need to install `cmake v3.10.3` manually.

[Please follow the guide from the cmake documentation](https://cmake.org/install/)


### MacOS

To build in OSX Please install `brew` if you have not already.

```bash
# Install brew with
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" 
```

This will prompt you through a few questions while it installs.

Having Issues? Please follow the instructions found at the brew main page: [https://brew.sh/](https://brew.sh/)

```bash
# Update brew
brew update
brew install python3 swig boost hwloc
```

You will need to install `cmake v3.10.3` manually.

[Please follow the guide from the cmake documantation](https://cmake.org/install/)

### Windows 10

Windows support in the current version is limited. An alternative is to install Ubuntu using the Linux Subsystem for Windows.

#### Ubuntu on Linux Subsystem for Windows (WSL)

You can run a full node in Windows utilizing the Windows Subsystem for Linux. There are a ton of guides out there on setting this up. Here are a few links to get you going.

The Windows Subsystem for Linux (WSL) is a new Windows 10 feature that enables you to run native Linux command-line tools directly on Windows, alongside your traditional Windows desktop and modern store apps.

You can follow [these instructions](https://msdn.microsoft.com/en-us/commandline/wsl/install-win10) to install Ubuntu using Linux Subsystem, 


#### Links - Installing Ubuntu in Windows 10

* [Windows Subsystem for Linux Documentation](https://docs.microsoft.com/en-us/windows/wsl/about)
* [Google Is Your Friend (install+ubuntu+in+windows+10)](https://www.google.com/search?hl=en&as_q=install+ubuntu+in+windows+10&as_epq=)
* [WSL Blog](https://blogs.msdn.microsoft.com/wsl/)



## Install QRL 

Now that we have a freshly updated system, the installation of QRL is a breeze, QRL uses python3 to install. The install is the same for all operating systems after you have installed the requirements. Using the Python3 package installer *pip3* we will install QRL.

Before we install QRL make sure setupTools is the latest. 

```bash
pip3 install -U setupTools
```
After this completes install QRL with:

```bash
{{ layout.v.qrlCommands.qrlInstall }}
```
This will install the QRL package and any required dependencies. 



## Start QRL Node

Now that we have QRL installed we can `start_qrl` and begin syncing the node. This will begin the node in the foreground of the shell. If you would like to continue using the shell you can either pass the `--quiet` flag or run the command in a `screen` session ( you will need screen installed ).


```bash
{{ layout.v.qrlCommands.startQRL }}
```

This will print out the details of the running QRL processes. For a more verbose output you can pass the `-l` option with `DEBUG, INFO,WARNING,ERROR,CRITICAL` depending on the level of information you need.

```bash 
{{ layout.v.qrlCommands.startQRL }} -l DEBUG
```

The node will sync the entire blockchain to your computer, make sure you have enough space. after syncing the chain you will begin seeing blocks added. Congrats, your QRL node is working. 


#### Help

If you would like to see all of the options you can pass along the command line simply add `--help` to the end of the command above.

```bash
{{ layout.v.qrlCommands.startQRL }} --help
```

This will print all of the various options available. 

```bash
Usage: qrl [OPTIONS] COMMAND [ARGS]...

  QRL Command Line Interface

Options:
  -v, --verbose       verbose output whenever possible
  --host TEXT         remote host address
                      [127.0.0.1]
  --port_pub INTEGER  remote port number (public api)
                      [19009]
  --wallet_dir TEXT   local wallet dir
  --json              output in json
  --version           Show the version and exit.
  --help              Show this message and exit.

Commands:
  slave_tx_generate    Generates Slave Transaction for
                       the wallet
  state                Shows Information about a
                       Node\'s State
  token_list           Fetch the list of tokens owned
                       by an address.
  tx_inspect           Inspected a transaction blob
  tx_message           Message Transaction
  tx_multi_sig_create  Creates Multi Sig Create
                       Transaction, that...
  tx_multi_sig_spend   Transfer coins from src to dsts
  tx_push              Sends a signed transaction blob
                       to a node
  tx_token             Create Token Transaction, that
                       results into...
  tx_transfer          Transfer coins from src to dsts
  tx_transfertoken     Create Transfer Token
                       Transaction, which...
  wallet_add           Adds an address or generates a
                       new wallet...
  wallet_decrypt
  wallet_encrypt
  wallet_gen           Generates a new wallet with one
                       address
  wallet_ls            Lists available wallets
  wallet_recover       Recovers a wallet from a
                       hexseed or mnemonic...
  wallet_rm            Removes an address from the
                       wallet using the...
  wallet_secret        Provides the mnemonic/hexseed
                       of the given...

```

## Configuration 

By default when the node is started it will **NOT** mine any coins. You will have to enable using a configuration file in the `{{ layout.v.qrlConf.qrlDir }}` directory. 

The configuration file is where you will change any options you want QRL to observe. You can grab a copy of the file and details about all of the settings in our [Configuration Guide](/node/configuration/)

The defaults can be used to run a QRL node, though you may need to change some of the directives for your use.


## Mining QRL

> If you want to mine using a QRL node, see the guide for [Mining QRL Solo](/mining/full-node) or the [pool guide](/mining/pool-mining) to get started.
{: .info}