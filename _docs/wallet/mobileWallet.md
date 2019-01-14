---
title: Mobile Wallet
layout: docs.video
categories: wallet
tags: wallet
---


The QRL wallet has been extended to provide the same quantum resistance that is provided by the Web and Desktop wallets into mobile platforms, further extending the usability of the first of its kind quantum resistant blockchain.

This mobile application is based on the react-native framework to provide an Android and iOS implementation of the QRL wallet.
All of the functions available in the web wallet have been extended into the mobile wallet. 

<img src="/assets/wallet/mobile/iosQrlWalletScreenshot.png" width="150" />


> The mobile-wallet apps are still under heavy development. Please be aware that frequent changes will occur to this repository.

## Install

Grab the applicatiaon from the app store or play store.

### iOS

For iOS search for the QRL wallet or follow this link.

[Future Link to App Store](#)

### Android

For Android search QRL in the play store or follow this link.

[Future Link to Play Store](#)

## Usage

Using the wallet is simple. Follow the instructions to create a new wallet and recieve funds. You can simply scan the QR code from another users wallet to send funds. 


---

## Building from Sources

#### Requirements

##### Common to iOS and Android

- React-Native (https://facebook.github.io/react-native/)
- CMake (https://cmake.org/)

##### iOS specific

- XCode
- Cocoapods (https://cocoapods.org/)

##### Android specific

- Android Studio (https://developer.android.com/studio/install)
- Gradle (https://gradle.org/): can be handled within Android Studio

#### How to generate the iOS libraries

To generate the iOS libraries you need to clone the [theQRL/qrllib](https://github.com/theQRL/qrllib) and build the \*.a iOS libraries (for the simulator and real device) using Xcode.

```bash
git clone https://github.com/theQRL/qrllib
git submodule update --init --recursive
cd qrllib
mkdir build
cd build
cmake -G Xcode ..
```
These commands will generate a new Xcode project called qrllib.xcodeproj.
Open the Xcode project and build the 4 different libraries (dilithium, kyber, qrllib and shasha) for the iOS simulator and "iOS generic device". You will see all the generated libraries under build/Debug-iphoneos and build/Debug-iphonesimulator directories.

#### How to generate the Android libraries

To generate the Android libraries you need to load the /android project folder in Android Studio and open the build-gradle file.
Open the "Gradle menu" and double click on "android:app [externalNativeBuildDebug]" under the "Run Configurations" category to start building the libraries.
The generated \*.so libraries are located under android/app/build/intermediates/cmake/debug/obj/.

#### How to update proto files

In case of any change on the proto file, one needs to regenerate the gRPC pods

```bash
rm -rf Pods
rm Podfile.lock
pod install
```

#### Load the generated libraries to the mobile-wallet app

- Open the mobile-wallet Xcode project (ios/theQRL.xcworkspace)
- Click on the project name (theQRL) and select theQRL under the TARGETS list
- Add all the generated .a libraries to the **Linked Frameworks and Libraries section**

#### RN <-> native code communication

For more information about the communication between React-Native and native code (Objective-C and c++) check the original [Communication between native and React Native](https://facebook.github.io/react-native/docs/communication-ios.html) documentation.