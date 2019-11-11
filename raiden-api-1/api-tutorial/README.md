---
description: >-
  This tutorial will show you how to use Raiden via the API by walking you
  through a few API calls. The steps are similar to the WebUI tutorial, but
  directly use the API endpoints.
---

# API Tutorial

We will outline the steps necessary for participating in a token network. To see all available endpoints visit the [resources](../resources/) part of the documentation.

In the examples throughout this tutorial we will be using a hypothetical ERC20 token with the address `0x9aBa529db3FF2D8409A1da4C9eB148879b046700`.

## Check if Raiden was started correctly

Before we start we'll make sure that Raiden is running correctly.

This gives us an opportunity to introduce the [`address`](../resources/address.md#info-about-your-raiden-node) endpoint.

```bash
curl -i http://localhost:5001/api/v1/address
```

Your Raiden node is up and running if the response returns the same address as the Ethereum address used for starting Raiden.

## Overview

You're now ready to start interacting with the different endpoints and learn how they can be used to:

{% page-ref page="1-join-a-token-network.md" %}

{% page-ref page="2-open-a-channel.md" %}

{% page-ref page="3-deposit.md" %}

{% page-ref page="3-make-a-payment.md" %}

{% page-ref page="withdraw-tokens.md" %}

{% page-ref page="4-settle-payments-and-close-channels.md" %}

