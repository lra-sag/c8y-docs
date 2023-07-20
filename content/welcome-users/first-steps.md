---
weight: 30
title: First steps with Cumulocity IoT
layout: bundle
section:
  - getting_started
---

This section of the {{< product-c8y-iot >}} documentation highlights the basic steps to take if you are new to the platform.

If you are technically interested in our IoT platform, you might want to learn about the architecture, technical concepts and domain models behind {{< product-c8y-iot >}} found in the <a href="/concepts/introduction/">Concepts guide</a>.


### Step 1: Accessing and logging into {{< product-c8y-iot >}} for the first time

To login into the {{< product-c8y-iot >}} platform and have access to your tenant, use the following URL:

```http
https://<tenant-domain>.{{< domain-c8y >}}/
```
This will direct you to the login page of your default application. See [Tenants](https://{{< domain-c8y >}}/api/core/{{< c8y-current-version >}}/#tag/Tenants) in the {{< openapi >}} for further details on tenant ID and tenant domain.

On the Login page, enter your username and password. The maximum number of failed logins (due to invalid credentials), after which a user is locked, can be configured by the {{< management-tenant >}} on platform level. The default value is 100.



{{< c8y-admon-info >}}
Find more information on how to access and log into the platform including how to reset your password in the following links:

* [Accessing and logging into the platform](/getting-started/accessing-platform/)
* [To reset your password](/getting-started/accessing-platform/#to-reset-your-password)
{{< /c8y-admon-info >}}


Click **Login** to enter the {{< product-c8y-iot >}} platform. Initially, you will be taken to the [Cockpit](/cockpit/overview/) application (if not configured differently).

Read about the three standard applications {{< product-c8y-iot >}} comes with at: [Standard platform applications](/getting-started/platform-applications/).

### Step 2: Learn about {{< product-c8y-iot >}}'s UI functionalities and features

All {{< product-c8y-iot >}} applications share a common structure. The **Navigator** on the left side of the page

### Step 3: Cockpit

### Step 4: Platform administration

### Step 5: Device Management
