---
title: Application options
layout: redirect
weight: 10
---

Each UI application can be customized with a set of defined options.
The options objects are defined in JSON and read and merged at runtime with the following order:

  - Static options defined at build time
  - Dynamic fetched options on application boot
  - URL options that can be added by the user as URL query params (mostly for debugging purposes)

This process of collecting and merging the different options is executed by a thin bootstrap layer included in `@c8y/cli`.

Although all of the options can be defined on any of the 3 levels some might not make sense at runtime, as they just influence the build process, or require a complex object making it particularly tricky to  write as a URL query parameter.

### Static options {#static-options}

Defined in the `package.json` of the application inside the fragment `c8y.application`:

```json
{
  "c8y": {
    "application": {
      "name": "cockpit",
      "contextPath": "cockpit",
      "key": "cockpit-application-key",
      "tabsHorizontal": true,
      "upgrade": true,
      "rightDrawer": true,
      "contentSecurityPolicy": "default-src 'self' 'unsafe-inline' http: https: ws: wss:; script-src 'self' *.mapquestapi.com 'unsafe-inline' 'unsafe-eval' data:; style-src * 'unsafe-inline' blob:; img-src * data:; font-src * data:; frame-src *;"
    }
  }
}
```

Can also be passed to `c8ycli`:

```sh
c8ycli build --app.contextPath=cockpit2 --app.dynamicOptionsUrl="/apps/public/public-options/options.json"
```

{{< c8y-admon-important >}}
The `key` property must match the application key specified for the application during creation, otherwise the user will not be able to authenticate using the web application.
{{< /c8y-admon-important >}}

### Dynamic fetched options {#dynamic-fetched-options}

Using the static options `dynamicOptionsUrl` the application will try to load a json from the specified URL at boot time. In the platform's built-in applications this option is set to `/apps/public/public-options/options.json` as that mechanism to provide instance level and {{< enterprise-tenant >}} customization.
As this property is defined statically at build time, it is possible for the application developer to decide if and where from their applications should load the dynamic fetched options at runtime.

A common use case, for example, is to disable the contextual help on each page, since it is only available in English. To do so you must upload an application on the context-path `public-options` and add an *options.json* to it with the following content:

```json
{
  "contextHelp": false
}
``` 

{{< c8y-admon-tip >}}
The `public-options` application is automatically created if you have a branding assigned via the UI-based branding editor. You can then simply download the ZIP file, align the JSON accordingly and upload it again.
{{< /c8y-admon-tip >}}

With this approach all runtime options of the application can be changed even if they are not listed in the UI-based branding editor. The full list of options can be found [here](http://resources.cumulocity.com/documentation/websdk/ngx-components/classes/ApplicationOptions.html).


### URL options {#url-options}

These can just be appended to the URL of the application as query parameters.

```sh
https://<instance domain>/apps/cockpit?dynamicOptionsUrl=/apps/my-options/options.json&rightDrawer=false
```

### Built-in Options {#built-in-options}

Refer to the [ApplicationOptions](http://resources.cumulocity.com/documentation/websdk/ngx-components/classes/ApplicationOptions.html) documentation for a list of the standard supported options.
These options can easily be extended with any custom property a developer might want to include in their application or extensions just by adding it in the static, dynamic or URL way as described above.

{{< c8y-admon-tip >}}
`contentSecurityPolicy` for the current application can be checked in the following places:
- When you do `c8ycli new my-cockpit cockpit -a @c8y/apps@1004.11.0` you can find the value of `contentSecurityPolicy` in package.json under the path: `c8y.application.contentSecurityPolicy` if it has been defined.
- When you inspect the page, you can look for `<meta http-equiv="Content-Security-Policy" content="...">` in the `<head>` tag. The active value is enclosed in the `content` attribute.
{{< /c8y-admon-tip >}}

<br>

{{< c8y-admon-info >}}
If you build a custom application based on the standard application, make sure you append your CSP value to the default one.
{{< /c8y-admon-info >}}
