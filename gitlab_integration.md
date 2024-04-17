---

copyright:
  years: 2015, 2024
lastupdated: "2024-04-17"

keywords: tool integrations, IBM Cloud Public, GitLab

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Configuring GitLab
{: #gitlab}

GitLab is a web-based hosting service for Git repos. You can have both local and remote copies of your repos, which makes it easy to collaborate.
{: shortdesc}

You can configure GitLab as a tool integration in your toolchain so that you can manage source code in a new or existing repo on GitLab.com or your company's GitLab instance. Engage in social coding through wikis, issue tracking, and merge requests.

If you are configuring this tool integration as you are creating the toolchain, follow these steps:

1. If you are storing your source code in a GitLab repo, in the Configurable Integrations section, click **GitLab**. If you are configuring this tool integration on {{site.data.keyword.cloud_notm}} Public, you must authorize {{site.data.keyword.cloud_notm}} to access GitLab by choosing either **OAuth** or **Personal Access Token**.

   * If you choose OAuth, click **Authorize** to go to the GitLab website. If you don't have an active GitLab session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.cloud_notm}} to access your GitLab account. If you have an active GitLab session but you didn't enter your password recently, you might be prompted to enter your GitLab password to confirm.

   * If you choose Personal Access Token, you must enter the personal access token to use to authorize with GitLab to clone repos and perform other actions on your behalf. If you don't have a personal access token, you can follow the documentation on the GitLab website to create one. Make sure that your personal access token has `api` rights.

1. If you are using a repo on your own GitLab server, in the Configurable Integrations section, click **Add custom server**.

   a. Type a title for your custom GitHub server, specify the root URL for the server, and enter your personal access token.

   b. If you don't have a personal access token, you can follow the documentation on the GitLab website to create one.

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
1. If you want to track the deployment of code changes by creating tags and comments on commits, and labels and comments on issues that are referenced by the commits, select the **Track deployment of code changes** checkbox. For more information, see [Track where your code is deployed with toolchains](https://www.ibm.com/blog/announcement/track-code-deployed-toolchains/){: external}.
1. Click **Create Integration**.
1. From your toolchain's Overview page, on the **Repositories** card, click the GitLab repo that you want to work with. Depending on the repo that you selected, either the GitLab website or your company's GitLab repo opens, where you can view the contents of the repo.
1. If you enabled GitLab Issues, click **GitLab Issues** to open it. You can use this instance of GitLab Issues for your entire toolchain, even if the toolchain contains multiple GitLab repos.

   If you don't have owner or master privileges for the repo that you are linking to, your integration is limited because you can't use a webhook. Webhooks are required to automatically run a pipeline when a commit is pushed to the repo. Without a webhook, you must start your pipelines manually.
   {: tip}

## Configuring GitLab by using the API
{: #gitlab-config-parameters}

The GitLab tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `gitlab` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| api_root_url | optional, updatable | String | api_root_url | The URL of the GitLab API. |
| api_token | optional, updatable | Password | api_token | The Personal Access Token (PAT). This parameter is required only if the `auth_type` is set to `pat`, otherwise it is ignored. |
| auth_type | optional, updatable, `Default: oauth` | String | auth_type | Set the authentication method to use to access the Git provider. |
| default_branch | optional, updatable | String | default_branch | The name of the default branch of the Git repo. |
| enable_traceability | optional, updatable, `Default: false` | Boolean | enable_traceability | Set this value to `true` to track the deployment of code changes by creating tags, labels and comments on commits, pull requests, and referenced issues. |
| git_id | optional, immutable | String | git_id | Set this value to `gitlab` for gitlab.com, or to the GUID of a custom GitLab server. |
| has_issues | optional, updatable, `Default: true` | Boolean | toolchain_issues_enabled | Set this value to `true` to enable Issues on the GitLab repo and add an Issues tool integration card to the toolchain. Set this value to `false` to remove the tool integration card from the toolchain. This action does not impact whether issues are enabled on the GitLab repo itself. |
| integration_owner | optional, updatable | String | integration_owner | Select the user that Git operations are performed as. |
| owner_id | optional, immutable | String | owner_id | The GitLab user or group that owns the repo. This parameter is required when you create a repo, or clone or fork a repo. This value is computed when you link to an existing repo. |
| private_repo | optional, immutable, `Default: true` | Boolean | private_repo | Set this value to `true` to make the repo private when you create a repo, or clone or fork a repo. This parameter is not used when you link to an existing repo. |
| repo_id | optional, immutable | String | repo_id | The ID of the GitLab project. |
| repo_name | optional, immutable | String | repo_name | The name of the GitLab repo to create. This parameter is required when you create a repo, or clone or fork a repo. This value is computed when you link to an existing repo. |
| repo_url | optional, immutable | String | repo_url | The URL of the GitLab repo for this tool integration. This parameter is required when you link to an existing repo. This value is computed when you create a repo, or clone or fork a repo. |
| source_repo_url | optional, immutable | String | source_repo_url | The URL of the repo that you want to fork or clone. This parameter is required when you fork or clone a repo, but it is not used when you create a repo or link to an existing repo. |
| token_url | optional, updatable | String | token_url | The token URL that is used to authorize with the GitLab server. |
| type | required, immutable | String | type | The operation to perform to initialize the new tool integration. Use `new` to create a Git repo, `clone` to clone an existing repo into a new Git repo, `fork` to fork an existing Git repo, or `link` to link to an existing Git repo. |
{: caption="Table 1. GitLab tool integration parameters" caption-side="bottom"}

