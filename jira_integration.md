---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-19"

keywords: tool integrations, IBM Cloud Public, IBM Cloud Dedicated, JIRA

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

# Configuring JIRA
{: #jira}

JIRA is a tool that tracks issues and bugs that are related to your software. The JIRA tool integration updates your project's issues whenever Jenkins or {{site.data.keyword.deliverypipeline}} runs a deployment.
{:shortdesc}

In order for the JIRA tool integration to track your issues, you must use JIRA Smart Commits in your commit messages. To learn more about JIRA Smart Commits, see [Using Smart Commits](https://confluence.atlassian.com/fisheye/using-smart-commits-298976812.html){:external}.

Configure JIRA to plan, track, and deliver quality code:

1. If you are configuring this tool integration as you are creating the toolchain, in the Configurable Integrations section, click **JIRA**.
1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**. 

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
1. From your toolchain, click **JIRA** to view the dashboard for the JIRA project that you connected to.

## Learn more about JIRA

To learn more about JIRA, see the [JIRA article](https://www.ibm.com/garage/method/practices/code/tool_jira){:external} on the IBM Cloud Garage Method.
