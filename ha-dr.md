---

copyright:
  years: 2018, 2021
lastupdated: "2021-06-16"

keywords: high availability, disaster recovery, SLA

subcollection: ContinuousDelivery


---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# High availability and disaster recovery
{: #ha-dr}

All {{site.data.keyword.cloud}} general availability (GA) services have a Service Level Agreement of 99.99% availability. {{site.data.keyword.contdelivery_full}} is a GA service that is offered in multiple regions: Dallas, Washington, Toronto, Frankfurt, Tokyo, Sydney, Osaka, and London. Each location has three different data centers for redundancy. The data for each location is kept in the three data centers near that location. If all of the data centers in a location fail, the {{site.data.keyword.contdelivery_short}} service for that location becomes unavailable.

{{site.data.keyword.contdelivery_short}} does not replicate data outside of a region, except for backup data. When possible, backup data is kept within the data centers of a country but data is always kept within a geography. European data does not leave the EU. To learn more about where {{site.data.keyword.contdelivery_short}} backup data is stored, see [Object Storage Location](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-compute-isolation#cd-object-storage).

{{site.data.keyword.contdelivery_short}} is available only on the public cloud, but the tools that are used with {{site.data.keyword.contdelivery_short}} can run in dedicated or public cloud environments and in on-premises environments. 

See [ensure zero downtime](/docs/overview?topic=overview-zero-downtime#zero-downtime) to learn more about the high availability and disaster recovery standards in {{site.data.keyword.cloud_notm}}. For more information about high availability and disaster recovery for {{site.data.keyword.contdelivery_short}}, see [Your responsibilities with using {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-responsibilities-cd#disaster-recovery). You can also find information about [Service Level Agreements](/docs/overview?topic=overview-slas).
