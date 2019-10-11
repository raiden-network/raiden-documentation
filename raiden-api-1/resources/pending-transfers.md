---
description: >-
  The pending transfers endpoints let you query information about transfers that
  have not been completed yet.
---

# Pending Transfers

## Pending Transfers Resource Overview

<table>
  <thead>
    <tr>
      <th style="text-align:left">HTTP Method</th>
      <th style="text-align:left">Resource</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">GET</td>
      <td style="text-align:left"><a href="pending-transfers.md#all-incomplete-transfers"><code>/api/&lt;version&gt;/pending_transfers</code></a>
      </td>
      <td style="text-align:left">All incomplete transfers</td>
    </tr>
    <tr>
      <td style="text-align:left">GET</td>
      <td style="text-align:left"><a href="pending-transfers.md#all-incomplete-transfers-for-a-specific-token"><code>/api/&lt;version&gt;/pending_transfers/&lt;token_address&gt;</code></a>
      </td>
      <td style="text-align:left">All incomplete transfers for a specific token</td>
    </tr>
    <tr>
      <td style="text-align:left">GET</td>
      <td style="text-align:left">
        <p><a href="pending-transfers.md#all-incomplete-transfers-for-a-specific-token-and-channel"><code>/api/&lt;version&gt;/pending_transfers/&lt;token_address&gt;</code></a>
        </p>
        <p><a href="pending-transfers.md#all-incomplete-transfers-for-a-specific-token-and-channel"><code>/&lt;partner_address&gt;</code></a>
        </p>
      </td>
      <td style="text-align:left">All incomplete transfers for a specific token and channel</td>
    </tr>
  </tbody>
</table>## Pending Transfers Resource Details

{% api-method method="get" host="http://localhost:5001" path="/api/v1/pending\_transfers" %}
{% api-method-summary %}
All Incomplete Transfers
{% endapi-method-summary %}

{% api-method-description %}
The "role" key in the response can either have the value "initiator", "mediator" or "target".
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
        "channel_identifier": "255",
        "initiator": "0x5E1a3601538f94c9e6D2B40F7589030ac5885FE7",
        "locked_amount": "119",
        "payment_identifier": "1",
        "role": "initiator",
        "target": "0x00AF5cBfc8dC76cd599aF623E60F763228906F3E",
        "token_address": "0xd0A1E359811322d97991E03f863a0C30C2cF029C",
        "token_network_addrss": "0x111157460c0F41EfD9107239B7864c062aA8B978",
        "transferred_amout": "331"
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

{% api-method method="get" host="http://localhost:5001" path="/api/v1/pending\_transfers/0xd0A1...029C" %}
{% api-method-summary %}
All Incomplete Transfers for a Specific Token
{% endapi-method-summary %}

{% api-method-description %}
Limits the response to pending transfers of the specified token.  
  
The "role" key in the response can either have the value "initiator", "mediator" or "target".
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
        "channel_identifier": "255",
        "initiator": "0x5E1a3601538f94c9e6D2B40F7589030ac5885FE7",
        "locked_amount": "119",
        "payment_identifier": "1",
        "role": "initiator",
        "target": "0x00AF5cBfc8dC76cd599aF623E60F763228906F3E",
        "token_address": "0xd0A1E359811322d97991E03f863a0C30C2cF029C",
        "token_network_addrss": "0x111157460c0F41EfD9107239B7864c062aA8B978",
        "transferred_amout": "331"
    }
]
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
No results found for the token specified in the query
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

{% api-method method="get" host="http://localhost:5001" path="/api/v1/pending\_transfers/0xd0A1...029C/0x2c4b...C685" %}
{% api-method-summary %}
All Incomplete Transfers for a Specific Token and Channel
{% endapi-method-summary %}

{% api-method-description %}
Limits the response to pending transfers of the specified token and channel.  
  
The "role" key in the response can either have the value "initiator", "mediator" or "target".
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
Address of the receiving node
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
        "channel_identifier": "255",
        "initiator": "0x5E1a3601538f94c9e6D2B40F7589030ac5885FE7",
        "locked_amount": "119",
        "payment_identifier": "1",
        "role": "initiator",
        "target": "0x00AF5cBfc8dC76cd599aF623E60F763228906F3E",
        "token_address": "0xd0A1E359811322d97991E03f863a0C30C2cF029C",
        "token_network_addrss": "0x111157460c0F41EfD9107239B7864c062aA8B978",
        "transferred_amout": "331"
    }
]
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
No result found for the token specified in the query
No result found for the channel specified in the query
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

