---
title: Desktop Wallet
categories: wallet
tags: wallet
---

[![Build Status](https://circleci.com/gh/theQRL/qrl-wallet.svg?style=shield&circle-token=:circle-token)](https://circleci.com/gh/theQRL/qrl-wallet)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/a91585507ea24454a43190dfb48d8c09)](https://www.codacy.com/app/qrl/qrl-wallet?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=theQRL/qrl-wallet&amp;utm_campaign=Badge_Grade)
[![Maintainability](https://api.codeclimate.com/v1/badges/30e006c07f50365faa9a/maintainability)](https://codeclimate.com/github/theQRL/qrl-wallet/maintainability)
[![Known Vulnerabilities](https://snyk.io/test/github/theqrl/qrl-wallet/badge.svg)](https://snyk.io/test/github/theqrl/qrl-wallet)
[![MIT licensed](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/theQRL/qrl-wallet/master/LICENSE)


The QRL wallet can be ran from any modern PC and is the exact same application that is ran in production and hosted at [wallet.theqrl.org](https://wallet.theqrl.org)

It provides both web and desktop interfaces using Meteor, Semantic UI, NodeJS and Electron.

All secure XMSS operations are run in a web assembly compiled version of qrllib locally in your browser or desktop application. Keys stay in the memory space of the XMSS object, which is destroyed the moment you close the wallet, browser window or desktop application.

> The source code can be found at [https://github.com/theQRL/qrl-wallet](https://github.com/theQRL/qrl-wallet) if you would like to contribute.


## Installation

Grab the latest QRL wallet files from [TheQRL GitHub](https://github.com/theQRL/qrl-wallet/releases/latest)

Make sure to grab the files for your Operating system. These files will install the wallet locally on your PC.

## Useage

See the great writeup for [Basic Wallet Use](/wallet/basics) for instructions on creating a wallet and sending funds.