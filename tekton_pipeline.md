---

copyright:
  years: 2020
lastupdated: "2020-01-14"

keywords: Tekton integration, delivery pipeline, Tekton delivery pipeline

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}


# Working with Tekton pipelines
{: #tekton-pipelines}

Tekton Pipelines is an open source project that you can use to configure and run continuous integration and {{site.data.keyword.contdelivery_short}} pipelines within a Kubernetes cluster. Tekton pipelines are defined in yaml files, which are typically stored in a Git repository (repo). 
{: shortdesc}

Tekton provides a set of [Custom Resources](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/){:external} extensions to Kubernetes to define pipelines. The following basic Tekton Pipeline resources are included in these extensions:

|Resource |Description	|
|:----------|:------------------------------|
|`Task`		|Defines a set of build steps such as compiling code, running tests, and building and deploying images.		|
|`Pipeline`		|Defines the set of tasks that compose a pipeline.		|
| `PipelineResource`		|Defines an object that is an input (such as a Git repository) or an output (such as a Docker image) of the pipeline.   		|
|`PipelineRun`		|Defines the execution of a pipeline. This resource references the Pipeline to run and which PipelineResource(s) to use as input and output.   |
{: caption="Table 1. Tekton pipeline resources" caption-side="top"}

There are several advantages to using Tekton Pipelines:

* **Cloud Native**: Tekton Pipelines run on Kubernetes, use Kubernetes clusters as a first class type, and use containers as their building blocks.
* **Decoupled**: You can use one pipeline to deploy to any Kubernetes cluster. You can run the tasks that comprise a pipeline in isolation. And you can switch resources (such as Git repos) between pipeline runs.
* **Typed**: You can switch implementations for specific types of resources, such as images.

The Tekton Pipelines project is an alpha release. You must update your pipeline with each new version of Tekton. For more information about the latest version of Tekton, see [https://github.com/tektoncd/pipeline/releases](https://github.com/tektoncd/pipeline/releases){:external}.
{: important}

{{site.data.keyword.contdelivery_full}} provides two types of delivery pipelines that you can use to build, test, and deploy your applications.

* **Classic**: Classic delivery pipelines are created graphically, with the status embedded in the pipeline diagram. These pipelines can run on shared workers in the cloud or on private workers that run on your own Kubernetes cluster. 
* **Tekton**: Tekton delivery pipelines are created within yaml files that define pipelines as a set of Kubernetes resources. You can edit those yaml files to change the behaviour of a pipeline. Tekton pipelines can run on private workers that run on your own cluster. They can also run on IBM-managed workers on the public cloud. The Tekton integration provides a dashboard that you can use to view the output of Tekton pipeline runs. It also provides mechanisms for identifying the pipeline definitions repo, the pipeline triggers, where the pipeline runs, and the storage and retrieval of properties.

When you use IBM-managed workers, only one Tekton pipeline can run per pipeline at a time. When you use private workers, multiple Tekton pipelines can run concurrently.
{: important}

Both types of pipelines isolate jobs or steps from one another by running in separate containers, and by using an image that you choose. Classic and Tekton pipelines both exist in a [toolchain](https://cloud.ibm.com/devops/toolchains){:external} and depend on that toolchain to add more tool integrations that are used in the build, test, and deployment process.
{: tip}

## Prerequisites
{: #tekton_pipelines_prereqs}

Before you add and run a Tekton pipeline, make sure that you have the following resources in place:

* [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-install-ibmcloud-cli) installed locally.
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/){:external} installed locally.
* A Kubernetes cluster such as an [{{site.data.keyword.containerlong}} cluster](https://cloud.ibm.com/kubernetes/catalog/cluster){:external}.
* A toolchain that contains the following tool integrations:

  * A repo tool integration (such as the GitHub tool integration) that contains your Tekton pipeline code, including a Tekton yaml file. For more information about getting started with Tekton pipelines, see [Tekton Pipelines](https://github.com/tektoncd/pipeline/tree/v0.8.0/docs#tekton-pipelines){:external}.
  * A {{site.data.keyword.deliverypipeline}} Private Worker tool integration that references your Kubernetes cluster. For more information about private workers, see [Installing Delivery Pipeline Private Workers](/docs/ContinuousDelivery?topic=ContinuousDelivery-install-private-workers).

The toolchain and the {{site.data.keyword.deliverypipeline}} Private Worker tool integration must be in the same region. 
{: important}

## Creating a {{site.data.keyword.deliverypipeline}} for Tekton 
{: #create_tekton_pipeline}

When you configure a {{site.data.keyword.deliverypipeline}} tool integration, you can select the type of pipeline that you want to create.

1. If you are configuring this tool integration as you are creating the toolchain, in the Configurable Integrations section, click **{{site.data.keyword.deliverypipeline}}**. Depending on the template that you use, different fields might be available. Review the default field values and if needed, change those settings.
1. If you have a toolchain and are adding this tool integration to it, on the DevOps dashboard, on the Toolchains page, click the toolchain to open its Overview page. Alternatively, on your app's Overview page, on the Continuous delivery card, click **View Toolchain** and click **Overview**.

 a. Click **Add a Tool**.

 b. In the Tool Integrations section, click **{{site.data.keyword.deliverypipeline}}**.

1. Specify a name for your new pipeline.
1. Select **Tekton** to create a Tekton {{site.data.keyword.deliverypipeline}}. This type of pipeline provides a dashboard that you can use to view the output of Tekton pipeline runs on a defined Kubernetes cluster, with support for configuring the pipeline definitions repos, the pipeline triggers, where the pipeline runs, and simple secrets.
1. If you plan to use your pipeline to deploy a user interface, select the **Show apps in the VIEW APP menu** checkbox. All of the apps that your pipeline creates are shown in the **View App** list on the toolchain's Overview page.
1. Click **Create Integration** to add the {{site.data.keyword.deliverypipeline}} to your toolchain.

### Configuring a {{site.data.keyword.deliverypipeline}} for Tekton 
{: #configure_tekton_pipeline}

1. Click the **{{site.data.keyword.deliverypipeline}}** card to open the Tekton {{site.data.keyword.deliverypipeline}} dashboard.
1. In the **Definitions** tab, complete the following tasks:

 a. Specify the Git repo and URL that contains the Tekton pipeline definition and related artifacts.

 b. Select the branch within your Git repo that you want to use.
 
 c. Specify the path to your pipeline definition within the Git repo. You can reference a specific definition within the same repo.
 
1. In the **Worker** tab, select the private worker that you want to use to run your Tekton pipeline on the associated cluster. For more information about private workers, see [Working with Delivery Pipeline Private Workers](/docs/ContinuousDelivery?topic=ContinuousDelivery-private-workers).

 The private worker must be defined in the same toolchain as your Tekton pipeline.
 {: important}

1. In the **Triggers** tab, click **Add trigger** to create a manual, timed, or Git repository trigger, and then associate that trigger with an event listener. Manual triggers run when you click the **Run** pipeline button and select the trigger. Timed triggers run at a scheduled time that is defined by the [CRON](http://crontab.org/){:external} value. Git repository triggers run when the specified Git event type occurs for the specified Git repo and branch. The list of available event listeners is populated with the listeners that are defined in the pipeline code repo.
 
 Triggers are based on [Tekton trigger definitions](https://github.com/tektoncd/triggers){:external}. Git respository triggers use the event listener that they are mapped to to extract information from the incoming event payload and create Kubernetes resources. These resources are applied to a Tekton `PipelineRun` resource.
 {: tip}

 The CRON expression for timed triggers is based on the [UNIX crontab syntax](http://crontab.org/){:external} and is a sequence of five time and date fields: `minute`, `hour`, `day of the month`, `month`, and `day of the week`. These fields are separated by spaces in the format `X X X X X`. The following examples show strings that use various timed frequencies.
   * `* * * * *` - The trigger runs every minute.
   * `0 * * * *` - The trigger runs at the start of every hour.
   * `0 9 * 1 MON-FRI` - The trigger runs at 9:00 AM every weekday in January.
   * `0 * * NOV,DEC 1` - The trigger runs every hour on Mondays during November and December.
 
 You can access the webhook payload that is delivered to a Git trigger from your Tekton pipeline resources. Although the exact fields are repo-specific, the general syntax for the webhook payload is `$(event.payloadFieldName)`.
 {: tip}

1. In the **Environment properties** tab, click **Add property** and define your own environment property. For example, you can define an `API_KEY` property that passes an API key that is used by all of the scripts in the pipeline to access {{site.data.keyword.cloud_notm}} resources. You can add the following types of properties:

 * **Text**: A property key with a single-line value.
 * **Text area**: A property key with a multi-line value.
 * **Secure**: A property key with a single-line value that is secured with AES-128 encryption. This value is displayed by using the asterisk character.
 
 You can access these properties in your Tekton pipeline resources. For example, to access the `API_KEY` property, type `$(params.API_KEY)`.
 {: tip}

1. Click **Save** and then **Close**.

## Viewing the {{site.data.keyword.deliverypipeline}} for Tekton dashboard 
{: #view_tekton_dashboard}

The Tekton {{site.data.keyword.deliverypipeline}} dashboard displays an empty table until at least one Tekton pipeline runs. After Tekton pipeline runs occur (either manually or as the result of external Git events), the table lists those runs, their status, and the last updated time of the run definition.

Pipeline runs can be in any of the following states:

* **Pending**: The `PipelineRun` definition is queued and waiting to run.
* **Running**: The `PipelineRun` definition is running in the cluster.
* **Succeeded**: The `PipelineRun` definition successfully completed in the cluster.
* **Failed**: The `PipelineRun` definition run failed. Review the log file for the run to determine the cause.

For detailed information about a selected run, click any row in the table. You view the `Task` definition and the steps in each `PipelineRun` definition. You can also view the status, logs, and details of each `Task` definition and step, and the overall status of the `PipelineRun` definition.
