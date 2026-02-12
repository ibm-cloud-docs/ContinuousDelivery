---

copyright:
  years: 2015, 2026
lastupdated: "2026-02-12"

keywords: troubleshoot, toolchains, tool integrations, DevOps Insights

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:tip: .tip}
{:important: .important}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:support: data-reuse='support'}

# Troubleshooting for {{site.data.keyword.DRA_short}}
{: #troubleshoot-insights}

{{site.data.keyword.contdelivery_short}} will be discontinued in these regions on 12 Feb 2027: au-syd, ca-mon, ca-tor, eu-es, jp-osa, us-east. Code Risk Analyzer and {{site.data.keyword.DRA_short}} will also be deprecated in all regions. Follow the [migration guide](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-migrate-region) to avoid disruption. However, if a region has no active usage of these features, the features in that region may be discontinued earlier and stop accepting new instances. [Learn more](/docs/ContinuousDelivery?topic=ContinuousDelivery-faq_region_feature_consolidation)
{: important}

General problems with using {{site.data.keyword.DRA_short}} might include toolchains, toolchain templates, or tool integration configuration issues. In many cases, you can recover from these problems by following a few easy steps.
{: shortdesc}


## How do I find toolchains that support {{site.data.keyword.DRA_short}}?
{: #find-toolchain-ts}
{: faq}

You can't find any toolchain templates that support {{site.data.keyword.DRA_short}}.
{: tsSymptoms}

Toolchains with {{site.data.keyword.DRA_short}} appear in the catalog when the correct locations are selected.
{: tsCauses}

Update your current location by completing the following steps:

1. From the {{site.data.keyword.cloud_notm}} console, click the **Menu** icon ![hamburger icon](images/icon_hamburger.svg) > **Platform Automation** > **Toolchains**.
2. From the **Location** menu, select your location.
3. Click **Create a Toolchain** to return to the toolchain templates page.
{: tsResolve}
