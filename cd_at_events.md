---

copyright:
  years: 2019
lastupdated: "2019-11-07"

keywords: event, security, IBM, activity tracker, LogDNA, Continuous Delivery

subcollection: containers

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:download: .download}
{:preview: .preview}

# {{site.data.keyword.at_full_notm}} events
{: #cd-at-events}

You can view, manage, and audit service-initiated and user-initiated activities in your {{site.data.keyword.contdelivery_full}} and toolchain instances by using the {{site.data.keyword.at_full}} service.
{: shortdesc}

{{site.data.keyword.contdelivery_short}} automatically generates events for specific actions and forwards these event logs to {{site.data.keyword.at_full_notm}}. To access these logs, you must [provision an instance of {{site.data.keyword.at_full_notm}}](/docs/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#gs_ov).

## Tracking {{site.data.keyword.contdelivery_short}} and toolchain events
{: #cd-events}

The following table lists the actions that generate an event:

| Action | Description | 
|:-----------------|:-----------------|
| `toolchain.instance.create` | Create a toolchain | 
| `toolchain.instance.delete` | Delete a toolchain |
| `toolchain.tool-instance.deploy` | Add a tool integration to a toolchain |
| `toolchain.tool-instance.undeploy` | Remove a tool integration from a toolchain |
| `continuous-delivery.auth-user.create` | Manually or automatically add authorized users. For more information about automatically adding authorized users, see [How are users counted for instances of {{site.data.keyword.contdelivery_short}} in resource groups?](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#how-are-users-counted-for-instances-of-continuous-delivery-in-resource-groups-) |
| `continuous-delivery.auth-user.delete` | Remove authorized users |
{: caption="Table 1. Actions that generate events" caption-side="top"}

## Interpreting authorized user events
{: #authorized-user-events}

When user emails are added to or removed from the authorized users list of a {{site.data.keyword.contdelivery_short}} service instance in a resource group, {{site.data.keyword.contdelivery_short}} sends events to {{site.data.keyword.at_full_notm}} when either of the following methods are used.

* An administrator manually adds or removes a user email from the **Manage** tab of the {{site.data.keyword.contdelivery_short}} service.
* The system automatically adds one or more user emails in response to user-initiated or service-initiated actions with {{site.data.keyword.contdelivery_short}} toolchains.

The following authorized user events are displayed in {{site.data.keyword.at_full_notm}}:

* `Continuous Delivery: create auth-user [service name] (auth-user(s): [EMAILS])`
* `Continuous Delivery: delete auth-user [service name] (auth-user(s): [EMAILS])`
* `Continuous Delivery: create auth-user [service name] (auth-user(s): [EMAILS]; root-action: [ACTION]; root-action-service-instance: [CRN])`
* `Continuous Delivery: delete auth-user [service name] (auth-user(s): [EMAILS]; root-action: [ACTION]; root-action-service-instance: [CRN])`

Where:

* `[EMAILS]` is a comma-separated list of the user email IDs that are added to or removed from the list of authorized users.
* `[ACTION]` identifies the action that prompted the automatic addition or removal of user emails from the list of authorized users. If a root-action is not specified, the addition or removal of the user emails was performed directly by a user from the **Manage** tab of the {{site.data.keyword.contdelivery_short}} service dashboard.
* `[CRN]` specifies the [Cloud Resource Name](/docs/resources?topic=resources-crn) of the resource to which the root-action was applied. This resource can either be a toolchain or the {{site.data.keyword.contdelivery_short}} service instance itself.

The following table lists and describes the root actions that prompt user emails to automatically be added to or removed from the authorized users list.

| Root action | Description | 
|:-----------------|:-----------------|
| `continuous-delivery.instance.create` | Add a user email when the {{site.data.keyword.contdelivery_short}} service is provisioned. This email belongs to the user who created the service instance. The `root-action-service-instance` CRN identifies the {{site.data.keyword.contdelivery_short}} service instance.   | 
| `continuous-delivery.instance.delete` | Remove user emails when the {{site.data.keyword.contdelivery_short}} service is de-provisioned. The `root-action-service-instance` CRN identifies the {{site.data.keyword.contdelivery_short}} service instance. |
| `toolchain.git-repos-and-issue-tracking-repo.evaluate` | Add user emails after system evaluation of a {{site.data.keyword.gitrepos}} repo. Multiple emails that correspond to users with Developer (or greater) access to the repo might be added. The `root-action-service-instance` CRN identifies the toolchain that contains the {{site.data.keyword.gitrepos}} tool integration. |
| `toolchain.pipeline-stage.start` | Add user emails when a delivery pipeline stage starts. If the pipeline stage is manually started, the email of the user who started the pipeline is added. If a pipeline stage is triggered by a change to a repository (repo) in the {{site.data.keyword.gitrepos}} tool integration, multiple emails that correspond to users with Developer (or greater) access to the repo might be added. The `root-action-service-instance` CRN identifies the toolchain that contains the pipeline. |
| `toolchain.pipeline.read` | Add a user email when the user views a delivery pipeline. The `root-action-service-instance` CRN identifies the toolchain that contains the pipeline.  |
| `toolchain.pipeline.update` | Add a user email when the user edits a delivery pipeline. The `root-action-service-instance` CRN identifies the toolchain that contains the pipeline.  |
| `toolchain.web-ide.read` | Add a user email when the user opens a workspace in the Eclipse Orion {{site.data.keyword.webide}}. The `root-action-service-instance` CRN identifies the toolchain that contains the {{site.data.keyword.webide}} workspace. |
{: caption="Table 2. Actions that add or remove user emails from the authorized users list" caption-side="top"}
