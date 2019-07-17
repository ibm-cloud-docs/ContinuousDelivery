---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-31"

keywords: secure environment, data, IBM Cloud Continuous Delivery, Data

subcollection: ContinuousDelivery

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Sécurisation de vos données    
{: #cd_data_security}  

{{site.data.keyword.contdelivery_full}} héberge vos bases de données dans un environnement hautement disponible et sécurisé :
   * Les données sont chiffrées au repos (GPFS, LUKS et disque intégré) et en cours (HTTPS et SSH). Les données d'identification client et système sont stockées sur des disques chiffrés.
   * L'application et les données sont configurées pour une haute disponibilité.
   * L'accès aux données est limité aux seuls utilisateurs qui ont besoin des données pour prendre en charge et maintenir le service.
