---

copyright:
  years: 2015, 2025
lastupdated: "2025-12-04"

keywords: tool integrations, IBM Cloud Public, Other Tool, Custom Tool

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Configuring a custom tool (Other Tool)
{: #othertool}

If your team uses a tool that isn't included in the toolchains integrations list, you can integrate a custom tool.
{: shortdesc}

Configure a custom tool so that it works with other tools in your toolchain and is available to your team:

1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Toolchains**. On the Toolchains page, click the toolchain to open its Overview page. 

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

## Configuring a custom tool (Other Tool) by using the API
{: #custom-tool-config-parameters}

The custom tool (Other Tool) tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `customtool` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| additional-properties | optional, updatable | String | additional_properties | Specifies any information that is required to integrate with other tools in the toolchain. |
| dashboard_url | required, updatable | String | dashboard_url | The URL of the dashboard for this tool integration. In the graphical UI, the browser goes to this dashboard when you click the Other Tool tool integration card. |
| description | optional, updatable | String | description | A description that outlines the function of this tool integration. |
| documentationUrl | optional, updatable | String | documentation_url | The URL of this tool integration's documentation. |
| imageUrl | optional, updatable | String | image_url | The URL of the icon that is displayed on the tool integration card in the graphical UI. |
| lifecyclePhase | required, updatable | String | lifecycle_phase | The lifecycle phase of the {{site.data.keyword.cloud_notm}} Garage Method that is the most closely associated with this tool integration. |
| name | required, updatable | String | name | The name of this tool integration. |
| type | required, updatable | String | type | The type of tool that this custom tool is integrating with. |
{: caption="Custom tool (Other Tool) tool integration parameters" caption-side="bottom"}
