---
weight: 10
title: Integrating Cumulocity IoT DataHub with TrendMiner
layout: redirect
---

TrendMiner provides process manufacturing companies the analytical means to further optimize their production processes. The self-service analytics approach allows you to conduct time-series industrial analytics, with data being automatically visualized in displays and dashboards.

For that purpose, TrendMiner accesses industrial data generated by these production processes, resulting in time series of sensor, instrument, and asset data. TrendMiner analyzes these time series in order to identify trends and patterns and derive actionable insights solving production issues.

With the offloading and query capabilities of {{< product-c8y-iot >}} DataHub, TrendMiner can also access and analyze the data being managed by the {{< product-c8y-iot >}} platform. Key features of the integration between {{< product-c8y-iot >}} DataHub and TrendMiner are:

* TrendMiner can leverage historical data of the {{< product-c8y-iot >}} platform without adversely affecting the Operational Store of the platform. {{< product-c8y-iot >}} DataHub offloads for that purpose the data from the Operational Store to a data lake.
* TrendMiner offers a time-series visualization interface and operational monitoring, both relying on live data from the {{< product-c8y-iot >}} platform. {{< product-c8y-iot >}} DataHub provides for that purpose a live view on recent data in the Operational Store of the platform.
* {{< product-c8y-iot >}} DataHub unifies the data access layer so that TrendMiner can access historical as well as live data by querying a single view.
* {{< product-c8y-iot >}} DataHub ensures that the layout of that table meets the query needs of TrendMiner, that is, the data is in a relational and flattened format, not in a document-based format as in the Operational Store.

The following diagram illustrates the high-level concepts of the integration between {{< product-c8y-iot >}} DataHub and TrendMiner.

<img src="/images/datahub-guide/trendminer-highlevel-concept.png" alt="Integration of {{< product-c8y-iot >}} DataHub and TrendMiner" style="max-width: 100%">

### Design of a TrendMiner offloading pipeline

Providing TrendMiner access to {{< product-c8y-iot >}} data requires you solely to define an offloading pipeline using the TrendMiner data layout. When the offloading pipeline is in place, {{< product-c8y-iot >}} data is regularly extracted from the Operational Store, flattened, and exported into a data lake. In addition, Dremio is configured to access recent data from the Operational Store, using the same schema as for the historical data.

In Dremio a new view is provided, which combines the historical data in the data lake with recent data from the Operational Store, effectively providing a unified view over *hot* data in the Operational Store and *cold* data in the data lake. {{< product-c8y-iot >}} DataHub takes care that the combined data in that view is lossless and does not introduce duplicates. This view is the single connection point to provide TrendMiner access to historical and live data of the {{< product-c8y-iot >}} platform.

> **Info:** So far {{< product-c8y-iot >}} DataHub provides TrendMiner acccess to the measurements collection. Other base collections are not yet supported.

You must follow the instructions in [Configuring offloading jobs](/datahub/working-with-datahub/#configuring-offloading-jobs) on how to configure an offloading pipeline for the measurements collection, so that TrendMiner can access the data.

### Accessing Cumulocity IoT data in TrendMiner

Once you have defined and activated a TrendMiner offloading pipeline, the initial offload must be completed before you can start querying the data in TrendMiner.

> **Info:** The offloading pipeline must be active. If the pipeline is deactivated, you can only query the contents offloaded into the data lake so far. Access to recent data will be deactivated.

{{< product-c8y-iot >}} DataHub provides the following views within Dremio, based on tables having the same name and the same schema:

* **c8y_cdh_tm_measurements** is the view over the table in the data lake, which stores historical data being offloaded from the Operational Store so far.
* **c8y_cdh_tm_measurements_live** is the live view combining **c8y_cdh_tm_measurements** with recent data from the Operational Store. Both views have the same schema.
* **c8y_cdh_tm_tags** is the view over the table in the data lake, which stores the tag names and the source IDs. The source ID identifies the device managed in the {{< product-c8y-iot >}} platform. The tagname combines the source ID with the path in the measurements documents to the values establishing the time series. In TrendMiner you use the tagnames to select the time series you want to investigate. With this view you can map this series to the device in the platform.

For details on the schema of these views/tables, see the section [Offloading Cumulocity IoT base collections](/datahub/working-with-datahub/#offloading-base-collections).

In TrendMiner you must connect to these Dremio views using ODBC. For the ODBC connection settings, you must navigate to the **Home** page in the {{< product-c8y-iot >}} DataHub UI and click the ODBC icon to open the ODBC connection settings.

For more details on the steps required in TrendMiner, see also the corresponding TrendMiner documentation of the [Generic ODBC Connector Configuration](https://support.trendminer.com/hc/en-us/articles/360039446851-Generic-Connector-Configuration).