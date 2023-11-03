---
weight: 10
title: Overview
layout: bundle
section:
  - edge_server
---

{{< product-c8y-iot >}} Edge is delivered as a software appliance designed to run on industrial PC's or local servers.

In contrast to {{< product-c8y-iot >}} platform, which is available in the cloud (for example, using AWS, Azure or other data centers), {{< product-c8y-iot >}} Edge is installed in factories, that is, in the same site ("onsite") in which the IoT assets are located.    

Reasons for using an onsite installation of {{< product-c8y-iot >}} Edge include:

* **Autonomy**: Even if there is no cloud connection, tasks like data collection and data analysis can still be performed.
* **Data reduction**: Data is analyzed and aggregated close to assets, and thus less data needs to be sent to the cloud.
* **Reactivity**: Both {{< product-c8y-iot >}} Edge and {{< product-c8y-iot >}} platform include real-time streaming analytics engines. However, placing the rule execution in {{< product-c8y-iot >}} Edge reduces latency, because the round-trip to cloud is omitted.

Features of {{< product-c8y-iot >}} Edge include:

* Edge Agent, which enables remote monitoring and management of an Edge instance from the {{< product-c8y-iot >}} tenant.
* Data Broker to send IoT data to the cloud and receive operations from the cloud, with web-based UI to filter data.
* Streaming Analytics engine for real-time local data analysis including the {{< product-c8y-iot >}} Analytics Builder.
* Ready-to-use Cockpit and Device Management applications.
* Native protocol support for MQTT and REST.
* Edge database for operational data storage.
* Cloud Fieldbus with web-based UI to create local Modbus and OPC UA connections.
* Easy installation, upgrades and backup/restore.
* Microservice hosting, which allows to run server-side applications which may be used to extend the {{< product-c8y-iot >}} platform with customer-specific functionality (optional component).
* [DataHub Edge](/datahub/running-datahub-on-the-edge/) for historical data storage and analytics (optional component).
* [Machine Learning](/machine-learning/introduction/) to train and deploy your machine learning models (optional component).


<img src="/images/edge/cumulocity-edge-overview.png" name="{{< product-c8y-iot >}} Edge overview" style="width:75%;"/>
