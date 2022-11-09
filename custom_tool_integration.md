---

copyright:
  years: 2015, 2022

lastupdated: "2022-11-09"

keywords: tool integrations, IBM Cloud Public, Other Tool, Custom Tool

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Configuring a custom tool (Other Tool)
{: #othertool}

If your team uses a tool that isn't included in the toolchains integrations list, you can integrate a custom tool.{: shortdesc}

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

## Configuring a custom tool by using the API
{: #config-parameters}

The custom tool (Other Tool) tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `customtool` property in the request body with the `artifactory` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| type | required, updatable | String | type | The name of this tool integration, for example, `Delivery Pipeline`. |
| lifecyclePhase | required, updatable | String | lifecycle_phase | The lifecycle phase of the {{site.data.keyword.cloud_notm}} Garage Method that is the most closely associated with this tool. |
| imageUrl | optional, updatable | String | image_url | The URL of the icon to display on your tool integration's card. |
| documentationUrl | optional, updatable | String | documentation_url | The URL for your tool's documentation. |
| name | required, updatable | String | name | The name for this specific tool integration, for example, `My Build and Deploy Pipeline`. |
| dashboard_url | required, updatable | String | dashboard_url | The URL that you want to go to when you click the tool integration card. |
| description | optional, updatable | String | description | A description for the tool instance. |
| additional-properties | optional, updatable | String | additional_properties | Advanced. Any information that is required to integrate with other tools in your toolchain. |
{: caption="Table 1. Custom tool tool integration parameters" caption-side="bottom"}

## Learn more about custom tool
{: #learn_custom_tool}

To learn more about the custom tool, take this tutorial:

* [Add a custom tool integration to a toolchain](https://www.ibm.com/cloud/architecture/tutorials/add-a-custom-tool-integration-to-a-toolchain){: external}
