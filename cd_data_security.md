---

copyright:
  years: 2018, 2022
lastupdated: "2022-06-01"

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
* Client and system credentials are stored on encrypted disks. 
* Configuration data for tool integrations and {{site.data.keyword.deliverypipeline}} property values might include sensitive information. This data is encrypted by using encryption keys that are internal to the {{site.data.keyword.contdelivery_short}} service because it is stored in databases that are internal to the service. 
* The application and data are configured for high availability.
* Access to data is limited to only those users who require the data to support and maintain the service.

## Protecting your sensitive data in {{site.data.keyword.contdelivery_short}}
{: #cd_secure_credentials}

The {{site.data.keyword.contdelivery_short}} service encrypts customer-owned sensitive data before it stores it in databases that are used internally by the service. Sensitive data includes third-party tool integration configuration data and {{site.data.keyword.deliverypipeline}} property values. Data is encrypted by using encryption keys that are internal to the {{site.data.keyword.contdelivery_short}} service.

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

## Deleting your data from {{site.data.keyword.contdelivery_short}}
{: #cd_delete-data}

When you delete a {{site.data.keyword.contdelivery_short}} service instance, the related toolchains, tool integrations, tools, and data (including personal data) are not deleted. For more information about how to manage and delete data that is stored with toolchains, tool integrations, and tools, see [Modifying, exploring, and deleting personal data](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_personal_data#managing_personal_data).
