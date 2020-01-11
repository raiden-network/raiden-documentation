---
description: >-
  To get you familiarized with the Raiden WebUI we have put together a short
  introduction to the most important screens of the application.
---

# Navigate the WebUI

The first screen you will see when the WebUI launches is the **"Home"** screen which has a short introduction to Raiden.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LfdOdNB3P6EjscN0LQW%2F-LmtmGMrLm7yWMJeP6xg%2F-LmtmKMI05O7RjNA44HH%2Fweb_ui_home_screen.png?alt=media&token=1243faba-1681-4fb8-bb13-27af47ffa805)

On the top bar and left hand side you'll find:

1. The address of your Raiden node together with your current ETH balance. Some of this ETH will be used anytime an on-chain activity happens.
2. The navigation menu for interacting with Raiden.

The menu options we will be focusing on are:

* [Tokens](screens.md#tokens-1)
* [Channels](screens.md#channels)
* [Address Book](screens.md#address-book)

## Tokens

In order to open a channel and start making payments you need to be connected to a token network. Each ERC20 token can theoretically have its own token network.

![Tokens screen](../../.gitbook/assets/web_ui_tokens_screen.png)

1. List of all tokens that have been registered in Raiden.
2. Details about each token including:
   * The token **symbol** \(WIZ\)
   * The token **name** \(WizardToken\)
   * Your current token **balance**
   * Buttons with which you can [**join a network**](join-a-token-network.md) or [**mint tokens**](payment.md)\*\*\*\*
3. **+** button for [**registering new token networks**](join-a-token-network.md#register-a-new-token-and-join-its-network) and options for **filtering** and **sorting** your tokens list

## Channels

To make payments you need to have a channel with at least one other Raiden node.

{% hint style="info" %}
If you have no channels open this screen will display a _"no channels found"_ message. The simplest way to get started is to open channels by [joining a token network](join-a-token-network.md).
{% endhint %}

![Channels screen](../../.gitbook/assets/web_ui_channels_screen.png)

1. List of all your open channels.
2. Details about each open channel which includes:
   * The address of the **partner** node you're connected to via the channel
   * The token **symbol** \(WIZ\) and the token **address** which gets displayed when hovering over the symbol
   * Your current **balance** of tokens in the channel
   * The **status** of your channel and whether it is **open**, **closed**, or **settled**
   * Buttons where you can [**pay**](payment.md) ****\(both the "PAY" and the "SEND TOKENS" button works the same as when paying from the "Tokens" screen after joining a token network\), [**deposit**](add-more-tokens.md), [**withdraw**](close-channels-and-settle-payments.md), or [**close a channel**](close-channels-and-settle-payments.md)\*\*\*\*
3. A **+** button for opening a channel with a counterpart of your choosing and options for **filtering** and **sorting** your channels list

## Address book

The address book gives you the possibility to save and label addresses.

![Address book screen](../../.gitbook/assets/web_ui_address_book_screen.png)

1. List of all your saved peers and their addresses.
2. Two options for saving a new address:
   * Type the address and label manually
   * Drag and drop a JSON file containing all your addresses

