---

copyright:
   years: 2020, 2021
lastupdated: "2021-04-20"

keywords: Kubernetes, Kube, cluster

subcollection: ContinuousDelivery

content-type: tutorial
account-plan: lite
completion-time: 10m

---

{:shortdesc: .shortdesc}
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}
{:important: .important}
{:external: target="_blank" .external}
{:step: data-tutorial-type='step'}

# Roll out your Kubernetes app by using the iter8 toolchain
{: #tutorial-cd-kube-iter8-toolchain}
{: toc-content-type="tutorial"}
{: toc-completion-time="10m"}

In this tutorial, you learn how to set up a continuous integration and delivery pipeline for containerized applications running on the {{site.data.keyword.containerlong}}. You set up source control, and then build, test, and deploy the code to different deployment stages. Then, you add integrations to other services like Slack notifications.
{: shortdesc}

![Architectural diagram](images/image.svg)
{: figure caption="Figure 1. A diagram that shows the architecture for my tutorial."}

The pipeline that you create has the following architecture:
1. Workflow step 1
1. Workflow step 2
1. Workflow step 3
1. Workflow step 4

## Before you begin
{: #cd-kube-prereqs}

* [Install the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started).
* [Set up the {{site.data.keyword.cloud_notm}} Container Registry CLI and your registry namespace](/docs/Registry?topic=registry-registry_setup_cli_namespace). 
* [Understand the basics of Kubernetes](https://kubernetes.io/docs/tutorials/kubernetes-basics/){: external}.

## Create a development Kubernetes cluster
{: #cd-kube-dev-cluster}
{: step}

To complete this tutorial, you need to set up a Kubernetes cluster on the {{site.data.keyword.containershort_notm}} service. The {{site.data.keyword.containershort_notm}} delivers powerful tools by combining Docker and Kubernetes technologies, an intuitive user experience, and built-in security and isolation to automate the deployment, operation, scaling, and monitoring of containerized apps in a cluster of compute hosts.

1. In the {{site.data.keyword.cloud}} catalog, go to the [Kubernetes Service](/kubernetes/catalog/cluster/create).
1. Select **Standard** as the cluster type, and select **2 MB / 1 Worker** as the machine type. All other options can be left as default.  
1. Click **Create** to create your cluster. Check the status of your cluster and worker nodes until they're in the Ready state. Your workers must be ready before you can proceed to the next step.

## Build your app locally
{: #cd-kube-build-app}
{: step}

You can build and run the app by using `mvn` for Java&trade; local development or `npm` for Node.js development. You can also build a Docker image and run the app in a container to make sure your app is run consistently both locally and on the cloud. Complete the following steps to build your Docker image.

1. Type **docker ps** to make sure that your local Docker engine is running.
   
2. Type **cd *project name*** to go to the generated project directory.
   
3. Type **ibmcloud dev build** to build the app locally.
   
It might take a few minutes to run the app because all of the app dependencies are downloaded, and a Docker image that contains your appl and all of the required environments, is built.

## Next steps
{: #cd-kube-step-next}

Want to start fresh? Remove the following resources that you created as a part of this tutorial:

* Delete the Git repo.
* Delete the toolchain.
* Delete the cluster.
* Delete the Slack channel.
