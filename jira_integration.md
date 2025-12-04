---

copyright:
  years: 2015, 2025
lastupdated: "2025-12-04"

keywords: tool integrations, IBM Cloud Public, JIRA

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}} 

# Configuring JIRA
{: #jira}

JIRA is a tool that tracks issues and bugs that are related to your software. The JIRA tool integration updates your project's issues whenever Jenkins or {{site.data.keyword.deliverypipeline}} runs a deployment.
{: shortdesc}

In order for the JIRA tool integration to track your issues, you must use JIRA Smart Commits in your commit messages. To learn more about JIRA Smart Commits, see [Using Smart Commits](https://confluence.atlassian.com/fisheye/using-smart-commits-960155400.html){: external}.

Configure JIRA to plan, track, and deliver quality code:

1. If you are configuring this tool integration as you are creating the toolchain, in the Configurable Integrations section, click **JIRA**.
1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Toolchains**. On the Toolchains page, click the toolchain to open its Overview page.  

   a. Click **Add tool**.

   b. In the Tool Integrations section, click **JIRA**.

1. If you have a JIRA project and want to connect to it, for the JIRA type, click **Existing**:

   a. Type the JIRA project key for the JIRA project. You can find the project key in the JIRA project's URL.

   b. Type the base API URL for your JIRA instance. You can find the API URL from the header of your JIRA instance. Click the **Administration** icon and click **System**.

   c. If you are connecting to a private JIRA instance, or you want to receive traceability information from a public JIRA instance, enter your JIRA user name and password.

   d. To track the deployment of code changes for the project by creating labels and comments for referenced issues, select the **Track deployment of code changes** checkbox. Make sure that you use JIRA Smart Commit to reference the JIRA issues in your GitHub commits. If you don't select this option, the JIRA tool integration ignores any commits.

1. If you want to create a JIRA project, for the JIRA type, click **New**:

   a. Type a JIRA project key to use for the new project. This key is used as a unique identifier in the project URL.

   b. Type a name for the JIRA project.

   c. Type the base API URL for your JIRA instance. You can find the API URL from the header of your JIRA instance. Click the **Administration** icon and click **System**.

   d. Type the user name for the JIRA project lead that you want to use for this project. To specify someone as the JIRA project lead, that person must have the project lead permission in JIRA.

   e. Type the administrator's user name for this instance of JIRA.

   f. Type the administrator's password for this instance of JIRA.

   g. To track the deployment of code changes for the project by creating labels and comments for referenced issues, select the **Track deployment of code changes** checkbox. Make sure that you use JIRA Smart Commit to reference the JIRA issues in your GitHub commits. If you don't select this option, the JIRA tool integration ignores any commits.

1. Click **Create Integration**.
1. On the Toolchain's Overview page, on the **Third-Party tools** card, click **JIRA** to view the dashboard for the JIRA project that you connected to.

## Configuring JIRA by using the API
{: #config-parameters}

The JIRA tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `jira` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| api_url | required, updatable | String | api_url | The base API URL for your JIRA instance. |
| enable_traceability | optional, updatable, `Default: false` | Boolean | enable_traceability | Track the deployment of code changes by creating tags, labels and comments on commits, pull requests and referenced issues. |
| password | optional, updatable | Password | api_token | The api token for your JIRA account. Optional for public projects. You can use a toolchain secret reference for this parameter. For more information, see [Protecting your sensitive data in Continuous Delivery](https://cloud.ibm.com/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security#cd_secure_credentials). |
| project_key | required, updatable | String | project_key | The project key of your JIRA project. |
| username | optional, updatable | String | username | The user name for your JIRA account. Optional for public projects. |
{: caption="JIRA tool integration parameters" caption-side="bottom"}
