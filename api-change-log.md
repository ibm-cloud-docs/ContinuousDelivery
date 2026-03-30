---

copyright:
  years:  2024
lastupdated: "2024-09-24"

keywords: change log for Continuous Delivery API, updates to Continuous Delivery API

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Continuous Delivery API change log
{: #api-change-log}

In this change log, you can learn about the latest changes, improvements, and updates for the Continuous Delivery API, which consists of the [Toolchain API](/apidocs/toolchain) and the [Tekton Pipeline API](/apidocs/tekton-pipeline). The change log lists changes that have been made, ordered by the date they were released. Changes to existing API versions are designed to be compatible with existing client applications.

For details on the latest version for each API, see:
- [Toolchain API versioning](/apidocs/toolchain#versioning)
- [Tekton Pipeline API versioning](/apidocs/tekton-pipeline#versioning)

For information about the latest changes to the `Continuous Delivery` SDKs, see the change logs in the SDK repositories:
- [Java SDK change log](https://github.com/IBM/continuous-delivery-java-sdk/blob/main/CHANGELOG.md)
- [Node SDK change log](https://github.com/IBM/continuous-delivery-node-sdk/blob/main/CHANGELOG.md)
- [Python SDK change log](https://github.com/IBM/continuous-delivery-python-sdk/blob/main/CHANGELOG.md)
- [Go SDK change log](https://github.com/IBM/continuous-delivery-go-sdk/blob/main/CHANGELOG.md)

## API versioning
{: #api-versioning}

API requests require a `version` path parameter that takes the date in the format `/toolchain/{version}/{endpoint}`, or `/pipeline/{version}/{endpoint}`, where `endpoint` represents any listed endpoint in the corresponding API documentation. The only version which is currently supported is `v2`.

When the API is changed in a way that is not compatible with previous versions, a new major version is released. To take advantage of the changes in a new version, change the value of the version parameter to the new version.

## 30 March 2026
{: #30-mar-2026}
{: release-note}
{{site.data.keyword.contdelivery_short}} will be discontinued in the following regions on 10 April 2026: **eu-es** and **jp-osa**.
This discontinuation also applies to any features provided within the service, including Code Risk Analyzer and {{site.data.keyword.DRA_short}}.

If you have the {{site.data.keyword.contdelivery_short}} service in Madrid (eu-es) or Osaka (jp-osa), we provide a [migration guide](https://cloud.ibm.com/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-migrate-region) to help you with:
* Migrate Git Repos and Issue Tracking projects across regions via direct transfer (GitLab feature).
* Copy toolchains (including Tekton pipelines) to another region using the migration guide
* Securely export and move secrets to Secrets Manager

## 12 February 2026
{: #12-feb-2026}

The {{site.data.keyword.contdelivery_short}} service is deprecated in the following regions: **au-syd**, **ca-mon**, **ca-tor**, **eu-es**, **jp-osa** and **us-east**. The regional endpoints for the Toolchain and Tekton Pipeline APIs in those regions will be discontinued on 12 February 2027. On 12 June 2026, customers will no longer be able to create new resources in the affected regions. However, if a region has no active usage, the region may be discontinued earlier and stop accepting new instances. [Learn more](/docs/ContinuousDelivery?topic=ContinuousDelivery-faq_region_feature_consolidation).

## 24 September 2024
{: #24-sep-2024}

The `POST /toolchains/:toolchain_id/events` endpoint is now generally available.
