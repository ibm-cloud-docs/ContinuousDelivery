---

copyright:
  years: 2015, 2019
lastupdated: "2019-1-31"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Sviluppo con Eclipse Orion Web IDE
{: #web_ide}

Eclipse Orion {{site.data.keyword.webide}} è un ambiente di sviluppo basato sul browser dove puoi eseguire attività di sviluppo per il web in JavaScript, HTML e CSS con l'aiuto dell'assistenza del contenuto, del completamento del codice e del controllo errori. {{site.data.keyword.webide}} funziona con quasi tutti i linguaggi e puoi evidenziare la sintassi per la maggior parte dei tipi di file. Il controllo di origine è integrato e può distribuire il codice localmente per verificare ed eseguire il debug delle tue applicazioni.
{:shortdesc}

Cosa più importante, {{site.data.keyword.webide}} si avvale della tecnologia web. Non hai nulla da installare, da mantenere e da scalare. Puoi sviluppare ovunque tu abbia una connessione a internet.

Non archiviare i dati regolamentati in file all'interno di {{site.data.keyword.webide}}. Le procedure per i dati regolamentati non sono attualmente implementate.
{: tip}

## Configurazione dell'IDE
{: #editorsetup}

{{site.data.keyword.webide}} è personalizzabile in modo che puoi scegliere gli schemi di colori, gli strumenti tecnici e le impostazioni che incontrano i tuoi bisogni di sviluppo. Per visualizzare e modificare le impostazioni, dalla barra laterale di navigazione a sinistra, fai clic sull'icona **Impostazioni** <img class="inline" src="images/webide_settings_icon_light_small.png"  alt="Icona di impostazioni">.

Se durante la modifica hai la necessità di cambiare spesso le impostazioni, puoi accedere rapidamente a esse utilizzando l'icona **Impostazioni dell'editor locali** <img class="inline" src="images/webide_local_settings_icon_light_small.png"  alt="Icona Impostazioni dell'editor locali">.

![Impostazioni dell'editor locali](images/webide_local_editor_settings_light.png)

Per impostazione predefinita, le impostazioni per lo stile dell'editor e la dimensione del carattere vengono sempre visualizzate. Per includere altre impostazioni dell'editor nel menu, completa la seguente procedura:

1. Fai clic sull'icona **Impostazioni dell'editor locali** <img class="inline" src="images/webide_local_settings_icon_light_small.png"  alt="Icona Impostazioni dell'editor locali">.

2. Fai clic su **Impostazioni dell'editor**.

3. Per includere o escludere un'impostazione dal menu **Impostazioni dell'editor locali**, fai clic sulla stella per ciascuna impostazione.

![Attiva impostazioni dell'editor](images/webide_editor_settings_toggle_light.png)


## Modifica del codice
{: #editcode}

{{site.data.keyword.webide}} ha due sezioni principali. La prima sezione è il navigator dei file, che mostra i tuoi file del progetto in tre strutture. Dal navigator dei file, puoi creare, ridenominare, eliminare e gestire i tuoi file e cartelle.

Per caricare i file nel navigator dei file, trascinaceli dal tuo computer.
{: tip}

La seconda sezione è il pannello dell'editor. L'editor fornisce diverse funzioni di scrittura del codice, tra cui l'assistenza del contenuto e la convalida della sintassi.

![Web IDE](images/webide_light.png)

### Utilizzo di più file
1. Per lavorare con due file contemporaneamente, fai clic sull'icona **Modifica modalità di suddivisione editor** <img class="inline" src="images/webide_split_editor_icon_light_small.png"  alt="Icona Suddivisione editor">.
2. Dal menu che si apre, seleziona una vista.

 Dopo avere selezionato la vista, se era già stato aperto un file nell'editor, viene visualizzato in entrambe le viste dell'editor.

 Per aprire o modificare un file visualizzato in una delle due viste dell'editor:
 1. Sposta il cursore del mouse nella vista editor che desideri modificare.
 2. Nel navigator dei file, fai clic su un file.

### Tasti di scelta rapida
Molti dei comandi in {{site.data.keyword.webide}} sono accessibili tramite dei tasti di scelta rapida.

Per visualizzare un elenco dei tasti di scelta rapida nell'editor, fai clic su **Tools** > **Show keys**. In alternativa, puoi vedere l'elenco premendo Alt+Maiusc+? oppure Ctrl+Maiusc+? su MacOS. Puoi personalizzare una scelta rapida spostando il mouse sul tasto, facendo clic sulla matita e digitando la nuova associazione di tasti.

## Gestione del codice di origine
{: #sourcecontrol}

{{site.data.keyword.webide}} è integrata con gli strumenti di gestione del codice di origine. Per lavorare con il repository Git, fai clic sull'icona **Repository Git** <img class="inline" src="images/webide_git_icon_light_small.png"  alt="Icona Repository Git">.  Per ulteriori informazioni, consulta [Utilizzo di Git in Eclipse Orion Web ID](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_web_ide#git_web_ide).

## Distribuzione di un'applicazione dal tuo spazio di lavoro
{: #deploy}

1. Per distribuire la tua applicazione, dalla barra del menu, seleziona o crea una configurazione di avvio.
   ![Barra di esecuzione](images/webide_runbar_light.png)   
1. Fai clic sull'icona di distribuzione <img class="inline" src="images/webide_deploy_button_light_small.png"  alt="Icona di distribuzione">. Viene distribuita un'istanza alla tua applicazione utilizzando i contenuti correnti del tuo spazio di lavoro e l'ambiente definito nella tua configurazione di avvio.
2. Dopo che la tua applicazione è stata distribuita, puoi utilizzare la barra di esecuzione per arrestare, riavviare o eseguire il debug della applicazione, dei log di visualizzazione o di altro.

<table role="presentation">
<tr><td><img src="./images/stop_button.png"  alt="Icona di arresto"></td><td>Arresta l'applicazione.</td></tr>
<tr><td> <img src="./images/open_app_url.png"  alt="Icona dell'URL di apertura dell'applicazione"></td><td> Apri l'applicazione distribuita.</td></tr>
<tr><td><img src="./images/view_logs.png"  alt="Icona di visualizzazione dei log"></td><td>Visualizza i log dell'applicazione distribuita.</td></tr>
<tr><td><img src="./images/open_dashboard.png"  alt="Icona di apertura del dashboard"></td><td>Apri il dashboard dell'applicazione.</td></tr>
</table>

Se stai sviluppando un'applicazione Node.js, abilita la modalità Live Edit:  <img  src="./images/enable_live_edit.png"  alt="Dispositivo a scorrimento di abilitazione di live edit">

<table role="presentation"><tr><td><img src="./images/live_edit_restart.png"  alt="Icona di riavvio di Live Edit"></td><td>Con la modalità Live Edit abilitata, riavvia l'applicazione rapidamente, senza rieseguire la distribuzione</td></tr>
<tr><td> <img src="./images/debug_icon.png"  alt="Icona di debug"></td>
<td>Con la modalità Live Edit abilitata, accedi al debugger.
</td></tr>
</table>

<!-- 3/6/2016: bl commands don't work with V2/CD
## Editing outside of the {{site.data.keyword.webide}}
{: #editlocal}

To use an editor besides the {{site.data.keyword.webide}}, set up {{site.data.keyword.Bluemix_live}} so that you can work directly with your project files in any tool. {{site.data.keyword.Bluemix_live_notm}} is a command-line application that synchronizes the changes in your local file system with your cloud workspace in {{site.data.keyword.Bluemix_short}}.

### Before you begin

Download and install the [{{site.data.keyword.Bluemix_live_notm}} command-line interface ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://livesyncdownload.ng.bluemix.net){: new_window}.

### Synchronizing your local environment with {{site.data.keyword.Bluemix_notm}}
{: #edit_local_download}

1. Open a command-line window.
2. Sign in to {{site.data.keyword.Bluemix_notm}}:

	```
	bl login
	```
	{: pre}

3. When you are prompted, enter your IBMid and password.
4. View a list of your {{site.data.keyword.Bluemix_notm}} projects:

	```
	bl projects
	```
	{: pre}

4. Synchronize your local environment with your project on {{site.data.keyword.Bluemix_notm}}:

	```
	bl sync projectName
	```
	{: pre}

where `projectName` is your {{site.data.keyword.Bluemix_notm}} app's name.

When you are finished editing, enter `q` to end synchronization.

### Enabling the Desktop Sync feature to edit code locally

The Desktop Sync feature is like Live Edit mode for the command line. You need the Desktop Sync feature to debug on the command line.
1. In another command-line window, enable the Desktop Sync feature:

	```
	cd localDirectory
	bl start
	```
	{: codeblock}

2. Use the launch configuration that you created in the {{site.data.keyword.webide}}. After you select the launch configuration, the Desktop Sync feature is enabled in your local environment. In the command-line window that you just opened, you can view the app's URL, the debug URL, the manage URL, and view the {{site.data.keyword.Bluemix_live_notm}} state.

3. Refresh the browser and verify that you can see the changes that you saved to static files in the local workspace.

### Disabling the Desktop Sync feature

1. In the second command-line window, enter `bl stop`.
2. In the first command-line window, enter `q`.

-->

## Linguaggi supportati
{: #supported_languages}

Eclipse Orion {{site.data.keyword.webide}} fornisce assistenza del contenuto, descrizioni a comparsa, anteprime e convalida ed evidenzia la sintassi per i file JavaScript, HTML, CSS e Markdown. Puoi anche evidenziare la sintassi per questi tipi di file:

<table role="presentation">
<tr>
<td>
<ul><li>Arduino
</li><li>C</li>
<li>C#
</li><li>C++
</li><li>CoffeeScript
</li><li>CSHTML
</li><li>Embedded JavaScript (ejs)
</li><li>Erlang
</li><li>Go
</li><li>Haml (HTML abstraction markup language)
</li><li>Jade
</li><li>Java
</li><li>JSON
</li><li>Less  
</li><li>Lua  
</li><li>Objective-C
</li><li>PHP
</li><li>Python</li></ul>
</td>
<td>
<ul><li>Ruby
</li><li>Sass/SCSS
</li><li>SQL
</li><li>Swift
</li><li>TypeScript
</li><li>vb (Visual Basic)
</li><li>VMHTML
</li><li>XHTML
</li><li>XML
</li><li>XQuery
</li><li>YAML
</li><li>File di avvio 	
</li><li>Dockerfile
</li><li>gitignore
</li><li>git config
</li><li>cfignore
</li><li>proprietà
</li></ul>
</td>
</tr>
</table>

## Visualizza una esercitazione: Eclipse Orion Web IDE
{: #toolchain_web_ide_tutorials}

Guarda una di queste esercitazioni su [IBM&reg; Cloud Garage Method ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage){:new_window}:

  * [Crea e utilizza la tua prima toolchain utilizzando la toolchain "Develop a Cloud Foundry app" ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}.

  * [Use the "Develop and test microservices on Cloud Foundry" toolchain ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}.
