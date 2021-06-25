---

copyright:
  years: 2021
lastupdated: "2021-06-25"

keywords: DevSecOps

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:table: .aria-labeledby="caption"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Building Docker images
{: #cd-devsecops-build-docker}

You can build all of the Docker images in the `containerize` stage that you need. If you wish that the default built-in CISO sign and VA scan process those images, you need to let the pipeline be aware of these images.
{: shortdesc}

## Adding image artifacts
{: #cd-devsecops-image-artifacts}

You can add image artifacts by using the `pipelinectl` interface. In the containerize stage, add the images as artifacts to the pipeline:

```
save_artifact <image-alias> type=image "name=${IMAGE}" "digest=${DIGEST}" [<prop>=<value>]
```

Where the value of name must be a fully qualified image name, for example: `your-docker-repository.artifactory.swg-devops.com/your-image-name:your-image-tag` and `digest` must be the `sha256` digest of the image, for example,  `sha256:c43e802dcc7485590b54614006ced9338d5bd9a045115c89d5570bb95eeb52d9`.

`<image-alias>` can be any string, its purpose to provide a human-readable name for your image among the other artifacts. You can add any properties to the artifact, like tags, timestamp, etc.

The **type**, **name**, and **digest** fields  are required!
{: important}

### Example
{: #cd-devsecops-artifacts-example}

```
save_artifact service type=image \
  name="${SERVICE_IMAGE}" \
  digest="${SERVICE_IMAGE_DIGEST}" \
  tags="${SERVICE_IMAGE_TAGS}"

save_artifact service_debug type=image \
  "name=${SERVICE_DEBUG_IMAGE}" \
  "digest=${SERVICE_DEBUG_IMAGE_DIGEST}"
```
{: screen}

By using this interface, the default built-in CISO sign and VA scan tasks will be able to pick up these images and process them.

## Loading image artifacts
{: #cd-devsecops-load-artifacts}

At the end of the pipeline in the release stage, you can access these artifacts using the pipelinectl interface:

```
list_artifacts
load_artifact <image-alias> <property>
```
{: screen}

`list_artifacts` lists the image aliases available. <property> is any property you or the pipeline added previously. Using these together you can iterate over your artifacts, for example:

```
list_artifacts | while IFS= read -r artifact; do

  $image=$(load_artifact "$artifact" name)
  $digest=$(load_artifact "$artifact" digest)
  $signature=$(load_artifact "$artifact" signature)

  # update your inventory using these 

done
```
{: screen}

The `signature` property is added by the default built-in CISO signing task.
{: tip}

<staging>

For more information, check out the following documentation:

* [Documentation on stages for user-defined scripts](https://pages.github.ibm.com/one-pipeline/docs/#/custom-scripts)
* [API documentation for pipelinectl](https://github.ibm.com/one-pipeline/compliance-baseimage/tree/master/pipelinectl)
* [The default built-in CISO sign script](https://github.ibm.com/one-pipeline/compliance-baseimage/blob/master/one-pipeline/internal/ciso/sign_icr)
* [The default built-in VA scan checker script](https://github.ibm.com/one-pipeline/compliance-baseimage/blob/master/one-pipeline/internal/container-registry/va_scan)

</staging>

