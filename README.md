![RxBluetoothKit Swift](http://i.imgur.com/aeT4p5o.png)

[![CI Status](http://img.shields.io/travis/Polidea/RxBluetoothKit.svg?style=flat)](https://travis-ci.org/Polidea/RxBluetoothKit)
[![Platform](https://img.shields.io/cocoapods/p/RxBluetoothKit.svg?style=flat)](http://cocoapods.org/pods/RxBluetoothKit)
[![Carthage Compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)

RxBluetoothKit is a Bluetooth library that makes interaction with BLE devices much more pleasant. It's backed by RxSwift and CoreBluetooth and it provides nice API, for both Central and Peripheral modes. All to work with and make your code more readable, reliable and easier to maintain. 

Here is a sneak peek of what you can do with RxBluetoothKit:
```swift
manager.scanForPeripherals(withServices: [serviceId])
    .take(1)
    .flatMap { $0.peripheral.establishConnection() }
    .flatMap { $0.discoverServices([serviceId]) }
    .flatMap { Observable.from($0) }
    .flatMap { $0.discoverCharacteristics([characteristicId]) }
    .flatMap { Observable.from($0) }
    .flatMap { $0.readValue() }
    .subscribe(onNext: { print("Value: \($0.value)") })
```
With just 9 lines it started scanning, connecting to the peripheral, discovering service and characteristics and read charecteristic's value!

## Central mode features

* [Observing manager states](https://github.com/Polidea/RxBluetoothKit/wiki/2.-Manager-State)
* [Scanning for peripherals](https://github.com/Polidea/RxBluetoothKit/wiki/3.-Scanning-peripherals)
* [Connecting to peripheral](https://github.com/Polidea/RxBluetoothKit/wiki/4.-Connecting-to-peripheral)
* [Discovering peripheral's services and characteristics](https://github.com/Polidea/RxBluetoothKit/wiki/5.-Discovering-services-&-characteristics)
* [Reading & Writing to characteristic's value](https://github.com/Polidea/RxBluetoothKit/wiki/6.-Reading-&-Writing-to-characteristic-value)
* [Monitoring characteristic value change](https://github.com/Polidea/RxBluetoothKit/wiki/7.-Monitoring-characteristic-value-change)
* Opening L2CAP channels
* [Convenience helper methods](https://github.com/Polidea/RxBluetoothKit/wiki/8.-Convenience-helper-methods)
* [And a lot more!](https://github.com/Polidea/RxBluetoothKit/wiki/9.-Other-functionalities)


## Peripheral mode features

* [Observing manager states](https://github.com/Polidea/RxBluetoothKit/wiki/2.-Manager-State)
* Advertising
* Observing read & writes
* Observing subscribe
* Publishing L2CAP channels
* And a lot more!

# Recent Changes

**5.2.1**

* Updated RxSwift to version 5.0 (#335)

[All previous changes](CHANGELOG.md)

Want to migrate from 4.x to 5.x? Check guidelines [here](https://github.com/Polidea/RxBluetoothKit/wiki/Migrating-to-5.x).

# Installation

## CocoaPods
[CocoaPods](http://cocoapods.org) is a dependency manager for CocoaProjects.
To integrate RxBluetoothKit into your Xcode project using CocoaPods specify it in your `Podfile`:
```ruby
pod 'RxBluetoothKit'
```
Then, run the following command:
`$ pod install`

## Carthage

[Carthage](https://github.com/Carthage/Carthage) is a decentralized dependency manager that builds your dependencies and provides you with binary frameworks.
To integrate RxBluetoothKit into your Xcode project using Carthage  specify it in your `Cartfile`:
```swift
github "Polidea/RxBluetoothKit"
```
Then, run `carthage update` to build framework and drag `RxBluetoothKit.framework` into your Xcode project.

## Swift Package Manager

Versions >= 4.0 of the library integrate with the Swift Package Manager. In order to do that please specify our project as one of your dependencies in `Package.swift` file.

# Getting Started

Check [our Wiki](https://github.com/Polidea/RxBluetoothKit/wiki) with guidelines to (almost) all library functionalites.

# Documentation & Support

* [Api reference](https://polidea.github.io/RxBluetoothKit/)
* [Sample App](https://github.com/Polidea/RxBluetoothKit/tree/master/ExampleApp)
* [Gitter channel](https://gitter.im/RxBLELibraries/RxBluetoothKit?utm_source=share-link&utm_medium=link&utm_campaign=share-link) if you want to talk about it, ask questions or give feedback.
* [StackOverflow](http://stackoverflow.com/questions/tagged/rxiosble?sort=active) if you have a problem
* Or open [an issue](https://github.com/Polidea/RxBluetoothKit/issues/new) on GitHub

Remember to follow [Polidea's Blog](https://www.polidea.com/blog/RxBluetoothKit_The_most_simple_way_to_code_BLE_devices/) blog to get all the news and updates!

Learn more about Polidea's BLE services [here](https://www.polidea.com/services/ble).

# Requirements

- iOS 8.0+
- OSX 10.10+
- watchOS 4.0+
- tvOS 11.0+
- Xcode 7.3+

## Swift versions
* 3.0 version supports Swift 3.0 and 3.1
* 5.0 version supports Swift 3.2 and 4.0
* 5.1.2 version supports Swift 4.1
* 5.2 version supports Swift 5.0 and 4.2
