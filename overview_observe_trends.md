---

copyright:
  years: 2019, 2022
lastupdated: "2022-03-25"

keywords: devops insights, observe trends, quality trends, trends, code coverage, test, tests, verification, app, sonarqube, dashboard

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:pre: .pre}

# Observe trends over time
{: #observe-trends}

The Quality Trends page shows the number of test cases that are passed or failed for a particular build. You can view trends for quality data sets such as unit tests, functional verification tests, code coverages, SonarQube scans, and security scans for builds. 
{: shortdesc}

For more information about data sets, see [Managing data sets](/docs/ContinuousDelivery?topic=ContinuousDelivery-adding-data-sets).

The following figure shows unit test trends for builds from the master branch, and the number of passed and failed test cases for the build. 

![Deployment Unit Test Trends](images/DRA_unit_test_trends.png){: caption="Figure 1. Quality Trends page" caption-side="bottom"}

The Quality Trends graph correlates with the Quality dashboard, and it is a good reference for noticing patterns in your builds. You can view trends for all of the test data in your Quality Trends dashboard.

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **DevOps**.
1. On the Toolchains page, click your toolchain to open its Overview page.
1. On the **IBM Cloud tools** card, click the {{site.data.keyword.DRA_short}} tool integration.
1. From the menu, select **Quality Trends**. 

Click the dots within the graph to find out why there are dips in quality.
{: tip}
