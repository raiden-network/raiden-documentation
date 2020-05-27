---
description: >-
  In this step, we will be setting all parameters and finally deploy the custom
  token to the Goerli testnet.
---

# Deploy Custom Token

Navigate to **"DEPLOY & RUN TRANSACTIONS"** in the left hand side menu.

![](../../.gitbook/assets/remix_deploy.png)

1. Select **"Injected Web3"** from the "Environment" dropdown. This will open up MetaMask.
2. Connect with MetaMask when prompted.
3. Click on the arrow next to the orange **"Deploy"** button to expand the configure parameters.
4. Use the following parameter values:
   * **initial\_supply** **= 10000**
   * **decimal\_units = 0**
   * **token\_name = MyToken**
   * **token\_symbol = TKN**
5. Click the orange **"transact"** button.
6. Confirm the transaction from MetaMask when prompted.

In the Remix Ethereum IDE terminal you should now see an output similar to the picture below. Congratulations, you have now successfully deployed a token to ethereum!

![](../../.gitbook/assets/remix_deploy3.png)

You can click the link in the terminal output that starts with "https://goerli.etherscan.io..." to open a new tab with all the details of the transaction you just sent.

All you need to do to start using your token is to download and install Raiden and register your token in Raiden.

