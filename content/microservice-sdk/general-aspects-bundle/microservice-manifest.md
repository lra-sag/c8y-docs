---
weight: 30
title: Microservice manifest
layout: redirect
---

The application manifest provides the required settings to manage microservice instances and the application deployment in the {{< product-c8y-iot >}} platform.
The definition is provided within the _cumulocity.json_ file in the binary uploaded to the {{< product-c8y-iot >}} platform.

Here is an example manifest:

```json
{
    "apiVersion": "v2",
    "name": "my-microservice",
    "version": "1.0.0",
    "provider": {
        "name": "New Company Ltd.",
        "domain": "https://new-company.com",
        "support": "support@new-company.com"
    },
    "isolation": "MULTI_TENANT",
    "scale": "AUTO",
    "replicas": 2,
    "resources": {
        "cpu": "1",
        "memory": "1G"
    },
    "requestedResources":{
            "cpu": "100m",
            "memory": "128Mi"
    },
    "requiredRoles": [
        "ROLE_ALARM_READ"
    ],
    "livenessProbe": {
        "httpGet": {
            "path": "/health"
        },
        "initialDelaySeconds": 60,
        "periodSeconds": 10
    },
    "readinessProbe": {
        "httpGet": {
            "path": "/health",
            "port": 80

        },
        "initialDelaySeconds": 20,
        "periodSeconds": 10
    },
    "settingsCategory": "my-ms",
    "settings": [
        {
            "key": "tracker-id",
            "defaultValue": "1234"
        }
    ]
}
```

See below for detailed information about available settings.

### Settings {#settings}

<table>
<colgroup>
  <col width="20%">
  <col width="20%">
  <col width="70%">
  <col width="10%">
</colgroup>
<thead>
<tr>
<th style="text-align:left">Name</th>
<th style="text-align:left">Type</th>
<th style="text-align:left">Description</th>
<th style="text-align:left">Required</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left">apiVersion</td>
<td style="text-align:left">String</td>
<td style="text-align:left">Document type format discriminator. The accepted values are positive integer numbers proceeded by an optional "v", such as "v2" and "2". Values which do not conform to this convention are considered "v1".</td>
<td style="text-align:left">Yes</td>
</tr>
<tr>
<td style="text-align:left">name</td>
<td style="text-align:left">String</td>
<td style="text-align:left">Application name</td>
<td style="text-align:left">No</td>
</tr>
<tr>
<td style="text-align:left">contextPath</td>
<td style="text-align:left">String</td>
<td style="text-align:left">Microservice contextPath is used to define extension points. <br>Default: Microservice name </td>
<td style="text-align:left">No</td>
</tr>
<tr>
<td style="text-align:left">version</td>
<td style="text-align:left">String</td>
<td style="text-align:left">Application version. Must be a correct <a href="https://semver.org" target="_blank">SemVer</a> value but the "+" sign is disallowed.</td>
<td style="text-align:left">Yes</td>
</tr>
<tr>
<td style="text-align:left">provider</td>
<td style="text-align:left">Provider</td>
<td style="text-align:left">Application provider information. Simple name allowed for predefined providers, for example, c8y. Detailed object for external provider.</td>
<td style="text-align:left">Yes</td>
</tr>
<tr>
<tr>
<td style="text-align:left">billingMode</td>
<td style="text-align:left">Enum</td>
<td style="text-align:left">Values: RESOURCES, SUBSCRIPTION<br>Default: RESOURCES<br><br> In case of RESOURCES, the number of resources used is exposed for billing calculation per usage. In case of SUBSCRIPTION, all resources usage is counted for the microservice owner and the subtenant is charged for subscription.</td>
<td style="text-align:left">No</td>
</tr>
<tr>
<td style="text-align:left">isolation</td>
<td style="text-align:left">Enum</td>
<td style="text-align:left">Values: MULTI_TENANT, PER_TENANT<br>Default: MULTI_TENANT<br><br>Deployment isolation. In case of PER_TENANT, there is a separate instance for each tenant; otherwise, there is one single instance for all subscribed tenants. Should be overridable on subscription and should affect billing.</td>
<td style="text-align:left">No</td>
</tr>
<tr>
<td style="text-align:left">scale</td>
<td style="text-align:left">Enum</td>
<td style="text-align:left">Values: AUTO, NONE<br>Default: NONE <br><br>Enables scaling policy. See <a href="#isolation-scaling">Isolation and scaling</a> for more details.</td>
<td style="text-align:left">No</td>
</tr>
<tr>
<td style="text-align:left">replicas</td>
<td style="text-align:left">Integer</td>
<td style="text-align:left">Value range: 1 - 5<br><br>Defines the number of microservice instances. For auto-scaled microservices, the value represents the minimum number of microservices instances.</td>
<td style="text-align:left">No</td>
</tr>
<tr>
<td style="text-align:left">resources</td>
<td style="text-align:left">Resources</td>
<td style="text-align:left">Configuration for resources limits.<br>Default limits are CPU=0.5, Memory=512MB. Different default values may be configured by the system administrator.</td>
<td style="text-align:left">No</td>
</tr>
<tr>
<td style="text-align:left">requestedResources</td>
<td style="text-align:left">RequestedResources</td>
<td style="text-align:left">Intended configuration for minimal required resources.<br>The values may be over-written based on system settings.<br>Default values are CPU=0.25, Memory=256MB. Different default values may be configured by the system administrator.</td>
<td style="text-align:left">No</td>
</tr>
<tr>
<td style="text-align:left">settings</td>
<td style="text-align:left">Option[ ]</td>
<td style="text-align:left">Set of tenant options available to define the configuration of a microservice. <br>Default: [ ] (empty list)</td>
<td style="text-align:left">No</td>
</tr>
<tr>
<td style="text-align:left">settingsCategory</td>
<td style="text-align:left">String</td>
<td style="text-align:left">Allows to specify custom category for microservice settings. By default contextPath is used.</td>
<td style="text-align:left">No</td>
</tr>
<tr>
<td style="text-align:left">requiredRoles</td>
<td style="text-align:left">String[ ]</td>
<td style="text-align:left">List of permissions required by a microservice to work.</td>
<td style="text-align:left">No</td>
</tr>
<tr>
<td style="text-align:left">roles</td>
<td style="text-align:left">String[ ]</td>
<td style="text-align:left">Roles provided by the microservice. <br>Default: [ ] (empty list)</td>
<td style="text-align:left">No</td>
</tr>
<tr>
<td style="text-align:left">livenessProbe</td>
<td style="text-align:left">Probe</td>
<td style="text-align:left">Defines the strategy used to verify if a microservice is alive or requires a restart.</td>
<td style="text-align:left">No</td>
</tr>
<tr>
<td style="text-align:left">readinessProbe</td>
<td style="text-align:left">Probe</td>
<td style="text-align:left">Defines the strategy used to verify if a microservice is ready to accept traffic.</td>
<td style="text-align:left">No</td>
</tr>
<tr>
<td style="text-align:left">extensions</td>
<td style="text-align:left">Extension[ ]</td>
<td style="text-align:left">Defines a set of extensions that should be enabled for a microservice. <br>Default: [ ] (empty list)</td>
<td style="text-align:left">No</td>
</tr>
</tbody>
</table>


#### Version {#version}

The version has an impact on the microservice upload behavior:

*   If a new ZIP file for a microservice is uploaded but the version is the same as the previous, for example, "1.1.0", then there is no guarantee that the Docker image for the microservice will be updated.
*   If the version is a snapshot, for example, "1.1.0-SNAPSHOT", then Docker will update the image on each ZIP upload.

The snapshot postfix means that the image build is a snapshot of your application at a given time and it is still under development. When your microservice is ready for production release, you can remove the postfix and just use the final version of your application.

#### Provider {#provider}

|Name|Type|Description|Required|
|:---|:---|:----------|:----------|
|name|String |Company name of the provider|Yes
|domain|String |Website of the provider |No
|support|Email|Email of the support person|No

#### Resources {#resources}

|Name|Type|Description|Required|
|:---|:---|:----------|:----------|
|cpu|String |Limit for number of CPUs or CPU time <br>Default CPU: 0.5, min: 0.1 <br>Default CPU time: 500m, min: 100m <br>A different default value may be configured by the system administrator.| No
|memory|String |Limit for microservice memory usage <br>Default: 512M, Min: 10M<br/>Possible units are: E, P, T, G, M, K, Ei, Pi, Ti, Gi, Mi, Ki <br>A different default value may be configured by the system administrator.|No

#### RequestedResources {#requestedresources}

|Name|Type|Description|Required|
|:---|:---|:----------|:----------|
|cpu|String |Intended minimal requirements for number of CPUs or CPU time  <br>The value may be over-written based on system settings. <br>Default: 250m<br>A different default value may be configured by the system administrator.|No
|memory|String |Intended minimal requirements for microservice memory usage <br>The value may be over-written based on system settings. <br>Default: 256M <br/>Possible postfix values are: E, P, T, G, M, K, Ei, Pi, Ti, Gi, Mi, Ki<br>A different default value may be configured by the system administrator.|No

#### Option {#option}

|Name|Type|Description|Required|
|:---|:---|:----------|:----------|
|key|String |Key of the option|Yes
|defaultValue|String|Default value|Yes
|editable|Boolean|Defines if the option can be changed by a subscribed tenant on runtime <br>Default: false |No
|overwriteOnUpdate|Boolean|Defines if an editable option is reset upon microservice update <br>Default: true |No
|inheritFromOwner|Boolean|Specifies if an option should be inherited from the owner <br>Default: true |No
#### Probe {#probe}

|Name|Type|Description|Required|
|:---|:---|:----------|:----------|
|exec | ExecAction | Commands to be executed on a container to probe the service | No
|tcpSocket | TCPSocketAction | TCP socket connection attempt as a probe | No
|httpGet | HTTPGetAction | HTTP request to be executed as a probe | No
|initialDelaySeconds |Number| Tells the platform for how long it should wait before performing <br>the first probe <br/>Default: 200 | No
|periodSeconds|Number| Defines in which interval the probe should be executed<br/>Default: 10 | No
|successThreshold|Number| Minimum consecutive successes for the probe to be considered <br>successful after having failed<br/> Default: 1 | No
|timeoutSeconds|Number| Number of seconds after which the probe times out<br/> Default: 1 | No
|failureThreshold|Number| Number of failed probes after which an action should be taken <br/>Default: 3 | No

#### ExecAction {#execaction}

|Name|Type|Description|Required|
|:---|:---|:----------|:----------|
|command | String[ ] | Commands to be executed on a container to probe the service | Yes

#### TCPSocketAction {#tcpsocketaction}

|Name|Type|Description|Required|
|:---|:---|:----------|:----------|
|host | String | Host to verify | Yes
|port | Number | Port to verify <br/>Default:80 | Yes

#### HTTPGetAction {#httpgetaction}

|Name|Type|Description|Required|
|:---|:---|:----------|:----------|
|host | String | Host name to connect to | Yes
|path | String | Path to access on the HTTP server | Yes
|port | Number | Port to verify <br/>Default: 80 | No
|scheme | String | Scheme to use for connecting to the host (HTTP or HTTPS)<br/> Default: HTTP | No
|headers | HttpHeader | HTTP headers to be added to a request | No

#### HttpHeader {#httpheader}

|Name|Type|Description|Required|
|:---|:---|:----------|:----------|
|name | String | Header name | Yes
|value | String | Header value | Yes

#### Extension {#extension}

|Name|Type|Description|Required|
|:---|:---|:----------|:----------|
|type | String | Type ID of the extension | Yes
|* | any | Configuration parameters | No
