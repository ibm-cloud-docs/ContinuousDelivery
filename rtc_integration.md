---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-19"

keywords: tool integrations, IBM Cloud Public, IBM Cloud Dedicated, Rational Team Concert

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

# Configuring Rational Team Concert
{: #rationalteamconcert}

IBM Rational Team Concert&trade; is a team collaboration tool that integrates development tasks, including iteration planning, change management, defect tracking, source control, build automation, and reporting.
{: shortdesc}

Configure Rational Team Concert to practice a DevOps approach and continuous delivery in your development environment:

1. If you are configuring this tool integration as you are creating the toolchain, in the Configurable Integrations section, click **Rational Team Concert**.
1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**. 

 a. Click **Add tool**.

 b. In the Tool Integrations section, click **Rational Team Concert**.

1. Type the URL for the Rational Team Concert server that you want to open when you click the Rational Team Concert card from your toolchain.
1. Type the user ID that you use to access the Rational Team Concert server.
1. Type the password that you use to access the Rational Team Concert server.
1. If you have a Rational Team Concert project area that you want to add to your toolchain, follow these steps:

 a. From the **Project Area type** list, select **Existing project area**.

 b. Type the name of the project area to add to your toolchain.

1. If you want to create a Rational Team Concert project area to add to your toolchain, follow these steps:

 a. From the **Project Area type** list, select **New project area**.

 b. Type a name for the new project area to add to your toolchain.

 c. Type the name of the Rational Team Concert process template to use to create the project.

1. To track the deployment of code changes for the project by creating tags and comments on work items, select the **Track deployment of code changes** checkbox.
1. Click **Create Integration**.
1. From your toolchain, click **Rational Team Concert** to open the Rational Team Concert dashboard that you configured.

## Learn more about Rational Team Concert

To learn more about Rational Team Concert, see the [IBM Rational Team Concert article](https://www.ibm.com/cloud/garage/content/think/tool_rtc/){: external} on the IBM Cloud Garage Method.
