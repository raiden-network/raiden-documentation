---
description: You can call the shutdown endpoint to stop a running Rainde node.
---

# Shutdown

## Shutdown Resource Overview

| HTTP Method | Resource | Description |
| :--- | :--- | :--- |
| POST | [`/api/<version>/shutdown`](shutdown.md#shutdown-resource-details) | Shutdown Raiden |

## Shutdown Resource Details

{% api-method method="post" host="http://localhost:5001" path="/api/v1/shutdown" %}
{% api-method-summary %}
Shutdown Raiden
{% endapi-method-summary %}

{% api-method-description %}
Stop a running Raiden node.
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
Successfully shutdown Raiden node
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

