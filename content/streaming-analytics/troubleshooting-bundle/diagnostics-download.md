---
weight: 10
title: Downloading diagnostics and logs
layout: redirect
---

{{< c8y-admon-info >}}
Diagnostics are not available for the Apama-ctrl-smartrules and Apama-ctrl-smartrulesmt microservices.
{{< /c8y-admon-info >}}

If a user has READ permission for "CEP management", then two links for downloading diagnostics information are available from the bottom of the Streaming Analytics application: one for downloading basic diagnostics information (the **Diagnostics** link) and another one for downloading enhanced (more resource-intensive) diagnostics information (the **Enhanced** link). These links are shown at the bottom of the home screen and also on the pages that appear when you go to the **Analytics Builder** and **EPL Apps** pages (that is, in the EPL app manager and in the model manager).

It may be useful to capture this diagnostics information when experiencing problems, or for debugging EPL apps. It is also useful to provide to [product support](/additional-resources/contacting-support/) if you are filing a support ticket.
You can see a version number next to the links.

Basic diagnostics information is provided in a ZIP file named *diagnostic-overview&lt;timestamp&gt;.zip* and includes the following information (this should be typically a few Megabytes, and be generated in about 5 seconds):

- The microservice log file contents, if available, including a record of the correlator's startup logging and the last hour or maximum of 20,000 lines of logging.

    {{< c8y-admon-info >}}
  In case of {{< product-c8y-iot >}} Edge, since Apama-ctrl is not deployed as a microservice in Edge, Apama logs can be retrieved using the diagnostic utility. For more details, see [Apama log file locations](/edge/operating-edge/#apama-log-file-locations) and [Diagnostic utility](/edge/operating-edge/#diagnostics).
    {{< /c8y-admon-info >}}

- Apama-internal diagnostics information (similar to the `engine_watch` and `engine_inspect` command-line tools available in Apama).

- A copy of all EPL apps, smart rules and analytic models.

- A copy of any alarms that the Apama-ctrl microservice has raised.

- CPU profiling (over a duration of 5 seconds).

- EPL memory profiler snapshots.

- Some information from the environment (tenant details, environment variables).

- Version numbers of the components.

Enhanced diagnostics information is provided in a ZIP file named *diagnostic-enhanced&lt;timestamp&gt;.zip* and includes the following information:

- Contains what is in the above-mentioned *diagnostic-overview&lt;timestamp&gt;.zip* file.
- In addition, it includes requests that are more resource-intensive and may significantly slow down the correlator. These include the contents of the queues, CPU usage, and so on.

What a user can see or do depends on the permissions:

- A user with only READ permission for "CEP management" has read-only access to EPL apps and analytic models.
- Without ADMIN permission for "CEP management", the user is not able to activate or edit EPL apps or analytic models.
- If a user has both READ and ADMIN permissions for "CEP management", the user has read-write access and can access the diagnostics information.
- If a user has only the ADMIN permission for "CEP management" and no READ permission, the user is able to load, edit and deploy EPL apps and analytic models, but is not able to see or access the diagnostics information.
