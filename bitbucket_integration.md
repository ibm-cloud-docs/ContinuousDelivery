---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-19"

keywords: tool integrations, IBM Cloud Public, IBM Cloud Dedicated, Bitbucket

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

# Configuring Bitbucket
{: #bitbucket}

Store your source code in a new or existing repository on bitbucket.org and engage in social coding through wikis, issue tracking, and pull requests.
{: shortdesc}

Configure Bitbucket to collaborate on code with your team:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain that you want to add Bitbucket to. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.

 a. Click **Add tool**.

 b. In the Tool Integrations section, click **Bitbucket**.

   If you are configuring this tool integration on {{site.data.keyword.cloud_notm}} Public and you did not authorize {{site.data.keyword.cloud_notm}} to access Bitbucket, click **Authorize** to go to the Bitbucket website. If you don't have an active Bitbucket session, you are prompted to log in. Click **Grant access** to allow {{site.data.keyword.cloud_notm}} Toolchains to access the following parts of your Bitbucket account:
   
   * **Read your account information**. Get basic user information to populate the user interface.
   
   * **Read and modify your repositories' issues**. Allow {{site.data.keyword.contdelivery_short}} to update issues to indicate when the pipeline deploys commits that are attached to those issues. 
   
   * **Read your team's project settings and read repositories that are contained within your team's projects**. Allow {{site.data.keyword.contdelivery_short}} to integrate with repos that are owned by teams.
   
   * **Read and modify your repositories and their pull requests**. Allow {{site.data.keyword.contdelivery_short}} to push sample code into repos, when users request the code.
   
   * **Administer your repositories**. Allow {{site.data.keyword.contdelivery_short}} to create new repos, when requested by users.
   
   * **Read your team membership information**. Allow {{site.data.keyword.contdelivery_short}} to show a list of your teams in the **Owner** menu that is displayed when you create a new repo.
   
   * **Read and modify your repositories' webhooks**. Allow the pipeline to trigger builds when commits are pushed to a repo.
   {: tip}
   
   If you have an active Bitbucket session but you didn't enter your password recently, you might be prompted to enter your Bitbucket password to confirm.

1. Click the Bitbucket server that you want to use.
1. If you have a Bitbucket repo that you want to use, type the URL for the repo. For the repository type, click **Existing**.
1. If you want to use a new Bitbucket repo, type a name for the repo, type the URL for the repo that you are cloning or forking, and select the repository type:

 a. To create an empty repo, click **New**.

 b. To create a copy of a repo, click **Clone**.

 c. To fork a repo so that you can contribute changes through pull requests, click **Fork**.

1. To create a private repo on the server, select the **Make this repository private** checkbox.
1. To use Bitbucket Issues for issue tracking, select the **Enable Bitbucket Issues** checkbox.
1. To track the deployment of code changes by creating tags and comments on commits, and labels and comments on issues that are referenced by the commits, select the **Track deployment of code changes** checkbox. For more information, see [Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){: external}.
1. Click **Create Integration**.
1. From your toolchain, click the card for the Bitbucket repo that you want to work with. The Bitbucket website opens where you can view the contents of the repo.
1. If you enabled Bitbucket Issues, click **Bitbucket Issues** to open it. You can use this instance of Bitbucket Issues for your entire toolchain, even if the toolchain contains multiple Bitbucket repos.    

If you don't have owner or master privileges for the repo that you are linking to, your integration is limited because you can't use a webhook. Webhooks are required to automatically run a pipeline when a commit is pushed to the repo. Without a webhook, you must start your pipelines manually.
{: tip}

## Learn more about Bitbucket

To learn more about Bitbucket, see the [Bitbucket article](https://www.ibm.com/cloud/garage/content/code/tool_bitbucket/){: external} on the IBM Cloud Garage Method.
