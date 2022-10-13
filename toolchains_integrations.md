---

copyright:
  years: 2015, 2022
lastupdated: "2022-10-13"

keywords: tool integrations, IBM Cloud Public, App Configuration, Artifactory, Bitbucket, Delivery Pipeline, DevOps Insights, Delivery Pipeline Private Worker, Git Repos and Issue Tracking, GitHub, GitLab, Hashicorp Vault, Jenkins, JIRA, IBM Key Protect, IBM Secrets Manager, Nexus, Custom Tool, PagerDuty, Rational Team Concert, Sauce Labs, Security and Compliance Center, Slack, SonarQube

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

|Tool integration |Tool type ID |Regions	|
|:----------|:----------|:------------------------------|
|[{{site.data.keyword.appconfig_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-app-configuration)		|appconfig |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[Artifactory](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-artifactory)		|artifactory |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[Bitbucket](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-bitbucket)		|bitbucketgit |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[{{site.data.keyword.deliverypipeline}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline) 		|pipeline |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London	   	|
|[{{site.data.keyword.deliverypipeline}} Private Worker](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-privateworker)			|private_worker |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Osaka, Sydney, London		|
|[{{site.data.keyword.DRA_short}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-dra)		|draservicebroker |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[{{site.data.keyword.gitrepos}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-grit)	|hostedgit |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[GitHub](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-github)		|githubconsolidated |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[GitLab](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-gitlab)		|gitlab |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[HashiCorp Vault](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-hashicorpvault)		|hashicorpvault |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[Jenkins](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-jenkins)	|jenkins |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[JIRA](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-jira)		|jira |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[{{site.data.keyword.keymanagementserviceshort}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-keyprotect)		|keyprotect |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[Nexus](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-nexus)			|nexus |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[Other Tool](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-othertool)			|customtool |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[PagerDuty](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-pagerduty)			|pagerduty |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[Rational Team Concert](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-rationalteamconcert)		|rationalteamconcert |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[Sauce Labs](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-saucelabs)		|saucelabs |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[Secrets Manager](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-secretsmanager)		|secretsmanager |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[Security and Compliance Center](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-scc)		|security_compliance |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[Slack](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-slack)		|slack |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
|[SonarQube](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-sonarqube)			|sonarqube |Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka, London		|
{: caption="Table 1. Tool integrations available for toolchains on {{site.data.keyword.cloud_notm}} Public" caption-side="top"}

If you want to start developing with your source code on {{site.data.keyword.cloud_notm}} Public, configure the GitHub tool integration or the {{site.data.keyword.gitrepos}} tool integration before you configure the {{site.data.keyword.deliverypipeline}}.
{: tip}
