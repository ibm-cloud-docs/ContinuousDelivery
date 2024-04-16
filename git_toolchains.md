---

copyright:
  years: 2020, 2024
lastupdated: "2024-04-16"

keywords: Git Repos, Issue Tracking, Collaborate, Git repository, Git source control, authentication, GitHub 

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Creating toolchains with Git
{: #toolchains_git}
{: help} 
{: support}

You can use a template that contains either a {{site.data.keyword.gitrepos}} or GitHub tool integration as a starting point to create a toolchain that you can add Git repositories (repos) to. Alternatively, you can start with either an empty toolchain or an existing toolchain and then add a {{site.data.keyword.gitrepos}} or GitHub tool integration to it. 
{: shortdesc}

To see which toolchain templates contain the {{site.data.keyword.gitrepos}} or GitHub tool integrations, see [Toolchain availability, templates, and tutorials](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_about#templates).

## Creating a toolchain from a template with {{site.data.keyword.gitrepos}} or GitHub by using the console 
{: #creating_a_toolchain_git}
{: ui}

You can use a template as a starting point to [create a toolchain](https://cloud.ibm.com/devops/create){: external} that includes either a {{site.data.keyword.gitrepos}} or GitHub tool integration. Learn more about how to use the templates from the [IBM Cloud Garage Method](https://www.ibm.com/architectures/hybrid){: external}.

1. Log in to [{{site.data.keyword.cloud_notm}}](http://cloud.ibm.com){: external}.
1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**.
1. On the DevOps dashboard, on the **Toolchains** page, click **Create a Toolchain**.
1. On the **Create a Toolchain** page, click a toolchain template.
1. Review the diagram of the toolchain that you are about to create. The diagram shows each tool integration in its lifecycle phase in the toolchain.
1. Review the default information for the toolchain settings:

   * The toolchain's name identifies it in {{site.data.keyword.cloud_notm}}. If you want to use a different name, change the toolchain's name.
   * The region to create the toolchain in. If you want to use a different region, select it from the list of available regions.
   * The resource group to create the toolchain in. If you want to use a different resource group, select it from the list of available resource groups.
   * The provider for your source repository, such as GitHub or GitLab. If you want to use a different source provider, select it from the list of available repos.

1. In the Tool Integrations section, select each tool integration that you want to configure for your toolchain. For more information about configuring the tool integrations, see [Configuring tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations).
1. Click **Create**. Several steps run automatically to set up your toolchain. The tool integrations that are set up are different depending on which toolchain template you selected. For example, when you create a Microservices toolchain on {{site.data.keyword.cloud_notm}} Public, these steps are run:

   * The toolchain is created.
   * If you configured Delivery Pipeline, the pipelines are created and triggered.
   * If you configured Sauce Labs, the toolchain is set up to add Sauce Labs test jobs to the pipelines.
   * If you configured {{site.data.keyword.en_short}}, the toolchain is set up to send event notifications to the {{site.data.keyword.en_short}} service that you specified.
   * If you configured PagerDuty, the toolchain is set up to send alert notifications to the PagerDuty service that you specified.
   * If you configured Slack, the toolchain is set up to send notifications about deployment status to the Slack channel that you specified.
   * If you configured a source code tool integration such as GitHub, the sample GitHub repo is cloned into your GitHub account.

   You can now distribute event notifications by using the [{{site.data.keyword.en_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-event-notifications-integration) tool integration. {{site.data.keyword.en_full_notm}} is the preferred method for distributing notifications to PagerDuty and other communication channels such as Slack, email, SMS, push notifications, webhook, Microsoft&reg; Teams, ServiceNow, and {{site.data.keyword.IBM_notm}} {{site.data.keyword.openwhisk_short}}. For more information about using {{site.data.keyword.en_short}}, see [Enabling event notifications for toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-event-notifications-cd).
   {: tip}

## Creating a toolchain from a template with {{site.data.keyword.gitrepos}} or GitHub with the API
{: #creating_a_toolchain_git_api}
{: api}

You can create a toolchain from a template only by using the console. To view the steps for using the console, switch to the **UI** instructions.

For more information about how to create a toolchain with the API instead of by using a template, see [Adding the Git tool integration to an existing toolchain with the API](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_git&interface=api#adding_to_toolchain_api).

## Creating a toolchain from a template with {{site.data.keyword.gitrepos}} or GitHub with Terraform
{: #creating_a_toolchain_git_terraform}
{: terraform}

You can create a toolchain from a template only by using the console. To view the steps for using the console, switch to the **UI** instructions.

For more information about how to create a toolchain with Terraform instead of by using a template, see [Adding the Git tool integration to an existing toolchain with Terraform](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_git&interface=terraform#adding_to_toolchain_terraform).

## Adding the Git tool integration to an existing toolchain by using the console
{: #adding_to_toolchain_ui}
{: ui}

You can add a Git tool integration to any existing toolchain by using the console.

1. Log in to [{{site.data.keyword.cloud_notm}}](http://cloud.ibm.com){: external}.
1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **Resource list**.
1. From the Resource list, expand the **Developer tools** section.
1. Either click a toolchain to which you want to add a Git tool integration, or create a toolchain. For information about creating toolchains, see [Creating toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started&interface=ui).
1. On the Toolchain's Overview page, click **Add Tool**, and then select **GitHub** or **{{site.data.keyword.gitrepos}}** to add either of these tool integrations to your toolchain.
1. Depending on which Git tool integration you select, you can [configure the the GitHub tool integration](/docs/ContinuousDelivery?topic=ContinuousDelivery-github) or you can configure the [{{site.data.keyword.gitrepos}} tool integration](/docs/ContinuousDelivery?topic=ContinuousDelivery-grit).

To try a tutorial to create a custom toolchain, see [Create a custom toolchain](https://www.ibm.com/cloud/architecture/tutorials/create-a-custom-toolchain){: external}.
{: tip}

## Adding the Git tool integration to an existing toolchain with the API
{: #adding_to_toolchain_api}
{: api}

You can add a Git tool integration to any existing toolchain with the API.

1. [Obtain an IAM bearer token](https://{DomainName}/apidocs/resource-controller#authentication){: external}. Alternatively, if you are using an SDK, [obtain an IAM API key](https://{DomainName}/iam/apikeys){: external} and set the client options by using environment variables.
   
   ```bash
   export CD_TOOLCHAIN_AUTH_TYPE=iam && \
   export CD_TOOLCHAIN_APIKEY={iam_api_key} && \
   export CD_TOOLCHAIN_URL=https://api.{region}.devops.cloud.ibm.com/toolchain/v2
   ```
   {: pre}

2. [Determine the region and ID of the toolchain](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started&interface=api#viewing-toolchain-api) that you want to add the Git tool integration to.

3. Add the Git tool integration to the toolchain. The following example shows how to add a Git tool integration that links to an existing repo on github.com. You can also add a Git tool integration with instructions to create, fork, or clone a new repo. And you can add tool integrations for other GitHub, GitLab, or Bitbucket servers. 

   ```curl
   curl -X POST \
     https://api.{region}.devops.cloud.ibm.com/toolchain/v2/toolchains/{toolchain_id}/tools \
     -H 'Authorization: Bearer {token}' \
     -H 'Accept: application/json` \
     -H 'Content-Type: application/json' \
       -d '{
       "tool_type_id": "githubconsolidated",
       "name": "{tool_integration_name}",
       "parameters": {
         "type": "link",
         "git_id": "github",
         "repo_url": "https://github.com/{git_org}/{git-repo}.git",
         "has_issues": true
       }
     }'
   ```
   {: pre}
   {: curl}

   ```javascript
   const CdToolchainV2 = require('@ibm-cloud/continuous-delivery/cd-toolchain/v2');
   const toolchainService = CdToolchainV2.newInstance();
   ...
   (async() => {
      const gitToolModel = {
         toolchainId: {toolchain_id},
         toolTypeId: 'githubconsolidated',
         name: {tool_integration_name},
         parameters: {
            type: 'link',
            git_id: 'github',
            repo_url: 'https://github.com/{git_org}/{git-repo}.git',
            has_issues: true,

         }
      };
      const gitTool = await toolchainService.createTool(gitToolModel);
   })();
   ```
   {: codeblock}
   {: node}

   ```go
   import (
	   "github.com/IBM/continuous-delivery-go-sdk/cdtoolchainv2"
   )
   ...
   toolchainClientOptions := &cdtoolchainv2.CdToolchainV2Options{}
   toolchainClient, err := cdtoolchainv2.NewCdToolchainV2UsingExternalConfig(toolchainClientOptions)
   createGitToolOptions := toolchainClient.NewCreateToolOptions({toolchain_id}, "githubconsolidated")
   gitParameters := map[string]interface{}{
    "type": "link",
    "git_id": "github",
    "repo_url": "https://github.com/{git_org}/{git-repo}.git",
    "has_issues": true,
   }
   createGitToolOptions.SetName({tool_integration_name})
   createGitToolOptions.SetParameters(gitParameters)
   gitTool, response, err := toolchainClient.CreateTool(createGitToolOptions)
   ```
   {: codeblock}
   {: go}

   ```python
   from ibm_continuous_delivery.cd_toolchain_v2 import CdToolchainV2
   ...
   toolchain_service = CdToolchainV2.new_instance()
   git_parameters = {
      "type": "link",
      "git_id": "github",
      "repo_url": "https://github.com/{git_org}/{git-repo}.git",
      "has_issues": True
   }
   git_tool = toolchain_service.create_tool(
      name = {tool_integration_ame},
      toolchain_id = {toolchain_id},
      tool_type_id = "githubconsolidated",
      parameters = git_parameters
   )
   ```
   {: codeblock}
   {: python}

   ```java
   import com.ibm.cloud.continuous_delivery.cd_toolchain.v2.CdToolchain;
   import com.ibm.cloud.continuous_delivery.cd_toolchain.v2.model.*;
   ...
   CdToolchain toolchainService = CdToolchain.newInstance();
   HashMap<String, Object> gitParameters = new HashMap<>();
   gitParameters.put("type", "link");
   gitParameters.put("git_id", "github");
   gitParameters.put("repo_url", "https://github.com/{git_org}/{git-repo}.git");
   gitParameters.put("has_issues", true);
   CreateToolOptions createGitToolOptions = new CreateToolOptions.Builder()
      .name({tool_integration_name})
      .parameters(gitParameters)
      .toolchainId({toolchain_id})
      .toolTypeId("githubconsolidated")
      .build();
   Response<ToolchainToolPost> response = toolchainService.createTool(createGitToolOptions).execute();
   ToolchainToolPost gitTool = response.getResult();
   ```
   {: codeblock}
   {: java}

The following table lists and describes each of the variables that are used in the previous steps.   
    
| Variable | Description |
|:---------|:------------|
| `{git_org}` | The organization on github.com that contains the repo. |
| `{git_repo}` | The repo on github.com to integrate into the toolchain. |
| `{iam_api_key}` | Your IAM API key. |
| `{region}` | The region in which the toolchain resides. For example, `us-south`. |
| `{tool_integration_name}` | A name for your tool integration. |
| `{toolchain_id}` | The ID of the toolchain to which to add the tool integration. |
| `{token}` | A valid IAM bearer token. |
{: caption="Table 1. Variables for adding the Git tool integration with the API" caption-side="top"}

For more information about each of the Git tool integrations, including additional parameters that you can configure, see the following topics:

* [Configuring Bitbucket](/docs/ContinuousDelivery?topic=ContinuousDelivery-bitbucket)
* [Configuring GitHub](/docs/ContinuousDelivery?topic=ContinuousDelivery-github)
* [Configuring {{site.data.keyword.gitrepos}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-grit)
* [Configuring GitLab](/docs/ContinuousDelivery?topic=ContinuousDelivery-gitlab)

## Adding the Git tool integration to an existing toolchain with Terraform
{: #adding_to_toolchain_terraform}
{: terraform}

You can add a Git tool integration to any existing toolchain with Terraform.

1. To install the Terraform CLI and configure the {{site.data.keyword.cloud_notm}} provider plug-in for Terraform, follow the tutorial for [Getting started with Terraform on {{site.data.keyword.cloud_notm}}](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started).

2. Locate the Terraform file (for example, `main.tf`) that contains the resource block for the toolchain to which you want to add the Git tool integration. In this file, add the configuration to create the tool integration.

   The following example creates the toolchain if it does not exist and then adds a Git tool integration that links to an existing repo on github.com by using the `ibm_cd_toolchain_tool_githubconsolidated` resource. You can also add a Git tool integration with instructions to create, fork, or clone a new repo. And you can add tool integrations for other GitHub, GitLab, or Bitbucket servers. 
  
   ```terraform
   data "ibm_resource_group" "group" {
     name = "default"
   }

   resource "ibm_cd_toolchain" "cd_toolchain" {
     name              = "my toolchain"
     resource_group_id = data.ibm_resource_group.group.id
   }

   resource "ibm_cd_toolchain_tool_githubconsolidated" "my-github-tool-integration" {
     toolchain_id = ibm_cd_toolchain.cd_toolchain.id
     initialization {
       git_id = "github"
       repo_url = "https://github.com/my-org/my-repo.git"
       type = "link"
       auth_type = "pat"
       api_token = "<TOKEN>"
     }
     parameters {
       has_issues = true
     }
   }
   ```
   {: codeblock}

   Where `<TOKEN>` represents a Personal Access Token (PAT) that belongs to the GitHub account that grants access to the target repo.

3. Initialize the Terraform CLI.

   ```terraform
   terraform init
   ```
   {: pre}
   
4. Create a Terraform execution plan. This plan summarizes all of the actions that must run to add the {{site.data.keyword.DRA_short}} tool integration to the toolchain.

   ```terraform
   terraform plan
   ```
   {: pre}

5. Apply the Terraform execution plan. Terraform takes all of the required actions to add the {{site.data.keyword.DRA_short}} tool integration to the toolchain.

   ```terraform
   terraform apply
   ```
   {: pre}

For more information about each of the Git tool integration resources, including additional parameters that you can configure, see the argument reference details in the Terraform Registry documentation: 

* Bitbucket: [`ibm_cd_toolchain_tool_bitbucketgit`](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/cd_toolchain_tool_bitbucketgit){: external}
* GitHub: [`ibm_cd_toolchain_tool_githubconsolidated`](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/cd_toolchain_tool_githubconsolidated){: external}
* {{site.data.keyword.gitrepos}}: [ibm_cd_toolchain_tool_hostedgit](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/cd_toolchain_tool_hostedgit){: external}
* GitLab: [`ibm_cd_toolchain_tool_gitlab`](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/cd_toolchain_tool_gitlab){: external}

For more information about using Terraform with {{site.data.keyword.contdelivery_short}}, see [Setting up Terraform for {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-terraform-setup).
