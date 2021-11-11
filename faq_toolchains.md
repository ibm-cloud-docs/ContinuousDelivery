---

copyright:
  years: 2015, 2020
lastupdated: "2020-07-30"

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

When you update the toolchain information directly from Cloud Foundry, it might take a few minutes for the {{site.data.keyword.contdelivery_short}} service to refresh and show your changes. For example, if you add or remove a user from a Cloud Foundry org, it might take a few minutes for {{site.data.keyword.contdelivery_short}} to discover that there is a new user and to allow that user to access the toolchain.


## I created a toolchain in a Cloud Foundry org, why does the Toolchains page show that a Continuous Delivery service is required?
{: #service_cloud_foundry}
{: faq}

When you create a toolchain in a resource group or org that does not have an instance of the {{site.data.keyword.contdelivery_short}} service, the toolchain platform attempts to automatically create an instance of the service by using the Lite plan. The error message indicates that the toolchain platform couldn't create the service instance.

This error might occur when you create a toolchain in the Dallas region and in a Cloud Foundry org that doesn't already have an instance of {{site.data.keyword.contdelivery_short}}. In the Dallas region, you must create all new instances of the {{site.data.keyword.contdelivery_short}} service in resource groups. 

You can either create the toolchain in a resource group or create the toolchain in an org that already has an instance of {{site.data.keyword.contdelivery_short}}.
  

## How do I move my toolchain from a Cloud Foundry org to a resource group?
{: #toolchain_move_to_resource_group}
{: faq}
{: support}

A feature to automatically migrate toolchains from a Cloud Foundry org to a resource group is not available yet. Instead, you can manually create the toolchain again in a resource group, and then remove the original toolchain from the Cloud Foundry org.


## How do I find my toolchain ID?
{: #find-toolchain-ID}
{: faq}

You can find your toolchain ID in the URL of your selected toolchain tool. For more information, see [Identifying your toolchain ID](/docs/ContinuousDelivery?topic=ContinuousDelivery-aggregating-multiple-sources). 
