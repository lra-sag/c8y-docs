---
weight: 10
title: Introduction
layout: bundle
section:
  - edge_server
---

{{< product-c8y-iot >}} Edge uses REST and MQTT as protocols for external communication. Both protocols may be used to interface devices with {{< product-c8y-iot >}} Edge. For more information, see [Device integration using REST](/device-integration/rest) and [SmartREST 2.0](/smartrest/smartrest-two/).

Additionally, {{< product-c8y-iot >}} Edge offers:

* Cloud Fieldbus functionality to collect data from fieldbus devices and remotely manage them. For example, Modbus protocol.

* OPC UA protocol. OPC UA protocols support through the OPC UA device gateway and OPC UA management service.

For details on how to integrate devices using Modbus and OPC UA protocols, see [Connecting a Modbus device](/edge/connecting-devices-to-edge/#connecting-modbus-device) and [Connecting an OPC UA device](/edge/connecting-devices-to-edge/#connecting-opcua-device).

{{< c8y-admon-info >}}
Currently, only the Modbus and OPC UA protocols are supported.
{{< /c8y-admon-info >}}
