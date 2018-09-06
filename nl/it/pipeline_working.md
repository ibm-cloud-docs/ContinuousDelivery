---

copyright:
  years: 2015, 2018
lastupdated: "2018-7-19"

---


{:screen: .screen}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:shortdesc: .shortdesc}

# Gestione delle pipeline {: #pipeline-working}

Per automatizzare le tue creazioni e le tue distribuzioni in {{site.data.keyword.Bluemix}}, utilizza le pipeline {{site.data.keyword.contdelivery_full}}.
{: shortdesc}

Con le pipeline, puoi scegliere tra diversi tipi di build. Fornisci lo script di build e {{site.data.keyword.contdelivery_short}} lo esegue; non ha bisogno di impostare dei sistemi di build. Quindi, con un singolo clic, puoi distribuire automaticamente la tua applicazione a uno o più spazi {{site.data.keyword.Bluemix_notm}} server Cloud Foundry pubblici o contenitori Docker su {{site.data.keyword.containerlong}}.

I lavori di creazione compilano e impacchettano il codice sorgente della tua applicazione da repository Git. I lavori di creazione producono delle risorse utente distribuibili, quali file WAR o contenitori Docker per {{site.data.keyword.containerlong_notm}}. Puoi inoltre eseguire delle verifiche di unità nella tua build automaticamente. Puoi impostare i tuoi lavori di creazione in modo che venga attivata una creazione ogni volta che si esegue il push del commit.

Un lavoro di distribuzione prende l'output da un lavoro di creazione e lo distribuisce ai server {{site.data.keyword.containerlong_notm}} o Cloud Foundry come {{site.data.keyword.Bluemix_notm}}.

Puoi eseguire la distribuzione a uno o più regioni e servizi. Ad esempio, puoi impostare il tuo {{site.data.keyword.deliverypipeline}} per utilizzare uno o più servizi, eseguire verifiche in una regione e distribuire in produzione in più regioni. Per ulteriori informazioni, consulta [Regioni](/docs/overview/whatisbluemix.html#ov_intro_reg){: new_window}.

##Creazione di una pipeline

Puoi utilizzare uno qualsiasi dei seguenti metodi per creare una pipeline:

   * [Crea una toolchain da un'applicazione Cloud Foundry esistente](/docs/services/ContinuousDelivery/toolchains_working.html#creating_a_toolchain_from_an_app){: new_window}. La toolchain risultante contiene una pipeline.

   * [Crea una toolchain da un template](/docs/services/ContinuousDelivery/toolchains_working.html#creating_a_toolchain_from_a_template){: new_window} che include almeno una pipeline.

   * [Aggiungi l'integrazione dello strumento {{site.data.keyword.deliverypipeline}}](/docs/services/ContinuousDelivery/toolchains_integrations.html#deliverypipeline){: new_window} a una toolchain esistente.
   
Da {{site.data.keyword.deliverypipeline}}, puoi modificare la tua configurazione, controllare lo stato delle creazioni, dell'applicazione distribuita e delle ultime distribuzioni, visualizzare i log più recenti e i dettagli di distribuzione oppure eliminare la tua pipeline.
