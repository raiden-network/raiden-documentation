---
description: >-
  Opening a channel and depositing tokens in it allows you to transfer these
  tokens to your channel partner -- and indirectly to other nodes connected to
  you partner.
---

# Open a Channel

To open a channel, a PUT request is made to the [`channels`](../raiden-api-1/resources/channels.md#create-a-channel) endpoint that includes a JSON object containing:

1. The address of the node you'd like to open the channel with. If you don't know to which partner you should connect, have a look at "Find suitable partner nodes" \(ADD LINK\).
2. The token address. We use W-ETH token in this example.
3. The amount of tokens you want to deposit in the channel \(Remember that it is always possible to [deposit more tokens](../raiden-api-1/api-tutorial/3-deposit.md) later\). 1 W-ETH is equivialent to 10^18 WEI.
4. The settle timeout period which corresponds to the number of blocks that have to be mined before a closed channel can be settled.

```bash
curl -i -X PUT \
http://localhost:5001/api/v1/channels \
-H 'Content-Type: application/json' \
--data-raw '{"partner_address": "0x61C808D82A3Ac53231750daDc13c777b59310bD9", "token_address": "0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2", "total_deposit": "1337", "settle_timeout": "500"}'
```

{% hint style="info" %}
Raiden utilizes a RESTful API where all URL paths starts with `/api/` followed by a version number. The current API version is `1` and therefore all requests begins with `/api/v1/` .
{% endhint %}

This will create a new channel and a successful request will return you the following response object:

```bash
HTTP/1.1 201 CREATED
Content-Type: application/json

{
    "token_network_address": "0x3C158a20b47d9613DDb9409099Be186fC272421a",
    "channel_identifier": "99",
    "partner_address": "0x61C808D82A3Ac53231750daDc13c777b59310bD9",
    "token_address": "0x9aBa529db3FF2D8409A1da4C9eB148879b046700",
    "balance": "1337",
    "total_deposit": "1337",
    "total_withdraw": "0",
    "state": "opened",
    "settle_timeout": "500",
    "reveal_timeout": "50"
}
```

As you can tell by the response object a channel identifier has been generated. This means that there now is a channel with that identifier inside the token network.

We're now ready to start sending W-ETH tokens!

{% page-ref page="make-a-payment.md" %}

