---
description: >-
  To make payments in Raiden you first need to join the network by opening
  channels for the token you want to make payments with.
---

# Join a Token Network

You can join a token network by either:

* [Quick Connect](join-a-token-network.md#quick-connect)
* [Registering a new token](join-a-token-network.md#registering-a-new-token)

{% hint style="info" %}
**What is a token?**

Each token complies to its own ERC20 smart contract which has a total supply of tokens.

These token contracts are like a registry where different amounts of the total supply is mapped to different owners.
{% endhint %}

{% hint style="info" %}
**What is a token network?**

Anyone running a Raiden node and owns a token can join a network with other nodes who own the very same token.

All nodes registered within such network form a token network.
{% endhint %}

## Quick Connect

_Quick Connect_ lets you automatically open channels with 3 random online nodes.

If you click the **"Transfer"** button without having any open channels for the selected token you will get prompted to use _Quick Connect_.

When using _Quick Connect_:

* Enter the amount of tokens you want to allocate and click **"Connect"**.
* The allocated tokens will be split with:
  * 20% in each of the three channels
  * 40% for whenever you are joining a channel that has been opened by another node.

The amount you choose when connecting is what will be available for making payments. You can always add more funds by depositing to a channel.

{% hint style="warning" %}
_Quick Connect_ is an on-chain activity that will consume some of your ETH.
{% endhint %}

You are now ready to make the first payment!

{% page-ref page="payment.md" %}

## Registering a new token

{% hint style="warning" %}
Registering a new token is only relevant on the testnets. The tokens allowed on mainnet for the Alderaan release are DAI and W-ETH. 
{% endhint %}

If you want to join the network for a token and that token is not displayed in the list of tokens it might mean that it has not been registered.

To register a token yourself:

1. Click **"Select network"** in the tokens view.
2. Click **"Add new network"**.
3. Enter the address of the token you'd like to register and click **"Register"**.

You can follow the steps for [_Quick Connect_](join-a-token-network.md#quick-connect) to join the network of your newly registered token.

