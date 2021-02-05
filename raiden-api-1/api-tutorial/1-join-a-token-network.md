---
description: >-
  To be able to make token payments in Raiden you first need to join the network
  of the token you're interested in making payments with.
---

# Create a Token Network

## Check if the token is registered

Before you can join a token network you need to determine whether the token has been registered and a network for the token has been created.

We can verify this by making a query to the [`tokens`](../resources/tokens.md#addresses-for-all-registered-tokens) endpoint.

```bash
curl -i http://localhost:5001/api/v1/tokens
```

If the address exists in the list returned by the response you can go ahead and [open a channel](2-open-a-channel.md#open-a-channel) in that token network.

If the address is not in the list you'll have to [register the token](1-join-a-token-network.md#register-a-new-token-and-join-its-network) before you can open a channel.

## Register a new token

Registering a new token is as simple as calling the [`tokens`](../resources/tokens.md#register-a-token) endpoint with a PUT request while providing the address of the token you want to register as a path parameter.

```bash
curl -i -X PUT http://localhost:5001/api/v1/tokens/0x9aBa529db3FF2D8409A1da4C9eB148879b046700 \
-H 'Content-Type: application/json'
```

If the call is successful the response will return a new address of the now newly created token network.

```bash
HTTP:/1.1 201 CREATED
Content-Type: application/json

{
    "token_network_address": "0xC4F8393fb7971E8B299bC1b302F85BfFB3a1275a"
}
```

Because this token was just registered by you, no one else will be connected to its network and you'll have to open a channel with another Raiden node.

{% page-ref page="2-open-a-channel.md" %}

{% hint style="info" %}
Payment channels between parties are opened in token networks.
{% endhint %}

{% hint style="warning" %}
Registering a new token is currently only relevant on the testnets. The tokens allowed on the mainnet for the Alderaan release are DAI and W-ETH. At some point in future, you will be able to register new token networks for the Ethereum mainnet, too.
{% endhint %}

