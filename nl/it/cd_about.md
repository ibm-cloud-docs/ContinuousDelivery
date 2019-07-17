---

Copyright:
  years: 2015, 2019
lastupdated: "2019-06-18"

keywords: IBM Cloud Public, Use Developer Insights, US South

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


# Disponibilità delle toolchain, template ed esercitazioni  
{: #cd_about}  

Le toolchain sono disponibili su {{site.data.keyword.Bluemix_notm}} Pubblico e Dedicato. Puoi utilizzare un template come un punto di partenza per creare una toolchain.
{:shortdesc}

## Disponibilità delle toolchain su {{site.data.keyword.Bluemix_notm}} Pubblico in confronto a {{site.data.keyword.Bluemix_notm}} Dedicato
{: #public_and_dedicated}

{{site.data.keyword.Bluemix_notm}} Pubblico è una piattaforma a standard aperti e basata sul cloud dove puoi creare, eseguire e gestire applicazioni con accesso mediante [http://cloud.ibm.com](http://cloud.ibm.com){: external}. {{site.data.keyword.Bluemix_notm}} Dedicato fornisce le funzionalità di {{site.data.keyword.Bluemix_notm}} in un ambiente di infrastruttura dedicata collegato in modo sicuro all'ambiente {{site.data.keyword.Bluemix_notm}} Pubblico e alla tua rete. L'ambiente {{site.data.keyword.Bluemix_notm}} Dedicato della tua azienda potrebbe non contenere le stesse integrazioni dello strumento come il sito {{site.data.keyword.Bluemix_notm}} Pubblico.

Per la gestione del codice sorgente e la traccia dei problemi, {{site.data.keyword.Bluemix_notm}} Pubblico generalmente utilizza {{site.data.keyword.gitrepos}} (ospitato da IBM e sviluppato su [GitLab Community Edition](https://about.gitlab.com/){: external}) oppure GitHub (github.com). {{site.data.keyword.Bluemix_notm}} Dedicato può anche utilizzare github.com, ma normalmente utilizza {{site.data.keyword.ghe_short}} che viene installato dalla tua azienda o gestito da IBM.

{{site.data.keyword.contdelivery_short}} è disponibile su {{site.data.keyword.Bluemix_notm}} Pubblico in specifiche regioni e in {{site.data.keyword.Bluemix_notm}} Dedicato. Le toolchain sono diverse a seconda se utilizzi {{site.data.keyword.contdelivery_short}} su {{site.data.keyword.Bluemix_notm}} Pubblico o {{site.data.keyword.Bluemix_notm}} Dedicato.

Anche se le toolchain non sono attualmente disponibili in tutte le regioni, puoi configurare la tua toolchain per distribuire le tue applicazioni in tutte le regioni. Per ulteriori informazioni, prova l'esercitazione [Deploy a secure web application across multiple regions](/docs/tutorials?topic=solution-tutorials-multi-region-webapp).
{: tip}

|Toolchain |{{site.data.keyword.Bluemix_notm}} Pubblico	|{{site.data.keyword.Bluemix_notm}} Dedicato |
|:----------|:------------------------------|:------------------|
|Integrazioni dello strumento 		|Per un elenco di integrazioni dello strumento, consulta [Configurazione delle integrazioni dello strumento](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations). 		|Le integrazioni dello strumento sono disponibili a seconda di come {{site.data.keyword.contdelivery_short}} è stato impostato nel tuo ambiente.			|
|Creazione di una toolchain da un template		|Accedi a [{{site.data.keyword.Bluemix_notm}}](http://cloud.ibm.com/devops){: external}.		|Accedi al tuo ambiente dedicato su {{site.data.keyword.Bluemix_notm}}.			|
|Creazione di una toolchain da un applicazione		|L'applicazione è configurata per la fornitura continua da un nuovo repository GitHub che viene popolato con il codice starter dell'applicazione.		|L'applicazione è configurata per la fornitura continua da un nuovo repository GitHub o GitHub Enterprise che viene popolato con il codice starter dell'applicazione.		|  
|Regioni di distribuzione di Delivery pipeline		|Tutte le regioni di {{site.data.keyword.Bluemix_notm}} Pubblico sono disponibili per i lavori di distribuzione Cloud Foundry. 		|La regione di {{site.data.keyword.Bluemix_notm}} Dedicato è disponibile. Altre regioni dedicate o locali nello stesso account del cliente potrebbero essere disponibili a seconda di come {{site.data.keyword.contdelivery_short}} è stato configurato nel tuo ambiente specifico.		|
|Lavori di distribuzione di Delivery pipeline		|Tutti i [tipi di lavoro](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_jobs) sono disponibili.		|I tipi di lavoro che dipendono dai servizi {{site.data.keyword.Bluemix_notm}} non installati nell'ambiente dedicato potrebbero non essere disponibili.	Ad esempio, il contenitore che crea e distribuisce i tipi di lavoro potrebbe non essere disponibile negli ambienti che non dispongono di {{site.data.keyword.containerlong_notm}}.	|
{: caption="Tabella 1. Differenze tra le toolchain su {{site.data.keyword.Bluemix_notm}} Dedicato e {{site.data.keyword.Bluemix_notm}} pubblico" caption-side="top"}


## Template toolchain
{: #templates}

Puoi utilizzare un template come punto di partenza per [creare una toolchain](https://cloud.ibm.com/devops/create){: external}. I template toolchain includono serie specifiche di integrazioni dello strumento che supportano le attività operative, di sviluppo e di distribuzione.

L'ambiente {{site.data.keyword.Bluemix_notm}} Dedicato della tua azienda potrebbe non contenere gli stessi modelli della toolchain del sito {{site.data.keyword.Bluemix_notm}} Pubblico. I template della toolchain disponibili in {{site.data.keyword.Bluemix_notm}} Pubblico e {{site.data.keyword.Bluemix_notm}} Dedicato potrebbero contenere una serie differente di integrazioni dello strumento in {{site.data.keyword.Bluemix_notm}} Dedicato.
{: note}

Alcuni template della toolchain includono le integrazioni dello strumento come parte del servizio {{site.data.keyword.contdelivery_short}}. Se un'istanza di tale servizio non è già nella tua organizzazione o nel tuo gruppo di risorse, quando fai clic su **Create** per creare la toolchain, il servizio viene automaticamente aggiunto con il piano Lite gratuito selezionato. Per ulteriori informazioni e i termini, vedi il [Catalogo di {{site.data.keyword.Bluemix_notm}}](https://cloud.ibm.com/catalog/services/continuous-delivery/){: external}.

La toolchain "Develop and test microservices on Cloud Foundry" distribuisce un'applicazione con API catalogo e ordini supportate da un negozio Cloudant. Come parte della distribuzione di un'applicazione, viene creata un'istanza del servizio Cloudant gratuita. Per ulteriori informazioni e i termini, vedi il [Catalogo di {{site.data.keyword.Bluemix_notm}}](https://cloud.ibm.com/catalog/services/cloudant-nosql-db/){: external}.

I template di toolchain DevOps predefiniti sono degli esempi consigliati che risolvono scenari reali e ciascuno di essi contiene un'applicazione di esempio.  Puoi utilizzare la tua applicazione specificando il tuo repository git quando crei la toolchain dal template.

<table valign="top" padding="2px">
  <caption>Tabella 2. Template di toolchain</caption>
  <tr>
    <th style="width:25%; text-align:left; vertical-align:top">Template e regioni disponibili</th>
    <th style="width:50%; text-align:left; vertical-align:top">Descrizione ed esercitazioni disponibili</th>
    <th style="text-align:left; vertical-align:top">Strumenti inclusi</th>
  </tr>
  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-toolchain" target="_blank">Toolchain “Sviluppa un'app Cloud Foundry" <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a> <br><br>

  Disponibile in Stati Uniti Sud, Stati Uniti Est, Germania, Tokyo e Regno Unito

  </td><td>
  Con questa toolchain, puoi sviluppare e distribuire un'applicazione Cloud Foundry. Per impostazione predefinita, questa toolchain utilizza un'applicazione Node.js "Hello world" di esempio ma puoi invece collegare il tuo proprio repository GitHub. La toolchain è preconfigurata per la fornitura continua, il controllo dell'origine, il tracciamento del problema e la modifica online.	<br><br>

  Prova l'esercitazione: <a href="https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain" target="_blank">Introduce Toolchains by using the “Develop a Cloud Foundry app” toolchain <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a> <br><br>
  </td><td><ul><li>
  {{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub e problemi
  </li><li>{{site.data.keyword.Bluemix_notm}}
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsecure-kube-toolchain" target="_blank">Toolchain "Sviluppa un'app Kubernetes" <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a> <br><br>

  Disponibile in Stati Uniti Sud, Stati Uniti Est, Germania, Tokyo e Regno Unito

  </td><td>
  Con questa toolchain, puoi sviluppare e distribuire un'applicazione in modo protetto in un cluster Kubernetes gestito di {{site.data.keyword.containerlong_notm}}. Per impostazione predefinita, la toolchain utilizza un'applicazione "Hello World" Node.js di esempio, ma puoi effettuare invece il collegamento al tuo repository GitHub. Questa toolchain è preconfigurata per la fornitura continua con il Controllo vulnerabilità, il controllo dell'origine, il tracciamento del problema e la modifica online. <br><br>
  Prova l'esercitazione: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-toolchain" target="_blank">Use the "Develop a Kubernetes app" toolchain <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a>  
  <br><br>
  </td><td><ul><li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub e problemi
  </li><li>{{site.data.keyword.containerlong_notm}} (cluster Kubernetes)
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-helm-toolchain" target="_blank">"Develop a Kubernetes app with Helm" toolchain
   <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a> <br><br>

  Disponibile in Stati Uniti Sud, Stati Uniti Est, Germania, Tokyo e Regno Unito

  </td><td>
  Con questa toolchain, puoi sviluppare un'applicazione Docker e il relativo grafico Helm insieme nel controllo origine e crearla e distribuirla automaticamente a un cluster Kubernetes. La toolchain esegue gli smoke test prima di eseguire la creazione o la distribuzione e garantisce la privacy utilizzando un registro contenitore privato e spazi dei nomi per il registro contenitore e il cluster Kubernetes. Questa toolchain utilizza anche Controllo vulnerabilità per garantire che vengano distribuite solo immagini sicure. <br><br>
  Prova l'esercitazione: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-with-helm-toolchain" target="_blank">Use the "Develop a Kubernetes app with Helm" toolchain  <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a>	 <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>Git Repos and Issue Tracking
  </li><li>{{site.data.keyword.containerlong_notm}} (cluster Kurbernetes) con un grafico Helm
  </li></ul>
  </td></tr>
  
  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fmicroservices-helm-toolchain" target="_blank">Toolchain "Sviluppo e test dei microservizi su Kubernetes con Helm" <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a> <br><br>

  Disponibile in Stati Uniti Sud, Germania e Regno Unito

  </td><td>
  Con questa toolchain nativa del cloud, puoi utilizzare una combinazione di pipeline di integrazione continua e distribuzione continua per coordinare i microservizi sviluppati singolarmente in release promosse negli ambienti. Questa toolchain utilizza un'applicazione di negozio online di esempio che consiste in tre microservizi: una API Catalog, una API Orders e un'interfaccia utente che richiama entrambe. La toolchain è preconfigurata per la fornitura continua, il controllo dell'origine, la verifica della funzionalità, il tracciamento del problema, la modifica online e la notifica degli avvisi. <br><br>
  Prova l'esercitazione: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-with-kubernetes-and-helm-toolchain" target="_blank">Use the "Develop and test microservices with Kubernetes and Helm" toolchain  <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a>	 <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>Git Repos and Issue Tracking
  </li><li>{{site.data.keyword.DRA_full}}
  </li><li>PagerDuty
  </li><li>Sauce Labs
  </li><li>{{site.data.keyword.containerlong_notm}} (cluster Kurbernetes) con un grafico Helm
  </li></ul>
  </td></tr>
  
  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fcanary-testing-istio-toolchain" target="_blank">Toolchain "Test Canary in Kubernetes utilizzando Istio"
   <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a> <br><br>

  Disponibile in Stati Uniti Sud, Stati Uniti Est, Germania, Tokyo e Regno Unito

  </td><td>
  Con questa toolchain, puoi eseguire in modo protetto lo sviluppo, i test A/B e la distribuzione di un'applicazione in un cluster Kubernetes gestito da {{site.data.keyword.containerlong_notm}}. Anche se la toolchain utilizza, per impostazione predefinita, un'applicazione Node.js Hello World di esempio, puoi collegarti invece al tuo repository GitHub. Questa toolchain è preconfigurata per la fornitura continua con i test A/B, il Controllo vulnerabilità, il controllo dell'origine, il tracciamento del problema e la modifica online. <br><br>
  Prova l'esercitazione: <a href="https://www.ibm.com/cloud/garage/tutorials/use-canary-testing-in-kubernetes-using-istio-toolchain" target="_blank">Utilizza "Run your first canary test in Kubernetes using the Istio toolchain" <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a>	 <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>Git Repos and Issue Tracking
    </li><li>{{site.data.keyword.containerlong_notm}} (cluster Kurbernetes)
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdra-toolchain-demo" target="_blank">"Develop and test a Cloud Foundry app" toolchain
   <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a> <br><br>

  Disponibile in Stati Uniti Sud, Germania e Regno Unito

  </td><td>
  Utilizzando questa toolchain nativa per il cloud, puoi utilizzare DevOps Insights per controllare la distribuzione di una semplice applicazione Cloud Foundry. Per impostazione predefinita, la toolchain utilizza un'app meteo Node.js di esempio, ma puoi collegarti al tuo repository GitHub. La toolchain esegue i test di unità utilizzando Mocha e verifica la copertura del codice utilizzando Istanbul.<br><br>
  Prova l'esercitazione: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain" target="_blank">Use the "Develop and test a Cloud Foundry app" toolchain  <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a>  <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>Git Repos and Issue Tracking
  </li><li>{{site.data.keyword.DRA_full}}
  </li></ul>
  </td></tr>


  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fmicroservices-toolchain-hosted" target="_blank">
  Toolchain "Sviluppa e verifica i microservizi su" <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a> <br><br>

  Disponibile in Stati Uniti Sud, Germania e Regno Unito

  </td><td>
  Con questa toolchain nativa nel cloud, puoi utilizzare un esempio per creare un negozio online composto da tre microservizi: un'API Catalogo, un'API Ordini e una IU che richiama entrambe le API. La toolchain è preconfigurata per la fornitura continua, il controllo dell'origine, la verifica della funzionalità, il tracciamento del problema, la modifica online e la notifica degli avvisi. <br><br>
  Prova questa esercitazione: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain" target="_blank">Use the "Develop and test microservices on Cloud Foundry" toolchain <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a><br><br>
  </td><td>
  <ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub e problemi
  </li><li>{{site.data.keyword.Bluemix_notm}}
  </li><li>{{site.data.keyword.DRA_full}}
  </li><li>PagerDuty
  </li><li>Sauce Labs
  </li><li>Slack
  </li></ul>
 </td>
</tr>

  <tr>
  <td><a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fcloud-native-toolchain-tutorial" target="_blank">
Toolchain "Esercitazione di Garage Method con Cloud Foundry" <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a> <br><br>

  Disponibile in Stati Uniti Sud, Stati Uniti Est, Germania, Tokyo e Regno Unito

</td><td>
Questa toolchain illustra le procedure DevOps offerte nel metodo Garage. La toolchain è preconfigurata per la fornitura continua, il controllo dell'origine, l'automazione del test e per le operazioni e il monitoraggio automatizzati. Viene fornita con un'applicazione di esempio scritta in Node.js Express 4, che puoi ulteriormente espandere. <br><br>Prova il corso: <a href="https://www.ibm.com/cloud/garage/content/course/gm_advocate" target="_blank">Become a Garage Method advocate <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a>
</td><td>
<ul>
<li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion {{site.data.keyword.webide}}
</li><li>GitHub e problemi
</li><li>Google Analytics
</li><li>{{site.data.keyword.Bluemix_notm}}
</li><li>New Relic
</li><li>PagerDuty
</li><li>Sauce Labs
</li><li>Slack
</li></ul>
</td></tr>

<tr><td>
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fdevops-insights%2FDevOpsInsights_Demo_Toolchain_Template" target="_blank">Toolchain di "demo di introduzione rapida a DevOps Insights" <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a> <br><br>

  Disponibile in Stati Uniti Sud, Germania e Regno Unito

</td><td>
Con questa toolchain, puoi esplorare {{site.data.keyword.DRA_short}} senza che sia necessaria alcuna configurazione. Per iniziare, esegui l'accesso a {{site.data.keyword.Bluemix}}. Questa demo contiene i dati da una toolchain di riferimento e tre repository GitHub. Esplora come organizzare, testare, creare e distribuire dati per tutte le applicazioni, da tutti i team, all'interno del dashboard della qualità. Valuta le tendenze e capisci quali sono le aree che hanno bisogno di miglioramenti in modo da sapere dove devi concentrare le tue risorse. Esamina in che modo i membri del team collaborano per ogni release all'interno di Team Dynamics.<br><br>
Prova questa esercitazione: <a href="https://www.ibm.com/cloud/garage/tutorials/explore-ibm-cloud-devops-insights" target="_blank">Explore {{site.data.keyword.DRA_full}} <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a> <br><br>
</td><td><ul><li>
GitHub e problemi
</li><li>{{site.data.keyword.DRA_full}}
</li></ul>
</td></tr>

<tr><td>
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fempty-toolchain" target="_blank">Build your own toolchain <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a> <br><br>

  Disponibile in Stati Uniti Sud, Stati Uniti Est, Germania, Tokyo e Regno Unito

</td><td>
Questa toolchain non ha strumenti preconfigurati. Se hai già familiarità con le toolchain, puoi configurare la tua propria toolchain. <br><br>
Prova l'esercitazione: <a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">Create a custom toolchain  <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a>
</td><td> &nbsp;&nbsp; Nessuno
</td></tr>

<tr><td>Toolchain Continuous Delivery <br><br>

 Disponibile in Stati Uniti Sud, Stati Uniti Est, Germania, Tokyo e Regno Unito

</td><td>
Questa toolchain è utilizzata quando si abilita la fornitura continua per un'applicazione. <br><br>
Prova le esercitazioni:

<ul><li><a href="https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app" target="_blank">Add a toolchain to an app <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a></li>
<li><a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">Create a custom toolchain <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a></li>
</ul></td>
<td><ul><li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion {{site.data.keyword.webide}}
</li><li>
GitHub e problemi
</li>
<li>{{site.data.keyword.Bluemix_notm}}</li></ul>
</td></tr>

<tr><td>Template di toolchain personalizzata <br><br>

 Disponibile in Stati Uniti Sud, Stati Uniti Est, Germania, Tokyo e Regno Unito

</td><td>
<br><br>
Puoi creare un template di toolchain personalizzata che può essere utilizzato da altri. <br><br>

Vedi la documentazione:
<a href="https://github.com/open-toolchain/sdk/wiki" target="_blank">Creazione di template di toolchain personalizzate <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a>
 <br><br>
Prova questa esercitazione:
<a href="https://www.ibm.com/cloud/garage/tutorials/create-a-template-for-a-custom-toolchain" target="_blank">Create a template for a custom toolchain <img src="../../icons/launch-glyph.svg" alt="Icona link esterno"></a></td>
<td>Nessuno
</td></tr>

</table>
