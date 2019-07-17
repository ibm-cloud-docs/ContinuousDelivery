---



copyright:
  years: 2015，2019
lastupdated: "2019-06-19"

keywords: IBM Cloud Live Synch, Use IBM Cloud Live Sync

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# {{site.data.keyword.Bluemix_notm}} Live Sync
{: #live-sync}

Se stai creando un'applicazione Node.js, puoi utilizzare {{site.data.keyword.Bluemix}} Live Sync per aggiornare rapidamente l'istanza dell'applicazione su {{site.data.keyword.Bluemix_notm}} e sviluppare senza ridistribuire manualmente.   
{: shortdesc}

Quando apporti una modifica, puoi vedere tale modifica nell'applicazione {{site.data.keyword.Bluemix_notm}} in esecuzione immediatamente. {{site.data.keyword.Bluemix_notm}} Live Sync funziona
<!--from both the command line and -->
in Eclipse Orion {{site.data.keyword.webide}} ({{site.data.keyword.webide}}). 

##Live Edit
{: #live-edit}

Puoi modificare un'applicazione Node.js in esecuzione in {{site.data.keyword.Bluemix_notm}} e verificarla subito nel tuo browser. Qualsiasi modifica da te apportata nel {{site.data.keyword.webide}} viene propagata immediatamente al file system dell'applicazione.

Se stai creando un'applicazione Node.js che viene eseguita su {{site.data.keyword.Bluemix_notm}}, la funzione Live Edit di {{site.data.keyword.Bluemix_notm}} Live Sync può aggiornare rapidamente l'istanza dell'applicazione. Live Edit è disponibile solo in {{site.data.keyword.webide}}. Puoi utilizzare Live Edit per effettuare attività di sviluppo come faresti sul desktop senza eseguire nuovamente la distribuzione.

Live Edit è supportato solo per le applicazioni Node.js.
{: important}

In {{site.data.keyword.webide}}, nella barra di esecuzione, fai clic su **Live Edit**.

![Immagine della bara di esecuzione con live edit](images/cloud-live-sync-light.png)

Utilizza Live Edit per visualizzare rapidamente in anteprima le modifiche alle applicazioni Node.js in esecuzione su {{site.data.keyword.Bluemix_notm}}. Quando aggiorni il tuo codice con Live Edit attivato, puoi aggiornare la finestra del browser della tua applicazione web per vedere tali modifiche riflesse entro pochi secondi da quando le hai apportate.

Per un'esercitazione sull'utilizzo della funzione Live Edit di {{site.data.keyword.Bluemix_notm}}, vedi [Use {{site.data.keyword.Bluemix_notm}} Live Sync to develop, debug, and deploy your app](https://www.ibm.com/cloud/garage/tutorials/use-live-sync-to-develop-debug-and-deploy-your-app){: external}.

Quando modifichi i file nel tuo {{site.data.keyword.webide}}, questi vengono ridistribuiti automaticamente alla tua istanza dell'applicazione su {{site.data.keyword.Bluemix_notm}}. Se hai bisogno di riavviare l'applicazione Node, fai clic sul pulsante **Restart** nella barra di esecuzione.

Per un'esperienza più coerente quanto utilizzi la funzione Live Edit di {{site.data.keyword.Bluemix_notm}} Live Sync, sono richiesti e aggiunti 256 MB di memoria supplementare.
{: tip}
