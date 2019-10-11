---
description: >-
  By querying the address endpoint you can check whether a Raiden node is up and
  running correctly.
---

# Address

## Address Resource Overview

| HTTP Method | Resource | Description |
| :--- | :--- | :--- |
| GET | [`/api/<version>/address`](address.md#info-about-your-raiden-node) | Info about your Raiden node |

## Address Resource Details

{% api-method method="get" host="http://localhost:5001" path="/api/v1/address" %}
{% api-method-summary %}
Info About Your Raiden Node
{% endapi-method-summary %}

{% api-method-description %}
Queries the Ethereum address you choose when starting Raiden. A Raiden node is up and running correctly if the response returns that same address.
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
{
    "our_address": "0x2a65Aca4D5fC5B5C859090a6c34d164135398226"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

