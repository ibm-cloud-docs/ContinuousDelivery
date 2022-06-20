---

copyright:
  years: 2018, 2022
lastupdated: "2022-06-20"

keywords: secure environment, data, Data, high availability, access

subcollection: ContinuousDelivery

---

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

# Securing your data in {{site.data.keyword.contdelivery_short}}
{: #cd_data_security}  

{{site.data.keyword.contdelivery_full}} hosts your databases in a highly available and secure environment:

* Data is encrypted at rest (GPFS, LUKS, and built-in disk) and in transit (HTTPS and SSH) by using encryption keys that are internal to the {{site.data.keyword.contdelivery_short}} service, or the services and infrastructure that it depends on.
* [Personal data can be encrypted only in the Professional plan](#cd_professional_plan) by using a root key within an instance of the {{site.data.keyword.keymanagementservicefull}} service.
* Client and system credentials are stored on encrypted disks. 
* Configuration data for tool integrations and {{site.data.keyword.deliverypipeline}} property values might include sensitive information. This data is encrypted by using encryption keys that are internal to the {{site.data.keyword.contdelivery_short}} service because it is stored in databases that are internal to the service. 
* The application and data are configured for high availability.
* Access to data is limited to only those users who require the data to support and maintain the service.

## Protecting your sensitive data in {{site.data.keyword.contdelivery_short}}
{: #cd_secure_credentials}

The {{site.data.keyword.contdelivery_short}} service encrypts customer-owned sensitive data before it stores it in databases that are used internally by the service. Sensitive data includes third-party tool integration configuration data and {{site.data.keyword.deliverypipeline}} property values. Data is encrypted by using encryption keys that are internal to the {{site.data.keyword.contdelivery_short}} service or by using encryption keys from the root key that is specified within an instance of the {{site.data.keyword.keymanagementservicefull}} service.

DevOps processes often require various types of credentials (such as usernames and passwords, API keys, service keys, and SSH keys) to interact with other systems to build, test, and deploy applications. You are responsible for ensuring that these credentials aren't inadvertently shared outside of their intended audience. Access to these credentials by malicious actors might disrupt your IT operations, cause unexpected costs, or use your resources to start attacks. IBM is not responsible for protecting and maintaining the security of your credentials.

To keep your credentials secure, make sure that you follow this guidance:

* Do not store credentials in Git repos. Depending on the repo settings, files within a repo might be visible to other members of your organization, other {{site.data.keyword.cloud_notm}} users, or the public internet.
* Do not include user credentials in {{site.data.keyword.deliverypipeline}} definitions because they might be visible to other users. Specifically, do not place user credentials within {{site.data.keyword.deliverypipeline}} Classic job definition scripts, {{site.data.keyword.deliverypipeline}} Tekton yaml files, or scripts that are started by delivery pipelines.
* Do not publish user credentials in log files that are created when a pipeline runs because these files might be shared.
   
{{site.data.keyword.cloud_notm}} provides several options that you can use for secure key storage and secrets.

* [Classic pipeline secure environment properties](/docs/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about)
* [Tekton pipeline secure environment properties](/docs/ContinuousDelivery?topic=ContinuousDelivery-tekton-pipelines)
* [{{site.data.keyword.keymanagementservicefull}}](/docs/key-protect?topic=key-protect-getting-started-tutorial)
* [HashiCorp Vault](https://www.vaultproject.io/){: external}
   
For more information about secure DevOps best practices, see [DevOps Security](https://www.ibm.com/cloud/learn/devops-a-complete-guide?mhsrc=ibmsearch_a&mhq=Secure%20DevOps#toc-security-j2-0639C){: external}.

## Protecting your personal data when you use the Professional plan 
{: #cd_professional_plan}

Personal data that is encrypted by using a customer key can be protected only in the {{site.data.keyword.contdelivery_short}} Professional plan. If you select your own KeyManagement Service, such as KeyProtect or {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}}, the following values are encrypted by using your own key instead of the encryption keys that are internal to the {{site.data.keyword.contdelivery_short}} service.

| Component | Value | 
|:-----------------|:-----------------|
|Toolchain		|Properties and parameters     |
|Pipeline		| * Property keys and values \n * Job logs \n * Job artifacts  |
|Integrations		| * Slack (Slack webhook) \n * Pagerduty (API access key, Integration key) \n * Sauce Labs  (Access key) \n * Artifactory (API key) \n * Hashicorp Vault (Token, Role ID, Secret ID, Password) \n *  Jenkins  (Jenkins API token) \n * JIRA (JIRA API token) \n * Nexus (Authentication token) \n * Rational Team Concert (Password) \n * Security and  Compliance Center ({{site.data.keyword.cloud_notm}} API key) \n * Sonarqube (SonarQube password or authentication token) |
|{{site.data.keyword.DRA_full}}		|Attachment in test records |
{: caption="Table 1. Values that are encrypted by using your own key" caption-side="top"}

The following components encrypt personal data by using only the provider-managed encryption key.


| Component | Value | 
|:-----------------|:-----------------|
|Eclipse Orion {{site.data.keyword.webide}}		|User workspaces    |
|{{site.data.keyword.gitrepos}}		| * Issues, pull requests, and source code \n * Personal information, such as name, email, profile picture, address, and other information from the profile page     |
{: caption="Table 2. Values that are encrypted by using the provider-managed key" caption-side="top"}


## Protecting your data when you use third-party tool integrations
{: #cd_secure_integrations}

When you configure a tool integration for a toolchain, you explicitly enable data sharing between the {{site.data.keyword.contdelivery_short}} service and the tool integration. The kind of data that is shared, and whether data is sent to the tool, received from the tool, or both, varies depending on the type of tool integration.

Before you configure a tool integration, make sure you understand what data is shared. If you work with regulated data or data that you consider sensitive, make sure that the third-party tool usage and any data that might be shared with it do not compromise the confidentiality, integrity, or availability of your resources, or otherwise violate regulatory controls.

To learn more about tool integrations, see [Configuring tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations).

## Protecting your data when you use {{site.data.keyword.gitrepos}}
{: #cd_secure_grit}

{{site.data.keyword.gitrepos}} is an IBM-hosted component of the {{site.data.keyword.contdelivery_short}} service. All of the data that you provide to {{site.data.keyword.gitrepos}}, including but not limited to source files, issues, pull requests, and project configuration properties, is managed securely within {{site.data.keyword.contdelivery_short}}. However, {{site.data.keyword.gitrepos}} supports various mechanisms for exporting, sending, or otherwise sharing data to users and third parties.

The ability of {{site.data.keyword.gitrepos}} to share information is typical of many social coding platforms. However, such sharing might conflict with regulatory controls that might apply to your business. After you create a project in {{site.data.keyword.gitrepos}}, but before you entrust any files, issues, records, or other data with the project, review the project settings and change any settings that you deem necessary to protect your data. Settings to review include visibility levels, email notifications, integrations, web hooks, access tokens, deploy tokens, and deploy keys.

### Project visibility levels
{: #cd_secure_grit_visibility}

{{site.data.keyword.gitrepos}} projects can have one of the following visibility levels: private, internal, or public.

* Private projects are visible only to project members. This setting is the default visibility level for new projects, and is the most secure visibility level for your data.
* Internal projects are visible to all users that are logged into {{site.data.keyword.cloud_notm}}.
* Public projects are visible to anyone.

To limit project access to only project members, complete the following steps:

1. From the project sidebar, click **Settings** > **General**.
2. On the General Settings page, click **Visibility** > **project features** > **permissions**.
3. Locate the Project visibility setting.
4. Select **Private**, if it is not already selected.
5. Click **Save changes**.

### Project email settings
{: #cd_secure_grit_email}

By default, {{site.data.keyword.gitrepos}} notifies project members by way of email about project activities. These emails typically include customer-owned data that was provided to {{site.data.keyword.gitrepos}} by users. For example, if a user posts a comment to an issue, {{site.data.keyword.gitrepos}} sends an email to all subscribers that includes information such as a copy of the comment, the user who posted it, and when the comment was posted. To turn off all email notifications for your project, complete the following steps:

1. From the project sidebar, click **Settings** > **General**.
2. On the General Settings page, click **Visibility** > **project features** > **permissions**.
3. Select the **Disable email notifications** checkbox.
4. Click **Save changes**.

### Project integrations and webhooks
{: #cd_secure_grit_integrations}

{{site.data.keyword.gitrepos}} projects might also be configured with integrations or webhooks to other systems, or equipped with access tokens, deploy tokens, and deploy keys. To review or change the integrations, webhooks, tokens, and keys that might be configured with your project, from the project sidebar, complete the following steps:

1. From the project sidebar, click **Settings**.
2. Click **Integrations** to work with your project's integrations with other applications.
3. Click **Webhooks** to work with your project's webhooks to other systems.
4. Click **Access Tokens** to work with access tokens that might grant access to your project.
5. Expand **Deploy Tokens** to work with the deploy tokens that might grant access to your project.
6. Expand **Deploy Keys** to work with deploy keys that might grant access to your project.

To learn more about working with {{site.data.keyword.gitrepos}}, see [{{site.data.keyword.gitrepos}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-git_working).

## Protecting your data when you use Delivery Pipelines
{: #cd_secure_pipeline}

{{site.data.keyword.contdelivery_short}} pipelines run the jobs and steps that you provide. The {{site.data.keyword.contdelivery_short}} service securely manages the log output and build artifacts that are produced by your pipeline runs. However, {{site.data.keyword.contdelivery_short}} does not limit or manage the function of your pipeline job or step scripts.

When you develop and configure your pipeline job and step scripts, make sure that your scripts do not run actions that might compromise the confidentiality, integrity, or availability of your resources, or otherwise violate regulatory controls.

To learn more about Delivery Pipelines, see and [Working with pipelines](/docs/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about) and [Working with Tekton pipelines](/docs/ContinuousDelivery?topic=ContinuousDelivery-tekton-pipelines).


## Deleting your data from {{site.data.keyword.contdelivery_short}}
{: #cd_delete-data}

When you delete a {{site.data.keyword.contdelivery_short}} service instance, the related toolchains, tool integrations, tools, and data (including personal data) are not deleted. For more information about how to manage and delete data that is stored with toolchains, tool integrations, and tools, see [Modifying, exploring, and deleting personal data](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_personal_data#managing_personal_data).
