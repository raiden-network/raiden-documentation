---
description: >-
  You can mint tokens for testing purposes by making a request to the _testing
  endpoint.
---

# Testing

| HTTP Method | Resource | Description |
| :--- | :--- | :--- |
| POST | [`/api/<version>/_testing/tokens/<token_address>/mint`](testing.md#mint-tokens) | Mint tokens |

{% hint style="warning" %}
Some tokens might require you to have minter privileges.
{% endhint %}

{% api-method method="post" host="http://localhost:5001" path="/api/v1/\_testing/tokens/0x782C...8209/mint" %}
{% api-method-summary %}
Mint Tokens
{% endapi-method-summary %}

{% api-method-description %}
The request will return the hash of the minting transaction.
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
{% api-method-parameter name="to" type="string" required=true %}
An address for which to deposit the minted tokens
{% endapi-method-parameter %}

{% api-method-parameter name="value" type="integer" required=true %}
Amount of tokens to be minted
{% endapi-method-parameter %}

{% api-method-parameter name="contract\_method" type="string" required=true %}
Name of the minting method in the smart contract, must be set to either **"mint"**, **"mintFor"**, or **"increaseSupply"**.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successful transaction
{% endapi-method-response-example-description %}

```bash
{
    "transaction_hash": "0x90896386c5b218d772c05586bde5c37c9dc90db5de660bba5bd897705c976edb"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The request failed
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Example request:

```bash
{
    "to": "0x2c4b0Bdac486d492E3cD701F4cA87e480AE4C685",
    "value": 1000,
    "contract_method": "mintFor"
}
```

