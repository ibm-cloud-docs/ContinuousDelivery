---

copyright:
  years: 2019, 2022
lastupdated: "2022-03-24"

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
{: #publish-build-cli}

Build records notify {{site.data.keyword.DRA_full}} when a build is complete. This record contains the application name, branch, build ID, reference to Git repo, and other fields. You must publish build records to view any test records, deployment records, or evaluate policies in {{site.data.keyword.DRA_short}}.  
{: shortdesc}


## Before you begin
{: #prereq-build-cli}

[Set consistent parameter values](/docs/ContinuousDelivery?topic=ContinuousDelivery-setting-values-cli).


## Uploading a build record
{: #upload-build-cli} 

In a build job, use the following script to upload a build record.

```bash
#!/bin/bash

#install the latest version of DevOps Insights plugin
ibmcloud plugin install -f doi

# Login to IBMCloud if you are not already logged in.  Assumes that $API_KEY environment variable has been set as a secured property in environment variable
ibmcloud login --apikey $API_KEY --no-region

# $GIT_BRANCH, $GIT_URL, $GIT_COMMIT are environment variables made available by the Continuous Delivery pipeline
# Assumes you have set $MY_APP_NAME and $MY_BUILD_NUMBER as described earlier

ibmcloud doi buildrecord-publish --logicalappname="$MY_APP_NAME" --buildnumber="$MY_BUILD_NUMBER" --branch $GIT_BRANCH --repositoryurl $GIT_URL --commitid $GIT_COMMIT --status pass
```
{: codeblock}

The `status` field takes the values `pass` or `fail`.
{: tip}


## Viewing the build frequency
{: #build-frequency-cli}

When the build job completes, the pipeline publishes a message to {{site.data.keyword.DRA_short}} that a build is complete. You can view the build record on the Build Frequency page. 

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Resource list**.
2. Select your toolchain.
3. From your toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.DRA_short}}**.
4. Click **Build Frequency** in the navigation.


## Next steps
{: #next-build-cli} 

[Publish a deployment record](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-deploy-cli).
