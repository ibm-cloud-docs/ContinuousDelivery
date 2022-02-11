---

copyright:
  years: 2015, 2022
lastupdated: "2022-02-11"

keywords: tool integrations, IBM Cloud Public, App Configuration, Artifactory, Bitbucket, Delivery Pipeline, DevOps Insights, Delivery Pipeline Private Worker, Eclipse Orion Web IDE, Git Repos and Issue Tracking, GitHub, GitLab, Hashicorp Vault, Jenkins, JIRA, IBM Key Protect, IBM Secrets Manager, Nexus, Custom Tool, PagerDuty, Rational Team Concert, Sauce Labs, Security and Compliance Center, Slack, SonarQube

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
{: shortdesc}

The tool integrations that are available to you depend on the region of your toolchain and the availability of tool integrations in that region.

|Tool Integration |Available on {{site.data.keyword.cloud_notm}} Public	|
|:----------|:------------------------------|
|[{{site.data.keyword.appconfig_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-app-configuration)		|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|Yes		|
|[Artifactory](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-artifactory)		|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|Yes		|
|[Bitbucket](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-bitbucket)		|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|No		|
|[{{site.data.keyword.deliverypipeline}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline) 		|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London	   	|Yes  		|
|[{{site.data.keyword.deliverypipeline}} Private Worker](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-privateworker)			|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Osaka, Sydney, London		|No		|
|[{{site.data.keyword.DRA_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-dra)		|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|No			|
|[Eclipse Orion {{site.data.keyword.webide}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-webide)		|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|Yes			|
|[{{site.data.keyword.gitrepos}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-grit)	|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|No		|
|[GitHub](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-github)		|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|Yes		|
|[GitLab](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-gitlab)		|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|No		|
|[HashiCorp Vault](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-hashicorpvault)		|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|Yes		|
|[Jenkins](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-jenkins)	|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|Yes		|
|[JIRA](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-jira)		|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|Yes		|
|[{{site.data.keyword.keymanagementserviceshort}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-keyprotect)		|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|Yes		|
|[Nexus](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-nexus)			|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|Yes		|
|[Other Tool](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-othertool)			|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|Yes		|
|[PagerDuty](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-pagerduty)			|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|Yes		|
|[Rational Team Concert](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-rationalteamconcert)		|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|Yes		|
|[Sauce Labs](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-saucelabs)		|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|No		|
|[Secrets Manager](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-secretsmanager)		|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|Yes		|
|[Security and Compliance Center](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-scc)		|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|Yes		|
|[Slack](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-slack)		|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|Yes		|
|[SonarQube](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-sonarqube)			|Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|Yes		|
{: caption="Table 1. Tool integrations available for toolchains on {{site.data.keyword.cloud_notm}} Public" caption-side="top"}

If you want to start developing with your source code on {{site.data.keyword.cloud_notm}} Public, configure the GitHub tool integration or the {{site.data.keyword.gitrepos}} tool integration before you configure the {{site.data.keyword.deliverypipeline}}.
{: tip}
