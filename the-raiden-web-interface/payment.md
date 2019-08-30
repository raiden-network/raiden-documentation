---
description: >-
  When you joined a token network three channels were automatically opened with
  three random nodes. These channels allows for Raiden transfers to be made
  without involving the actual blockchain.
---

# Make a Payment

When you have one or more channels open you can start making payments. Let's walk through how to pay from the tokens screen.

{% hint style="info" %}
**What is a Channel?**

Text
{% endhint %}

## Pay from the Tokens Screen

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LfdOdNB3P6EjscN0LQW%2F-Lmohs2CCzY8OU3NPFVM%2F-LmohxxLR9o6PvNIJAv3%2Fweb_ui_make_payment_1.png?alt=media&token=902f6fee-dbe8-439f-86c9-cef0b8d475c1)

Click the **"PAY"** button that has been made available for the token network you joined.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LfdOdNB3P6EjscN0LQW%2F-LmolS2Q18ey4xDWCRMX%2F-LmolVRkkEkdgTimB5tK%2Fweb_ui_make_payment_2.png?alt=media&token=fe11e87a-e171-4e10-b0de-a291b0f99721)

In the popup dialogue:

1. Enter the address of the receiver of your payment.
2. Select the token associate with the token network you're making the payment from.
3. Enter the amount you want to pay.
4. You can choose to fill in any number in the **"Set payment identifier"** dropdown for identifying your payment. If nothing is provided your payment identifier will default to a timestamp.
5. Click **"Send"** to complete your payment.

{% hint style="info" %}
**Make Payments to any Raiden Node**

You don't need to have a direct channel with the peer you wish to send a payment. A transfer can be made between two peers that do not have a direct channel with each other as long as there are routes connecting them via other peers.
{% endhint %}

