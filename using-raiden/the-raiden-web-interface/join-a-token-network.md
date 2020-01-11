---
description: >-
  To be able to make payments in Raiden you first need to join the network for
  the token you're interested in making payments with.
---

# Join a Token Network

To join a token network navigate to the **"Tokens"** screen where you can choose to either:

* [Join an existing token network](join-a-token-network.md#join-an-existing-token-network)
* [Register a new token and join its network](join-a-token-network.md#register-a-new-token-and-join-its-network)

{% hint style="info" %}
**What is a token?**

Each token is defined within its own ERC20 compliant smart contract and each smart contract has a total supply of tokens. The token contracts are like a registry where different amounts of the total supply are mapped to different owners.
{% endhint %}

{% hint style="info" %}
**What Is a token network?**

Anyone who runs a Raiden node and owns a token can join a network with other nodes who own the very same token. All nodes registered within such network form a token network.
{% endhint %}

## Join an existing token network

![Tokens Screen](../../.gitbook/assets/web_ui_join_network_1%20%281%29.png)

Click the **"JOIN NETWORK"** button next to the token which network you want to join.

![Tokens screen](../../.gitbook/assets/web_ui_join_network_2.png)

Enter the amount of tokens you want to allocate and click **"Join"**.

The amount you choose is what will be available for making payments and you can always [add more funds later](add-more-tokens.md). 

**Joining a token network is an on-chain activity and will therefore consume some of your ETH.**

You're now ready to make a first payment!

{% page-ref page="payment.md" %}

## Register a new token and join its network

If you want to join the network for a token and the token is not displayed in the list of tokens it might mean that it has not been registered yet. In this case you can register it yourself.

![Tokens screen](../../.gitbook/assets/web_ui_register_token_1.png)

Click the upper right **"+"** button.

![Tokens screen](../../.gitbook/assets/web_ui_register_token_2%20%281%29.png)

Enter the address of the token you want to register and click **"Register"**.

To join the network of your newly registered token follow the steps for [joining an existing token network](join-a-token-network.md#join-an-existing-token-network).

