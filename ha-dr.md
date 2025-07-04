---

copyright:
  years: 2018, 2025
lastupdated: "2025-06-06"

keywords: high availability, disaster recovery, SLA

subcollection: ContinuousDelivery


---

{{site.data.keyword.attribute-definition-list}}


# {{site.data.keyword.contdelivery_short}} high availability and disaster recovery
{: #ha-dr}

{{site.data.keyword.contdelivery_full}} is a general availability (GA) service with a Service Level Agreement of 99.99% availability that is offered in multiple regions: Dallas (`us-south`), Washington DC (`us-east`), Toronto (`ca-tor`), Sao Paulo (`br-sao`), Frankfurt (`eu-de`), Madrid (`eu-es`), London (`eu-gb`), Tokyo (`jp-tok`), Osaka (`jp-osa`), and Sydney (`au-syd`). Each location has three different data centers for redundancy. The data for each location is kept in the three data centers near that location. If all of the data centers in a location fail, the {{site.data.keyword.contdelivery_short}} service for that location becomes unavailable.

{{site.data.keyword.contdelivery_short}} does not replicate data outside of a region, except for backup data. When possible, backup data is kept within the data centers of a country but data is always kept within a geography. European data does not leave the EU. To learn more about where {{site.data.keyword.contdelivery_short}} backup data is stored, see [Object Storage Location](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-compute-isolation#cd-object-storage).

{{site.data.keyword.contdelivery_short}} is available only on the public cloud, but the tools that are used with {{site.data.keyword.contdelivery_short}} can run in public cloud environments and in on-premises environments.

See [ensure zero downtime](/docs/resiliency?topic=resiliency-ha-redundancy#zero-downtime) to learn more about the high availability and disaster recovery standards in {{site.data.keyword.cloud_notm}}. For more information about high availability and disaster recovery for {{site.data.keyword.contdelivery_short}}, see [Your responsibilities with using {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-responsibilities-cd#disaster-recovery). You can also find information about [Service Level Agreements](/docs/overview?topic=overview-slas).

In the event that a region becomes unavailable, you can use {{site.data.keyword.contdelivery_short}} in another region. The following table lists recommended alternate regions to use. The recommendations are based on geographic proximity and data sovereignty; however, you can choose any alternate region that suits your requirements.

| Region                        | Suggested alternate region       |
| ------------------------------| ---------------------------------|
| Dallas (`us-south`)           | Washington (`us-east`)           |
| Frankfurt (`eu-de`)           | Madrid (`eu-es`)                 |
| London (`eu-gb`)              | Frankfurt (`eu-de`)              |
| Madrid (`eu-es`)              | Frankfurt (`eu-de`)              |
| Osaka (`jp-osa`)              | Tokyo (`jp-tok`)                 |
| São Paulo (`br-sao`)          | Dallas (`us-south`)              |
| Sydney (`au-syd`)             | Tokyo (`jp-tok`)                 |
| Tokyo (`jp-tok`)              | Osaka (`jp-osa`)                 |
| Toronto (`ca-tor`)            | Washington (`us-east`)           |
| Washington (`us-east`)        | Dallas (`us-south`)              |
{: caption="Regions and suggested alternates" caption-side="top"}
