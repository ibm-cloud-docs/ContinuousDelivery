---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-20"

keywords: IBM Cloud Continuous Delivery, GitHub tool integration, error message

subcollection: ContinuousDelivery

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

## Warum wird auf der Seite 'Toolchains' angezeigt, dass der Lite-Plan des Service {{site.data.keyword.contdelivery_short}} überschritten wurde?
{: #plan_exceeded}
{: faq}

{{site.data.keyword.contdelivery_short}} bietet zwei Pläne: Lite und Professional. Wenn Sie den {{site.data.keyword.contdelivery_short}}-Lite-Plan verwenden, können Sie Toolchains bis zu den Grenzwerten des Plans kostenlos verwenden. Die Fehlernachricht weist darauf hin, dass Sie einen oder mehrere Grenzwerte des Lite-Plans überschritten haben. Sie könnten den Plan beispielsweise überschreiten, wenn Sie zu viele berechtigte Benutzer haben, die der Instanz des Service {{site.data.keyword.contdelivery_short}} zugeordnet sind, oder wenn Sie die maximale Anzahl von {{site.data.keyword.deliverypipeline}}-Jobs ausgeführt haben. Weitere Informationen zu den Bedingungen Ihres Plans finden Sie unter [Einschränkungen beim Plan und bei der Nutzung](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage){: new_window}.


## Mein {{site.data.keyword.contdelivery_short}}-Service gibt an, dass Service des Lite-Plans nach 30 Tagen der Inaktivität gelöscht werden. Was bedeutet Inaktivität hier? 
{: #plan_inactivity}
{: faq}

Eine Instanz des {{site.data.keyword.contdelivery_short}}-Service wird als aktiv betrachtet, wenn eine oder mehrere der Toolchains in derselben Ressourcengruppe oder Cloud Foundry-Organisation aktiv sind. Eine Toolchain wird als aktiv betrachtet, wenn die Benutzer über die Benutzerschnittstelle mit ihr interagieren, wenn Delivery Pipeline-Jobs getriggert werden, wenn auf von {{site.data.keyword.gitrepos}} verwaltete Repositorys zugegriffen wird, oder wenn {{site.data.keyword.webide}}-Arbeitsbereiche von Eclipse Orion verwendet werden. Damit eine Instanz als inaktiv betrachtet wird, müssen alle diese Bedingungen für alle Toolchains, die dem {{site.data.keyword.contdelivery_short}}-Service zugeordnet sind, 30 Tage lang nicht erfüllt werden. 


## Ich habe eine Toolchain erstellt. Warum zeigt die Seite 'Toolchains' an, dass ein Service Continuous Delivery erforderlich ist?
{: #service_required_resource_group}
{: faq}

Die Bedingungen des Plans für die Instanz des Service {{site.data.keyword.contdelivery_short}}, die sich in derselben Ressourcengruppe oder Organisation wie die Toolchain befindet, steuern die Verwendung einiger der Toolintegrationen ({{site.data.keyword.deliverypipeline}}, Eclipse Orion-{{site.data.keyword.webide}} und {{site.data.keyword.gitrepos}}), die im Service enthalten sind. Die Fehlernachricht gibt an, dass die Ressourcengruppe bzw. die Organisation die erforderliche Instanz des Service {{site.data.keyword.contdelivery_short}} nicht enthält. Weitere Informationen zu den Bedingungen Ihres Plans finden Sie unter [Einschränkungen beim Plan und bei der Nutzung](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage){: new_window}.


## Ich habe Informationen für eine Toolchain aus einer Cloud Foundry-Organisation aktualisiert, warum kann ich meine Änderungen nicht in der Toolchain sehen?
{: #updates_in_cloud_foundry}
{: faq}

Wenn Sie die Toolchaininformationen direkt aus Cloud Foundry aktualisieren, kann es einige Minuten dauern, bis der {{site.data.keyword.contdelivery_short}}-Service aktualisiert wurde und Ihre Änderungen anzeigt. Wenn Sie beispielsweise einen Benutzer zu einer Cloud Foundry-Organisation hinzufügen oder daraus entfernen, kann es einige Minuten dauern, bis {{site.data.keyword.contdelivery_short}} feststellt, dass es einen neuen Benutzer gibt und dass dieser Benutzer auf die Toolchain zugreifen darf. 


## Ich habe eine Toolchain in einer Cloud Foundry-Organisation erstellt. Warum zeigt die Seite 'Toolchains' an, dass ein Service Continuous Delivery erforderlich ist?
{: #service_required_cloud_foundry}
{: faq}

Wenn Sie eine Toolchain in einer Ressourcengruppe oder Organisation erstellen, die keine Instanz des Service {{site.data.keyword.contdelivery_short}} enthält, versucht die Toolchain-Plattform, eine Instanz des Service mithilfe des Lite-Plans automatisch zu erstellen. Die Fehlernachricht weist darauf hin, dass die Toolchain-Plattform die Serviceinstanz nicht erstellen konnte.

Dieser Fehler kann auftreten, wenn Sie eine Toolchain in der Region 'Vereinigte Staaten (Süden)' und in einer Cloud Foundry-Organisation erstellen, für die es noch keine Instanz von {{site.data.keyword.contdelivery_short}} gibt. In der Region 'Vereinigte Staaten (Süden)' müssen Sie alle neuen Instanzen des Service {{site.data.keyword.contdelivery_short}} in Ressourcengruppen erstellen. 

Sie können entweder die Toolchain in einer Ressourcengruppe erstellen oder die Toolchain in einer Organisation erstellen, die bereits über eine Instanz von {{site.data.keyword.contdelivery_short}} verfügt.
  

## Wie verschiebe ich meine Toolchain aus einer Cloud Foundry-Organisation zu einer Ressourcengruppe? 
{: #toolchain_move_to_resource_group}
{: faq}

Derzeit gibt es keine Möglichkeit, Toolchains aus einer Cloud Foundry-Organisation zu einer Ressourcengruppe zu migrieren. Stattdessen können Sie die Toolchain manuell in einer Ressourcengruppe erstellen und dann die ursprüngliche Toolchain aus der Cloud Foundry-Organisation entfernen. 


## Warum wird beim Versuch, eine App auf {{site.data.keyword.Bluemix_notm}} bereitzustellen, eine Fehlernachricht angezeigt?
{: #org_outofmemory}
{: faq}

Wenn Sie eine App auf {{site.data.keyword.Bluemix_notm}} bereitstellen möchten und eine Fehlernachricht erhalten, ist die für Ihre Organisation verbleibende Speicherkapazität geringer als die Speichermenge, die für die App erforderlich ist, die Sie bereitstellen möchten.

`FEHLGESCHLAGEN - Serverfehler, Statuscode: 400, Fehlercode: 100005, Nachricht: Sie haben die Speicherbegrenzung Ihres Unternehmens überschritten.`

Wahlweise können Sie das Speicherkontingent Ihres Kontos heraufsetzen oder den durch Ihre Apps belegten Speicher verringern. Das maximale Speicherkontingent für ein Testkonto beläuft sich auf 2 GB. Wenn Sie das Speicherkontingent Ihres Kontos heraufsetzen möchten, müssen Sie Ihr Testkonto in ein zahlungspflichtiges Konto umwandeln. Informationen zum Konvertieren des Testkontos in ein kostenpflichtiges Konto finden Sie in [Wie kann ich ein Upgrade meines Kontotyps durchführen oder das Konto ändern?](/docs/account?topic=account-accountfaqs#changeacct). Wenn Sie den durch Ihre Apps belegten Speicher verringern möchten, verwenden Sie hierzu entweder die {{site.data.keyword.Bluemix_notm}}-Konsole oder die Befehlszeilenschnittstelle 'cf'.

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


## In der erstellten App werden in der Ausführungsleiste keine {{site.data.keyword.Bluemix_notm}} Live Sync-Symbole in der {{site.data.keyword.webide}} angezeigt. Warum?
{: #ts_llz_lkb_3r}
{: faq}

![Ausführungsleiste](images/webide_runbar_light.png)   

Beim Bearbeiten einer Node.js-App in der {{site.data.keyword.webide}} sind die {{site.data.keyword.Bluemix_notm}}-Symbole für Live Edit, den schnellen Neustart und das Debugging in der Ausführungsleiste in folgenden Fällen nicht verfügbar: 


* Die Datei `manifest.yml` ist nicht auf der höchsten Ebene Ihres Projekts gespeichert.
* Ihre App ist in einem Unterverzeichnis und nicht im Stammverzeichnis gespeichert, aber der Pfad zum Unterverzeichnis ist nicht in der Datei `manifest.yml` angegeben.
* Die App enthält keine Datei `package.json`.


Wenn die Datei `manifest.yml` nicht im Stammverzeichnis gespeichert ist, speichern Sie sie dort. Wenn Ihre App in einem Unterverzeichnis gespeichert ist, geben Sie den Pfad zum Unterverzeichnis in der Datei `manifest.yml` an. Wenn die App die Datei `package.json` nicht enthält, erstellen Sie sie im selben Verzeichnis, in der sich Ihre App befindet.


## Ich habe auf die {{site.data.keyword.webide}}-Schaltfläche 'Ausführen' geklickt. Wo sind die Protokolldateien?  
{: #web_ide_log_files}
{: faq}  

Wenn Sie auf die Schaltfläche 'Ausführen' klicken, wird der Inhalt Ihres Arbeitsbereichs auf dieselbe Weise nach Cloud Foundry übertragen, wie wenn Sie auf Ihrem Desktop den Befehl `cf push` eingeben. Sie können die Protokolldateien über das Cloud Foundry-Dashboard finden. 

Weitere Informationen zum Bereitstellen der Inhalte Ihres Arbeitsbereichs finden Sie unter [App vom Arbeitsbereich aus bereitstellen](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#deploy). 


## Wie kann ich verhindern, dass die {{site.data.keyword.webide}} alle Änderungen in der Git-Ansicht automatisch auswählt? 
{: #web_ide_git_view}
{: faq} 

Die {{site.data.keyword.webide}} setzt voraus, dass Sie jedes Mal, wenn Sie die GIT-Seite öffnen, ausgehende Änderungen an Ihr Code-Repository übertragen möchten. Wenn Sie manuell auswählen möchten, welche Ressourcen festgeschrieben, synchronisiert, zurückgesetzt und ersetzt werden sollen, deaktivieren Sie auf der GIT-Vorgabenseite das Kontrollkästchen **Geänderte Dateien immer auswählen**. 


## Warum unterstützt die {{site.data.keyword.webide}} meine Sprache nicht? 
{: #web_ide_language_support}
{: faq}  

Die {{site.data.keyword.webide}} stellt umfangreiche Tools sowie Unterstützung für JavaScript, HTML und CSS bereit. Sie bietet auch eine Syntaxhervorhebung für die gängigsten Sprachen. Sie können die {{site.data.keyword.webide}} um die Unterstützung einer bestimmten Sprache erweitern. Eine vollständige Liste der Sprachen, die von der {{site.data.keyword.webide}} unterstützt werden, finden Sie unter [Unterstützte Sprachen](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#supported_languages). 


## Wie finde ich den Status von {{site.data.keyword.Bluemix_notm}} und des {{site.data.keyword.contdelivery_short}}-Service?
{: #toolchains_load}
{: faq}

Prüfen Sie die {{site.data.keyword.Bluemix_notm}}-Statusseite auf bekannte Probleme, die sich auf die {{site.data.keyword.Bluemix_notm}}-Plattform und die wichtigsten Services in {{site.data.keyword.Bluemix_notm}} auswirken.

Anhand einer der folgenden Optionen gelangen Sie zur Statusseite:

  * Melden Sie sich bei der {{site.data.keyword.Bluemix_notm}}-Konsole an. Klicken Sie in der Menüleiste auf **Support** und wählen Sie **Status** aus. Prüfen Sie die aufgelisteten Ressourcen auf das Symbol ![Probleme](../../get-support/images/some_issues.svg). Dieses Symbol kann auf einen Ausfall hinweisen.
  * Greifen Sie direkt auf [{{site.data.keyword.Bluemix_notm}} - Systemstatus ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/status){: new_window} zu.

Weitere Informationen zur {{site.data.keyword.Bluemix_notm}}-Statusseite finden Sie in [{{site.data.keyword.Bluemix_notm}}-Status anzeigen](/docs/get-support?topic=get-support-viewing-cloud-status#viewing-cloud-status){: new_window}.


## Wie übergebe ich Artefakte zwischen Pipelinejobs?
{: #artifacts_pipeline_jobs}
{: faq}

Da alle Pipelinejobs in einer Stage die gleiche Stage-Eingabe empfangen, können Sie keine Artefakte zwischen Jobs übergeben, die sich in derselben Stage befinden. Buildjobs generieren jedoch Artefakte, die Jobs in anderen Stages verwenden können. Um Artefakte zwischen zwei Jobs zu übergeben, verschieben Sie die einzelnen Jobs in eine separate Stage. Weitere Informationen zu Pipelinejobs finden Sie unter [Jobs](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_jobs). 


## Gibt es ein maximales Zeitlimit für die Ausführung meiner Pipelinejobs?
{: #pipeline_jobs_time_limit}
{: faq}

Ein Pipelinejob kann maximal 60 Minuten ausgeführt werden. Wenn ein Job dieses Limit überschreitet, schlägt er fehl. Untersuchen Sie, ob die Arbeit, die der Pipelinejob ausführt, in kleinere Schritte unterteilt werden kann. Sie können den Pipelinejob in verschiedene kürzere Pipelinejobs unterteilen, die jeweils weniger als 60 Minuten dauern. 


## Wie sicher sind die sicheren Pipeline-Eigenschaften?
{: #pipeline_secure_properties}
{: faq}

Sichere Pipeline-Eigenschaften werden mit AES-128 verschlüsselt und sie werden unmittelbar vor der Übertragung an Ihr Pipeline-Script entschlüsselt. Diese Eigenschaften werden außerdem mithilfe von Sternen in der Eigenschaften-Benutzerschnittstelle und in Ihren Pipelineprotokolldateien maskiert. Bevor Daten für Ihren Pipelinejob in die Protokolldatei geschrieben werden, wird sie nach exakten Übereinstimmungen mit allen Werten in den sicheren Pipeline-Eigenschaften durchsucht. Wird eine Übereinstimmung gefunden, wird sie mithilfe von Sternen maskiert. Gehen Sie vorsichtig vor, wenn Sie mit sicheren Eigenschaften und Protokolldateien arbeiten, da nur exakte Übereinstimmungen maskiert werden.  
