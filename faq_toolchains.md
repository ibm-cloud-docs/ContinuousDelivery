---

copyright:
  years: 2015, 2024
lastupdated: "2024-04-15"

keywords: tool integrations, error message, Lite plan, toolchains, resource groups, IBM Cloud

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# FAQs for toolchains
{: #faq_toolchains}

Get answers to frequently asked questions about using toolchains.
{: shortdesc} 


## Why does the Toolchains page show that the {{site.data.keyword.contdelivery_short}} service Lite plan is exceeded?
{: #plan_exceeded}
{: faq}
{: support}

{{site.data.keyword.contdelivery_short}} offers two plans: Lite and Professional. If you have the {{site.data.keyword.contdelivery_short}} Lite plan, you can use toolchains for free, up to the limits of the plan. The error message indicates that you exceeded one or more limits of the Lite plan. For example, you might exceed the plan if you have too many authorized users who are associated with the {{site.data.keyword.contdelivery_short}} service instance, or if you ran the maximum number of {{site.data.keyword.deliverypipeline}} jobs. For more information about the terms of your plan, see [Plan limitations and usage](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).


## I created a toolchain, why does the Toolchains page show that a Continuous Delivery service is required?
{: #service_required_resource_group}
{: faq}
{: support}

The terms of the plan for the {{site.data.keyword.contdelivery_short}} service instance that is in the same resource group as the toolchain manages the use of some of the tool integrations ({{site.data.keyword.deliverypipeline}} and {{site.data.keyword.gitrepos}}) that are contained in the service. The error message indicates that the resource group doesn't contain the required instance of the {{site.data.keyword.contdelivery_short}} service. For more information about the terms of your plan, see [Plan limitations and usage](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).


## Can I create a toolchain instance from a template programmatically?
{: #toolchain_create_prog}
{: faq}
{: support}

You can directly call the toolchain creation page endpoint to pass all of the parameter values. For more information about these parameters, see [Toolchain Creation Page Parameters](https://github.com/open-toolchain/sdk/wiki/Toolchain-Creation-page-parameters){: external}.


## Do I need a separate toolchain instance for each piece of work that my team owns?
{: #toolchain_separate_instance}
{: faq}
{: support}

You can define multiple pipelines within a single toolchain. However, if these pieces of work are unrelated and only share a definition repo, you can create them in separate toolchains so that you can administer them separately.


## Can I create a toolchain template and then use it to create a toolchain for each piece of work that my team owns?
{: #toolchain_template_create}
{: faq}
{: support}

Creating a custom template is more work, but it ensures that all of your toolchains have the same structure. By using a template, you can quickly add toolchains in the future. If you’re creating only a few toolchains and a standard template exists that is similar to what you need, use that template and customize your toolchains after they are created.


## I created a toolchain template that specified a particular tag and then created toolchains from that template. If I edit my template to change the tag are my toolchains updated with that tag?
{: #toolchain_template_tag}
{: faq}
{: support}

Because the template doesn't link to the toolchains that were created from it, toolchains that were created from the original template are not updated with the new tag.


## Why does the Toolchains page show that a Continuous Delivery service is required?
{: #service_cloud_foundry}
{: faq}
{: support}

Toolchains in a resource group must be accompanied by an instance of the {{site.data.keyword.contdelivery_short}} service in the same resource group. The error message indicates that the resource group does not contain an instance of the {{site.data.keyword.contdelivery_short}} service. To resolve this error, create an instance of the {{site.data.keyword.contdelivery_short}} service in the resource group. For more information about this requirement, see [Plan limitations and usage](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).


## How do I find my toolchain ID?
{: #find-toolchain-id}
{: faq}
{: support}

You can find your toolchain ID in the URL of your selected toolchain tool. For more information, see [Identifying your toolchain ID](/docs/ContinuousDelivery?topic=ContinuousDelivery-aggregating-multiple-sources). 


## Can I manage toolchains by using Terraform?
{: #manage_toolchains_terraform}
{: faq}
{: support}

You can use Terraform to create, read, update, and delete toolchains and tool integrations. For more information about using Terraform with toolchains, see [Creating a toolchain with Terraform](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started&interface=terraform#creating_a_toolchain_terraform), [Deleting a toolchain with Terraform](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using&interface=terraform#deleting_a_toolchain_terraform), [Working with tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations&interface=terraform), and the [`ibm_cd_toolchain` resources documentation](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/cd_toolchain){: external}.


## Can I manage toolchains by using an API?
{: #manage_toolchains_api}
{: faq}
{: support}

You can use HTTP APIs or selected programming language SDKs to create, read, update, and delete toolchains and tool integrations. For more information about using toolchains and tool integrations with the API, see [Creating a toolchain with the API](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started&interface=api#creating_a_toolchain_api), [Deleting a toolchain with the API](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using&interface=api#deleting_a_toolchain_api), [Working with tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations&interface=api), and the [CD Toolchain API docs](https://cloud.ibm.com/apidocs/toolchain){: external}.


## Can I use the console, APIs, or CLI to modify resources that are managed by Terraform?
{: #toolchains_resource_drift}
{: faq}
{: support}

When you use Terraform to manage resources such as {{site.data.keyword.contdelivery_short}} service instances, toolchains, and Tekton pipelines, avoid changing the resources by using the console, APIs, or CLI, or by any other method outside of Terraform's control.

If you circumvent Terraform by directly changing resources, you might cause [resource drift](https://developer.hashicorp.com/terraform/tutorials/state/resource-drift){: external}, a situation in which the states of your actual resources on {{site.data.keyword.cloud_notm}} deviate from the definition of the resources in Terraform. The next time that you apply the Terraform configuration, Terraform attempts to update your resources to align them with the Terraform configuration. This action might lead to unintended consequences, such as reverting changes or deleting and then re-creating resources.

For more information about resource drift, see [Manage Resource Drift](https://developer.hashicorp.com/terraform/tutorials/state/resource-drift){: external}.
