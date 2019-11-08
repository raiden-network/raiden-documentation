---
description: >-
  At some point you might want to open channels manually. Perhaps you'd like to
  have a direct channel to a friend's node or maybe no channels have been opened
  yet for a token that was just registered.
---

# Open a Channel

This section will cover the endpoints you would use to:

1. [Open a channel](2-open-a-channel.md#open-a-channel)
2. [Query the state of a channel](2-open-a-channel.md#query-the-state-of-a-channel)

## Open a channel

To open a channel a PUT request is made to the [`channels`](../resources/channels.md#create-a-channel) endpoint that includes a JSON object containing:

1. The address of the node you'd like to open the channel with.
2. The amount of tokens you want to deposit in the channel. Remember that it is always possible to [deposit more tokens](3-deposit.md) later.
3. The settle timout period which corespond to the number of blocks that have to be mined before a closed channel can be settled.

```bash
curl -i -X PUT \
http://localhost:5001/api/v1/channels \
-H 'Content-Type: application/json' \
--data-raw '{"partner_address": "0x61C808D82A3Ac53231750daDc13c777b59310bD9", "token_address": "0x9aBa529db3FF2D8409A1da4C9eB148879b046700", "total_deposit": 1337, "settle_timeout": 500}'
```

This will create a new channel and a successful request will return you the following response object:

```bash
HTTP/1.1 201 CREATED
Content-Type: application/json

{
    "token_network_address": "0x3C158a20b47d9613DDb9409099Be186fC272421a",
    "channel_identifier": 99,
    "partner_address": "0x61C808D82A3Ac53231750daDc13c777b59310bD9",
    "token_address": "0x9aBa529db3FF2D8409A1da4C9eB148879b046700",
    "balance": 1337,
    "total_deposit": 1337,
    "total_withdraw": 0,
    "state": "opened",
    "settle_timeout": 500,
    "reveal_timeout": 50
}
```

As you can tell by the response object a channel identifier has been generated. This means that there now is a channel with that identifier inside the token network.

You're now ready to start making payments.

{% page-ref page="3-make-a-payment.md" %}

{% hint style="info" %}
Opening a channel works the same way whether the partner node holds tokens or not.
{% endhint %}

## Query the state of a channel

If you want to view the current state of a channel it is as easy as making a query to the [`channels`](../resources/channels.md#info-about-one-of-your-channels) endpoint while providing:

1. The token address as a path parameter.
2. The address of the partner node as a path parameter.

```bash
curl -i \
http://localhost:5001/api/v1/channels/0x9aBa529db3FF2D8409A1da4C9eB148879b046700/0x61C808D82A3Ac53231750daDc13c777b59310bD9
```

This will give you the same response object as when [opening a channel](2-open-a-channel.md#open-a-channel).

