---

copyright:
  years: 2015, 2025
lastupdated: "2025-06-30"

keywords: tool integrations, IBM Cloud Public, Git Repos and Issue Tracking

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Configuring {{site.data.keyword.gitrepos}}
{: #grit}

The [{{site.data.keyword.gitrepos}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-git_working) tool integration is based on GitLab Community Edition, which is a web-based hosting service for Git repositories (repos). You can have both local and remote copies of your repos. To learn more, see [{{site.data.keyword.gitrepos}}](https://us-south.git.cloud.ibm.com/help){: external}.
{: shortdesc}

If you are configuring {{site.data.keyword.gitrepos}} as you are creating the toolchain, follow these steps:

1. In the Configurable Integrations section, click **{{site.data.keyword.gitrepos}}**.
1. Review the default target locations for the Git repos. Those repos are cloned from the sample repos. If needed, change the names of the target repos.

If you have a toolchain and want to migrate a Git repo in your toolchain to {{site.data.keyword.gitrepos}}, follow these steps:

These instructions apply to toolchains that already contain the Git repo that you want to migrate to {{site.data.keyword.gitrepos}}. For information about adding different types of Git repos to your toolchain, see [Configuring GitHub](/docs/ContinuousDelivery?topic=ContinuousDelivery-github) and [Configuring GitLab](/docs/ContinuousDelivery?topic=ContinuousDelivery-gitlab).
{: tip}

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Toolchains**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.
1. Click **Add**.
1. In the Tool Integrations section, click **{{site.data.keyword.gitrepos}}**.
1. Select the server that you want to deploy code changes to. After you create the integration, you can edit it to manage the list of servers that you are authorized to work with. Click **Manage Authorization** to view a list of all of the servers and to delete the token that you provided to authorize with the server.
1. To create a copy of the Git repo, for the repository type, click **Clone**. Type a new repo name and the URL for the source repo.
1. Your username is automatically selected to assign ownership of this new integration to yourself. After the integration is created, another authorized user can reassign ownership of the integration to themself when they edit it.
1. If you want to create a private repo, select the **Make this repository private** checkbox.
1. If you want to use Issues for issue tracking, select the **Enable Issues** checkbox.
1. If you want to track the deployment of code changes by creating tags and comments on commits, and labels and comments on issues that are referenced by the commits, select the **Track deployment of code changes** checkbox. For more information about tracking code deployments, see [Track where your code is deployed with toolchains](https://www.ibm.com/blog/announcement/track-code-deployed-toolchains/){: external}.
1. Click **Create Integration**.

After you clone the Git repo, you can remove it from your toolchain.
{: tip}

If you have a toolchain and are adding {{site.data.keyword.gitrepos}} to it, follow these steps:

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Toolchains**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.
1. Click **Add tool**.
1. In the Tool Integrations section, click **{{site.data.keyword.gitrepos}}**.
1. Select the server that you want to deploy code changes to. After you create the integration, you can edit it to manage the list of servers that you are authorized to work with. Click **Manage Authorization** to view a list of all of the servers and to delete the token that you provided to authorize with the server.
1. Select a repository type:

   a. To create an empty repo, for the repository type, click **New** and type a repository name.
   b. To fork a Git repo so that you can contribute changes through merge requests, for the repository type, click **Fork**. Type the URL for the source repo.
   c. To create a copy of a Git repo, for the repository type, click **Clone**. Type a new repo name and the URL for the source repo.
   d. If you have a Git repo and want to use it, for the repository type, click **Existing**. Type the URL for the source repo.

1. Your username is automatically selected to assign ownership of this new integration to yourself. After the integration is created, another authorized user can reassign ownership of the integration to themself when they edit it.
1. If you want to create a private repo, select the **Make this repository private** checkbox.
1. If you want to use Issues for issue tracking, select the **Enable Issues** checkbox.
1. If you want to track the deployment of code changes by creating tags and comments on commits, and labels and comments on issues that are referenced by the commits, select the **Track deployment of code changes** checkbox. For more information, see [Track where your code is deployed with toolchains](https://www.ibm.com/blog/announcement/track-code-deployed-toolchains/){: external}.
1. Click **Create Integration**.
1. From your toolchain's Overview page, on the **Repositories** card, click the Git repo that you want to work with. Your project overview page opens.

If you don't have Master or Owner privileges for the repo that you are linking to, your integration is limited because you can't use a webhook. Webhooks are required to automatically run a pipeline when a commit is pushed to the repo. Without a webhook, you must start your pipelines manually.
{: tip}

## Configuring {{site.data.keyword.gitrepos}} by using the API
{: #grit-config-parameters}

The {{site.data.keyword.gitrepos}} tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `hostedgit` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| api_root_url | optional, updatable | String | api_root_url | The URL of the {{site.data.keyword.gitrepos}} API. |
| api_token | optional, updatable | Password | api_token | The Personal Access Token (PAT). This parameter is required only if the `auth_type` is set to `pat`, otherwise it is ignored. |
| auth_type | optional, updatable, `Default: oauth` | String | auth_type | Set the authentication method to use to access the Git provider. |
| default_branch | optional, updatable | String | default_branch | The name of the default branch of the Git repo. |
| enable_traceability | optional, updatable, `Default: false` | Boolean | enable_traceability | Set this value to `true` to track the deployment of code changes by creating tags, labels and comments on commits, pull requests, and referenced issues. |
| git_id | optional, immutable | String | git_id | Set this value to `hostedgit` to target {{site.data.keyword.gitrepos}}. |
| has_issues | optional, updatable, `Default: true` | Boolean | toolchain_issues_enabled | Set this value to `true` to enable issues on the {{site.data.keyword.gitrepos}} repo and add an Issues tool integration card to the toolchain. Set this value to `false` to remove the tool integration card from the toolchain. This action does not impact whether issues are enabled on the {{site.data.keyword.gitrepos}} repo itself. |
| integration_owner | optional, updatable | String | integration_owner | Select the user that Git operations are performed as. |
| owner_id | optional, immutable | String | owner_id | The {{site.data.keyword.gitrepos}} user or group that owns the repo. This parameter is required when you create a repo, or clone or fork a repo. This value is computed when you link to an existing repo. |
| private_repo | optional, immutable, `Default: true` | Boolean | private_repo | Set this value to `true` to make the repo private when you create a repo, or when you clone or fork a repo. This parameter is not used when you link to an existing repo. |
| repo_id | optional, immutable | String | repo_id | The ID of the {{site.data.keyword.gitrepos}} project. |
| repo_name | optional, immutable | String | repo_name | The name of the {{site.data.keyword.gitrepos}} repo to create. This parameter is required when you create a repo, or clone or fork a repo. This value is computed when you link to to an existing repo. |
| repo_url | optional, immutable | String | repo_url | The URL of the {{site.data.keyword.gitrepos}} repo for this tool integration. This parameter is required when you link to an existing repo. This value is computed when you create a repo, or clone or fork a repo. |
| source_repo_url | optional, immutable | String | source_repo_url | The URL of the repo that you want to fork or clone. This parameter is required when you fork or clone a repo, but it is not used when you create a repo or link to an existing repo. |
| token_url | optional, updatable | String | token_url | The token URL that is used to authorize with the {{site.data.keyword.gitrepos}} server. |
| type | required, immutable | String | type | The operation to perform to initialize the new tool integration. Use `new` to create a Git repo, `clone` to clone an existing Git repo into a new Git repo, `fork` to fork an existing Git repo, or `link` to link to an existing Git repo. |
{: caption="{{site.data.keyword.gitrepos}} tool integration parameters" caption-side="bottom"}

If you are logged into IBM Cloud using a Trusted Profile, when configuring a Git Repos and Issue Tracking tool integration, you must use the Personal Access Token authentication method. The OAuth authentication method is incompatible with Trusted Profiles.The Personal Access Token (PAT) authentication allows you to configure the integration of Git Repos and Issue Tracking tool either using GUI, API, or Terraform. This is because the PAT is tied to the actual user who owns the trusted profile. Users can use their Personal Access Tokens to create or re-configure Git Repos and Issue Tracking tool integrations in the toolchain.
However, they should log in as a regular user to access the actual Git repo UI.
{: exception}
