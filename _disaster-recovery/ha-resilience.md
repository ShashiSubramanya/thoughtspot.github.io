---
title: [High Availability (HA) and resilience]
last_updated: 08/18/2020
summary: "Consider these guidelines to ensure HA of ThoughtSpot app, and node resilience."
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---
## Requirements for node resilience

- The cluster must have at least 3 nodes.
- The cluster must have spare capacity; if one node fails, the remaining nodes must be able to host and serve all loaded data.


## What happens during node failure

- When a node loses connection with the main service manager process, it becomes **unhealthy**.
- ThoughtSpot migrates all migratable services that run on the failed node to other (**healthy**) nodes. For all practical purposes, ThoughtSpot ignores the failed node until it reports itself as **healthy**.
- ThoughtSpot rebalances and redistributes the data served from the failed node onto healthy nodes. Healthy nodes read the data from the the HDFS storage layer into the in-memory database processes.

## Disruption: impact on users

The process of redistributing and loading the data in the affected tables on HDFS layer from a failed node to the remaining healthy nodes is not instantaneous. The failover may impact the user experience.