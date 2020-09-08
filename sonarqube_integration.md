---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-19"

keywords: tool integrations, IBM Cloud Public, IBM Cloud Dedicated, Sonarqube

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

# Configuring Sonarqube
{: #sonarqube}

SonarQube provides an overview of the overall health and quality of your source code and highlights issues that are found in new code. The code analyzers detect tricky bugs, such as null-pointer dereferences, logic errors, and resource leaks, for more than 20 coding languages.
{:shortdesc}

Configure SonarQube to continuously analyze and measure the quality of your source code:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**. 
 
 a. Click **Add a Tool**.

 b. In the Tool Integrations section, click **SonarQube**.

1. Type a name for this instance of the SonarQube tool integration.
1. Type the URL for the SonarQube instance that you want to open when you click the SonarQube card from your toolchain.
1. Optional: Type the user name that you use to connect to the SonarQube server.

 You need to specify a user name only if you use a password to connect to the SonarQube server. If you use an authentication token to connect, leave this field empty.
 {: tip}

1. Type the password or authentication token that you use to connect to the SonarQube server.
1. Click **Create Integration**.
1. From your toolchain, click **SonarQube** to view the dashboard for the SonarQube instance that you connected to.

## Learn more about SonarQube

To learn more about SonarQube, see [Integrate your SonarQube analysis into your toolchain](https://www.ibm.com/blogs/cloud-archive/2017/06/integrate-sonarqube-analysis-into-your-toolchain/){:external}. 
