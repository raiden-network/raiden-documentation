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

Download the latest Raiden [https://github.com/raiden-network/raiden/releases/](https://github.com/raiden-network/raiden/releases/)

## Run Raiden

You can start Raiden with either Geth, Parity or Infura as RPC Endpoint. All you need is an Ethereum Account and the respective keystore file funded with the tokens you want to transfer.

```console
raiden \
--address $YOUR-ETHEREUM-ADDRESS \
--keystore-path $PATH-TO-YOUR-KEYSTORE-FILE \
--password-file $PASSWORD-FILE-FOR-KEYSTORE-FILE \
--eth-rpc-endpoint $YOUR-ETHEREUM-NODE
```

In doubt, you can use 

```console
raiden --help
```

to see all possible CLI arguments. 

## Certain defaults for the usage of the Raiden services are set

Per default a **Pathfinding Service** is used by your Raiden client when a **mediated transfer** is initiated. The maximum amount paid for one request to the Pathfinding services is set to `0.05` RDN and 3 different paths are requested.

```console
--pathfinding-service-address auto \
--pathfinding-max-fee 50000000000000000 \
--pathfinding-max-paths 3
```

By default the **Monitoring Services** are disabled. Enabling monitoring of channels will require a default reward value of `5` RDN for successfully monitoring your channel.

```console
--enable-monitoring FALSE
```

## Testnet usage

When using one of the Ethereum testnets, you have to set the `--environment-type` to development-mode,
so that the correct Matrix federation network for the PFS will be chosen.

In order to connect to one of the Ethereum testnets, you have to provide the following additional arguments:

```console
--network-id $TESTNET-NAME-OR-ID \
--environment-type development 
```

E.g. for the Goerli testnet `$TESTNET-NAME-OR_ID` would be `goerli` or `5`.

More information on how to aquire and deposit the utility token (SVT) on the testnets are [provided in the v1 docs](https://raiden-network.readthedocs.io/en/latest/overview_and_guide.html#depositing-tokens-to-pay-the-services).

