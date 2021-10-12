---

copyright:
  years: 2016, 2020
lastupdated: "2020-04-20"

keywords: devops insights, devops, insights, integrate, adding, code coverage, test, tests, verification, install, app, dashboard, risk

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}
{:important: .important}

# Adding {{site.data.keyword.DRA_short}} to your toolchain
{: #add-devops-insights}

Use {{site.data.keyword.DRA_full}} to help improve build quality for your projects. {{site.data.keyword.DRA_short}} is a tool that provides data for team insights and deployment risk. Get insights about your application by uploading unit tests, code coverage, functional verification tests, and static security scans for each application to {{site.data.keyword.DRA_short}}.
{: shortdesc}


## Before you begin
{: #adding-insights-prereq}

To use {{site.data.keyword.DRA_short}}, you must have a toolchain. A toolchain is a group of tools that are attached to one of your applications. Think of the tools as enhancements to the app and the toolchain as a utility belt. {{site.data.keyword.DRA_short}} works with the other tools in the toolchain, like GitHub and {{site.data.keyword.deliverypipeline}}, to aggregate data for your application.

For more information about toolchains, see [Creating a toolchain from an app](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_an_app).


## Integrating {{site.data.keyword.DRA_short}}
{: #integrate-insights-toolchain}

You can add {{site.data.keyword.DRA_short}} to any toolchain by selecting it from the tool integration catalog.

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) **> DevOps**.
2. Select your toolchain.  
3. Click **Add tool**.
4. Select the **{{site.data.keyword.DRA_short}}** tile.
5. Click **Create Integration**.
6. Click the **{{site.data.keyword.DRA_short}}** tile to view your {{site.data.keyword.DRA_short}} dashboard.


## Next steps
{: #adding-next-steps}

After you add {{site.data.keyword.DRA_short}}, you can publish quality data from other sources. These sources include {{site.data.keyword.deliverypipelinelong}} in the toolchain, Jenkins, Travis CI, or other pipelines. To learn more, see [aggregating data from multiple sources into a single toolchain](/docs/ContinuousDelivery?topic=ContinuousDelivery-aggregating-multiple-sources).
