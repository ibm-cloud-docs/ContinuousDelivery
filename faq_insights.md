---

copyright:
  years: 2015, 2022
lastupdated: "2022-11-04"

keywords: tool integration, toolchains, IBM Cloud, DevOps Insights, Quality Dashboard

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# FAQs for {{site.data.keyword.DRA_short}}
{: #faq_insights}

Get answers to frequently asked questions about using {{site.data.keyword.DRA_short}}.
{: shortdesc} 


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


## Can I manage {{site.data.keyword.DRA_short}} by using Terraform or APIs?
{: #insights_terraform_api}
{: faq}
{: support}

You can use Terraform or APIs to add {{site.data.keyword.DRA_short}} to a toolchain or to remove it from a toolchain. For more information about working with the {{site.data.keyword.DRA_short}} tool integration, see [Working with tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations) and [Adding {{site.data.keyword.DRA_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-dra).

You cannot use Terraform or APIs to manage {{site.data.keyword.DRA_short}} policies, rules, tags, or data. Instead, use the following methods to manage {{site.data.keyword.DRA_short}} policies, rules, tags, or data.

* Manage {{site.data.keyword.DRA_short}} policies and rules by using either the console or the `ibmcloud` CLI `doi` plug-in. Although you cannot delete policies by using the `ibmcloud` CLI `doi` plug-in, you can use the console to delete policies.
* Manage {{site.data.keyword.DRA_short}} tags only by using the console.
* Manage {{site.data.keyword.DRA_short}} data sets only by using the console. For more information about managing {{site.data.keyword.DRA_short}} data sets, see [Managing data sets](/docs/ContinuousDelivery?topic=ContinuousDelivery-adding-data-sets).
* Publish test data to {{site.data.keyword.DRA_short}} by using the `ibmcloud` CLI `doi` plug-in. For more information about publishing test data, see [Publishing test data to DevOps Insights](/docs/ContinuousDelivery?topic=ContinuousDelivery-publishing-test-data).
* Explore build, environment, quality, deployment frequency, build frequency, and quality trend data only by using the console. For more information about exploring this data, see [Working with DevOps Insights](/docs/ContinuousDelivery?topic=ContinuousDelivery-di_working).
