---
description: >-
  To do mediated transfers we need to have RDN (Raiden Network Tokens) in the
  UDC (User Deposit Contract) for paying the monitoring and pathfinding
  services.
---

# Deposit Tokens to the UDC

This section will describe how to manually add Raiden Network Tokens to the UDC by:

1. [Approving the UDC to use RDN](deposit-tokens-to-the-udc.md#approving-the-udc-to-use-rdn)
2. [Using Etherscan to deposit RDN to the UDC](deposit-tokens-to-the-udc.md#using-etherscan-to-deposit-rdn-to-the-udc)

## Approving the UDC to use RDN

We need to approve a value of Raiden Network Tokens that the UDC is allowed to spend. To do so:

1. Visit the [RDN token on Etherscan](https://etherscan.io/address/0x255Aa6DF07540Cb5d3d297f0D0D4D84cb52bc8e6#writeContract).
2. Go to the "**approve"** field under "**Write Contract"**.
3. Enter `0x1c62fF66aF8aaD410065E02338F5bFbbe23e1f10` \(the mainnet UDC address\) as argument for **"\_spender"**.
4. Enter an amount of `100000000000000000000` \(corresponding to 100 RDN\) as argument for **"\_value"**.
5. Click on **"Write"** to approve.

## Using Etherscan to deposit RDN to the UDC

Once we obtained the UDC address and approved a RDN amount all that reamins is for us to deposit tokens to the UDC.

1. Visit the [UDC on Etherscan](https://etherscan.io/address/0x1c62fF66aF8aaD410065E02338F5bFbbe23e1f10#writeContract).
2. Go to the **"deposit"** field under **"Write Contract"**.
3. Enter the address of the Raiden node you want to use as argument for **"beneficiary"**.
4. Enter an amount of e.g. `20000000000000000000` \(corresponding to 20 RDN\) as argument for **"new\_total\_deposit"**.
5. Click on **"Write"** to make the deposit.

