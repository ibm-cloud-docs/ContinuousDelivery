---

copyright:
  years: 2021, 2022
lastupdated: "2022-11-10"

keywords: tool integrations, IBM Cloud Public, Security and Compliance Center

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}   

# Configuring {{site.data.keyword.compliance_short}}
{: #scc}

You can use the {{site.data.keyword.compliance_full}} to embed security checks into your everyday workflows to monitor for security and compliance. By monitoring for risks, you can identify security vulnerabilities and quickly work to mitigate the impact and fix the issues.
{: shortdesc}

Currently, you can use this tool integration only with toolchains that are created from the DevSecOps continuous integration and continuous delivery templates. Before you configure a {{site.data.keyword.compliance_short}} tool integration, make sure that you have a Git repository (repo) that contains the evidence locker for your toolchain and a configured Git tool integration that points to this repo.
{: important}

This tool integration verifies the security and compliance posture of your toolchain by identifying the location of the evidence locker and the path to the evidence summary. For more information about evidence format and structure, see [Evidence](/docs/devsecops?topic=devsecops-devsecops-evidence). You can also configure a pipeline task to trigger security and compliance scans by using this tool.

Configure {{site.data.keyword.compliance_short}} to embed security checks into your workflows to monitor for security and compliance:

1. If you are configuring this tool integration as you are creating the toolchain, and a {{site.data.keyword.compliance_short}} tool integration exists within the template that you are configuring, click the **{{site.data.keyword.compliance_short}}** tab. Alternatively, in the **More tools** section, click **{{site.data.keyword.compliance_short}}**.
1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.  

   a. Click **Add tool**.

   b. In the Tool Integrations section, click **{{site.data.keyword.compliance_short}}**.

1. Type the name that you want to display for this tool integration on the {{site.data.keyword.compliance_short}} card in your toolchain. This name is used to identify the tool integration in your toolchain.

1. Specify the **Evidence repository name or URL**. This is the name or URL of the repo that stores the evidence locker for your toolchain. This repo must correspond to the Git tool integration you previously added to your toolchain to store your evidence. Currently, only GitHub, GitLab, and IBM-hosted Git are supported. {{site.data.keyword.compliance_short}} scans run with the user credentials that are configured in the {{site.data.keyword.compliance_short}} scope. That user must have Git OAuth credentials for this toolchain's region and read access to the evidence repo.

1. Enable **Trigger validation scan after deploy** to configure a pipeline task to trigger scans.

   a. Select an existing **IBM Cloud API key** from a secrets store or click **New** to create one. This API key is used to access the {{site.data.keyword.compliance_short}} API.
 
   b. Select a **Scope name**. A scope narrows the focus of the scan. For more information about scopes, see [Managing scopes](/docs/security-compliance?topic=security-compliance-scopes).

   c. Select a **Profile name**. A profile is a collection of security controls. For more information about profiles, see [Working with profiles](/docs/security-compliance?topic=security-compliance-profiles).

    Select the {{site.data.keyword.cloud_notm}} Security Best Practices v1.0.0 profile for DevSecOps toolchains.
    {: tip}

1. Click **Create Integration**.
1. On your Toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.compliance_short}}**.
 
## Configuring {{site.data.keyword.compliance_short}} by using the API
{: #config-parameters}

The {{site.data.keyword.compliance_short}} tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `security_compliance` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| name | required, updatable | String | name | The name of this tool integration, for example `my-security-compliance`, that is displayed in your toolchain. |
| evidence_repo_name | required, updatable | String | evidence_repo_name | To collect and store evidence for all of the performed tasks, you must specify a Git repo as an evidence locker. |
| trigger_scan | optional, updatable | String | trigger_scan | Enable trigger validation scans to provide details for a pipeline task to trigger a scan. |
| evidence_namespace | optional, updatable | String | evidence_namespace | The type of pipeline evidence to display in {{site.data.keyword.compliance_short}} for this toolchain. The evidence locker is searched for continuous deployment pipeline evidence or continuous compliance pipeline evidence. |
| api-key | optional, updatable | Password | api-key | The {{site.data.keyword.cloud_notm}} API key that is used to access the {{site.data.keyword.compliance_short}} API. You can obtain your API key by using the `ibmcloud iam api-key-create` command or by clicking **Create API key** from the [console](https://cloud.ibm.com/iam#/apikeys). You can view each API key only one time.  |
| scope | optional, updatable | String | scope | Select an existing scope name to narrow the focus of the validation scan. For more information about scopes, see [Managing scopes](/docs/security-compliance?topic=security-compliance-scopes).
| profile | optional, updatable | String | profile | Select an existing profile, where a profile is a collection of security controls. For more information about profiles, see [Understanding profiles](/docs/security-compliance?topic=security-compliance-custom-profiles&interface=ui#understand-profiles). |
{: caption="Table 1. {{site.data.keyword.compliance_short}} tool integration parameters" caption-side="bottom"}

## Learn more about {{site.data.keyword.compliance_short}}
{: #learn_scc}

To learn more about {{site.data.keyword.compliance_short}}, see [Getting started with Security and Compliance Center](/docs/security-compliance?topic=security-compliance-getting-started). 
