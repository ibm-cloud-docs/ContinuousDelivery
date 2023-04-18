---

copyright:
  years: 2020, 2023

lastupdated: "2023-04-11"

keywords: ibmcloud, resource, service instance, create, IBM Cloud, Terraform

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Creating a {{site.data.keyword.contdelivery_short}} service instance
{: #create_cd_service}
{: help} 
{: support}

You must have an {{site.data.keyword.contdelivery_full}} service instance before you can create and use toolchains that contain certain tool integrations. For more information about this limitation, see [Scope of a service instance](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#service_scope).
{: shortdesc}

After you create a {{site.data.keyword.contdelivery_short}} service instance, you can [create continuous delivery toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-getting-started).

You can have one active instance of {{site.data.keyword.contdelivery_short}} only in a region and resource group. For information about deleting an existing service instance, see [Deleting a {{site.data.keyword.contdelivery_short}} service instance](/docs/ContinuousDelivery?topic=ContinuousDelivery-delete_cd_service).
{: important}

## Creating a {{site.data.keyword.contdelivery_short}} service instance by using the console
{: #create_cd_service_ui}
{: ui}

1. Log in to [{{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/){: external}.
1. From the {{site.data.keyword.cloud_notm}} console, click **Catalog** and select **Services**.
1. Select the **Developer Tools** category.
1. Click the **{{site.data.keyword.contdelivery_short}}** tile.
1. Select the region that you want to create the {{site.data.keyword.contdelivery_short}} service in.
1. Choose a Lite or Professional pricing plan. Lite plans offer the full capabilities of {{site.data.keyword.contdelivery_short}} to small teams at no cost, with usage limits. If you create a Lite-plan instance, it is automatically deleted 30 days after creation. For more information about {{site.data.keyword.contdelivery_short}} service plans, see [Plan limitations and usage](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).
1. In the **Configure your resource** section, specify a name for the {{site.data.keyword.contdelivery_short}} instance that you are creating.
1. Select the resource group where you want to create the {{site.data.keyword.contdelivery_short}} service instance. You cannot change the selected resource group after you create the {{site.data.keyword.contdelivery_short}} service instance. For more information about how to organize resources in your {{site.data.keyword.cloud_notm}} account, see [Best practices for organizing resources in a resource group](/docs/account?topic=account-account_setup).
1. Specify the tags that you want to use to organize and filter the resources in your resource list. You can also use these tags to identify team usage or cost allocation. These tags are visible account wide. For more information about using tags, see [Working with tags](/docs/account?topic=account-tag).
1. If you chose a Professional pricing plan, you can select the instance of the {{site.data.keyword.keymanagementservicefull}} service or the instance of the {{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}}, and the root key that is used to encrypt your personal information. Make sure that the {{site.data.keyword.keymanagementserviceshort}} instance or the {{site.data.keyword.hscrypto}} instance and the root key exist and the toolchain resources are authorized to access {{site.data.keyword.keymanagementserviceshort}} or {{site.data.keyword.hscrypto}} in the **Manage Authorizations** section. Only private endpoints are currently supported for the {{site.data.keyword.hscrypto}} service instance. For more information about what types of data are encrypted, see [Protecting your personal data when you use the Professional plan](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security#cd_professional_plan).
1. Click **Create**.

## Creating a {{site.data.keyword.contdelivery_short}} service instance from the CLI
{: #create_cd_service_cli}
{: cli}

1. Log in to {{site.data.keyword.cloud_notm}} by using the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli).

   ```sh
   ibmcloud login
   ```
   {: pre}

   If the login fails, run the `ibmcloud login --sso` command to try again. The `--sso` parameter is required when you log in with a federated ID. If you use this option, go to the link that is listed in the CLI output to generate a one-time passcode.
   {: tip}

2. Select the account, region, and resource group where you want to create a {{site.data.keyword.contdelivery_short}} service instance.

   ```sh
   ibmcloud target -c ACCOUNT -r REGION -g RESOURCE_GROUP
   ```
   {: pre}

3. Create an instance of {{site.data.keyword.contdelivery_short}} within the targeted account, region, and resource group.

   ```sh
   ibmcloud resource service-instance-create INSTANCE_NAME continuous-delivery PLAN REGION -p ENCRYPTION
   ```
   {: pre}

The following table lists and describes each of the variables that are used in the previous steps.

| Variable | Description |
|:---------|:------------|
| `ACCOUNT` | The name or ID of the account in which to provision the service instance. To find the names and IDs of the available accounts, run `ibmcloud account list`. |
| `ENCRYPTION` | Optional. To provision your service instance to use customer-managed encryption, append `-p '{"kms_info": {"id": <kms_instance_id>, "url": <kms_url>}, "kms_key": {"id": <kms_root_key_id>, "crn": <kms_transaction_crn>}}`. |
| `INSTANCE_NAME` | The name for your service instance. |
| `PLAN` | The name or ID of the pricing plan that you want to use. To find the names and IDs of the available plans, run `ibmcloud catalog service continuous-delivery`. |
| `REGION` | The region in which to provision the service instance. For example, `us-south`. |
| `RESOURCE_GROUP` | The name or ID of the resource group in which to provision the service instance. To find the names and IDs of the available resource groups, run `ibmcloud resource groups`. |
{: caption="Table 1. Variables for provisioning the {{site.data.keyword.contdelivery_short}} service from the CLI" caption-side="top"}

For more information about plan IDs or about how to update your service plan after you create an instance, see [Updating your service plan](/docs/billing-usage?topic=billing-usage-changing).

## Creating a {{site.data.keyword.contdelivery_short}} service instance with the API
{: #create_cd_service_api}
{: api}

1. [Obtain an IAM bearer token](https://{DomainName}/apidocs/resource-controller#authentication){: external}. Alternatively, if you are using an SDK, [obtain an IAM API key](https://{DomainName}/iam/apikeys){: external} and set the client options by using environment variables.
   
   ```bash
   export RESOURCE_CONTROLLER_APIKEY={iam_api_key}
   ```
   {: pre}

2. [Look up the ID of the resource group](https://{DomainName}/apidocs/resource-controller/resource-manager#list-resource-groups){: external} in which you want to create your instance.

3. Choose the region in which you want to create your instance.

4. [Look up the ID of the service plan](https://globalcatalog.cloud.ibm.com/search?q=continuous-delivery){: external} of the instance that you want to create.

5. Create an instance of {{site.data.keyword.contdelivery_short}} within the targeted account, region, and resource group.

   ```curl
   curl -X POST \
     https://resource-controller.cloud.ibm.com/v2/resource_instances \
     -H 'Authorization: Bearer {token}' \
     -H 'Content-Type: application/json' \
       -d '{
       "name": "{instance_name}",
       "target": "{region}",
       "resource_group": "{resource_group_id}",
       "resource_plan_id": "{plan_id}"
       "parameters": "{parameters}"
     }'
   ```
   {: pre}
   {: curl}

   ```java
   import com.ibm.cloud.platform_services.resource_controller.v2.ResourceController;
   import com.ibm.cloud.platform_services.resource_controller.v2.model.*;
   ...
   ResourceController resourceControllerService = ResourceController.newInstance();
   CreateResourceInstanceOptions createCdInstanceOptions = new CreateResourceInstanceOptions.Builder()
      .name({instance_name})
      .target({region})
      .resourceGroup({resource_group_id})
      .resourcePlanId({plan_id})
      .build();
   Response<ResourceInstance> response = resourceControllerService.createResourceInstance(createCdInstanceOptions).execute();
   ResourceInstance cdInstance = response.getResult();
   ```
   {: codeblock}
   {: java}

   ```javascript
   const ResourceControllerV2 = require('@ibm-cloud/platform-services/resource-controller/v2');
   const resourceControllerService = ResourceControllerV2.newInstance({});
   ...
   (async () => {
      const params = {
         name: {instance_name},
         target: {region},
         resourceGroup: {resource_group_id},
         resourcePlanId: {plan_id},
      };
      const res = await resourceControllerService.createResourceInstance(params);
      const cdInstanceGuid = res.result.guid;
   })();
   ```
   {: codeblock}
   {: node}

   ```python
   from ibm_platform_services import ResourceControllerV2
   ...
   resource_controller_service = ResourceControllerV2.new_instance()
   cd_instance = resource_controller_service.create_resource_instance(
      name={instance_name},
      target={region},
      resource_group={resource_group_id},
      resource_plan_id={plan_id}
   ).get_result()
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
   createCdInstanceOptions := resourceControllerService.NewCreateResourceInstanceOptions(
      {instance_name},
      {region},
      {resource_group_id},
      {plan_id},
   )
   cdInstance, response, err := resourceControllerService.CreateResourceInstance(createCdInstanceOptions)
   ```
   {: codeblock}
   {: go}

The following table lists and describes each of the variables that are used in the previous steps.   
    
| Variable | Description |
|:---------|:------------|
| `{iam_api_key}` | Your IAM API key. |
| `{instance_name}` | A name for your service instance. |
| `{parameters}` | To provision your service instance to use customer-managed encryption, pass the following parameters: `'{"kms_info": {"id": <kms_instance_id>, "url": <kms_url>}, "kms_key": {"id": <kms_root_key_id>, "crn": <kms_transaction_crn>}}`. |
| `{plan_id}` | The ID of the pricing plan that you want to use. |
| `{region}` | The region in which to provision the service instance. For example, `us-south`. |
| `{resource_group_id}` | The ID of the resource group in which to provision the service instance. To find the IDs of the available resource groups, run `ibmcloud resource groups`. |
| `{token}` | A valid IAM bearer token. |
{: caption="Table 2. Variables for provisioning the {{site.data.keyword.contdelivery_short}} service with the API" caption-side="top"}

For more information about creating service instances, see [Creating new resource instances by using the API](/docs/account?topic=account-manage_resource&interface=api&code=curl#create-resource-instance-api).

## Creating a {{site.data.keyword.contdelivery_short}} service instance with Terraform
{: #create_cd_service_terraform}
{: terraform}

1. To install the Terraform CLI and configure the {{site.data.keyword.cloud_notm}} provider plug-in for Terraform, follow the tutorial for [Getting started with Terraform on {{site.data.keyword.cloud_notm}}](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started).

2. Create a Terraform configuration file that is named `main.tf`. In this file, add the configuration to create resource instances by using the HashiCorp Configuration Language. For more information about using this configuration language, see the [Terraform documentation](https://www.terraform.io/docs/language/index.html){: external}.

   The following example creates a {{site.data.keyword.contdelivery_short}} service instance by using the `ibm_resource_instance` resource, where `name` is a unique, descriptive name that identifies the resource instance.  
  
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

   For more information about `ibm_resource_instance`, see the argument reference details in the [Terraform Registry Documentation](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/resource_instance){: external}.
   
   To provision your service instance to use customer-managed encryption, add and populate the parameters attribute with your key management service instance ID and root key ID.
   
   ```terraform
     parameters = {
       kms_instance = <kms_instance_id>
       kms_key = <kms_key>
     }
   ```
   {: codeblock}
  
3. Initialize the Terraform CLI.

   ```terraform
   terraform init
   ```
   {: pre}
   
4. Create a Terraform execution plan. This plan summarizes all of the actions that must be run to create a {{site.data.keyword.contdelivery_short}} service instance.

   ```terraform
   terraform plan
   ```
   {: pre}

5. Apply the Terraform execution plan. Terraform takes all of the required actions to create the {{site.data.keyword.contdelivery_short}} service instance.

   ```terraform
   terraform apply
   ```
   {: pre}
