---

copyright:
  years: 2019, 2023
lastupdated: "2023-02-16"

keywords: devops insights, manage, data, quality, delete, test, tests, app, dashboard

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Deleting your {{site.data.keyword.DRA_short}} data
{: #deleting_data}

{{site.data.keyword.DRA_full}} hosts your data in a highly available and secure environment. Client and system credentials are stored on encrypted disks. Access to data is limited to only those users that require the data to support and maintain {{site.data.keyword.DRA_short}}. Data that is stored in {{site.data.keyword.DRA_short}} is indexed by a toolchain ID. When you delete a toolchain, all of the data that is related to repos that was collected as part of the toolchain is deleted.
{: shortdesc}

You can delete data in the following ways:

- Delete build, test, and deploy records
- Delete {{site.data.keyword.DRA_short}} data for a repo by disabling
- Delete integration between Toolchain and {{site.data.keyword.DRA_short}}
- Delete a repo from your toolchain

For more information about toolchains, see [Creating a toolchain from an app](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_an_app).

{{site.data.keyword.IBM_notm}} doesn't manage data in {{site.data.keyword.DRA_short}}. If you stop using {{site.data.keyword.DRA_short}}, you must delete your own data. To delete your data, delete the {{site.data.keyword.DRA_short}} tool integration from your toolchain. If the {{site.data.keyword.DRA_short}} tool integration is not added again to the toolchain within seven days, the data is deleted.
{: important}


## Deleting {{site.data.keyword.DRA_short}} data sets
{: #deleting-data-sets}

With the Manage data dashboard, you can delete {{site.data.keyword.DRA_short}} data for a toolchain, an environment, an application, or a branch. All {{site.data.keyword.DRA_short}} data for builds, test results, and deployment records are deleted. This data includes predefined and custom data, but not repo data. 

Data can’t be recovered after it is deleted.
{: tip}

To see your manage data dashboard, complete the following steps: 

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **DevOps**.
2. On the Toolchains page, select your toolchain.
3. From your toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.DRA_short}}**.
4. Select **Manage Data**.
5. Select **Quality Data**.

### Deleting toolchain data
{: #deleting-toolchain-data}

Toolchain data is all of the data that is associated with that toolchain. Deleting toolchain data doesn't delete the toolchain, or the tools that are associated with it. It deletes the data that is used by all of the tools that are attached to that toolchain.

1. To delete toolchain data, go to **Manage Data** > **Quality Data**.
2. Select **Toolchain data**. 
3. Click **Delete**.

### Deleting environment data
{: #deleting-environment-data}

Environment data refers to data that is associated with a specific location. For example, dallas-dev, dallas-prod, frankfurt-prod, or frankfurt-staging. To delete the environment data, complete the following steps:

1. Go to **Manage Data > Quality Data**.
2. Select **Environment data**. 
3. Select the environment that has the data that you want to delete
4. Click **Delete**.

### Deleting application data
{: #deleting-application-data}

Application data is all of the data that is associated with a certain app that is attached to a toolchain. To delete the environment data sets, complete the following steps:

1. Go to **Manage Data** > **Quality Data**.
2. Select **Application data**.
3. Select the app that has the data you want to delete, and click **Delete**.

### Deleting branch data for an application
{: #deleting-branch-application}

Branch data for an application is the data that is associated with a specific repo of an application. For example, the master branch or staging repo. 

1. To delete the environment data, go to **Manage Data** > **Quality Data**.
2. Select **Branch data for an application**.
3. Select the app and the branch that has the data you want to delete.
4. Click **Delete**.


## Deleting a {{site.data.keyword.DRA_short}} tool integration
{: #insights-delete-integration}

To delete the {{site.data.keyword.DRA_short}} tool integration, you must delete {{site.data.keyword.DRA_short}} from your toolchain. To delete {{site.data.keyword.DRA_short}} from your toolchain, complete the following steps to delete the tool integration by using the console, with the API, or with Terraform.

### Deleting a {{site.data.keyword.DRA_short}} tool integration by using the console
{: #insights-delete-integration-ui}
{: ui}

1. Click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **DevOps**.
2. On the Toolchains page, select your toolchain.
3. From your toolchain's Overview page, on the **IBM Cloud tools** card, click the Overflow icon ![ellipsis icon](images/overflow-icon-2.svg) on your {{site.data.keyword.DRA_short}} instance. Then, select **Delete**.

### Deleting a {{site.data.keyword.DRA_short}} tool integration with the API
{: #insights-delete-integration-api}
{: api}

1. [Obtain an IAM bearer token](https://{DomainName}/apidocs/toolchain#authentication){: external}. Alternatively, if you are using an SDK, [obtain an IAM API key](https://{DomainName}/iam/apikeys){: external} and set the client options by using environment variables.
   
   ```bash
   export CD_TOOLCHAIN_AUTH_TYPE=iam && \
   export CD_TOOLCHAIN_APIKEY={iam_api_key} && \
   export CD_TOOLCHAIN_URL={base_url}
   ```
   {: pre}

2. [Determine the region and ID of the toolchain](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started&interface=api#viewing-toolchain-api).

3. Determine the ID of the {{site.data.keyword.DRA_short}} tool integration.

   ```curl
   curl -X GET \
     {base_url}/toolchains/{toolchain_id}/tools \
     -H "Authorization: Bearer {token}" \
     -H "Accept: application/json"
   ```
   {: pre}
   {: curl}

   ```javascript
   const CdToolchainV2 = require('@ibm-cloud/continuous-delivery/cd-toolchain/v2');
   ...
   const toolchainService = CdToolchainV2.newInstance(); 
   const tools = await toolchainService.listTools({
      toolchainId: {toolchain_id},
   });
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
	listToolsOptions := toolchainClient.NewListToolsOptions({toolchain_id})
	tools, response, err := toolchainClient.ListTools(listToolsOptions)
   ```
   {: codeblock}
   {: go}

   ```python
   from ibm_continuous_delivery.cd_toolchain_v2 import CdToolchainV2
   ...
   toolchain_service = CdToolchainV2.new_instance()
   tools = toolchain_service.list_tools(
      toolchain_id = {toolchain_id}
   )
   ```
   {: codeblock}
   {: python}

   ```java
   import com.ibm.cloud.continuous_delivery.cd_toolchain.v2.CdToolchain;
   import com.ibm.cloud.continuous_delivery.cd_toolchain.v2.model.*;
   ...
   CdToolchain toolchainService = CdToolchain.newInstance();
   ListToolsOptions listToolsOptions = new ListToolsOptions.Builder()
      .toolchainId({toolchain_id})
      .build();
   Response<ToolchainToolCollection> response = toolchainService.listTools(listToolsOptions).execute();
   ToolchainToolCollection tools = response.getResult();
   ```
   {: codeblock}
   {: java}

4. Delete the {{site.data.keyword.DRA_short}} tool integration from the toolchain.

   ```curl
   curl -X DELETE \
     {base_url}/toolchains/{toolchain_id}/tools/{tool_integration_id} \
     -H 'Authorization: Bearer {token}'
   ```
   {: pre}
   {: curl}

   ```javascript
   const response = await toolchainService.deleteTool({
      toolchainId: {toolchain_id},
      toolId: {tool_integration_id}
   });
   ```
   {: codeblock}
   {: node}

   ```go
   deleteToolOptions := toolchainClient.NewDeleteToolOptions({toolchain_id}, {tool_integration_id})
   response, err := toolchainClient.DeleteTool(deleteToolOptions)
   ```
   {: codeblock}
   {: go}

   ```python
   response = toolchainService.delete_tool(
      toolchain_id = {toolchain_id},
      tool_id = {tool_integration_id}
   )
   ```
   {: codeblock}
   {: python}

   ```java
   DeleteToolOptions deleteToolOptions = new DeleteToolOptions.Builder()
      .toolchainId({toolchain_id})
      .toolId({tool_integration_id})
      .build();
   Response<Void> response = toolchainService.deleteTool(deleteToolOptions).execute();
   ```
   {: codeblock}
   {: java}

The following table lists and describes each of the variables that are used in the previous steps.   
    
| Variable | Description |
|:---------|:------------|
| `{base_url}` | The Toolchain API endpoint URL, for example `https://api.us-south.devops.cloud.ibm.com/toolchain/v2`. For more information about this endpoint URL, including a list of values, see [Endpoint URL](https://{DomainName}/apidocs/toolchain#endpoint-url){: external}. |
| `{iam_api_key}` | Your IAM API key. |
| `{tool_integration_id}` | The ID of the tool integration. |
| `{toolchain_id}` | The ID of the toolchain in which to delete the tool integration. |
| `{token}` | A valid IAM bearer token. |
{: caption="Table 1. Variables for deleting the {{site.data.keyword.DRA_short}} tool integration with the API" caption-side="top"}

For more information about the {{site.data.keyword.DRA_short}} tool integration, see [Adding DevOps Insights](/docs/ContinuousDelivery?topic=ContinuousDelivery-dra).

### Deleting a {{site.data.keyword.DRA_short}} tool integration with Terraform
{: #insights-delete-integration-terraform}
{: terraform}

1. Locate the Terraform file (for example, `main.tf`) that contains the `resource` block for the existing {{site.data.keyword.DRA_short}} tool integration.

   The `resource` blocks in the following example describe an existing toolchain and {{site.data.keyword.DRA_short}} tool integration.

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

2. Remove the `resource "ibm_cd_toolchain_tool_devopsinsights"` block from your Terraform file.

3. Initialize the Terraform CLI.

   ```terraform
   terraform init
   ```
   {: pre}
   
4. Create a Terraform execution plan. This plan summarizes all of the actions that must run to delete the {{site.data.keyword.DRA_short}} tool integration.

   ```terraform
   terraform plan
   ```
   {: pre}

5. Apply the Terraform execution plan. Terraform takes all of the required actions to delete the {{site.data.keyword.DRA_short}} tool integration.

   ```terraform
   terraform apply
   ```
   {: pre}

For more information about using Terraform with {{site.data.keyword.contdelivery_short}}, see [Setting up Terraform for {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-terraform-setup).

## Deleting a repo
{: #deleting-repo}

When you delete a repo, all of the data that is related to that repo is also deleted.

1. Click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **DevOps**.
2. On the Toolchains page, select your toolchain.
3. From your toolchain's Overview page, on the **Repositories** card, click the Overflow icon ![ellipsis icon](images/overflow-icon-2.svg) on the repo that you  want to delete. Then, select **Delete**.
