---

copyright:
  years: 2016, 2022
lastupdated: "2022-12-14"

keywords: devops insights, devops, insights, integrate, adding, code coverage, test, tests, verification, install, app, dashboard, risk

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

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

### Integrating {{site.data.keyword.DRA_short}} by using the console
{: #integrate-insights-toolchain-ui}
{: ui}

You can add {{site.data.keyword.DRA_short}} to any toolchain by selecting it from the tool integration catalog.

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) **> DevOps**.
2. Select your toolchain.  
3. Click **Add tool**.
4. Select the **{{site.data.keyword.DRA_short}}** tile.
5. Click **Create Integration**.
6. On the Toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.DRA_short}}** to view your {{site.data.keyword.DRA_short}} dashboard.

### Integrating {{site.data.keyword.DRA_short}} with the API
{: #integrate-insights-toolchain-api}
{: api}

1. [Obtain an IAM bearer token](https://{DomainName}/apidocs/toolchain#authentication){: external}. Alternatively, if you are using an SDK, [obtain an IAM API key](https://{DomainName}/iam/apikeys){: external} and set the client options by using environment variables.
   
   ```bash
   export CD_TOOLCHAIN_AUTH_TYPE=iam && \
   export CD_TOOLCHAIN_APIKEY={iam_api_key} && \
   export CD_TOOLCHAIN_URL={base_url}
   ```
   {: pre}

2. [Determine the region and ID of the toolchain](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started&interface=api#viewing-toolchain-api) that you want to add the {{site.data.keyword.DRA_short}} tool integration to.

3. Add the {{site.data.keyword.DRA_short}} tool integration to the toolchain.

   ```curl
   curl -X POST \
     {base_url}/toolchains/{toolchain_id}/tools \
     -H 'Authorization: Bearer {token}' \
     -H 'Accept: application/json` \
     -H 'Content-Type: application/json' \
       -d '{
       "tool_type_id": "draservicebroker",
       "name": "{tool_integration_name}"
     }'
   ```
   {: pre}
   {: curl}

   ```javascript
   const CdToolchainV2 = require('ibm-continuous-delivery/cd-toolchain/v2');
   ...
   (async () => { 
      const toolchainService = CdToolchainV2.newInstance();
      const draPrototypeModel = {
         toolchainId: {toolchain_id},
         toolTypeId: 'draservicebroker',
         name: {tool_integration_name}
      };
      const draTool = await toolchainService.createTool(draPrototypeModel);
   })();
   ```
   {: codeblock}
   {: node}

   ```go
   import (
	   "github.com/IBM/continuous-delivery-go-sdk/cdtoolchainv2"
   )
   ...
   toolchainClientOptions := &cdtoolchainv2.CdToolchainV2Options{}
   toolchainClient, err := cdtoolchainv2.NewCdToolchainV2UsingExternalConfig(toolchainClientOptions)
   createDraToolOptions := toolchainClient.NewCreateToolOptions({toolchain_id}, "draservicebroker")
   createDraToolOptions.SetName({tool_integration_name})
   draTool, response, err := toolchainClient.CreateTool(createDraToolOptions)
   ```
   {: codeblock}
   {: go}

   ```python
   from ibm_continuous_delivery.cd_toolchain_v2 import CdToolchainV2
   ...
   toolchainService = CdToolchainV2.new_instance()
   draTool = toolchainService.create_tool(
      name = {tool_integration_name}
      toolchain_id = {toolchain_id}
      tool_type_id = "draservicebroker"
   )
   ```
   {: codeblock}
   {: python}

The following table lists and describes each of the variables that are used in the previous steps.   
    
| Variable | Description |
|:---------|:------------|
| `{base_url}` | The Toolchain API endpoint URL, for example `https://api.us-south.devops.cloud.ibm.com/toolchain/v2`. For more information about this endpoint URL, including a list of values, see [Endpoint URL](https://{DomainName}/apidocs/toolchain#endpoint-url){: external}. |
| `{iam_api_key}` | Your IAM API key. |
| `{tool_integration_name}` | A name for your tool integration. |
| `{toolchain_id}` | The ID of the toolchain to which to add the tool integration. |
| `{token}` | A valid IAM bearer token. |
{: caption="Table 1. Variables for adding the {{site.data.keyword.DRA_short}} tool integration with the API" caption-side="top"}

For more information about the {{site.data.keyword.DRA_short}} tool integration, see [Adding DevOps Insights](/docs/ContinuousDelivery?topic=ContinuousDelivery-dra).

### Integrating {{site.data.keyword.DRA_short}} with Terraform
{: #integrate-insights-toolchain-terraform}
{: terraform}

1. To install the Terraform CLI and configure the {{site.data.keyword.cloud_notm}} provider plug-in for Terraform, follow the tutorial for [Getting started with Terraform on {{site.data.keyword.cloud_notm}}](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started).

2. Locate the Terraform file (for example, `main.tf`) that contains the resource block for the toolchain to which you want to add the {{site.data.keyword.DRA_short}} tool integration. In this file, add the configuration to create the tool integration.

   The following example creates the toolchain if it does not exist, then adds the {{site.data.keyword.DRA_short}} tool integration by using the `ibm_cd_toolchain_tool_devopsinsights` resource.
  
   ```terraform
   data "ibm_resource_group" "group" {
     name = "default"
   }

   resource "ibm_cd_toolchain" "cd_toolchain" {
     name              = "my toolchain"
     resource_group_id = data.ibm_resource_group.group.id
   }

   resource "ibm_cd_toolchain_tool_devopsinsights" "cd_toolchain_tool_insights" {
     toolchain_id = ibm_cd_toolchain.cd_toolchain.id
   }
   ```
   {: codeblock}

   For more information about `ibm_cd_toolchain_tool_devopsinsights`, see the argument reference details in the [Terraform Registry Documentation](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/cd_toolchain_tool_devopsinsights){: external}.
  
3. Initialize the Terraform CLI.

   ```terraform
   terraform init
   ```
   {: pre}
   
4. Create a Terraform execution plan. This plan summarizes all of the actions that must run to add the {{site.data.keyword.DRA_short}} tool integration to the toolchain.

   ```terraform
   terraform plan
   ```
   {: pre}

5. Apply the Terraform execution plan. Terraform takes all of the required actions to add the {{site.data.keyword.DRA_short}} tool integration to the toolchain.

   ```terraform
   terraform apply
   ```
   {: pre}

For more information about using Terraform with {{site.data.keyword.contdelivery_short}}, see [Setting up Terraform for {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-terraform-setup).

## Next steps
{: #adding-next-steps}

After you add {{site.data.keyword.DRA_short}}, you can publish quality data from other sources. These sources include {{site.data.keyword.deliverypipelinelong}} in the toolchain, Jenkins, Travis CI, or other pipelines. To learn more, see [aggregating data from multiple sources into a single toolchain](/docs/ContinuousDelivery?topic=ContinuousDelivery-aggregating-multiple-sources).
