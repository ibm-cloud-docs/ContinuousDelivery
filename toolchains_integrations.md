---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-19"

keywords: tool integrations, IBM Cloud Public, IBM Cloud Dedicated, Artifactory, Availability Monitoring, Bitbucket, Cloud Event Management, Delivery Pipeline, DevOps Insights, Delivery Pipeline Private Worker, Eclipse Orion Web IDE, Git Repos and Issue Tracking, GitHub, Dedicated GitHub Enterprise and Issues, GitLab, Hashicorp Vault, Jenkins, JIRA, Key Protect, Nexus, Custom Tool, PagerDuty, Rational Team Concert, Sauce Labs, Slack, SonarQube

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

# Configuring tool integrations
{: #integrations}

You can configure tool integrations that support development, deployment, and operations tasks while you create an open toolchain, or you can add and configure tool integrations to customize an existing toolchain.  
{:shortdesc}

The tool integrations that are available to add and configure for your toolchain are different depending on whether you are using toolchains on {{site.data.keyword.cloud}} Public or {{site.data.keyword.cloud_notm}} Dedicated. If you are using toolchains on {{site.data.keyword.cloud_notm}} Public, the tool integrations that are available to you depend on the region of your toolchain and the availability of tool integrations in that region. If you are using toolchains on {{site.data.keyword.cloud_notm}} Dedicated, the tool integrations that are available to you depend on how {{site.data.keyword.contdelivery_full}} was set up on your specific environment.

|Tool Integration |Available on {{site.data.keyword.cloud_notm}} Public	|Available on {{site.data.keyword.cloud_notm}} Dedicated (Environment Dependent)|
|:----------|:------------------------------|:------------------|
|[Artifactory](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-artifactory)		|Dallas, Washington, Frankfurt, Tokyo, London		|Yes		|
|[Availability Monitoring](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-availabilitymonitoring)		|Dallas		|No		|
|[Bitbucket](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-bitbucket)		|Dallas, Washington, Frankfurt, Tokyo, London		|No		|
|[Cloud Event Management](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cloudeventmanagement)		|Dallas		|No		|
|[{{site.data.keyword.deliverypipeline}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline) 		|Dallas, Washington, Frankfurt, Tokyo, London	   	|Yes  		|
|[{{site.data.keyword.deliverypipeline}} Private Worker](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-privateworker)			|Dallas, Washington, Frankfurt, Tokyo, London		|No		|
|[{{site.data.keyword.DRA_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-dra)		|Dallas, Frankfurt, London		|No			|
|[Eclipse Orion {{site.data.keyword.webide}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-webide)		|Dallas, Washington, Frankfurt, Tokyo, London		|Yes			|
|[{{site.data.keyword.gitrepos}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-grit)	|Dallas, Washington, Frankfurt, Tokyo, London		|No		|
|[GitHub](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-github)		|Dallas, Washington, Frankfurt, Tokyo, London		|Yes		|
|[Dedicated {{site.data.keyword.ghe_short}} and Issues](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-configghe)			|No		|Yes		|
|[GitLab](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-gitlab)		|Dallas, Washington, Frankfurt, Tokyo, London		|No		|
|[HashiCorp Vault](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-hashicorpvault)		|Dallas, Washington, Frankfurt, Tokyo, London		|Yes		|
|[Jenkins](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-jenkins)	|Dallas, Washington, Frankfurt, Tokyo, London		|Yes		|
|[JIRA](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-jira)		|Dallas, Washington, Frankfurt, Tokyo, London		|Yes		|
|[{{site.data.keyword.keymanagementserviceshort}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-keyprotect)		|Dallas, Washington, Frankfurt, Tokyo, London		|Yes		|
|[Nexus](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-nexus)			|Dallas, Washington, Frankfurt, Tokyo, London		|Yes		|
|[Other Tool](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-othertool)			|Dallas, Washington, Frankfurt, Tokyo, London		|Yes		|
|[PagerDuty](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-pagerduty)			|Dallas, Washington, Frankfurt, Tokyo, London		|Yes		|
|[Rational Team Concert](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-rationalteamconcert)		|Dallas, Washington, Frankfurt, Tokyo, London		|Yes		|
|[Sauce Labs](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-saucelabs)		|Dallas, Washington, Frankfurt, Tokyo, London		|No		|
|[Slack](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-slack)		|Dallas, Washington, Frankfurt, Tokyo, London		|Yes		|
|[SonarQube](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-sonarqube)			|Dallas, Washington, Frankfurt, Tokyo, London		|Yes		|
{: caption="Table 1. Tool integrations available for toolchains on {{site.data.keyword.cloud_notm}} Public and Dedicated" caption-side="top"}

If you want to start developing with your source code on {{site.data.keyword.cloud_notm}} Public, configure the GitHub tool integration or the {{site.data.keyword.gitrepos}} tool integration before you configure the {{site.data.keyword.deliverypipeline}}. If you want to start developing with your code on {{site.data.keyword.cloud_notm}} Dedicated, configure the {{site.data.keyword.ghe_short}} tool integration or the GitHub tool integration before you configure the {{site.data.keyword.deliverypipeline}}.
{: tip}
