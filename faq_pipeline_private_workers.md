---

copyright:
  years: 2015, 2024
  
lastupdated: "2024-04-16"

keywords: private workers

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# FAQs for Pipeline Private Workers
{: #faq_pipeline_private_workers}

Get answers to frequently asked questions about using Pipeline Private Workers.
{: shortdesc} 

## How do I install a multi-cluster worker pool?
{: #install_mc_worker_pool}
{: faq}
{: support}

You can install agents on multiple clusters that work together within a single private worker pool. By using this configuration, the private worker pool can manage more pipeline runs in parallel, and you can remove clusters from the maintenance rotation without deactivating the worker pool.

Although having multiple agents on the same cluster supports multiple worker pools, it does not improve performance or throughput. 
{: tip}

To configure a multi-cluster worker pool, follow the instructions for [installing directly on a cluster](/docs/ContinuousDelivery?topic=ContinuousDelivery-install-private-workers#install_pw) and [registering a {{site.data.keyword.deliverypipeline}} Private Worker](/docs/ContinuousDelivery?topic=ContinuousDelivery-install-private-workers#register_pw) for each cluster that participates in the worker pool. Make sure that you update the worker name to identify the cluster on which the worker resides.

The multiple worker agents are now listed in the private worker integration UI and jobs are scheduled on those agents based on the cluster load at pipeline run request time.

## How do I view the status of private workers on multiple clusters by using the CLI?
{: #pipeline_private_worker_status}
{: faq}
{: support}

You can use the following command within a script that traverses all of the clusters that private workers are installed on.

```text
kubectl get workeragent -ojson | jq '.items[] | .status.versionStatus.state'
```

Consider upgrading any private workers that return results that are not `OK`.

## Which attributes can I use for private worker agents?
{: #install_pw_agent_states}
{: faq}
{: support}

The following attributes are available for private worker agents:

* **NAME**: The name that was specified when the agent was registered. This name appears on the Private Worker integration page.
* **SERVICEID**: The work queue ID from which this agent processes work requests.
* **AGENT**: A value of `OK` indicates that the agent can process work requests.
* **REGISTERED**: A value of `Succeeded` indicates that the agent successfully registered with the regional private worker service.
* **VERSION**: A value of `OK` indicates whether the version of the agent is current.
* **AUTH**: A value of `OK` indicates whether the agent `apikey` is valid.
* **CONSTRAINED**: A value of `false` indicates that enough cluster resources are available for the agent to run tasks. A value of `True` specifies that the cluster is `resource-constrained`.
* **PAUSED**: A value of `false` indicates that the agent is operational and can run tasks. A value of `true` specifies that the agent is paused and cannot run any tasks. One reason that an agent might be paused is for cluster maintenance.

## How do I set my `ClusterImagePolicy` so that I can access Tekton images?
{: #pipeline_private_worker_image_policy}
{: faq}
{: support}

Because {{site.data.keyword.deliverypipeline}} private workers depend on the Tekton and tekton-pipelines infrastructure, they must pull `tekton-releases` images from `icr.io` (`icr.io/continuous-delivery/pipeline/`). You might need to define a specific Kubernetes `ClusterImagePolicy` to pull images from these container registries. To add the `ClusterImagePolicy` type to your Kubernetes cluster, you must install several [Helm charts](/docs/Registry?topic=Registry-registry_helm_charts).

## How do I self-host container images for {{site.data.keyword.deliverypipeline}} Private Worker?
{: #self_host_pw_}
{: faq}
{: support}

Security constraints might prevent you from pulling images from the `icr.io/continuous-delivery/pipeline` container registry. In such scenarios, complete the following steps:

1. Provision the container images on a supported container registry.
2. Install the `deployment.yaml` file to reference the container images in this container registry. 
3. For each container image that is referenced in the regular deployment yaml file, complete the following steps:

   * Docker pull the image to a local Dockerfile.
   * Docker tag the image with the new reference on the supported container registry.
   * Docker push this new image.
 
   You can obtain the deployment yaml file from `https://private-worker-service.$region.devops.cloud.ibm.com/install`.
   {: tip}

4. Replace the reference to each image in the installation file with the tag for the new image.
5. Run the following command to install the private worker by using the specific container registry: `kubectl apply –filename updated_deployment.yaml`.
6. Continue the [installation](/docs/ContinuousDelivery?topic=ContinuousDelivery-install-private-workers&interface=ui).

## How do I provision and update the private worker installation file for {{site.data.keyword.cloud}} Private?
{: #provision_pw_install}
{: faq}
{: support}

If your pipeline worker is installed on {{site.data.keyword.cloud_notm}} Private, you can use the following script to provision and update the private worker installation file.

```bash
\#\!/bin/bash
region=${region:-"us-south"}
target_cr="mycluster.icp:8500"
install_filename="updated-private-worker-install.yaml"
curl -o $install_filename
https://private-worker-service.$region.devops.cloud.ibm.com/install
cat $install_filename | grep -e
'gcr.io/tekton-releases/github.com/tektoncd/pipeline/cmd' -e 'image:' \\
| sed 's/- gcr.io/gcr.io/g' \\
| sed 's/- image: gcr.io/gcr.io/g' \\
| sed 's/image: gcr.io/gcr.io/g' \\
| sed 's/image://g' \\
| awk '{$1=$1;print}' \\
| while read -r image ; do

echo "Processing $image"
docker pull $image
new_image_tag=$image
# if $image only have a single slash it is coming from dockerhub
number_of_slashes=$(echo $image | tr -cd '/' | wc -c)
if [ "$number_of_slashes" == "1" ]; then
new_image_tag="$target_cr/$image"
fi

# replace the sha id reference in the tag if any
new_image_tag="${new_image_tag@sha256}"
# replace gcr.io to the target cr domain
new_image_tag="${new_image_tag/gcr.io/$target_cr}"
docker tag $image $new_image_tag
docker push $new_image_tag
# replace the image reference in the installation.yaml file
sed -i "s~$image~$new_image_tag~g" $install_filename
done

echo "*****"
echo "Provisioning of docker images to $target_cr done."
echo "Update of the install file $install_filename done"
echo "Change the scope of the images to global before"
echo "running 'kubectl apply --filename $install_filename'
echo "to install the delivery pipeline private worker"
```
{: codeblock}

This script contains the following requirements:

* The `ibmcom` and `tekton-releases` namespaces currently exist on the target {{site.data.keyword.cloud}} Private.
* The Docker client is connected to the {{site.data.keyword.cloud}} Private’s private container registry. For more information about authentication for the Docker CLI, see [Configuring authentication for the Docker CLI](https://www.ibm.com/docs/en/cloud-private/3.2.x?topic=images-configuring-authentication-docker-cli){: external}.   

After you provision the container images on the {{site.data.keyword.cloud}} Private’s private registry, update the image's scope to global to make sure that the images can be accessed from any namespaces. For more information about updating the scope of an image, see [Changing image scope](https://www.ibm.com/docs/en/cloud-private/3.2.x?topic=images-changing-image-scope){: external}.

You can provide pipeline users with access to the base images (`icr.io/continuous-delivery/pipeline/pipeline-base-image`) that are used to run pipeline jobs, which are supplied by the global {{site.data.keyword.registrylong_notm}}. To use these images, you must configure your pipeline jobs by using the `Custom Dockerimage`. You must also reference the expected image in the {{site.data.keyword.cloud}} Private’s private registry, for example: `mycluster.icp:8500/icr.io/continuous-delivery/pipeline/pipeline-base-image:latest`.
{: tip}

## Can I manage private workers by using Terraform or APIs?
{: #pw_terraform_api}
{: faq}
{: support}

You can use Terraform or APIs to add, update, or remove {{site.data.keyword.deliverypipeline}} private worker tool integrations in a toolchain. For more information about working with the {{site.data.keyword.deliverypipeline}} private worker tool integration, see [Working with tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations) and [Configuring {{site.data.keyword.deliverypipeline}} Private Worker](/docs/ContinuousDelivery?topic=ContinuousDelivery-privateworker).

You cannot use Terraform or APIs to manage {{site.data.keyword.deliverypipeline}} private workers. Instead, use the console or the CLI to install, register, configure, and update private workers. For more information about these tasks, see [Installing {{site.data.keyword.deliverypipeline}} Private Workers](/docs/ContinuousDelivery?topic=ContinuousDelivery-install-private-workers). 

