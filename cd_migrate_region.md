---

copyright:
  years: 2025
lastupdated: "2026-01-05"

keywords: migrate, migration, migrating, region, resource group, Terraform, Tekton, pipeline, toolchain, git, continuous delivery, IBM Cloud, tools, resource, resources, data

subcollection: ContinuousDelivery

content-type: tutorial
services: ContinuousDelivery
account-plan: paid
completion-time: 60m

---

{{site.data.keyword.attribute-definition-list}}

# Migrate {{site.data.keyword.contdelivery_short}} resources to another region
{: #cd-migrate-region}
{: toc-content-type="tutorial"}
{: toc-services="ContinuousDelivery"}
{: toc-account-plan="paid"}
{: toc-completion-time="60m"}

You can migrate {{site.data.keyword.contdelivery_short}} resources, including toolchains, tool integrations, Tekton {{site.data.keyword.deliverypipeline}}s, and {{site.data.keyword.gitrepos}} projects and groups to another region by copying the resources using the [@ibm-cloud/cd-tools](https://www.npmjs.com/package/@ibm-cloud/cd-tools){: external} tools.
{: shortdesc}

## Supported resources
{: #cd-migrate-region-supported-resources}

The following resources are supported for migration to another region -

| Resource | Has support for migration|
| :- | :- |
| [Toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using) | Yes <sup>[1](#cd-migrate-region-limitations-toolchain)</sup> |
| [{{site.data.keyword.gitrepos}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-git_working) | Yes <sup>[2](#cd-migrate-region-limitations-grit)</sup> |
| [{{site.data.keyword.deliverypipeline}} (Tekton)](/docs/ContinuousDelivery?topic=ContinuousDelivery-tekton-pipelines) | Yes <sup>[3](#cd-migrate-region-limitations-toolchain)</sup> |
| [{{site.data.keyword.deliverypipeline}} (Classic)](/docs/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about) | No |
| [{{site.data.keyword.DRA_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-di_working) | No |
| [Other Tool Integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations) | Yes |
{: caption="Supported resources" caption-side="bottom"}

## Limitations for Toolchains and {{site.data.keyword.deliverypipeline}}
{: #cd-migrate-region-limitations-toolchain}

Migration of resources from one region to another is subject to the following limitations.

1. [Classic pipelines](/docs/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about) are not supported.
1. [{{site.data.keyword.DRA_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-di_working) is not supported.
1. Secrets stored directly in Toolchains or {{site.data.keyword.deliverypipeline}} (environment properties or trigger properties) will not be copied. An `export-secrets` command is provided to export secrets into a [{{site.data.keyword.secrets-manager_short}}](/docs/secrets-manager?topic=secrets-manager-getting-started) instance, replacing the stored secrets with secret references. Secret references are supported. It is recommended to store secrets in [{{site.data.keyword.secrets-manager_short}}](/docs/secrets-manager?topic=secrets-manager-getting-started).
1. Tekton pipeline webhook trigger secrets will not be copied, as references are not supported for webhook trigger secrets. You will need to add the secret after copying the toolchain.
1. Tekton pipeline run history, logs, and assets will not be copied. You can keep the original pipelines for some time to retain history.
1. GitHub and {{site.data.keyword.gitrepos}} tool integrations configured with OAuth type authentication will automatically be converted to use the OAuth identity of the user performing the copy (the owner of the API key) rather than the original user. This is to simplify the copy operation. You can re-configure the tool integrations after copying to use a different user.
1. {{site.data.keyword.gitrepos}} tool integrations that use Personal Access Tokens (PATs) for authentication will automatically be converted to use OAuth. You can re-configure the tool integrations after copying to use a PAT again.

## Limitations for {{site.data.keyword.gitrepos}}
{: #cd-migrate-region-limitations-grit}

The following limitations apply only if you are migrating [{{site.data.keyword.gitrepos}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-git_working) projects.

1. Personal projects are not supported. If you created a project under a [personal namespace](https://docs.gitlab.com/user/namespace/){: external}, you can either [move your personal project to a group](https://docs.gitlab.com/tutorials/move_personal_project_to_group/){: external}, or [convert your personal namespace into a group](https://docs.gitlab.com/tutorials/convert_personal_namespace_to_group/){: external}. It is recommended that you store projects in groups, as they allow multiple administrators and allow better continuity of a project over time.
1. This command requests a GitLab direct transfer and is subject to the [limitations of using direct transfer](https://docs.gitlab.com/user/group/import/#known-issues){: external}.
1. Copying large projects, or projects with large files or many resources, can take time.
1. As each region of {{site.data.keyword.gitrepos}} is independent, your projects' users may not yet exist in the destination region. The `copy-project-group` command will ensure that the users exist in the new region, however there may be user name conflicts with other users in the destination region. In the event of a user name conflict, the user name in the destination region may be changed slightly by adding a suffix.

## Overview
{: #cd-migrate-region-overview}

The recommended approach to migrate {{site.data.keyword.contdelivery_short}} resources from one region to another is to **copy** the resources to the new region using the migration tools described in this migration guide. Your original resources will still be available in the original region and you can continue to use them until you've validated the resources in the new region and are ready to transition.

The recommended steps for migrating {{site.data.keyword.contdelivery_short}} resources to another region are:

1. Copy {{site.data.keyword.gitrepos}} projects to the new region (if applicable)
1. Export secrets stored in toolchains or Tekton pipelines to {{site.data.keyword.secrets-manager_short}} (if applicable)
1. Copy toolchains (including Tekton pipelines) to the new region
1. Validate the resources in the new region
1. Disable the original resources

If you are migrating [{{site.data.keyword.gitrepos}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-git_working) projects, then after copying the projects to the new region, any changes made to the original projects will not reflect in the copy. As such, you should notify your team that a migration is in progress so that changes made during the migration are not lost.
{: tip}

Migration tools are provided as command-line tools in the form of an [npx](https://docs.npmjs.com/cli/commands/npx){: external} command. [npx](https://docs.npmjs.com/cli/commands/npx){: external} (Node Package Execute) is a utility provided with [Node.js](https://nodejs.org/){: external} which automatically downloads a module and its dependencies, and runs it on your machine. 

The [@ibm-cloud/cd-tools](https://www.npmjs.com/package/@ibm-cloud/cd-tools){: external} npx utility provides the following commands:
* [copy-toolchain](https://github.com/IBM/continuous-delivery-tools?tab=readme-ov-file#copy-toolchain){: external}: Copies a toolchain, including tool integrations and Tekton pipelines, to another region or resource group
* [copy-project-group](https://github.com/IBM/continuous-delivery-tools?tab=readme-ov-file#copy-project-group){: external}: Copies a group of {{site.data.keyword.gitrepos}} projects to another region
* [export-secrets](https://github.com/IBM/continuous-delivery-tools?tab=readme-ov-file#export-secrets){: external}: Exports secrets stored directly in toolchains or pipelines to {{site.data.keyword.secrets-manager_short}}

The following sections describe each step of the migration in more detail.

## Prerequisites
{: #cd-migrate-region-prereqs}

To perform the migration, you will need the following -

* An [{{site.data.keyword.cloud_notm}} API key](/docs/account?topic=account-manapikey) with the IAM access listed below.
* **Viewer** access for the source Toolchain(s) being copied
* **Editor** access for creating new Toolchains in the target region
* **Administrator** access for other {{site.data.keyword.cloud_notm}} service instances that have a tool integration with IAM service-to-service authorizations, such as [{{site.data.keyword.secrets-manager_short}}](/docs/secrets-manager?topic=secrets-manager-getting-started), [Event Notifications](/docs/event-notifications?topic=event-notifications-getting-started), etc.
* Access to any GitHub or {{site.data.keyword.gitrepos}} **repositories** referenced by tool integrations in the toolchain, with permission to **read the repository** and **create webhooks**. This is required in order to create pipeline Git type triggers, which require a webhook to be added on the repository to trigger the pipeline, and for the pipeline to be able to clone the repositories during execution.
* A [{{site.data.keyword.contdelivery_short}}](/catalog/services/continuous-delivery) service instance is required in the target region and resource group in order to properly create the toolchain copy. Note that {{site.data.keyword.contdelivery_short}} capabilities ({{site.data.keyword.deliverypipeline}}, {{site.data.keyword.gitrepos}}, etc) are subject to the plan of the {{site.data.keyword.contdelivery_short}} instance in the same region and resource group as the toolchain. [Learn more](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage)
* Personal Access Tokens (PAT) for the {{site.data.keyword.gitrepos}} service in the **source** and **destination** regions, with the `api` scope. These are only required if migrating {{site.data.keyword.gitrepos}} projects.

### Important notes
{: #cd-migrate-region-important-notes}

You must review the following important notes before you begin migration.

Billing considerations
:   During the migration, you will need to create a new [{{site.data.keyword.contdelivery_short}}](/catalog/services/continuous-delivery) instance in the destination region and resource group to enable your toolchains, pipelines, and projects in the destination region. You may also wish to keep the original resources in the source region available for use until you have transitioned to the new region. If you use the {{site.data.keyword.contdelivery_short}} service with the **Professional** plan, please be aware that you will be charged for both regions according to the number of authorized users configured in each instance. If costs are a concern, you can change the plan in the source region's {{site.data.keyword.contdelivery_short}} instance to Lite once you have transitioned to the new region. The resources will be read-only if you have exceeded the Lite plan limits. However you can change back to the Professional plan at any time if you wish to use it again.

Duplicate Pipeline runs
:   During the migration, you may create new pipelines in the destination region. If those pipelines have timed triggers set to run automatically on a schedule, or Git triggers configured to run automatically on Git events like PRs or commits, those events could trigger duplicate pipeline runs (one in the original pipeline and one in the new pipeline). To avoid potential disruption, copied pipelines will have these types of triggers disabled by default. It is recommended to manage these triggers such that there is only one set enabled at a time. Once you are comfortable with the transition to the new pipeline, you can enable the triggers on it and disable the triggers on the original pipeline.

## Install dependencies
{: #cd-migrate-region-install}
{: step}

The [@ibm-cloud/cd-tools](https://www.npmjs.com/package/@ibm-cloud/cd-tools){: external} runs on your local machine, and requires [Node.js](https://nodejs.org/){: external} to be installed. The `copy-toolchain` command works by first serializing a toolchain and its tool integrations (including Tekton pipelines) into [Terraform](https://developer.hashicorp.com/terraform){: external} (.tf) files, then applying the Terraform files to the new region to create the toolchain copy.

To use the [@ibm-cloud/cd-tools](https://www.npmjs.com/package/@ibm-cloud/cd-tools){: external} npx utility on your local machine, first install the required dependencies:
* Node.js v20 (or later)
* Terraform v1.13.3 (or later)

### MacOS
{: #cd-migrate-region-install-OnMacOS}

Run the following commands to install dependencies on MacOS.

```bash
brew install node
brew tap hashicorp/tap
brew install hashicorp/tap/terraform
```
{: pre}

### Other platforms
{: #cd-migrate-region-install-OnOtherPlatforms}

* Node.js [install instructions](https://nodejs.org/en/download){: external}
* Terraform [install instructions](https://developer.hashicorp.com/terraform/install){: external}

## Create a {{site.data.keyword.contdelivery_short}} instance in the target region
{: #cd-migrate-cd-instance}
{: step}

In order to successfully provision a copy of your toolchain(s) in a new region or resource group, you should ensure that there is a [{{site.data.keyword.contdelivery_short}}](/catalog/services/continuous-delivery) service instance in that region and in the target resource group.

To view your [{{site.data.keyword.contdelivery_short}}](/catalog/services/continuous-delivery) service instances, open the [Resource List](/resources) page, then select your account in the header of the page. The service instances will be shown in the **Developer tools** section.

If you do not yet have a {{site.data.keyword.contdelivery_short}} instance, see [Creating a {{site.data.keyword.contdelivery_short}} service instance](/docs/ContinuousDelivery?topic=ContinuousDelivery-create_cd_service).

## Copy {{site.data.keyword.gitrepos}} projects
{: #cd-migrate-region-copy-grit}
{: step}

This step only applies if you use [{{site.data.keyword.gitrepos}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-git_working) projects in {{site.data.keyword.cloud_notm}}. If you don't use these, you can skip this step.
{: note}

If you use [{{site.data.keyword.gitrepos}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-git_working) projects, they must be copied to the new region before the toolchains and pipelines. Follow these steps to copy your projects and groups.

1. Determine the list of groups to copy.
  
   A [group](https://docs.gitlab.com/user/group/){: external} is a collection of related projects. The group name is part of the URL path of a project. For example, for the project url `https://us-south.git.cloud.ibm.com/my-group/my-project`, the group is `my-group`. If you created a project under a [personal namespace](https://docs.gitlab.com/user/namespace/){: external}, you can either [move your personal project to a group](https://docs.gitlab.com/tutorials/move_personal_project_to_group/){: external}, or [convert your personal namespace into a group](https://docs.gitlab.com/tutorials/convert_personal_namespace_to_group/){: external}. It is recommended that you store projects in groups, as they allow multiple administrators and allow better continuity of a project over time.

1. For each group, run the `copy-project-group` command from [@ibm-cloud/cd-tools](https://www.npmjs.com/package/@ibm-cloud/cd-tools){: external} to copy the group to the new region.

   For example, the following command copies the group `my-group` and all its projects from the `us-east` (Washington DC) region to the `us-south` (Dallas) region using the personal access tokens (PATs) provided.
   ```bash
   npx @ibm-cloud/cd-tools copy-project-group -g my-group -s us-east -d us-south --st ${PAT_US_EAST} --dt ${PAT_US_SOUTH} 
   ```
   {: pre}

   Note that for large groups or projects this step may take time.

1. Verify that the projects in the group were copied successfully.

   Before continuing, it's important to make sure that no data is missing. Ensure that the correct users are included as members to the projects, and spot check the data in the projects (repos, issues, etc) to ensure the data is intact. Note that personal access tokens are not included in the copy.

## Copy Toolchains and Tekton pipelines
{: #cd-migrate-region-copy-toolchains}
{: step}

Next, copy your toolchains to the new region. Tool integrations, including Tekton pipelines, will be included in the copy of the toolchain, with the limitations stated in the above Limitations sections. You can find your toolchains in the [Resource list](/resources) page, or in the [Toolchains](/automation/toolchains) page under [Platform Automation](/automation/overview). 

### CRN
{: #cd-migrate-region-getCRN}

{{site.data.keyword.cloud_notm}} resources are uniquely identified by a [Cloud Resource Name (CRN)](/docs/account?topic=account-crn). You will need the CRN of the toolchain you want to copy. You can get the CRN of a toolchain a few ways:

1. Locate the toolchain in the [Platform Automation](/automation) > [Toolchains](/automation/toolchains) page, open the toolchain, and click **Details** to see the toolchain details, which shows the CRN.
1. Locate the toolchain in the [Resource list](/resources) page, click on the toolchain row to expand the details panel, which shows the CRN.
1. Using the [ibmcloud cli](/docs/cli?topic=cli-getting-started), you can list toolchains and their CRNs via
   ```bash
   ibmcloud resource service-instances --service-name toolchain --long
   ```
   {: pre}
1. Using the [CD Toolchain API](/apidocs/toolchain).

### Copy toolchains
{: #cd-migrate-region-copyToolchains}

To copy a toolchain, run the [@ibm-cloud/cd-tools](https://www.npmjs.com/package/@ibm-cloud/cd-tools){: external} `copy-toolchain` command. To see the available options run:

```shell-session
$ npx @ibm-cloud/cd-tools copy-toolchain -h
Usage: @ibm-cloud/cd-tools copy-toolchain [options]

Copies a toolchain, including tool integrations and Tekton pipelines, to another region or resource group.

Examples:
  export IBMCLOUD_API_KEY='...'
  npx @ibm-cloud/cd-tools copy-toolchain -c ${TOOLCHAIN_CRN} -r us-south
      Copy a toolchain to the Dallas region with the same name, in the same resource group.
  npx @ibm-cloud/cd-tools copy-toolchain -c ${TOOLCHAIN_CRN} -r eu-de -n new-toolchain-name -g new-resource-group --apikey ${APIKEY}
      Copy a toolchain to the Frankfurt region with the specified name and target resource group, using the given API key

Environment Variables:
  IBMCLOUD_API_KEY                       API key used to authenticate. Must have IAM permission to read and create toolchains and service-to-service authorizations in source and target
region / resource group

Basic options:
  -c, --toolchain-crn <crn>              The CRN of the source toolchain to copy
  -r, --region <region>                  The destination region of the copied toolchain (choices: "au-syd", "br-sao", "ca-mon", "ca-tor", "eu-de", "eu-es", "eu-gb", "jp-osa", "jp-tok",
                                         "us-east", "us-south")
  -a, --apikey <api_key>                 API key used to authenticate. Must have IAM permission to read and create toolchains and service-to-service authorizations in source and target
                                         region / resource group
  -n, --name <name>                      (Optional) The name of the copied toolchain (default: same name as original)
  -g, --resource-group <resource_group>  (Optional) The name or ID of destination resource group of the copied toolchain (default: same resource group as original)
  -t, --tag <tag>                        (Optional) The tag to add to the copied toolchain
  -h, --help                             Display help for command

Advanced options:
  -d, --terraform-dir <path>             (Optional) The target local directory to store the generated Terraform (.tf) files
  -D, --dry-run                          (Optional) Skip running terraform apply; only generate the Terraform (.tf) files
  -f, --force                            (Optional) Force the copy toolchain command to run without user confirmation
  -S, --skip-s2s                         (Optional) Skip creating toolchain-generated service-to-service authorizations
  -T, --skip-disable-triggers            (Optional) Skip disabling Tekton pipeline Git or timed triggers. Note: This may result in duplicate pipeline runs
  -C, --compact                          (Optional) Generate all resources in a single resources.tf file
  -v, --verbose                          (Optional) Increase log output
  -q, --quiet                            (Optional) Suppress non-essential output, only errors and critical warnings are displayed
```
{: pre}

#### Examples

Copy the toolchain with the CRN `crn:v1:bluemix:public:toolchain:au-syd:a/9d5d528aa786af01ce99593a827a05f0:69e8d78b-0d1a-49ed-9a46-3b4c1bb4f24a::` from the Sydney region to the Tokyo region, in the same resource group and with the same name:

```bash
export IBMCLOUD_API_KEY='<your_api_key>'
npx @ibm-cloud/cd-tools copy-toolchain -c 'crn:v1:bluemix:public:toolchain:au-syd:a/9d5d528aa786af01ce99593a827a05f0:69e8d78b-0d1a-49ed-9a46-3b4c1bb4f24a::' -r jp-tok
```
{: pre}

Copy a toolchain to the Frankfurt region, but provide the API key via a parameter instead of an environment property:

```bash
npx @ibm-cloud/cd-tools copy-toolchain -c "${CRN}" -r eu-de --apikey '<your_api_key>'
```
{: pre}

Copy a toolchain to the Dallas region, renaming it to `toolchain-dallas`:

```bash
export IBMCLOUD_API_KEY='<your_api_key>'
npx @ibm-cloud/cd-tools copy-toolchain -c "${CRN}" -r us-south -n 'toolchain-dallas'
```
{: pre}

#### Retrying after errors

If an error occurs while copying the toolchain, the copied toolchain may be incomplete. You may need to try the command again. To try again, you can either:
1. Delete the partially created toolchain and run the `copy-toolchain` command again.
1. Re-run the `terraform apply` command.<br/><br/>The `copy-toolchain` first serializes the source toolchain into Terraform (.tf) files. If you don't specify the `-d, --terraform-dir <path>`, the Terraform files will be placed in a folder in the current working directory named `output-{id}`, e.g. `output-1764100766410`. You can locate the most recent output folder and re-run `terraform apply`. This will continue where the previous command left off. When prompted for an API key, specify the same API key you used to run the `copy-toolchain` command.
```shell-session
$ cd output-1764102115772
$ terraform apply
var.ibmcloud_api_key
  Enter a value: {api_key}
...
```
