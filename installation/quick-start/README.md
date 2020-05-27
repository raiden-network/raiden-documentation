---
description: >-
  This quick start section will help you install Raiden and run a Raiden node on
  the Ethereum mainnet using the Raiden Wizard.
---

# Quick Start

## Overview

In this tutorial we will walk through the steps to:

* [Get MetaMask](get-metamask.md)
* [Get an Infura ID](infura-quick-start.md)
* [Download and run the Raiden Wizard](download-and-run-the-raiden-wizard.md#download-the-raiden-wizard)

## Prerequisites

In order to use the Raiden Wizard and Raiden you'll need:

* A computer running **Linux** or **macOS**
* MetaMask and an account with at least `0.125` ETH
* An Infura ID

## Downloadthe Raiden Wizard

You can download the Raiden Wizard for either macOS or Linux:

* Go to the [**release page**](https://github.com/raiden-network/raiden-installer/releases/).
* Find the latest release that is **not** marked `Pre-Release`.
* Click on `Assets` and donwload an archive for your operating system.

You will need to unpack the downloaded archive. In it you will find an executable program named `raiden_wizard`.

## **Run the Raiden Wizard**

This will setup and launch Raiden.

{% hint style="warning" %}
You need an internet connection to run the Raiden Wizard. The Wizard will launch in your default browser.

The setup process can take up to five minutes, make sure not to close the browser.
{% endhint %}

1. Extract and open the `raiden_wizard` program.
2. Your web browser should open a new window \(if not, type [http://localhost:1994](http://localhost:1994) in your browser, to manually open it\).
3. Follow the configuration steps of the Wizard.

In the process you will

* Create a new Ethereum account for use with Raiden \(the "Raiden Account"\).
* Fund the Raiden Account with `ETH`.
* Acquire `RDN` tokens for use with the [User Deposit Contract](../../raiden-api-1/glossary.md#user-deposit).
* Acquire `DAI` tokens for making payments in the Raiden Network.

When you have finished the steps of the Wizard, you can `LAUNCH` Raiden and start interacting with:

{% page-ref page="../../using-raiden/the-raiden-web-interface/" %}

## Need help?

If you run into problems or discover bugs, you can:

* Ask for help in the [Raiden gitter chat](https://gitter.im/raiden-network/raiden)
* Create a [GitHub issue](https://github.com/raiden-network/raiden/issues/new/choose) for either a bug report or feature request

