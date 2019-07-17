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


# Come rendere sicuri i tuoi dati    
{: #cd_data_security}  

{{site.data.keyword.contdelivery_full}} ospita i tuoi database in un ambiente sicuro ad alta disponibilità:
   * I dati sono crittografati quando inattivi (GPFS, LUKS e disco integrato) e quando in transito (HTTPS e SSH). Le credenziali di cliente e sistema vengono archiviate su dischi crittografati.
   * L'applicazione e i dati sono configurati per l'alta disponibilità.
   * L'accesso ai dati è limitato a solo gli utenti che richiedono i dati per il supporto e la manutenzione del servizio.
