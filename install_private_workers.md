---

copyright:
  years: 2019, 2022
lastupdated: "2022-12-09"

keywords: Delivery Pipeline Private Workers, Installation, Kubernetes cluster, private worker

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}


# Installing {{site.data.keyword.deliverypipeline}} Private Workers
{: #install-private-workers}

Install and register a {{site.data.keyword.deliverypipeline}} Private Worker so that {{site.data.keyword.contdelivery_full}} Development teams can use the private worker in their toolchain configuration. Developers can run workloads within the network scope of the private worker installation without any inbound network connectivity. 
{: shortdesc}

The {{site.data.keyword.deliverypipeline}} uses public and private workers to run pipeline jobs. By default, pipeline jobs are run by using public workers on IBM-managed public shared infrastructure. Pipeline jobs can access resources only on the public network (both within and outside of IBM) and are limited to 60 minutes run time per job.

In certain scenarios, your {{site.data.keyword.deliverypipeline}} might require access to internal or on-premises resources. In these situations, you can connect to and integrate a {{site.data.keyword.deliverypipeline}} Private Worker to run on your own Kubernetes infrastructure.

The private worker agents that are installed on private clusters request data only from the IBM-hosted private worker service. The data flow is one way and originates only from the agent.

## Prerequisites
{: #pw_install_prereqs}

Before you install a private worker, make sure that you have an {{site.data.keyword.cloud}} account to create authentication keys. You need the latest kubectl version that is installed on the Administrator's desktop computer. And you must also have a [Kubernetes cluster](https://cloud.ibm.com/kubernetes/clusters){: external} (version 1.15 or higher) with Administrative access to install a private worker.

* Suggested Kubernetes cluster configurations:

   * {{site.data.keyword.containerlong_notm}} version 1.21 or higher to run workloads in isolation on {{site.data.keyword.cloud_notm}} Public.
   * {{site.data.keyword.openshiftlong}} version 4.9 or later.
  
* Network access:

   * Inbound: Not required.
   * Outbound network access uses `(TCP:443)` where the region matches the delivery pipeline location and is either au-syd (Sydney, Australia), eu-de (Frankfurt, Germany), eu-gb (London, United Kingdom), jp-tok (Tokyo, Japan), jp-osa (Osaka, Japan), us-south (Dallas, US), us-east (Washington DC, US), br-sao (Sao Paulo), or ca-tor (Toronto, CA). For example, for the Frankfurt region specify `https://private-worker-service.eu-de.devops.cloud.ibm.com (TCP:443)`. For network access to the global endpoint for API key validation, use `https://iam.cloud.ibm.com (TCP:443)`. 
  
* Permissions to pull images from icr.io. Private workers require the tekton-pipelines infrastructure and must be able to pull tekton-releases images from icr.io to complete the private worker installation.

   To pull images from the `icr.io` container registry, you might need to [define a specific Kubernetes ClusterImagePolicy](/docs/ContinuousDelivery?topic=ContinuousDelivery-faq_pipeline_private_workers&interface=ui#pipeline_private_worker_image_policy).
   {: tip}
   
* Optional. If you want to install the private worker by using the Operator Lifecycle Manager (OLM), the OLM operator framework must be [installed on your cluster](https://operator-framework.github.io/olm-book/docs/install-olm.html){: external}. This framework is preinstalled by default on all {{site.data.keyword.openshiftlong}} clusters. 

   A previous version of the {{site.data.keyword.containerlong_notm}} was provided on clusters that were created before v1.23. To use OLM on an {{site.data.keyword.containerlong_notm}} cluster, you must first update the cluster to v1.23. Next, you must upgrade to a current version of OLM by uninstalling the previous version of OLM and reinstalling OLM.

   To uninstall the previous OLM framework from an {{site.data.keyword.containerlong_notm}} cluster, run the following commands:

   ```text
   kubectl delete deployment -n ibm-system catalog-operator
   kubectl delete deployment -n ibm-system olm-operator
   kubectl delete crd operatorgroups.operators.coreos.com
   kubectl delete crd operators.operators.coreos.com
   kubectl delete crd subscriptions.operators.coreos.com
   kubectl delete crd catalogsources.operators.coreos.com
   kubectl delete crd clusterserviceversions.operators.coreos.com
   kubectl delete crd installplans.operators.coreos.com
   kubectl delete sa -n ibm-system olm-operator-serviceaccount 
   kubectl delete clusterrole system:controller:operator-lifecycle-manager
   kubectl delete clusterrolebinding olm-operator-binding-ibm-system 
   kubectl delete clusterrole aggregate-olm-edit                                                     
   kubectl delete clusterrole aggregate-olm-view
   ```

   For instructions about how to install the new OLM framework, see [How do I install OLM?](https://operator-framework.github.io/olm-book/docs/install-olm.html){: external}.

Because private workers are not compatible with {{site.data.keyword.redhat_openshift_notm}} Pipelines, it is recommended that you do not install them on a cluster with {{site.data.keyword.redhat_openshift_notm}} pipelines.
{: important}  

## Installing a {{site.data.keyword.deliverypipeline}} Private Worker
{: #install_pw}  

To install a private worker, you must have Administrator level access to a cluster. Private worker installation can be completed only by way of the command line since no graphical user interface is available.
{: important}

### Installing the {{site.data.keyword.deliverypipeline}} Private Worker by using the CLI
{: #install_pw_cli}
{: cli}

The following steps are intended for Administrators who are preparing environments and private workers for multiple people or teams. To install private workers for your own use, see [Setting up a Delivery Pipeline Private Worker](/docs/ContinuousDelivery?topic=ContinuousDelivery-private-workers#set_up_private_worker).
{: tip}

You can install the private worker framework directly on either an {{site.data.keyword.cloud_notm}} Kubernetes cluster or a {{site.data.keyword.openshiftlong}} cluster, or you can install the framework by using the [Operator Lifecycle Manager (OLM)](https://docs.openshift.com/container-platform/4.9/operators/understanding/olm/olm-understanding-olm.html){: external}.

#### Installing directly on a cluster
{: #direct_install_pw_cli}
{: cli}

To install the framework directly on a cluster, you must have admin access to the cluster. From the {{site.data.keyword.cloud_notm}} CLI, type the following command:

   ```text
   kubectl apply --filename "https://private-worker-service.{REGION}.devops.cloud.ibm.com/install"
   ```
   
   Where `{REGION}` is the location of the toolchain's pipeline. You can specify any of the following values for the `{REGION}`:
   
   - `au-syd` (Sydney, Australia)
   - `eu-de` (Frankfurt, Germany)
   - `eu-gb` (London, United Kingdom)
   - `jp-tok` (Tokyo, Japan)
   - `jp-osa` (Osaka, Japan)
   - `us-south` (Dallas, US)
   - `us-east` (Washington DC, US)
   - `ca-tor` (Toronto, CA)
   - `br-sao` (Sao Paulo, Brazil)

#### Installing by using the OLM
{: #olm_install_pw_cli}
{: cli}

The OLM handles the installation and sets the framework for automatic updates. This method ensures that your private worker is always up to date with the latest release. You can use the OLM on both {{site.data.keyword.openshiftlong}} and {{site.data.keyword.cloud_notm}} Kubernetes clusters. For more information about how to install the OLM framework, see [How do I install OLM?](https://operator-framework.github.io/olm-book/docs/install-olm.html){: external}.

Type the following command to install the framework for automatic updates on a {{site.data.keyword.openshiftlong}} cluster:

   ```text
   kubectl apply --filename "https://private-worker-service.{REGION}.devops.cloud.ibm.com/install?type=openshift&olm=true"
   ```
    
   Where `{REGION}` is the location of the toolchain's pipeline. You can specify any of the following values for the `{REGION}`:
   
   - `au-syd` (Sydney, Australia)
   - `eu-de` (Frankfurt, Germany)
   - `eu-gb` (London, United Kingdom)
   - `jp-tok` (Tokyo, Japan)
   - `jp-osa` (Osaka, Japan)
   - `us-south` (Dallas, US)
   - `us-east` (Washington DC, US)
   - `ca-tor` (Toronto, CA)
   - `br-sao` (Sao Paulo, Brazil)

   The following code snippet shows an example of a private worker OLM installation in the Dallas region on {{site.data.keyword.openshiftlong}}:
   
   ```text
   $ kubectl apply --filename "https://private-worker-service.us-south.devops.cloud.ibm.com/install?type=openshift&olm=true"
   catalogsource.operators.coreos.com/private-worker-agent created
   subscription.operators.coreos.com/private-agent-subscription created
   ```
    
Type the following command to install the framework for automatic updates on an {{site.data.keyword.cloud_notm}} Kubernetes cluster:
  
   ```text
   kubectl apply --filename "https://private-worker-service.{REGION}.devops.cloud.ibm.com/install?type=iks&olm=true"
   ```
 
   Where `{REGION}` is the location of the toolchain's pipeline. You can specify any of the following values for the `{REGION}`:
   
   - `au-syd` (Sydney, Australia)
   - `eu-de` (Frankfurt, Germany)
   - `eu-gb` (London, United Kingdom)
   - `jp-tok` (Tokyo, Japan)
   - `jp-osa` (Osaka, Japan)
   - `us-south` (Dallas, US)
   - `us-east` (Washington DC, US)
   - `ca-tor` (Toronto, CA)
   - `br-sao` (Sao Paulo, Brazil)

   The following code snippet shows an example of a private worker OLM installation in the Dallas region on {{site.data.keyword.cloud_notm}} Kubernetes:
   
   ```text
   $ kubectl apply --filename "https://private-worker-service.us-south.devops.cloud.ibm.com/install?type=iks&olm=true"
   catalogsource.operators.coreos.com/private-worker-agent created
   catalogsource.operators.coreos.com/tekton-framework created
   operatorgroup.operators.coreos.com/agent-operator-group created
   subscription.operators.coreos.com/private-agent-subscription created
   ```

To set up a pool of private workers, repeat this process with more Kubernetes clusters.
{: tip}
  
## Registering a {{site.data.keyword.deliverypipeline}} Private Worker
{: #register_pw}

### Creating a service ID
{: #pw_create_service_id}

A service ID represents a pool of one or more private workers that act together. You can initially register one private worker installation, and then incrementally register more private workers into the same group by reusing the same service ID. Registering multiple private workers in the same group supports higher availability and horizontal scaling of your private worker capacity. For more information about service IDs, see [Creating and working with service IDs](/docs/account?topic=account-serviceids).

#### Creating a service ID in the console
{: #console_create_service_id}
{: ui}

1. Log in to [{{site.data.keyword.cloud_notm}}](http://cloud.ibm.com){: external}.
2. Go to [https://cloud.ibm.com/iam/serviceids](https://cloud.ibm.com/iam/serviceids){: external}.
3. Click **Create**.
4. Enter a name and description for the service ID. If you are creating a service ID for a pool of private workers, specify the name of the private workers pool, for example: **Pipeline Private Workers for Acme**.
5. Click **Create**. 
6. Save your service ID for later use. The service ID is required on the Kubernetes cluster that is targeted for the {{site.data.keyword.deliverypipeline}} Private Worker installation.

#### Creating a service ID by using the CLI
{: #cli_create_service_id}
{: cli}

From the {{site.data.keyword.cloud_notm}} CLI, type the following command:

```text
$ ibmcloud iam service-id-create {worker-pool-name} -d "{worker-pool-description}"

Creating service ID {worker-pool-name} bound to current account as username@domain.com...OK
Service ID {worker-pool-name} is created successfully

Name           {worker-pool-name}
Description    {worker-pool-description}
CRN            crn:v1:bluemix:public:iam-identity::a/8d63fb1cc5e99e86dd7229dddff75fef::serviceid:ServiceId-38ffff31-3ea3-4ecc-9732-190f7a993097
Bound To       crn:v1:bluemix:public:::a/8d63fb1cc5e99e86dd7229dddff75fef:::
Version        1-6df15bde97b6e87f583a557f8731888f
Locked         false
UUID         ServiceId-38ffff31-3ea3-4ecc-9732-190f7a993097

```

### Creating an API key
{: #pw_create_api_key}

An API key is a unique code that is passed to an API to identify the application or user that is calling it. To prevent malicious use of an API, you can use API keys to track and control how that API is used. For more information about API keys, see [Understanding API keys](/docs/account?topic=account-manapikey).

#### Creating an API key in the console
{: #console_create_key}
{: ui}

1. Log in to [{{site.data.keyword.cloud_notm}}](http://cloud.ibm.com){: external}.
2. Go to [https://cloud.ibm.com/iam/serviceids](https://cloud.ibm.com/iam/serviceids){: external}.
3. Select the Service ID that you want to create an API for.
4. In the **API keys** tab, click **Create**.
5. Enter a name and description for the API key to specify the private worker installation, such as **Pipeline Private Worker in IBM Cloud Private**.
6. Click **Create**.
7. Copy or download your API key. You cannot retrieve your API key again after you create it.

#### Creating an API key by using the CLI
{: #cli_create_key}
{: cli}

From the {{site.data.keyword.cloud_notm}} CLI, type the following command:

```text
$ ibmcloud iam service-api-key-create {worker-api-key-name} (SERVICE\_ID\_NAME|SERVICE\_ID\_UUID) \[-d, --description DESCRIPTION\] \[--file OUT_FILE\]

Creating API key  {worker-api-key-name} of service
SERVICE\_ID\_NAME as username@domain.com...
OK
Service API key {worker-api-key-name} is created
Successfully saved API key information to FILE
Please preserve the API key! It cannot be retrieved after it's created.

Name           {worker-api-key-name}
Description    Description
Bound To       crn:v1:bluemix:public:iam-identity::a/2cac145ae78048679b129009cfe8c7f9::serviceid:ServiceId-9a6a14e5-5811-4c2c-9131-0e1d4bb7dfe1
Created At     2019-07-04T10:51+0000
API Key        doJX9kORc4q5PRkH19H3lePDwYRAKNWk4XlIuEBrriOD
Locked         false
UUID           ApiKey-c1ee0fb5-90f2-476e-a260-a796e6d7f5f7

```

### Registering the private worker with {{site.data.keyword.cloud_notm}}
{: #pw_register_cloud}

Before you can register the private worker with {{site.data.keyword.cloud_notm}}, you must [deploy the private worker framework](/docs/ContinuousDelivery?topic=ContinuousDelivery-install-private-workers&interface=cli#install_pw). To use the registration commands, you must be logged in to the Kubernetes cluster (with kubectl) into which you previously installed a private worker.
{: tip}

You must register a private worker with the specific {{site.data.keyword.cloud_notm}} region that corresponds to the location of the delivery pipelines that you want to enable.

1. Specify a meaningful name for your private worker. This name must start and end with lowercase alphanumeric characters and can also contain `_` or `.` characters.
2. Run the following command with the service ID and API key that you created previously, the private worker name, and the `{REGION}` which is the location of the toolchain's pipeline.

   ```text
   $ kubectl apply --filename "https://private-worker-service.{REGION}.devops.cloud.ibm.com/install/worker?serviceId={SERVICE_ID}&apikey={API_KEY}&name={WORKER_NAME}"

   workeragent.devops.cloud.ibm.com/worker-name created
   secret/worker-name-auth created
   ```

   You can specify any of the following values for the `{REGION}`:

      * au-syd (Sydney, Australia)
      * eu-de (Frankfurt, Germany)
      * eu-gb  (London, United Kingdom)
      * jp-tok (Tokyo, Japan)
      * jp-osa (Osaka, Japan)
      * us-south (Dallas, US)
      * us-east (Washington DC, US)
      * ca-tor (Toronto, CA)
      * br-sao (Sao Paulo, Brazil)
   {: tip}

3. To verify that the agent is registered correctly, type the following command:

   ```text
   $ kubectl get workeragents
   NAME           SERVICEID     AGENT   REGISTERED   VERSION   AUTH   CONSTRAINED   PAUSED
   <worker_name>  <ServiceId>   OK      Succeeded    OK        OK     false         false
   ```

## Configuring the {{site.data.keyword.deliverypipeline}} Private Worker to use private endpoints
{: #install_pw_agent_pse}

By default, private workers use public endpoints for communication. A cluster administrator can update the private worker configuration to use private endpoints so that communication between the private worker and the {{site.data.keyword.contdelivery_full}} service does not use the public internet.

1. Get the name of the agent that is installed on the cluster:

   ```text
   kubectl get workeragents
   ```

2. Change the `apiUrl` for that agent:

   ```text
   kubectl patch workeragent {WORKER_NAME} --type='merge' -p '{"spec": {"apiUrl":"https://private-worker-service.private.{REGION}.devops.cloud.ibm.com"}}'
   ```

   Where `{REGION}` is the location of the toolchain's pipeline. Private endpoints are available in the following regions:

    * `us-south (Dallas, US)`
    * `us-east (Washington, US)`
    * `eu-de (Frankfurt, DE)`

   You must have a [VRF enabled](/docs/account?topic=account-vrf-service-endpoint&interface=ui) {{site.data.keyword.cloud_notm}} account to use this feature.
   {: important}

3. Optional. To return to using public endpoints for the agent,  type the following command:

   ```text
   kubectl patch workeragent {WORKER_NAME} --type='merge' -p '{"spec": {"apiUrl":"https://private-worker-service.{REGION}.devops.cloud.ibm.com"}}'
   ```

## Configuring the Delivery Pipeline Private Worker to use Satellite link endpoints
{: #install_pw_agent_satellite}

By default, private workers use public endpoints for communication. A cluster administrator can update the private worker configuration to use Satellite link endpoints so that communication between the private worker and the {{site.data.keyword.contdelivery_short}} service goes through Satellite link endpoints.

1. [Create a cloud Satellite link endpoint](/docs/satellite?topic=satellite-link-cloud-create) for the {{site.data.keyword.contdelivery_full}} service and set `FQDN` and `Service indication name` to use the following value:

   ```text
   private-worker-service.{REGION}.devops.cloud.ibm.com
   ```
    
   Where `{REGION}` is the location of the toolchain's pipeline.
   
2. Create a configmap in the private worker namespace that maps the public endpoints to the Satellite link endpoints:

   ```text
   apiVersion: v1
   kind: ConfigMap
   metadata:
      name: pipelineworker-url-map
   data:
      iam.cloud.ibm.com: <default IAM satellite link endpoint for your satellite location>
      private-worker-service.{REGION}.devops.cloud.ibm.com: <satellite link endpoint created in step 1)>
   ```
     
   You can add endpoints to the configmap, such as these [default Satellite link endpoints](/docs/satellite?topic=satellite-default-link-endpoints).
   {: tip}
     
## Updating the {{site.data.keyword.deliverypipeline}} Private Worker installation
{: #install_pw_update} 

If the private worker is reported as inactive, you must update the installation.

To view the version of your private worker, type one of the following commands:

* {{site.data.keyword.containerlong_notm}}: `kubectl -n tekton-pipelines describe deploy private-worker-agent | grep Image`
* {{site.data.keyword.openshiftlong}}: `kubectl -n openshift-operators describe deploy private-worker-agent-controller-manager | grep Image`

To update your private worker installation, complete the following steps:

1. Run the [installation command](#install_pw) again.
2. [Register the private worker](#register_pw) on your Kubernetes cluster again.

You can reuse the `apikey` that you used for the existing private worker.
{: tip}

For more information about {{site.data.keyword.deliverypipeline}} Private Workers, see [Troubleshooting for {{site.data.keyword.deliverypipeline}} Private Workers](/docs/ContinuousDelivery?topic=ContinuousDelivery-troubleshoot-pipeline-private-workers#troubleshoot-pw-images) and [FAQs for Pipeline Private Workers](/docs/ContinuousDelivery?topic=ContinuousDelivery-faq_pipeline_private_workers&interface=ui).
{: tip} 
