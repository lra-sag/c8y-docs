---
title: Implementation
weight: 20
layout: bundle
---

This section describes how to implement a device agent at a gateway.

![Image 1](/images/cra/cra-api-image1.png)

The device agent is responsible for creating the device part of the tunnel between an unencrypted TCP/IP connection at private network and the secure device WebSocket endpoint.

### Supported operation {#supported-operation}

To indicate that your device is capable of handling Cloud Remote Access, it should report `c8y_RemoteAccessConnect` as supported operation in its managed object:

```json
	"c8y_SupportedOperations": [
		...
		"c8y_RemoteAccessConnect",
		...
	]
```

### Connect operation {#connect-operation}

This operation is created when the application generates a connect request. The operation is then sent to the device agent to establish the connection between the WebSocket endpoint at the server and the local network endpoint.

Example of an `c8y_RemoteAccessConnect` operation:

```json
	{
		"deviceId" : "10200",
		"c8y_RemoteAccessConnect": {
			"hostname": "10.0.0.67",
			"port": 5900,
			"connectionKey": "eb5e9d13-1caa-486b-bdda-130ca0d87df8"
		},
		"description": "Connect to remote access server"
	}
```

|Field|Data type|Details|
|:---|:---|:---|
|connectionKey|String|Shared secret to authenticate the connection request from device side. |
|hostname|Number|Endpoint on the local network to connect to.|
|port|String|Port to be used on local network endpoint.|

### Connecting to a new endpoint {#connecting-to-a-new-endpoint}

For each `c8y_RemoteAccessConnect` operation received the device agent connects to the provided hostname and port using TCP. Using the provided ConnectionKey the agent also securely connects to the WebSocket endpoint on server side. If all these operations succeeded the device reports the operation as SUCCESSFUL and starts forwarding binary packets between the TCP connection and the WebSocket in both directions.

![Image 2](/images/cra/cra-api-image2.png)

The following events are triggered when the device agent receives a `c8y_RemoteAccessConnect` operation.

* The operation status is set to EXECUTING.
* The connectionKey is used to connect to the {{< product-c8y-iot >}} Cloud Remote Access WebSocket. All data received from the WebSocket should be forwarded to the TCP connection (if already established): *wss://<hostname>/service/remoteaccess/device/<connectionKey>*
* The hostname and port is used to connect TCP in a local area network. Hostname and port are configured on server side and are used to connect to the endpoint of the device. Depending on the protocol (VNC, Telnet, SSH) the device will initiate a protocol-specific handshake. All data should be forwarded directly to the WebSocket endpoint (if already established).
* The operation status is set to SUCCESSFUL or FAILED based on the status of the previous steps.

### Operating a connected endpoint {#operating-a-connected-endpoint}

When both connections are established and fully functional the agent simply needs to forward all binary packets between the TCP connection and the WebSocket in both directions.

### Disconnecting an endpoint {#disconnecting-an-endpoint}

Whenever one of the connections is terminated (WebSocket or TCP) the device agent should consider the session as ended and should also terminate both connections associated with the tunnel.

### Recommendations {#recommendations}

It is highly recommended to implement a small buffer especially for bootstrapping when one connection is already functional while the other is not setup yet.
