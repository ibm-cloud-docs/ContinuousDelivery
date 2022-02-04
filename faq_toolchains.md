---

copyright:
  years: 2015, 2022
lastupdated: "2022-02-03"

keywords: tool integrations, error message, Lite plan, toolchains, Cloud Foundry orgs, resource groups, IBM Cloud

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:faq: data-hd-content-type='faq'}
{:support: data-reuse='support'}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}

# FAQs for toolchains
{: #faq_toolchains}

Get answers to frequently asked questions about using toolchains.
{: shortdesc} 


## Why does the Toolchains page show that the {{site.data.keyword.contdelivery_short}} service Lite plan is exceeded?
{: #plan_exceeded}
{: faq}
{: support}

{{site.data.keyword.contdelivery_short}} offers two plans: Lite and Professional. If you have the {{site.data.keyword.contdelivery_short}} Lite plan, you can use toolchains for free, up to the limits of the plan. The error message indicates that you exceeded one or more limits of the Lite plan. For example, you might exceed the plan if you have too many authorized users who are associated with the {{site.data.keyword.contdelivery_short}} service instance, or if you ran the maximum number of {{site.data.keyword.deliverypipeline}} jobs. For more information about the terms of your plan, see [Plan limitations and usage](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).


## I created a toolchain, why does the Toolchains page show that a Continuous Delivery service is required?
{: #service_required_resource_group}
{: faq}
{: support}

The terms of the plan for the {{site.data.keyword.contdelivery_short}} service instance that is in the same resource group or org as the toolchain manages the use of some of the tool integrations ({{site.data.keyword.deliverypipeline}}, Eclipse Orion {{site.data.keyword.webide}}, and {{site.data.keyword.gitrepos}}) that are contained in the service. The error message indicates that the resource group or org doesn't contain the required instance of the {{site.data.keyword.contdelivery_short}} service. For more information about the terms of your plan, see [Plan limitations and usage](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).


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


## I updated information for a toolchain from a Cloud Foundry org, why don't I see my changes in the toolchain?
{: #updates_in_cloud_foundry}
{: faq}
{: support}

Cloud Foundry Org-based {{site.data.keyword.contdelivery_short}} service instances and toolchains are deprecated. You can no longer create Cloud Foundry org-based {{site.data.keyword.contdelivery_short}} service instances. As of 14 January 2022, you cannot create new toolchains within Cloud Foundry orgs. You can create new toolchains in resource groups. As of 14 February 2022, all toolchains within Cloud Foundry orgs that do not contain a Professional plan instance of the {{site.data.keyword.contdelivery_short}} service will be deleted. As of 14 June 2022, all toolchains within Cloud Foundry orgs that contain a Professional plan instance of the {{site.data.keyword.contdelivery_short}} service will be deleted. Before these dates, you can use the [toolchain migration wizard](/docs/ContinuousDelivery?topic=ContinuousDelivery-migrate_toolchains) to migrate existing toolchains from Cloud Foundry orgs to resource groups.
{: deprecated}

When you update the toolchain information directly from Cloud Foundry, it might take a few minutes for the {{site.data.keyword.contdelivery_short}} service to refresh and show your changes. For example, if you add or remove a user from a Cloud Foundry org, it might take a few minutes for {{site.data.keyword.contdelivery_short}} to discover that there is a new user and to allow that user to access the toolchain.


## Why does the Toolchains page show that a Continuous Delivery service is required?
{: #service_cloud_foundry}
{: faq}
{: support}

Toolchains in a resource group or org must be accompanied by an instance of the {{site.data.keyword.contdelivery_short}} service in the same resource group or org. The error message indicates that neither the resource group or org contains an instance of the {{site.data.keyword.contdelivery_short}} service. For more information about this requirement, see [Plan limitations and usage](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).

If the toolchain is in a resource group, create an instance of the {{site.data.keyword.contdelivery_short}} service in the resource group. If the toolchain is in an org, migrate the toolchain to a resource group that has an instance of the {{site.data.keyword.contdelivery_short}} service. For more information about migrating toolchains, see [Migrating toolchains to a resource group](/docs/ContinuousDelivery?topic=ContinuousDelivery-migrate_toolchains).
  

## How do I move my toolchain from a Cloud Foundry org to a resource group?
{: #toolchain_move_to_resource_group}
{: faq}
{: support}

Go to the toolchain Overview page. A banner message appears indicating that the toolchain is eligible for migration. Click **migrate this toolchain** within the banner message to open the Migration wizard. The wizard guides you through the process of migrating your toolchain to a resource group. For more information about the migration process, see [Migrating toolchains to a resource group](/docs/ContinuousDelivery?topic=ContinuousDelivery-migrate_toolchains).


## How do I find my toolchain ID?
{: #find-toolchain-ID}
{: faq}
{: support}

You can find your toolchain ID in the URL of your selected toolchain tool. For more information, see [Identifying your toolchain ID](/docs/ContinuousDelivery?topic=ContinuousDelivery-aggregating-multiple-sources). 
