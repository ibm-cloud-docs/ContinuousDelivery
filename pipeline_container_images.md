---

copyright:
  years: 2020
lastupdated: "2020-09-25"

keywords: Delivery Pipeline, container image

subcollection: ContinuousDelivery

---
<!-- Copyright info at top of file: REQUIRED
    The copyright info is YAML content that must occur at the top of the MD file, before attributes are listed.
    It must be surrounded by 3 dashes.
    The value "years" can contain just one year or a two years separated by a comma. (years: 2014, 2016)
    Indentation as per the previous template must be preserved.
-->

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

# Building container images
{: #pipeline_container_images}

You can use either Classic pipelines or Tekton pipelines to build container images.
{:shortdesc}

## Classic pipelines
{: #pipeline_classic_images}

You can use Classic pipelines to build container images by using the Container Registry job type. This job type provides context to access the IBM Cloud Container Registry, and uses the `cr build` command from the job's build script. Several of the toolchain templates use this script to build container images.

## Tekton pipelines
{: #pipeline_tekton_images}

The {{site.data.keyword.contdelivery_short}} service includes several Tekton tasks that you can reference within your pipelines to build container images. These tasks are stored in the [Open Toolchain Tekton Catalog](https://github.com/open-toolchain/tekton-catalog/tree/master/container-registry){:external}:

* [icr-containerize](https://github.com/open-toolchain/tekton-catalog/blob/master/container-registry/README.md#icr-containerize
){:external}: Builds and pushes an image to the [IBM Cloud Container Registry](/docs/Registry?topic=Registry-getting-started). This task depends on [Buildkit](https://github.com/moby/buildkit){:external} to build the container image.
* [icr-execute-in-dind](https://github.com/open-toolchain/tekton-catalog/blob/master/container-registry/README.md#icr-execute-in-dind){:external}: Runs Docker commands such as build and inspect, against a Docker engine that is running as a sidecar container. Then, it pushes the resulting image to the IBM Cloud Container Registry.

* [icr-execute-in-dind-cluster](https://github.com/open-toolchain/tekton-catalog/blob/master/container-registry/README.md#icr-execute-in-dind-cluster){:external}: Runs Docker commands such as build and inspect, against a Docker engine that is running in a Kubernetes cluster. If a Docker DinD isn't available on the build cluster, a new one is deployed. Then, it pushes the resulting image to the IBM Cloud Container Registry.

