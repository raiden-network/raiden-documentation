---
description: >-
  Closing a channel will settle the balance between you and your peer. This
  means that both of you will receive your net balance of tokens back on-chain
  and the balance of the channel will be 0.
---

# Settle Payments and Close Channels

You can choose to either:

1. [Close a specific channel](4-settle-payments-and-close-channels.md#close-a-specific-channel)
2. [Leave a token network and close all channels](4-settle-payments-and-close-channels.md#leave-a-token-network-and-close-all-channels)

## Close a specific channel

Closing a specific channel is done with a PATCH request to the [`channels`](../resources/channels.md#close-a-channel) endpoint that includes:

1. The token address as a path parameter.
2. The address of the partner node as a path parameter.
3. The state set to _"closed"_ in the body parameter.

```bash
curl -i -X PATCH \
http://localhost:5001/api/v1/channels/0x9aBa529db3FF2D8409A1da4C9eB148879b046700/0x61C808D82A3Ac53231750daDc13c777b59310bD9 \
-H 'Content-Type: application/json' \
--data-raw '{"state": "closed"}'
```

A successful response will return a normal channel object with the state set to `"closed"`.

```bash
HTTP/1.1 200 OK
Content-Type: application/json

{
    "token_network_address": "0x3C158a20b47d9613DDb9409099Be186fC272421a",
    "channel_identifier": "99",
    "partner_address": "0x61C808D82A3Ac53231750daDc13c777b59310bD9",
    "token_address": "0x9aBa529db3FF2D8409A1da4C9eB148879b046700",
    "balance": "350",
    "total_deposit": "7331",
    "total_withdraw": "0",
    "state": "closed",
    "settle_timeout": "500",
    "reveal_timeout": "50"
}
```

{% hint style="info" %}
The settle timeout period will start as soon as a channel is closed and the channel is settled once the settle timeout period is over. The state of the channel will then be changed to`settled`.
{% endhint %}

## Leave a token network and close all channels

If you wish to leave a token network altogether you can do so by making a DELETE request to the [connections](../resources/connections.md#leave-a-token-network) endpoint with the token address as a path parameter.

```bash
curl -i -X DELETE \
http://localhost:5001/api/v1/connections/0x9aBa529db3FF2D8409A1da4C9eB148879b046700 \
-H 'Content-Type: application/json'
```

Once done, the response will return a list containing the addresses of all closed channels.

```bash
HTTP/1.1 200 OK
Content-Type: application/json

[
    "0x41BCBC2fD72a731bcc136Cf6F7442e9C19e9f313",
    "0x5A5f458F6c1a034930E45dC9a64B99d7def06D7E",
    "0x8942c06FaA74cEBFf7d55B79F9989AdfC85C6b85"
]
```

{% hint style="info" %}
Please note that leaving a token network will take some time since you need to wait for the settle timeout to expire for each channel before a settle can happen.
{% endhint %}

