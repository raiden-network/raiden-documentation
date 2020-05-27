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

Download Raiden Alderaan [https://github.com/raiden-network/raiden/releases/tag/v1.0.0](https://github.com/raiden-network/raiden/releases/tag/v1.0.0)

* macOS
* Linux

## Run Raiden

You can start Raiden with either Geth, Parity or Infura as RPC Endpoint. All you need is an Ethereum Account and the respective keystore file funded with the tokens you want to transfer.

```text
raiden /
--address $YOUR-ETHEREUM-ADDRESS / 
--keystore-path $PATH-TO-YOUR-KEYSTORE-FILE /
--password-file $PASSWORD-FILE-FOR-KEYSTORE-FILE /
--eth-rpc-endpoint $YOUR-ETHEREUM-NODE
```

In doubt, you can use 

```text
raiden --help
```

to see all possible CLI arguments. 

## Certain defaults for the usage of the Raiden services are set

Per default a **Pathfinding Service** is used by your Raiden client when a **mediated transfer** is initiated. The maximum amount paid for one request to the Pathfinding services is set to `0.05` RDN and 3 different paths are requested.

```text
--pathfinding-service-address auto /
--pathfinding-max-fee 50000000000000000 /
--pathfinding-max-paths 3
```

By default the **Monitoring Services** are disabled. Enabling monitoring of channels will require a default reward value of `5` RDN for successfully monitoring your channel.

```text
--enable-monitoring FALSE
```

