---

copyright:
  years: 2015, 2020
lastupdated: "2020-02-27"

keywords: tool integration, toolchains, IBM Cloud, DevOps Insights, Quality Dashboard

subcollection: ContinuousDelivery

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:faq: data-hd-content-type='faq'}
{:support: data-reuse='support'}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# FAQs for {{site.data.keyword.DRA_short}}
{: #faq_insights}

Get answers to frequently asked questions about using {{site.data.keyword.DRA_short}}.
{:shortdesc} 


## Can {{site.data.keyword.DRA_short}} be installed and run in an on-premises environment?
{: #run-on-prem}
{: faq}

{{site.data.keyword.DRA_short}} isn't available for an on-premises environment. It's only available in {{site.data.keyword.IBM_notm}} Public Cloud.


## My Jenkins or Travis CI is running in an on-premises environment or in another public cloud. Can I still publish build records, test records, deployment records to DevOps Insights, and use quality gates?
{: #CI-on-prem}
{: faq}

Yes, it doesn't matter from where your pipeline tool is running.


## I am deploying my applications to on-premises environments or other public clouds. Can I publish build records, test records, deployment records to {{site.data.keyword.DRA_short}}, and use quality gates for these applications? 
{: #app-on-prem}
{: faq}

Yes, it doesn't matter where your applications are deployed.


## Why can't I see my app on the Quality Dashboard page?
{: #app-quality-dashboard}
{: faq}

For an application to show up in the Quality Dashboard page, it must have a build record for the selected branch, and at least one test record for that build. For more information about build and test records, see [Integrating your {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-setting-values-cli).

You can find published build records on the Build Frequency page. For more information, see [Viewing the build frequency](/docs/ContinuousDelivery?topic=ContinuousDelivery-publish-build-cli#build-frequency-cli).


## How do I delete {{site.data.keyword.DRA_short}}?
{: #delete-insights-faq}
{: faq}

Deleting your tool integration deletes all data that is associated with that toolchain. For more information about how to delete your {{site.data.keyword.DRA_short}} instance, see [Deleting a DevOps Insights tool integration](/docs/ContinuousDelivery?topic=ContinuousDelivery-deleting_data).  


## Can I delete build, test, and deploy data from {{site.data.keyword.DRA_short}}?
{: #delete-specific-data}
{: faq}

You can delete data sets from for toolchain, environment, application, and for a branch. For more information about how to delete a specific data set, see [Deleting {{site.data.keyword.DRA_short}} data sets](/docs/ContinuousDelivery?topic=ContinuousDelivery-deleting_data).


## Do I need a {{site.data.keyword.contdelivery_short}} service instance to use {{site.data.keyword.DRA_short}}?
{: #cd-for-di}

Yes. To use {{site.data.keyword.DRA_short}}, you must create a {{site.data.keyword.contdelivery_short}} [service instance](https://cloud.ibm.com/catalog/services/continuous-delivery) if you don't already have one. For more information, see [Scope of a service instance](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#service_scope). 


## How am I billed for {{site.data.keyword.DRA_short}}?
{: #billed-devops-insights}

You are not billed for {{site.data.keyword.DRA_short}} as an individual service. {{site.data.keyword.DRA_short}} counts toward your {{site.data.keyword.contdelivery_short}} limitations and usage. A user of {{site.data.keyword.DRA_short}} is added to your {{site.data.keyword.contdelivery_short}} authorized users. For more information, see [Authorized users](/docs/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage#authorized_users). 
