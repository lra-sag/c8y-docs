---
weight: 10
title: Overview
layout: bundle
slug: introduction
section:
  - device_management
---

{{< company-c8y >}} offers a wide range of functionality for interfacing IoT devices and other IoT-related data sources with the {{< product-c8y-iot >}} platform.

We recommend you to can integrate devices via [thin-edge.io](https://thin-edge.io/). See the tutorial for [thin-edge.io on a Raspberry Pi](/device-integration/integration-tutorials/#thin-edge-raspberry-pi) for an easy-to-follow and hands-on example.

You can also use [MQTT](/device-integration/mqtt) and [SmartREST](/smartrest/smartrest-two/) to integrate devices, which can be very efficiently implemented using available MQTT client libraries such as [Eclipse Paho](https://www.eclipse.org/paho/).

Refer to [Device integration using REST](/device-integration/rest) for detailed information on integrating via REST.

An up-to-date open source reference implementation of a {{< product-c8y-iot >}} agent for embedded Linux systems with many device management features can be found at [https://github.com/SoftwareAG/cumulocity-agents-linux](https://github.com/SoftwareAG/cumulocity-agents-linux). Note that the reference implementation currently uses SmartREST 1 with the choice to switch between HTTP and MQTT as transport protocol.

For information on the general concept of agents being used for interfacing IoT data sources with {{< product-c8y-iot >}}, refer to [Interfacing devices](/concepts/interfacing-devices/).
