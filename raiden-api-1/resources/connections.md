---
description: >-
  The connections endpoints allow you to automatically connect to a token
  network as well as leave a token network by closing and settling all open
  channels.
---

# Connections

## Connections Resource Overview

| HTTP Method | Resource | Description |
| :--- | :--- | :--- |
| GET | [`/api/<version>/connections`](connections.md#details-of-all-joined-token-networks) | Details of all joined token networks |
| PUT | [`/api/<version>/connections/<token_address>`](connections.md#join-a-token-network) | Join a token network |
| DELETE | [`/api/<version>/connections/<token_address>`](connections.md#leave-a-token-network) | Leave a token network |

{% hint style="warning" %}
Currently all API calls are blocking. In case of long running API calls like joining or leaving a token network, if any concurrent API calls are made they will be queued.
{% endhint %}

## Connections Resource Details

{% api-method method="get" host="http://localhost:5001" path="/api/v1/connections" %}
{% api-method-summary %}
Details of All Joined Token Networks
{% endapi-method-summary %}

{% api-method-description %}
Each key in the JSON response object is a token address for which you have open channels.
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
  
The value for the token address key is an object containing:  
- "funds", an integer of the token amount from your last connect request  
- "sum\_deposits", an integer of the sum of deposits in all currently open channels  
- "channels", an integer of all channels currently open for the specific token
{% endapi-method-response-example-description %}

```bash
{
    "0x2a65Aca4D5fC5B5C859090a6c34d164135398226": {
        "funds": 100,
        "sum_deposits": 67,
        "channels": 3
    },
    "0x0f114A1E9Db192502E7856309cc899952b3db1ED": {
        "funds": 49,
        "sum_deposits": 31,
        "channels": 1
    }
}
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

{% api-method method="put" host="http://localhost:5001" path="/api/v1/connections/0x2a65...8226" %}
{% api-method-summary %}
Join a Token Network
{% endapi-method-summary %}

{% api-method-description %}
Calling this endpoint lets you join the token network for the specified token and automatically open channels.  
  
If you have already joined the token network for the specified token a call to this endpoint can be made to change the funds allocated in the token network.  
  
The request might take some time and will only return once all blockchain calls for opening and/or depositing to a channel have been completed.
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

{% api-method-body-parameters %}
{% api-method-parameter name="funds" type="integer" required=true %}
Amount of tokens to be put into the network
{% endapi-method-parameter %}

{% api-method-parameter name="initial\_channel\_target" type="integer" required=false %}
Number of channels to open proactively, defaults to 3 if nothing is provided
{% endapi-method-parameter %}

{% api-method-parameter name="joinable\_funds\_target" type="number" required=false %}
Floating point number as a fraction of the funds that will be reserved for joining channels opened by others, defaults to 0.4 if nothing is provided.  
  
This means that of 100 tokens 40 will get reserved.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
A successful connection has been created
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
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=408 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
A timeout happened during any of the transactions
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=409 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Some invalid input has been provided
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

#### Example request:

```bash
{
    "funds": 1337
}
```

{% hint style="warning" %}
If the number of channels provided as a value for `initial_channel_target` is greater than the current number of peers in the token network the funds will still get split according to the value you provided.

This means that if you have funds of 100 tokens and want to open 4 channels but there are only 3 peers in the network then 15 tokens will get distributed for the 3 channels while the remaining 15 will be used for opening a 4th channel as soon as one more peer becomes available.
{% endhint %}

{% api-method method="delete" host="http://localhost:5001" path="/api/v1/connections/0x2a65...8226" %}
{% api-method-summary %}
Leave a Token Network
{% endapi-method-summary %}

{% api-method-description %}
The request might take some time and will only return once all blockchain calls for closing and settling a channel have been completed.  
  
The response is a list with addresses of all closed channels.
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
Successfully leaving a token network
{% endapi-method-response-example-description %}

```bash
[
    "0x41BCBC2fD72a731bcc136Cf6F7442e9C19e9f313",
    "0x5A5f458F6c1a034930E45dC9a64B99d7def06D7E",
    "0x8942c06FaA74cEBFf7d55B79F9989AdfC85C6b85"
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

