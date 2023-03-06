---

copyright:
  years: 2023
lastupdated: "2023-03-06"

keywords: high availability, disaster recovery, toolchains, toolchain backup

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}

# Managing alternative toolchains in different regions
{: #cd-ha-dr-alttoolchains}

You can define your toolchain by using Terraform Configuration Language, and then apply and maintain your toolchain definition in two regions: a primary region with active pipelines, and an alternative region with idle pipelines. If you use {{site.data.keyword.gitrepos}}, you can also [mirror your Git repos](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-ha-dr-mirrorgit) from the primary region to the alternative region. Maintaining primary and alternative toolchains and Git repos provides faster failover and redundancy. It also ensures smooth operation if issues arise in the primary region. By codifying your toolchain in Terraform, you can update your toolchain and apply the changes to both regions.

For more information about using Terraform, see [Setting up Terraform for {{site.data.keyword.contdelivery_short}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-terraform-setup).
