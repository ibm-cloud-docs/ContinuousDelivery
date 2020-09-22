---

copyright:
  years: 2015, 2020
lastupdated: "2020-06-24"

keywords: private workers

subcollection: ContinuousDelivery

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
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

# FAQs for Pipeline Private Workers
{: #faq_pipeline_private_workers}

Get answers to frequently asked questions about using Pipeline Private Workers.
{:shortdesc} 


## How do I view the status of private workers on multiple clusters by using the CLI?
{: #pipeline_private_worker_status}
{: faq}
{: support}

You can use the following command within a script that traverses all of the clusters that private workers are installed on.

```
kubectl get workeragent -ojson | jq '.items[] | .status.versionStatus.state'
```

Consider upgrading any private workers that return results that are not `OK`.
