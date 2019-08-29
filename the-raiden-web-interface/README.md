---
description: >-
  The Raiden WebUI was created to help you get an idea of what Raiden is capable
  of and inspire you to create your own applications that utilizes the Raiden
  REST API endpoints.
---

# WebUI

## Run the Raiden Web Application

The easiest way to start using the WebUI is to download and install Raiden by going to

{% page-ref page="../quick-start/" %}

Once you have a Raiden node up and running the WebUI will be available from [http://localhost:5001](http://localhost:5001).

## Join a Token Network

You need to join a token network for the token you're interested in doing payments with. 

{% hint style="info" %}
**What is a token?** 

A token is defined within a ERC20 compliant smart contract. The token contract is as a registry where different amounts of the total supply are mapped to different owners.

**What is a token network?**

For each ERC-20 compliant token a Raiden Token Network can be registered. All Raiden Nodes registered within this network form a token network.
{% endhint %}

## Join an Existing Token Network

![](../.gitbook/assets/web_ui_join_network_1%20%281%29.png)

Click the **"JOIN NETWORK"** button next to the token which network you want to join.

{% hint style="info" %}
**What is the balance?**

The Token Network Balance shows the on-chain balance of the respective token which the Raiden account holds.
{% endhint %}

![](../.gitbook/assets/web_ui_join_network_2.png)

Enter the the amount of tokens you want to allocate and click **"Join"**. The amount you choose is what will be available for making payments and you can always [add more funds later](./#add-more-tokens).

With joining the token network channels have been automatically opened channels to connect you to your peers.

{% hint style="info" %}
**What is a channel?**

A channel or payment channel allows Raiden transfers to be made back and forth between parties without involving the actual blockchain.
{% endhint %}

{% hint style="info" %}
**How does opening a channel works?**

This works by first creating an initial on-chain deposit with the amount specified when you for instance joined a token network.

The net sum can be used in the Raiden off-chain transactions and the actual blockchain only needs to be involved in the initial setup or when choosing to deposit more tokens or settle a netted amount.
{% endhint %}

{% hint style="info" %}
**How are channels automatically opened?**

When you joined a token network three channels were automatically opened with three random nodes and 60% of the tokens you provided got equally distributed with 20% in each channel. 

The remaining 40% are reserved for when someone wants to open a channel with you.
{% endhint %}

{% hint style="info" %}
**Can I only pay Raiden Nodes where I have got a direct channel to?**

In Raiden channels make up routes between peers. A transfer can be made between two peers that do not have a direct channel with each other as long as there are routes connecting them via other peers.
{% endhint %}

You're now ready to [make a payment](./#make-a-payment)!

