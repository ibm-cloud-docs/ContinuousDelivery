---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: IBM Cloud Continuous Delivery, private workers integration

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


# Gestione dei nodi di lavoro privati {{site.data.keyword.deliverypipeline}}
{: #private-workers}

La {{site.data.keyword.deliverypipeline}} utilizza i nodi di lavoro pubblici e privati per eseguire i lavori di pipeline. Per impostazione predefinita, i lavori di pipeline vengono eseguiti utilizzando i nodi di lavoro pubblici sull'infrastruttura condivisa pubblica gestita da IBM.
{: shortdesc}

In alcuni scenari, la tua {{site.data.keyword.deliverypipeline}} potrebbe richiedere 'accesso a risorse interne o in loco. In queste situazioni, puoi connetterti a, e integrare, un nodo di lavoro privato {{site.data.keyword.deliverypipeline}} per l'esecuzione sulla tua infrastruttura Kubernetes.

## Prerequisiti
{: #private_workers_prereqs}

Prima di impostare un nodo di lavoro privato, assicurati di avere le seguenti risorse correttamente posizionate:

* Un cluster Kubernetes. Devi disporre di un cluster per installare un nodo di lavoro privato. Puoi fornire un tuo cluster oppure puoi [impostare un cluster](https://cloud.ibm.com/kubernetes/clusters){:external} da {{site.data.keyword.containerlong_notm}}.

* Una toolchain con una pipeline che contiene almeno una fase. Puoi utilizzare una toolchain esistente o [creare una toolchain](https://cloud.ibm.com/devops/create){:external}.

## Impostazione di un nodo di lavoro privato {{site.data.keyword.deliverypipeline}}
{: #set_up_private_worker}

Per impostare un nodo di lavoro privato, completa la seguente procedura:

1. Configura l'integrazione dello strumento di nodo di lavoro privato {{site.data.keyword.deliverypipeline}} per la tua toolchain.
2. Configura il tuo cluster Kubernetes con un nodo di lavoro privato.
3. Utilizza il nodo di lavoro privato nella tua pipeline.

### Configurazione dell'integrazione dello strumento di nodo di lavoro privato {{site.data.keyword.deliverypipeline}}
{: #configure_private_worker_integration}

Completa la seguente procedura per configurare l'integrazione dello strumento di nodo di lavoro privato {{site.data.keyword.deliverypipeline}} per la tua toolchain:

1. Se stai configurando questa integrazione dello strumento mentre stai creando la toolchain, nella sezione Configurable Integrations, fai clic su **{{site.data.keyword.deliverypipeline}} Private Worker**.
1. Se disponi di una toolchain a cui stai aggiungendo questa integrazione dello strumento, nella pagina Toolchains del dashboard DevOps, fai clic sulla toolchain per aprirne la pagina della panoramica. In alternativa, nella tua pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e su **Overview**.

 a. Fai clic su **Add a Tool**.

 b. Nella sezione Tool Integrations, fai clic su **{{site.data.keyword.deliverypipeline}} Private Worker**.

1. Immetti un nome per l'integrazione dello strumento. Questo nome identifica un pool di nodi di lavoro privati nella scheda **Workers** della fase della pipeline.
1. Immetti la tua chiave API di ID servizio per autenticare l'accesso alla coda di lavoro dove uno o più nodi di lavoro privati possono cercare del lavoro. Se non hai una chiave API di ID servizio, fai clic su **Create** per generarne una per questo nodo di lavoro privato.
1. Fai clic su **Create Integration**.
1. Dalla tua toolchain, fai clic su **{{site.data.keyword.deliverypipeline}} Private Worker** per visualizzare un elenco di tutti i nodi di lavoro che sono registrati utilizzando una chiave API associata a questo ID servizio.

Per ulteriori informazioni sull'integrazione dello strumento di **nodo di lavoro privato {{site.data.keyword.deliverypipeline}}**, vedi [Configurazione del nodo di lavoro privato {{site.data.keyword.deliverypipeline}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations#privateworker).

### Configurazione del cluster Kubernetes
{: #configure_kubernetes_cluster}

Configura il tuo cluster Kubernetes con un nodo di lavoro privato:

1. Nel dashboard DevOps, nella pagina **Toolchain**, fai clic su una toolchain per aprirne la pagina Overview. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e quindi su **Overview**.
1. Fai clic sulla scheda per l'integrazione dello strumento di nodo di lavoro privato {{site.data.keyword.deliverypipeline}} che vuoi configurare.
1. Fai clic su **Getting Started** e attieniti quindi alla procedura per installare e registrare un nodo di lavoro privato sul tuo cluster Kubernetes.

### Utilizzo del nodo di lavoro privato {{site.data.keyword.deliverypipeline}} nella tua pipeline
{: #use_private_worker_pipeline}

Completa la seguente procedura per utilizzare il nodo di lavoro privato nella tua pipeline:

1. Nel dashboard DevOps, nella pagina **Toolchain**, fai clic su una toolchain per aprirne la pagina Overview. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e quindi su **Overview**.
1. Fai clic sulla scheda per la pipeline con cui vuoi utilizzare il nodo di lavoro privato.
1. Nella pagina Pipeline, sulla fase, fai clic sull'icona **Stage Configuration** e fai quindi clic su **Configure Stage**.
1. Fai clic sulla scheda **Workers**.
1. Seleziona il nodo di lavoro privato che vuoi utilizzare nella tua pipeline. 

 Per impostazione predefinita, i lavori in una fase della pipeline vengono eseguiti utilizzando un pool di nodi di lavoro condivisi gestiti da IBM nella regione dove è definita la pipeline.
 {: tip}
 
1. Fai clic su **Save**.
1. Puoi eseguire manualmente la tua fase oppure attendere che un trigger esegua i lavori nella fase utilizzando il nodo di lavoro privato specificato nel cluster Kubernetes associato. Puoi visualizzare l'output del file di log per i lavori per determinare quale nodo di lavoro è stato utilizzato.  


## Modifica delle credenziali dell'integrazione dello strumento di nodo di lavoro privato {{site.data.keyword.deliverypipeline}}
{: #modify_private_worker}

Dopo che hai impostato il tuo nodo di lavoro privato, puoi aggiornare le credenziali utilizzate per l'integrazione dello strumento. Potresti voler modificare queste credenziali se sono eliminate, scadute o compromesse. Puoi aggiornare le credenziali creando un nuovo ID servizio oppure aggiornando la chiave API.

### Creazione di un ID servizio
{: #create_service_id}

Per creare un ID servizio, completa la seguente procedura:

1. Nel dashboard DevOps, nella pagina **Toolchain**, fai clic su una toolchain per aprirne la pagina Overview. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e quindi su **Overview**.
1. Nella scheda per l'integrazione dello strumento di nodo di lavoro privato che vuoi modificare, fai clic sul menu per accedere alle opzioni di configurazione.
1. Fai clic su **Create**.
1. Immetti un nome e una descrizione per l'ID servizio.
1. Fai clic su **Save Integration**.
1. Nel dashboard DevOps, nella pagina **Toolchain**, fai clic su una toolchain per aprirne la pagina Overview. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e quindi su **Overview**.
1. Fai clic sulla scheda per l'integrazione dello strumento di nodo di lavoro privato {{site.data.keyword.deliverypipeline}} per cui vuoi specificare le nuove credenziali utente.
1. Fai clic su **Getting Started** e completa i passi 2 e 3 per registrare e verificare il nodo di lavoro privato sul tuo cluster.

### Aggiornamento della chiave API
{: #update_api_key}

Completa la seguente procedura per aggiornare la chiave API per l'utilizzo con l'integrazione dello strumento di nodo di lavoro privato {{site.data.keyword.deliverypipeline}}:

1. Nel dashboard DevOps, nella pagina **Toolchain**, fai clic su una toolchain per aprirne la pagina Overview. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e quindi su **Overview**.
1. Nella scheda per l'integrazione dello strumento di nodo di lavoro {{site.data.keyword.deliverypipeline}} che vuoi modificare, fai clic sul menu per accedere alle opzioni di configurazione.
1. Specifica la tua nuova chiave API. 
1. Fai clic su **Save Integration**.

## Eliminazione di un nodo di lavoro privato {{site.data.keyword.deliverypipeline}}
{: #delete_private_worker}

Per eliminare un nodo di lavoro privato, completa la seguente procedura:

1. Elimina il nodo di lavoro privato dal pool di nodi di lavoro.
1. Elimina il nodo di lavoro privato dal tuo cluster Kubernetes.

### Eliminazione di un nodo di lavoro privato {{site.data.keyword.deliverypipeline}} dal pool di nodi di lavoro

Per eliminare il nodo di lavoro privato dal pool di nodi di lavoro, completa la seguente procedura:

1. Nel dashboard DevOps, nella pagina **Toolchain**, fai clic su una toolchain per aprirne la pagina Overview. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e quindi su **Overview**.
1. Fai clic sulla scheda per l'integrazione dello strumento di nodo di lavoro privato {{site.data.keyword.deliverypipeline}} che vuoi configurare.
1. Fai clic su **Overview**.
1. Fai clic sul menu per il nodo di lavoro privato che vuoi eliminare per accedere alle opzioni di configurazione.
1. Fai clic su **Remove** e fai quindi clic su **Confirm**.

### Eliminazione di un nodo di lavoro privato {{site.data.keyword.deliverypipeline}} dal tuo cluster Kubernetes

Per eliminare il nodo di lavoro privato dal tuo cluster, completa la seguente procedura:

1. Fai clic sulla scheda per l'integrazione dello strumento di nodo di lavoro privato {{site.data.keyword.deliverypipeline}} che vuoi configurare.
1. Fai clic su **Getting Started** e attieniti alla procedura per eliminare il nodo di lavoro privato dal tuo cluster.

## Eliminazione dell'integrazione dello strumento di nodo di lavoro privato {{site.data.keyword.deliverypipeline}}
{: #delete_private_workers_tool_integration}

Se elimini l'integrazione dello strumento di nodo di lavoro privato {{site.data.keyword.deliverypipeline}} dalla tua toolchain, l'eliminazione non può essere annullata.
{: important}

Per eliminare un'integrazione dello strumento di nodo di lavoro privato {{site.data.keyword.deliverypipeline}}, completa la seguente procedura:

1. Nel dashboard DevOps, nella pagina **Toolchain**, fai clic su una toolchain per aprirne la pagina Overview. In alternativa, nella pagina della panoramica dell'applicazione, nella scheda di fornitura continua, fai clic su **View Toolchain** e quindi su **Overview**.
1. Nella scheda per l'integrazione dello strumento di nodo di lavoro privato {{site.data.keyword.deliverypipeline}} che vuoi eliminare, fai clic sul menu per accedere alle opzioni di configurazione.
1. Per eliminare l'integrazione dello strumento dalla tua toolchain, fai clic su **Delete**.
1. Conferma facendo clic su **Delete**. L'integrazione dello strumento di nodo di lavoro privato {{site.data.keyword.deliverypipeline}} viene rimossa dalla toolchain e non è più disponibile nella scheda **Workers** nella pagina Stage Configuration della delivery pipeline.

Se elimini l'integrazione dello strumento di nodo di lavoro privato {{site.data.keyword.deliverypipeline}} da una toolchain e il nodo di lavoro privato è configurato per una fase della pipeline, essa è ancora elencata nella scheda **Workers** della pagina Stage Configuration. Tuttavia, il nodo di lavoro privato è disabilitato ed etichettato come REMOVED. Devi selezionare un nodo di lavoro privato differente (se ne esiste uno) oppure utilizzare invece un nodo di lavoro pubblico.
{: tip}
