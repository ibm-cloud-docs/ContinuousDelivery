---

copyright:
  years: 2019, 2020
lastupdated: "2020-06-24"

keywords: devops insights, publish, build, record, cli, test, tests, app

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:pre: .pre}

# Publishing a build record 
{: #publish-build-cicd}

You can publish a build record by using other continuous integration and continuous delivery (CI/CD) tools with the {{site.data.keyword.Bluemix_notm}} command line interface (CLI) to integrate with {{site.data.keyword.DRA_full}}. Build records notify {{site.data.keyword.DRA_short}} when a build is complete. This record contains the application name, branch, build ID, reference to Git repo, and other fields. You must publish build records to view any test records, deployment records, or evaluate policies in {{site.data.keyword.DRA_short}}.
{: shortdesc}


## Before you begin
{: #prereq-build-cicd}

Before you publish a build record, you must set consistent parameter values. For more information, see [Setting consistent parameter values by using other CI/CD tools](/docs/ContinuousDelivery?topic=ContinuousDelivery-setting-values-cicd).


## Publishing a build record with other CI/CD tools
{: #build-cicd}

In a build job, use the following script to upload a build record. Use the **`buildrecord-publish`** command to upload a build record. 

```bash
#!/bin/bash

#install the latest version of DevOps Insights plugin
ibmcloud plugin install -f doi

# Log in to IBM Cloud if you are not already logged in.  Assumes that $API_KEY environment variable has been set
ibmcloud login --apikey $API_KEY --no-region

# Please set variable $GIT_BRANCH, $GIT_URL and $GIT_COMMIT for better build record data
# Assumes you have set $MY_APP_NAME and $MY_BUILD_NUMBER as described earlier

ibmcloud doi buildrecord-publish --logicalappname="$MY_APP_NAME" --buildnumber="$MY_BUILD_NUMBER" --branch $GIT_BRANCH --repositoryurl $GIT_URL --commitid $GIT_COMMIT --status pass
```
{: codeblock}

The `status` field takes the `pass` or `fail` values.
{: tip}


## Viewing Build Frequency
{: #build-frequency-cicd}

When this build job completes, your CI/CD tool publishes a message to {{site.data.keyword.DRA_short}} that a build is complete. You can view the build record on the Build Frequency page. To view the Build Frequency page, use the following steps.

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**.
2. Select your toolchain from the table.  
3. Click the **{{site.data.keyword.DRA_short}}** tile.
4. Click **Build Frequency**.  


## Next steps
{: #next-build-cicd} 

[Publish a deployment record](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-deploy-cicd) by using other CI/CD tools.
