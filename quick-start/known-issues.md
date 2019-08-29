---
description: >-
  The Raiden Wizard is in an early stage of implementation. In this section you
  will learn how to handle known limitations and shortcomings.
---

# Known Issues

### Handling Internal Server Error

{% hint style="warning" %}
**Important**

The Raiden Wizard will display an _**Internal Server Error**_ ****if an invalid Project ID is provided. To solve this you have to [manually delete the configuration](../#delete-configuration-files) file that got created.
{% endhint %}

### Stop Raiden from Running

The Wizard does not provide a way of shutting down the Raiden node. You have to cancel the process to stop Raiden.

{% tabs %}
{% tab title="Mac" %}
Use the Activity Monitor app for stopping the Raiden process.
{% endtab %}

{% tab title="Linux" %}
Use any Linux process manager for stopping the Raiden process.
{% endtab %}
{% endtabs %}

### Delete Configuration Files

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
/home/<username>/.local/share/raiden/
```

Delete desired **.toml** file/files.
{% endtab %}
{% endtabs %}

