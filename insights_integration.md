---

copyright:
  years: 2015, 2026
lastupdated: "2026-03-30"

keywords: tool integrations, IBM Cloud Public, DevOps Insights

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}  

# Adding DevOps Insights
{: #dra}

{{site.data.keyword.contdelivery_short}} will be discontinued in the following regions on 10 April 2026: **eu-es** and **jp-osa**.
This discontinuation also applies to any features provided within the service, including Code Risk Analyzer and {{site.data.keyword.DRA_short}}.
[Learn more](/docs/ContinuousDelivery?topic=ContinuousDelivery-faq_region_feature_consolidation)
{: important}

{{site.data.keyword.contdelivery_short}} will be discontinued in the following regions on 12 February 2027: **au-syd**, **ca-mon**, **ca-tor**, **us-east**. Code Risk Analyzer and {{site.data.keyword.DRA_short}} will also be deprecated in all regions on that date. However, if a region has no active usage of these features, the features in that region may be discontinued earlier and stop accepting new instances. [Learn more](/docs/ContinuousDelivery?topic=ContinuousDelivery-faq_region_feature_consolidation)
{: important}

{{site.data.keyword.DRA_full}} collects and analyzes the results from unit tests, functional tests, and code coverage tools to determine whether your code meets predefined criteria at specified gates in your deployment process. If your code does not meet or exceed the criteria, the deployment is stopped to prevent risks from being released. You can use {{site.data.keyword.DRA_short}} as a safety net for your continuous delivery environment or as a way to implement and improve quality standards.
{: shortdesc}

This tool integration is available only on {{site.data.keyword.cloud_notm}} Public. It is preconfigured and does not require any configuration parameters. You cannot reconfigure this tool integration.
{: tip}

Add {{site.data.keyword.DRA_short}} to maintain and improve the quality of your code in {{site.data.keyword.cloud_notm}} by monitoring your deployments to identify risks before they are released.

1. If you are configuring this tool integration as you are creating the toolchain, in the Configurable Integrations section, click **{{site.data.keyword.DRA_short}}**.
1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Toolchains**. On the Toolchains page, click the toolchain to open its Overview page. 

   a. Click **Add tool**.

   b. In the Tool Integrations section, click **{{site.data.keyword.DRA_short}}**.

1. Click **Create Integration**.
1. On the Toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.DRA_short}}** and complete the getting started steps: create criteria, connect the criteria to the pipeline, and run the pipeline.

## Configuring {{site.data.keyword.DRA_short}} by using the API
{: #insights-config-parameters}

The {{site.data.keyword.DRA_short}} tool integration is preconfigured and does not require any configuration parameters when you use the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} to [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `draservicebroker` value.
{: important}
