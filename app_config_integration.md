---

copyright:
  years: 2022
lastupdated: "2022-02-18"

keywords: tool integrations, IBM Cloud Public, App Configuraton, AppConfig

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

# Configuring {{site.data.keyword.appconfig_short}}
{: #app-configuration}

[{{site.data.keyword.appconfig_full}}](/docs/app-configuration?topic=app-configuration-getting-started) is a centralized feature management and configuration service that provides a convenient, consistent, and secure approach to accessing, referencing, and reusing collections of feature flags and properties within toolchains.
{: shortdesc}

You can configure an {{site.data.keyword.appconfig_short}} instance by using the {{site.data.keyword.appconfig_short}} service instance dashboard to add and manage specific environments and collections that contain sets of feature flags and properties. You can further refine the use of feature flags and properties by specifying target segments that evaluate based on user attributes and rules.

You can also add an {{site.data.keyword.appconfig_short}} tool integration to a toolchain and apply specific feature flags or properties from the service instance to the environment or trigger properties of the associated pipeline. You can repeat this process across multiple toolchains by using {{site.data.keyword.appconfig_short}} service instances, as required. For example, you can use a service instance to centrally store and manage all of the feature flags and properties that are required by toolchains across several environments.

When you apply feature flags or properties to a toolchain, special {{site.data.keyword.appconfig_short}} feature flag and property references are saved within the toolchain instead of in the literal values. This feature supports centralized management of feature flags and properties directly from an {{site.data.keyword.appconfig_short}} service instance. Feature flags and property values are then immediately available to toolchains that contain references to those feature flags and property values during subsequent pipeline runs.

## Creating an {{site.data.keyword.appconfig_short}} integration
{: #creating-app-configuration}

Before you create an {{site.data.keyword.appconfig_short}} tool integration in your toolchain, make sure that you provision an instance of the {{site.data.keyword.appconfig_short}} service in a region and resource group that your toolchain can refer to.
{: important}

1. If you are configuring this tool integration as you are creating the toolchain, and an {{site.data.keyword.appconfig_short}} tool integration exists within the template that you are configuring, click the **{{site.data.keyword.appconfig_short}}** tab. Alternatively, in the **More tools** section, click **{{site.data.keyword.appconfig_short}}**.

1. If you have an existing toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the existing toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.  

   a. Click **Add tool**.

   b. In the Tool Integrations section, click **{{site.data.keyword.appconfig_short}}**.

1. Type the name that you want to display for this new tool integration on the {{site.data.keyword.appconfig_short}} card in your toolchain. This name is used to identify the tool integration in your toolchain.

1. Select the **Region** and **Resource group** where your {{site.data.keyword.appconfig_short}} service instance exists.

1. Select the appropriate **App Configuration Environment** and **App Configuration Collection** options from your chosen {{site.data.keyword.appconfig_short}} service instance.

1. Click **Create Integration**.

## Applying feature flags and properties
{: #apply_flags_and_properties}

After you configure your {{site.data.keyword.appconfig_short}} tool integration, you can use it to apply feature flags and properties to the toolchain environment and trigger properties.

1. Within the Pipeline environment properties tab or the Trigger properties tab, click **Add** to display the list of available property types.

1. Select **AppConfig value** and choose the feature flags or properties that you want to apply to the toolchain environment and trigger properties. 

1. Specify the name for the new toolchain environment or trigger property.

1. Select the {{site.data.keyword.appconfig_short}} tool integration and an **Environment** and **Collection** from within it.

1. Select **Feature flag** or **Property** and from the list within your {{site.data.keyword.appconfig_short}} service instance, choose the target feature flag or property.

1. Click **OK** to apply an {{site.data.keyword.appconfig_short}} reference to the field that is associated with it.

## Authorizing your toolchain to access feature flags and properties
{: #authorize_secrets}

References to feature flags and properties that are stored in an {{site.data.keyword.appconfig_short}} service instance are dynamically resolved when the toolchain runs. To access the required feature flags and properties, you must authorize your toolchain to access the {{site.data.keyword.appconfig_short}} instance. If you create a toolchain that has a valid {{site.data.keyword.appconfig_short}} tool integration, or add this tool integration to an existing toolchain, a request is automatically made to create the authorization.

To view your authorizations in {{site.data.keyword.cloud_notm}}, complete the following steps:

1. From the {{site.data.keyword.cloud_notm}} console, click **Manage** > **Access (IAM)**.
1. Click **Authorizations**.

You can also access your authorizations on the [Manage authorizations](https://cloud.ibm.com/iam/authorizations){: external} page. 
{: tip}

You can also create the authorization manually, if required. To successfully resolve {{site.data.keyword.appconfig_short}} references, your toolchain instance must have both `Viewer` and `Reader` access to the correct {{site.data.keyword.appconfig_short}} service instance.

## Learn more about {{site.data.keyword.appconfig_short}}
{: #learn_app-config}

To learn more about {{site.data.keyword.appconfig_short}}, see [Getting Started with {{site.data.keyword.appconfig_short}}](/docs/app-configuration?topic=app-configuration-getting-started). 
