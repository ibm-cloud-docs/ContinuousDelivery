---

copyright:
  years: 2019, 2022
lastupdated: "2022-03-25"

keywords: devops insights, publish, build, record, idra, test, tests, install, app, dashboard

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

# Publishing a build record (deprecated)
{: #publish-build-idra}

You can publish a build record by using idra (deprecated) to integrate your {{site.data.keyword.deliverypipeline}} with {{site.data.keyword.DRA_full}}. Build records notify {{site.data.keyword.DRA_short}} when a build is complete. This record contains the application name, branch, build ID, reference to Git repo, and more. You must publish build records to view any test records, deployment records, or evaluate policies in {{site.data.keyword.DRA_short}}.  
{: shortdesc}

{{site.data.keyword.DRA_short}} tracks deployment risk based on published test data. When you integrate {{site.data.keyword.DRA_short}} with your {{site.data.keyword.deliverypipeline}}, you are instrumenting {{site.data.keyword.DRA_short}} to gather information from the pipeline. Information that is gathered from the pipeline is presented in {{site.data.keyword.DRA_short}} dashboard to provide visibility into your DevOps process.

{{site.data.keyword.DRA_short}} requires the following information from your pipeline to analyze deployment risk:

* Build records
* Deployment records
* Test results


## Before you begin
{: #prereq-build-idra}

You must configure {{site.data.keyword.deliverypipeline}} in your toolchain to build, test, and deploy. For more information, see [Configuring {{site.data.keyword.deliverypipeline}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline).


## Publishing a build record (deprecated)
{: #build-idra}

In the last build job, use the following script to upload a build record.

```bash
#!/bin/bash
# Add user api key to stage environment variable as a secured property
export LOGICAL_APP_NAME="SampleApp"
export BUILD_PREFIX="master"

# $GIT_BRANCH, $GIT_URL, $GIT_COMMIT are environment variables made available by the CD pipeline
# node 4.x or above is needed
export PATH=/opt/IBM/node-v4.2/bin:$PATH
npm install -g grunt-idra3

idra --publishbuildrecord --branch=$GIT_BRANCH --repositoryurl=$GIT_URL --commitid=$GIT_COMMIT --status=pass
```
{: codeblock}

Environment variables that you define in the pipeline provide context for publishing these records. You can define them by using the `export` command in your jobs' scripts. You can also set them in each pipeline stage's Environment Properties menu.


| Environment Variable  | Purpose                                                                                        | Required |
|-----------------------|------------------------------------------------------------------------------------------------|-------------|
| `IBM_CLOUD_API_KEY`   | The {{site.data.keyword.Bluemix_notm}} user's API key.                                         | All jobs that start the idra CLI and enforce {{site.data.keyword.DRA_short}} risk policies.  |
| `LOGICAL_APP_NAME`    | The app's name on the dashboard.                                                               | All jobs that build, test, deploy, and enforce {{site.data.keyword.DRA_short}} risk policies. |
| `BUILD_PREFIX`        | Text that is added as a prefix to the stage's builds. This text also appears on the dashboard. | All jobs that build, test, deploy, and enforce {{site.data.keyword.DRA_short}} risk policies. |
{: caption="Table 1. Environment variable and purpose" caption-side="top"}

Be sure to use these variables consistently:

* The `IBM_CLOUD_API_KEY` is similar to a password; add it to each {{site.data.keyword.contdelivery_short}} pipeline stage environment as a Secure property.
* For a particular application, use the same `LOGICAL_APP_NAME` in all jobs or stages.
* Make sure that the `BUILD_PREFIX` is the same for a particular app and build type. For example, for builds from the master branch, `BUILD_PREFIX` might be `"master"`.


## Viewing build frequency
{: #build-frequency-idra}

When this build job completes, the pipeline publishes a message to {{site.data.keyword.DRA_short}} that a build is complete. You can view the build record on the Build Frequency page. To view the Build Frequency page, use the following steps.

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**.
2. Select your toolchain.
3. From your toolchain's Overview page, on the **IBM Cloud tools** card, click **{{site.data.keyword.DRA_short}}**.
4. Click **Build Frequency**.

## Next steps
{: #next-build-idra} 

Learn how to [publish a deployment record](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-deploy-idra) by using idra (deprecated).
