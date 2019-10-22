---
description: >-
  Payment channels allow for Raiden transfers to be made without the need to
  involve the actual blockchain.
---

# Make a Payment

If you have one or more channels open you can start making payments. When you joined a token network three channels were automatically opened with three nodes. 

Let's walk through how to [pay from the tokens screen](payment.md#pay-from-the-tokens-screen).

{% hint style="info" %}
**How do payment channels work?**

Payment channels enable tokens to be exchanged bi-directionally between counter-parties off-chain.

Not involving the blockchain for every transfer helps avoiding the blockchain consensus bottleneck and makes transfers faster and cheaper.

A payment channel in Raiden is always backed by an on-chain deposit of tokens. Depositing tokens or opening payment channels an on-chain transactions, which cause transaction fees to be paid in ETH \(gas\).

Raiden lets users pay anyone in the network by using a path of connected payment channels to mediate the payment. **This means that you don't need to open channels with every node you want to send a payment to!**
{% endhint %}

## Pay from the tokens screen

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LfdOdNB3P6EjscN0LQW%2F-Lmohs2CCzY8OU3NPFVM%2F-LmohxxLR9o6PvNIJAv3%2Fweb_ui_make_payment_1.png?alt=media&token=902f6fee-dbe8-439f-86c9-cef0b8d475c1)

Click the **"PAY"** button that has been made available for the token network you joined.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LfdOdNB3P6EjscN0LQW%2F-LmolS2Q18ey4xDWCRMX%2F-LmolVRkkEkdgTimB5tK%2Fweb_ui_make_payment_2.png?alt=media&token=fe11e87a-e171-4e10-b0de-a291b0f99721)

In the popup dialogue:

1. Enter the address of the receiver of your payment.
2. Select the token associated with the token network you're making the payment from. Note: The token is already pre-selected when you pay via the tokens screen.
3. Enter the amount you want to pay.
4. You can choose to fill in any number in the **"Set payment identifier"** dropdown for identifying your payment. If nothing is provided your payment identifier will default to a timestamp.
5. Click **"Send"** to complete your payment.

{% hint style="info" %}
**Minting tokens**

The Raiden WebUI lets you mint tokens if you need to fund your account with additional testnet tokens.

To do so, click the **"MINT TOKEN"** button in the **"Tokens"** screen next to your token of choice.

This will trigger an on-chain transaction and use some of your testnet ETH in exchange for more tokens.
{% endhint %}

