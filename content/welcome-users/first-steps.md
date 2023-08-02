---
weight: 30
title: First steps with Cumulocity IoT
layout: bundle
section:
  - getting_started
---

This section of the {{< product-c8y-iot >}} documentation highlights the basic steps to take if you are new to the platform.

If you are technically interested in our IoT platform, you might want to learn about the architecture, technical concepts and domain models behind {{< product-c8y-iot >}} found in the <a href="/concepts/introduction/">Concepts guide</a>.


### Step 1: Logging into {{< product-c8y-iot >}} for the first time

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


Click **Login** to enter the {{< product-c8y-iot >}} platform. Initially, you will be taken to the [Cockpit](/cockpit/overview/) application (if not configured differently). Read about the three standard applications {{< product-c8y-iot >}} comes with at: [Standard platform applications](/getting-started/platform-applications/).

![image alt text](/images/users-guide/cockpit/cockpit-home-screen.png)

You will see a predefined dashboard with a number of [widgets](/cockpit/using-widgets/#using-widgets) such as a welcome message, a [map](/cockpit/widgets-collection/#widget-map) that shows the location of registered devices, and [all critical alarms](/cockpit/widgets-collection/#all-alarms). To see the list of all preset widget types head to [Widgets collection](/cockpit/widgets-collection/).

### Step 2: Learn about {{< product-c8y-iot >}}'s basic UI functionalities and features

#### Main screen elements

All {{< product-c8y-iot >}} applications share a common structure and includes the following screen elements:

![{{< product-c8y-iot >}} application](/images/users-guide/getting-started/getting-started-screen-elements.png)

<table>
<col width="15%">
<col width="85%">
<thead>
<tr>
<th style="text-align:left">Element</th>
<th style="text-align:left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left"><b>Navigator</b></td>
<td style="text-align:left">On the left you find the navigator. At the top of the navigator the name and logo of the application is displayed, indicating which application you are currently using. Below you find a list of entries leading to the various pages of the application. The entries are grouped into menus and menu items. You can collapse or expand menus in the navigator by clicking the menu name. Clicking the small arrow at the very left of the top bar will hide/or unhide the navigator. Per default, it is visible.</td>
</tr>
<tr>
<td style="text-align:left"><b>Page</b></td>
<td style="text-align:left">"Page" actually refer to the main area in the application. The content provided here depends on the menu item selected in the dashboard. The structuring of the content differs from page to page. Data can for example be displayed in a list with a row for each object or you can find it being presented in a grid in which objects are represented by cards. </td>
</tr>
<tr>
<td style="text-align:left"><b>Tabs</b></td>
<td style="text-align:left">Some pages, for example the page of any particular device, are divided into several tabs, either displayed vertically or horizontally.</td>
</tr>
<tr>
<td style="text-align:left"><b>Top bar</b></td>
<td style="text-align:left"><b>Page title</b><br> At the left of the top bar the title of the active page is displayed, if any. <br> <br><img src="/images/icons/search-icon.png" alt="Search" style="max-width:100%"> <b>Search button</b><br> Clicking the <b>Search</b> button opens a search field to enter text for a full-text search. For details, see <a href="/getting-started/gui-features/#searching" class="no-ajaxy">Searching</a> for more. Not always available. <br><br><img src="/images/icons/switcher-icon.png" alt="User" style="max-width:100%"> <b>Application Switcher button</b><br> Clicking the <b>Application Switcher</b> button opens the <a href="/getting-started/gui-features/#app-switcher" class="no-ajaxy">application switcher</a> which allows you to quickly switch between applications. <br><br> <img src="/images/icons/user-icon.png" alt="User" style="max-width:100%"> <b>User button</b><br> Right from the Application Switcher button you will find the <b>User</b> button with your username. Clicking it will open up a context menu with commands related to your account settings. More on <a href="#user-options" class="no-ajaxy">user settings and options</a> below. <br> <br>Other buttons/ information may be available in the top bar depending on the application and the page being displayed. </td>
</tr>
<tr>
<td style="text-align:left"><b>Top menu bar</b></td>
<td style="text-align:left">Depending on the active application and the active page, a secondary bar is displayed below the top bar providing further functionalities like a <b>Reload</b> link for reloading the page or a <b>Realtime</b> link for the display of realtime data. </td>
</tr>
<tr>
<td style="text-align:left"><b>Right drawer</b></td>
<td style="text-align:left">Clicking the user icon at the very right of the top bar will unhide/hide the right drawer, offering access to the user settings, quick links to other applications and to relevant documentation. Per default, the right drawer is hidden.</td>
</tr>
</tbody>
</table>

{{< c8y-admon-info >}}
See the [UI functionalities and features](/getting-started/gui-features/) section of our documentation for more information on {{< product-c8y-iot >}}'s UI features.
{{< /c8y-admon-info >}}

<a name="user-options"></a>
#### User options and settings

Clicking the **User button** at the top right will open a menu which provides access to the following actions or information:

<img src="/images/users-guide/getting-started/getting-started-user-account-menu.png" alt="User account menu"  style="max-width: 60%">

The **User** menu contains the following items:

<table>
<colgroup>
<col width = "20%">
<col width = "80%">
</colgroup>
<thead>
<tr>
<th style="text-align:left">Menu item</th>
<th style="text-align:left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left">User settings</td>
<td style="text-align:left">Provides access to the user settings, here you can <a href="/getting-started/user-settings/#change-user-settings" class="no-ajaxy">change user settings</a> such as the <a href="/getting-started/user-settings/#languages" class="no-ajaxy">language</a> of the UI and <a href="/getting-started/user-settings/#change-password" class="no-ajaxy">changing your password</a>. </td>
</tr>
<tr>
<td style="text-align:left">Access denied requests</td>
<td style="text-align:left">Shows a list of data requests which could not be accessed due to missing permissions, if any. </td>
</tr>
<tr>
<td style="text-align:left">Logout</td>
<td style="text-align:left">Logs you out from your {{< product-c8y-iot >}} account. </td>
</tr>
<tr>
<td style="text-align:left">Request support</td>
<td style="text-align:left">Redirects you to the <a href="{{< link-sag-portal >}}" class="no-ajaxy">{{< company-sag >}} {{< sag-portal >}}</a>. </td>
</tr>
<tr>
<td style="text-align:left">Activate support</td>
<td style="text-align:left">Allows support users to access your account.<br>
<br>
Note that this option is only available if support user access is not set globally for subtenant users in the {{< management-tenant >}}, for details see <a href="/users-guide/enterprise-tenant/#support-user-access" class="no-ajaxy">Support user access</a>. After the support user access has been activated, the menu item switches to <strong>Deactivate support</strong>. If your support request has been resolved but the duration for the support user access is not expired (24 hours per default) you can actively disable an active support user request here.</td>
</tr>
<tr>
<td style="text-align:left">Revoke tokens</td>
<td style="text-align:left">Revoking tokens logs out all users currently logged in via "OAI-Secure" or "Single sign-on redirect". Note that JWT tokens retrieved by your devices will also be revoked.<br>
<br>
To revoke tokens, you must have ADMIN permission for the permission type "User management".  
</td>
</tr>
<tr>
<td style="text-align:left">Version information</td>
<td style="text-align:left">Shows release information on the {{< product-c8y-iot >}} version you are using (for example, 10.13.0.034) for both Backend and UI. Moreover shows the ID of your tenant, which might be required if you request support. Click the copy icon next to the tenant ID to copy it to the clipboard.</td>
</tr>
</tbody>
</table>

### Step 3: Registering a device

To integrate a device to {{< product-c8y-iot >}}, you need to register it by clicking **Registration** in the **Devices** menu of the navigator in the **Device management application**.

{{< c8y-admon-info >}}
* To manually connect one device or several devices one by one follow the instructions at [single device registration](/device-management-application/registering-devices/#single-device-registration).

* To connect larger amounts of devices in one step follow the instructions at [bulk device registration](/device-management-application/registering-devices/#bulk-device-registration).
{{< /c8y-admon-info >}}

For more information on how to register a device go to [Device management application > Registering devices](/device-management-application/registering-devices/).

#### Connecting a smartphone with the {{< product-c8y-iot >}} Sensor App

Register and connect your smartphone to {{< product-c8y-iot >}} using the {{< product-c8y-iot >}} Sensor App. The {{< product-c8y-iot >}} Sensor App is a free smartphone application available for iOS and Android smartphones.

The app is designed to collect measurements from your smartphone, nearby Bluetooth device sensors, and vehicle On-board Debug (OBD) sensors, and send them to the {{< product-c8y-iot >}} platform. The {{< product-c8y-iot >}} Sensor App can also send commands to the smartphone directly from the phone dashboard.

Go to [Getting started > Sensor App](/sensor-app/overview/) to see which smartphone sensors and Bluetooth devices are currently supported as well as [how to install](/sensor-app/installation/) and [how to register the Sensor App in the platform](/sensor-app/register/).

#### Device integration via thin.edge.io on a Raspberry Pi

thin-edge.io is an open-source project to provide a cloud-agnostic edge framework. It is much more generic than the device management agent, so it can connect to multiple IoT cloud platforms, and it allows flexible logic being executed on the device. It is optimized for a very small footprint and high performance.

The Raspberry Pi is a relatively simple and cheap yet powerful device. This makes it ideal for testing and trying out as well as some production use cases.

For an overview of the installation and configuration of thin-edge.io with Raspberry Pi go to [Device integration > Integration tutorials > thing-edge.io on a Raspberry Pi](/device-integration/integration-tutorials/#prerequisites).

### Step 4: Working with dashboards

The predefined dashboard can be edited and designed individually according to your needs. You can add, remove or change widgets being displayed here. Go to [Widgets collection](/cockpit/widgets-collection/) to see a list of all preset widgets.

{{< c8y-admon-info >}}
You can also develop your own widgets and add them to your {{< product-c8y-iot >}} account. For more information go to [Developing applications > Tutorials > Add a custom widget to a dashboard](/web/tutorials/#add-a-custom-widget).
{{< /c8y-admon-info >}}

#### Creating a dashboard

### Step 5:
