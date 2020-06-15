---
description: >-
  The payment endpoint is used for transferring tokens to another node. You can
  send the desired amount of tokens by providing the address of the token and
  the address of the receiving node.
---

# Payments

## Payments Resource Overview

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
      <td style="text-align:left">
        <p><a href="payments.md#payment-history"><code>/api/&lt;version&gt;/payments/&lt;token_address&gt;</code></a>
        </p>
        <p><a href="payments.md#payment-history"><code>/&lt;target_address&gt;</code></a>
        </p>
      </td>
      <td style="text-align:left">Payment history</td>
    </tr>
    <tr>
      <td style="text-align:left">POST</td>
      <td style="text-align:left">
        <p><a href="payments.md#initiate-a-payment"><code>/api/&lt;version&gt;/payments/&lt;token_address&gt;</code></a>
        </p>
        <p><a href="payments.md#initiate-a-payment"><code>/&lt;target_address&gt;</code></a>
        </p>
      </td>
      <td style="text-align:left">Initiate a payment</td>
    </tr>
  </tbody>
</table>

## Payment Resource Details

{% api-method method="get" host="http://localhost:5001" path="/api/v1/payments/0x0f11...b1ED/0x8264...5ba7" %}
{% api-method-summary %}
Payment History
{% endapi-method-summary %}

{% api-method-description %}
When querying the payment history the response will include:  
- "EventPaymentSentSuccess" for successful payments  
- "EventPaymentSentFailed" for failed payments  
- "EventPaymentReceivedSuccess" for received payments
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="version" type="string" required=true %}
Version of the API
{% endapi-method-parameter %}

{% api-method-parameter name="token\_address" type="string" required=false %}
Address of a token, will filter response list according to token\_address
{% endapi-method-parameter %}

{% api-method-parameter name="target\_address" type="string" required=false %}
Address of the receiving node, will filter response list according to target\_address
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="?limit=" type="integer" required=false %}
Limits the payment history result to the amount specified after =
{% endapi-method-parameter %}

{% api-method-parameter name="&offset=" type="integer" required=false %}
Offsets the payment history result by the amount specified after =
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successful query
{% endapi-method-response-example-description %}

```bash
[
    {
        "event": "EventPaymentSentSuccess",
        "amount": "20",
        "target": "0x82641569b2062B545431cF6D7F0A418582865ba7",
        "identifier": "3",
        "log_time": "2018-10-30T07:10:13.122",
        "token_address": "0x62083c80353Df771426D209eF578619EE68D5C7A"
    },
    {
        "target": "0x82641569b2062B545431cF6D7F0A418582865ba7",
        "event": "EventPaymentSentFailed",
        "log_time": "2018-10-30T07:04:22.293",
        "reason": "there is no route available",
        "token_address": "0x62083c80353Df771426D209eF578619EE68D5C7A"
    },
    {
        "event": "EventPaymentReceivedSuccess",
        "amount": "5",
        "initiator": "0x82641569b2062B545431cF6D7F0A418582865ba7",
        "identifier": "1",
        "log_time": "2018-10-30T07:03:52.193",
        "token_address": "0x62083c80353Df771426D209eF578619EE68D5C7A"
    }
]
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The token address is not a valid EIP55-encoded Ethereum address
The target address is not a valid EIP55-encoded Ethereum address
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=409 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
An invalid token address has been provided
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

{% api-method method="post" host="http://localhost:5001" path="/api/v1/payments/0x2a65...8226/0x61C8...0bD9" %}
{% api-method-summary %}
Initiate a Payment
{% endapi-method-summary %}

{% api-method-description %}
The request might take some time and will only return once the payment either succeeds or fails.
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

{% api-method-parameter name="target\_address" type="string" required=true %}
Address of the receiving node
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="amount" type="string" required=true %}
Amount of tokens to be sent
{% endapi-method-parameter %}

{% api-method-parameter name="identifier" type="string" required=false %}
Integer for identifying the payment
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successful payment
{% endapi-method-response-example-description %}

```bash
{
    "initiator_address": "0xEA674fdDe714fd979de3EdF0F56AA9716B898ec8",
    "target_address": "0x61C808D82A3Ac53231750daDc13c777b59310bD9",
    "token_address": "0x2a65Aca4D5fC5B5C859090a6c34d164135398226",
    "amount": "200",
    "identifier": "42"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The provided JSON is in some way incorrect
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=402 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The payment can't start due to insufficient balande
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
The token address is not a valid EIP55-encoded Ethereum address
The target address is not a valid EIP55-encoded Ethereum address
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=408 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
A timeout happened during the payment
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=409 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
An invalid token and/or target address has been provided
An invalid token amount has been provided
There is no path to the receiving node
The identifier is already in use for a different payment
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

#### Example request body:

```bash
{
    "amount": "200",
    "identifier" "42"
}
```

{% hint style="warning" %}
**Failing Payments**

A payment can fail due to:

* The secret for opening the hashlock not being revealed in time and the lock expires
* The target node being offline
* The channels leading to the target node not having enough `settle timeout` and `reveal_timeout`
* The funds not being enough
{% endhint %}

