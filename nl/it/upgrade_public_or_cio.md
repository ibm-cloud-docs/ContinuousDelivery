---

copyright:
  years: 2015, 2018
lastupdated: "2018-3-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Upgrade dei progetti riservati di IBM alle toolchain 
{: #upgrade_public_or_cio}

{{site.data.keyword.jazzhub}} si sta trasformando in {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.contdelivery_short}}. Come parte di tale cambiamento, i progetti saranno aggiornati in toolchain.

Quando il tuo progetto è pronto per l'upgrade, viene visualizzato un messaggio nella relativa pagina di panoramica. Puoi quindi eseguire l'upgrade del progetto a una toolchain su {{site.data.keyword.Bluemix_notm}} Pubblico. La toolchain includerà un repository (repo) Whitewater {{site.data.keyword.ghe_short}} per il tuo codice sorgente. Whitewater {{site.data.keyword.ghe_short}} viene fornito ai team IBM per promuovere e abilitare il social coding in IBM. 
{: shortdesc}

Le toolchain **{{site.data.keyword.contdelivery_short}} sono approvate per il materiale riservato di IBM quando vengono utilizzate con Whitewater {{site.data.keyword.ghe_short}}.** Le Delivery Pipeline che ricevono input dai repository Whitewater {{site.data.keyword.ghe_short}} possono eseguire la distribuzione agli ambienti di preparazione (YS1) e a quelli pubblici (YP).

Durante l'upgrade, ti verrà richiesto di autorizzare {{site.data.keyword.contdelivery_short}} ad accedere a Whitewater {{site.data.keyword.ghe_short}} per tuo conto.

## Aggiunta di membri al tuo repository Whitewater {{site.data.keyword.ghe_short}} dopo l'upgrade

Se il tuo progetto utilizza un repository ospitato su JazzHub, durante l'upgrade viene creato un nuovo repository in Whitewater {{site.data.keyword.ghe_short}}. Dopo l'upgrade, l'utente che lo ha avviato deve aggiungere i membri del team al repository Whitewater {{site.data.keyword.ghe_short}} e assicurarsi che dispongano dei privilegi corretti prima che possano accedere al nuovo repository.

## Risoluzione dei problemi

A volte si verifica un problema intermittente quando provi a modificare la destinazione di una fase di distribuzione della pipeline. Quando si verifica questo problema, viene visualizzato un errore nei campi **Organizzazione** e **Spazio**.

Questo problema di norma si verifica solo quando modifichi la destinazione dalla pipeline in modo che la pipeline creata durante l'upgrade verrà distribuita correttamente alle stesse destinazioni come faceva in precedenza.

Se provi a modificare la destinazione e si verifica questo problema, passa da una destinazione all'altra diverse volte finché i campi **Organizzazione** e **Spazio** non verranno completati.

Un problema correlato causa occasionalmente il malfunzionamento delle distribuzioni alle destinazioni YS1. Questa situazione è rara; se si verifica, esegui nuovamente la pipeline.

Il team IBM DevOps Services si sta attivamente adoperando per risolvere questi problemi.
