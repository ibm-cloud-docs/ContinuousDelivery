---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-6"

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:faq: data-hd-content-type='faq'}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# Häufig gestellte Fragen
{: #ts_cd}

Hier erhalten Sie Antworten auf allgemeine Fragen zur Verwendung von {{site.data.keyword.contdelivery_full}}.
{:shortdesc}


## Beim Versuch, die GitHub-Toolintegration zu meiner Toolchain hinzuzufügen, wurde die Toolintegration nicht hinzugefügt. Warum?
{: #cannot_authorize_github}
{: faq}

Wenn {{site.data.keyword.Bluemix_notm}} nicht für den Zugriff auf Ihr GitHub-Konto autorisiert ist, kann die Toolintegration nicht zur Toolchain hinzugefügt werden.

Wenn Sie die GitHub-Toolintegration beim Erstellen Ihrer Toolchain konfigurieren, befolgen Sie diese Schritte, um eine Autorisierung mit GitHub durchzuführen:

  1. Klicken Sie im Abschnitt mit den konfigurierbaren Integrationen auf **GitHub**.
  1. Wenn Sie die Toolchain unter {{site.data.keyword.Bluemix_notm}} Public erstellen und {{site.data.keyword.Bluemix_notm}} nicht für den Zugriff auf GitHub autorisiert ist, klicken Sie auf **Autorisieren**, um zur GitHub-Website zu wechseln.
  1. Wenn keine aktive GitHub-Sitzung existiert, werden Sie aufgefordert, sich anzumelden. Klicken Sie auf **Anwendung autorisieren**, um {{site.data.keyword.Bluemix_notm}} den Zugriff auf Ihr GitHub-Konto zu erlauben.

Wenn Sie bereits über eine Toolchain verfügen, aktualisieren Sie die Konfiguration der GitHub-Toolintegration wie folgt:

 1. Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf die Toolchain, um die zugehörige Übersichtsseite zu öffnen. Alternativ können Sie auf der Übersichtsseite der App auf der Karte für Continuous Delivery auf **Toolchain anzeigen** und dann auf **Übersicht** klicken.
 1. Klicken Sie auf der Karte für GitHub auf das Menü und klicken Sie dann auf **Konfigurieren**.
 1. Aktualisieren Sie die Konfigurationseinstellungen so, dass {{site.data.keyword.Bluemix_notm}} die Autorisierung für den Zugriff auf GitHub erhält. Klicken Sie auf **Autorisieren**, um zur GitHub-Website zu wechseln. Wenn keine aktive GitHub-Sitzung existiert, werden Sie aufgefordert, sich anzumelden. Klicken Sie auf **Anwendung autorisieren**, um {{site.data.keyword.Bluemix_notm}} den Zugriff auf Ihr GitHub-Konto zu erlauben.
 1. Wenn Sie die Aktualisierung der Einstellungen abgeschlossen haben, klicken Sie auf **Integration speichern**.


## Warum wird beim Versuch, eine Toolchain zu erstellen, eine Fehlernachricht angezeigt?
{: #cannot_create_toolchain}
{: faq}

Wenn Sie eine Toolchain in einer Organisation erstellen möchten und die folgende Fehlernachricht erhalten, entfernen Sie mindestens eine Toolchain aus der Organisation und erstellen Sie dann Ihre Toolchain erneut.

`Diese Organisation enthält 200 Toolchains, was dem Maximalwert entspricht. Bevor Sie eine weitere Toolchain hinzufügen können, müssen Sie zuvor eine oder mehrere Toolchain aus der Organisation entfernen.`


## Warum wird auf der Seite 'Toolchains' angezeigt, dass der Lite-Plan des Service {{site.data.keyword.contdelivery_short}} überschritten wurde?
{: #plan_exceeded}
{: faq}

{{site.data.keyword.contdelivery_short}} bietet zwei Pläne: Lite und Professional. Wenn Sie den {{site.data.keyword.contdelivery_short}}-Lite-Plan verwenden, können Sie Toolchains bis zu den Grenzwerten des Plans kostenlos verwenden. Die Fehlernachricht weist darauf hin, dass Sie einen oder mehrere Grenzwerte des Lite-Plans überschritten haben. Sie könnten den Plan beispielsweise überschreiten, wenn Sie zu viele berechtigte Benutzer haben, die der Instanz des Service {{site.data.keyword.contdelivery_short}} zugeordnet sind, oder wenn Sie die maximale Anzahl von {{site.data.keyword.deliverypipeline}}-Jobs ausgeführt haben. Weitere Informationen zu den Bedingungen Ihres Plans finden Sie unter [Einschränkungen beim Plan und bei der Nutzung](/docs/services/ContinuousDelivery/limitations_plans.html){: new_window}.


## Ich habe eine Toolchain erstellt. Warum zeigt die Seite 'Toolchains' an, dass ein Service Continuous Delivery erforderlich ist?
{: #service_required_resource_group}
{: faq}

Die Bedingungen des Plans für die Instanz des Service {{site.data.keyword.contdelivery_short}}, die sich in derselben Ressourcengruppe oder Organisation wie die Toolchain befindet, steuern die Verwendung einiger der Toolintegrationen ({{site.data.keyword.deliverypipeline}}, Eclipse Orion-{{site.data.keyword.webide}} und {{site.data.keyword.gitrepos}}), die im Service enthalten sind. Die Fehlernachricht gibt an, dass die Ressourcengruppe bzw. die Organisation die erforderliche Instanz des Service {{site.data.keyword.contdelivery_short}} nicht enthält. Weitere Informationen zu den Bedingungen Ihres Plans finden Sie unter [Einschränkungen beim Plan und bei der Nutzung](/docs/services/ContinuousDelivery/limitations_plans.html){: new_window}.


## Ich habe eine Toolchain in einer Cloud Foundry-Organisation erstellt. Warum zeigt die Seite 'Toolchains' an, dass ein Service Continuous Delivery erforderlich ist?
{: #service_required_cloud_foundry}
{: faq}

Wenn Sie eine Toolchain in einer Ressourcengruppe oder Organisation erstellen, die keine Instanz des Service {{site.data.keyword.contdelivery_short}} enthält, versucht die Toolchain-Plattform, eine Instanz des Service mithilfe des Lite-Plans automatisch zu erstellen. Die Fehlernachricht weist darauf hin, dass die Toolchain-Plattform die Serviceinstanz nicht erstellen konnte.

Dieser Fehler kann auftreten, wenn Sie eine Toolchain in der Region 'Vereinigte Staaten (Süden)' und in einer Cloud Foundry-Organisation erstellen, für die es noch keine Instanz von {{site.data.keyword.contdelivery_short}} gibt. In der Region 'Vereinigte Staaten (Süden)' müssen Sie alle neuen Instanzen des Service {{site.data.keyword.contdelivery_short}} in Ressourcengruppen erstellen. 

Sie können entweder die Toolchain in einer Ressourcengruppe erstellen oder die Toolchain in einer Organisation erstellen, die bereits über eine Instanz von {{site.data.keyword.contdelivery_short}} verfügt.
  

## Warum wird beim Versuch, eine App auf {{site.data.keyword.Bluemix_notm}} bereitzustellen, eine Fehlernachricht angezeigt?
{: #org_outofmemory}
{: faq}

Wenn Sie eine App auf {{site.data.keyword.Bluemix_notm}} bereitstellen möchten und eine Fehlernachricht erhalten, ist die für Ihre Organisation verbleibende Speicherkapazität geringer als die Speichermenge, die für die App erforderlich ist, die Sie bereitstellen möchten.

`FEHLGESCHLAGEN - Serverfehler, Statuscode: 400, Fehlercode: 100005, Nachricht: Sie haben die Speicherbegrenzung Ihres Unternehmens überschritten.`

Wahlweise können Sie das Speicherkontingent Ihres Kontos heraufsetzen oder den durch Ihre Apps belegten Speicher verringern. Das maximale Speicherkontingent für ein Testkonto beläuft sich auf 2 GB. Wenn Sie das Speicherkontingent Ihres Kontos heraufsetzen möchten, müssen Sie Ihr Testkonto in ein zahlungspflichtiges Konto umwandeln. Informationen dazu, wie Sie Ihr Testkonto in ein zahlungspflichtiges Konto umwandeln, können Sie unter [Zahlkonten](/docs/pricing/index.html#pay-accounts) nachlesen. Wenn Sie den durch Ihre Apps belegten Speicher verringern möchten, verwenden Sie hierzu entweder die {{site.data.keyword.Bluemix_notm}}-Konsole oder die Befehlszeilenschnittstelle 'cf'.

Führen Sie bei Verwendung der {{site.data.keyword.Bluemix_notm}}-Konsole die folgenden Schritte aus:

1. Wählen Sie im Apps-Dashboard Ihre App aus. Die Seite mit den Details der App wird geöffnet.
1. Im Teilfenster für die Laufzeit können Sie die maximale Speichermenge herabsetzen, die Anzahl der App-Instanzen verringern oder eine Kombination beider Maßnahmen durchführen.

Führen Sie bei Verwendung der Befehlszeilenschnittstelle 'cf' die folgenden Schritte aus:

1. Prüfen Sie, wie viel Speicher Ihre Apps belegen. Der Befehl 'cf apps' bewirkt die Auflistung aller Apps, die Sie im aktuellen Bereich bereitgestellt haben. Außerdem wird für die einzelnen Apps jeweils der Status angezeigt.

	  ```
	  cf apps
	  ```

1. Sie können die durch Ihre App belegte Speichermenge verringern, indem Sie die Anzahl der App-Instanzen verringern, die maximale Speichermenge herabsetzen oder eine Kombination beider Maßnahmen durchführen:

	  ```
	  cf push app-name -p anwendungspfad -i anzahl_instanzen -m speicherbegrenzung
      ```
    
1. Führen Sie für Ihre App einen Neustart durch, damit die Änderungen in Kraft treten.


## In der erstellten App werden in der Ausführungsleiste keine {{site.data.keyword.Bluemix_notm}} Live Sync-Symbole in der Eclipse Orion-Web-IDE angezeigt. Warum?
{: #ts_llz_lkb_3r}
{: faq}

![Ausführungsleiste](images/webide_runbar_light.png)   

Beim Bearbeiten einer Node.js-App in der Web-IDE sind die {{site.data.keyword.Bluemix_notm}}-Symbole für Live Edit, den schnellen Neustart und das Debugging in der Ausführungsleiste in folgenden Fällen nicht verfügbar:


* Die Datei `manifest.yml` ist nicht auf der höchsten Ebene Ihres Projekts gespeichert.
* Ihre App ist in einem Unterverzeichnis und nicht im Stammverzeichnis gespeichert, aber der Pfad zum Unterverzeichnis ist nicht in der Datei `manifest.yml` angegeben.
* Die App enthält keine Datei `package.json`.


Wenn die Datei `manifest.yml` nicht im Stammverzeichnis gespeichert ist, speichern Sie sie dort. Wenn Ihre App in einem Unterverzeichnis gespeichert ist, geben Sie den Pfad zum Unterverzeichnis in der Datei `manifest.yml` an. Wenn die App die Datei `package.json` nicht enthält, erstellen Sie sie im selben Verzeichnis, in der sich Ihre App befindet.


## Beim Klicken auf eine Toolchain zum Anzeigen der Übersichtsseite wird die Toolchain nicht geladen. Warum?
{: #toolchains_load}
{: faq}

Prüfen Sie die {{site.data.keyword.Bluemix_notm}}-Statusseite auf bekannte Probleme, die sich auf die {{site.data.keyword.Bluemix_notm}}-Plattform und die wichtigsten Services in {{site.data.keyword.Bluemix_notm}} auswirken.

Anhand einer der folgenden Optionen gelangen Sie zur Statusseite:

  * Melden Sie sich bei der {{site.data.keyword.Bluemix_notm}}-Konsole an. Klicken Sie in der Menüleiste auf **Support** und wählen Sie **Status** aus. Prüfen Sie die aufgelisteten Ressourcen auf das Symbol ![Probleme](../../get-support/images/some_issues.svg). Dieses Symbol kann auf einen Ausfall hinweisen.
  * Greifen Sie direkt auf [{{site.data.keyword.Bluemix_notm}} - Systemstatus ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/status){: new_window} zu.

Weitere Informationen zur Statusseite für {{site.data.keyword.Bluemix_notm}} finden Sie in [{{site.data.keyword.Bluemix_notm}}-Status anzeigen](https://cloud.ibm.com/docs/get-support/ViewStatus.html#viewing-bluemix-status).


## Es wurde eine Toolintegration für meine Toolchain konfiguriert, aber die Konfiguration wird nicht angezeigt. Warum?
{: #tool_integration_error}
{: faq}

Wenn Sie eine Toolintegration hinzufügen, kommuniziert die Toolchain mit dem Tool, das durch die Toolintegration dargestellt wird, um alle notwendigen Ressourcen bereitzustellen und diese der Toolchain zuzuordnen. Wenn während der Einrichtung ein Fehler auftritt oder die Kommunikation zwischen der Toolchain und dem Tool nicht ordnungsgemäß abgeschlossen wird, so wird die Toolintegration in einen Fehlerstatus versetzt.

 ![Fehler 'Einrichtung fehlgeschlagen'](images/tool_setup_failed.png)

Versuchen Sie, die Toolintegration erneut zu konfigurieren:

1. Bewegen Sie auf der Karte des Tools den Mauszeiger über die Nachricht `Einrichtung fehlgeschlagen` und klicken Sie auf **Neu konfigurieren**.

 ![Schaltfläche 'Neu konfigurieren'](images/tool_reconfigure.png)

1. Stellen Sie sicher, dass Sie gültige Konfigurationsparameter verwenden. Wenn der Fehler durch eine ungültige Konfiguration verursacht wurde, wird eine Fehlermeldung angezeigt, wie zum Beispiel `Die Integration konnte nicht eingerichtet werden. Überprüfen Sie die Einstellungen und wiederholen Sie die Operation. Ursache: Ungültiger api_key:fakeKey`. Aktualisieren Sie die Einstellungen für die Toolintegration und klicken Sie auf **Integration speichern**.
1. Wenn der Fehler durch einen Kommunikationsfehler verursacht wurde, klicken Sie auf **Integration speichern**, um einen erneuten Versuch zu starten.
