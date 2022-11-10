---

copyright:
  years: 2015, 2022
lastupdated: "2022-11-10"

keywords: tool integrations, IBM Cloud Public, GitHub

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Configuring GitHub
{: #github}

GitHub is a web-based hosting service for Git repos. You can have both local and remote copies of your repos, which makes it easy to collaborate.
{: shortdesc}

{{site.data.keyword.ghe_short}} is an on-premises, web-based hosting service for Git repos.

GitHub Issues is a tracking tool that keeps your work and your plans all in one place. It is integrated with your development repo so that you can focus on important tasks.

You can configure GitHub as a tool integration in your toolchain so that you can manage source code in a new or existing repo on GitHub.com or your company's {{site.data.keyword.ghe_short}} instance. Engage in social coding through wikis, issue tracking, and pull requests.

If you are configuring this tool integration as you are creating the toolchain, follow these steps:

1. If you are storing your source code in a GitHub repo, in the Configurable Integrations section, click **GitHub**. If you are configuring this tool integration on {{site.data.keyword.cloud_notm}} Public, you must authorize {{site.data.keyword.cloud_notm}} to access GitHub by choosing either **OAuth** or **Personal Access Token**. 

   * If you choose OAuth, click **Authorize** to go to the GitHub website. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.cloud_notm}} to access your GitHub account. If you have an active GitHub session but you didn't enter your password recently, you might be prompted to enter your GitHub password to confirm.

   * If you choose Personal Access Token, you must enter the personal access token to use to authorize with GitHub to clone repos and perform other actions on your behalf. If you don't have a personal access token, you can follow the documentation on the GitHub website to create one.


1. If you are using a repo on your own {{site.data.keyword.ghe_short}} server, in the Configurable Integrations section, click **Add custom server**.

   * Type a title for your custom GitHub server and specify the root URL for the server. Enter your personal access token and then click **Save custom integration**.

   * If you don't have a personal access token, you can follow the documentation on the GitHub website to create one.

1. Review the default target repo locations for the GitHub repos. Those repos are cloned from the sample repos. If needed, change the names of the target repos.


If you have a toolchain and are adding this tool integration to it, follow these steps:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.
1. Click **Add tool**.
1. In the Tool Integrations section, click **GitHub**.
1. Click the GitHub server that you want to use.
1. If you have a GitHub or {{site.data.keyword.ghe_short}} repo and want to use it, for the repository type, click **Existing** and type the URL.
1. If you want to use a new GitHub or {{site.data.keyword.ghe_short}} repo, type a name for the repo, type the URL for the repo that you are cloning or forking, and select the repository type:

   a. To create an empty repo, click **New**.

   b. To create a copy of a GitHub or {{site.data.keyword.ghe_short}} repo, click **Clone**.

   c. To fork a GitHub or {{site.data.keyword.ghe_short}} repo so that you can contribute changes through pull requests, click **Fork**.

1. If you are a GitHub.com user with an upgraded account, or you selected a {{site.data.keyword.ghe_short}} server and you want to make a new private repo on the server, select the **Make this repository private** checkbox.
1. If you want to use GitHub's Issues for issue tracking, select the **Enable GitHub Issues** checkbox.
1. If you want to track the deployment of code changes by creating tags and comments on commits, and labels and comments on issues that are referenced by the commits, select the **Track deployment of code changes** checkbox. For more information, see [Track where your code is deployed with toolchains](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){: external}.
1. Click **Create Integration**.
1. From your toolchain's Overview page, on the **Repositories** card, click the GitHub or {{site.data.keyword.ghe_short}} repo that you want to work with. Depending on the repo that you selected, either the GitHub website or your company's {{site.data.keyword.ghe_short}} repo opens, where you can view the contents of the repo.
1. If you enabled GitHub Issues, click **GitHub Issues** to open it. You can use this instance of GitHub Issues for your entire toolchain, even if the toolchain contains multiple GitHub or {{site.data.keyword.ghe_short}} repos.    

   If you don't have admin privileges for the repo that you are linking to, your integration is limited because you can't use a webhook. Webhooks are required to automatically run a pipeline when a commit is pushed to the repo. Without a webhook, you must start your pipelines manually.
   {: tip}

## Configuring GitHub by using the API
{: #config-parameters}

The GitHub tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `githubconsolidated` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| git_id | optional, immutable | String | git_id | The ID of the GitHub server.|  |
| api_root_url | optional, updatable | String | api_root_url | The URL of the GitHub API, such as `https://api.github.example.com`. |
| default_branch | optional, updatable | String | default_branch | The name of the default branch, for example, `main`. |
| owner_id | optional, immutable | String | owner_id | Your GitHub ID. |
| repo_name | optional, immutable | String | repo_name | The name of the GitHub repo to create. |
| repo_url | optional, immutable | String | repo_url | The URL of the repo that you are linking to. |
| source_repo_url | optional, immutable | String | source_repo_url | The URL of the repo that you are forking or cloning. |
| token_url | optional, updatable | String | token_url | The integration token URL. |
| type | required, immutable | String | type | The type of your GitHub repo. The allowed values are `new`, `fork`, `clone`, and `link`. |
| private_repo | optional, immutable, `Default: false` | Boolean | private_repo | Select this checkbox to make this repo private. |
| has_issues | optional, updatable, `Default: true` | Boolean | has_issues | Select this checkbox to enable GitHub Issues for lightweight issue tracking. |
| auto_init | optional, immutable, `Default: false` | Boolean | auto_init | Select this checkbox to initialize this repo with a readme file. |
| enable_traceability | optional, updatable, `Default: false` | Boolean | enable_traceability | Select this checkbox to track the deployment of code changes by creating tags, labels and comments on commits, pull requests, and referenced issues. |
| integration_owner | optional, updatable | String | integration_owner | Select the user who Git operations are performed as. |
{: caption="Table 1. GitHub tool integration parameters" caption-side="bottom"}

## Learn more about GitHub
{: #learn_github}

To learn more about GitHub, see the [GitHub article](https://www.ibm.com/cloud/garage/content/code/tool_github/){: external} and the [GitHub Issues article](https://www.ibm.com/cloud/garage/content/think/tool_github_issues/){: external} on the IBM Cloud Garage Method or take the [Ensure quality deployments by using the "Deployment Risk Analytics with GitHub and Jenkins" toolchain](https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain){: external} tutorial.
