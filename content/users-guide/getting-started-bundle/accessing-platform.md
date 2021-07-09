---
weight: 20
title: Accessing and logging into the platform
layout: redirect
aliases:
  - /users-guide/overview/#accessing-cumulocity-platform
  - /users-guide/getting-started/#accessing-cumulocity-platform
---

You access the {{< product-name-1 >}} platform via a web browser.

### Supported browsers

Supported browsers in this version are:

* Microsoft Edge (latest Chromium-based version)
* Mozilla Firefox (latest Extended Support Release [1])
* Google Chrome [2]
* Internet Explorer 11 [3]

[1] Only the Extended Support Releases of Mozilla Firefox are explicitly supported. Due to frequent upgrades of the Mozilla Firefox consumer release, the compatibility of {{< product-name-1 >}} with future versions of Mozilla Firefox cannot be fully guaranteed. Possible incompatibilities will be removed during the regular maintenance process of {{< product-name-1 >}}.

[2] The Google Chrome support is based on Google Chrome Version 84. Due to frequent version upgrades of Google Chrome, compatibility of {{< product-name-1 >}} with future versions of Google Chrome cannot be fully guaranteed. Possible incompatibilities will be removed during the regular maintenance process of {{< product-name-1 >}}.

>**Important:** [3] Though {{< product-name-1 >}} is functional on Internet Explorer 11, it does not allow us to provide you with a state-of-the-art user experience. As a result, {{< product-name-1 >}} 10.7 will be the last release that supports this browser. With upcoming releases we will continue to support the latest version of the Microsoft Edge browser as the successor to the Internet Explorer.

You may also use recent smartphone and tablet web browsers. We have tested our products with the following mobile web browsers:

* Chrome on Android (latest version) on Galaxy smartphones and tablets
* Safari on iOS (latest version) on Apple iPhone and iPad

>**Info:** {{< product-name-1 >}} on mobile devices shows some limitations:
>
* The usage may be constrained by the memory and the processing power available on the devices. For example, loading graphs with large amounts of data points may make the mobile device unresponsive.
* Using the private mode on browsers may not work.
* The [Streaming Analytics application](/apama/overview-analytics/) does not support mobile/touch devices.

### URL

To access the applications for your {{< product-name-1 >}} tenant, use the following URL:

```http
https://<tenant-domain>.{{< URL >}}/
```

This will direct you to the login page of your default application. See [Tenants](https://{{< URL >}}/api/#tag/Tenants) in the {{< OpenAPI >}} for further details on tenant ID and tenant domain.

>**Info:** The above URL is only valid for {{< product-name-1 >}} {{< tenant-type-1 >}} subscribers. For {{< tenant-type-2 >}} deployments of {{< product-name-1 >}}, the URL is specific to your organization.

> **Important:** Make sure that the address bar of your browser shows a lock icon. The lock icon indicates that you are using a secure connection and that you are indeed connected to the {{< product-name-1 >}} platform.

<a name="login"></a>
### To log into the {{< product-name-1 >}} platform

On the Login screen, enter your username (case-sensitive) and password.

If you use one of the public cloud instances of the {{< product-name-1 >}} platform and log in for the first time, you will see a cookie banner at the bottom:

<img src="/images/users-guide/getting-started/getting-started-cookie-banner.png" alt="Login prompt">
<br>

> **Info:** The cookie banner is turned on by default on the {{< product-name-1 >}} public cloud instances. For on-premise instances, this feature can be configured, see [{{< tenant-type-2 >}} > Customizing your platform > Branding](/users-guide/administration/#branding).

* Click **Agree and Proceed** to accept the default cookie settings (required and functional cookies enabled).
* Click **Privacy policy** to open the [{{< company-name-2 >}} privacy statement]({{< privacy-statement-link >}}) with details on the {{< company-name-2 >}} privacy policy.
* Click **Preferences** to select your individual cookie preferences:
	* **Required** - Required to enable core site functionality. They perform a task or operation without which a site's functionality would not be possible. Required cookies cannot be disabled.
	* **Functional** - Used to track site usage and to process personal data to measure and improve usability and performance. Functional cookies must be actively enabled by the user.
<br>
    <img src="/images/users-guide/getting-started/getting-started-cookie-selection.png" alt="Login prompt">
<br>

Select the **Remember me** checkbox if you want the browser to remember your credentials, so that you do not have to enter them again when opening the application the next time. This is especially convenient if you frequently switch between {{< product-name-1 >}} applications, as the {{< product-name-1 >}} platform will request you to authenticate each time when starting an application. You can make the browser "forget" your credentials by explicitly logging out.

Finally, click **Login** to enter the {{< product-name-1 >}} platform. Initially, you will be taken to the [Cockpit](/users-guide/cockpit) application (if not configured differently).

![image alt text](/images/users-guide/cockpit/cockpit-home-screen.png)

To explicitly logout, click the **User** button at the right of the the top bar and from the context menu select **Logout**.

<img src="/images/users-guide/getting-started/getting-started-logout.png" alt="Logout menu" style="max-width: 100%">

<a name="reset-password"></a>
### To reset your password

1. Click the **Forgot password?** link on the Login screen.
2. In the resulting dialog box, enter your email address and click **Reset password**.
3. Check your email account for an email from the {{< product-name-1 >}} platform support providing a password reset link.
4. Click the link in the email and provide your new password.

> **Info:** The password reset link is only valid for one day.

>**Info:** The automated password reset will only work if your email address is stored with your {{< product-name-1 >}} user. If you get a warning that the password cannot be reset, you are either using a different email address than the one stored with your {{< product-name-1 >}} user, or your {{< product-name-1 >}} user has no email address stored. In either case, contact a {{< product-name-1 >}} administrator in your organization. Administrators can reset your password.
>
If you yourself are the primary administrator, your email address used on first registering is automatically stored with your user. If you have questions, please contact [product support](/welcome/contacting-support/).

<a name="URLs"></a>
### Accessing pages using URLs

You can navigate straight to any place inside a {{< product-name-1 >}} application using the respective URL. For example, to show the basic information for a device, you can enter the following URL:

```http
https://<tenant-domain>.{{< URL >}}/apps/devicemanagement/index.html#/device/<id>/info
```

Using such an URL, you can:

*   Save bookmarks for specific devices or pages.
*   Send emails (manually or automatically, using the real-time event engine) which include a link to devices or sensor data.
*   Use the backward and forward navigation of your browser.
*   Write own web applications which link directly to information contained in a {{< product-name-1 >}} application.
chromium-based