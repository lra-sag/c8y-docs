---
weight: 20
title: IMPACT Integration
layout: redirect
---

Cumulocity IoT offers an integration with the Nokia IMPACT Data Collector which is designed to collect data from heterogeneous devices. Integrating Cumulocity IOT with IMPACT, enables you to make use of existing Cumulocity IoT features like connectivity monitoring, data visualization or real-time analytics with IMPACT devices.

>**Info:** Currently only the integration of LWM2M devices has been tested.

The IMPACT agent in Cumulocity IoT registers itself at the Nokia IMPACT platform. Similarly, it subscribes to events such as devices coming online or reporting data at IMPACT.

The following illustration provides an overview on the Cumulocity IoT IMPACT integration.

<img src="/images/device-protocols/impact/impact-integration.png" alt="IMPACT integration" style="max-width: 100%">

>**Info:** Your subscription needs to include the IMPACT feature. If you do not see the functionality described in this document, please contact [product support](/welcome/contacting-support/).
>
>To be able to communicate with a device through IMPACT the device must be registered in IMPACT. How to register a device in IMPACT is not in the scope of this document.