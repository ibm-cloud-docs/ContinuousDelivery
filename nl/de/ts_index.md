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

Wenn Sie {{site.data.keyword.Bluemix_notm}} nicht für den Zugriff auf Ihr GitHub-Konto autorisiert haben, kann eines der folgenden Probleme auftrete:
{: tsSymptoms}

 * Bei dem Versuch, die GitHub-Toolintegration zu Ihrer Toolchain hinzuzufügen, wird die Toolintegration nicht hinzugefügt.
 * Die Pipeline wird nicht automatisch ausgeführt (ausgelöst), wenn Sie Änderungen per Push-Operation an Ihr GitHub- oder GitHub Enterprise-Repository übertragen.

{{site.data.keyword.Bluemix_notm}} ist nicht für den Zugriff auf GitHub autorisiert.  
{: tsCauses}

Wenn Sie die GitHub-Toolintegration konfigurieren, während Sie die Toolchain erstellen, gehen Sie dabei anhand der folgenden Schritte vor:
{: tsResolve}

  1. Klicken Sie im Abschnitt mit den konfigurierbaren Integrationen auf **GitHub**.
  1. Wenn Sie die Toolchain unter {{site.data.keyword.Bluemix_notm}} Public erstellen und {{site.data.keyword.Bluemix_notm}} nicht für den Zugriff auf GitHub autorisiert haben, klicken Sie auf **Autorisieren**, um zur GitHub-Website zu wechseln.
  1. Wenn keine aktive GitHub-Sitzung existiert, werden Sie aufgefordert, sich anzumelden. Klicken Sie auf **Anwendung autorisieren**, um {{site.data.keyword.Bluemix_notm}} den Zugriff auf Ihr GitHub-Konto zu erlauben. Falls eine aktive GitHub-Sitzung existiert, Sie Ihr Kennwort aber bereits vor einiger Zeit eingegeben haben, werden Sie möglicherweise aufgefordert, Ihr GitHub-Kennwort durch erneute Eingabe zu bestätigen.

Wenn Sie bereits über eine Toolchain verfügen, aktualisieren Sie die Konfiguration der GitHub-Toolintegration wie folgt:

 1. Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf die Toolchain, um die zugehörige Übersichtsseite zu öffnen. Alternativ können Sie auf der Übersichtsseite der App auf der Karte für Continuous Delivery auf **Toolchain anzeigen** und dann auf **Übersicht** klicken.
 1. Klicken Sie auf der Karte für GitHub auf das Menü und klicken Sie dann auf **Konfigurieren**.
 1. Aktualisieren Sie die Konfigurationseinstellungen so, dass {{site.data.keyword.Bluemix_notm}} die Autorisierung für den Zugriff auf GitHub erhält. Klicken Sie auf **Autorisieren**, um zur GitHub-Website zu wechseln. Wenn keine aktive GitHub-Sitzung existiert, werden Sie aufgefordert, sich anzumelden. Klicken Sie auf **Anwendung autorisieren**, um {{site.data.keyword.Bluemix_notm}} den Zugriff auf Ihr GitHub-Konto zu erlauben. Falls eine aktive GitHub-Sitzung existiert, Sie Ihr Kennwort aber bereits vor einiger Zeit eingegeben haben, werden Sie möglicherweise aufgefordert, Ihr GitHub-Kennwort durch erneute Eingabe zu bestätigen.
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

Unter Umständen ist es nicht möglich, eine App auf {{site.data.keyword.Bluemix_notm}} bereitzustellen, wenn Sie die Speicherbegrenzung für Ihre Organisation überschritten haben. Wahlweise können Sie den durch Ihre Apps belegten Speicher verringern oder das Speicherkontingent Ihres Kontos heraufsetzen. Das maximale Speicherkontingent für ein Testkonto beläuft sich auf 2 GB und kann nur durch Wechseln zu einem zahlungspflichtigen Konto erweitert werden.

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
