---
weight: 150
title: S
layout: bundle
section:
  - getting_started
---


### Sensor library {#sensor-library}

{{< product-c8y-iot >}} includes a sensor library to model specific sensing and controlling skills across device products. A single device can have many sensor and control characteristics. The sensor library covers basic sensors and controls, and is supported by the {{< product-c8y-iot >}} client libraries. It also enables writing powerful generic IoT software plugins.
Technically, the sensor library defines standard fragments for inventory, measurements, events and device control, following the naming convention.

For details see [Getting started > Technical concepts > {{< product-c8y-iot >}}'s domain model > Sensor library](/concepts/domain-model/#sensor-library) and [Getting started > Technical concepts > {{< product-c8y-iot >}}'s domain model > Inventory](/concepts/domain-model/#inventory).


### Smart rules {#smart-rules}

{{< product-c8y-iot >}} includes a rule engine to analyze data in realtime and to perform actions based on data. To easily create rules, the Cockpit application includes a “smart rules” builder which allows you to create rules from templates (so-called smart rule templates).

For details see [Application enablement & solutions > Cockpit > Smart rules](/cockpit/smart-rules).


### Standard tenant {#standard-tenant}

A tenant type in the [{{< product-c8y-iot >}} tenant hierarchy](/glossary/t/#tenant-hierarchy).

At the bottom of the tenant hierarchy you can find single tenants which are represented by the concept of {{< standard-tenant >}}.
A {{< standard-tenant >}} offers most of the device management and monitoring functionality of the {{< product-c8y-iot >}} platform, but has certain limitations when it comes to administrative aspects.

See also [{{< enterprise-tenant >}}](/glossary/e/#enterprise-tenant) and [{{< management-tenant >}}](/glossary/m/#management-tenant).


### Subscription {#subscription}

The application concept of {{< product-c8y-iot >}} includes a basic application marketplace.
Tenants can be subscribed to applications which have been deployed by their superior tenant ({{< management-tenant >}} or {{< enterprise-tenant >}}).
Granting access to subtenants and subscribing to applications is done in the Administration application.

For details see [Getting started > Technical concepts > Developing applications > Application subscription](/concepts/applications/#application-subscription) and [Platform administration > {{< standard-tenant >}} administration > Managing the ecosystem > Managing applications](/standard-tenant/ecosystem/#managing-applications).
