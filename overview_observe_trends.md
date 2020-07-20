---

copyright:
  years: 2019, 2020
lastupdated: "2020-04-17"

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
{:shortdesc}

For more information about data sets, see [Managing data sets](/docs/ContinuousDelivery?topic=ContinuousDelivery-adding-data-sets).

The following figure shows unit test trends for builds from the master branch, and the number of passed and failed test cases for the build. 

![Deployment Unit Test Trends](images/DRA_unit_test_trends.png "Quality Trends page has a graph of passed and failed tests for a selected app and data set") Figure 1. Quality Trends page example

The quality trends graph correlates with the quality dashboard, and it is a good reference for noticing patterns in your builds. You can view trends for all test data. To view your quality trends dashboard, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**. Select your toolchain. Click the {{site.data.keyword.DRA_short}} tile, and then click **Quality Trends**. 

Click the dots within the graph to find out why there are dips in quality.
{: tip}
