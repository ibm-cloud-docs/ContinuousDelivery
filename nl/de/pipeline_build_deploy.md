---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-14"

keywords: ADD STAGE, Run Stage icon, JOBS tab

subcollection: ContinuousDelivery

---
<!-- Copyright info at top of file: REQUIRED
    The copyright info is YAML content that must occur at the top of the MD file, before attributes are listed.
    It must be surrounded by 3 dashes.
    The value "years" can contain just one year or a two years separated by a comma. (years: 2014, 2016)
    Indentation as per the previous template must be preserved.
-->

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Builderstellung und Bereitstellung
{: #deliverypipeline_build_deploy}

{{site.data.keyword.contdelivery_full}} enthält die Delivery Pipeline, die es Ihnen ermöglicht, einen reproduzierbaren, kontinuierlichen Integrationsprozess und einen Continuous Delivery-Prozess zu implementieren.
{:shortdesc}

Führen Sie die folgenden Tasks aus, um eine Pipeline zu konfigurieren.

## Eine Stage hinzufügen
{: #deliverypipeline_add_stage}

1. Klicken Sie auf der Seite 'Pipeline' auf **Stage hinzufügen**. Die Seite 'Stagekonfiguration' wird angezeigt.
2. Konfigurieren Sie die Stage.
  1. Wählen Sie auf der Registerkarte **EINGABE** eine Eingabe für die Stage aus.  Für Build-Stages enthält die Eingabe-Registerkarte ein **Zweig**-Feld, um die Verzweigung im Repository anzugeben, das für die Eingabe verwendet werden soll.
  2. Fügen Sie auf der Registerkarte **JOBS** mindestens einen Job hinzu und konfigurieren Sie diesen. Die erste Stage verfügt in der Regel mindestens über einen Buildjob.
3. Klicken Sie auf **Speichern**.

## Einen Job zu einer Stage hinzufügen
{: #deliverypipeline_add_job}

1. Klicken Sie in der Stage auf das Symbol **Phasenkonfiguration** und dann auf **Phase konfigurieren**.
2. Klicken Sie auf die Registerkarte **JOBS**.
3. Klicken Sie auf **Job hinzufügen**. Wählen Sie den Typ von Job aus, der hinzugefügt werden soll.
4. Konfigurieren Sie den Job.
5. Klicken Sie auf **Speichern**.

![Einen Job zu einer Stage hinzufügen](images/AddJob2.png)

## Eine Stage ausführen
{: #deliverypipeline_run_stage}

Sie können eine Stage manuell ausführen, indem Sie auf das Symbol **Stage ausführen** auf der Seite 'Pipeline' klicken.

![Auf das Symbol für die Ausführung der Stage in der Stage klicken](images/RunStage.png)

Sie können über eine von zwei Möglichkeiten auch bedarfsgerechte Builds und Bereitstellungen von der Seite für Buildprotokolle anfordern.
* Ziehen Sie einen Build auf die Box, die sich unter einer konfigurierten Stage befindet.
* Klicken Sie im Abschnitt für das Ergebnis der letzten Ausführung (LAST EXECUTION RESULT) auf das Symbol für **Senden an** und wählen Sie dann einen Bereich aus, in dem die Bereitstellung erfolgen soll.
  ![Die Stage für die Ausführung mit diesem Buildsymbol](images/deploy_to.png)

Klicken Sie in der Stage auf **Protokolle und Verlauf anzeigen**, um eine aktive Stage abzubrechen. Klicken Sie in der Liste der Jobs auf die Nummer des aktiven Jobs und anschließend auf **ABBRECHEN**. Sie können Jobs auch einzeln abbrechen, indem Sie auf einen Job und anschließend auf das Symbol **Abbrechen** klicken, oder indem Sie für einen Job in seiner Stage auf das Symbol **Stopp** klicken.

## Eine App bereitstellen
{: #deliverypipeline_deploy}

Ein ordnungsgemäß konfigurierter Bereitstellungsjob stellt Ihre App immer dann in Ihrem Ziel bereit, wenn der Job ausgeführt wird. Um einen Bereitstellungsjob manuell auszuführen, klicken Sie auf das Symbol **Stage ausführen** der Stage, in der sich der Job befindet.

### Eingabeüberarbeitungen
{: #deliverypipeline_input_revisions}

Wenn Sie eine Stage manuell ausführen, oder wenn sie ausgeführt wird, weil eine Stage vor ihr abgeschlossen wurde, wählt die aktive Stage ihre Eingabeüberarbeitung aus. In der Regel ist die Eingabeüberarbeitung eine Buildnummer. Zur Auswahl der Eingabeüberarbeitung erfüllt die Stage die folgenden Bedingungen:

* Falls eine bestimmte Überarbeitung ausgewählt ist, wird diese verwendet.
* Falls keine bestimmte Überarbeitung ausgewählt ist, werden vorherige Stages durchsucht, bis eine Stage gefunden wurde, die dieselbe Eingabe verwendet. Die letzte erfolgreich ausgeführte Überarbeitung dieser Eingabe wird gesucht und verwendet.
* Falls keine bestimmte Überarbeitung angegeben ist und keine anderen Stages die angegebene Quelle als Eingabe verwenden, wird die letzte Überarbeitung der Eingabe verwendet.

Sie können einen vorherigen Build bereitstellen. Klicken Sie in der Stage, die den Build enthält, auf **Protokolle und Verlauf anzeigen**. Klicken Sie auf der Seite, die geöffnet wird, um die Ausführungsnummer zu erweitern, und klicken Sie anschließend auf den Buildjob. Klicken Sie auf **Senden an** und wählen Sie ein Ziel aus.
{: tip}

### Services zu Apps hinzufügen
{: #deliverypipeline_add_services}

Sie können Services zu Ihren Apps hinzufügen und diese Services von Ihrem {{site.data.keyword.Bluemix_notm}}-Dashboard aus oder über die Cloud Foundry-CLI (CLI = Befehlszeilenschnittstelle) verwalten. Sie können für Pipeline-Jobs auch Cloud Foundry-CLI-Befehle in Scripts ausgeben. Sie können zum Beispiel einen Service zu einer App im Script eines Bereitstellungsjobs hinzufügen. Weitere Informationen zum Hinzufügen von Services finden Sie in [Services mit externen Apps verbinden](/docs/resources?topic=resources-externalapp).

## Protokolle anzeigen
{: #deliverypipeline_view_logs}

Sie können die Protokolle für Jobs anzeigen und Stages, die gerade ausgeführt werden, auf der Seite mit dem Stageverlaufsprotokoll anzeigen.

1. Um das Protokoll eines Jobs anzuzeigen, klicken Sie auf den Job. Alternativ können Sie in einer Stage auf **Protokolle und Verlauf anzeigen** klicken.

2. Um das Laufzeitprotokoll einer bereitgestellten Anwendung anzuzeigen, klicken Sie auf **Laufzeitprotokoll anzeigen**.

Zusätzlich zu den Jobprotokollen können Sie Komponententestergebnisse, generierte Artefakte und Codeänderungen für beliebige Buildjobs anzeigen.

Sie können ferner eine Stage auf der Seite mit dem Stageverlaufsprotokoll ausführen, abbrechen oder konfigurieren. Klicken Sie auf **AUSFÜHREN**, um die Stage auszuführen, auf **ERNEUT BEREITSTELLEN**, um einen Bereitstellungsjob erneut bereitzustellen, oder auf **KONFIGURIEREN**, um eine Stage zu konfigurieren. Während der Ausführung einer Stage können Sie diese abbrechen, indem Sie auf die Ausführungsnummer und anschließend auf **Abbrechen** klicken.

### Protokolle aus einem Script herunterladen
{: #deliverypipeline_download_logs}

Sie können die Protokolldatei für einen Pipelinejob aus einem Script herunterladen und die `PIPELINE_LOG_URL` speichern, die während der Ausführung des Pipelinejobs bereitgestellt wird. Im folgenden Beispiel finden Sie die Schritte zum Herunterladen der Protokolldatei des Pipelinejobs auf ein anderes System.


1. Richten Sie eine `JOB_LOG`-Umgebungseigenschaft für Ihre Stage ein.

1. Speichern Sie die `PIPELINE_LOG_URL` in Ihrem Pipelinejob.

   ```shell
   export JOB_LOG="$PIPELINE_LOG_URL"
   ```
1. Verwenden Sie die `PIPELINE_LOG_URL` in einem späteren Job in derselben Stage, um die Protokolldatei für den Export auf ein anderes System herunterzuladen. Verwenden Sie ein IBM Cloud-Trägertoken, um auf die Protokolldatei zuzugreifen.

   ```shell
   ibmcloud login -a cloud.ibm.com \
     --apikey <INSERT API KEY HERE>

   BEARER=$( ibmcloud iam oauth-tokens | grep "IAM token" | sed 's/^.*Bearer //g' )

   curl -H "Authorization: Bearer $BEARER"  \
     -H "Accept: text/plain" \
     -D /tmp/headers.txt \
     -o job_log.txt \
     "$JOB_LOG"
   ```
1. Prüfen Sie den Header `X-More-Data`. Wenn der Header auf `true` gesetzt ist, wird die Protokolldatei generiert oder verarbeitet. Wenn der Header auf `false` gesetzt ist, kann die Protokolldatei verwendet werden.

   ```shell
   grep X-More-Data /tmp/headers.txt
   X-More-Data: false
   ```
1. Laden Sie die Protokolldatei auf Ihr System hoch.

   ```shell
   scp job_log.txt user@example.org:/job1/logs
   ```


### Artefakte aus einem Script herunterladen
{: #deliverypipeline_download_artifacts}

Sie können die Artefakte für einen Pipeline-Buildjob aus einem Script herunterladen und die `PIPELINE_ARTIFACT_URL` speichern, die während der Ausführung des Pipelinejobs bereitgestellt wird. Im folgenden Beispiel finden Sie die Schritte zum Hochladen der Artefakte des Pipelinejobs auf ein anderes System.


1. Richten Sie eine `JOB_ARTIFACT`-Umgebungseigenschaft für Ihre Stage ein.

1. Speichern Sie die `PIPELINE_ARTIFACT_URL` in Ihrem Pipelinejob.

   ```shell
   export JOB_ARTIFACT="$PIPELINE_ARTIFACT_URL"
   ```
   
1. Verwenden Sie die `PIPELINE_ARTIFACT_URL` in einem späteren Job in derselben Stage, um die Artefakte für den Export auf ein anderes System herunterzuladen. Verwenden Sie ein IBM Cloud-Trägertoken, um auf die Artefakte zuzugreifen.

   ```shell
   ibmcloud login -a cloud.ibm.com \
     --apikey <INSERT API KEY HERE>

   BEARER=$( ibmcloud iam oauth-tokens | grep "IAM token" | sed 's/^.*Bearer //g' )

   DOWNLOAD_URL=$( curl -H "Authorization: Bearer $BEARER"  \
     "$JOB_ARTIFACT" )

   curl -O  "$DOWNLOAD_URL"
   ```
   
1. Laden Sie die Artefakte auf Ihr System hoch.

   ```shell
   scp $(basename "$DOWNLOAD_URL") user@example.org:/job1/artifacts
   ```
