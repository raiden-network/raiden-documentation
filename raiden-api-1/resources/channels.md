---
description: >-
  The channels endpoints allow you to open channels with other Raiden nodes as
  well as closing channels, querying them for information and making deposits or
  withdrawals.
---

# Channels

## Channels Resource Overview

| HTTP Method | Resource | Description |
| :--- | :--- | :--- |
| GET | [`/api/<version>/channels`](channels.md#all-unsettled-channels-for-a-specific-token) | All unsettled channels |
| GET | [`/api/<version>/channels/<token_address>`](channels.md#all-unsettled-channels-for-a-specific-token) | All unsettled channels for a specific token |
| GET | [`/api/<version>/channels/<token_address>/<partner_address>`](channels.md#info-about-one-of-your-channels) | Info about one of your channels |
| PUT | [`/api/<version>/channels`](channels.md#create-a-channel) | Create a channel |
| PATCH | [`/api/<version>/channels/<token_address>/<partner_address>`](channels.md#close-a-channel) | Close a channel, increase deposit, withdraw tokens or update reveal timeout |

{% hint style="warning" %}
**Alderaan Deposit Limits**

The maximum deposits per token and node for Alderaan are:

* **DAI**

  The deposit limit is 1000 worth of DAI per channel participant making the maximum amount of DAI 2000 per channel.

* **WETH**

  Details on the deposit limit for WETH will be added soon.
{% endhint %}

## Channels Resource Details

{% api-method method="get" host="http://localhost:5001" path="/api/v1/channels" %}
{% api-method-summary %}
All Unsettled Channels
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="version" type="string" required=true %}
Version of the API
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successful query
{% endapi-method-response-example-description %}

```bash
[
    {
        "token_network_address": "0xE5637F0103794C7e05469A9964E4563089a5E6f2",
        "channel_identifier": 20,
        "partner_address": "0x61C808D82A3Ac53231750daDc13c777b59310bD9",
        "token_address": "0xEA674fdDe714fd979de3EdF0F56AA9716B898ec8",
        "balance": 25000000,
        "total_deposit": 35000000,
        "total_withdraw": 5000000,
        "state": "opened",
        "settle_timeout": 100,
        "reveal_timeout": 30
    }
]
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Internal Raiden node error
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://localhost:5001" path="/api/v1/channels/0xEA67...8ec8" %}
{% api-method-summary %}
All Unsettled Channels for a Specific Token
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="version" type="string" required=true %}
Version of the API
{% endapi-method-parameter %}

{% api-method-parameter name="token\_address" type="string" required=true %}
Address of a token
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successfull query
{% endapi-method-response-example-description %}

```bash
[
    {
        "token_network_address": "0xE5637F0103794C7e05469A9964E4563089a5E6f2",
        "channel_identifier": 20,
        "partner_address": "0x61C808D82A3Ac53231750daDc13c777b59310bD9",
        "token_address": "0xEA674fdDe714fd979de3EdF0F56AA9716B898ec8",
        "balance": 25000000,
        "total_deposit": 35000000,
        "total_withdraw": 5000000,
        "state": "opened",
        "settle_timeout": 100,
        "reveal_timeout": 30
    }
]
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The token address is not a valid EIP55-encoded Ethereum address
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Internal Raiden node error
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://localhost:5001" path="/api/v1/channels/0xEA67...8ec8/0x61C8...0bD9" %}
{% api-method-summary %}
Info About One of Your Channels
{% endapi-method-summary %}

{% api-method-description %}
The channel is specified by the address of a token and the address of the partner node which the channel is opened with.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="version" type="string" required=true %}
Version of the API
{% endapi-method-parameter %}

{% api-method-parameter name="token\_address" type="string" required=true %}
Address of a token
{% endapi-method-parameter %}

{% api-method-parameter name="partner\_address" type="string" required=true %}
Address of the partner node
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successful query
{% endapi-method-response-example-description %}

```bash
{
    "token_network_address": "0xE5637F0103794C7e05469A9964E4563089a5E6f2",
    "channel_identifier": 20,
    "partner_address": "0x61C808D82A3Ac53231750daDc13c777b59310bD9",
    "token_address": "0xEA674fdDe714fd979de3EdF0F56AA9716B898ec8",
    "balance": 25000000,
    "total_deposit": 35000000,
    "total_withdraw": 5000000,
    "state": "opened",
    "settle_timeout": 100,
    "reveal_timeout": 30
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The token address is not a valid EIP55-encoded Ethereum address
The target address is not a valid EIP55-encoded Ethereum address
The channel does not exist
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Internal Raiden node error
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="http://localhost:5001" path="/api/v1/channels" %}
{% api-method-summary %}
Create a Channel
{% endapi-method-summary %}

{% api-method-description %}
The request will open a channel and return a channel object.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="version" type="string" required=true %}
Version of the API
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="partner\_address" type="string" required=true %}
Address of the partner node with whom we're opening the channel
{% endapi-method-parameter %}

{% api-method-parameter name="token\_address" type="string" required=true %}
Address of the token to be used in the channel
{% endapi-method-parameter %}

{% api-method-parameter name="total\_deposit" type="integer" required=true %}
Amount of tokens to be deposited into the channel
{% endapi-method-parameter %}

{% api-method-parameter name="settle\_timeout" type="integer" required=true %}
The number of blocks after which a channel can be settled
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}
Channel successfully created
{% endapi-method-response-example-description %}

```bash
{
    "token_network_address": "0xE5637F0103794C7e05469A9964E4563089a5E6f2",
    "channel_identifier": 20,
    "partner_address": "0x61C808D82A3Ac53231750daDc13c777b59310bD9",
    "token_address": "0xEA674fdDe714fd979de3EdF0F56AA9716B898ec8",
    "balance": 25000000,
    "total_deposit": 35000000,
    "total_withdraw": 0,
    "state": "opened",
    "settle_timeout": 500,
    "reveal_timeout": 30
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The provided JSON is in some way incorrect
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=402 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Insufficient balance of ETH to pay for the on-chain transaction
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=408 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The deposit event was not read on time by the Ethereum node
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=409 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Some invalid input has been provided, e.g. to low settle_timeout value
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Internal Raiden node error
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Example request body:

```bash
{
    "partner_address": "0x61C808D82A3Ac53231750daDc13c777b59310bD9",
    "token_address": "0xEA674fdDe714fd979de3EdF0F56AA9716B898ec8",
    "total_deposit": 35000000,
    "settle_timeout": 500,
    "reveal_timeout": 50
}
```

{% api-method method="patch" host="http://localhost:5001" path="/api/v1/channels/0xEA67...8ec8/0x61C8...0bD9" %}
{% api-method-summary %}
Close a Channel
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="version" type="string" required=true %}
Version of the API
{% endapi-method-parameter %}

{% api-method-parameter name="token\_address" type="string" required=true %}
Address of a token
{% endapi-method-parameter %}

{% api-method-parameter name="partner\_address" type="string" required=true %}
Address of the partner node
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="state" type="string" required=true %}
Can only be set to **"closed"**
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successfully closed channel
{% endapi-method-response-example-description %}

```bash
{
    "token_network_address": "0xE5637F0103794C7e05469A9964E4563089a5E6f2",
    "channel_identifier": 20,
    "partner_address": "0x61C808D82A3Ac53231750daDc13c777b59310bD9",
    "token_address": "0xEA674fdDe714fd979de3EdF0F56AA9716B898ec8",
    "balance": 25000000,
    "total_deposit": 35000000,
    "total_withdraw": 5000000,
    "state": "closed",
    "settle_timeout": 500,
    "reveal_timeout": 30
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The provided JSON is in some way incorrect
"state" has not been provided or don't have the valid value "closed"
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=402 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Insufficient balance of ETH to pay for the on-chain transactions
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The token address is not a valid EIP55-encoded Ethereum address
The target address is not a valid EIP55-encoded Ethereum address
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=409 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The channel does not exist
"total_withdraw" and/or "total_deposit" have been trying to update in the same request
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Internal Raiden node error
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Example request body:

```bash
{
    "state": "closed"
}
```

{% api-method method="patch" host="http://localhost:5001" path="/api/v1/channels/0xEA67...8ec8/0x61C8...0bD9" %}
{% api-method-summary %}
Increase Deposit
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="version" type="string" required=true %}
Version of the API
{% endapi-method-parameter %}

{% api-method-parameter name="token\_address" type="string" required=true %}
Address of a token
{% endapi-method-parameter %}

{% api-method-parameter name="partner\_address" type="string" required=true %}
Address of the partner node
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="total\_deposit" type="integer" required=true %}
Amount of tokens for increasing the total deposit
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successfully increased the deposit
{% endapi-method-response-example-description %}

```bash
{
    "token_network_address": "0xE5637F0103794C7e05469A9964E4563089a5E6f2",
    "channel_identifier": 20,
    "partner_address": "0x61C808D82A3Ac53231750daDc13c777b59310bD9",
    "token_address": "0xEA674fdDe714fd979de3EdF0F56AA9716B898ec8",
    "balance": 25000000,
    "total_deposit": 35000000,
    "total_withdraw": 5000000,
    "state": "closed",
    "settle_timeout": 500,
    "reveal_timeout": 30
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The provided JSON is in some way incorrect
"total_deposit" has not been provided
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=402 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Insufficient balance of ETH to pay for the on-chain transactions
Insufficient token balance for making the desired deposit
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The token address is not a valid EIP55-encoded Ethereum address
The target address is not a valid EIP55-encoded Ethereum address
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=408 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The deposit event was not read on time by the Ethereum node
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=409 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The channel does not exist
"state" and/or "total_withdraw" have been trying to update in the same request
The amount of deposited tokens is lower than the current on-chain token balance in the channel
The amount of deposited tokens is higher than the allowed limit
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Internal Raiden node error
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Example request body:

```bash
{
    "total_deposit": 100
}
```

{% api-method method="patch" host="http://localhost:5001" path="/api/v1/channels/0xEA67...8ec8/0x61C8...0bD9" %}
{% api-method-summary %}
Withdraw Tokens
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="version" type="string" required=true %}
Version of the API
{% endapi-method-parameter %}

{% api-method-parameter name="token\_address" type="string" required=true %}
Address of a token
{% endapi-method-parameter %}

{% api-method-parameter name="partner\_address" type="string" required=true %}
Address of the partner node
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="total\_withdraw" type="integer" required=true %}
Amount of tokens to withdraw
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successfully withdrawn tokens
{% endapi-method-response-example-description %}

```bash
{
    "token_network_address": "0xE5637F0103794C7e05469A9964E4563089a5E6f2",
    "channel_identifier": 20,
    "partner_address": "0x61C808D82A3Ac53231750daDc13c777b59310bD9",
    "token_address": "0xEA674fdDe714fd979de3EdF0F56AA9716B898ec8",
    "balance": 25000000,
    "total_deposit": 35000000,
    "total_withdraw": 5000000,
    "state": "closed",
    "settle_timeout": 500,
    "reveal_timeout": 30
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The provided JSON is in some way incorrect
"total_withdraw" has not been provided
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=402 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Insufficient balance of ETH to pay for the on-chain transactions
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The token address is not a valid EIP55-encoded Ethereum address
The target address is not a valid EIP55-encoded Ethereum address
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=409 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The channel does not exist
"state" and/or "total_deposit" have been trying to update in the same request
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Internal Raiden node error
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Example request body:

```bash
{
    "total_withdraw": 50
}
```

{% api-method method="patch" host="http://localhost:5001" path="/api/v1/channels/0xEA67...8ec8/0x61C8...0bD9" %}
{% api-method-summary %}
Update Reveal Timeout
{% endapi-method-summary %}

{% api-method-description %}
This request will update the number of blocks that are allowed between setting a hashlock and the revealing of the related secret.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="version" type="string" required=true %}
Version of the API
{% endapi-method-parameter %}

{% api-method-parameter name="token\_address" type="string" required=true %}
Address of a token
{% endapi-method-parameter %}

{% api-method-parameter name="partner\_address" type="string" required=true %}
Address of the partner node
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="reveal\_timeout" type="integer" required=true %}
Value for the new reveal timeout
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Example request body:

```bash
{
    "reveal_timeout": 50
}
```

