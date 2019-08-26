---
description: Running a Raiden node with the Raiden Wizard
---

# Quick Start

## Overview

This tutorial will teach you how to:

* [Download the Raiden Wizard](./#download-the-raiden-wizard)
* [Setup and run Raiden](./#setup-and-run-raiden)
* [Get an Infura Project ID](./#get-an-infura-project-id)
* [Relaunch Raiden](./#relaunch-raiden)
* [Handle limitations and shortcomings](./#handle-limitations-and-shortcomings)

### Download the Raiden Wizard

Download the Raiden Wizard for either macOS or Linux.

[**macOS download**](https://github.com/raiden-network/raiden-installer/releases/download/v0.100.5-dev0/raiden_wizard.macOS.zip)\*\*\*\*

[**Linux download**](https://github.com/raiden-network/raiden-installer/releases/download/v0.100.5-dev0/raiden_wizard.linux-gnu.zip)\*\*\*\*

### **Setup and Run Raiden**

1. Extract and open the **Raiden Wizard** file. The Wizard will launch in your default browser.
2. Insert your Infura Project ID. Don't have a Infura Project ID? Get one in the [section below](./#get-an-infura-project-id).
3. Click **"Create New Configuration"** to configure, install and launch the latest Raiden.

{% hint style="warning" %}
The setup process can take up to five minutes, make sure not to close the browser.
{% endhint %}

#### You are now running a Raiden node!  ****🎉

Congratulations! Now you can start interacting with Raiden!

To get an overview of how to use the web interface, you can:

[Read this tutorial about the web interface](the-raiden-web-interface.md)

[Watch this video on the web interface](https://www.youtube.com/watch?v=ASWeFdHDK-E)

![The Raiden Wizard setup process](.gitbook/assets/raiden_wizard_installation_process.gif)

#### For developers

If you are interested in contributing to the Raiden Wizard, a good start is to:

Read the our [contributing guide](https://github.com/raiden-network/raiden-installer/blob/master/CONTRIBUTING.md)

### Get an Infura Project ID

1. Visit [infura.io](https://infura.io/) and sign up for a new account.
2. Create a new project.
3. View your project and you'll find the Project ID under the **KEYS** tab.

![Steps to get a Infura Project ID](.gitbook/assets/infura_project_id_setup.gif)

{% hint style="info" %}
**What is Infura and why do I need a Project ID?**

By using Infura you don't have to worry about syncing the blockchain on your own system. You can simply access all test networks and the Ethereum mainnet through the API endpoints provided by Infura.

The Raiden Wizard sets up a Raiden node on top of Infura and your Project ID works as a way to authenticate your access to Infura.
{% endhint %}

### Relaunch Raiden

Open the **Raiden Wizard** file, you will find two ways of relaunching Raiden.

1. Click the **"Launch"** button next to a configuration you already created.
2. Repeat the steps from [Setup and Run Raiden](./#setup-and-run-raiden) to create a new configuration.

{% hint style="warning" %}
Each new configuration created will be added to the list and currently you can't delete configurations from the Wizard. Read more under [Handle Limitations and Shortcomings](./#handle-limitations-and-shortcomings).
{% endhint %}

### Handle Limitations and Shortcomings

The Raiden Wizard is in an early stage of implementation. In this section you will learn how to handle known limitations and shortcomings.

{% hint style="danger" %}
**Important**

The Raiden Wizard will display an _**Internal Server Error**_ ****if an invalid Project ID is provided. To solve this you have to [manually delete the configuration](./#delete-configuration-files) file that got created.
{% endhint %}

#### Stop Raiden from Running

The Wizard does not provide a way of shutting down the Raiden node. You have to cancel the process to stop Raiden.

{% tabs %}
{% tab title="Mac" %}
Use the Activity Monitor app for stopping the Raiden process.
{% endtab %}

{% tab title="Linux" %}
Use any Linux process manager for stopping the Raiden process.
{% endtab %}
{% endtabs %}

#### Delete Configuration Files

You might want to delete configuration files if the Wizard is taking a long time to start or if an invalid Project ID has been provided and the Wizard won't start at all.

{% tabs %}
{% tab title="Mac" %}
Navigate to following folder:

```text
/Users/<username>/.local/share/raiden/
```

Delete desired **.toml** file/files.
{% endtab %}

{% tab title="Linux" %}
Navigate to following folder:

```text
/home/<username>/.local/raiden/
```

Delete desired **.toml** file/files.
{% endtab %}
{% endtabs %}

**Disclaimer:** Please note, that even though we do our best to ensure the quality and accuracy of the information provided, this publication may contain views and opinions, errors and omissions for which the content creator\(s\) and any represented organization cannot be held liable. The wording and concepts regarding financial terminology \(e.g. "payments", "checks", "currency", "transfer" \[of value\]\) are exclusively used in an exemplary way to describe technological principles and do not necessarily conform to the real world or legal equivalents of theses terms and concepts.

