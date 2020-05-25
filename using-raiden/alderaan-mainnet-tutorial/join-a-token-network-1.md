# Join a Token Network

To join a token network we have to make a PUT request to the [`connections`](../../raiden-api-1/resources/connections.md#join-a-token-network) connections endpoint and provide:

1. The address of the W-ETH token as a path parameter.
2. The amount of tokens you want to deposit in the channel as a body parameter. The

   token values in this tutorial are denoted in WEI. 1 W-ETH is equivialent to 10^18 WEI.

```text
curl -i -X PUT \
http://localhost:5001/api/v1/connections/0xC02aaA39b223FE8D0A0e5C4F27eAD90 \
-H 'Content-Type: application/json' \
--data-raw '{"funds":"20000"}'
```

{% hint style="info" %}
Raiden utilizes a RESTful API where all URL paths starts with `/api/` followed by a version number. The current API version is `1` and therefore all requests begins with `/api/v1/` .
{% endhint %}

When you join a token network three channels will automatically be opened with random nodes. 20% of the tokens will be deposited in each channel and the remaining 40% are reserved for whenever you are joining a channel that has been opened by another node.

We're now ready to start sending W-ETH tokens!

{% page-ref page="make-a-payment.md" %}

