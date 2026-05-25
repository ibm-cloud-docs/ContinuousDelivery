---

copyright:
  years: 2019, 2026
lastupdated: "2026-05-25"

keywords: devops insights, risk, analysis, application, environment, app, dashboard

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Analyzing risks for your deployment environments
{: #deployment-environment}

{{site.data.keyword.DRA_short}} will be discontinued in all regions on February 12, 2027. New {{site.data.keyword.DRA_short}} tool integrations cannot be created after June 12, 2026. However, if the feature has no active usage, it may be discontinued earlier. [Learn more](/docs/ContinuousDelivery?topic=ContinuousDelivery-faq_region_feature_consolidation)
{: important}

Risk analysis is useful for customers that deploy to several environments. You can view all of your apps deployments and deployment environments. With risk analysis, you get an overview of the risks that are associated with your applications from all of your environments. The Risk Analysis page is automatically populated with the most recent information that is sent from your continuous integration and continuous delivery (CI/CD) tools.
{: shortdesc}

![Deployment Risk analysis](images/DRA_risk_analysis.png){: caption="Risk Analysis page" caption-side="bottom"}

Within the Risk Analysis dashboard you can select from two tabs: **Application** and **Environment**. Within the **Application** tab, you can see the number of active builds and risk evaluations for each of your apps. In the **Environment** tab, you can view the location of the app, the number of deployed applications, and the risk evaluations associated with the environment.

To view the Risk Analysis page, complete the following steps:

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Toolchains**.
1. On the Toolchains page, click your toolchain to open its Overview page.
1. On the **IBM Cloud tools** card, click the {{site.data.keyword.DRA_short}} tool integration.
1. From the menu, select **Risk Analysis**.
