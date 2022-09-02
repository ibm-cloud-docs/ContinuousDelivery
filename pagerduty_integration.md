---

copyright:
  years: 2015, 2022
lastupdated: "2022-08-26"

keywords: tool integrations, IBM Cloud Public, PagerDuty

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

# Configuring PagerDuty
{: #pagerduty}

PagerDuty integrates data from multiple monitoring systems into a single view. When a problem occurs, PagerDuty ensures that the team member who is best able to fix it at the time is notified. If the team member does not respond to the problem, escalations can be configured to route it to secondary representatives or operations managers.
{: shortdesc}

Configure PagerDuty to send notifications when pipeline stage failures occur so that you can fix problems faster and reduce downtime:

1. If you are configuring this tool integration as you are creating the toolchain, in the Configurable Integrations section, click **PagerDuty**.
1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**. 

   a. Click **Add tool**.

   b. In the Tool Integrations section, click **PagerDuty**.

1. If you want to integrate PagerDuty at the account level by using an API key, click **Account**:

   a. Type the API access key for your PagerDuty account. If you don't have a PagerDuty account, [register for one](https://www.pagerduty.com/sign-up/){: external}. For instructions to find the key, see [Generating an API Key](https://support.pagerduty.com/hc/en-us/articles/202829310-Generating-an-API-Key){: external}.

   b. Type the name of your PagerDuty service.

   c. Type the email address for the primary PagerDuty contact.

   d. Type the phone number for the primary PagerDuty contact.

1. If you want to integrate PagerDuty at the service level by using an integration key, click **Service**:

   a. Type the URL for the PagerDuty service that you want to post alerts to.

   b. Type your PagerDuty integration key. You can find your key or create a key in the Integrations section of your PagerDuty service page.

1. Click **Create Integration**.
1. On your Toolchain's Overview page, on the **Third-Party tools** card, click **PagerDuty** to go to pagerduty.com. You can view the events that are associated with the PagerDuty service that you specified when you configured this tool integration for your toolchain.

## Learn more about PagerDuty
{: #learn_pagerduty}

To learn more about PagerDuty, see the [PagerDuty article](https://www.ibm.com/cloud/garage/content/manage/tool_pagerduty/){: external} on the {{site.data.keyword.cloud_notm}} Garage Method or take the [Become a Garage Method advocate](https://www.ibm.com/cloud/garage/content/course/gm_advocate/){: external} course.
