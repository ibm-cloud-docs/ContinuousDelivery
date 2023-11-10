---

copyright:
  years: 2018, 2023
lastupdated: "2023-11-10"

keywords: high availability, disaster recovery, SLA

subcollection: ContinuousDelivery


---

{{site.data.keyword.attribute-definition-list}}


# {{site.data.keyword.contdelivery_short}} high availability and disaster recovery
{: #ha-dr}

{{site.data.keyword.contdelivery_full}} is a general availability (GA) service with a Service Level Agreement of 99.99% availability that is offered in multiple regions: Dallas, Washington, Toronto, Sao Paulo, Frankfurt, Tokyo, Sydney, Osaka,  London, and Madrid. Each location has three different data centers for redundancy. The data for each location is kept in the three data centers near that location. If all of the data centers in a location fail, the {{site.data.keyword.contdelivery_short}} service for that location becomes unavailable.

{{site.data.keyword.contdelivery_short}} does not replicate data outside of a region, except for backup data. When possible, backup data is kept within the data centers of a country but data is always kept within a geography. European data does not leave the EU. To learn more about where {{site.data.keyword.contdelivery_short}} backup data is stored, see [Object Storage Location](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-compute-isolation#cd-object-storage).

{{site.data.keyword.contdelivery_short}} is available only on the public cloud, but the tools that are used with {{site.data.keyword.contdelivery_short}} can run in public cloud environments and in on-premises environments. 

See [ensure zero downtime](/docs/overview?topic=overview-zero-downtime#zero-downtime) to learn more about the high availability and disaster recovery standards in {{site.data.keyword.cloud_notm}}. For more information about high availability and disaster recovery for {{site.data.keyword.contdelivery_short}}, see [Your responsibilities with using {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-responsibilities-cd#disaster-recovery). You can also find information about [Service Level Agreements](/docs/overview?topic=overview-slas).
