---

copyright:
  years: 2020, 2023

lastupdated: "2023-02-07"

keywords: ibmcloud, resource, service instance, restore, CLI tool, IBM Cloud

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Deleting a {{site.data.keyword.contdelivery_short}} service instance
{: #delete_cd_service}
{: help} 
{: support}

You can delete resource group-based {{site.data.keyword.contdelivery_short}} service instances.
{: shortdesc}

To delete a {{site.data.keyword.contdelivery_short}} service instance, you must have either the Administrator or Editor user permissions.

Deleting an instance of the {{site.data.keyword.contdelivery_short}} service impacts your ability to use tool integrations within toolchains that are contained in the same region and resource group as the deleted service instance. For more information about this limitation, see [Plan limitations and usage](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).
{: important}

## Deleting a {{site.data.keyword.contdelivery_short}} service instance by using the console
{: #deleting_rg_console}
{: ui}

1. Log in to [{{site.data.keyword.cloud_notm}}](http://cloud.ibm.com){: external}.
1. Go to the [Resource list](https://cloud.ibm.com/resources){: external} for your {{site.data.keyword.cloud_notm}} account.
1. In the **Services** section, locate the active {{site.data.keyword.contdelivery_short}} service instance.
1. From the {{site.data.keyword.contdelivery_short}} service instance's **Actions** ![Overflow icon](images/overflow-icon-2.svg) menu, click **Delete**.
1. Click **Delete** to confirm that you want to delete the {{site.data.keyword.contdelivery_short}} service.

## Deleting a {{site.data.keyword.contdelivery_short}} service instance from the CLI
{: #deleting_rg_cli}
{: cli}

1. Log in to {{site.data.keyword.cloud_notm}} by using the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli).

   ```sh
   ibmcloud login
   ```
   {: pre}

   If the login fails, run the `ibmcloud login --sso` command to try again. The `--sso` parameter is required when you log in with a federated ID. If you use this option, go to the link that is listed in the CLI output to generate a one-time passcode.
   {: tip}

2. Optional. List all of the {{site.data.keyword.contdelivery_short}} service instances in the targeted account to identify the instance that you want to delete.

   ```sh
   ibmcloud resource service-instances --all-resource-groups --service-name continuous-delivery
   ```
   {: pre}

3. Delete a service instance by running the [`ibmcloud resource service-instance-delete`](/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_delete) command.

   ```sh
   ibmcloud resource service-instance-delete SERVICE_NAME_OR_ID
   ```
   {: pre}

The following table lists and describes each of the variables that are used in the previous steps.

| Variable | Description |
|:---------|:------------|
| `SERVICE_NAME_OR_ID` | The name or ID of the {{site.data.keyword.contdelivery_short}} service instance that you want to delete. |
{: caption="Table 1. Variables for deleting the {{site.data.keyword.contdelivery_short}} service from the CLI" caption-side="top"}

## Deleting a {{site.data.keyword.contdelivery_short}} service instance with the API
{: #deleting_rg_api}
{: api}

1. [Obtain an IAM bearer token](https://{DomainName}/apidocs/resource-controller#authentication){: external}. Alternatively, if you are using an SDK, [obtain an IAM API key](https://{DomainName}/iam/apikeys){: external} and set the client options by using environment variables. 
   
   ```bash
   export RESOURCE_CONTROLLER_APIKEY={iam_api_key}
   ```
   {: pre}

2. Delete the instance of the {{site.data.keyword.contdelivery_short}} service instance that you want to remove.

   ```curl
   curl -X DELETE \
     https://resource-controller.cloud.ibm.com/v2/resource_instances/{instance_id} \
     -H 'Authorization: Bearer {token}'
   ```
   {: pre}
   {: curl}

   ```java
   import com.ibm.cloud.platform_services.resource_controller.v2.ResourceController;
   import com.ibm.cloud.platform_services.resource_controller.v2.model.*;
   ...
   ResourceController resourceControllerService = ResourceController.newInstance();
   DeleteResourceInstanceOptions deleteCdInstanceOptions = new DeleteResourceInstanceOptions.Builder()
      .id({instance_id})
      .recursive(false)
      .build();
   Response<Void> response = resourceControllerService.deleteResourceInstance(deleteCdInstanceOptions).execute();
   ```
   {: codeblock}
   {: java}

   ```javascript
   const ResourceControllerV2 = require('@ibm-cloud/platform-services/resource-controller/v2');
   const resourceControllerService = ResourceControllerV2.newInstance({});
   ...
   (async() => {
      const params = {
         id: {instance_id},
         recursive: false,
      };
      await resourceControllerService.deleteResourceInstance(params);
   })();
   ```
   {: codeblock}
   {: node}

   ```python
   from ibm_platform_services import ResourceControllerV2
   ...
   resource_controller_service = ResourceControllerV2.new_instance()
   response = resource_controller_service.delete_resource_instance(
      id={instance_id},
      recursive=False
   )
   ```
   {: codeblock}
   {: python}

   ```go
   import {
      "github.com/IBM/platform-services-go-sdk/resourcecontrollerv2"
   }
   ...
   resourceControllerServiceOptions := &resourcecontrollerv2.ResourceControllerV2Options{}
   resourceControllerService, err := resourcecontrollerv2.NewResourceControllerV2UsingExternalConfig(resourceControllerServiceOptions)
   deleteCdInstanceOptions := resourceControllerService.NewDeleteResourceInstanceOptions(
      {instance_id},
   )
   deleteCdInstanceOptions.SetRecursive(false)
   response, err := resourceControllerService.DeleteResourceInstance(deleteCdInstanceOptions)
   ```
   {: codeblock}
   {: go}

The following table lists and describes each of the variables that are used in the previous steps.   
    
| Variable | Description |
|:---------|:------------|
| `{iam_api_key}` | Your IAM API key. |
| `{instance_id}` | The ID of the {{site.data.keyword.contdelivery_short}} service instance that you want to delete. |
| `{token}` | A valid IAM bearer token. |
{: caption="Table 2. Variables for deleting the {{site.data.keyword.contdelivery_short}} service with the API" caption-side="top"}

For more information about deleting service instances, see [Deleting resource instances by using the API](/docs/account?topic=account-delete-resource&interface=api#delete-resource-instance-api).

## Deleting a {{site.data.keyword.contdelivery_short}} service instance with Terraform
{: #deleting_rg_terraform}
{: terraform}

1. Locate the Terraform file (for example, `main.tf`) that contains the `resource` block for the existing service instance. For more information about using Terraform with {{site.data.keyword.contdelivery_short}}, see [Creating a {{site.data.keyword.contdelivery_short}} service instance with Terraform](/docs/ContinuousDelivery?topic=ContinuousDelivery-create_cd_service&interface=terraform#create_cd_service_terraform).

   The `resource` in the following example describes an existing {{site.data.keyword.contdelivery_short}} service instance.

   ```terraform
   data "ibm_resource_group" "group" {
     name = "default"
   }

   resource "ibm_resource_instance" "cd_service_instance" {
     name              = "my CD service instance"
     service           = "continuous-delivery"
     plan              = "lite"
     location          = "us-south"
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
   
4. Create a Terraform execution plan. This plan summarizes all of the actions that must be run to delete the {{site.data.keyword.contdelivery_short}} service instance.

   ```terraform
   terraform plan
   ```
   {: pre}

5. Apply the Terraform execution plan. Terraform takes all of the required actions to delete the {{site.data.keyword.contdelivery_short}} service instance.

   ```terraform
   terraform apply
   ```
   {: pre}

## Restoring a deleted service instance
{: #restoring_cd_instance}

After you delete an instance of the {{site.data.keyword.contdelivery_short}} service, you can restore the deleted service instance within the data retention period of seven days. After the seven-day period expires, the service instance is permanently deleted. 

To view which service instances are available for restoration and to restore a deleted service, see [Using resource reclamations](/docs/account?topic=account-resource-reclamation). If you try to restore a deleted service and an active {{site.data.keyword.contdelivery_short}} service instance exists, the restoration is blocked. For more information about how to view the details for a resource reclamation, see [Listing reclaimed resources by using the CLI](/docs/account?topic=account-resource-reclamation&interface=cli) or [Listing reclaimed resources by using the API](/docs/account?topic=account-resource-reclamation&interface=api).

You can have one active instance of {{site.data.keyword.contdelivery_short}} only in a region and resource group. After you delete an instance of the {{site.data.keyword.contdelivery_short}} service from a region and resource group, you can restore the deleted service instance to create a service instance again within the data retention period of seven days.
