---

copyright:
  years: 2015, 2020
lastupdated: "2019-08-20"

keywords: IBM Cloud, build types, build jobs, deployment job, build script, create pipeline, 

subcollection: ContinuousDelivery

---


{:screen: .screen}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:shortdesc: .shortdesc}

# Working with pipelines 
{: #pipeline-working}

To automate your builds and deployments to {{site.data.keyword.cloud}}, use {{site.data.keyword.contdelivery_full}} pipelines.
{: shortdesc}

With pipelines, you can choose from several build types. You provide the build script, and {{site.data.keyword.contdelivery_short}} runs it; you don't need to set up build systems. Then, with one click, you can automatically deploy your app to one or many {{site.data.keyword.cloud_notm}} spaces, public Cloud Foundry servers, or Docker containers on the {{site.data.keyword.containerlong}}.

Build jobs compile and package your app source code from Git repositories. The build jobs produce deployable artifacts, such as WAR files or Docker containers for the {{site.data.keyword.containerlong_notm}}. In addition, you can run unit tests within your build automatically. You can set up your build jobs so that each time a commit is pushed, a build is triggered.

A deployment job takes output from a build job and deploys it to either the {{site.data.keyword.containerlong_notm}} or Cloud Foundry servers such as {{site.data.keyword.cloud_notm}}.

You can deploy to one or many regions and services. For example, you can set up your {{site.data.keyword.deliverypipeline}} to use one or more services, test in one region, and deploy to production in multiple regions.

## Creating a pipeline
{: #creating-pipeline}

You can use any of the following methods to create a pipeline:

   * [Create a toolchain from an existing Cloud Foundry application](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_an_app). The resulting toolchain contains a pipeline.

   * [Create a toolchain from a template](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_a_template) that includes at least one pipeline.

   * [Add the {{site.data.keyword.deliverypipeline}} tool integration](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#deliverypipeline) to an existing toolchain.
   
From your {{site.data.keyword.deliverypipeline}}, change your configuration; check the status of builds, the deployed app, and recent deployments; see the most recent logs and deployment details; or delete your pipeline.

## Viewing a pipeline by using the CLI
{: #viewing-pipeline-cli}

To get the details that are required to invoke a pipeline, run the `**ibmcloud dev toolchains**` command to view the name of the toolchain. If you already know the name of the toolchain, run the `**ibmcloud dev toolchain-get [toolchain-name]**` to view the toolchain details. 

* To get the details of a pipeline and its stages, identify the pipeline and its ID to run the following command:
  ```
  ibmcloud dev pipeline-get [pipelineID]
  ```
  {: codeblock}

* Using the pipeline ID from the previous command, you can now run the pipeline:
  ```
  ibmcloud dev pipeline-run [pipelineID]
  ```
  {: codeblock}

  This command invokes an execution of the stage and its jobs. A successful execution results in the job execution for each job in the selected stage.
  
### Viewing pipeline logs by using the CLI
{: #viewing-pipeline-logs-cli}

You can view detailed output of each stage during a pipeline's execution.

* To view the logs from a pipeline's execution, run the following command:
  ```
  ibmcloud dev pipeline-log [pipelineID]
  ```
  {: codeblock}

* To filter the logs by stage, apply the previous command and add the stage ID:
  ```
  ibmcloud dev pipeline-log [pipelineID] --stage-id [stageID]
  ```
  {: codeblock}
