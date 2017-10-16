---

copyright:
  years: 2015, 2017
lastupdated: "2017-5-25"

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Fehlerbehebung für {{site.data.keyword.contdelivery_short}}
{: #ts_cd}

Hier erhalten Sie Antworten auf allgemeine Fragen zur Fehlerbehebung im Zusammenhang mit der Verwendung von {{site.data.keyword.contdelivery_full}}.
{:shortdesc}


## Autorisierung mit GitHub nicht möglich
{: #cannot_authorize_github}

Sie sind nicht mit GitHub autorisiert.
{:shortdesc}

Wenn {{site.data.keyword.Bluemix_notm}} nicht für den Zugriff auf Ihr GitHub-Konto autorisiert ist, kann eines der folgenden Probleme auftreten:
{: tsSymptoms}

 * Bei dem Versuch, die GitHub-Toolintegration zu Ihrer Toolchain hinzuzufügen, wird die Toolintegration nicht hinzugefügt.
 * Die Pipeline wird nicht automatisch ausgeführt (ausgelöst), wenn Sie Änderungen per Push-Operation an Ihr GitHub- oder GitHub Enterprise-Repository übertragen.

{{site.data.keyword.Bluemix_notm}} ist nicht für den Zugriff auf GitHub autorisiert.  
{: tsCauses}

Wenn Sie die GitHub-Toolintegration konfigurieren, während Sie die Toolchain erstellen, gehen Sie dabei anhand der folgenden Schritte vor:
{: tsResolve}

  1. Klicken Sie im Abschnitt mit den konfigurierbaren Integrationen auf **GitHub**.
  1. Wenn Sie die Toolchain unter {{site.data.keyword.Bluemix_notm}} Public erstellen und {{site.data.keyword.Bluemix_notm}} nicht für den Zugriff auf GitHub autorisiert ist, klicken Sie auf **Autorisieren**, um zur GitHub-Website zu wechseln.
  1. Wenn keine aktive GitHub-Sitzung existiert, werden Sie aufgefordert, sich anzumelden. Klicken Sie auf **Anwendung autorisieren**, um {{site.data.keyword.Bluemix_notm}} den Zugriff auf Ihr GitHub-Konto zu erlauben.

Wenn Sie bereits über eine Toolchain verfügen, aktualisieren Sie die Konfiguration der GitHub-Toolintegration wie folgt:

 1. Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf die Toolchain, um die zugehörige Übersichtsseite zu öffnen. Alternativ können Sie auf der Übersichtsseite der App auf der Karte für Continuous Delivery auf **Toolchain anzeigen** und dann auf **Übersicht** klicken.
 1. Klicken Sie auf der Karte für GitHub auf das Menü und klicken Sie dann auf **Konfigurieren**.
 1. Aktualisieren Sie die Konfigurationseinstellungen so, dass {{site.data.keyword.Bluemix_notm}} die Autorisierung für den Zugriff auf GitHub erhält. Klicken Sie auf **Autorisieren**, um zur GitHub-Website zu wechseln. Wenn keine aktive GitHub-Sitzung existiert, werden Sie aufgefordert, sich anzumelden. Klicken Sie auf **Anwendung autorisieren**, um {{site.data.keyword.Bluemix_notm}} den Zugriff auf Ihr GitHub-Konto zu erlauben.
 1. Wenn Sie die Aktualisierung der Einstellungen abgeschlossen haben, klicken Sie auf **Integration speichern**.


## Toolchain kann nicht erstellt werden
{: #cannot_create_toolchain}

Es wird ein Fehler angezeigt, wenn Sie eine Toolchain erstellen.
{:shortdesc}

Beim Erstellen einer Toolchain wird eine Fehlernachricht mit folgendem Inhalt angezeigt:
{: tsSymptoms}

`Diese Organisation enthält 200 Toolchains, was dem Maximalwert entspricht. Bevor Sie eine weitere Toolchain hinzufügen können, müssen Sie zuvor eine oder mehrere Toolchain aus der Organisation entfernen.`

Eine Organisation (org) kann nicht mehr als 200 Toolchains enthalten.  
{: tsCauses}

Entfernen Sie mindestens eine Toolchain aus der Organisation und erstellen Sie dann Ihre Toolchain erneut.
{: tsResolve}


## Speicherbegrenzung der Organisation wurde überschritten
{: #org_outofmemory}

Unter Umständen ist es nicht möglich, eine App auf {{site.data.keyword.Bluemix_notm}} bereitzustellen, wenn Sie die Speicherbegrenzung für Ihre Organisation überschritten haben. Wahlweise können Sie den durch Ihre Apps belegten Speicher verringern oder das Speicherkontingent Ihres Kontos heraufsetzen. Das maximale Speicherkontingent für ein Testkonto beläuft sich auf 2 GB. Das Kontingent kann durch Wechseln zu einem zahlungspflichtigen Konto erweitert werden.

Beim Bereitstellen einer App auf {{site.data.keyword.Bluemix_notm}} wird eine Fehlernachricht mit folgendem Inhalt angezeigt:
{: tsSymptoms}

`FEHLGESCHLAGEN - Serverfehler, Statuscode: 400, Fehlercode: 100005, Nachricht: Sie haben die Speicherbegrenzung Ihres Unternehmens überschritten.`

Dieser Fehler tritt auf, wenn die für Ihre Organisation verbleibende Speicherkapazität geringer ist als die Speichermenge, die für die App erforderlich ist, die Sie bereitstellen möchten. Das maximale Speicherkontingent für ein Testkonto beläuft sich auf 2 GB.
{: tsCauses}

Wahlweise können Sie das Speicherkontingent Ihres Kontos heraufsetzen oder den durch Ihre Apps belegten Speicher verringern.
{: tsResolve}

  * Wenn Sie das Speicherkontingent Ihres Kontos heraufsetzen möchten, müssen Sie Ihr Testkonto in ein zahlungspflichtiges Konto umwandeln. Informationen dazu, wie Sie Ihr Testkonto in ein zahlungspflichtiges Konto umwandeln, können Sie unter [Zahlkonten](/docs/pricing/index.html#pay-accounts) nachlesen.
  * Wenn Sie den durch Ihre Apps belegten Speicher verringern möchten, verwenden Sie hierzu entweder die {{site.data.keyword.Bluemix_notm}}-Konsole oder die Befehlszeilenschnittstelle 'cf'.

    Führen Sie bei Verwendung der {{site.data.keyword.Bluemix_notm}}-Konsole die folgenden Schritte aus:

    1. Wählen Sie im Apps-Dashboard Ihre App aus. Die Seite mit den Details der App wird geöffnet.
    2. Im Teilfenster für die Laufzeit können Sie die maximale Speichermenge herabsetzen, die Anzahl der App-Instanzen verringern oder eine Kombination beider Maßnahmen durchführen.

    Führen Sie bei Verwendung der Befehlszeilenschnittstelle 'cf' die folgenden Schritte aus:

    1. Prüfen Sie, wie viel Speicher Ihre Apps belegen:

	  ```
	  cf apps
	  ```

	  Der Befehl 'cf apps' bewirkt die Auflistung aller Apps, die Sie im aktuellen Bereich bereitgestellt haben. Außerdem wird für die einzelnen Apps jeweils der Status angezeigt.

    2. Sie können die durch Ihre App belegte Speichermenge verringern, indem Sie die Anzahl der App-Instanzen verringern, die maximale Speichermenge herabsetzen oder eine Kombination beider Maßnahmen durchführen:

	  ```
	  cf push app-name -p anwendungspfad -i anzahl_instanzen -m speicherbegrenzung
      ```

    3. Führen Sie für Ihre App einen Neustart durch, damit die Änderungen in Kraft treten.

Weitere Informationen zu allgemeinen Problemen im Zusammenhang mit der Verwaltung Ihrer Apps finden Sie in [Fehlerbehebung bei der Verwaltung von Apps](https://console.bluemix.net/docs/troubleshoot/ts_apps.html#managingapps).


## Ausführungsleiste enthält keine Bluemix Live Sync-Symbole in der Eclipse Orion-Web-IDE
{: #ts_llz_lkb_3r}

Sie haben eine App erstellt, aber die IBM Bluemix Live Sync-Symbole werden nicht in der Ausführungsleiste der Eclipse Orion-Web-IDE angezeigt. Es wird nicht die vollständige Ausführungsleiste mit den Live Edit-Symbolen angezeigt:

![Ausführungsleiste](images/webide_runbar_light.png)   

Beim Bearbeiten einer Node.js-App in der Web-IDE werden die {{site.data.keyword.Bluemix_notm}}-Symbole für Live Edit, den schnellen Neustart und das Debugging nicht in der Ausführungsleiste angezeigt.
{: tsSymptoms}

Die Symbole sind in folgenden Fällen nicht verfügbar:
{: tsCauses}

* Die Datei `manifest.yml` ist nicht auf der höchsten Ebene Ihres Projekts gespeichert. 
* Ihre App ist in einem Unterverzeichnis und nicht im Stammverzeichnis gespeichert, aber der Pfad zum Unterverzeichnis ist nicht in der Datei `manifest.yml` angegeben. 
* Die App enthält keine Datei `package.json`.

Verwenden Sie eine der folgenden Methoden:
{: tsResolve}

* Wenn die Datei `manifest.yml` nicht im Stammverzeichnis gespeichert ist, speichern Sie sie dort.
* Wenn Ihre App in einem Unterverzeichnis gespeichert ist, geben Sie den Pfad zum Unterverzeichnis in der Datei `manifest.yml` an.
   ```
    path: path_to_application
    ```
* Erstellen Sie eine Datei `package.json`, die sich im selben Verzeichnis wie Ihre App befindet.


## Toolchain wird nicht geladen
{: #toolchains_load}

Wenn Sie auf eine Toolchain klicken, damit die zugehörige Übersichtsseite angezeigt wird, so wird die Toolchain nicht geladen.
{:shortdesc}

Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf die Toolchain, um die zugehörige Übersichtsseite zu öffnen. Alternativ können Sie auf der Übersichtsseite der App auf der Karte für Continuous Delivery auf **Toolchain anzeigen** klicken. Klicken Sie anschließend auf **Übersicht**. Die Seite für 'Übersicht' für die Toolchain wird nicht geöffnet.
{: tsSymptoms}

Prüfen Sie den {{site.data.keyword.Bluemix_notm}}-Status, um festzustellen, ob das Problem durch eine Unterbrechung verursacht wird.
{: tsCauses}

Überprüfen Sie auf der Statusseite für {{site.data.keyword.Bluemix_notm}}, ob bekannte Probleme vorliegen, die sich auf die {{site.data.keyword.Bluemix_notm}}-Plattform und die wichtigsten Services in {{site.data.keyword.Bluemix_notm}} auswirken.
{: tsResolve}

Anhand einer der folgenden Optionen gelangen Sie zur Statusseite:

  * Melden Sie sich bei der {{site.data.keyword.Bluemix_notm}}-Konsole an. Klicken Sie in der Menüleiste auf **Support** und wählen Sie **Status** aus. Überprüfen Sie die aufgelisteten Ressourcen auf das Symbol ![Einige Probleme](../../support/images/some_issues.svg). Dieses Symbol kann auf einen Ausfall hinweisen.
  * Öffnen Sie die Statusseite direkt über [IBM {{site.data.keyword.Bluemix_notm}} - Systemstatus ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://ibm.biz/bluemixstatus){: new_window}.

Weitere Informationen zur Statusseite für {{site.data.keyword.Bluemix_notm}} enthält [{{site.data.keyword.Bluemix_notm}}-Status anzeigen](https://console.bluemix.net/docs/support/index.html#viewing-bluemix-status).


## Toolintegration ist nicht konfiguriert
{: #tool_integration_error}

Nachdem Sie die Toolintegration für Ihre Toolchain konfiguriert haben, wird der Fehler `Einrichtung fehlgeschlagen` auf der Karte des Tools angezeigt.
{:shortdesc}

Nachdem Sie eine Toolintegration konfiguriert haben, zeigen Sie auf der Übersichtsseite der Toolchain die Karte für das Tool an und stellen fest, dass die Einrichtung fehlgeschlagen ist.
{: tsSymptoms}

 ![Fehler 'Einrichtung fehlgeschlagen'](images/tool_setup_failed.png)

Wenn Sie eine Toolintegration hinzufügen, kommuniziert die Toolchain mit dem Tool, das durch die Toolintegration dargestellt wird, um alle notwendigen Ressourcen bereitzustellen und diese der Toolchain zuzuordnen. Wenn während der Einrichtung ein Fehler auftritt oder die Kommunikation zwischen der Toolchain und dem Tool nicht ordnungsgemäß abgeschlossen wird, so wird die Toolintegration in einen Fehlerstatus versetzt.
{: tsCauses}

Konfigurieren Sie die Toolintegration erneut:
{: tsResolve}

1. Bewegen Sie auf der Karte des Tools den Mauszeiger über die Nachricht `Einrichtung fehlgeschlagen` und klicken Sie auf **Neu konfigurieren**.

 ![Schaltfläche 'Neu konfigurieren'](images/tool_reconfigure.png)

1. Stellen Sie sicher, dass Sie gültige Konfigurationsparameter verwenden. Wenn der Fehler durch eine ungültige Konfiguration verursacht wurde, wird eine Fehlermeldung angezeigt, wie zum Beispiel `Die Integration konnte nicht eingerichtet werden. Überprüfen Sie die Einstellungen und wiederholen Sie die Operation. Ursache: Ungültiger api_key:fakeKey`. Aktualisieren Sie die Einstellungen für die Toolintegration und klicken Sie auf **Integration speichern**.
1. Wenn der Fehler durch einen Kommunikationsfehler verursacht wurde, klicken Sie auf **Integration speichern**, um einen erneuten Versuch zu starten.



<!-- ## Pipeline job failures
{: #cannot_authorize_github}

A pipeline job failed.
{:shortdesc}

Your pipeline job failed.
{: tsSymptoms}

 * Some reasons

Many reasons  
{: tsCauses}

If you are configuring the GitHub tool integration while you are creating your toolchain, follow these steps:
{: tsResolve}

  1. In the Configurable Integrations section, click **GitHub**.
  1. If you are creating the toolchain on {{site.data.keyword.Bluemix_notm}} Public and you have not authorized {{site.data.keyword.Bluemix_notm}} to access GitHub, click **Authorize** to go to the GitHub website.
  1. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account. If you have an active GitHub session but you haven't entered your password recently, you might be prompted to enter your GitHub password to confirm.

If you already have a toolchain, update the GitHub tool integration's configuration:

 1. On the DevOps dashboard, on the **Toolchains** page, click the toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**, and then click **Overview**.
 1. On the GitHub card, click the menu and click **Configure**.
 1. Update the configuration settings to authorize {{site.data.keyword.Bluemix_notm}} to access GitHub. Click **Authorize** to go to the GitHub website. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account. If you have an active GitHub session but you haven't entered your password recently, you might be prompted to enter your GitHub password to confirm.
 1. When you are finished updating the settings, click **Save Integration**.  -->




<!-- This is the template for a problem topic.  -->

<!-- The short description section contains a brief description of problem. For example:  

After you create an app on the Dashboard, you click *ADD GIT* to create a Git repository, but you cannot proceed.
{:shortdesc} -->

<!-- The symptoms section contains a description of problem symptoms. For example:  
When you click ADD GIT, a window opens and one of these issues occur:
- The window hangs with a blank screen.
- A message states that a problem exists with 3rd party cookies.
{: tsSymptoms} -->

<!-- The causes section contains a brief explanation of what causes the problem. For example:  
Your browser might be configured to prevent a cookie from being set. That cookie must be set from the IBM Bluemix DevOps Services site in the hub.jazz.net internet domain from within the context of the Bluemix console.
{: tsCauses} -->

<!-- The resolve section contains steps to resolve the problem. For example:  
You can fix this problem in one of three ways:
- Follow the instructions that are in the window that opens from the Bluemix console. Click the button. Another browser window opens temporarily. In that window, DevOps Services sets the authentication cookie.
- In another browser tab, go to https://hub.jazz.net and log in. Return to the Bluemix console and refresh the page. Click ADD GIT again.
- Change your browser settings to enable 3rd party cookies and click ADD GIT again.
{: tsResolve} -->
