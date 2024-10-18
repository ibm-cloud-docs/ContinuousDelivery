---

copyright:
  years: 2015, 2024
lastupdated: "2024-10-18"

keywords: tool integrations, IBM Cloud Public, Bitbucket

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Configuring Bitbucket
{: #bitbucket}

Store your source code in a new or existing repository (repo) on bitbucket.org and engage in social coding through wikis, issue tracking, and pull requests.
{: shortdesc}

Configure Bitbucket to collaborate on code with your team:

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Toolchains**. On the Toolchains page, click the toolchain that you want to add Bitbucket to. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.

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
   
   If you have an active Bitbucket session but you didn't enter your password recently, you might be prompted to enter your Bitbucket password to confirm.
   {: tip}

1. Click the Bitbucket server that you want to use.
1. If you have a Bitbucket repo that you want to use, type the URL for the repo. For the repository type, click **Existing**.
1. If you want to use a new Bitbucket repo, type a name for the repo, type the URL for the repo that you are cloning or forking, and select the repository type:

   a. To create an empty repo, click **New**.

   b. To create a copy of a repo, click **Clone**.

   c. To fork a repo so that you can contribute changes through pull requests, click **Fork**.

1. To create a private repo on the server, select the **Make this repository private** checkbox.
1. To use Bitbucket Issues for issue tracking, select the **Enable Bitbucket Issues** checkbox.
1. To track the deployment of code changes by creating tags and comments on commits, and labels and comments on issues that are referenced by the commits, select the **Track deployment of code changes** checkbox. For more information, see [Track where your code is deployed with toolchains](https://www.ibm.com/blog/announcement/track-code-deployed-toolchains/){: external}.
1. Click **Create Integration**.
1. From your toolchain, on the **Third-Party tools** card, click the Bitbucket tool integration for the Bitbucket repo that you want to work with. The Bitbucket website opens where you can view the contents of the repo.
1. If you enabled Bitbucket Issues, click **Bitbucket Issues** to open it. You can use this instance of Bitbucket Issues for your entire toolchain, even if the toolchain contains multiple Bitbucket repos.    

If you don't have owner or master privileges for the repo that you are linking to, your integration is limited because you can't use a webhook. Webhooks are required to automatically run a pipeline when a commit is pushed to the repo. Without a webhook, you must start your pipelines manually.
{: tip}

## Configuring Bitbucket by using the API
{: #bitbucket-config-parameters}

The Bitbucket tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `bitbucketgit` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| api_root_url | optional, updatable | String | api_root_url | The URL of the Bitbucket API, such as `https://api.bitbucket.org`. |
| default_branch | optional, updatable | String | default_branch | The name of the default branch, for example, `main`. |
| enable_traceability | optional, updatable, `Default: false` | Boolean | enable_traceability | Set this value to `true` to track the deployment of code changes by creating tags, labels and comments on commits, pull requests, and referenced issues. |
| git_id | optional, immutable | String | git_id | Set this value to `bitbucketgit` for bitbucket.org, or to the GUID of a custom Bitbucket server. |
| has_issues | optional, updatable, `Default: true` | Boolean | toolchain_issues_enabled | Set this value to `true` to enable issues on the Bitbucket repo and to add an Issues tool card to the toolchain. Set this value to `false` to remove the tool integration card from the toolchain. This setting does not impact whether Issues are enabled on the Bitbucket repo itself. |
| integration_owner | optional, updatable | String | integration_owner | The user who performs Git operations. |
| owner_id | optional, immutable | String | owner_id | The Bitbucket user or group that owns the repo. This parameter is required when you create a repo, or clone or fork a repo. This value is computed when you link to an existing repo. |
| private_repo | optional, immutable, `Default: false` | Boolean | private_repo | Set this value to `true` to make the repo private when you create a repo, or when you clone or fork a repo. This parameter is not used when you link to an existing repo. |
| repo_id | optional, immutable | String | repo_id | The ID of the Bitbucket repo. |
| repo_name | optional, immutable | String | repo_name | The name of the Bitbucket repo to create. This parameter is required when you create a repo, or clone or fork a repo. This value is computed when you link to an existing repo. |
| repo_url | optional, immutable | String | repo_url | The URL of the Bitbucket repo for this tool integration. This parameter is required when you link to an existing repo. This value is computed when you create a repo, or clone or fork a repo. |
| source_repo_url | optional, immutable | String | source_repo_url | The URL of the repo that you want to fork or clone. This parameter is required when you fork or clone a repo, but it is not used when you create a repo or link to an existing repo. |
| token_url | optional, updatable | String | token_url | The token URL that is used to authorize with the Bitbucket server. |
| type | required, immutable | String | type | The operation to perform to initialize the new tool integration. Use `new` to create a Git repo, `clone` to clone an existing repo into a new Git repo, `fork` to fork an existing Git repo, or `link` to link to an existing Git repo. |
{: caption="Bitbucket tool integration parameters" caption-side="bottom"}


## Learn more about Bitbucket
{: #learn_more_bitbucket}

To learn more about Bitbucket, see the [Bitbucket Cloud resources](https://support.atlassian.com/bitbucket-cloud/resources/){: external}.
