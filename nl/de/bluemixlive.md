---



copyright:
  years: 2015，2019
lastupdated: "2019-2-1"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# {{site.data.keyword.Bluemix_notm}} Live Sync
{: #live-sync}


Wenn Sie eine Node.js-Anwendung erstellen, können Sie {{site.data.keyword.Bluemix}} Live Sync verwenden, um die Anwendungsinstanz unter {{site.data.keyword.Bluemix_notm}} rasch zu aktualisieren und Entwicklungsarbeiten ohne manuelle Neubereitstellung auszuführen.   
{: shortdesc}

Wenn Sie eine Änderung vornehmen, ist diese Änderung sofort in Ihrer aktiven {{site.data.keyword.Bluemix_notm}}-Anwendung sichtbar. {{site.data.keyword.Bluemix_notm}} Live Sync wird
<!--from both the command line and -->
in der Eclipse Orion-Web-IDE (Web-IDE) ausgeführt. Sie können Anwendungen debuggen, die in Node.js geschrieben werden, indem Sie {{site.data.keyword.Bluemix_notm}} Live Sync verwenden.  

{{site.data.keyword.Bluemix_notm}} Live Sync setzt sich aus zwei Features zusammen.
<!--three -->

<!--
**Desktop Sync**  

You can synchronize any desktop directory tree with a cloud-based project workspace similar to the way Dropbox works. The Web IDE directly edits the same cloud-based workspace, so both stay in sync. Desktop Sync works for any kind of application. To use Desktop Sync, you need to download and install the BL command line interface.  
-->

**Live Edit**

Sie können eine Node.js-Anwendung, die unter {{site.data.keyword.Bluemix_notm}} ausgeführt wird, bearbeiten und direkt in Ihrem Browser testen. Alle Änderungen, die Sie in der Web-IDE vornehmen, werden umgehend an das Dateisystem der Anwendung weitergegeben.  

**Debug**  

Während sich eine Node.js-Anwendung im Modus 'Live Edit' befindet, können Sie sie mit der Shell aufrufen und debuggen. Mit dem Debugger 'Node Inspector' können Sie Code dynamisch bearbeiten, Unterbrechungspunkte einfügen, Code schrittweise durchgehen, die Laufzeit erneut starten usw.  


##Live Edit
{: #live-edit}

Wenn Sie eine Node.js-Anwendung erstellen, die unter {{site.data.keyword.Bluemix_notm}} ausgeführt wird, kann das Live Edit-Feature von {{site.data.keyword.Bluemix_notm}} Live Sync die Anwendungsinstanz schnell aktualisieren. Live Edit steht nur in der Web-IDE zur Verfügung. Mithilfe von Live Edit können Sie Entwicklungsprozesse wie auf dem Desktop durchführen, ohne dass eine erneute Bereitstellung erforderlich ist.

Live Edit wird nur für Node.js-Anwendungen unterstützt.

Klicken Sie in der Eclipse Orion-Web-IDE (Web-IDE) in der Ausführungsleiste auf **Live Edit**.

![Abbildung der Ausführungsleiste mit Live Edit](images/bluemix-live-sync-light.png)

Mit Live Edit erhalten Sie in kürzester Zeit eine Vorschau der Änderungen an Node.js-Anwendungen, die unter {{site.data.keyword.Bluemix_notm}} ausgeführt werden. Wenn Sie den Code bei aktiviertem Live Edit-Feature ändern, können Sie das Browserfenster Ihrer Webanwendung aktualisieren und die vorgenommenen Änderungen sind wenige Sekunden später sichtbar.

Ein Lernprogramm zur Verwendung der Live Edit-Funktion von {{site.data.keyword.Bluemix_notm}} Live Sync finden Sie in [{{site.data.keyword.Bluemix_notm}} Live Sync zum Entwickeln, Debuggen und Bereitstellen Ihrer App verwenden ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/cloud/garage/tutorials/use-live-sync-to-develop-debug-and-deploy-your-app){:new_window}.

Wenn Sie die Dateien in Ihrer Web-IDE ändern, werden sie automatisch für Ihre Anwendungsinstanz unter {{site.data.keyword.Bluemix_notm}} neu bereitgestellt. Wenn Sie die Node-Anwendung erneut starten müssen, klicken Sie in der Ausführungsleiste auf die Schaltfläche **Erneut starten**.

Für ein möglichst konsistentes Verarbeitungsverhalten bei Verwendung des Live Edit-Features von {{site.data.keyword.Bluemix_notm}} Live Sync ist eine zusätzliche Speicherkapazität von 256 MB erforderlich und wird hinzugefügt.
{: tip}

## {{site.data.keyword.Bluemix_notm}} Live Debug
{: #live-debug}

{{site.data.keyword.Bluemix_notm}} Live Sync Debug verwendet [Node Inspector ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/node-inspector/node-inspector){:new_window}, um Debug-Features zur Verfügung zustellen. Sie müssen Version 4 von Node verwenden, damit der Debugger zur Verfügung steht, da spätere Versionen von Node.js den Node Inspector nicht enthalten.

Sie können auf {{site.data.keyword.Bluemix_notm}} Live Debug zugreifen, wenn {{site.data.keyword.Bluemix_notm}} Live Edit für Ihre Node.js-App aktiviert ist.  

Mit dem Debug-Feature können Sie Code dynamisch bearbeiten, Unterbrechungspunkte einfügen, Code schrittweise durchgehen, die Laufzeit erneut starten usw., während Ihre App unter {{site.data.keyword.Bluemix_notm}} ausgeführt wird. Sie können Ihre App Schritt für Schritt flexibel entwickeln und dabei aus der umfangreichen Liste von {{site.data.keyword.Bluemix_notm}}-Services die für Sie geeigneten auswählen.

{{site.data.keyword.Bluemix_notm}} Live Debug umfasst die folgenden Features:

* Anwendungslaufzeitsteuerung
* Debugging unter Verwendung von [Node Inspector ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/node-inspector/node-inspector){:new_window}
* Shell-Zugriff

### Anwendungslaufzeitsteuerung {: #app-runtime}

Bei der Anwendungslaufzeitsteuerung können Sie das Debugging-Feature verwenden, um den Status der App beim Start zu überprüfen. Diese Funktion unterstützt Sie bei der Fehlerbehebung, wenn eine App beim Starten fehlschlägt.

Bei der Entwicklung Ihrer App können Sie eine der folgenden Aktionen auswählen:

* Ausführen eines schnellen Neustarts Ihrer App
* Aussetzen der App, bevor App-Code ausgeführt wird

Wenn Sie sich angemeldet haben, wird die {{site.data.keyword.Bluemix_notm}} Live Debug-Seite geöffnet.

### Debugging {: #debug}

**Voraussetzung:** Google Chrome und Node 4 sind erforderlich.

Das Debugging-Feature bietet folgende Funktionalität:  
* Festlegen von Unterbrechungspunkten im App-Code, um die Ausführung in einer bestimmten Zeile anzuhalten.
  Unterbrechungspunkte werden nicht im Hauptprogramm, sondern in den Einstiegspunkten unterstützt.
  {: tip}
* Bearbeiten von Unterbrechungspunktbedingungen, um die Ausführung nur dann anzuhalten, wenn bestimmte Kriterien erfüllt sind.
* Überprüfen des Status lokaler Variablen und Felder.
* Sofortiges Anzeigen der Debugausgabe von `console.log()`-Aufrufen. Diese Aktion ist schneller als das Überwachen von cf-Protokollen.
* Verwenden des integrierten Quellcodeeditors, um sofortige, aber temporäre Änderungen am aktiven App-Code vorzunehmen.

### Shell {: #shell}

Mit diesem Tool erhalten Sie Shellzugriff auf den Container, in dem Ihre App ausgeführt wird. Mithilfe dieses Terminals können Sie Shelldiagnosebefehle über Fernzugriff ausführen, um Ihre App zu verwalten. Alle Versionen von Node.js unterstützen das Shell-Feature.

Sie können die Speicher- und CPU-Auslastung in der Instanz überwachen, die Linux-Standardbefehle wie **top**, **ps** und **kill** verwendet.

### App zur Aktivierung von {{site.data.keyword.Bluemix_notm}} Live Debug konfigurieren {: #configure_app_debug}

1. Der {{site.data.keyword.Bluemix_notm}} Live Debugger verwendet Node Inspector. Sie müssen Node Version 4 verwenden. Außerdem müssen Sie es dem Buildpack ermöglichen, den App-Startbefehl zu erkennen. Der Startbefehl muss automatisch vom Buildpack erkannt werden, er darf nicht in der Datei 'manifest.yml' eingestellt werden.

   Im Folgenden wird eine Datei `package.json` gezeigt, die {{site.data.keyword.Bluemix_notm}} Live Debug unterstützt:

  ```
  {
      "scripts": {
         "start": "node app.js"
      },
      "engines": {
         "node": "4"
      }
  }
  ```

2. Vergrößern Sie den Speicher.  

    a. Fügen Sie in der Datei `manifest.yml` der App 128 MB oder mehr zu dem Wert hinzu, der für das Speicherattribut angegeben ist.

Wenn {{site.data.keyword.Bluemix_notm}} Live Debug installiert wurde, können Sie die Debug-Tools verwenden.

Übertragen Sie die App per Push-Operation und navigieren Sie anschließend zu `https://_app-host.mybluemix.net_/bluemix-debug/manage`, um auf die {{site.data.keyword.Bluemix_notm}}-Debug-Benutzerschnittstelle zuzugreifen. Wenn Sie zur Authentifizierung aufgefordert werden, geben Sie Ihren IBM ID-Benutzernamen und das Kennwort oder einen Einmalkenncode ein.    

Es kann etwa eine Minute dauern, bis der Debugger initialisiert ist.
{: tip}

### App-Konfigurationen wiederherstellen und {{site.data.keyword.Bluemix_notm}} Live Debug inaktivieren {: #restore_live_debug}

1. Stellen Sie die ursprüngliche Node.js-Version, den Startbefehl und Speicherwert der App wieder her.

2. Übertragen Sie die App per Push-Operation.
