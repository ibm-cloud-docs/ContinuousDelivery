---

copyright:
  years: 2024
lastupdated: "2025-12-04"

keywords: Continuous Delivery, toolchain, client owned data

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Understanding data portability for {{site.data.keyword.contdelivery_short}}
{: #data-portability}

Data portability involves a set of tools and procedures that enable you to export the digital artifacts that would be needed to implement similar workloads and data processing with different service providers or on-premises software. It includes procedures for copying and storing customer-owned data that is held by the {{site.data.keyword.contdelivery_short}} service, and for related configurations used by the service to store and process customer owned data.
{: shortdesc}

## Responsibilities
{: #data-portability-responsibilities}

{{site.data.keyword.Bluemix_notm}} services provide interfaces and instructions to guide you through the process of copying and storing service customer content, including the related configuration, in your selected location.

You're responsible for the use of the exported data and configuration for data portability to other infrastructures, which includes:

- The planning and execution for setting up alternative infrastructure on different cloud providers or on-premises software that provide similar capabilities to the {{site.data.keyword.IBM_notm}} services.
- The planning and execution for the porting of the required application code on the alternative infrastructure, including the adaptation of your application code, deployment automation, and more.
- The conversion of the exported data and configuration to the format that is required by the alternative infrastructure and adapted applications.

To find out more about responsibility ownership for using {{site.data.keyword.cloud}} products between {{site.data.keyword.IBM_notm}} and the customer, see [Shared responsibilities for {{site.data.keyword.cloud_notm}} products](/docs/overview?topic=overview-shared-responsibilities).

For more information about your responsibilities for {{site.data.keyword.contdelivery_short}}, see [Your responsibilities with using {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-responsibilities-cd).

## Data export procedures
{: #data-portability-procedures}

{{site.data.keyword.contdelivery_short}} provides the mechanisms to export your content that is uploaded, stored, and processed when you use the service. In addition, {{site.data.keyword.contdelivery_short}} provides mechanisms to export settings and configurations that are used to process your content. Data retrieval procedures are organized below by the major components of the {{site.data.keyword.contdelivery_short}} service.

### Prerequisites
{: #pre-req-cd}

All data retrieval procedures require sufficient access rights. For more information, see [Managing user access for Continuous Delivery in resource groups](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security) and [Managing access for toolchains in resource groups](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security).

Some data retrieval procedures use the {{site.data.keyword.cloud}} command line interface (CLI) or {{site.data.keyword.cloud}} APIs. Before you attempt to export data, complete the following steps:

1. [Install the stand-alone IBM Cloud CLI](/docs/cli?topic=cli-install-ibmcloud-cli).
1. Open a command shell.
1. Before using the CLI to retrieve data, run `ibmcloud login` to authenticate to {{site.data.keyword.cloud}}.
1. Before invoking APIs to retrieve data, run `export TOKEN=$(ibmcloud iam oauth-tokens | sed 's!^IAM *token: *Bearer *!!')` to obtain and assign a bearer token to the `TOKEN` environment variable.
1. Before invoking APIs to retrieve data, set the `REGION` environment variable to the region that contains the instance of {{site.data.keyword.contdelivery_short}} from which you want to retrieve data. Example: `export REGION=us-south`.

Some of the following procedures use the open source tool [`curl`](https://curl.se){: external} to retrieve data from HTTP APIs. Some procedures use [`jq`](https://jqlang.org/){: external} to process JSON data that is returned from HTTP APIs. Use of these tools is not mandatory. At your discretion, you can substitute different tools or techniques to retrieve and process the data.
{: tip}

### {{site.data.keyword.contdelivery_short}} service instances
{: #data-portability-procedures-cd}

{{site.data.keyword.contdelivery_short}} service instances directly manage authorized user email addresses, and computed usage and billing metrics. Most client-owned data is processed by toolchains and tools that are associated with {{site.data.keyword.contdelivery_short}} service instances.

For related information about modifying, exporting, or deleting personal data in the CD service, see [Managing personal data for {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_personal_data).
{: tip}

#### Authorized user email addresses
{: #data-portability-procedures-cd-emails}

To retrieve the list of email addresses, complete the following steps:

1. Open the [resource list](https://cloud.ibm.com/resources){: external}.
1. Select **Developer tools**.
1. Click the {{site.data.keyword.contdelivery_short}} service instance of interest.
1. Select **Manage** > **Authorized users**.
1. Select and copy the contents of the table of email addresses to the clipboard, and paste to a plain text file.

For more information about managing authorized users, see [Plan limitations and usage](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#authorized_users).

### Toolchains and tool integrations
{: #data-portability-procedures-toolchains}

The configurations of {{site.data.keyword.contdelivery_short}} toolchains and tool integrations consist of client-owned data.

#### Toolchain configurations
{: #data-portability-procedures-toolchains-configs}

You can retrieve a list of toolchains and their configurations by using the [Toolchain API](/apidocs/toolchain){: external}, specifically the methods to [Get a list of toolchains](/apidocs/toolchain#list-toolchains){: external} or [Get a toolchain](/apidocs/toolchain#get-toolchain-by-id){: external}. To retrieve toolchain configuration data, complete the following steps:

1. `GET https://resource-controller.cloud.ibm.com/v2/resource_groups` to retrieve a list of resource groups in the account.
1. For each resource group, `GET https://api.$REGION.devops.cloud.ibm.com/toolchain/v2/toolchains?resource_group_id=$RG_ID` to retrieve the list of toolchains in the resource group.

You can also retrieve a subset of Toolchain resource metadata by using the [Global Search API](https://cloud.ibm.com/apidocs/search){: external} or the [Resource Controller API](https://cloud.ibm.com/apidocs/resource-controller/resource-controller){: external}.
{: tip}

#### Tool integration configurations
{: #data-portability-procedures-toolchains-integrations}

You can retrieve tool integration configuration data by using the [Toolchain API](https://cloud.ibm.com/apidocs/toolchain){: external}, specifically the methods to [Get a list of tools bound to a toolchain](https://cloud.ibm.com/apidocs/toolchain#list-tools){: external} and to [Get a tool](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}. To retrieve tool integration configuration data, complete the following steps:

1. For a specific toolchain, use `GET https://api.$REGION.devops.cloud.ibm.com/toolchain/v2/toolchains/$TOOLCHAIN_ID/tools` to retrieve configuration details for all tool integrations in the toolchain.

You cannot retrieve secret properties from {{site.data.keyword.contdelivery_short}}. Some of the properties of a tool integration configuration are secrets, such as access tokens, API keys, and passwords. It's a best practice to configure these properties by reference to a secrets store, such as {{site.data.keyword.secrets-manager_short}}. In this case, the API returns strings that reference the locations of the properties in their secrets stores. If secret property values are stored directly in a tool integration configuration, the API doesn't return the secret values, only a hash of the value for information security.
{: exception}

### Delivery pipelines
{: #data-portability-procedures-pipelines}

Client-owned data in {{site.data.keyword.contdelivery_short}} pipelines fall into two categories:

- Customer provided data constituting the configuration of pipelines, pipeline definitions, pipeline properties, pipeline triggers, and pipeline run requests.
- Pipeline-generated data, namely execution logs and metrics, produced during the execution of Tekton pipeline steps and Classic Pipeline jobs.

{{site.data.keyword.contdelivery_short}} supports two pipeline architectures: Classic and Tekton. The method for retrieving information differs for each.

#### Tekton pipelines
{: #data-portability-procedures-pipelines-tekton-list}

You can retrieve a list of Tekton pipelines that are integrated into a toolchain by using the [Toolchain API](https://cloud.ibm.com/apidocs/toolchain){: external}. To retrieve the list of Tekton pipelines, complete the following steps:

1. For a specific toolchain, use `GET https://api.$REGION.devops.cloud.ibm.com/toolchain/v2/toolchains/$TOOLCHAIN_ID/tools` to obtain a list of all tool integrations in the toolchain.
1. Use a tool such as [jq](https://jqlang.github.io/jq){: external} to filter the list to only pipeline tool integrations, and to derive the corresponding pipeline IDs.
   - Use the following command to produce a list of IDs for all Tekton and Classic pipelines in a toolchain: `curl -s -X GET -H "Authorization: Bearer $TOKEN" -H "Accept: application/json" https://api.$REGION.devops.cloud.ibm.com/toolchain/v2/toolchains/$TOOLCHAIN_ID/tools | jq -r '.tools[] | select(.tool_type_id == "pipeline").id'`
   - Use the following command to produce a list of IDs for all Tekton pipelines in a toolchain: `curl -s -X GET -H "Authorization: Bearer $TOKEN" -H "Accept: application/json" https://api.$REGION.devops.cloud.ibm.com/toolchain/v2/toolchains/$TOOLCHAIN_ID/tools | jq -r '.tools[] | select(.tool_type_id == "pipeline" and .parameters.type == "tekton").id'`
   - Use the following command to produce a list of IDs of all Classic pipelines in a toolchain: `curl -s -X GET -H "Authorization: Bearer $TOKEN" -H "Accept: application/json" https://api.$REGION.devops.cloud.ibm.com/toolchain/v2/toolchains/$TOOLCHAIN_ID/tools | jq -r '.tools[] | select(.tool_type_id == "pipeline" and .parameters.type == "classic").id'`

#### Tekton pipeline configurations
{: #data-portability-procedures-pipelines-tekton-configs}

You can retrieve the configuration of a Tekton pipeline, including its definitions, properties, triggers, and trigger properties, by using the [Tekton Pipeline API](https://cloud.ibm.com/apidocs/tekton-pipeline){: external}, specifically the method to [Get Tekton pipeline data](https://cloud.ibm.com/apidocs/tekton-pipeline#get-tekton-pipeline){: external}.

To work with Classic pipelines, see [Classic pipeline configurations](#data-portability-procedures-pipelines-classic-configs).
{: tip}

To retrieve configuration data about a Tekton pipeline, complete the following step:

1. For a specific Tekton pipeline, use `GET https://api.$REGION.devops.cloud.ibm.com/pipeline/v2/tekton_pipelines/$TEKTON_PIPELINE_ID` to retrieve the configuration of the pipeline.

Responses from this method do not include pipeline runs. To retrieve data about pipeline runs, see [Tekton pipeline runs](#data-portability-procedures-pipelines-tekton-runs).
{: note}

#### Tekton pipeline runs
{: #data-portability-procedures-pipelines-tekton-runs}

Pipeline run data is the result of running, not configuring, pipelines. It is not considered essential to implementing pipeline workloads with different service providers or on-premises software. Therefore, this section is included as a convenience, not as a requisite of data portability.
{: note}

You can retrieve metadata about pipeline runs by using the Tekton pipeline API method to [List pipeline run records](https://cloud.ibm.com/apidocs/tekton-pipeline#list-tekton-pipeline-runs){: external}.

1. For a specific Tekton pipeline, use `GET https://api.$REGION.devops.cloud.ibm.com/pipeline/v2/tekton_pipelines/$TEKTON_PIPELINE_ID/pipeline_runs` to retrieve a list of pipeline runs.

The response includes detailed information about pipeline runs, except for pipeline logs. To retrieve pipeline logs, see [Tekton pipeline logs](#data-portability-procedures-pipelines-tekton-logs).

#### Tekton pipeline logs
{: #data-portability-procedures-pipelines-tekton-logs}

Pipeline run logs result from running, not configuring, pipelines. They are not considered essential to implementing pipeline workloads with different service providers or on-premises software. Therefore, this section is included as a convenience, not as a requisite of data portability.
{: note}

You can retrieve pipeline logs by using Tekton pipeline API methods to [Get a list of pipeline run log objects](https://cloud.ibm.com/apidocs/tekton-pipeline#get-tekton-pipeline-run-logs){: external} and to [Get the log content of a pipeline run step](https://cloud.ibm.com/apidocs/tekton-pipeline#get-tekton-pipeline-run-log-content){: external}.

To retrieve logs, complete the following steps:

1. For a specific Tekton pipeline, use `GET https://api.$REGION.devops.cloud.ibm.com/pipeline/v2/tekton_pipelines/$TEKTON_PIPELINE_ID/pipeline_runs/$RUN_ID/logs` to retrieve a list of pipeline run log descriptors, including log descriptor IDs.
1. For a specific log descriptor, use `GET https://api.$REGION.devops.cloud.ibm.com/pipeline/v2/tekton_pipelines/$TEKTON_PIPELINE_ID/pipeline_runs/$RUN_ID/logs/$LOG_ID` to return the log contents.

#### Classic pipeline configurations
{: #data-portability-procedures-pipelines-classic-configs}

You can retrieve the configuration of a Classic pipeline by using the `ibmcloud dev pipeline-get` CLI. This CLI is for Classic pipelines only. To work with Tekton pipelines, see [Tekton pipeline configurations](#data-portability-procedures-pipelines-tekton-configs).

To retrieve the configuration of a Classic pipeline, complete the following steps:

1. For a specific Classic pipeline, run `ibmcloud dev pipeline-get $CLASSIC_PIPELINE_ID --output JSON`.

#### Classic pipeline runs
{: #data-portability-procedures-pipelines-classic-runs}

Pipeline run data is the result of running, not configuring, pipelines. It is not considered essential to implementing pipeline workloads with different service providers or on-premises software. Therefore, this section is included as a convenience, not as a requisite of data portability.
{: note}

To produce Classic pipeline run data, trigger a run. You can trigger a run by using the `ibmcloud dev pipeline-run` CLI. This CLI is for Classic pipelines only. To work with Tekton pipeline runs, see [Tekton pipeline runs](#data-portability-procedures-pipelines-tekton-runs). To trigger a run and retrieve information about the run, complete the following step:

1. For a specific Classic pipeline, run `ibmcloud dev pipeline-run $CLASSIC_PIPELINE_ID --output JSON`.

#### Classic pipeline logs
{: #data-portability-procedures-pipelines-classic-logs}

Pipeline run data is the result of executing, not configuring, pipelines. It is not considered essential to implementing pipeline workloads with different service providers or on-premises software. Therefore, this section is included as a convenience, not as a requisite of data portability.
{: note}

You can retrieve Classic pipeline logs by using the `ibmcloud dev pipeline-log` CLI. This CLI is for Classic pipelines only. To work with Tekton pipeline logs, see [Tekton pipeline logs](#data-portability-procedures-pipelines-tekton-logs). To retrieve logs, run the following command:

1. For a specific Classic pipeline, run `ibmcloud dev pipeline-log $CLASSIC_PIPELINE_ID`.

### Git Repos and Issue Tracking
{: #data-portability-procedures-git}

Git Repos and Issue Tracking are powered by GitLab Community Edition. Procedures for exporting or retrieving data from Git Repos and Issue Tracking are the same as those for GitLab. Data retrieval procedures are scoped to individual projects. Procedures that involve the GitLab API require an authentication token, such as a personal access token. For more information, see [Authentication](https://docs.gitlab.com/api/rest/#authentication){: external} in the GitLab Docs.

#### GitLab projects
{: #data-portability-procedures-git-projects}

If you want to migrate a Git Repos and Issue Tracking project to another instance of GitLab, use the “Export Project” feature. To export a project archive, complete the following steps:

1. Go to the Git Repos and Issue Tracking home page for the project of interest.
1. Select **Settings** > **General** > **Advanced** > **Export Project**.
1. The export process runs in the background. After the process completes, a **Download Export** button appears on the Export Project section of the page. You are also sent an email with a link to download the archive.

For more information about the "Export Project" feature, see [Migrate projects and groups by using file exports](https://docs.gitlab.com/user/project/settings/import_export/){: external} in the GitLab Docs.

If you want to harvest data from Git Repos and Issue Tracking for use in another system, the "Export Project" feature might not be appropriate. Review the following sections for alternative methods for exporting GitLab data.
{: tip}

#### GitLab project repositories
{: #data-portability-procedures-git-repos}

You can obtain a copy of a project's file repository, complete with its commit history, by cloning the project repository to a local file system. To clone a Git Repos and Issue Tracking project, see [Setting up local clients to work with Git source control](/docs/ContinuousDelivery?topic=ContinuousDelivery-git_local).

#### Current GitLab project repository files
{: #data-portability-procedures-git-files}

You can obtain an archive that contains the current files in any branch of a project. An archive that you export this way does not include the commit history. To export an archive, complete the following steps:

1. Go to the Git Repos and Issue Tracking home page for the project of interest.
1. Select the branch of the repository that you want to export.
1. Click the **Code**.
1. Choose an export format, such as `zip`, `tar`, `tar.gz`, or `tar.bz2`.

For more information, see [Download repository source code](https://docs.gitlab.com/user/project/repository/#download-repository-source-code){: external} in the GitLab Docs.

#### GitLab merge requests
{: #data-portability-procedures-git-mergerequests}

To export the data of a project's merge requests, complete the following steps:

1. From the Git Repos and Issue Tracking home page for the project, select **Code** > **Merge requests**.
1. Query for all merge requests of interest.
1. Select **Actions** ![List of actions icon](../icons/action-menu-icon.svg) > **Export as CSV**.

For more information, see [Export merge requests to CSV](https://docs.gitlab.com/user/project/merge_requests/csv_export/){: external} in the GitLab Docs.

#### GitLab issues
{: #data-portability-procedures-git-issues}

To export the data of a project's issues, complete the following steps:

1. From the Git Repos and Issue Tracking home page for the project, select **Plan** > **Issues**.
1. Query for all applicable issues.
1. Select **Actions** ![List of actions icon](../icons/action-menu-icon.svg) > **Export as CSV**.

For more information, see [Export issues to CSV](https://docs.gitlab.com/user/project/issues/csv_export/){: external}.

#### GitLab snippets
{: #data-portability-procedures-git-snippets}

You can retrieve snippets from a Git Repos and Issue Tracking project. To retrieve snippets, complete the following steps:

1. Use the GitLab `GET /snippets/all` API to list all snippets to which you have access. This includes personal and project snippets. For more information, see [List all snippets](https://docs.gitlab.com/api/snippets/#list-all-snippets){: external} in the GitLab API Docs.
1. Use the GitLab `GET /snippets/:id/raw` API to retrieve the raw content of each snippet of interest. For more information, see [Single snippet contents](https://docs.gitlab.com/api/snippets/#single-snippet-contents){: external} in the GitLab API Docs.

You cannot retrieve private snippets that belong to another user. If you need to obtain private snippets of another user, contact the user and request access to their snippets, or that they export their snippets.
{: exception}

For more information, see [Snippets](https://docs.gitlab.com/user/snippets/){: external} in the GitLab Docs.

#### GitLab project members
{: #data-portability-procedures-git-users}

You can obtain a list of member users of a Git Repos and Issue Tracking project. To list member users and their basic metadata, use the following command:

1. Use the GitLab `GET /projects/:id/members` API to list members of the project.

You can't retrieve detailed information about users other than yourself. If you need to obtain detailed user metadata for members of your project, contact the users on the members list and request that they export their details.
{: exception}

For more information, see [List all members of a group or project](https://docs.gitlab.com/api/group_members/#list-all-members-of-a-group){: external} in the GitLab API Docs.

#### GitLab Wikis
{: #data-portability-procedures-git-wikis}

You can obtain a copy of a project wiki by cloning the wiki repository to a local file system. To clone a Git Repos and Issue Tracking wiki, complete the following steps:

1. From the Git Repos and Issue Tracking home page for the project, select **Plan** > **Wiki**.
1. Select **Actions** ![List of actions icon](../icons/action-menu-icon.svg) > **Clone repository**.

For more information, see [Create or edit wiki pages locally](https://docs.gitlab.com/user/project/wiki/#create-or-edit-wiki-pages-locally){: external}.

### DevOps Insights
{: #data-portability-procedures-insights}

Client-owned data in DevOps Insights falls into three basic categories:

- Client provided configurations of DevOps Insights policy rules.
- Client generated build, deploy, and test records that are uploaded, usually from pipeline steps and jobs, to DevOps Insights.
- Analytics computed by DevOps Insights from uploaded build, deploy, and test records.

Build record, deploy record, test record, and analytics data are the result of running {{site.data.keyword.contdelivery_short}} pipeline workloads. As computed, not configuration, data, it is not considered essential to implementing workloads similar to DevOps Insights with different service providers or on-premises software.

#### DevOps Insights policies and rules
{: #data-portability-procedures-insights-rules}

A DevOps Insights policy is defined by the rules within it. These are managed by using the DevOps Insights GUI. To retrieve the details of policy rules, complete the following steps:

1. Select a toolchain from the Overview page.
1. Type "DevOps Insights" into the search field.
1. If there is a **DevOps Insights** tool integration in the toolchain, select it.
1. Select **Policies** in the DevOps Insights dashboard.
1. For each policy of interest, select **Manage policies** > **Actions** ![List of actions icon](../icons/action-menu-icon.svg) > **Edit Rules**.
1. For each rule of interest, select **Manage rules** > **Actions** ![List of actions icon](../icons/action-menu-icon.svg) > **Edit**.
1. Copy the data in the resulting dialog to the clipboard, and paste to a plain text file.

### Code Risk Analyzer
{: #data-portability-procedures-cra}

No client-owned data is in Code Risk Analyzer that is needed to implement similar workloads with different service providers or on-premises software.

## Exported data formats
{: #data-portability-data-formats}

{{site.data.keyword.contdelivery_short}} supports the following data formats and schemas of the exported data, configuration, and application:

| Format | Data |
|:-------|:-----|
| JSON | Most of the [Data export procedures](#data-portability-procedures) produce data in JSON format, conforming to associated API specifications. |
| Plain text | Classic pipeline logs and GitLab snippets. |
| CSV | Git Repos and Issue Tracking (GitLab) merge requests and issues. |
| Files and file archives | Git Repos and Issue Tracking (GitLab) projects and repositories. |
| RFC 5322 email addresses | {{site.data.keyword.contdelivery_short}} authorized user email addresses. |
{: caption="Exported data formats" caption-side="top"}

{{site.data.keyword.contdelivery_short}} does not support the export of the following data format and schema of the exported data, configuration, and application:

- Secret tool integration and secure pipeline properties are not exported due to the sensitive nature of the properties. For more information and best practices about managing secrets and secure properties, see [Protecting your credentials by using secrets references](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security#cd_secrets_references).
- Build, test, and deploy records that are uploaded to DevOps Insights and resulting analytics are not exported because this constitutes data that is produced in the execution of delivery pipelines, not data employed in the configuration of delivery pipeline workloads with other service providers or on-premises software.

## Data ownership
{: #data-portability-ownership}

All exported data is classified as customer content. Apply the full customer ownership and licensing rights, as stated in the [IBM Cloud Service Agreement](https://www.ibm.com/support/customer/csol/terms/?id=Z126-6304_WS&cc=in&lc=en).
