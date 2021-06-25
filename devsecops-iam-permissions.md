---

copyright:
  years: 2021
lastupdated: "2021-06-23"

keywords: DevSecOps, COS, secure toolchain, compliance

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:table: .aria-labeledby="caption"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# IAM permissions needed for various {{site.data.keyword.cloud_notm}} resources
{: #cd-devsecops-iam-permissions}

Certain IAM permissions are required for the various {{site.data.keyword.cloud_notm}} resources that are used with the DevSecOps CI/CD pipeline templates.
{: shortdesc}

| Role | Resource |
|--|--|
|  Administrator, Writer  |  {{site.data.keyword.cos_full_notm}} service in <your team's resource group name> resource group  |
|  Administrator, Writer  |  {{site.data.keyword.contdelivery_full}} service in <your team's resource group name> resource group  |
|  Administrator  |  Toolchain service in <your team's resource group name> resource group  |
|  KeyPurge, Writer, Editor, Manager, Administrator  |   {{site.data.keyword.keymanagementservicefull}}  service in <your team's resource group name> resource group  |
|  Viewer, Reader, Writer  |  {{site.data.keyword.containerlong}}  |
|  Viewer, ReaderPlus  |  {{site.data.keyword.keymanagementserviceshort}} service in <your team's resource group name> resource group  |

## Related information
{: #cd-devsecops-iam-related-content}

* [IAM roles and actions](/docs/account?topic=account-iam-service-roles-actions)
* [Access management in {{site.data.keyword.cloud_notm}}](/docs/account?topic=account-cloudaccess)
* [IAM access](/docs/account?topic=account-userroles)
