---
description: >-
  Having an (empty) open channel won't in itself let you make payments. You also
  need to make sure that you have tokens deposited at your end of the channel.
---

# Deposit Tokens

If you opened a channel by yourself you most likely already  deposited tokens when sending the request. However, in case someone opened a channel with you, you will not yet have any tokens at your end of the channel.

You need to make a deposit whenever you want to:

* Add tokens to an empty channel
* Top up the amount of tokens in a channel

## Deposit into a channel

The [`channel`](../resources/channels.md#increase-deposit) endpoint together with a PATCH request is used for depositing tokens into a channel. When making the call you need to include:

1. The token address as a path parameter.
2. The address of the partner node as a path parameter.
3. The amount of tokens you want to deposit in the channel as a body parameter.

```bash
curl -i -X PATCH \
http://localhost:5001/api/v1/channels/0x9aBa529db3FF2D8409A1da4C9eB148879b046700/0x61C808D82A3Ac53231750daDc13c777b59310bD9 \
-H 'Content-Type: application/json' \
--data-raw '{"total_deposit": 7331}'
```

This will give you the same response object as when [opening a channel](2-open-a-channel.md#open-a-channel) or [querying the state of a channel](2-open-a-channel.md#query-the-state-of-a-channel).

Now, once there are tokens at your end of the channel, let's start making payments.

{% page-ref page="3-make-a-payment.md" %}



