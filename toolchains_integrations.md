---

copyright:
  years: 2015, 2022
lastupdated: "2022-11-29"

keywords: tool integrations, IBM Cloud Public, App Configuration, Artifactory, Bitbucket, Delivery Pipeline, DevOps Insights, Delivery Pipeline Private Worker, Git Repos and Issue Tracking, GitHub, GitLab, Hashicorp Vault, Jenkins, JIRA, IBM Key Protect, IBM Secrets Manager, Nexus, Custom Tool, PagerDuty, Rational Team Concert, Sauce Labs, Security and Compliance Center, Slack, SonarQube

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}  

# Working with tool integrations
{: #integrations}

You can add, update, and delete tool integrations by using the console, with the API, or with Terraform. You can configure tool integrations that support development, deployment, and operations tasks while you create an open toolchain, or you can add and configure tool integrations to customize an existing toolchain.  
{: shortdesc}

## Adding a tool integration by using the console
{: #create_integration_ui}
{: ui}

You can add tool integrations to your toolchain by using the console.

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**.
1. On the Toolchains page, click a toolchain to open its Overview page. Alternatively, on the App details page in your app, click the toolchain name.
1. To see a list of tool integrations to add, click **Add tool**.
1. Click a tool integration that you want to add.
1. Enter any required information to configure the tool integration.
1. Click **Create Integration** to add the tool integration to your toolchain.

## Adding a tool integration with the API
{: #create_integration_api}
{: api}

You can add tool integrations to your toolchain with the API.

1. [Obtain an IAM bearer token](https://{DomainName}/apidocs/toolchain#authentication){: external}. Alternatively, if you are using an SDK, [obtain an IAM API key](https://{DomainName}/iam/apikeys){: external} and set the client options by using environment variables.
   
   ```bash
   export CD_TOOLCHAIN_AUTH_TYPE=iam
   export CD_TOOLCHAIN_APIKEY={iam_api_key}
   export CD_TOOLCHAIN_URL={base_url}
   ```
   {: pre}

1. [Look up the ID of the toolchain](https://{DomainName}/apidocs/toolchain#list-toolchains){: external} in which you want to create your tool integration.
1. [Look up the `tool_type_id` value](#integrations) that corresponds to the tool integration that you want to add.
1. Add the tool integration within the targeted toolchain.
   
   ```curl
   curl -X POST --location --header "Authorization: Bearer {iam_token}" \
     --header "Accept: application/json" \
     --header "Content-Type: application/json" \
     --data '{ "name": "{tool_name}", "tool_type_id": "{tool_type_id}", "parameters": {tool_parameters} }' \
     "{base_url}/toolchains/{toolchain_id}/tools"
   ```
   {: pre}
   {: curl}

   ```javascript
   const CdToolchainV2 = require('ibm-continuous-delivery/cd-toolchain/v2');
   const toolchainService = CdToolchainV2.newInstance();
   ...
   (async() => {
      const toolPrototypeModel = {
         toolchainId: {tool_type_id},
         toolTypeId: {tool_type_id},
         name: {tool_name},
         parameters: {tool_parameters}
      };
      const response = await toolchainService.createTool(toolPrototypeModel);
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
   createToolOptions := toolchainClient.NewCreateToolOptions({tool_type_id}, {tool_type_id})
   createToolOptions.SetName({tool_name})
   createToolOptions.SetParameters({tool_parameters})
   tool, response, err := toolchainClient.CreateTool(createToolOptions)
   ```
   {: codeblock}
   {: go}

The following table lists and describes each of the variables that are used in the previous steps.   
    
| Variable | Description |
|:---------|:------------|
| `{base_url}` | The Toolchain API endpoint URL. For more information about supported values, see [Endpoint URL](https://{DomainName}/apidocs/toolchain#endpoint-url){: external}. |
| `{iam_api_key}` | Your IAM API key. |
| `{iam_token}` | A valid IAM bearer token. |
| `{tool_name}` | The name of the tool integration. |
| `{tool_parameters}` | Unique key-value pairs that represent the parameters to use to create the tool integration. For more information about the supported parameters for each tool integration, see [Tool integrations](#integrations). |
| `{tool_type_id}` | The unique, short name that represents the type of the tool integration. |
| `{toolchain_id}` | The toolchain in which to create the tool integration. |
{: caption="Table 1. Variables for provisioning the tool integration with the API" caption-side="top"}

## Adding a tool integration with Terraform
{: #create_integration_terraform}
{: terraform}

You can add tool integrations to your toolchain with Terraform.

1. To install the Terraform CLI and configure the {{site.data.keyword.cloud_notm}} provider plug-in for Terraform, follow the tutorial for [Getting started with Terraform on {{site.data.keyword.cloud}}](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started).
1. Create a Terraform configuration file that is named `main.tf`. In this file, add the configuration to create resource instances by using the HashiCorp Configuration Language (HCL). For more information about using this configuration language, see the [Terraform documentation](https://www.terraform.io/docs/language/index.html){: external}.

   The following example creates a {{site.data.keyword.deliverypipeline}} tool integration by using the `ibm_cd_toolchain_tool_pipeline` resource, where `toolchain_id` is a GUID that represents the toolchain in which to create the tool integration. 
   
   ```terraform
   data "ibm_cd_toolchain" "cd_toolchain" {
     toolchain_id = {toolchain_id}
   }
   
   resource "ibm_cd_toolchain_tool_pipeline" "cd_pipeline" {
     toolchain_id = data.ibm_cd_toolchain.cd_toolchain.id
     parameters {
       name = "myPipeline"
     }
   }
   ```
   {: codeblock}

   For more information about tool integration resources, see the full list of supported tool integration resources in the [{{site.data.keyword.cloud_notm}} Terraform Registry](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/cd_toolchain){: external}.

1. Initialize the Terraform CLI.

   ```terraform
   terraform init
   ```
   {: pre}
   
1. Create a Terraform execution plan. This plan summarizes all of the actions that must run to create the tool integration.

   ```terraform
   terraform plan
   ```
   {: pre}

1. Apply the Terraform execution plan. Terraform takes all of the required actions to create the tool integration.

   ```terraform
   terraform apply
   ```
   {: pre}

## Updating a tool integration by using the console
{: #update_integration_ui}
{: ui}

If you deferred the configuration of a tool integration when you created a toolchain, a Configure button is shown on its card. If you configured a tool integration when you created a toolchain, you can update the configuration settings by using the console.

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. 
1. On the Toolchains page, click the toolchain that contains the tool integration that you want to update to open its Overview page. Alternatively, on the App details page in your app, click the toolchain name.
1. If you need to configure a tool integration for the first time, on its card, click **Configure**.
1. When you are finished configuring the tool integration, click **Save Integration**.
1. If you need to update a tool integration's configuration, click the **Actions** icon ![Actions icon](../../icons/action-menu-icon.svg "Actions") **> Configure**.
1. When you are finished updating the settings, click **Save Integration**.

## Updating a tool integration with the API
{: #update_integration_api}
{: api}

If you configured a tool integration when you created a toolchain, you can update the configuration settings with the API.

1. [Obtain an IAM bearer token](https://{DomainName}/apidocs/toolchain#authentication){: external}. Alternatively, if you are using an SDK, [obtain an IAM API key](https://{DomainName}/iam/apikeys){: external} and set the client options by using environment variables.
   
   ```bash
   export CD_TOOLCHAIN_AUTH_TYPE=iam
   export CD_TOOLCHAIN_APIKEY={iam_api_key}
   export CD_TOOLCHAIN_URL={base_url}
   ```
   {: pre}

1. [Look up the ID of the toolchain](https://{DomainName}/apidocs/toolchain#list-toolchains){: external} where the tool integration exists.
1. Using the ID of the toolchain, [look up the ID of the tool integration](https://{DomainName}/apidocs/toolchain#list-tools).
1. Update the tool integration within the targeted toolchain.
   
   ```curl
   curl -X PATCH --location --header "Authorization: Bearer {iam_token}" \
     --header "Accept: application/json" \
     --header "Content-Type: application/merge-patch+json" \
     --data '{ "name": "{new_tool_name}", "parameters": {new_tool_parameters} }' \
     "{base_url}/toolchains/{toolchain_id}/tools/{tool_id}"
   ```
   {: pre}
   {: curl}

   ```javascript
   const CdToolchainV2 = require('ibm-continuous-delivery/cd-toolchain/v2');
   const toolchainService = CdToolchainV2.newInstance();
   ...
   (async() => {
      const toolPatchModel = {
         toolchainId: {tool_type_id},
         toolId: {tool_id},
         name: {new_tool_name},
         parameters: {new_tool_parameters}
      };
      const response = await toolchainService.updateTool(toolPatchModel);
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
   updateToolOptions := toolchainClient.NewUpdateToolOptions({tool_type_id}, {tool_id})
   updateToolOptions.SetName({new_tool_name})
   updateToolOptions.SetParameters({new_tool_parameters})
   tool, response, err := toolchainClient.UpdateTool(updateToolOptions)
   ```
   {: codeblock}
   {: go}

The following table lists and describes each of the variables that are used in the previous steps.   
    
| Variable | Description |
|:---------|:------------|
| `{base_url}` | The Toolchain API endpoint URL. For more information about this endpoint URL, including a list of values, see [Endpoint URL](https://{DomainName}/apidocs/toolchain#endpoint-url){: external}. |
| `{iam_api_key}` | Your IAM API key. |
| `{iam_token}` | A valid IAM bearer token. |
| `{new_tool_name}` | The new name of the tool integration. |
| `{new_tool_parameters}` | The unique key-value pairs that represent the parameters to use to update the tool integration. To view a list of parameters for each tool integration, see [Tool integrations](#integrations). |
| `{tool_id}` | The ID of the tool integration that you want to update. |
| `{toolchain_id}` | The ID of the toolchain where the tool integration exists. |
{: caption="Table 2. Variables for updating the tool integration with the API" caption-side="top"}

## Updating a tool integration with Terraform
{: #update_integration_terraform}
{: terraform}

If you configured a tool integration when you created a toolchain, you can update the configuration settings with Terraform.

1. Install the Terraform CLI and configure the {{site.data.keyword.cloud_notm}} provider plug-in for Terraform by following the tutorial for [Getting started with Terraform on {{site.data.keyword.cloud_notm}}](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started){: external}.
1. Use the Terraform configuration file that you used to create the tool integration. If your tool integration was not created with Terraform, run `terraform import` to avoid creating another tool integration. For more information about using this configuration language, see the [Terraform documentation](https://www.terraform.io/docs/language/index.html){: external}.

   The following example updates the name of an existing {{site.data.keyword.deliverypipeline}} tool integration by using the `ibm_cd_toolchain_tool_pipeline` resource, where `toolchain_id` is a GUID that represents the toolchain where the tool integration exists.  
   
   ```terraform
   data "ibm_cd_toolchain" "cd_toolchain" {
     toolchain_id = {toolchain_id}
   }
   
   resource "ibm_cd_toolchain_tool_pipeline" "cd_pipeline" {
     toolchain_id = data.ibm_cd_toolchain.cd_toolchain.id
     parameters {
       name = "myUpdatedPipelineName"
     }
   }
   ```
   {: codeblock}

   For more information about tool integration resources, see the full list of supported tool integration resources in the [{{site.data.keyword.cloud_notm}} Terraform Registry](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/cd_toolchain){: external}.

1. Initialize the Terraform CLI.

   ```terraform
   terraform init
   ```
   {: pre}
   
1. Create a Terraform execution plan. This plan summarizes all of the actions that must run to modify the tool integration.

   ```terraform
   terraform plan
   ```
   {: pre}

1. Apply the Terraform execution plan. Terraform takes all of the required actions to modify the tool integration.

   ```terraform
   terraform apply
   ```
   {: pre}

## Deleting a tool integration by using the console
{: #delete_integration_ui}
{: ui}

You can delete tool integrations from your toolchain by using the console. If you delete a tool integration from your toolchain, the deletion cannot be undone.

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**.
1. On the Toolchains page, click a toolchain to open its Overview page. Alternatively, on the App details page in your app, click the toolchain name.
1. On the tool integration that you want to delete, click the **Actions** icon ![Actions icon](../../icons/action-menu-icon.svg) **> Delete**.
1. Confirm by clicking **Delete**.

## Deleting a tool integration with the API
{: #delete_integration_api}
{: api}

You can delete tool integrations from your toolchain with the API. If you delete a tool integration from your toolchain, the deletion cannot be undone.

1. [Obtain an IAM bearer token](https://{DomainName}/apidocs/toolchain#authentication){: external}. Alternatively, if you are using an SDK, [obtain an IAM API key](https://{DomainName}/iam/apikeys){: external} and set the client options by using environment variables.
   
   ```bash
   export CD_TOOLCHAIN_AUTH_TYPE=iam
   export CD_TOOLCHAIN_APIKEY={iam_api_key}
   export CD_TOOLCHAIN_URL={base_url}
   ```
   {: pre}

2. [Look up the ID of the toolchain](https://{DomainName}/apidocs/toolchain#list-toolchains){: external} where the tool integration exists.
3. Using the ID of the toolchain, [look up the ID of the tool integration](https://{DomainName}/apidocs/toolchain#list-tools){: external}.
4. Delete the tool integration within the targeted toolchain.
   
   ```curl
   curl -X DELETE --location --header "Authorization: Bearer {iam_token}" \
     --header "Accept: application/json" \
     "{base_url}/toolchains/{toolchain_id}/tools/{tool_id}"
   ```
   {: pre}
   {: curl}

   ```javascript
   const CdToolchainV2 = require('ibm-continuous-delivery/cd-toolchain/v2');
   const toolchainService = CdToolchainV2.newInstance();
   ...
   (async() => {
      const response = await toolchainService.deleteTool({
         toolchainId: {tool_type_id},
         toolId: {tool_id}
      });
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
   deleteToolOptions := toolchainClient.NewDeleteToolOptions({tool_type_id}, {tool_id})
   response, err := toolchainClient.DeleteTool(deleteToolOptions)
   ```
   {: codeblock}
   {: go}

The following table lists and describes each of the variables that are used in the previous steps.   
    
| Variable | Description |
|:---------|:------------|
| `{base_url}` | The Toolchain API endpoint URL. For more information about this endpoint URL, including a list of values, see [Endpoint URL](https://{DomainName}/apidocs/toolchain#endpoint-url) for a list of values. |
| `{iam_api_key}` | Your IAM API key. |
| `{iam_token}` | A valid IAM bearer token. |
| `{tool_id}` | The ID of the tool integration that you want to update. |
| `{toolchain_id}` | The ID of the toolchain where the tool integration exists. |
{: caption="Table 3. Variables for deleting the tool integration with the API" caption-side="top"}

## Deleting a tool integration with Terraform
{: #delete_integration_terraform}
{: terraform}

You can delete tool integrations from your toolchain with Terraform. If you delete a tool integration from your toolchain, the deletion cannot be undone.

1. To install the Terraform CLI and configure the {{site.data.keyword.cloud_notm}} provider plug-in for Terraform, follow the tutorial for [Getting started with Terraform on {{site.data.keyword.cloud_notm}}](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started).
2. Use the Terraform configuration file that you used to create the tool integration. Comment or remove the tool integration resource from the configuration file.
3. Initialize the Terraform CLI.

   ```terraform
   terraform init
   ```
   {: pre}
   
4. Create a Terraform execution plan. This plan summarizes all of the actions that must run to delete the tool integration.

   ```terraform
   terraform plan
   ```
   {: pre}

5. Apply the Terraform execution plan. Terraform takes all of the required actions to delete the tool integration.

   ```terraform
   terraform apply
   ```
   {: pre}

## Tool integrations
{: #integrations}

The tool integrations that are available to you depend on the region of your toolchain and the availability of tool integrations in that region.

|Tool integration |Tool type ID |Regions	|Financial services validated|
|:----------|:----------|:------------------------------|:-----|
|[{{site.data.keyword.appconfig_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-app-configuration)		|appconfig |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[Artifactory](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-artifactory)		|artifactory |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[Bitbucket](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-bitbucket)		|bitbucketgit |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[{{site.data.keyword.deliverypipeline}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline) 		|pipeline |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London	   	| ![Checkmark icon](../icons/checkmark-icon.svg) 		|
|[{{site.data.keyword.deliverypipeline}} Private Worker](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-privateworker)			|private_worker |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Osaka, Sydney, London		|		|
|[{{site.data.keyword.DRA_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-dra)		|draservicebroker |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		| ![Checkmark icon](../icons/checkmark-icon.svg)			|
|[{{site.data.keyword.gitrepos}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-grit)	|hostedgit |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[GitHub](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-github)		|githubconsolidated |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[GitLab](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-gitlab)		|gitlab |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[HashiCorp Vault](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-hashicorpvault)		|hashicorpvault |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[Jenkins](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-jenkins)	|jenkins |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[JIRA](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-jira)		|jira |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[{{site.data.keyword.keymanagementserviceshort}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-keyprotect)		|keyprotect |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[Nexus](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-nexus)			|nexus |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[Other Tool](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-othertool)			|customtool |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[PagerDuty](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-pagerduty)			|pagerduty |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[Rational Team Concert](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-rationalteamconcert)		|rationalteamconcert |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[Sauce Labs](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-saucelabs)		|saucelabs |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[Secrets Manager](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-secretsmanager)		|secretsmanager |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[Security and Compliance Center](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-scc)		|security_compliance |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[Slack](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-slack)		|slack |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
|[SonarQube](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-sonarqube)			|sonarqube |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|		|
{: caption="Table 4. Tool integrations available for toolchains on {{site.data.keyword.cloud_notm}} Public" caption-side="top"}

If you want to start developing with your source code on {{site.data.keyword.cloud_notm}} Public, configure the GitHub tool integration or the {{site.data.keyword.gitrepos}} tool integration before you configure the {{site.data.keyword.deliverypipeline}}.
{: tip}
