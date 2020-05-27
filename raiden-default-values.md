---
description: Raiden starts with some default settings
---

# Raiden Services Default Settings

## Routing via a paid Pathfinding Service is the default

Per default Raiden starts with PFS routing enabled.

```text
--rounting-mode PFS
```

That means for every **mediated transfer** your Raiden Client will request a route from a Pathfinding Service, **chosen automatically** from the registered services. The **maximum amount** that is paid by the client is set to **0.05 RDN** and **3 different paths** are requested. 

```text
--pathfinding-service-address auto --pathfinding-max-fee 50000000000000000 --pathfinding-max-paths 3
```

## Monitoring Services are disabled per default the Raiden Client

Monitoring of a channel is disabled per default. If enabled, the default reward for a Monitoring service successfully monitoring your channel is set to 5 RDN.

```text
--enable-monitoring FALSE
```

## 

