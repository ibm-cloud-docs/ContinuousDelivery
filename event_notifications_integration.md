---

copyright:
  years: 2023
lastupdated: "2023-04-12"

keywords: tool integrations, IBM Cloud Public, Event Notifications

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}   

# Configuring {{site.data.keyword.en_short}}
{: #event-notifications-integration}

You can use the {{site.data.keyword.en_full_notm}} service to receive information about critical events that occur in your {{site.data.keyword.cloud}} account. You can filter and route event notifications from {{site.data.keyword.cloud_notm}} services like Monitoring, Security and Compliance Center, and Secrets Manager to communication channels like email, SMS, push notifications, webhook, slack, Microsoft&reg; Teams, ServiceNow, and {{site.data.keyword.IBM_notm}} {{site.data.keyword.openwhisk_short}}.
{: shortdesc}

Currently, you can use this tool integration only with toolchains that are created from the DevSecOps continuous integration and continuous delivery templates. Before you configure a {{site.data.keyword.compliance_short}} tool integration, make sure that you have a Git repository (repo) that contains the evidence locker for your toolchain and a configured Git tool integration that points to this repo.
{: important}

This tool integration verifies the security and compliance posture of your toolchain by identifying the location of the evidence locker and the path to the evidence summary. For more information about evidence format and structure, see [Evidence](/docs/devsecops?topic=devsecops-devsecops-evidence). You can also configure a pipeline task to trigger security and compliance scans by using this tool.

{{site.data.keyword.compliance_short}} supports two scan types: the older hybrid cloud scan and the new cloud scan. Both of these scan types can find toolchains and associated evidence, as it is configured in the **Name**, **Evidence repository name or URL**, and **Evidence namespace** fields within the {{site.data.keyword.compliance_short}} tool integration.

The **trigger validation scan after deploy** field, and the other three trigger scan option fields work only with hybrid cloud scans.
{: tip}

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
1. On your Toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.en_short}}**.
 
## Configuring {{site.data.keyword.en_short}} by using the API
{: #event-notifications-config-parameters}

The {{site.data.keyword.en_short}} tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `security_compliance` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| api-key | optional, updatable | Password | api-key | The {{site.data.keyword.cloud_notm}} API key that is used to access the {{site.data.keyword.compliance_short}} API. This parameter is relevant only when the `trigger_scan` parameter is `enabled`. You can use a toolchain secrets reference for this parameter. For more information about secrets references, see [Protecting your sensitive data in {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security#cd_secure_credentials). |
| evidence_namespace | required, updatable | String | evidence_namespace | The type of pipeline evidence to display in {{site.data.keyword.compliance_short}} for this toolchain. Valid values are `cd` (uses evidence that is generated by a continuous deployment pipeline) or `cc` (uses evidence that is generated by a continuous compliance pipeline). |
| evidence_repo_name | required, updatable | String | evidence_repo_url | The URL of a Git repo evidence locker. The DevSecOps toolchain templates collect and store evidence for scans and tasks in an evidence repo. Make sure that this URL matches the `repo_url` for a Git tool integration in this toolchain. The DevSecOps toolchain goals in the {{site.data.keyword.compliance_short}} check the evidence repo for the pass or fail results for those goals. |
| name | required, updatable | String | name | The name of this tool integration. |
| profile | optional, updatable | String | profile | The name of a {{site.data.keyword.compliance_short}} profile. You can use the predefined {{site.data.keyword.cloud_notm}} Security Best Practices v1.0.0 profile that contains the DevSecOps toolchain goals. Or, you can use a user-authored customized profile that is configured to contain those goals. When the `trigger_scan` parameter is set to `enabled`, the Validation scan uses the controls and goals in the configured profile. If the configuration contains a profile that does not check the DevSecOps toolchain goals, it might incorrectly indicate the toolchain status as `passed` even though some of the DevSecOps scans failed. This parameter is relevant only when the `trigger_scan` parameter is `enabled`. |
| scope | optional, updatable | String | scope | The name of a {{site.data.keyword.compliance_short}} scope that was previously created in that service. When the `trigger_scan` parameter is set to `enabled`, the Validation scan scans all of the resources in that scope. Select a scope that contains this toolchain so that the scan finds the evidence that was recently updated by the DevSecOps `pipeline-run`. This parameter is relevant only when the `trigger_scan` parameter is `enabled`. |
| trigger_scan | optional, updatable | String | trigger_scan | Set to `enabled` to indicate that a DevSecOps pipeline task must trigger a {{site.data.keyword.compliance_short}} run of a hybrid cloud validation scan. Each scan might incur charges. When enabled, the `api_key`, `scope`, and `profile` parameters are required to trigger that scan. |
{: caption="Table 1. {{site.data.keyword.en_short}} tool integration parameters" caption-side="bottom"}

## Learn more about {{site.data.keyword.en_short}}
{: #learn_event_notifications}

To learn more about {{site.data.keyword.en_short}}, see [Getting started with {{site.data.keyword.en_short}}](/docs/event-notifications?topic=event-notifications-getting-started).
