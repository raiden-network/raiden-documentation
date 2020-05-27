---
description: >-
  Starting Raiden manually gives you full control where you don't need to adhere
  to the values provided by the Raiden Wizard.
---

# Starting Raiden Manually

You might want to start Raiden manually if:

* You want to run a Raiden node on either mainnet or any testnet.
* You want to configure Raiden with your preferred settings.
* You already have the knowledge on how to acquire all necessary tokens.

## Downloading Raiden

Download Raiden for:

* macOS
* Linux

## Run Raiden

Open your terminal and provide the path to the Raiden binary with the following default configurations:

```text
--routing-mode PFS
```

This allows your Raiden client to request routes from the **Pathfinding Services** when doing mediated transfers.

```text
--pathfinding-service-address auto /
--pathfinding-max-fee 50000000000000000 /
--pathfinding-max-paths 3
```

This will set the maximum amout paid for the pathfinding services to `0.05` RDN and request 3 different paths.

```text
--enable-monitoring FALSE
```

By default the **Monitoring Services** are disabled. Enabling monitoring of channels will require a default reward value of `5` RDN for successfullt monitoring your channel.

