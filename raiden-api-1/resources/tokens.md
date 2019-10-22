---
description: >-
  The tokens endpoints are used for registering new tokens and querying
  information about already registered tokens.
---

# Tokens

## Tokens Resource Overview

| HTTP Method | Resource | Description |
| :--- | :--- | :--- |
| GET | [`/api/<version>/tokens`](tokens.md#addresses-for-all-registered-tokens) | Addresses for all registered tokens |
| GET | [`/api/<version>/tokens/<token_address>`](tokens.md#address-of-token-network-for-a-specific-token) | Address of token network for a specific token |
| GET | [`/api/<version>/tokens/<token_address>/partners`](tokens.md#all-partner-nodes-with-unsettled-channels-for-a-specific-token) | All partner nodes with unsettled channels for a specific token |
| PUT | [`/api/<version>/tokens/<token_address>`](tokens.md#register-a-token) | Register a token |

{% hint style="warning" %}
**Alderaan Token Registration**

For the Alderaan release two tokens will be registered, **DAI** and **WETH**.
{% endhint %}

## Tokens Resource Details

{% api-method method="get" host="http://localhost:5001" path="/api/v1/tokens" %}
{% api-method-summary %}
Addresses for All Registered Tokens
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
    "0xEA674fdDe714fd979de3EdF0F56AA9716B898ec8",
    "0x61bB630D3B2e8eda0FC1d50F9f958eC02e3969F6"
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

{% api-method method="get" host="http://localhost:5001" path="/api/v1/tokens/0xEA67...8ec8" %}
{% api-method-summary %}
Address of Token Network for a Specific Token
{% endapi-method-summary %}

{% api-method-description %}
The request will return the token network address for the specified token only if the token is already registered.
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
Successful query
{% endapi-method-response-example-description %}

```
"0x61bB630D3B2e8eda0FC1d50F9f958eC02e3969F6"
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
No token network was found for the provided token address
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://localhost:5001" path="/api/v1/tokens/0x61bB...69F6/partners" %}
{% api-method-summary %}
All Partner Nodes With Unsettled Channels for a Specific Token
{% endapi-method-summary %}

{% api-method-description %}
The value for the "channel" key in the response is a link to the channel resource.
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
Successful query
{% endapi-method-response-example-description %}

```bash
[
    {
        "partner_address": "0x2a65aca4d5fc5b5c859090a6c34d164135398226",
        "channel": "/api/<version>/channels/0x61C808D82A3Ac53231750daDc13c777b59310bD9/0x2a65aca4d5fc5b5c859090a6c34d164135398226"
    }
]
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=302 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
If the user accesses the channel link endpoint
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The token does not exist
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

{% api-method method="put" host="http://localhost:5001" path="/api/v1/tokens/0xEA67...8ec8" %}
{% api-method-summary %}
Register a Token
{% endapi-method-summary %}

{% api-method-description %}
A token needs to be registered for a token network to exist for that specific token.
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
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}
A token network for the specified token has been successfully created
{% endapi-method-response-example-description %}

```bash
{
    "token_network_address": "0xC4F8393fb7971E8B299bC1b302F85BfFB3a1275a"
}
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
The token address is not valid
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=409 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The token has already been registered
The registration transaction failed
The address does not contain code
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=501 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Registering a token only works on testnet.
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

