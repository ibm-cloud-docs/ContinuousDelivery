---

copyright:
  years: 2020, 2021
lastupdated: "2021-09-15"

keywords: Delivery Pipeline, container image

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

# Building container images
{: #pipeline_container_images}

You can use either Classic pipelines or Tekton pipelines to build container images.
{: shortdesc}

## Classic pipelines
{: #pipeline_classic_images}

You can use Classic pipelines to build container images by using the Container Registry job type. This job type provides context to access the {{site.data.keyword.registrylong}}, and uses the [Buildkit](https://github.com/moby/buildkit){: external} command from the job's [build script](https://github.com/open-toolchain/commons/blob/master/scripts/build_image_buildkit.sh). Several of the toolchain templates use this script to build container images.

The [`cr build`](/docs/container-registry-cli-plugin?topic=container-registry-cli-plugin-containerregcli#bx_cr_build) command is deprecated. To migrate your existing build container image job from the `cr build` command to the [Buildkit](https://github.com/moby/buildkit){: external} command, edit your stage properties and select your build container image job. Replace the line that sources `build_image.sh` with `source <(curl -sSL "https://raw.githubusercontent.com/open-toolchain/commons/master/scripts/build_image_buildkit.sh")`. When you switch to use this script, you must provide a new `IBM_CLOUD_API_KEY` secret environment variable for the corresponding stage. This API key must have access to the namespace in which the image is built. If the `IBM_CLOUD_API_KEY` secret environment variable is not provided, 401 errors appear in the logs. For more information about this replacement, see the [{{site.data.keyword.registrylong}} is Deprecating Container Builds](https://www.ibm.com/cloud/blog/announcements/ibm-cloud-container-registry-deprecating-container-builds){: external} blog post.
{: deprecated}

## Tekton pipelines
{: #pipeline_tekton_images}

The {{site.data.keyword.contdelivery_short}} service includes several Tekton tasks that you can reference within your pipelines to build container images. These tasks are stored in the [Open Toolchain Tekton Catalog](https://github.com/open-toolchain/tekton-catalog/tree/master/container-registry){: external}:

* [icr-containerize](https://github.com/open-toolchain/tekton-catalog/blob/master/container-registry/README.md#icr-containerize){: external}: Builds and pushes an image to the [{{site.data.keyword.registrylong}}](/docs/Registry?topic=Registry-getting-started). This task depends on [Buildkit](https://github.com/moby/buildkit){: external} to build the container image.

* [icr-execute-in-dind](https://github.com/open-toolchain/tekton-catalog/blob/master/container-registry/README.md#icr-execute-in-dind){: external}: Runs Docker commands such as build and inspect, against a Docker engine that is running as a sidecar container. Then, it pushes the resulting image to the {{site.data.keyword.registrylong}}.

* [icr-execute-in-dind-cluster](https://github.com/open-toolchain/tekton-catalog/blob/master/container-registry/README.md#icr-execute-in-dind-cluster){: external}: Runs Docker commands such as build and inspect, against a Docker engine that is running in a Kubernetes cluster. If a Docker DinD isn't available on the build cluster, a new one is deployed. Then, it pushes the resulting image to the {{site.data.keyword.registrylong}}.


The [`cr build`](/docs/container-registry-cli-plugin?topic=container-registry-cli-plugin-containerregcli#bx_cr_build) command is deprecated. If you use this command, or reference it from the [icr-cr-build](https://github.com/open-toolchain/tekton-catalog/blob/master/container-registry/README.md#icr-cr-build){: external} task, you can migrate to the [icr-containerize](https://github.com/open-toolchain/tekton-catalog/blob/master/container-registry/README.md#icr-containerize
){: external}, [icr-execute-in-dind](https://github.com/open-toolchain/tekton-catalog/blob/master/container-registry/README.md#icr-execute-in-dind){: external}, or [icr-execute-in-dind-cluster](https://github.com/open-toolchain/tekton-catalog/blob/master/container-registry/README.md#icr-execute-in-dind-cluster){: external} Tekton tasks to build container images. For more information about this replacement, see the [{{site.data.keyword.registrylong}} is Deprecating Container Builds](https://www.ibm.com/cloud/blog/announcements/ibm-cloud-container-registry-deprecating-container-builds){: external} blog post.
{: deprecated}
