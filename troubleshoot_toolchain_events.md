---

copyright:
  years: 2023
lastupdated: "2023-05-17"

keywords: troubleshoot, toolchains, toolchain events, Event Notifications

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Troubleshooting for toolchain events
{: #troubleshoot-toolchains-events}

General problems with toolchain events might include tool configuration or missing authorization issues. Often, you can recover from these problems by following a few easy steps.
{: shortdesc}


## Why am I not receiving any toolchain events?
{: #troubleshoot-receive-events}
{: troubleshoot}
{: support}

An {{site.data.keyword.en_full}} tool integration was added to the toolchain, but the required service-to-service authorization policy is not in place.

The {{site.data.keyword.en_short}} service is not receiving events from the toolchain.
{: tsSymptoms}

A toolchain must be authorized to send events to the {{site.data.keyword.en_short}} service. Without this service-to-service authorization policy, the {{site.data.keyword.en_short}} service cannot receive toolchain events.
{: tsCauses}

Grant service-to-service authorization between the toolchain and the {{site.data.keyword.en_short}} service instance.
{: tsResolve}

Make sure that the selected {{site.data.keyword.en_short}} service instance has an [IAM authorization policy](/iam/authorizations/grant) that allows the toolchain to send events to this service instance. For more information about granting authorization with the {{site.data.keyword.en_short}} service instance, see [Why am I denied permission to integrate an {{site.data.keyword.en_short}} instance?](/docs/event-notifications?topic=event-notifications-troubleshoot-integrate).

## Why am I not receiving any Tekton pipeline events?
{: #troubleshoot-receive-tekton-events}
{: troubleshoot}
{: support}

Unlike Classic pipelines, you can configure individual Tekton pipelines to send {{site.data.keyword.en_short}}. Pipeline events are sent only for Tekton pipelines for which {{site.data.keyword.en_short}} are enabled.

The {{site.data.keyword.en_short}} service is not receiving events from one or more Tekton pipelines. However, toolchain events and other events from tools in the same toolchain are received.  
{: tsSymptoms}

To configure a Tekton pipeline to send events, you must enable {{site.data.keyword.en_short}} on a per pipeline basis.
{: tsCauses}

Enable {{site.data.keyword.en_short}} for the Tekton pipeline:
{: tsResolve}

1. From your toolchain's Overview page, on the Delivery pipelines card, click the Delivery Pipeline to open the Tekton Delivery Pipeline dashboard.
1. In the **Other settings** section, enable **Event notifications**.
1. Click **Save**.
