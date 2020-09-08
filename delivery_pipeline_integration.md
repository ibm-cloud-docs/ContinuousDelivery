---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-19"

keywords: tool integrations, IBM Cloud Public, IBM Cloud Dedicated, Delivery Pipeline
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

# Configuring Delivery Pipeline
{: #deliverypipeline}

{{site.data.keyword.deliverypipeline}} automates the continuous deployment of your projects through sequences of stages that retrieve input and run jobs, such as builds, tests, and deployments.
{:shortdesc}

Configure {{site.data.keyword.deliverypipeline}} to automate the continuous building, testing, and deployment of your apps:

1. If you are configuring this tool integration as you are creating the toolchain, in the Configurable Integrations section, click **{{site.data.keyword.deliverypipeline}}**. Depending on the template that you use, different fields might be available. Review the default field values and if needed, change those settings.
1. If you have a toolchain and are adding this tool integration to it, from the {{site.data.keyword.cloud_notm}} console, click the menu icon ![hamburger icon](images/icon_hamburger.svg) and select **DevOps**. On the Toolchains page, click the toolchain that you want to add {{site.data.keyword.deliverypipeline}} to. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View toolchain**. Then, click **Overview**.

 a. Click **Add tool**.

 b. In the Tool Integrations section, click **{{site.data.keyword.deliverypipeline}}**.

1. Specify a name for your new pipeline.
1. If you plan to use your pipeline to deploy a user interface, select the **Show apps in the View app menu** checkbox. All of the apps that your pipeline creates are shown in the **View App** list on the toolchain's Overview page.
1. Select the type of pipeline that you want to create:

 * **Classic**: Provides an easy to use graphical user interface for defining stages and jobs that run on public shared infrastructure, with support for running individual stages on private workers.
 * **Tekton**: Provides a dashboard that you can use to view the output of [Tekton pipeline](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-tekton-pipelines) runs on a defined Kubernetes cluster, with support for configuring pipeline definitions repos, the pipeline triggers, where the pipeline runs, and simple secrets.

1. Click **Create Integration** to add the {{site.data.keyword.deliverypipeline}} to your toolchain.
1. Click **{{site.data.keyword.deliverypipeline}}** to view the pipeline and configure it. To learn the basics of configuring a pipeline, see [Building and deploying pipelines](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

  If you want the pipeline to automatically run when a commit is pushed to your GitHub, {{site.data.keyword.ghe_short}}, or Git repository (repo), follow these steps:

   a. Configure GitHub, {{site.data.keyword.ghe_short}}, or {{site.data.keyword.gitrepos}} for your toolchain before you define the stages for your pipeline. The pipeline stages need the Git URLs for your repos. Each pipeline stage can refer to only one of the GitHub, {{site.data.keyword.ghe_short}}, or Git repos that are associated with your toolchain. For instructions to configure GitHub, see the [GitHub](#github) section. For instructions to configure Dedicated {{site.data.keyword.ghe_short}}, see [Getting started with {{site.data.keyword.ghe_long}}](/docs/services/ghededicated?topic=ghededicated-getting-started). For instructions to configure {{site.data.keyword.gitrepos}}, see the [{{site.data.keyword.gitrepos}}](#grit) section.

   b. Use a webhook. Without a webhook, you can run pipelines manually only. To use a webhook when you link to a GitHub or {{site.data.keyword.ghe_short}} repo, you need admin privileges. To link to a {{site.data.keyword.gitrepos}} repo, you need Master or Owner privileges.

1. Optional: If you are using a toolchain on {{site.data.keyword.Bluemix_notm}} Public and you want Sauce Labs to run tests on your app, configure the {{site.data.keyword.deliverypipeline}} to add a Sauce Labs test job. For instructions to configure the test job, see the [Configuring a Sauce Labs test job in your pipeline](#config_saucelabs) section.

## Configuring a Sauce Labs test job in your pipeline
{: #config_saucelabs}

Before you configure a Sauce Labs test job in your pipeline, you need a working pipeline that has stages to build and deploy your app. You must also configure Sauce Labs for your toolchain. For instructions to configure Sauce Labs, see the [Sauce Labs](#saucelabs) section.

Configure the {{site.data.keyword.deliverypipeline}} to add a Sauce Labs test job:

1. If you don't have a stage that deploys a test version of your app, create one.
1. On the stage, add a test job after the deploy job. By placing these jobs in the same stage, they can access the same set of environment properties.   
  ![Test job](images/toolchain_test_job.png)

1. Configure the stage. On the **ENVIRONMENT PROPERTIES** tab, create the CF_APP_NAME property.

  The Sauce Labs user name and access key are available in the test job script as the SAUCE_USERNAME and SAUCE_ACCESS_KEY environment variables. When you write your tests, you must use these environment variables to authenticate with Sauce Labs.
  {: tip}

1. Configure the deploy job. In the **Deploy Script** field, include this command: `export CF_APP_NAME="$CF_APP"`. That command exports the app name as an environment property.
1. Configure the test job. 
  The **Service Instance**, **Target**, **Organization**, and **Space** fields are populated with the Sauce Labs user name, region, org, and space that you are using.
  {: tip}

  a. For the tester type, select **Sauce Labs**.

  b. For the service instance, select the Sauce Labs user name that you used when you configured Sauce Labs for your toolchain.

   To see the user name and access key that you used when you configured Sauce Labs for your toolchain, click **Configure**.
   {: tip}

  c. In the **Test Execution Command** field, enter the commands that install the dependencies that are required by your tests and then run the tests. For example, for a Node.js app, you might enter these commands:
     ```
     npm install
     node_modules/grunt-cli/bin/grunt test:sauce:parallel
     ```

    d. If you want to see your test reports in the test job logs, select the **Enable Test Report** checkbox, and set the Test Result File Pattern to `test/*.xml`.

1. Click **SAVE**. Whenever your pipeline runs, your Sauce Labs tests run.

## Learn more about Delivery Pipeline

To learn more about {{site.data.keyword.deliverypipeline}}, see [Working with pipelines](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-pipeline-working) and the [Delivery Pipeline article](https://www.ibm.com/cloud/garage/content/deliver/tool_delivery_pipeline/){:external} on the IBM Cloud Garage Method or take these tutorials:

  * [Create a pipeline](https://www.ibm.com/cloud/garage/tutorials/create-a-pipeline){:external}

  * [Create and use your first toolchain by using the "Develop a Cloud Foundry app" toolchain](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:external}
