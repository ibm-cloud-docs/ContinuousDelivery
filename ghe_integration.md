---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-19"

keywords: tool integrations, IBM Cloud Public, IBM Cloud Dedicated, GitHub Enterprise and Issues
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

# Configuring GitHub Enterprise and Issues on {{site.data.keyword.cloud_notm}} Dedicated
{: #configghe}

{{site.data.keyword.ghe_long}} is an on-premises, web-based hosting service for Git repos. Dedicated {{site.data.keyword.ghe_short}} is for {{site.data.keyword.Bluemix_notm}} Dedicated customers only. GitHub Issues is a tracking tool that keeps your work and your plans in one place. It is integrated with your development repo so that you can focus on important tasks.
{:shortdesc}

For more information about Dedicated {{site.data.keyword.ghe_short}} and GitHub Issues, see [Getting started with {{site.data.keyword.ghe_long}}](/docs/services/ghededicated?topic=ghededicated-getting-started) and the [GitHub Issues article](https://www.ibm.com/cloud/garage/content/think/tool_github_issues/){:external} on the IBM Cloud Garage Method.

These instructions apply to {{site.data.keyword.Bluemix_notm}} Dedicated for {{site.data.keyword.ghe_short}}. If you are using your own managed version of {{site.data.keyword.ghe_short}}, some steps might differ depending on your internal procedures.
 {: important}

You can configure {{site.data.keyword.ghe_short}} as a tool integration in your toolchain so that you can manage source code in your company's {{site.data.keyword.cloud_notm}} Dedicated instance.

1. If you are configuring this tool integration as you are creating the toolchain, follow these steps:

 a. Before you log in to Dedicated {{site.data.keyword.ghe_short}} for the first time, ask your company's region administrator to add your user ID to your {{site.data.keyword.cloud_notm}} Dedicated instance from your company's user registry by using LDAP. For information about setting up your {{site.data.keyword.ghe_short}} account, see [Getting started with {{site.data.keyword.ghe_long}}](/docs/services/ghededicated?topic=ghededicated-getting-started).

 b. In the Configurable Integrations section, click **{{site.data.keyword.ghe_short}}**.    

 c. Review the default name for the new {{site.data.keyword.ghe_short}} repo. If needed, change the name of the new repo. The following image shows an example of a repo that is cloned from a sample repo. You can use an existing repo or a new repo. To use a new repo, you can create an empty repo, clone a repo, or fork a repo.
 ![Default repo locations](images/toolchain_ghe_config.png)

1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.

 a. Click **Add tool**.

 b. In the Tool Integrations section, click **{{site.data.keyword.ghe_short}}**.

1. If you have a {{site.data.keyword.ghe_short}} repo that you want to use, type the URL for the repo. For the repository type, click **Existing**.
1. If you want to use a new {{site.data.keyword.ghe_short}} repo, type a name for the repo, type the URL for the repo that you are cloning or forking, and select the repository type:

 a. To create an empty repo, click **New**.

 b. To create a copy of a repo, click **Clone**.

 c. To fork a repo so that you can contribute changes through pull requests, click **Fork**.

1. To use GitHub Issues for issue tracking, select the **Enable GitHub Issues** checkbox.
1. Click **Create Integration**.
1. Click the card for the {{site.data.keyword.ghe_short}} repo that you want to work with. Your company's {{site.data.keyword.ghe_short}} repo opens.

  You can use the integrated source code management tools in Eclipse Orion {{site.data.keyword.webide}} to edit the {{site.data.keyword.ghe_short}} repo and deploy an app from your workspace.
  {: tip}

1. If you enabled GitHub Issues, click **GitHub Issues**. You can use this instance of GitHub Issues for your entire toolchain, even if the toolchain contains multiple GitHub repos.    

If you don't have admin privileges for the repo that you are linking to, your integration is limited because you can't use a webhook. Webhooks are required to automatically run a pipeline when a commit is pushed to the repo. Without a webhook, you must start your pipelines manually.
{: tip}
