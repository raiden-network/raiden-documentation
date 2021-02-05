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
- "funds", a string of the token amount from your last connect request  
- "sum\_deposits", a string of the sum of deposits in all currently open channels  
- "channels", a string of all channels currently open for the specific token
{% endapi-method-response-example-description %}

```bash
{
    "0x2a65Aca4D5fC5B5C859090a6c34d164135398226": {
        "funds": "100",
        "sum_deposits": "67",
        "channels": "3"
    },
    "0x0f114A1E9Db192502E7856309cc899952b3db1ED": {
        "funds": "49",
        "sum_deposits": "31",
        "channels": "1"
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

