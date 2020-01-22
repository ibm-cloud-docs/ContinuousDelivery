---

copyright:
  years: 2019, 2020
lastupdated: "2020-01-22"

keywords: customer responsibilities, IBM responsibilities, terms and conditions

subcollection: ContinuousDelivery

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}
{:preview: .preview}

# Your responsibilities with using {{site.data.keyword.contdelivery_short}}
{: #responsibilities-cd}

Learn about the management responsibilities and terms and conditions that you have when you use {{site.data.keyword.contdelivery_full}}. For a high-level view of the service types in {{site.data.keyword.cloud}} and the breakdown of responsibilities between the customer and {{site.data.keyword.IBM_notm}} for each type, see [Shared responsibilities for {{site.data.keyword.cloud_notm}} offerings](/docs/overview?topic=overview-shared-responsibilities).
{:shortdesc}

You can integrate third-party tools (such as Public GitHub), or tools that you manage (such as a private Tekton worker that is running on your infrastructure), into {{site.data.keyword.contdelivery_short}} toolchains. However, IBM’s management responsibilities do not extend to any tools that are managed by you or by third-parties.
{:important}

Review the following sections for the specific responsibilities for you and for {{site.data.keyword.IBM_notm}} when you use {{site.data.keyword.contdelivery_short}}. For the overall terms of use, see [{{site.data.keyword.cloud_notm}} Terms and Notices](/docs/overview/terms-of-use?topic=overview-terms).

  
## Incident and operations management
{: #incident-and-ops}

<!-- Include an introductory sentence or two about this table. Leave the cell blank for the responsible party column if they do not have responsibility for the given task.  -->

| Task | IBM responsibilities | Your responsibilities |
|----------|-----------------------|--------|
|Maintain high availability and respond to incidents.| Operate the {{site.data.keyword.contdelivery_short}} service in accordance with the {{site.data.keyword.cloud_notm}} Public [Service Level Agreements (SLAs)](/docs/overview/terms-of-use?topic=overview-slas).  | Plan the deployment of your apps and data to meet your availability objectives. For more information about managing availability, see [How do I ensure zero downtime?](/docs/overview/terms-of-use?topic=overview-zero-downtime) |
{: caption="Table 1. Responsibilites for incident and operations" caption-side="top"}


## Change management
{: #change-management}

<!-- Include an introductory sentence or two about this table. Leave the cell blank for the responsible party column if they do not have responsibility for the given task.  -->

| Task | IBM responsibilities | Your responsibilities |
|----------|-----------------------|--------|
|Update {{site.data.keyword.deliverypipeline}} images.| Provide updated {{site.data.keyword.deliverypipeline}} job container images. These images might include updates to command tools (such as `ibmcloud`) that might affect the function of existing pipeline job scripts.  | Update {{site.data.keyword.deliverypipeline}} job scripts to respond to changes in underlying container images, or configure pipeline job scripts to use specific versions of container images instead of the latest version. |
|Deploy apps and other workloads by using the {{site.data.keyword.deliverypipeline}}.| Maintain the {{site.data.keyword.deliverypipeline}} service.  | Maintain the job scripts that are run by the {{site.data.keyword.deliverypipeline}} service, the inputs to pipeline job stages (such as source code), and the apps and other workloads that are deployed by job scripts. |
|Support {{site.data.keyword.deliverypipeline}} private workers to allow pipeline workloads to run on customer infrastructure.| Provide and maintain the private worker agent that integrates customer-managed infrastructure into the {{site.data.keyword.deliverypipeline}} service.  | Install the private worker agent into your Kubernetes cluster with enough capacity to run your pipeline workloads. Update the agent as new versions become available. |
{: caption="Table 1. Responsibilities for change management" caption-side="top"}


## Identity and access management
{: #iam-responsibilities}

<!-- Include an introductory sentence or two about this table. Leave the cell blank for the responsible party column if they do not have responsibility for the given task.  -->

| Task | IBM responsibilities | Your responsibilities |
|----------|-----------------------|--------|
|Manage access to toolchains in resource groups and their associated IBM-hosted tools, except for {{site.data.keyword.gitrepos}}.| N/A  | Grant, revoke, and manage access to toolchains by using {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM). For more information about access management, see [Managing user access to toolchains in resource groups](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security). |
|Manage access to toolchains in Cloud Foundry orgs.| N/A  | Add, remove, and manage access to toolchains by updating the members and roles of users in both Cloud Foundry orgs and Cloud Foundry-based toolchains. For more information about access management, see [Managing access to toolchains in Cloud Foundry orgs](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-cf-security). |
|Manage the {{site.data.keyword.contdelivery_short}} service's access to third-party tools that are integrated into toolchains. | N/A  | Add, update, or delete third-party tool integration configurations (including access credentials for tool integrations) in toolchains. For more information about working with tool integrations, see [Configuring tool integrations](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations). |
|Manage access to repos in {{site.data.keyword.gitrepos}}. | N/A  | From the **Settings** > **Members** page in the {{site.data.keyword.gitrepos}} dashboard, manage project members and role permissions. |
|Manage all other access to third-party tools that are integrated with {{site.data.keyword.contdelivery_short}}. | N/A  | Manage access by using the capabilities that are provided by the third-party tools.  |
{: caption="Table 2. Responsibilities for identity and access management" caption-side="top"}

## Security and regulation compliance
{: #security-compliance}

<!-- Include an introductory sentence or two about this table. Leave the cell blank for the responsible party column if they do not have responsibility for the given task.  -->

| Task | IBM responsibilities | Your responsibilities |
|----------|-----------------------|--------|
|Meet security and compliance objectives.| Provide a secure {{site.data.keyword.contdelivery_short}} service that complies with key standards. For more information about data security, see [How do I know that my data is safe?](/docs/overview/terms-of-use?topic=overview-security)  | Secure your workloads and data. To learn more about securing your cloud apps, see [Security to safeguard and monitor your cloud apps](https://www.ibm.com/cloud/garage/architectures/securityArchitecture){:external}. To learn more about securing your data while you are using the {{site.data.keyword.contdelivery_short}} service, see [Securing your data](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security). |
{: caption="Table 4. Responsibilites for security and regulation compliance" caption-side="top"}

## Disaster recovery
{: #disaster-recovery}

IBM is responsible for maintaining backups and high availability of the {{site.data.keyword.contdelivery_short}} service in each supported region. However, because {{site.data.keyword.contdelivery_short}} toolchains are region-dependent, automated global failover is not supported. If a regional disaster occurs, the recovery time for toolchains depends on the recovery time for the region. You can implement manual failover to another region by creating and maintaining copies of your toolchains and Git repos that have idle pipelines, in another {{site.data.keyword.cloud_notm}} region.
{:important}

| Task | IBM responsibilities | Your responsibilities |
|----------|-----------------------|--------|
|Back up toolchain data.| Maintain regular backups of toolchain and pipeline definitions, Git repos, and any other toolchain integration data that is stored and managed by IBM.  | To support global failover, create and maintain copies of your toolchain and pipeline definitions, including tool integration data and your Git repos, in another IBM region. |
|Restore toolchain data.| Restore all toolchain and Git repos to the original {{site.data.keyword.cloud_notm}} region, when that region is available.    | To support global failover, manually switch to using the copied toolchains and repos in another region. |
{: caption="Table 5. Responsibilites for disaster recovery" caption-side="top"} 
