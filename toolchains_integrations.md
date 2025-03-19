---

copyright:
  years: 2015, 2025
lastupdated: "2025-03-19"

keywords: tool integrations, IBM Cloud Public, App Configuration, Artifactory, Bitbucket, Delivery Pipeline, DevOps Insights, Delivery Pipeline Private Worker, Event Notifications, Git Repos and Issue Tracking, GitHub, GitLab, HashiCorp Vault, Jenkins, JIRA, IBM Key Protect, IBM Secrets Manager, Nexus, Custom Tool, PagerDuty, Rational Team Concert, Sauce Labs, Security and Compliance Center, Slack, SonarQube

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Working with tool integrations
{: #integrations}

You can add, update, and delete tool integrations by using the console, with the API, or with Terraform. You can configure tool integrations that support development, deployment, and operations tasks while you create an open toolchain, or you can add and configure tool integrations to customize an existing toolchain.
{: shortdesc}

## Understanding tool integrations with {{site.data.keyword.cloud_notm}} for Financial Services
{: #financial_services_validated}

Although the {{site.data.keyword.contdelivery_short}} and Toolchain services are designated as {{site.data.keyword.cloud_notm}} for Financial Services Validated, this designation does not apply to all of the tools that you can integrate into toolchains.

The following tools and tool integrations are *not* Financial Services Validated:

* The {{site.data.keyword.gitrepos}} component of the {{site.data.keyword.contdelivery_short}} service.
* Tool integrations for services in the {{site.data.keyword.cloud_notm}} catalog that are not designated as Financial Services Validated.
* Tool integrations for third-party, customer, or tools and services that are not owned and operated by {{site.data.keyword.cloud_notm}}.

For more information about which tools and tool integrations are Financial Services Validated, see [Tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations#tool_integrations).

For more information about {{site.data.keyword.cloud_notm}} for Financial Services, see [{{site.data.keyword.cloud_notm}} Framework for Financial Services](/docs/framework-financial-services).

The {{site.data.keyword.contdelivery_short}} service is Financial Services Validated in the same regions as {{site.data.keyword.cloud_notm}} for Financial Services. For more information about which multi-zone regions are designated as Financial Services Validated, see [Deploy your {{site.data.keyword.cloud_notm}} resources only to approved multizone regions](/docs/framework-financial-services?topic=framework-financial-services-about).
{: important}

## Adding a tool integration by using the console
{: #create_integration_ui}
{: ui}

You can add tool integrations to your toolchain by using the console.

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Toolchains**.
1. On the Toolchains page, click a toolchain to open its Overview page. Alternatively, on the App details page in your app, click the toolchain name.
1. To see a list of tool integrations to add, click **Add**.
1. Click a tool integration that you want to add.
1. Enter any required information to configure the tool integration.
1. Click **Create Integration** to add the tool integration to your toolchain.

## Adding a tool integration with the API
{: #create_integration_api}
{: api}

You can add tool integrations to your toolchain with the API.

1. [Obtain an IAM bearer token](https://{DomainName}/apidocs/toolchain#authentication){: external}. Alternatively, if you are using an SDK, [obtain an IAM API key](https://{DomainName}/iam/apikeys){: external} and set the client options by using environment variables.

   ```bash
   export CD_TOOLCHAIN_AUTH_TYPE=iam && \
   export CD_TOOLCHAIN_APIKEY={iam_api_key} && \
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
   const CdToolchainV2 = require('@ibm-cloud/continuous-delivery/cd-toolchain/v2');
   const toolchainService = CdToolchainV2.newInstance();
   ...
   (async() => {
      const toolPrototypeModel = {
         toolchainId: {toolchain_id},
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
   createToolOptions := toolchainClient.NewCreateToolOptions({toolchain_id}, {tool_type_id})
   createToolOptions.SetName({tool_name})
   createToolOptions.SetParameters({tool_parameters})
   tool, response, err := toolchainClient.CreateTool(createToolOptions)
   ```
   {: codeblock}
   {: go}

   ```python
   from ibm_continuous_delivery.cd_toolchain_v2 import CdToolchainV2
   ...
   toolchain_service = CdToolchainV2.new_instance()
   tool = toolchain_service.create_tool(
      name = {tool_name},
      toolchain_id = {toolchain_id},
      tool_type_id = {tool_type_id},
      parameters = {tool_parameters}
   )
   ```
   {: codeblock}
   {: python}

   ```java
   import com.ibm.cloud.continuous_delivery.cd_toolchain.v2.CdToolchain;
   import com.ibm.cloud.continuous_delivery.cd_toolchain.v2.model.*;
   ...
   CdToolchain toolchainService = CdToolchain.newInstance();
   CreateToolOptions createToolOptions = new CreateToolOptions.Builder()
      .name({tool_name})
      .parameters({tool_parameters})
      .toolchainId({toolchain_id})
      .toolTypeId({tool_type_id})
      .build();
   Response<ToolchainToolPost> response = toolchainService.createTool(createToolOptions).execute();
   ToolchainToolPost tool = response.getResult();
   ```
   {: codeblock}
   {: java}

The following table lists and describes each of the variables that are used in the previous steps.

| Variable | Description |
|:---------|:------------|
| `{base_url}` | The Toolchain API endpoint URL. For more information about supported values, see [Endpoint URL](https://{DomainName}/apidocs/toolchain#endpoint-url){: external}. |
| `{iam_api_key}` | Your IAM API key. |
| `{iam_token}` | A valid IAM bearer token. |
| `{tool_name}` | The name of the tool integration. |
| `{tool_parameters}` | Unique key-value pairs that represent the parameters to use to create the tool integration. For more information about the supported parameters for each tool integration, see [Tool integrations](#integrations). |
| `{tool_type_id}` | The unique, short name that represents the type of the tool integration. For a list of supported values, see [Tool integrations](#tool_integrations). |
| `{toolchain_id}` | The toolchain in which to create the tool integration. |
{: caption="Variables for provisioning the tool integration with the API" caption-side="top"}

## Adding a tool integration with Terraform
{: #create_integration_terraform}
{: terraform}

You can add tool integrations to your toolchain with Terraform.

1. To install the Terraform CLI and configure the {{site.data.keyword.cloud_notm}} provider plug-in for Terraform, follow the tutorial for [Getting started with Terraform on {{site.data.keyword.cloud}}](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started).
1. Create a Terraform configuration file that is named `main.tf`. In this file, add the configuration to create resource instances by using the HashiCorp Configuration Language (HCL). For more information about using this configuration language, see the [Terraform documentation](https://developer.hashicorp.com/terraform/language){: external}.

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

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Toolchains**.
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
   export CD_TOOLCHAIN_AUTH_TYPE=iam && \
   export CD_TOOLCHAIN_APIKEY={iam_api_key} && \
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
   const CdToolchainV2 = require('@ibm-cloud/continuous-delivery/cd-toolchain/v2');
   const toolchainService = CdToolchainV2.newInstance();
   ...
   (async() => {
      const toolPatchModel = {
         toolchainId: {toolchain_id},
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
   toolPatchModel := map[string]interface{}{
      "name": {new_tool_name},
      "parameters": {new_tool_parameters},
   }
   updateToolOptions := toolchainClient.NewUpdateToolOptions({toolchain_id}, {tool_id}, toolPatchModel)
   tool, response, err := toolchainClient.UpdateTool(updateToolOptions)
   ```
   {: codeblock}
   {: go}

   ```python
   from ibm_continuous_delivery.cd_toolchain_v2 import CdToolchainV2
   ...
   toolchain_service = CdToolchainV2.new_instance()
   tool = toolchain_service.update_tool(
      toolchain_id = {toolchain_id},
      tool_id = {tool_id},
      toolchain_tool_prototype_patch = {
         "name": {new_tool_name},
         "parameters": {new_tool_parameters}
      }
   )
   ```
   {: codeblock}
   {: python}

   ```java
   import com.ibm.cloud.continuous_delivery.cd_toolchain.v2.CdToolchain;
   import com.ibm.cloud.continuous_delivery.cd_toolchain.v2.model.*;
   ...
   CdToolchain toolchainService = CdToolchain.newInstance();
   HashMap<String,Object> toolchainToolPrototypePatch = new HashMap<>();
   toolchainToolPrototypePatch.put("name", {new_tool_name});
   toolchainToolPrototypePatch.put("parameters", {new_tool_parameters});
   UpdateToolOptions updateToolOptions = new UpdateToolOptions.Builder()
      .toolchainId({toolchain_id})
      .toolId({tool_id})
      .toolchainToolPrototypePatch(toolchainToolPrototypePatch)
      .build();
   Response<ToolchainToolPatch> response = toolchainService.updateTool(updateToolOptions).execute();
   ToolchainToolPatch tool = response.getResult();
   ```
   {: codeblock}
   {: java}

The following table lists and describes each of the variables that are used in the previous steps.

| Variable | Description |
|:---------|:------------|
| `{base_url}` | The Toolchain API endpoint URL, for example `https://api.us-south.devops.cloud.ibm.com/toolchain/v2`. For more information about this endpoint URL, including a list of values, see [Endpoint URL](https://{DomainName}/apidocs/toolchain#endpoint-url){: external}. |
| `{iam_api_key}` | Your IAM API key. |
| `{iam_token}` | A valid IAM bearer token. |
| `{new_tool_name}` | The new name of the tool integration. |
| `{new_tool_parameters}` | The unique key-value pairs that represent the parameters to use to update the tool integration. To view a list of parameters for each tool integration, see [Tool integrations](#integrations). |
| `{tool_id}` | The ID of the tool integration that you want to update. |
| `{toolchain_id}` | The ID of the toolchain where the tool integration exists. |
{: caption="Variables for updating the tool integration with the API" caption-side="top"}

## Updating a tool integration with Terraform
{: #update_integration_terraform}
{: terraform}

If you configured a tool integration when you created a toolchain, you can update the configuration settings with Terraform.

1. Install the Terraform CLI and configure the {{site.data.keyword.cloud_notm}} provider plug-in for Terraform by following the tutorial for [Getting started with Terraform on {{site.data.keyword.cloud_notm}}](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started){: external}.
1. Use the Terraform configuration file that you used to create the tool integration. If your tool integration was not created with Terraform, run `terraform import` to avoid creating another tool integration. For more information about using this configuration language, see the [Terraform documentation](https://developer.hashicorp.com/terraform/language){: external}.

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

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Toolchains**.
1. On the Toolchains page, click a toolchain to open its Overview page. Alternatively, on the App details page in your app, click the toolchain name.
1. On the tool integration that you want to delete, click the **Actions** icon ![Actions icon](../../icons/action-menu-icon.svg) **> Delete**.
1. Confirm by clicking **Delete**.

## Deleting a tool integration with the API
{: #delete_integration_api}
{: api}

You can delete tool integrations from your toolchain with the API. If you delete a tool integration from your toolchain, the deletion cannot be undone.

1. [Obtain an IAM bearer token](https://{DomainName}/apidocs/toolchain#authentication){: external}. Alternatively, if you are using an SDK, [obtain an IAM API key](https://{DomainName}/iam/apikeys){: external} and set the client options by using environment variables.

   ```bash
   export CD_TOOLCHAIN_AUTH_TYPE=iam && \
   export CD_TOOLCHAIN_APIKEY={iam_api_key} && \
   export CD_TOOLCHAIN_URL={base_url}
   ```
   {: pre}

2. [Look up the ID of the toolchain](https://{DomainName}/apidocs/toolchain#list-toolchains){: external} where the tool integration exists.
3. Using the ID of the toolchain, [look up the ID of the tool integration](https://{DomainName}/apidocs/toolchain#list-tools){: external}.
4. Delete the tool integration within the targeted toolchain.

   ```curl
   curl -X DELETE --location --header "Authorization: Bearer {iam_token}" \
     "{base_url}/toolchains/{toolchain_id}/tools/{tool_id}"
   ```
   {: pre}
   {: curl}

   ```javascript
   const CdToolchainV2 = require('@ibm-cloud/continuous-delivery/cd-toolchain/v2');
   const toolchainService = CdToolchainV2.newInstance();
   ...
   (async() => {
      const response = await toolchainService.deleteTool({
         toolchainId: {toolchain_id},
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
   deleteToolOptions := toolchainClient.NewDeleteToolOptions({toolchain_id}, {tool_id})
   response, err := toolchainClient.DeleteTool(deleteToolOptions)
   ```
   {: codeblock}
   {: go}

   ```python
   from ibm_continuous_delivery.cd_toolchain_v2 import CdToolchainV2
   ...
   toolchain_service = CdToolchainV2.new_instance()
   response = toolchain_service.delete_tool(
      toolchain_id = {toolchain_id},
      tool_id = {tool_id}
   )
   ```
   {: codeblock}
   {: python}

   ```java
   import com.ibm.cloud.continuous_delivery.cd_toolchain.v2.CdToolchain;
   import com.ibm.cloud.continuous_delivery.cd_toolchain.v2.model.*;
   ...
   CdToolchain toolchainService = CdToolchain.newInstance();
   DeleteToolOptions deleteToolOptions = new DeleteToolOptions.Builder()
      .toolchainId({toolchain_id})
      .toolId({tool_id})
      .build();
   Response<Void> response = toolchainService.deleteTool(deleteToolOptions).execute();
   ```
   {: codeblock}
   {: java}

The following table lists and describes each of the variables that are used in the previous steps.

| Variable | Description |
|:---------|:------------|
| `{base_url}` | The Toolchain API endpoint URL. For more information about this endpoint URL, including a list of values, see [Endpoint URL](https://{DomainName}/apidocs/toolchain#endpoint-url) for a list of values. |
| `{iam_api_key}` | Your IAM API key. |
| `{iam_token}` | A valid IAM bearer token. |
| `{tool_id}` | The ID of the tool integration that you want to delete. |
| `{toolchain_id}` | The ID of the toolchain where the tool integration exists. |
{: caption="Variables for deleting the tool integration with the API" caption-side="top"}

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
{: #tool_integrations}

The {{site.data.keyword.contdelivery_short}} service supports several tool integrations.

Although the {{site.data.keyword.contdelivery_short}} and Toolchain services are designated as {{site.data.keyword.cloud_notm}} for Financial Services Validated, this designation does not apply to all of the tools that you can integrate into toolchains. The following table indicates which tool integrations and tools are designated as {{site.data.keyword.cloud_notm}} for Financial Services Validated when they are used with {{site.data.keyword.contdelivery_short}} toolchains.
{: important}

If you are using the [{{site.data.keyword.contdelivery_short}} Toolchain API to create a tool integration](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, set the `tool_type_id` parameter in the API request to the **Tool type ID** value for the tool integration that is listed in the following table.
{: tip}

|Tool integration |Tool type ID |Financial services validated|
|:----------|:----------|:-----|
|[{{site.data.keyword.appconfig_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-app-configuration)		|appconfig |		|
|[Artifactory](/docs/ContinuousDelivery?topic=ContinuousDelivery-artifactory)		|artifactory |		|
|[Bitbucket](/docs/ContinuousDelivery?topic=ContinuousDelivery-bitbucket)		|bitbucketgit |		|
|[{{site.data.keyword.deliverypipeline}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline) 		|pipeline | ![Checkmark icon](../icons/checkmark-icon.svg) 		|
|[{{site.data.keyword.deliverypipeline}} Private Worker](/docs/ContinuousDelivery?topic=ContinuousDelivery-privateworker)			|private_worker |		|
|[{{site.data.keyword.DRA_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-dra)		|draservicebroker | ![Checkmark icon](../icons/checkmark-icon.svg)			|
|[{{site.data.keyword.en_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-event-notifications-integration)	|eventnotifications | ![Checkmark icon](../icons/checkmark-icon.svg)		|
|[{{site.data.keyword.gitrepos}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-grit)	|hostedgit |		|
|[{{site.data.keyword.cos_full_notm}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-cos_integration)|cloudobjectstorage	|		|
|[GitHub](/docs/ContinuousDelivery?topic=ContinuousDelivery-github)		|githubconsolidated |		|
|[GitLab](/docs/ContinuousDelivery?topic=ContinuousDelivery-gitlab)		|gitlab |		|
|[HashiCorp Vault](/docs/ContinuousDelivery?topic=ContinuousDelivery-hashicorpvault)		|hashicorpvault |		|
|[Jenkins](/docs/ContinuousDelivery?topic=ContinuousDelivery-jenkins)	|jenkins |		|
|[JIRA](/docs/ContinuousDelivery?topic=ContinuousDelivery-jira)		|jira |		|
|[{{site.data.keyword.keymanagementserviceshort}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-keyprotect)		|keyprotect |		|
|[Nexus](/docs/ContinuousDelivery?topic=ContinuousDelivery-nexus)			|nexus |		|
|[Other Tool](/docs/ContinuousDelivery?topic=ContinuousDelivery-othertool)			|customtool |		|
|[PagerDuty](/docs/ContinuousDelivery?topic=ContinuousDelivery-pagerduty)			|pagerduty |		|
|[Rational Team Concert](/docs/ContinuousDelivery?topic=ContinuousDelivery-rationalteamconcert)		|rationalteamconcert |		|
|[Sauce Labs](/docs/ContinuousDelivery?topic=ContinuousDelivery-saucelabs)		|saucelabs |		|
|[Secrets Manager](/docs/ContinuousDelivery?topic=ContinuousDelivery-secretsmanager)		|secretsmanager | ![Checkmark icon](../icons/checkmark-icon.svg)		|
|[Security and Compliance Center](/docs/ContinuousDelivery?topic=ContinuousDelivery-scc)		|security_compliance | ![Checkmark icon](../icons/checkmark-icon.svg)		|
|[Slack](/docs/ContinuousDelivery?topic=ContinuousDelivery-slack)		|slack |		|
|[SonarQube](/docs/ContinuousDelivery?topic=ContinuousDelivery-sonarqube)			|sonarqube |		|
{: caption="Tool integrations available for toolchains on {{site.data.keyword.cloud_notm}} Public" caption-side="top"}

If you want to start developing with your source code on {{site.data.keyword.cloud_notm}} Public, configure the GitHub tool integration or the {{site.data.keyword.gitrepos}} tool integration before you configure the {{site.data.keyword.deliverypipeline}}.
{: tip}
