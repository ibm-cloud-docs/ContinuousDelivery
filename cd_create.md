---

copyright:
  years: 2020, 2022

lastupdated: "2022-06-01"

keywords: ibmcloud, resource, service instance, create, IBM Cloud

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Creating a {{site.data.keyword.contdelivery_short}} service instance
{: #create_cd_service}
{: help} 
{: support}

You must have an {{site.data.keyword.contdelivery_full}} service instance before you can create and use toolchains that contain certain tool integrations. For more information about this limitation, see [Scope of a service instance](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#service_scope).
{: shortdesc}

After you create a {{site.data.keyword.contdelivery_short}} service instance by selecting it from the {{site.data.keyword.cloud_notm}} catalog, you can [create continuous delivery toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-getting-started).

You can have one active instance of {{site.data.keyword.contdelivery_short}} only in a region and resource group. For information about deleting an existing service instance, see [Deleting a {{site.data.keyword.contdelivery_short}} service instance](/docs/ContinuousDelivery?topic=ContinuousDelivery-delete_cd_service).
{: important}

1. Log in to [{{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/){: external}.
1. From the {{site.data.keyword.cloud_notm}} console, click **Catalog** and select **Services**.
1. Select the **Developer Tools** category.
1. Click the **{{site.data.keyword.contdelivery_short}}** tile.
1. Select the region that you want to create the {{site.data.keyword.contdelivery_short}} service in.
1. Choose a Lite or Professional pricing plan. Lite plans offer the full capabilities of {{site.data.keyword.contdelivery_short}} to small teams at no cost, with usage limits. If you create a Lite-plan instance, it is automatically deleted 30 days after creation. For more information about {{site.data.keyword.contdelivery_short}} service plans, see [Plan limitations and usage](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).
1. In the **Configure your resource** section, specify a name for the {{site.data.keyword.contdelivery_short}} instance that you are creating.
1. Select the resource group where you want to create the {{site.data.keyword.contdelivery_short}} service instance. You cannot change the selected resource group after you create the {{site.data.keyword.contdelivery_short}} service instance. For more information about how to organize resources in your {{site.data.keyword.cloud_notm}} account, see [Best practices for organizing resources in a resource group](/docs/account?topic=account-account_setup).
1. Specify the tags that you want to use to organize and filter the resources in your resource list. You can also use these tags to identify team usage or cost allocation. These tags are visible account wide. For more information about using tags, see [Working with tags](/docs/account?topic=account-tag).
1. If you chose a Professional pricing plan, you can select the instance of the {{site.data.keyword.keymanagementservicefull}} service and the root key that is used to encrypt your personal information. Make sure that the {{site.data.keyword.keymanagementserviceshort}} instance and the root key exist and the toolchain resources are authorized to access {{site.data.keyword.keymanagementserviceshort}} in the **Manage Authorizations** section.
1. Click **Create**.
