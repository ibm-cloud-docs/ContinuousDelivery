---

copyright:
  years: 2019, 2020
lastupdated: "2020-04-20"

keywords: devops insights, publish, deploy, record, idra, test, tests, app, dashboard

subcollection: ContinuousDelivery

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Publishing a deployment record (deprecated)
{: #publish-deploy-idra}

You can publish a deployment record by using idra (deprecated) to integrate your {{site.data.keyword.deliverypipeline}} with {{site.data.keyword.DRA_short}}. Deployment records inform {{site.data.keyword.DRA_full}} about the deployments that are made during the deployment process. This record contains the application name, build ID, environment name, status of the deployment, and more. The application name and build ID in the deployment record must match the ones that are used in the build record for a specific build.
{:shortdesc}


## Before you begin
{: #prereq-deploy-idra}

Before you publish a deployment a record, you must publish a build record. For more information about publishing a build record, see [Publishing a build record by using idra (deprecated)](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-build-idra).


## Publishing a deployment record (deprecated)
{: #deploy-idra}

In the deployment job, use the following script to upload a deployment record. The `--env` flag identifies the deployment environment.

```
#!/bin/bash
# Add user api key to stage environment variable as a secured property
export LOGICAL_APP_NAME="SampleApp"
export BUILD_PREFIX="master"

# node 4.x or above is needed
export PATH=/opt/IBM/node-v4.2/bin:$PATH
npm install -g grunt-idra3

idra --publishdeployrecord --env=staging --status=pass
```
{:codeblock}

Environment variables that you define in the pipeline provide context for publishing these records. You can define them by using the `export` command in your jobs' scripts. You can also set them in each pipeline stage's Environment Properties menu.


| Environment Variable  | Purpose                                                                                        | Required |
|-----------------------|------------------------------------------------------------------------------------------------|-------------|
| `IBM_CLOUD_API_KEY`   | The {{site.data.keyword.Bluemix_notm}} user's API key.                                         | All jobs that start the idra CLI and enforce {{site.data.keyword.DRA_short}} risk policies.  |
| `LOGICAL_APP_NAME`    | The app's name on the dashboard.                                                               | All jobs that build, test, deploy, and enforce {{site.data.keyword.DRA_short}} risk policies. |
| `BUILD_PREFIX`        | Text that is added as a prefix to the <br> stage's builds. This text also appears <br> on the dashboard. | All jobs that build, test, deploy, and enforce {{site.data.keyword.DRA_short}} risk policies. |
{: caption="Table 1. Environment variable and purpose" caption-side="top"}

Be sure to use these variables consistently:

* The `IBM_CLOUD_API_KEY` is similar to a password; add it to each {{site.data.keyword.contdelivery_short}} pipeline stage environment as a Secure property.
* For a particular application, use the same `LOGICAL_APP_NAME` in all jobs or stages.
* Make sure that the `BUILD_PREFIX` is the same for a particular app and build type. For example, for builds from the master branch, `BUILD_PREFIX` might be `"master"`.


## Viewing Deployment Frequency
{: #deploy-frequency-idra}

When the deployment job completes, the pipeline publishes a message to {{site.data.keyword.DRA_short}} that the specified build and app was deployed. You can view the deployment record on the Deployment Frequency page. To view the Deployment Frequency page, use the following steps:

1. From the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**.
2. Select your toolchain from the table.  
3. Click the **{{site.data.keyword.DRA_short}}** tile.
4. Click **Deployment Frequency**.


## Next steps
{: #next-deploy-idra} 

Learn how to [publish test results](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-test-idra) by using idra (deprecated).
