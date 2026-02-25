---

copyright:
  years: 2020, 2026
lastupdated: "2026-02-25"

keywords: Delivery Pipeline, container image

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Building container images
{: #pipeline_container_images}

{{site.data.keyword.contdelivery_short}} will be discontinued in the following regions on 12 February 2027: **au-syd**, **ca-mon**, **ca-tor**, **eu-es**, **jp-osa**, **us-east**. Code Risk Analyzer and {{site.data.keyword.DRA_short}} will also be deprecated in all regions on that date. However, if a region has no active usage of these features, the features in that region may be discontinued earlier and stop accepting new instances. [Learn more](/docs/ContinuousDelivery?topic=ContinuousDelivery-faq_region_feature_consolidation)
{: important}

You can use either Classic pipelines or Tekton pipelines to build container images.
{: shortdesc}

## Classic pipelines
{: #pipeline_classic_images}

You can use Classic pipelines to build container images by using the Container Registry job type. This job type provides context to access the {{site.data.keyword.registrylong}}, and uses the [Buildkit](https://github.com/moby/buildkit){: external} command from the job's [build script](https://github.com/open-toolchain/commons/blob/master/scripts/build_image_buildkit.sh). Several of the toolchain templates use this script to build container images.

The [`cr build`](/docs/Registry?topic=Registry-containerregcli) command is deprecated. To migrate your existing build container image job from the `cr build` command to the [Buildkit](https://github.com/moby/buildkit){: external} command, edit your stage properties and select your build container image job. Replace the line that sources `build_image.sh` with `source <(curl -sSL "https://raw.githubusercontent.com/open-toolchain/commons/master/scripts/build_image_buildkit.sh")`. When you switch to use this script, you must provide a new `IBM_CLOUD_API_KEY` secret environment variable for the corresponding stage. This API key must have access to the namespace in which the image is built. If the `IBM_CLOUD_API_KEY` secret environment variable is not provided, 401 errors appear in the logs.
{: deprecated}

## Tekton pipelines
{: #pipeline_tekton_images}

The {{site.data.keyword.contdelivery_short}} service includes several Tekton tasks that you can reference within your pipelines to build container images. These tasks are stored in the [Open Toolchain Tekton Catalog](https://github.com/open-toolchain/tekton-catalog/tree/master/container-registry){: external}:

* [icr-containerize](https://github.com/open-toolchain/tekton-catalog/blob/master/container-registry/README.md#icr-containerize){: external}: Builds and pushes an image to the [{{site.data.keyword.registrylong}}](/docs/Registry?topic=Registry-getting-started). This task depends on [Buildkit](https://github.com/moby/buildkit){: external} to build the container image.

* [icr-execute-in-dind](https://github.com/open-toolchain/tekton-catalog/blob/master/container-registry/README.md#icr-execute-in-dind){: external}: Runs Docker commands such as build and inspect, against a Docker engine that is running as a sidecar container. Then, it pushes the resulting image to the {{site.data.keyword.registrylong}}.

* [icr-execute-in-dind-cluster](https://github.com/open-toolchain/tekton-catalog/blob/master/container-registry/README.md#icr-execute-in-dind-cluster){: external}: Runs Docker commands such as build and inspect, against a Docker engine that is running in a Kubernetes cluster. If a Docker DinD isn't available on the build cluster, a new one is deployed. Then, it pushes the resulting image to the {{site.data.keyword.registrylong}}.


The [`cr build`](/docs/Registry?topic=Registry-containerregcli) command is deprecated. If you use this command, or reference it from the [icr-cr-build](https://github.com/open-toolchain/tekton-catalog/blob/master/container-registry/README.md#icr-cr-build){: external} task, you can migrate to the [icr-containerize](https://github.com/open-toolchain/tekton-catalog/blob/master/container-registry/README.md#icr-containerize
){: external}, [icr-execute-in-dind](https://github.com/open-toolchain/tekton-catalog/blob/master/container-registry/README.md#icr-execute-in-dind){: external}, or [icr-execute-in-dind-cluster](https://github.com/open-toolchain/tekton-catalog/blob/master/container-registry/README.md#icr-execute-in-dind-cluster){: external} Tekton tasks to build container images.
{: deprecated}
