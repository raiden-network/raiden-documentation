---
description: >-
  By querying the contracts endpoint you can check which on-chain smart
  contracts are used.
---

# Contracts Information

## Contracts Resource Overview

| HTTP Method | Resource | Description |
| :--- | :--- | :--- |
| GET | `/api/<version>/contracts` | Addresses of the used smart contracts |

## Contracts Resource Details

{% api-method method="get" host="http://localhost:5001" path="/api/v1/contracts" %}
{% api-method-summary %}
Contract information
{% endapi-method-summary %}

{% api-method-description %}
Queries the version and addresses of the smart contracts used by the Raiden client.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="version" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successful query
{% endapi-method-response-example-description %}

```
{
    "contracts_version": "0.37.1",
    "monitoring_service_address": "0x20e8e5181000e60799A523a2023d630868f378Fd",
    "one_to_n_address": "0xA514Da2418576CeC4070C82996f30532dDa99706",
    "secret_registry_address": "0x9fC80eb1939d8147aB90BAC01AD585f3a71BeE7e",
    "service_registry_address": "0x3bc9C8d34f5714327095358668fD436D7c457C6C",
    "token_network_registry_address": "0x5a5CF4A63022F61F1506D1A2398490c2e8dfbb98",
    "user_deposit_address": "0x0794F09913AA8C77C8c5bdd1Ec4Bb51759Ee0cC5"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



