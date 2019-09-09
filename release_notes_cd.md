---

copyright:
  years: 2019
lastupdated: "2019-09-05"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# Release notes
{: #release-notes-cd}

Use these release notes to learn about the latest updates to {{site.data.keyword.contdelivery_full}} that are grouped by date. 
{:shortdesc}

For DevOps announcements, see [{{site.data.keyword.cloud_notm}} Announcements](https://www.ibm.com/cloud/blog/announcements/devops){: external}. For DevOps blog posts, see [DevOps](https://www.ibm.com/cloud/blog/devops){: external}.
{: tip}

## September 2019
{: #september-update}

|Date |Description	|
|:----------|:------------------------------|
|05 September 2019 		|The Develop and test microservices with Kubernetes and Helm template does not support API keys that are not bound to a specific account.	When a {{site.data.keyword.deliverypipeline}} stage attempts to run the `ibmcloud login` command, it fails because no account is specified. To work around this limitation, complete the following steps: <p><ol><li>In the {{site.data.keyword.deliverypipeline}} within the Develop and test microservices with Kubernetes and Helm template, create a pipeline property that is called `ACCOUNTID` and add the account that you want to use with the pipeline.</li><li> In each pipeline stage, add `-c $ACCOUNTID` to each instance of the `ibmcloud login` command.</li></ol></p>		|
|03 September 2019		|{{site.data.keyword.deliverypipeline}} events are not translated. Events that are triggered by the {{site.data.keyword.deliverypipeline}} send Slack messages. Since Slack APIs do not support multi-language message payload, these Slack messages cannot be translated. |
{: caption="Table 1. {{site.data.keyword.contdelivery_short}} September updates" caption-side="top"}
