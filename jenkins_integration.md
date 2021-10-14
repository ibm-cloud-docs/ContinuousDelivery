---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-19"

keywords: tool integrations, IBM Cloud Public, IBM Cloud Dedicated, Jenkins

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}   

# Configuring Jenkins
{: #jenkins}

Jenkins is an open source, server-based tool that builds and tests software continuously, supporting the practices of continuous integration and continuous delivery.
{: shortdesc}

Before you create a Jenkins tool integration, you must have a Jenkins server.
{: important}

With the Jenkins tool integration, you can send your Jenkins job notifications to other tools in your toolchain, such as Slack and PagerDuty. To trace code in deployments, you can add deployment messages to your Git commits and your related Git or JIRA issues. You can also view your deployments on the Toolchain Connections page. You can feed test results to {{site.data.keyword.DRA_short}}, add automated quality gates, and track your deployment risk.

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
1. From your toolchain, click **Jenkins** to view the Jenkins server.  

## Learn more about Jenkins

To learn more about Jenkins, see the [Jenkins article](https://www.ibm.com/cloud/garage/content/deliver/tool_jenkins/){: external} on the IBM Cloud Garage Method or take this tutorial:

   * [Ensure quality deployments by using the "Deployment Risk Analytics with GitHub and Jenkins" toolchain](https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain){: external}
