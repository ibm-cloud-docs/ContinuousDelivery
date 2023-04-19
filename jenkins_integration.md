---

copyright:
  years: 2015, 2023
lastupdated: "2023-04-19"

keywords: tool integrations, IBM Cloud Public, Jenkins

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}} 

# Configuring Jenkins
{: #jenkins}

Jenkins is an open source, server-based tool that builds and tests software continuously, supporting the practices of continuous integration and continuous delivery.
{: shortdesc}

Before you create a Jenkins tool integration, you must have a Jenkins server.
{: important}

With the Jenkins tool integration, you can send your Jenkins job notifications to other tools in your toolchain, such as Slack, and PagerDuty. To trace code in deployments, you can add deployment messages to your Git commits and your related Git or JIRA issues. You can also view your deployments on the Toolchain Connections page. You can feed test results to {{site.data.keyword.DRA_short}}, add automated quality gates, and track your deployment risk.

Configure Jenkins to automate the continuous building, testing, and deployment of your apps:

1. If you are configuring this tool integration as you are creating the toolchain, in the Configurable Integrations section, click **Jenkins**.
1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**. 

   a. Click **Add tool**.

   b. In the Tool Integrations section, click **Jenkins**.

1. Type the name that you want to display for this tool integration on the Jenkins card in your toolchain.
1. Type the URL for the Jenkins server that you want to open when you click the Jenkins card from your toolchain.
1. Copy the generated toolchain webhook.
1. In your Jenkins server, complete these steps:

   a. [Install the IBM Cloud DevOps plug-in](https://wiki.jenkins-ci.org/display/JENKINS/IBM+Cloud+DevOps+Plugin#IBMCloudDevOpsPlugin-Installingtheplugin){: external}.

   b. [Configure Jenkins to notify toolchains](https://wiki.jenkins-ci.org/display/JENKINS/IBM+Cloud+DevOps+Plugin#IBMCloudDevOpsPlugin-Notifyingtoolchains){: external}.

   c. Return to the Configure the Integration page for the Jenkins tool integration.

1. Click **Create Integration**.
1. On the Toolchain's Overview page, on the **Third-Party tools** card, click **Jenkins** to view the Jenkins server.

## Configuring Jenkins by using the API
{: #jenkins-config-parameters}

The Jenkins tool integration supports the following configuration parameters that you can use with the [Toolchain HTTP API and SDKs](https://cloud.ibm.com/apidocs/toolchain){: external} when you [create](https://cloud.ibm.com/apidocs/toolchain#create-tool){: external}, [read](https://cloud.ibm.com/apidocs/toolchain#get-tool-by-id){: external}, and [update](https://cloud.ibm.com/apidocs/toolchain#update-tool){: external} tool integrations.

You must specify the `tool_type_id` property in the request body with the `jenkins` value.
{: important}

| Parameter | Usage | Type | Terraform argument | Description |
| --- | --- | --- | --- | --- |
| api_token | optional, updatable | Password | api_token | The API token to use for Jenkins REST API calls so that {{site.data.keyword.DRA_short}} can collect data from Jenkins. You can find the API token on the Configuration page of your Jenkins instance. You can use a toolchain secret reference for this parameter. For more information about secret references, see [Protecting your sensitive data in Continuous Delivery](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_data_security#cd_secure_credentials). |
| api_user_name | optional, updatable | String | api_user_name | The username to use with the Jenkins server's API token, which is required so that {{site.data.keyword.DRA_short}} can collect data from Jenkins. You can find your API username on the Configuration page of your Jenkins instance. |
| dashboard_url | required, updatable | String | dashboard_url | The URL of the Jenkins server dashboard for this tool integration. In the graphical UI, the browser goes to this dashboard when you click the Jenkins tool integration card. |
| name | required, updatable | String | name | The name of this tool integration. |
| webhook_url | optional, updatable | String | webhook_url | The webhook to use in your Jenkins jobs to send notifications to other tools in your toolchain. |
{: caption="Table 1. Jenkins tool integration parameters" caption-side="bottom"}

## Learn more about Jenkins
{: #learn_jenkins}

To learn more about Jenkins, see the [Jenkins article](https://www.ibm.com/garage/method/practices/code/tool_jenkins/){: external} on the IBM Cloud Garage Method or take this tutorial:

* [Ensure quality deployments by using the "Deployment Risk Analytics with GitHub and Jenkins" toolchain](https://www.ibm.com/cloud/architecture/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain){: external}
