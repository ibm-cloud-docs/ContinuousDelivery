---

copyright:
  years: 2023
lastupdated: "2023-02-03"

keywords: tool integrations, IBM Cloud, GitHub integration, Git Repos and Issue Tracking integration, GitLab project

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# FAQs for GitHub, GitLab, and {{site.data.keyword.gitrepos}}
{: #faq_git}

Get answers to frequently asked questions about using GitHub, GitLab, and {{site.data.keyword.gitrepos}}.
{: shortdesc}


## Can I manage GitHub, GitLab, and {{site.data.keyword.gitrepos}} by using Terraform?
{: #terraform}
{: faq}
{: support}

You can use Terraform to add GitHub, GitLab, and {{site.data.keyword.gitrepos}} tool integrations to a toolchain, to update those tool integrations, or to remove those tool integrations from a toolchain. For more information about working with the GitHub, GitLab, and {{site.data.keyword.gitrepos}} tool integrations, see [Working with tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations) and [Creating toolchains with Git](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_git).

You might be able to use Terraform to work directly with some GitHub and GitLab repositories (repos). For more information about the GitHub Terraform provider, see the [GitHub Provider documentation](https://registry.terraform.io/providers/integrations/github/latest/docs){: external}. For more information about the GitLab Terraform provider, see the [GitLab Provider documentation](https://registry.terraform.io/providers/gitlabhq/gitlab/latest/docs){: external}.
{: tip}

## Can I manage GitHub, GitLab, and {{site.data.keyword.gitrepos}} by using an API?
{: #api}
{: faq}
{: support}

You can use HTTP APIs or selected programming language SDKs to add GitHub, GitLab, and {{site.data.keyword.gitrepos}} tool integrations to a toolchain, to update those tool integrations, or to remove those tool integrations from a toolchain. For more information about working with the GitHub, GitLab, and {{site.data.keyword.gitrepos}} tool integrations, see [Working with tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations) and [Creating toolchains with Git](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_git).

You might be able to use APIs to work directly with some repos. For more information about the GitHub API, see [REST API](https://docs.github.com/en/rest){: external}. For more information about the GitLab API, see [REST API](https://docs.gitlab.com/ee/api){: external}.
{: tip}

## What is the difference between the `initialization` block and the `parameters` block in Git tool integration Terraform resources?
{: #terraform_initialization_block}
{: faq}
{: support}

In a Git tool integration Terraform resource, the `initialization` block consists of arguments that control how the tool integration prepares and binds itself to a specific target repo. If you change any of the arguments in the `initialization` block, Terraform deletes the tool integration from the toolchain and creates a replacement tool integration. All of the arguments in the `initialization` block are annotated with the Terraform behavior `Forces new resource`.

By contrast, arguments in the `parameters` block influence how the tool integration works after it is initialized. If an argument is not annotated with `Forces new resource` and you change the argument, Terraform applies the change to the existing tool integration. It does not delete and re-create the tool integration.

If you change any resource argument that is annotated with `Forces new resource`, Terraform deletes and re-creates the resource, irrespective of the block that contains the argument.
{: tip}

For more information about the Git tool integration Terraform resources, see the following Terraform Registry documentation:

* [ibm_cd_toolchain_tool_bitbucketgit](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/cd_toolchain_tool_bitbucketgit){: external}
* [ibm_cd_toolchain_tool_githubconsolidated](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/cd_toolchain_tool_githubconsolidated){: external}
* [ibm_cd_toolchain_tool_gitlab](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/cd_toolchain_tool_gitlab){: external}
* [ibm_cd_toolchain_tool_hostedgit](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/cd_toolchain_tool_hostedgit){: external}

## What type of authentication should I use to access GitHub repos from my toolchain?
{: #repo_authorization}
{: faq}
{: support}

Before you can use a repo integration, you must authorize it so that {{site.data.keyword.cloud_notm}} can access your GitHub account by using one of the following authentication methods. 

* **{{site.data.keyword.cloud_notm}} OAuth app**: When you grant authorization by using the {{site.data.keyword.cloud_notm}} OAuth App, you allow {{site.data.keyword.cloud_notm}} to act as the authenticated user. You can also revoke permissions from the Oauth App.
* **Personal Access Token**: Use a Personal Access Token (PAT) to provide granular access to a specific user or repo. Authorizing with a PAT is recommended when you use Terraform or the API.
