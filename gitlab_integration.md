---

copyright:
  years: 2015, 2022
lastupdated: "2022-11-10"

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

   * If you choose Personal Access Token, you must enter the personal access token to use to authorize with GitLab to clone repos and perform other actions on your behalf. If you don't have a personal access token, you can follow the documentation on the GitLab website to create one.

1. If you are using a repo on your own GitLab server, in the Configurable Integrations section, click **Add custom server**.

   * Type a title for your custom GitLab server and specify the root URL for the server. Enter your personal access token and then click **Save custom integration**.

   * If you don't have a personal access token, you can follow the documentation on the GitLab website to create one.

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
1. If you enabled GitLab Issues, click **GitLab Issues** to open it. You can use this instance of GitLab Issues for your entire toolchain, even if the toolchain contains multiple GitLab repos.    

   If you don't have owner or master privileges for the repo that you are linking to, your integration is limited because you can't use a webhook. Webhooks are required to automatically run a pipeline when a commit is pushed to the repo. Without a webhook, you must start your pipelines manually.
   {: tip}

## Configuring GitLab by using the API
{: #config-parameters}

The GitLab tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `gitlab` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| git_id | optional, immutable | String | git_id | The ID of the GitLab server. |
| api_root_url | optional, updatable | String | api_root_url | The URL of the GitLab API, such as `https://gitlab.example.com/api/v4`. |
| default_branch | optional, updatable | String | default_branch | The name of the default branch, for example, `main`. |
| owner_id | optional, immutable | String | owner_id | Your GitLab ID. |
| repo_id | optional, immutable | String | repo_name | The ID of the GitLab repo. |
| repo_name | optional, immutable | String | repo_name | The name of the GitLab repo to create. |
| repo_url | optional, immutable | String | repo_url | The URL of the repo that you are linking to. |
| source_repo_url | optional, immutable | String | source_repo_url | The URL of the repo that you are forking or cloning. |
| token_url | optional, updatable | String | token_url | The integration token URL. |
| type | required, immutable | String | type | The type of your GitLab repo. The allowed values are `new`, `fork`, `clone`, and `link`. |
| private_repo | optional, immutable, `Default: true` | Boolean | private_repo | Select this checkbox to make this repo private. |
| has_issues | optional, updatable, `Default: true` | Boolean | has_issues | Select this checkbox to enable GitLab Issues for lightweight issue tracking. |
| enable_traceability | optional, updatable, `Default: false` | Boolean | enable_traceability | Select this checkbox to track the deployment of code changes by creating tags, labels and comments on commits, pull requests, and referenced issues. |
| integration_owner | optional, updatable | String | integration_owner | Select the user who Git operations are performed as. |
{: caption="Table 1. GitLab tool integration parameters" caption-side="bottom"}

## Learn more about GitLab
{: #learn_gitlab}

To learn more about GitLab, see the [GitLab article](https://www.ibm.com/cloud/garage/content/code/tool_gitlab/){: external} on the IBM Cloud Garage Method.
