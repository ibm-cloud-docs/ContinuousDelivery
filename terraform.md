---

copyright:
  years: 2022, 2024
lastupdated: "2024-04-16"

keywords: Terraform, toolchains, Continuous Delivery

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Setting up Terraform for {{site.data.keyword.contdelivery_short}}
{: #terraform-setup}

Terraform on {{site.data.keyword.cloud}} enables predictable and consistent creation of {{site.data.keyword.cloud_notm}} services so that you can rapidly build complex, multitier cloud environments by following Infrastructure as Code (IaC) principles. Similar to using the {{site.data.keyword.cloud_notm}} CLI or API and SDKs, you can automate the creation, update, and deletion of your {{site.data.keyword.contdelivery_full}} instances by using the HashiCorp Configuration Language (HCL).
{: shortdesc}

Looking for a managed Terraform on {{site.data.keyword.cloud}} solution? Try out [{{site.data.keyword.bplong}}](/docs/schematics?topic=schematics-getting-started). With {{site.data.keyword.bpshort}}, you can use the Terraform scripting language that you are familiar with without worrying about setting up and maintaining the Terraform command line and the {{site.data.keyword.cloud}} Provider plug-in. {{site.data.keyword.bpshort}} also provides pre-defined Terraform templates that you can easily install from the {{site.data.keyword.cloud}} catalog.
{: tip}

## Installing Terraform and configuring resources for {{site.data.keyword.contdelivery_short}}
{: #install-terraform}

Before you begin, make sure that you have the [required access](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security) to create and work with `continuous-delivery` resources, and the [required access](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security) to create and work with `toolchain` resources.

1. Follow the [Terraform on {{site.data.keyword.cloud_notm}} getting started tutorial](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started) to install the Terraform CLI and configure the {{site.data.keyword.cloud_notm}} Provider plug-in for Terraform. The plug-in abstracts the {{site.data.keyword.cloud_notm}} APIs that are used to create, update, or delete `continuous-delivery` service instances and `toolchain` resources. 

2. Create a Terraform configuration file that is named `main.tf`. In this file, add the configuration to create a {{site.data.keyword.contdelivery_short}} service instance and to assign a user an access policy in Identity and Access Management (IAM) for that instance by using HCL. You also add the configuration to create a basic toolchain resource in the same resource group and region as the {{site.data.keyword.contdelivery_short}} service instance, and to assign a user an access policy in IAM for that resource. The toolchain and the {{site.data.keyword.contdelivery_short}} service instance that governs usage of the toolchain are in the same resource group and region. For more information about working with the Terraform configuration file, see the [Terraform documentation](https://developer.hashicorp.com/terraform/language){: external}. 

   The {{site.data.keyword.contdelivery_short}} service instance in the following example is named `my_cd`. It is created with the professional pricing plan in the `default` resource group and in the `us-south` region. The user `user1@ibm.com` is assigned the Manager role in the IAM access policy for the service instance.

   The toolchain resource is named `my_toolchain`. It is created in the `default` resource group and in the region that is specified in the `provider "ibm"` block in your `provider.tf` file. For this example, the `region` in `provider.tf` is set to `us-south`. The user `user2@ibm.com` is assigned the Editor role in the IAM access policy for the toolchain resource.

   ```terraform
   data "ibm_resource_group" "default_rg" {
     name = "default"
   }

   resource "ibm_resource_instance" "cd_instance" {
     name              = "my_cd"
     service           = "continuous-delivery"
     plan              = "professional"
     location          = "us-south"
     resource_group_id = data.ibm_resource_group.default_rg.id
   }

   resource "ibm_iam_user_policy" "cd_policy" {
     ibm_id = "user1@ibm.com"
     roles  = ["Manager"]
     resources {
       service              = "continuous-delivery"
       resource_instance_id = element(split(":", ibm_resource_instance.cd_instance.id), 7)
     }
   }

   resource "ibm_cd_toolchain" "toolchain_instance" {
     name              = "my_toolchain"
     resource_group_id = data.ibm_resource_group.default_rg.id
   }

   resource "ibm_iam_user_policy" "toolchain_policy" {
     ibm_id = "user2@ibm.com"
     roles  = ["Editor"]
     resources {
       service              = "toolchain"
       resource_instance_id = ibm_cd_toolchain.toolchain_instance.id
     }
   }
   ```
   {: codeblock}

3. Initialize the Terraform CLI. 

   ```terraform
   terraform init
   ```
   {: pre}

4. Create a Terraform execution plan. The Terraform execution plan summarizes all of the actions that you must run to create the {{site.data.keyword.contdelivery_short}} service instance, toolchain resource, and associated IAM access policies in your account.

   ```terraform
   terraform plan
   ```
   {: pre}

5. Create the {{site.data.keyword.contdelivery_short}} service instance, toolchain resource, and associated IAM access policies in your account in {{site.data.keyword.cloud_notm}}.

   ```terraform
   terraform apply
   ```
   {: pre}
   
6. From the [{{site.data.keyword.cloud_notm}} resource list](/resources){: external}, expand the Developer tools section, then select the {{site.data.keyword.contdelivery_short}} service instance that you created and note the instance ID.

7. Verify that the access policy is successfully assigned. For more information about assigning access policies, see [Reviewing assigned access in the console](/docs/account?topic=account-assign-access-resources#review-your-access-console&interface=ui).

8. From the [{{site.data.keyword.cloud_notm}} resource list](/resources){: external}, expand the Developer tools section, then select the toolchain resource that you created and note the instance ID.

9. Verify that the access policy is successfully assigned.

## What's next?
{: #terraform-setup-next}

Now that you successfully created your first {{site.data.keyword.contdelivery_short}} service instance and toolchain resource with Terraform on {{site.data.keyword.cloud_notm}}, you can choose between the following tasks:

- [Deleting a {{site.data.keyword.contdelivery_short}} service instance](/docs/ContinuousDelivery?topic=ContinuousDelivery-delete_cd_service)
- [Using toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using)
- [Configuring tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations)
- [Working with Tekton pipelines](/docs/ContinuousDelivery?topic=ContinuousDelivery-tekton-pipelines)
- [Working with Delivery Pipeline Private Workers](/docs/ContinuousDelivery?topic=ContinuousDelivery-private-workers)
- [Creating toolchains with Git](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_git)
- [Adding DevOps Insights to your toolchain](/docs/ContinuousDelivery?topic=ContinuousDelivery-add-devops-insights)
- [Managing personal data for {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_personal_data)

For more information about {{site.data.keyword.cloud_notm}} Provider resources and data sources, see the [Terraform Registry documentation](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs){: external}.
