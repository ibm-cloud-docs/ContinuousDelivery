---

copyright:
  years: 2015, 2020
lastupdated: "2020-02-21"

keywords: troubleshoot, toolchains, tool integrations, DevOps Insights

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
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

General problems with using {{site.data.keyword.DRA_short}} might include toolchains, toolchain templates, or tool integration configuration issues. In many cases, you can recover from these problems by following a few easy steps.
{:shortdesc}


## How do I find toolchains that support {{site.data.keyword.DRA_short}}?
{: #find-toolchain-ts}
{: faq}

You can't find any toolchain templates that support {{site.data.keyword.DRA_short}}.
{: tsSymptoms}

Toolchains with {{site.data.keyword.DRA_short}} appear in the catalog when the correct locations are selected. {{site.data.keyword.DRA_short}} is available only in three locations: Dallas, Frankfurt, and London.
{: tsCauses}

Update your current location by completing the following steps:

1. Click the **menu** icon ![hamburger icon](images/icon_hamburger.svg), and select **DevOps**.
2. From the **LOCATION** menu, select Dallas, Frankfurt, or London depending on your location.
3. Click **Create a Toolchain** to return to the toolchain templates page.
{: tsResolve}
