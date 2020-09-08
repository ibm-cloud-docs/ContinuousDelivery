---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-19"

keywords: tool integrations, IBM Cloud Public, IBM Cloud Dedicated, Other Tool, Custom Tool

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

# Configuring a custom tool (Other Tool)
{: #othertool}

If your team uses a tool that isn't included in the toolchains integrations list, you can integrate a custom tool.{:shortdesc}

Configure a custom tool so that it works with other tools in your toolchain and is available to your team:

1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**. 

 a. Click **Add tool**.

 b. In the Tool Integrations section, click **Other Tool**.

1. Type the tool name.
1. Select the lifecycle phase that is most closely associated with the tool. This selection determines which category your tool is listed under on the Overview page.
1. Add an icon URL. The icon is shown on your tool integration's card.
1. Add a documentation URL.
1. Specify a tool instance name. For example, My Team Tool.
1. Add a tool instance URL. This URL opens whenever the tool integration's card is clicked.
1. Add a description of your tool.
1. (Advanced) Add more properties as needed. For example, list any information or attributes that are required for your tool to integrate with other tools in the toolchain.  
1. Click **Create Integration**.

## Learn more about custom tool

To learn more about the custom tool, take this tutorial:

  * [Add a custom tool integration to a toolchain](https://www.ibm.com/cloud/garage/tutorials/add-a-custom-tool-integration-to-a-toolchain){:external}
