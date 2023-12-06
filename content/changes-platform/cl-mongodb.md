---
title: MongoDB
layout: change_log
section:
  - change_log
weight: 40
---

### December 2023

#### -Change-  New sorting of Inventory API queries

If users do a search from the UI or via the Inventory API, the text parameters are now sorted by relevance making it easier to see the more appropriate data returned. [MTM-54563]

#### -Change-  New text index

A new text index has been introduced for the GET <code>/inventory/managedObjects</code> endpoint. By default it only includes the following fields:

<code>_id</code>, <code>type</code>, <code>name</code>, <code>owner</code>, <code>externalIds</code> [MTM-54562]

#### -Change- Version upgrades

- A MongoDB Java driver has been upgraded to the latest version 4.10.2. [MTM-53824]
- The MongoDB version has been upgraded to 5.0.18-1 in offline installation dependencies. [MTM-53200]