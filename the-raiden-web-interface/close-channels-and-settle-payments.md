---
description: >-
  To get your tokens back on-chain you need to either settle a payment or close
  a channel.
---

# Settle Payments and Close Channels

You have a couple of ways for depositing tokens back to your token network balance.

* [Withdraw token from an open channel](close-channels-and-settle-payments.md#withdraw-tokens) 
* [Close a channel](close-channels-and-settle-payments.md#close-a-channel)
* [Leave a token network](close-channels-and-settle-payments.md#leave-a-network)

## Withdraw tokens

![](../.gitbook/assets/web_ui_withdraw_tokens.png)

In the **"Channels"** screen:

1. Click the **"WITHDRAW"** button next to the channel from which you would like to make the withdraw.
2. Enter the amount for your withdraw.
3. Click **"Confirm"**.

The token amount will be added to your total token network balance. **Your payment channel with the partner will remain open and you can continue exchanging payments \(if your balance allows it\).**

## Close a channel

If you don't plan to use a specific channel anymore you can close it. A closed channel is no longer available for making payments.

![](../.gitbook/assets/web_ui_close_channel.png)

In the **"Channels"** screen:

1. Click the **"CLOSE"** button next to the channel you wish to close.
2. Click **"Confirm"** to finish closing the channel.

The token amount will be payed out in accordance to the transactions that have been made between the channel participants.

## Leave a token network

Leaving a network has the same outcome as [closing a channel](close-channels-and-settle-payments.md#close-a-channel) with the difference that _all_ channels belonging to the network you're leaving get closed.

![](../.gitbook/assets/web_ui_leave_network%20%281%29.png)

Click the **"LEAVE NETWORK"** button in the **"Tokens"** screen next to the token network you wish to leave.

