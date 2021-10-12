---

copyright:
  years: 2021
lastupdated: "2021-04-01"

keywords: IBM Cloud, monitoring, supertenant

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
{:download: .download}

# Monitoring metrics for {{site.data.keyword.contdelivery_short}}
{: #cd-monitor-sysdig}

{{site.data.keyword.mon_full}} is a third-party cloud-native, and container-intelligence management system that you can include as part of your {{site.data.keyword.cloud_notm}} architecture. Use it to gain operational visibility into the performance and health of your applications, services, and platforms. It offers administrators, DevOps teams and developers full stack telemetry with advanced features to monitor and troubleshoot, define alerts, and design custom dashboards.
{: shortdesc}


## Platform metrics overview
{: #cd_platform_metrics}

You can configure one instance only of the {{site.data.keyword.mon_full_notm}} service per region to collect platform metrics. 
* To configure the Monitoring instance, you must set the platform metrics configuration. 
* If a Monitoring instance in a region is already enabled to collect platform metrics, metrics from enabled-monitoring services are collected automatically and available for monitoring through this instance. For more information about enabled-monitoring services, see [Cloud services]().
* After a Monitoring instance in an account and region is enabled to collect platform metrics, it automatically collects metrics from all {{site.data.keyword.contdelivery_short}} service instances in the same account and region. You do not need to opt in to the {{site.data.keyword.contdelivery_short}} service metrics collection. You also cannot opt out of the {{site.data.keyword.contdelivery_short}} service metrics collection.

To monitor platform metrics, check that the {{site.data.keyword.mon_full_notm}} instance is provisioned in the same region where the {{site.data.keyword.contdelivery_short}} instance is provisioned.
{: important}

## Enabling platform metrics from the {{site.data.keyword.contdelivery_short}} dashboard
{: #cd_enable_platform_metrics}

Complete the following steps to configure platform metrics:

1. Log in to {{site.data.keyword.cloud_notm}}. 
    
1. Click **View resources**.

1. In the **Services** section, click the {{site.data.keyword.contdelivery_short}} instance that you plan to monitor. 

1. From the **Manage** page, click the overflow menu ![overflow menu](../../icons/actions-icon-vertical.svg "Overflow menu"). Then, select **Add monitoring** to configure *platform metrics* in the region of your {{site.data.keyword.contdelivery_short}} instance.

    If the menu choices include the **Monitoring** option, then the account and region that contain the {{site.data.keyword.contdelivery_short}} instance is already configured for platform metrics. 
    {: tip}
    
5. Provision an instance of the {{site.data.keyword.mon_full_notm}} service.

After you provision the Monitoring instance, the **Observability** page opens. To continue working with {{site.data.keyword.contdelivery_short}}, go back to the {{site.data.keyword.contdelivery_short}} UI.


## Viewing metrics
{: #cd_view_metrics}

To monitor {{site.data.keyword.contdelivery_short}} metrics, you must launch the Monitoring web UI instance that is enabled for platform metrics in the region where your {{site.data.keyword.contdelivery_short}} instance is available.
{: important}

There are different options to launch the Monitoring web UI and monitor metrics:

### Launching the Monitoring web UI from the {{site.data.keyword.contdelivery_short}} dashboard
{: #cd_view_metrics_opt1}

Complete the following steps to launch the Monitoring web UI from the {{site.data.keyword.contdelivery_short}} dashboard:

1. Log in to {{site.data.keyword.cloud_notm}}. 
    
1. Click **View resources**.

1. In the *Services* section, click the {{site.data.keyword.contdelivery_short}} instance that you plan to monitor. 

1. From the **Manage** page, click the overflow menu ![overflow menu](../../icons/actions-icon-vertical.svg "Overflow menu"). Then, select **Monitoring** to view the {{site.data.keyword.contdelivery_short}} dashboard within the context of your {{site.data.keyword.contdelivery_short}} instance.


### Launching the Monitoring web UI from the Observability page
{: #cd_view_metrics_opt2}

Complete the following steps to launch the Monitoring web UI from the **Observability** page:

1. [Launch the Monitoring web UI](/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-launch).
1. Select **DASHBOARDS**.
1. In the **Default Dashboards** section, expand **IBM**.
1. Choose the {{site.data.keyword.contdelivery_short}} dashboard from the list.

To monitor a {{site.data.keyword.contdelivery_short}} instance, change the scope or make a copy of the Default dashboard.
{: tip}


## Monitoring {{site.data.keyword.contdelivery_short}}
{: #cd-monitor-service}

Consider the following tasks when you monitor an instance of the {{site.data.keyword.contdelivery_short}} service:

| Task                                      | Predefined Alert | What to Look For  |
|:-------------------------------------------|:------------------|:-------------------|
| Monitor how long delivery pipeline runs remain queued before they begin executing on a private pipeline worker pool. | {{site.data.keyword.contdelivery_short}} Pipeline queue time | If the queue time repeatedly exceeds more than 10 seconds, the private worker pool might not have enough capacity to handle the pipeline runs being requested of it. You might need to scale up the worker pool, create a new worker pool, or reduce the number of pipeline runs.|
{: caption="Table 1. {{site.data.keyword.contdelivery_short}} moitoring tasks" caption-side="top"}


### Monitor delivery pipeline queue times
{: #cd-task1}

#### Description
{: #cd-task1-pr}

The pipeline queue time tracks the elapsed time in seconds between the {{site.data.keyword.contdelivery_short}} service receiving and queuing a request to run a pipeline, and a private worker pool dequeuing and commencing execution of the pipeline. Ideally, pipeline requests spend only a second or two on the queue before being picked up by the private worker pool. If pipeline requests remain queued for several seconds or minutes, the private worker pool might lack the capacity to handle the incoming pipeline workload. Alerting when pipeline queue times exceed a reasonable threshold, such as 10 seconds, can help draw your attention to a private worker pool that needs to be scaled up.

#### User action
{: #cd-task1-action}

The {{site.data.keyword.contdelivery_short}} dashboard in Monitoring can help to identify trends in pipeline queue time. If the queue times for pipelines serviced by a private worker pool last several seconds or are trending upwards, check the configuration of the private worker pool, including the number and processing capacity of the nodes in the pool. You might lower queue times by scaling up the private worker pool, or by reducing the frequency, variety, or complexity of pipeline jobs and tasks that are dispatched to the private worker pool.


## {{site.data.keyword.contdelivery_short}} predefined dashboards
{: #cd_dashboards_dictionary}

The following table outlines the pre-defined dashboards that you can use to monitor {{site.data.keyword.contdelivery_short}} metrics:

| Dashboard Name            | Description    |
|:---------------------------|:----------------|
| `{{site.data.keyword.contdelivery_short}}` | Default dashboard when you launch the Monitoring web UI from your service instance UI. |
{: caption="Table 2. Pre-defined dashboards" caption-side="top"}


You cannot change the Default dashboard. To customize the dashboard, you can create a copy of it.
{: important}

## Metrics available by service plan
{: #cd_metrics_by_plan}

| Metric Name |Lite|Professional|
|:-----------|:--------|:--------|:--------|
| [Pipeline queue time](#cd_ibm_toolchain_pipeline_queue_time_seconds) | ![Checkmark icon](../../icons/checkmark-icon.svg) | ![Checkmark icon](../../icons/checkmark-icon.svg) |
{: caption="Table 3: Metrics Available by Plan Names" caption-side="top"}


## Predefined alerts
{: #cd_default_alerts}

The following table outlines the pre-defined alerts that are available in Monitoring: 

| Alert Name                                 | Description | 
|:--------------------------------------------|:-------------|
| {{site.data.keyword.contdelivery_short}} high pipeline queue time | Use this alert to monitor the queue time for pipeline requests to let you know if a private worker pool is taking too long to process requests. |
{: caption="Table 4. Pre-defined alerts" caption-side="top"}


## {{site.data.keyword.contdelivery_short}} metrics dictionary
{: #cd_metrics_dictionary}

### Pipeline queue time
{: #cd_ibm_toolchain_pipeline_queue_time_seconds}

The elapsed time in seconds between the {{site.data.keyword.contdelivery_short}} service receiving and queuing a request to run a pipeline, and a private worker pool dequeuing and commencing execution of the pipeline.

| Metadata | Description |
|:----------|:-------------|
| `Metric Name` | `ibm_toolchain_pipeline_queue_time_seconds`|
| `Metric Type` | `gauge` |
| `Value Type`  | `second` |
| `Segment By` | `Service instance, Service instance name, Private worker pool ID` |
{: caption="Table 5: Pipeline queue time metric metadata" caption-side="top"}


## Attributes for segmentation
{: #cd_segmentation_attributes}

### Global attributes
{: #cd-global-attributes}

The following attributes are available for segmenting all of the metrics listed in this topic.

| Attribute | Attribute Name | Attribute Description | Valid Values |
|:-----------|:----------------|:-----------------------|:--------------|
| `Cloud Type` | `ibm_ctype` | Type of Cloud         | Valid values are `public`, `dedicated`, or `local`. |
| `Location` | `ibm_location` | Location of the monitored resource. | You can specify a region, a data center, or `global`. |
| `Resource group` | `ibm_resource_group_name` | Resource group that is associated with the service instance. | Choose a resource group from the ones that are available in your account. |
| `Scope` | `ibm_scope` | The extent of the data samples that are considered.  | You can choose the scope to be the account, an organization, or a space GUID that is associated with this metric. |
| `Service name` | `ibm_service_name` | Name of the service that generates this metric. | `toolchain` | 
{: caption="Table 6. Global segmentation attributes" caption-side="top"}


### Additional attributes
{: #cd_additional_attributes}

The following attributes are available for segmenting one or more global attributes:

Check each individual metric for the supported segmentation options.
{: important}

| Attribute | Attribute Name | Attribute Description |
|:-----------|:----------------|:-----------------------|
| `Private worker pool` | `ibm_toolchain_pipeline_worker_pool` | The unique id of a {{site.data.keyword.contdelivery_short}} pipeline private worker pool. |
{: caption="Table 7. Additional segmentation attributes" caption-side="top"}
