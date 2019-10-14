---
description: >-
  You can query the version endpoint to see which version of Raiden you're
  currently running.
---

# Version

## Address Resource Overview

| HTTP Method | Resource | Description |
| :--- | :--- | :--- |
| GET | [`/api/<version>/version`](version.md#version-resource-details) | Version of Raiden |

## Version Resource Details

{% api-method method="get" host="http://localhost:5001" path="/api/v1/version" %}
{% api-method-summary %}
Version of Raiden
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
{
    "version": "0.100.5a1.dev157+geb2af878d"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

