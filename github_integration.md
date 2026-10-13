---

copyright:
  years: 2016, 2026
lastupdated: "2026-10-13"

keywords: tool integrations, IBM Cloud Public, GitHub

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Configuring GitHub
{: #github}

{{site.data.keyword.contdelivery_short}} will be discontinued in the following regions on 12 February 2027: **au-syd**, **ca-tor**, **us-east**. Code Risk Analyzer will also be discontinued in all regions on that date. If a region has no active usage of these features, the features in that region may be discontinued earlier and stop accepting new instances. [Learn more](/docs/ContinuousDelivery?topic=ContinuousDelivery-faq_region_feature_consolidation)
{: important}

GitHub is a web-based hosting service for Git repos. You can have both local and remote copies of your repos, which makes it easy to collaborate.
{: shortdesc}

{{site.data.keyword.ghe_short}} is an on-premises, web-based hosting service for Git repos.

GitHub Issues is a tracking tool that keeps your work and your plans all in one place. It is integrated with your development repo so that you can focus on important tasks.

You can configure GitHub as a tool integration in your toolchain so that you can manage source code in a new or existing repo on GitHub.com or your company's {{site.data.keyword.ghe_short}} instance. Engage in social coding through wikis, issue tracking, and pull requests.

If you are configuring this tool integration as you are creating the toolchain, follow these steps:

1. If you are storing your source code in a GitHub repo, in the Configurable Integrations section, click **GitHub**. If you are configuring this tool integration on {{site.data.keyword.cloud_notm}} Public, you must authorize {{site.data.keyword.cloud_notm}} to access GitHub by choosing **OAuth**, **Personal Access Token**, or **GitHub App**.

   * If you choose OAuth, click **Authorize** to go to the GitHub website. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.cloud_notm}} to access your GitHub account. If you have an active GitHub session but you didn't enter your password recently, you might be prompted to enter your GitHub password to confirm.

   * If you choose Personal Access Token, you must enter the personal access token to use to authorize with GitHub to clone repos and perform other actions on your behalf. If you don't have a personal access token, you can follow the documentation on the GitHub website to create one. Make sure that your personal access token has `repo`, `delete_repo`, `read:user`, and `workflow` rights.

   * If you choose GitHub App, {{site.data.keyword.cloud_notm}} uses a GitHub App installation to authenticate with GitHub on your behalf instead of an OAuth token. GitHub Apps provide finer-grained permission control and do not depend on individual user credentials. Choose one of the following methods:

      * **Managed** — Use the IBM-provided GitHub App that is preconfigured for your GitHub server. Click **Authorize** to be redirected to GitHub, where you approve the app's access to your account.

      * **Custom** — Bring your own GitHub App. Enter the **App ID** and **Private Key** (PEM format) of a GitHub App that you have registered and installed on your repositories. The app must be installed on any repository you want to use with this integration. For more information about creating a GitHub App, see the [GitHub documentation](https://docs.github.com/en/apps/creating-github-apps/about-creating-github-apps/about-creating-github-apps){: external}.

1. If you are using a repo on your own {{site.data.keyword.ghe_short}} server, in the Configurable Integrations section, click **Custom Server**.

   a. Type a title for your custom GitHub server, specify the root URL for the server, and enter your personal access token.

   b. If you don't have a personal access token, you can follow the documentation on the GitHub website to create one.

   c. If your GitHub server is air-gapped or is not accessible on the public internet, you can connect and integrate a {{site.data.keyword.deliverypipeline}} Private Worker to run on your own Kubernetes infrastructure to access internal or on-premises resources. For more information about {{site.data.keyword.deliverypipeline}} Private Workers, see [Working with {{site.data.keyword.deliverypipeline}} Private Workers](/docs/ContinuousDelivery?topic=ContinuousDelivery-private-workers).

   d. If your {{site.data.keyword.ghe_short}} server has a GitHub App registered, you can also choose the **GitHub App** authentication method and provide your App ID and Private Key, or use the managed app if one is preconfigured for your server.

1. Review the default target repo locations for the GitHub repos. Those repos are cloned from the sample repos. If needed, change the names of the target repos.


If you have a toolchain and are adding this tool integration to it, follow these steps:

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Toolchains**. On the Toolchains page, click the toolchain to open its Overview page.
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
1. If you want to track the deployment of code changes by creating tags and comments on commits, and labels and comments on issues that are referenced by the commits, select the **Track deployment of code changes** checkbox.
1. Click **Create Integration**.
1. From your toolchain's Overview page, on the **Repositories** card, click the GitHub or {{site.data.keyword.ghe_short}} repo that you want to work with. Depending on the repo that you selected, either the GitHub website or your company's {{site.data.keyword.ghe_short}} repo opens, where you can view the contents of the repo.
1. If you enabled GitHub Issues, click **GitHub Issues** to open it. You can use this instance of GitHub Issues for your entire toolchain, even if the toolchain contains multiple GitHub or {{site.data.keyword.ghe_short}} repos.

   If you don't have admin privileges for the repo that you are linking to, your integration is limited because you can't use a webhook. Webhooks are required to automatically run a pipeline when a commit is pushed to the repo. Without a webhook, you must start your pipelines manually.
   {: tip}

## Configuring GitHub by using the API
{: #github-config-parameters}

The GitHub tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apis/toolchain){: external} when you [create](https://cloud.ibm.com/apis/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apis/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apis/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `githubconsolidated` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| api_root_url | optional, updatable | String | api_root_url | The URL of the API root for the GitHub server. |
| api_token | optional, updatable | Password | api_token | The Personal Access Token (PAT). This parameter is required only if the `auth_type` is set to `pat`, otherwise it is ignored. |
| auth_type | optional, updatable | String | auth_type | Set the authentication method to use to access the Git provider. Valid values are `oauth`, `pat`, and `github_app`. When `github_app` is specified, authentication uses a GitHub App installation token instead of a user OAuth token or PAT. |
| auto_init | optional, immutable, `Default: false` | Boolean | auto_init | Set this value to `true` to initialize this repo with a readme file. This parameter is used only when you create a repo. |
| blind_connection | optional, updatable, `Default: false` | Boolean | blind_connection | Setting this value to true means the server is not addressable on the public internet. {{site.data.keyword.cloud_notm}} can't validate the connection details you provide. Certain functionality that requires API access to the git server will be disabled. Delivery pipeline will only work using a private worker that has network access to the git server. |
| default_branch | optional, updatable | String | default_branch | The default branch of the Git repo. |
| enable_traceability | optional, updatable, `Default: false` | Boolean | enable_traceability | Set this value to `true` to track the deployment of code changes by creating tags, labels and comments on commits, pull requests, and referenced issues. |
| git_id | optional, immutable | String | git_id | Set this value to `github` for github.com, or to the GUID of a custom GitHub Enterprise server. |
| github_app_auth_method | optional, updatable | String | github_app_auth_method | The GitHub App authentication method to use when `auth_type` is `github_app`. Set to `managed` to use the IBM-provided GitHub App (default), or `custom` to supply your own GitHub App credentials via `github_app_credential_app_id` and `github_app_credential_private_key`. |
| github_app_credential_app_id | optional, updatable | String | github_app_credential_app_id | The GitHub App ID for a custom GitHub App. Required when `github_app_auth_method` is `custom`. |
| github_app_credential_private_key | optional, updatable | Password | github_app_credential_private_key | The RSA private key (PEM format) for a custom GitHub App. Required when `github_app_auth_method` is `custom`. The key is stored encrypted. |
| has_issues | optional, updatable, `Default: true` | Boolean | toolchain_issues_enabled | Set this value to `true` to enable issues on the GitHub repo and add an Issues tool card to the toolchain. Set the value to `false` to remove the tool integration card from the toolchain. This setting does not impact whether issues are enabled on the GitHub repo itself. |
| integration_owner | optional, updatable | String | integration_owner | Select the user that the Git operations are performed as. |
| owner_id | optional, immutable | String | owner_id | The GitHub user or organization that owns the repo. This parameter is required when you create a repo, or clone or fork a repo. This value is computed when you link to an existing repo. |
| private_repo | optional, immutable, `Default: false` | Boolean | private_repo | Set this value to `true` to make the repo private when you create a repo or clone or fork a repo. This parameter is not used when you link to an existing repo. |
| repo_id | optional, immutable | String | repo_id | The ID of the GitHub repo. |
| repo_name | optional, immutable | String | repo_name | The name of the GitHub repo to create. This parameter is required when you create a repo, or clone or fork a repo. This value is computed when you link to an existing repo. |
| repo_url | optional, immutable | String | repo_url | The URL of the GitHub repo for this tool integration. This parameter is required when you link to an existing repo. This value is computed when you create a repo, or clone or fork a repo. |
| root_url | optional, updatable | String | root_url | The Root URL of the server. e.g. https://github.example.com |
| source_repo_url | optional, immutable | String | source_repo_url | The URL of the repo that you are forking or cloning. This parameter is required when you fork or clone a repo. It is not used when you create a repo or link to an existing repo. |
| title | optional, updatable | String | title | The title of the server. e.g. My GitHub Enterprise Server |
| token_url | optional, updatable | String | token_url | The token URL that is used to authorize with the GitHub server. |
| type | required, immutable | String | type | The operation to perform to initialize the new tool integration. Use `new` to create a Git repo, `clone` to clone an existing repo into a new Git repo, `fork` to fork an existing Git repo, or `link` to link to an existing Git repo. |
{: caption="GitHub tool integration parameters" caption-side="bottom"}

## Using GitHub App authentication
{: #github-app-auth}

GitHub App authentication is an alternative to OAuth and Personal Access Token (PAT) methods. GitHub Apps authenticate as the application rather than as a user, which provides finer-grained repository permissions, no dependency on individual user account credentials, and tokens that are automatically rotated and scoped to specific repositories.

Two modes are available:

**Managed** (`github_app_auth_method: managed`)
: {{site.data.keyword.cloud_notm}} uses an IBM-provided GitHub App that is pre-registered for your GitHub server. You authorize the app through an OAuth consent flow, and the resulting user-to-server token (`ghu_`) is stored and used automatically.

**Custom** (`github_app_auth_method: custom`)
: You register and manage your own GitHub App on GitHub or {{site.data.keyword.ghe_short}}. You provide the App ID and a PEM-encoded RSA private key. {{site.data.keyword.cloud_notm}} uses these credentials to mint short-lived installation access tokens (`ghs_`) automatically. The GitHub App must be installed on every repository you want to use with this integration.

### Before you begin with custom GitHub App authentication
{: #github-app-prereqs}

Before you configure custom GitHub App authentication, complete the following steps:

1. [Create a GitHub App](https://docs.github.com/en/apps/creating-github-apps/about-creating-github-apps/about-creating-github-apps){: external} in your GitHub organization or personal account. Give the app the following repository permissions at minimum:
   - **Contents**: Read and write
   - **Metadata**: Read-only
   - **Pull requests**: Read and write (if you use pull request tracking)
   - **Workflows**: Read and write (if your pipelines trigger GitHub Actions)

1. Generate a private key for the app and save the PEM file. You will need this key when you configure the integration.

1. Install the GitHub App on the organization or repositories that your toolchain will access. The app must be installed before you can validate the credential.

After you configure the tool integration with your App ID and private key, {{site.data.keyword.cloud_notm}} validates the credential by calling the GitHub API. If the app is not yet installed on a specified repository, you will receive an error prompting you to install the app first.
{: note}
