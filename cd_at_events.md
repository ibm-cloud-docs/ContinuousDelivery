---

copyright:
  years: 2018, 2025
lastupdated: "2025-04-10"

keywords: event, security, IBM, Continuous Delivery, toolchain

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Activity tracking events for {{site.data.keyword.contdelivery_short}}
{: #at_events}

{{site.data.keyword.cloud}} services, such as {{site.data.keyword.contdelivery_short}}, generate activity tracking events.
{: shortdesc}

Activity tracking events report on activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use the events to investigate abnormal activity and critical actions and to comply with regulatory audit requirements.

You can use {{site.data.keyword.atracker_full_notm}}, a platform service, to route auditing events in your account to destinations of your choice by configuring targets and routes that define where activity tracking events are sent. For more information, see [About {{site.data.keyword.atracker_full_notm}}](/docs/atracker?topic=atracker-about).

You can use {{site.data.keyword.logs_full_notm}} to visualize and alert on events that are generated in your account and routed by {{site.data.keyword.atracker_full_notm}} to an {{site.data.keyword.logs_full_notm}} instance.

As of 28 March 2024, the {{site.data.keyword.at_full_notm}} service is deprecated and will no longer be supported as of 30 March 2025. Customers will need to migrate to {{site.data.keyword.logs_full_notm}} before 30 March 2025. During the migration period, customers can use {{site.data.keyword.at_full_notm}} along with {{site.data.keyword.logs_full_notm}}. Activity tracking events are the same for both services. For information about migrating from {{site.data.keyword.at_full_notm}} to {{site.data.keyword.logs_full_notm}} and running the services in parallel, see [migration planning](/docs/cloud-logs?topic=cloud-logs-migration-intro).


## Locations where activity tracking events are generated
{: #at-locations}

{{site.data.keyword.contdelivery_short}} sends activity tracking events from the regions that are indicated in the following table.

| Dallas (`us-south`) | Washington (`us-east`) | Toronto (`ca-tor`) | Sao Paulo (`br-sao`) |
|---------------------|------------------------|--------------------|----------------------|
| [Yes]{: tag-green}  | [Yes]{: tag-green}     | [Yes]{: tag-green} | [Yes]{: tag-green}   |
{: caption="Regions from which activity tracking events are sent in Americas locations" caption-side="top"}
{: #at-origins-table-1}
{: tab-title="Americas"}
{: tab-group="atorigins"}
{: class="simple-tab-table"}
{: row-headers}

| Tokyo (`jp-tok`)   | Sydney (`au-syd`)  |  Osaka (`jp-osa`)  | Chennai (`in-che`) |
|--------------------|--------------------|--------------------|--------------------|
| [Yes]{: tag-green} | [Yes]{: tag-green} | [Yes]{: tag-green} | [No]{: tag-red}    |
{: caption="Regions from which activity tracking events are sent in Asia Pacific locations" caption-side="top"}
{: #at-origins-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="atorigins"}
{: class="simple-tab-table"}
{: row-headers}

| Frankfurt (`eu-de`) | London (`eu-gb`)   | Madrid (`eu-es`)   |
|---------------------|--------------------|--------------------|
| [Yes]{: tag-green}  | [Yes]{: tag-green} | [Yes]{: tag-green} |
{: caption="Regions from which activity tracking events are sent in Europe locations" caption-side="top"}
{: #at-origins-table-3}
{: tab-title="Europe"}
{: tab-group="atorigins"}
{: class="simple-tab-table"}
{: row-headers}

## Locations where activity tracking events are sent to {{site.data.keyword.at_full_notm}} hosted event search
{: #at-legacy-locations}

{{site.data.keyword.contdelivery_short}} sends activity tracking events to {{site.data.keyword.at_full_notm}} hosted event search in the regions that are indicated in the following table.

| Dallas (`us-south`) | Washington (`us-east`) | Toronto (`ca-tor`) | Sao Paulo (`br-sao`) |
|---------------------|------------------------|--------------------|----------------------|
| [Yes]{: tag-green}  | [Yes]{: tag-green}     | [Yes]{: tag-green} | [Yes]{: tag-green}   |

{: caption="Regions where activity tracking events are sent in Americas locations" caption-side="top"}
{: #at-table-1}
{: tab-title="Americas"}
{: tab-group="at"}
{: class="simple-tab-table"}
{: row-headers}

| Tokyo (`jp-tok`)   | Sydney (`au-syd`)  |  Osaka (`jp-osa`)  | Chennai (`in-che`) |
|--------------------|--------------------|--------------------|--------------------|
| [Yes]{: tag-green} | [Yes]{: tag-green} | [Yes]{: tag-green} | [No]{: tag-red}    |
{: caption="Regions where activity tracking events are sent in Asia Pacific locations" caption-side="top"}
{: #at-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="at"}
{: class="simple-tab-table"}
{: row-headers}

| Frankfurt (`eu-de`) | London (`eu-gb`)   | Madrid (`eu-es`)   |
|---------------------|--------------------|--------------------|
| [Yes]{: tag-green}  | [Yes]{: tag-green} | [Yes]{: tag-green} |
{: caption="Regions where activity tracking events are sent in Europe locations" caption-side="top"}
{: #at-table-3}
{: tab-title="Europe"}
{: tab-group="at"}
{: class="simple-tab-table"}
{: row-headers}

## Locations where activity tracking events are sent by {{site.data.keyword.atracker_full_notm}}
{: #atracker-locations}

{{site.data.keyword.contdelivery_short}} sends activity tracking events by {{site.data.keyword.atracker_full_notm}} in the regions that are indicated in the following table.

| Dallas (`us-south`) | Washington (`us-east`) | Toronto (`ca-tor`) | Sao Paulo (`br-sao`) |
|---------------------|------------------------|--------------------|----------------------|
| [Yes]{: tag-green}  | [Yes]{: tag-green}     | [Yes]{: tag-green} | [Yes]{: tag-green}   |
{: caption="Regions where activity tracking events are sent in Americas locations" caption-side="top"}
{: #atracker-table-1}
{: tab-title="Americas"}
{: tab-group="atracker"}
{: class="simple-tab-table"}
{: row-headers}

| Tokyo (`jp-tok`)   | Sydney (`au-syd`)  |  Osaka (`jp-osa`)  | Chennai (`in-che`) |
|--------------------|--------------------|--------------------|--------------------|
| [Yes]{: tag-green} | [Yes]{: tag-green} | [Yes]{: tag-green} | [No]{: tag-red}    |
{: caption="Regions where activity tracking events are sent in Asia Pacific locations" caption-side="top"}
{: #atracker-table-2}
{: tab-title="Asia Pacific"}
{: tab-group="atracker"}
{: class="simple-tab-table"}
{: row-headers}

| Frankfurt (`eu-de`) | London (`eu-gb`)   | Madrid (`eu-es`)   |
|---------------------|--------------------|--------------------|
| [Yes]{: tag-green}  | [Yes]{: tag-green} | [Yes]{: tag-green} |
{: caption="Regions where activity tracking events are sent in Europe locations" caption-side="top"}
{: #atracker-table-3}
{: tab-title="Europe"}
{: tab-group="atracker"}
{: class="simple-tab-table"}
{: row-headers}

## Viewing activity tracking events for {{site.data.keyword.contdelivery_short}}
{: #at-viewing}

You can use {{site.data.keyword.logs_full_notm}} to visualize and alert on events that are generated in your account and routed by {{site.data.keyword.atracker_full_notm}} to an {{site.data.keyword.logs_full_notm}} instance.

{{site.data.keyword.contdelivery_short}} in a region sends activity tracking events by {{site.data.keyword.atracker_full_notm}} in the same region.

### Launching {{site.data.keyword.logs_full_notm}} from the Observability page
{: #log-launch-standalone}

For information on launching the {{site.data.keyword.logs_full_notm}} UI, see [Launching the UI in the {{site.data.keyword.logs_full_notm}} documentation.](/docs/cloud-logs?topic=cloud-logs-instance-launch)

## List of platform events
{: #at_actions_platform}

The following table lists the activity tracking event actions that the {{site.data.keyword.cloud_notm}} platform generates when {{site.data.keyword.contdelivery_short}} instances are processed.

| Action                                          | Description |
|-------------------------------------------------|-------------|
| `continuous-delivery.instance.create`           | An event is generated when you provision a service instance. |
| `continuous-delivery.instance.update`           | An event is generated when you rename a service instance or when you change the service plan. |
| `continuous-delivery.instance.delete`           | An event is generated when a service instance is deleted. |
| `continuous-delivery.instance.schedule_reclaim` | An event is generated when a service instance is pending_reclamation. |
| `continuous-delivery.instance.restore`          | An event is generated when a service instance is restored. |
{: caption="Actions that generate platform events" caption-side="bottom"}

The following table lists the actions that generate an event for managing service credentials that are associated with a service instance.

| Action                           | Description |
|----------------------------------|-------------|
| `continuous-delivery.key.create` | An event is generated when an API key is created for a service instance through the *Service credentials* section of the service instance UI. |
| `continuous-delivery.key.delete` | An event is generated when an API key that is associated with a service instance is deleted from the *Service credentials* section of the service instance UI. |
{: caption="Actions that generate service credentials events" caption-side="bottom"}

## Events for {{site.data.keyword.contdelivery_short}}
{: #at_actions_cd}

The following table lists the actions that generate {{site.data.keyword.contdelivery_short}} management and data events:

| Action                           | Description                        |
|----------------------------------|------------------------------------|
| `continuous-delivery.settings.read` | View the settings of a {{site.data.keyword.contdelivery_short}} service instance. |
| `continuous-delivery.settings.update` | Update the settings of a {{site.data.keyword.contdelivery_short}} service instance. |
{: caption="Lists of management events for {{site.data.keyword.contdelivery_short}}" caption-side="bottom"}
{: #componentcd-table-1}
{: tab-title="Management events"}
{: tab-group="componentcd"}
{: class="simple-tab-table"}
{: row-headers}

| Action                           | Description                        |
|----------------------------------|------------------------------------|
| `continuous-delivery.auth-user.create` | Manually or automatically add authorized users. For more information about automatically adding authorized users, see [How are users counted for instances of {{site.data.keyword.contdelivery_short}} in resource groups?](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage&interface=ui#count_users_rg). |
| `continuous-delivery.auth-user.read` | View the list of authorized users from the Manage tab of a {{site.data.keyword.contdelivery_short}} service instance. |
| `continuous-delivery.auth-user.delete` | Delete authorized users from the {{site.data.keyword.contdelivery_short}} service instance. |
| `continuous-delivery.consolidated-auth-users.list` | View the list of consolidated authorized users from the Manage tab of a {{site.data.keyword.contdelivery_short}} service instance. |
{: caption="Lists of data events for {{site.data.keyword.contdelivery_short}}" caption-side="bottom"}
{: #componentcd-table-2}
{: tab-title="Data events"}
{: tab-group="componentcd"}
{: class="simple-tab-table"}
{: row-headers}

## Events for toolchains
{: #at_actions_toolchain}

The following table lists the actions that generate toolchain management and data events:

| Action                           | Description                        |
|----------------------------------|------------------------------------|
| `toolchain.instance.create` | Create a toolchain |
| `toolchain.instance.update` | Rename a toolchain. This event is not sent when tool integrations are added to (`toolchain.tool-instance.deploy`) or removed from (`toolchain.tool-instance.undeploy`) a toolchain. If the toolchain is secured by a customer root key in a professional plan, the event contains the root key identifier. |
| `toolchain.instance.delete` | Delete a toolchain. |
| `toolchain.tool-instance.deploy` | Add a tool integration to a toolchain. |
| `toolchain.tool-instance.undeploy` | Remove a tool integration from a toolchain. |
| `toolchain.instance-key-state.update` | Update the root key in the key management service (KMS) provider that the toolchain uses. For example, enable, disable, or rotate a root key in a KMS provider. |
| `toolchain.instance.unwrap` | Unwrap a wrapped Data Encryption Key (wDEK) in order to encrypt or decrypt customer personal information. |
{: caption="Lists of management events for toolchains" caption-side="bottom"}
{: #componenttc-table-1}
{: tab-title="Management events"}
{: tab-group="componenttc"}
{: class="simple-tab-table"}
{: row-headers}

| Action                           | Description                        |
|----------------------------------|------------------------------------|
| `toolchain.event.send` | Send a client bespoke toolchain event. The event metadata includes the bespoke toolchain event's `title` and `description` values. |
| `toolchain.tool-instance.create` | Add a tool integration to a toolchain. This event is always followed by the toolchain.tool-instance.deploy event. |
| `toolchain.tool-instance.read` | View the configuration of a tool integration. |
| `toolchain.tool-instance.update` | Save configuration changes to a tool integration. |
| `toolchain.tool-instance.delete` | Remove a tool integration from a toolchain. This event is always preceded by the toolchain.tool-instance.undeploy event. |
{: caption="Lists of data events for toolchains" caption-side="bottom"}
{: #componenttc-table-2}
{: tab-title="Data events"}
{: tab-group="componenttc"}
{: class="simple-tab-table"}
{: row-headers}


Activity tracking events are different from client bespoke toolchain events. When you invoke the [POST /toolchains/{toolchain_id}/events](https://cloud.ibm.com/apidocs/toolchain#create-toolchain-event){: external} API to send a bespoke toolchain event, the toolchain sends a notification event to any instances of {{site.data.keyword.en_short}} that are integrated into the toolchain. In addition, the toolchain sends an activity tracking event that serves as a record of the API having been invoked. {: tip}

## Events for {{site.data.keyword.DRA_short}}
{: #at_actions_insights}

The following table lists the actions that generate {{site.data.keyword.DRA_short}} management and data events:

| Action                           | Description                        |
|----------------------------------|------------------------------------|
| `toolchain.insights-tag.create` | Create a tag. |
| `toolchain.insights-tag.read` | View a tag. |
| `toolchain.insights-tag.update` | Update a tag. |
| `toolchain.insights-tag.delete` | Delete a tag. |
| `toolchain.insights-decision.evaluate` | Make a gate decision on a build. |
{: caption="Lists of management events for {{site.data.keyword.DRA_short}}" caption-side="bottom"}
{: #componentdra-table-1}
{: tab-title="Management events"}
{: tab-group="componentdra"}
{: class="simple-tab-table"}
{: row-headers}

| Action                           | Description                        |
|----------------------------------|------------------------------------|
| `toolchain.insights.read` | View any build, deploy, or test record. |
| `toolchain.insights.update` | Publish a new build, deploy, or test record. The event's metadata includes `toolchainId` (unique identifier for toolchain) and might also contain the `build_artifact` (name of application), `build_id` (id of build), `branch` (Git branch of build), `environment_name` (name of environment where the test ran), and `operationId` (indicates how the update was completed, such as `postBuild`, `postResults`, `postDeployment`, `postResultsById`, `postLifeCycleStage`, `postBuildArtifactMetaData`, `putLifeCycleStage`, `putLifeCycleStagesOrder`, and `resultsMultipart`) values. The values that are included in the event's metadata is determined by the type of record (build, deployment, or test) that is published. |
| `toolchain.insights-policy.create` | Create a policy. |
| `toolchain.insights-policy.read` | View a policy. |
| `toolchain.insights-policy.update` | Update a policy. The event's metadata might include the `toolchainId` (unique identifier for toolchain) and `policyName` (name of policy that was updated) values. |
| `toolchain.insights-policy.delete` | Delete a policy. |
| `toolchain.insights-data-toolchain.delete` | Delete data for a toolchain. |
| `toolchain.insights-data-environment.delete` | Delete data for a specific environment. |
| `toolchain.insights-data-application.delete` | Delete data for a specific application. |
| `toolchain.insights-data-branch.delete` | Delete data for a specific application and branch. |
{: caption="Lists of data events for {{site.data.keyword.DRA_short}}" caption-side="bottom"}
{: #componentdra-table-2}
{: tab-title="Data events"}
{: tab-group="componentdra"}
{: class="simple-tab-table"}
{: row-headers}

## Events for component {{site.data.keyword.deliverypipeline}}
{: #at_actions_pipeline}

The following table lists the actions that generate {{site.data.keyword.deliverypipeline}} management and data events:

| Action                           | Description                        |
|----------------------------------|------------------------------------|
| `toolchain.pipeline.create` | Create a Classic delivery pipeline or a Tekton delivery pipeline for a toolchain. |
| `toolchain.pipeline-run.create` | Trigger a Classic delivery pipeline or a Tekton delivery pipeline to either run manually, at a scheduled time, when a specified Git event occurs, or by way of a POST request to the generic webhook URL. |
{: caption="Lists of management events for {{site.data.keyword.deliverypipeline}}" caption-side="bottom"}
{: #componentdp-table-1}
{: tab-title="Management events"}
{: tab-group="componentdp"}
{: class="simple-tab-table"}
{: row-headers}

| Action                           | Description                        |
|----------------------------------|------------------------------------|
| `toolchain.pipeline.read` | View the delivery pipeline or the Tekton pipeline from a  {{site.data.keyword.contdelivery_short}} service instance. |
| `toolchain.pipeline.update` | Rename the delivery pipeline or a Tekton pipeline. Update pipeline properties. Add, edit, or delete stages. This event is triggered by a change to a tool integration configuration. Because the customer data that is included in a typical update might contain secret data, job scripts, and more, this event does not include the `InitialValue` and `newValue` values. |
| `toolchain.pipeline.delete` | Delete the delivery pipeline or Tekton pipeline from the {{site.data.keyword.contdelivery_short}} toolchain instance  |
| `toolchain.pipeline-run.read` | View the run logs for a delivery pipeline or a Tekton pipeline in the Tekton dashboard. |
| `toolchain.pipeline-run.update` | Update the delivery pipeline when a job completes within a stage or a user cancels a stage. Because the customer data that is included in a typical update might contain secret data, log output, large data, and more, this event does not include the `InitialValue` and `newValue` values. |
| `toolchain.pipeline-run.delete` | Delete the delivery pipeline when a pipeline job run is deleted by the {{site.data.keyword.contdelivery_short}} service. The delivery pipeline retains a limited number of runs.  |
{: caption="Lists of data events for {{site.data.keyword.deliverypipeline}}" caption-side="bottom"}
{: #componentdp-table-2}
{: tab-title="Data events"}
{: tab-group="componentdp"}
{: class="simple-tab-table"}
{: row-headers}

## Analyzing {{site.data.keyword.contdelivery_short}} activity tracking events
{: #at_events_cd_analyze}

When user emails are added to or removed from the authorized users list of a {{site.data.keyword.contdelivery_short}} service instance in a resource group, {{site.data.keyword.contdelivery_short}} sends events to {{site.data.keyword.atracker_full_notm}} when either of the following methods are used.

* An administrator manually adds or removes a user email from the **Manage** tab of the {{site.data.keyword.contdelivery_short}} service.
* The system automatically adds one or more user emails in response to user-initiated or service-initiated actions with {{site.data.keyword.contdelivery_short}} toolchains.

The following authorized user events are sent to {{site.data.keyword.atracker_full_notm}}:

* `Continuous Delivery: create auth-user [service name] (auth-user(s): [EMAILS])`
* `Continuous Delivery: delete auth-user [service name] (auth-user(s): [EMAILS])`
* `Continuous Delivery: create auth-user [service name] (auth-user(s): [EMAILS]; root-action: [ACTION]; root-action-service-instance: [CRN])`
* `Continuous Delivery: delete auth-user [service name] (auth-user(s): [EMAILS]; root-action: [ACTION]; root-action-service-instance: [CRN])`

where:

* `[EMAILS]` is a comma-separated list of the user email IDs that are added to or removed from the list of authorized users.
* `[ACTION]` identifies the action that prompted the automatic addition or removal of user emails from the list of authorized users. If a root-action is not specified, the addition or removal of the user emails was performed directly by a user from the **Manage** tab of the {{site.data.keyword.contdelivery_short}} service dashboard.
* `[CRN]` specifies the [Cloud Resource Name](/docs/account?topic=account-crn) of the resource to which the root-action was applied. This resource can either be a toolchain or the {{site.data.keyword.contdelivery_short}} service instance itself.

The following table lists and describes the root actions that prompt user emails to automatically be added to or removed from the authorized users list.

| Root action | Description |
|:-----------------|:-----------------|
| `continuous-delivery.instance.create` | Add a user email when the {{site.data.keyword.contdelivery_short}} service is provisioned. This email belongs to the user who created the service instance. The `root-action-service-instance` CRN identifies the {{site.data.keyword.contdelivery_short}} service instance. |
| `continuous-delivery.instance.delete` | Remove user emails when the {{site.data.keyword.contdelivery_short}} service is de-provisioned. The `root-action-service-instance` CRN identifies the {{site.data.keyword.contdelivery_short}} service instance. |
| `toolchain.git-repos-and-issue-tracking-repo.evaluate` | Add user emails after system evaluation of a {{site.data.keyword.gitrepos}} repo. Multiple emails that correspond to users with Developer (or greater) access to the repo might be added. The `root-action-service-instance` CRN identifies the toolchain that contains the {{site.data.keyword.gitrepos}} tool integration. |
| `toolchain.pipeline-stage.start` | Add user emails when a delivery pipeline stage starts. If the pipeline stage is manually started, the email of the user who started the pipeline is added. If a pipeline stage is triggered by a change to a repository (repo) in the {{site.data.keyword.gitrepos}} tool integration, multiple emails that correspond to users with Developer (or greater) access to the repo might be added. The `root-action-service-instance` CRN identifies the toolchain that contains the pipeline. |
| `toolchain.pipeline.read` | Add a user email when the user views a delivery pipeline. The `root-action-service-instance` CRN identifies the toolchain that contains the pipeline. |
| `toolchain.pipeline.update` | Add a user email when the user edits a delivery pipeline. The `root-action-service-instance` CRN identifies the toolchain that contains the pipeline. |
{: caption="Actions that add or remove user emails from the authorized users list" caption-side="top"}
