---
description: >-
  Payment channels allow for Raiden transfers to be made without the need to
  involve the actual blockchain.
---

# Make a Payment

If you have one or more channels open you can start making payments. If you used [_Quick Connect_](join-a-token-network.md#quick-connect) three channels were automatically opened with three nodes.

Let's walk through how to make a transfer.

## Transfer

After selecting a token network with open channels. Click on the **"Transfer"** button, this will bring open the _transfer dialog_.

1. If you accessed the transfer dialog from the _all networks view_, you can select the token network you want to make payments in also here.
2. Enter the receiving address.
3. Enter the amount.
4. Click **"Send"** to complete the transfer.

{% hint style="info" %}
**Minting tokens**

When running Raiden on a testnet the WebUI lets you mint tokens to fund your account with additional tokens.

To mint tokens, click the three dots on the top right of the token network view and choose **"Mint"**.

Minting tokens is an on-chain transaction that will consume some of your ETH.
{% endhint %}

{% hint style="info" %}
**How does payment channels work?**

Payment channels enable parties to exchange tokens off-chain without involving the blockchain for every transaction.

This helps to avoid the blockchain consensus bottleneck and makes transfers both faster and cheaper.

Raiden lets users pay anyone in the network by using a path of connected payment channels to mediate payments. This means that _a user don't need to open channels with every node they want to send payments to_.

A payment channel in Raiden is always backed by an on-chain deposit of tokens. Depositing tokens or opening payment channels are on-chain transactions which require transaction fees \(gas\) that are paid in ETH.
{% endhint %}

