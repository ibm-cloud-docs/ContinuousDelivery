---

copyright:
  years: 2015, 2020
lastupdated: "2020-09-10"

keywords: tool integrations, IBM Cloud Public, IBM Cloud Dedicated, Git Repos and Issue Tracking

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

# Configuring Git Repos and Issue Tracking
{: #grit}

The [{{site.data.keyword.gitrepos}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working) tool integration is based on GitLab Community Edition, which is a web-based hosting service for Git repos. You can have both local and remote copies of your repos. To learn more, see [{{site.data.keyword.gitrepos}}](https://us-south.git.cloud.ibm.com/help){:external}. 
{:shortdesc}

If you are configuring {{site.data.keyword.gitrepos}} as you are creating the toolchain, follow these steps:    

1. In the Configurable Integrations section, click **Git Repos and Issue Tracking**.
1. Review the default target locations for the Git repos. Those repos are cloned from the sample repos. If needed, change the names of the target repos.

If you have a toolchain and want to migrate a Git repo in your toolchain to {{site.data.keyword.gitrepos}}, follow these steps:

These instructions apply to toolchains that already contain the Git repo that you want to migrate to {{site.data.keyword.gitrepos}}. For information about adding different types of Git repos to your toolchain, see the [Configuring GitHub](/docs/ContinuousDelivery?topic=ContinuousDelivery-github), [Configuring GitHub Enterprise and Issues on {{site.data.keyword.cloud_notm}} Dedicated](/docs/ContinuousDelivery?topic=ContinuousDelivery-configghe), and [Configuring GitLab](/docs/ContinuousDelivery?topic=ContinuousDelivery-gitlab).
{: tip}

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.
1. Click **Add tool**.
1. In the Tool Integrations section, click **Git Repos and Issue Tracking**.
1. Select the server that you want to deploy code changes to. After you create the integration, you can edit it to manage the list of servers that you are authorized to work with. Click **Manage Authorization** to view a list of all of the servers and to delete the token that you provided to authorize with the server.
1. To create a copy of the Git repo, for the repository type, click **Clone**. Type a new repo name and the URL for the source repo.
1. Your username is automatically selected to assign ownership of this new integration to yourself. After the integration is created, another authorized user can reassign ownership of the integration to themself when they edit it.
1. If you want to create a private repo, select the **Make this repository private** checkbox.
1. If you want to use Issues for issue tracking, select the **Enable Issues** checkbox.
1. If you want to track the deployment of code changes by creating tags and comments on commits, and labels and comments on issues that are referenced by the commits, select the **Track deployment of code changes** checkbox. For more information, see [Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){:external}.
1. Click **Create Integration**.

After you clone the Git repo, you can remove it from your toolchain.
{: tip}

If you have a toolchain and are adding {{site.data.keyword.gitrepos}} to it, follow these steps:    

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.
1. Click **Add tool**.
1. In the Tool Integrations section, click **Git Repos and Issue Tracking**.
1. Select the server that you want to deploy code changes to. After you create the integration, you can edit it to manage the list of servers that you are authorized to work with. Click **Manage Authorization** to view a list of all of the servers and to delete the token that you provided to authorize with the server.
1. Select a repository type:     

  a. To create an empty repo, for the repository type, click **New** and type a repository name.    
  b. To fork a Git repo so that you can contribute changes through merge requests, for the repository type, click **Fork**. Type the URL for the source repo.    
  c. To create a copy of a Git repo, for the repository type, click **Clone**. Type a new repo name and the URL for the source repo.     
  d. If you have a Git repo and want to use it, for the repository type, click **Existing**. Type the URL for the source repo.

1. Your username is automatically selected to assign ownership of this new integration to yourself. After the integration is created, another authorized user can reassign ownership of the integration to themself when they edit it.
1. If you want to create a private repo, select the **Make this repository private** checkbox.
1. If you want to use Issues for issue tracking, select the **Enable Issues** checkbox.
1. If you want to track the deployment of code changes by creating tags and comments on commits, and labels and comments on issues that are referenced by the commits, select the **Track deployment of code changes** checkbox. For more information, see [Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){:external}.
1. Click **Create Integration**.
1. Click the card for the Git repo that you want to work with. Your project overview page opens.    

If you don't have Master or Owner privileges for the repo that you are linking to, your integration is limited because you can't use a webhook. Webhooks are required to automatically run a pipeline when a commit is pushed to the repo. Without a webhook, you must start your pipelines manually.
{: tip}

## Learn more about Git Repos and Issue Tracking

To learn more about {{site.data.keyword.gitrepos}}, see the [{{site.data.keyword.gitrepos}}: Social coding hosted by IBM article](https://www.ibm.com/cloud/garage/content/code/tool_git_repos_and_issue_tracking/){:external} on the IBM Cloud Garage Method or take this tutorial:

  * [Create and use your first toolchain by using the "Develop a Cloud Foundry app" toolchain](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:external}
