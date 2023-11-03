---
weight: 60
title: Configuring Apama
layout: bundle
section:
  - edge_server
---

### Updating the memory and CPU limit for Apama {#updating-the-memory-and-cpu-limit-for-apama}

The memory limit for Apama container is set to 2048 MB and the CPU limit is set to 256 as default values. For most use cases, these values are sufficient. You can change the values as per your requirements.

`CTRL_DOCKER_OPTIONS="--memory 2048m --cpu-shares 256"`

You can specify the CPU limit in `--cpu-shares` or `--cpus`.

- `--cpu-shares`  specifies the share or percentage of the host machine’s CPU cycles allocated. For example, `--cpu-shares 256`  allocates a quarter of total CPUs available.
- `--cpus` specifies how much of the available CPU resources the Apama container can use. For example, `--cpus 2`  allocates two CPUs out of the available CPUs from the host machine.

For more information about CPU limits, see Docker documentation.

To change the memory and CPU limit:

1. Log in to the Edge appliance.
2. Open the file "/etc/init.d/apama".
3. Edit the parameter `CTRL_DOCKER_OPTIONS` to the required values.
4. Restart the Apama service:
   - `[admin@iot-edge-server ~]$ sudo service apama restart`

{{< c8y-admon-important >}}

Since the changes to this file are overwritten when the Edge appliance is updated, you must reapply the changes to this file after the update process.

{{< /c8y-admon-important >}}
