---

copyright:
  years: 2015, 2022
lastupdated: "2022-03-23"

keywords: tool integrations, IBM Cloud Public, GitLab

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

# Configuring GitLab
{: #gitlab}

GitLab is a web-based hosting service for Git repos. You can have both local and remote copies of your repos, which makes it easy to collaborate.
{: shortdesc}

You can configure GitLab as a tool integration in your toolchain so that you can manage source code in a new or existing repo on GitLab.com or your company's GitLab instance. Engage in social coding through wikis, issue tracking, and merge requests.

If you are configuring this tool integration as you are creating the toolchain, follow these steps:

1. If you are storing your source code in a GitLab repo, in the Configurable Integrations section, click **GitLab**. If you are configuring this tool integration on {{site.data.keyword.cloud_notm}} Public and you did not authorize {{site.data.keyword.cloud_notm}} to access GitLab, click **Authorize** to go to the GitLab website. If you don't have an active GitLab session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.cloud_notm}} to access your GitLab account. If you have an active GitLab session but you didn't enter your password recently, you might be prompted to enter your GitLab password to confirm.
1. If you are using a repo on your own GitLab server, in the Configurable Integrations section, click **Add custom server**.

   Type a title for your custom GitLab server and specify the root URL for the server. Enter your personal access token and then click **Save custom integration**.

   If you don't have a personal access token, you can create one:

   a. On any GitLab page, click your profile icon and then click **Settings**.

   b. On the Access Tokens page, type the name of the application that you want to create a personal access token for.

   c. Optional. Choose an expiry date for the access token.

   d. Select the **api** checkbox to define the access for the personal token.

   e. Click **Create personal access token**.

   f. Copy the token to a secure location or password management app. For security reasons, after you leave the page, you can no longer see the token.

1. Review the default target repo locations for the GitLab repos. Those repos are cloned from the sample repos. If needed, change the names of the target repos.

If you have a toolchain and are adding this tool integration to it, follow these steps:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.
1. Click **Add tool**.
1. In the Tool Integrations section, click **GitLab**.
1. Click the GitLab server that you want to use.
1. If you have a GitLab repo and want to use it, for the repository type, click **Existing** and type the URL.
1. If you want to use a new GitLab repo, type a name for the repo, type the URL for the repo that you are cloning or forking, and select the repository type:

   a. To create an empty repo, click **New**.

   b. To create a copy of a GitLab repo, click **Clone**.

   c. To fork a GitLab repo so that you can contribute changes through merge requests, click **Fork**.

1. If you want to create a public repo on the server, clear the **Make this repository private** checkbox.
1. If you want to use GitLab's Issues for issue tracking, select the **Enable GitLab Issues** checkbox.
1. If you want to track the deployment of code changes by creating tags and comments on commits, and labels and comments on issues that are referenced by the commits, select the **Track deployment of code changes** checkbox. For more information, see [Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){: external}.
1. Click **Create Integration**.
1. From your toolchain's Overview page, on the **Repositories** card, click the GitLab repo that you want to work with. Depending on the repo that you selected, either the GitLab website or your company's GitLab repo opens, where you can view the contents of the repo.

   You can use the integrated source code management tools in Eclipse Orion {{site.data.keyword.webide}} to edit the GitLab repo and deploy an app from your workspace.
   {: tip}

1. If you enabled GitLab Issues, click **GitLab Issues** to open it. You can use this instance of GitLab Issues for your entire toolchain, even if the toolchain contains multiple GitLab repos.    

   If you don't have owner or master privileges for the repo that you are linking to, your integration is limited because you can't use a webhook. Webhooks are required to automatically run a pipeline when a commit is pushed to the repo. Without a webhook, you must start your pipelines manually.
   {: tip}

## Learn more about GitLab
{: #learn_gitlab}

To learn more about GitLab, see the [GitLab article](https://www.ibm.com/cloud/garage/content/code/tool_gitlab/){: external} on the IBM Cloud Garage Method.
