---
description: The Raiden Wizard makes setting up a Raiden node as easy as 1-2-3.
---

# Quick Start

## Get Started

This guide will teach you how to:

* [Download the Raiden Wizard](./#download-the-raiden-wizard)
* [Setup and run Raiden](./#setup-and-run-raiden)
* [Relaunch Raiden](./#relaunch-raiden)
* [Get a Infura Project ID](./#get-a-infura-project-id)
* [Handle limitations and shortcomings](./#handle-limitations-and-shortcomings)

### Download the Raiden Wizard

Download the Raiden Wizard for either macOS or Linux.

[**macOS download**](https://github.com/raiden-network/raiden-installer/releases/download/v0.100.5-dev0/raiden_wizard.macOS.zip)\*\*\*\*

[**Linux download**](https://github.com/raiden-network/raiden-installer/releases/download/v0.100.5-dev0/raiden_wizard.linux-gnu.zip)\*\*\*\*

### **Setup and Run Raiden**

1. Extract and open the **Raiden Wizard** file. The Wizard will launch in your default browser.
2. Insert your Infura Project ID. Don't have a Infura Project ID? Learn how to get one in the [section below](./#get-a-infura-project-id).
3. Click **"Create New Configuration"** to configure, install and launch the latest Raiden.

{% hint style="warning" %}
The setup process can take up to five minutes, make sure not to close the browser.
{% endhint %}

**Congratulations! You're now ready to start interacting with Raiden!** 🎉

![The Raiden Wizard setup process](.gitbook/assets/raiden_wizard_installation_process.gif)

To get an overview of the web interface:

[Watch this video on the web interface](https://www.youtube.com/watch?v=ASWeFdHDK-E)

[Read this tutorial about the web interface](https://raiden-network.readthedocs.io/en/stable/webui_tutorial.html)

[Read the developer API guide](https://raiden-network.readthedocs.io/en/stable/rest_api.html)

### Relaunch Raiden

Open the **Raiden Wizard** file, you will find two ways of relaunching Raiden.

1. Click the **"Launch"** button next to a configuration you already created.
2. Repeat the steps from [Setup and Run Raiden](./#setup-and-run-raiden) to create a new configuration.

{% hint style="warning" %}
Each new configuration created will be added to the list and currently you can't delete configurations from the Wizard. Read more under [Handle Limitations and Shortcomings](./#handle-limitations-and-shortcomings).
{% endhint %}

### Get a Infura Project ID

1. Visit [infura.io](https://infura.io/) and sign up for a new account.
2. Create a new project.
3. View your project and you'll find the Project ID under the **KEYS** tab.

![Steps to get a Infura Project ID](.gitbook/assets/infura_project_id_setup.gif)

{% hint style="info" %}
**What is Infura and why do I need a Project ID?**

By using Infura you don't have to worry about syncing the blockchain on your own system. You can simply access all test networks and the Ethereum mainnet through the API endpoints provided by Infura.

The Raiden Wizard sets up a Raiden node on top of Infura and your Project ID works as a way to authenticate your access to Infura.
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

