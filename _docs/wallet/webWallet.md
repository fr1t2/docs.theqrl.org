---
title: Web Wallet
categories: wallet
description:
tags: wallet
---

[![Build Status](https://circleci.com/gh/theQRL/qrl-wallet.svg?style=shield&circle-token=:circle-token)](https://circleci.com/gh/theQRL/qrl-wallet)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/a91585507ea24454a43190dfb48d8c09)](https://www.codacy.com/app/qrl/qrl-wallet?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=theQRL/qrl-wallet&amp;utm_campaign=Badge_Grade)
[![Maintainability](https://api.codeclimate.com/v1/badges/30e006c07f50365faa9a/maintainability)](https://codeclimate.com/github/theQRL/qrl-wallet/maintainability)
[![Known Vulnerabilities](https://snyk.io/test/github/theqrl/qrl-wallet/badge.svg)](https://snyk.io/test/github/theqrl/qrl-wallet)
[![MIT licensed](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/theQRL/qrl-wallet/master/LICENSE)

![QRL Web Wallet](/assets/wallet/web/qrlWallet.png)

The QRL wallet application developed by The QRL team, and hosted on [wallet.theqrl.org](https://wallet.theqrl.org) provides both web and desktop interfaces using [Meteor](https://www.meteor.com/), [Semantic UI](https://semantic-ui.com/), [NodeJS](https://nodejs.org/en/) and [Electron](https://electronjs.org/).

All secure XMSS operations are run in a web assembly compiled version of [qrllib](https://github.com/theQRL/qrllib) locally in your browser or desktop application. Keys stay in the memory space of the XMSS object, which is destroyed the moment you close the wallet, browser window or desktop application.


## Creating A Wallet

Browse over to the only official QRL wallet hosted on [https://wallet.theqrl.org](https://wallet.theqrl.org).

> For more info see the [Wallet Basics](/wallet/basics) document.

## Installation

To run a local version of the wallet in a development environment follow the directions below. If you are looking to just run the application grab a copy from the links above.

> If you would like to contribute to the QRL wallet, please submit changes to the [GitHub repo](https://github.com/theQRL/qrl-wallet)

### Development Dependencies

The following dependencies are required for a functional local development environment.

[NodeJS](https://nodejs.org/en/) v8.9.3

[Meteor](https://www.meteor.com/install)

[electrify-qrl](https://www.npmjs.com/package/electrify-qrl)

	npm install -g electrify-qrl

[chimp](https://github.com/xolvio/chimp)

	npm install -g chimp

Windows Only - [Build Tools for Visual Studio 2017](https://www.visualstudio.com/downloads/#build-tools-for-visual-studio-2017)


Windows Only - [node-gyp](https://github.com/nodejs/node-gyp)

	npm install -g node-gyp


### Install qrl-wallet

	git clone https://github.com/theQRL/qrl-wallet.git
	cd qrl-wallet
	meteor npm install --unsafe-perm
	cd .electrify
	npm install
	cd ..

### Run Meteor

	meteor

### Run Tests

Note: meteor must already be running for this to work!

	chimp --ddp=http://localhost:3000 --watch --path=tests

### Run Electron Client

	electrify

### Package Electron Client

	mkdir .electrify/.dist
	electrify package -o .electrify/.dist/
