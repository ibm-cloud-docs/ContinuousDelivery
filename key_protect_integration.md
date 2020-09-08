---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-19"

keywords: tool integrations, IBM Cloud Public, IBM Cloud Dedicated, Key Protect

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
{:deprecated: .deprecated}
{:download: .download}   

# Configuring {{site.data.keyword.keymanagementserviceshort}}
{: #keyprotect}

{{site.data.keyword.keymanagementservicefull}} helps you to securely store and apply secrets for apps across {{site.data.keyword.cloud_notm}} services. To learn more about {{site.data.keyword.keymanagementserviceshort}}, see [Key types](/docs/key-protect?topic=key-protect-envelope-encryption#key-types).
{:shortdesc}

Before you create a {{site.data.keyword.keymanagementserviceshort}} tool integration, you must have an instance of the {{site.data.keyword.keymanagementserviceshort}} service provisioned in the region and resource group that you want to create the tool integration in. For instructions to provision an instance of the {{site.data.keyword.keymanagementserviceshort}} service, see [Provisioning the service](/docs/services/key-protect?topic=key-protect-provision).
{: important}

Configure {{site.data.keyword.keymanagementserviceshort}} to securely manage secrets, such as API keys, that are part of your  toolchain:

1. If you are configuring this tool integration as you are creating the toolchain, in the Configurable Integrations section, click **{{site.data.keyword.keymanagementserviceshort}}**.
1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.  

 a. Click **Add tool**.

 b. In the Tool Integrations section, click **{{site.data.keyword.keymanagementserviceshort}}**.

1. Specify a name for this instance of the {{site.data.keyword.keymanagementserviceshort}} tool integration to use in your toolchain.
1. Review the default values for **Region** and **Resource-Group** and update, if required.
1. Select the instance of the **{{site.data.keyword.keymanagementserviceshort}}** service that you want to use.
1. Click **Create Integration**.
1. From your toolchain, click **Key Protect**.

## Learn more about {{site.data.keyword.keymanagementserviceshort}}

To learn more about {{site.data.keyword.keymanagementserviceshort}}, see [About the service](/docs/services/key-protect?topic=key-protect-about).
