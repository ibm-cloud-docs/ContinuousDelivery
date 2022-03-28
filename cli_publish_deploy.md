---

copyright:
  years: 2019, 2022
lastupdated: "2022-03-25"

keywords: devops insights, publish, deploy, record, cli, deployment, test, tests, app

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
{: #publish-deploy-cli}

Deployment records inform {{site.data.keyword.DRA_short}} about the deployments that are made during the deployment process. This record contains the application name, build ID, environment name, status of the deployment, and more. 
{: shortdesc}


## Before you begin
{: #prereq-deploy-cli}

[Publish a build record](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-build-cli).

## Uploading a deployment record
{: #deploy-cli}

The application name and build ID in the deployment record must match the ones that are used in the build record for a specific build. In the deployment job, use the following script to upload a deployment record. The `--env` flag identifies the deployment environment.

```bash
#!/bin/bash

#install the DevOps Insights plugin
ibmcloud plugin install -f doi

# Login to IBMCloud if you are not already logged in.  Assumes that $API_KEY environment variable has been set as a secured property
ibmcloud login --apikey $API_KEY --no-region

ibmcloud doi deployrecord-publish --logicalappname="$MY_APP_NAME" --buildnumber="$MY_BUILD_NUMBER" --env staging --status pass
```
{: codeblock}

## Viewing deployment frequency
{: #deploy-frequency-cli}

When the deployment job completes, the pipeline publishes a message to {{site.data.keyword.DRA_short}} that the specified build and app was deployed. 

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **Resource List**.
2. Select your toolchain.
3. From your toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.DRA_short}}**.
4. Click **Deployment Frequency**.


## Next steps
{: #next-deploy-cli} 

[Publish test results](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-test-cli).
