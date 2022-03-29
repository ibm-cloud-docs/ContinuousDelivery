---

copyright:
  years: 2015, 2022
lastupdated: "2022-03-29"

keywords: tool integrations, IBM Cloud Public, DevOps Insights

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}   

# Adding DevOps Insights
{: #dra}

{{site.data.keyword.DRA_full}} collects and analyzes the results from unit tests, functional tests, and code coverage tools to determine whether your code meets predefined criteria at specified gates in your deployment process. If your code does not meet or exceed the criteria, the deployment is stopped to prevent risks from being released. You can use {{site.data.keyword.DRA_short}} as a safety net for your continuous delivery environment or as a way to implement and improve quality standards.
{: shortdesc}

This tool integration is available only on {{site.data.keyword.cloud_notm}} Public. It is preconfigured and does not require any configuration parameters. You cannot reconfigure this tool integration.
{: tip}

Add {{site.data.keyword.DRA_short}} to maintain and improve the quality of your code in {{site.data.keyword.Bluemix_notm}} by monitoring your deployments to identify risks before they are released.

1. If you are configuring this tool integration as you are creating the toolchain, in the Configurable Integrations section, click **{{site.data.keyword.DRA_short}}**.
1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.

   a. Click **Add tool**.

   b. In the Tool Integrations section, click **{{site.data.keyword.DRA_short}}**.

1. Click **Create Integration**.
1. On the Toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.DRA_short}}** and complete the getting started steps: create criteria, connect the criteria to the pipeline, and run the pipeline.

## Learn more about DevOps Insights
{: #learn_insights}

To learn more about {{site.data.keyword.DRA_short}}, see the [{{site.data.keyword.DRA_short}} article](https://www.ibm.com/cloud/garage/content/learn/tool_devops_insights/){: external} on the IBM Cloud Garage Method or take these tutorials:

* [Use the "Develop and test a Cloud Foundry app" toolchain](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain){: external}

* [Use the "Develop and test microservices on Cloud Foundry" toolchain](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){: external}

* [Explore {{site.data.keyword.DRA_full}}](https://www.ibm.com/cloud/garage/tutorials/explore-ibm-cloud-devops-insights){: external}
