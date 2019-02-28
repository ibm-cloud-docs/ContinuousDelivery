---

copyright:
  years: 2018, 2019
lastupdated: "2019-2-25"

keywords: secure environment, data, IBM Cloud Continuous Delivery, Data

subcollection: ContinuousDelivery

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Securing your data    
{: #cd_data_security}  

{{site.data.keyword.contdelivery_full}} hosts your databases in a highly available and secure environment:
   * Data is encrypted at rest (GPFS, LUKS, and Softlayer) and in flight (HTTPS and SSH). Client and system credentials are stored on encrypted disks.
   * The application and data are configured for high availability.
   * Access to data is limited to only those users who require the data to support and maintain the service.
