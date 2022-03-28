---

copyright:
  years: 2019, 2022
lastupdated: "2022-03-25"

keywords: devops insights, publish, deploy, record, cli, deployment, other ci/cd tools, app

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:pre: .pre}

# Publishing a deployment record
{: #publish-deploy-cicd}

You can publish a deployment record by using other continuous integration and continuous delivery (CI/CD) tools with the {{site.data.keyword.Bluemix}} command line interface (CLI) to integrate with {{site.data.keyword.DRA_full}}. Deployment records inform {{site.data.keyword.DRA_short}} about the deployments that are made during the deployment process. This record contains the application name, build ID, environment name, status of the deployment, and more. The application name and build ID in the deployment record must match the ones that are used in the build record for a specific build.
{: shortdesc}


## Before you begin
{: #prereq-deploy-cicd}

Before you publish a deployment a record, you must publish a build record. For more information about publishing a build record, see [Publishing a build record by using other CI/CD tools](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-build-cicd).


## Publishing a deployment record for {{site.data.keyword.contdelivery_short}}
{: #deploy-cicd}

In the deployment job, use the following script to upload a deployment record. The `--env` flag identifies the deployment environment. Use the `deployrecord-publish` command to upload a deployment record. 

```bash
#!/bin/bash

#install the DevOps Insights plugin
ibmcloud plugin install -f doi

# Log in to IBM Cloud if you are not already logged in.  Assumes that $API_KEY environment variable has been set as a secured property
ibmcloud login --apikey $API_KEY --no-region

ibmcloud doi deployrecord-publish --logicalappname="$MY_APP_NAME" --buildnumber="$MY_BUILD_NUMBER" --env staging --status pass
```
{: codeblock}


## Providing a job url to upload deployment records
{: #uploading-joburl}

Provide a `joburl` to upload deployment records. To include `joburl` as a parameter to upload a deployment record, pass it in as a parameter:

```text
ibmcloud doi deploymentrecord-publish --logicalappname "$MY_APP_NAME" --buildnumber "$MY_BUILD_NUMBER" --env staging --joburl "$JOB_URL" --status pass
```
{: codeblock}


## Viewing Deployment Frequency
{: #deploy-frequency-cicd}

When the deployment job completes, your CI/CD tool publishes a message to {{site.data.keyword.DRA_short}} that the specified build and app was deployed. You can view the deployment record on the Deployment Frequency page. To view the Deployment Frequency page, use the following steps:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**.
2. Select your toolchain.
3. From your toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.DRA_short}}**.
4. Click **Deployment Frequency**.

## Next steps
{: #next-deploy-cicd} 

[Publish test results](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-test-cicd) by using other CI/CD tools.
