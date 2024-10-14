---

copyright:
  years: 2019, 2022
lastupdated: "2022-03-25"

keywords: devops insights, publish, deploy, record, deployment, jenkins, app

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Publishing a deployment record
{: #publish-deploy-jenkins}

You can publish a deployment record by using Jenkins to integrate your projects with {{site.data.keyword.DRA_full}}. Deployment records inform {{site.data.keyword.DRA_short}} about the deployments that are made during the deployment process. This record contains the application name, build ID, environment name, status of the deployment, and more. The application name and build ID in the deployment record must match the ones that are used in the build record for a specific build.
{: shortdesc}


## Before you begin
{: #prereq-deploy-jenkins}

Before you publish a deployment a record, you must publish a build record. For more information, see [Publishing a build record by using Jenkins](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-build-jenkins).


## Publishing a deployment record 
{: #deploy-jenkins}

Publish deployment records with the publishDeployRecord step. This step requires two parameters. It can also accept two of the three optional parameters.

| Parameter         | Definition                                                                                                                   |
|-------------------|------------------------------------------------------------------------------------------------------------------------------|
| `environment`     | The environment to which you deploy your app, like DEV or STAGING or any other value.                                        |
| `result`          | The result of the build stage. The value is either `SUCCESS` or `FAIL`.                                                      |
| `appUrl`          | Optional: The URL used to access your application.                                                                           |
| `buildNumber`     | Optional: The set value to any string that represents version number.                                                            |
| `applicationName` | Optional: Set the application name. If this value is set, the environment variable `IBM_CLOUD_DEVOPS_APP_NAME` is ignored. |
{: caption="Publishing build records parameters and definitions" caption-side="top"}

The following example commands include the parameters. The first command publishes the deployment record for a staging environment. The second command publishes the deployment record for a production environment.

```text
publishDeployRecord environment: "STAGING", appUrl: "http://staging-Weather-App.mybluemix.net", result:"SUCCESS"
publishDeployRecord environment: "PRODUCTION", appUrl: "http://Weather-App.mybluemix.net", result:"SUCCESS"
```
{: codeblock}

For each command, you need to specify the toolchain ID to export the environment variable. For more information, see [Environment variables and definitions](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-build-jenkins). 
{: tip} 


## Viewing the deployment frequency
{: #deploy-frequency-jenkins}

When the deployment job completes, the pipeline publishes a message to {{site.data.keyword.DRA_short}} that the specified build and app was deployed. You can view the deployment record on the Deployment Frequency page. To view the Deployment Frequency page, use the following steps:

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **DevOps**.
2. Select your toolchain.
3. From your toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.DRA_short}}**.
4. Click **Deployment Frequency**.

## Next steps
{: #next-deploy-jenkins}

[Publish test results](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-test-jenkins) by using Jenkins.
