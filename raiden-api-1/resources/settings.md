---
description: >-
  By querying the settings endpoint you can check which settings you are running
  your Raiden node with.
---

# Settings

## Settings Resource Overview

| HTTP Method | Resource | Description |
| :--- | :--- | :--- |
| GET | [`/api/<version>/settings`](settings.md#settings-information) | Settings of your Raiden node |

## Settings Resource Details

{% api-method method="get" host="http://localhost:5001" path="/api/v1/settings" %}
{% api-method-summary %}
Settings Information
{% endapi-method-summary %}

{% api-method-description %}
Queries the settings of your Raiden node. At the moment only the URL of the pathfinding service is returned. The endpoint will provide more settings in the future.
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

```
{
    "pathfinding_service_address": "https://pfs.transport04.raiden.network"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

