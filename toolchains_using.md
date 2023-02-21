---

copyright:
  years: 2015, 2023
lastupdated: "2023-02-16"

keywords: user management function, toolchains, tool integrations, user access

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Using toolchains
{: #toolchains-using}

Open toolchains are available on {{site.data.keyword.cloud}}. You can use a toolchain to be productive in your daily development, deployment, and operations work. After you set up a toolchain, you can add, delete, or configure tool integrations and manage access to the toolchain. For more information about working with tool integrations, see [Working with tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations).
{: shortdesc}

## Managing access to toolchains
{: #managing_access_resource_groups}

You can use the Identity and Access Management (IAM) service to manage user access to toolchains in resource groups. For more information about managing access control with IAM, see [Managing user access to toolchains in resource groups](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security).

Users with access to toolchains might be counted as authorized users of the {{site.data.keyword.contdelivery_full}} service. For more information about how authorized users are counted, see [Plan limitations and usage](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).

## Organizing toolchains
{: #organizing_toolchains}

You can add tags to your toolchains to organize them and easily find them later. A tag is a label that you assign to a toolchain for easy filtering of toolchains in your toolchains list.

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. 
1. On the Toolchains page, locate the toolchain that you want to add a tag to and click **Add tags**.
1. Enter a name for the tag that you want to add to the toolchain. You can add multiple tags, which are separated by commas.
1. Click **Save**.

For more information about tags, see [Working with tags](/docs/account?topic=account-tag).

## Viewing toolchain connections to apps, clusters, and services
{: #view_toolchain_connections}

You can view your toolchain's connections to Kubernetes clusters and services.

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. 
1. On the Toolchains page, click a toolchain to open its Overview page. Alternatively, on the App details page in your app, click the toolchain name.
1. Select the **Connections** tab, and select the app, cluster, or service that you want to view.


## Deleting a toolchain
{: #deleting_a_toolchain}

You can delete a toolchain. When you delete a toolchain, all of the tool integrations that belong to that toolchain are also deleted. The deletion cannot be undone.

When you delete a {{site.data.keyword.deliverypipeline}} tool integration, the associated {{site.data.keyword.deliverypipeline}} is also deleted.
{: tip}

When you delete a GitHub or {{site.data.keyword.gitrepos}} tool integration, the associated repo is not deleted from GitHub or {{site.data.keyword.gitrepos}}. You must manually remove the repo.
{: tip}

### Deleting a toolchain by using the console
{: #deleting_a_toolchain_ui}
{: ui}

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. 
1. On the Toolchains page, click a toolchain to open its Overview page. Alternatively, on the App details page in your app, click the toolchain name.
1. Click the **Actions** menu and select **Delete**. Deleting a toolchain removes all of its tool integrations, which might delete resources that are managed by those integrations.
1. Confirm the deletion by typing the name of the toolchain and clicking **Delete**.

### Deleting a toolchain from the CLI (Beta)
{: #deleting_a_toolchain_cli}
{: cli}

1. Log in to {{site.data.keyword.cloud_notm}} by using the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli).

   ```sh
   ibmcloud login
   ```
   {: pre}

   If the login fails, run the `ibmcloud login --sso` command to try again. The `--sso` parameter is required when you log in with a federated ID. If you use this option, go to the link that is listed in the CLI output to generate a one-time passcode.
   {: tip}

2. Optional. List all of the toolchains in the targeted account, region, and resource group to identify the instance that you want to delete.

   ```sh
   ibmcloud dev toolchains
   ```
   {: pre}

3. Delete a toolchain by running the [`ibmcloud dev toolchain-delete`](/docs/ContinuousDelivery?topic=cli-idt-cli#toolchain-delete) command.

   ```sh
   ibmcloud dev toolchain-delete TOOLCHAIN-NAME
   ```
   {: pre}

The following table lists and describes each of the variables that are used in the previous steps.

| Variable | Description |
|:---------|:------------|
| `TOOLCHAIN_NAME` | The name of the toolchain that you want to delete. |
{: caption="Table 1. Variables for deleting the toolchain from the CLI" caption-side="top"}

### Deleting a toolchain with the API
{: #deleting_a_toolchain_api}
{: api}

1. [Obtain an IAM bearer token](https://{DomainName}/apidocs/toolchain#authentication){: external}. Alternatively, if you are using an SDK, [obtain an IAM API key](https://{DomainName}/iam/apikeys){: external} and set the client options by using environment variables.
   
   ```bash
   export CD_TOOLCHAIN_AUTH_TYPE=iam && \
   export CD_TOOLCHAIN_APIKEY={iam_api_key} && \
   export CD_TOOLCHAIN_URL={base_url}
   ```
   {: pre}

2. Delete the toolchain that you want to remove.

   ```curl
   curl -X DELETE \
     "{base_url}/toolchains/{toolchain_id}" \
     -H 'Authorization: Bearer {token}'
   ```
   {: pre}
   {: curl}

   ```javascript
   const CdToolchainV2 = require('@ibm-cloud/continuous-delivery/cd-toolchain/v2');
   const toolchainService = CdToolchainV2.newInstance();
   ...
   (async() => {
      const response = await toolchainService.deleteToolchain({
         toolchainId: {toolchain_id}
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
   deleteToolchainOptions := toolchainClient.NewDeleteToolchainOptions({toolchain_id})
   response, err := toolchainClient.DeleteToolchain(deleteToolchainOptions)
   ```
   {: codeblock}
   {: go}

   ```python
   from ibm_continuous_delivery.cd_toolchain_v2 import CdToolchainV2
   ...
   toolchain_service = CdToolchainV2.new_instance()
   response = toolchain_service.delete_toolchain(
      toolchain_id = toolchain_id
   )
   ```
   {: codeblock}
   {: python}

   ```java
   import com.ibm.cloud.continuous_delivery.cd_toolchain.v2.CdToolchain;
   import com.ibm.cloud.continuous_delivery.cd_toolchain.v2.model.*;
   ...
   CdToolchain toolchainService = CdToolchain.newInstance();
   DeleteToolchainOptions deleteToolchainOptions = new DeleteToolchainOptions.Builder()
      .toolchainId({toolchain_id})
      .build();
   Response<Void> response = toolchainService.deleteToolchain(deleteToolchainOptions).execute();
   ```
   {: codeblock}
   {: java}

The following table lists and describes each of the variables that are used in the previous steps.   
    
| Variable | Description |
|:---------|:------------|
| `{base_url}` | The Toolchain API endpoint URL, for example `https://api.us-south.devops.cloud.ibm.com/toolchain/v2`. For more information about this endpoint URL, including a list of values, see [Endpoint URL](https://{DomainName}/apidocs/toolchain#endpoint-url){: external}. |
| `{iam_api_key}` | Your IAM API key. |
| `{token}` | A valid IAM bearer token. |
| `{toolchain_id}` | The ID of the toolchain that you want to delete. |
{: caption="Table 2. Variables for deleting the toolchain with the API" caption-side="top"}

### Deleting a toolchain with Terraform
{: #deleting_a_toolchain_terraform}
{: terraform}

1. Locate the Terraform file (for example, `main.tf`) that contains the `resource` block for the existing toolchain. For more information about using Terraform with toolchains, see [Creating a toolchain with Terraform](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started&interface=terraform).

   The `resource` in the following example describes an existing toolchain.

   ```terraform
   data "ibm_resource_group" "group" {
     name = "default"
   }

   resource "ibm_cd_toolchain" "cd_toolchain" {
     name              = "my toolchain"
     resource_group_id = data.ibm_resource_group.group.id
   }
   ```
   {: codeblock}

2. Remove the `resource` block from your Terraform file.

3. Initialize the Terraform CLI.

   ```terraform
   terraform init
   ```
   {: pre}
   
4. Create a Terraform execution plan. This plan summarizes all of the actions that must run to delete the toolchain.

   ```terraform
   terraform plan
   ```
   {: pre}

5. Apply the Terraform execution plan. Terraform takes all of the required actions to delete the toolchain.

   ```terraform
   terraform apply
   ```
   {: pre}

## Take a tutorial: Using toolchains
{: #toolchain-tutorial}

Try the [Add a toolchain to an app](https://www.ibm.com/cloud/architecture/tutorials/add-a-toolchain-to-an-app?task=2){: external} tutorial on the [{{site.data.keyword.cloud_notm}} Garage Method](https://www.ibm.com/garage/method){: external}.
