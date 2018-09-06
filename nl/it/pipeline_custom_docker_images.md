---

Copyright:
  years: 2018
lastupdated: "2018-8-2"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# Utilizzo di immagini docker personalizzate
{: #custom_docker_images}

L'immagine di base della pipeline potrebbe non supportare tutti i requisiti della tua build. Ad esempio, potresti avere bisogno di un controllo più dettagliato sulle versioni di nodo, java, o altri strumenti. Puoi risolvere questo problema includendo un primo passo nei tuoi lavori della pipeline che installa una serie di nuovi pacchetti e configura attentamente le variabili di ambiente, come ad esempio `PATH`, per configurare il tuo ambiente. Tuttavia, un approccio migliore consiste nell'utilizzare il supporto della pipeline per eseguire una"immagine Docker personalizzata" come base per il tuo lavoro.

Indipendentemente dal fatto che tu stia utilizzando un tipo di lavoro di build, test o distribuzione, puoi selezionare un sottotipo di immagine Docker personalizzata per fornire il nome dell'immagine Docker da utilizzare e specificare gli script da eseguire. Usa, ad esempio, le seguenti opzioni per eseguire un lavoro di build con Maven 3.5.3 e IBM Java:

 ![Build Maven con immagine personalizzata](images/custom-image-maven-build.png)


## Specifica del nome dell'immagine Docker
{: #docker_image_name}

Il nome dell'immagine Docker nei lavori dell'immagine Docker personalizzata è progettato per funzionare nello stesso modo in cui funzionano i nomi immagine con la CLI Docker. Il formato di un nome di immagine Docker è: `[repository][:][tag]`. Ad esempio, per `docker run maven:3.5.3-ibmjava`, il nome di immagine Docker è `maven:3.5.3-ibmjava`, dove `maven` è il repository e `3.5.3-ibmjava` è la tag. Non ci sono limitazioni sul nome di immagine Docker che puoi utilizzare; funziona qualsiasi immagine Docker valida.

Se il campo **Docker image name** non viene completato, viene utilizzata l'immagine di base della pipeline standard.
{: tip}

Per impostazione predefinita, viene eseguita una ricerca nel tuo repository su [Docker Hub ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://hub.docker.com/){: new_window}. Se utilizzi un altro registro Docker, come ad esempio IBM Cloud Registry, puoi utilizzare il nome DNS completo. Puoi anche utilizzare il nome completo per le immagini su Docker Hub. Ad esempio, `registry.hub.docker.com/library/maven:3.5.3-ibmjava`.

La `tag` per un'immagine Docker è facoltativa. Se non specifichi una tag, viene automaticamente impostata su `latest`. Un valore predefinito `latest` è solo un nome di tag che il proprietario del repository deve gestire. Non significa che, cronologicamente parlando, questa immagine Docker sia quella più recente.

Puoi trovare una grande community di repository in Docker Hub. IBM ospita diversi repository pubblici che il team IBM Cloud utilizza all'indirizzo [https://hub.docker.com/u/ibmcom/ ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://hub.docker.com/u/ibmcom/){: new_window}. I repository `ibmcom/ibmjava` e `ibmcom/ibmnode` sono utili come base su cui creare. 

## Utilizzo di un registro di immagini privato
{: #private_image_registry}

Se stai utilizzando un registro privato che richiede l'autenticazione, devi impostare due proprietà dell'ambiente della fase supplementari: `DOCKER_USERNAME` e `DOCKER_PASSWORD`. Puoi utilizzare una proprietà sicura per mascherare la tua `DOCKER_PASSWORD`. Prima che la tua immagine venga estratta, il lavoro dell'immagine Docker personalizzata utilizza le tue credenziali di nome utente e password per completare un `docker login`.

Per la maggior parte dei registri, puoi utilizzare il nome utente e la password che ti sono stati forniti. Se utilizzi IBM Cloud Registry per archiviare le tue immagini private, devi utilizzare una chiave API della piattaforma per l'autenticazione. 

1. [Richiedi una chiave API della piattaforma ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/iam/#/apikeys){: new_window} e assicurati di salvare la chiave. 
1. Crea le due proprietà dell'ambiente della fase utilizzando `iamapikey` per il tuo `DOCKER_USERNAME` e la chiave API della piattaforma che hai salvato per la `DOCKER_PASSWORD`.

 ![Credenziali di IBM Cloud Registry](images/custom-image-private-repository.png)


## Specifica dello script
{: #specify_script}

Puoi utilizzare il blocco **script** nei lavori di immagine Docker personalizzata per creare un file di script che viene eseguito un una cartella attività, simile a come funzionano i normali lavori della pipeline. 

`ENTRYPOINT` e `CMD` dal Dockerfile della tua immagine Docker vengono sovrascritti e non vengono richiamati. In alcuni casi, questo potrebbe significare che devi aggiungere dei passi di inizializzazione al tuo script.
{: tip}

I lavori di immagine Docker personalizzata ti offrono una maggiore flessibilità per quanto riguarda la modalità di esecuzione del tuo script; specificamente, puoi controllare l'interprete dei comandi. Di norma, se la prima riga dello script inizia con `#!` e il nome di un interprete di comandi, tale voce viene utilizzata per eseguire i comandi nel lavoro. Se non specifichi un interprete dei comandi, viene utilizzata la shell predefinita per l'immagine Docker. Di norma, vengono utilizzati `#!/bin/bash` o `#!/bin/sh`; funzionano anche gli interpreti dei comandi immagine per `awk`, `node` e `ruby`, se specifichi un'immagine Docker appropriata.
