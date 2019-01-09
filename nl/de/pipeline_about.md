---

copyright:
  years: 2016, 2018
lastupdated: "2018-11-29"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}


# Delivery Pipeline-Überblick
{: #deliverypipeline_about}

{{site.data.keyword.contdelivery_full}} enthält die Delivery Pipeline, die reproduzierbare Builds, Tests und Bereitstellungen ermöglicht und nur geringe manuelle Eingriffe erfordert. In einer Pipeline rufen Abfolgen von Stages Eingabe- und Ausgabejobs wie Builds, Tests und Bereitstellungen ab.
{:shortdesc}

Ihre Berechtigungen zum Anzeigen, Ändern oder Ausführen einer Pipeline basieren auf der Zugriffssteuerung für die Toolchain, die Eigner der Pipeline ist. Weitere Informationen zur Zugriffssteuerung für Toolchains finden Sie in den Abschnitten [Zugriff auf Toolchains in Ressourcengruppen verwalten](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_resource_groups){: new_window} und [Zugriff auf Toolchains in Cloud Foundry-Organisationen verwalten](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_orgs){: new_window}.
{: important}

Sie können die Scripts angeben, die in einer Vielzahl von Jobtypen ausgeführt werden sollen, die von der Pipeline bereitgestellt werden; Sie können darüber steuern, was durch den Job ausgeführt wird. Diese Scripts werden in einem Docker-Image ausgeführt, das eine Reihe von Standardentwicklungstools enthält; dazu gehören Tools, die für die Interaktion mit den {{site.data.keyword.Bluemix_notm}}-Laufzeiten erforderlich sind. Weitere Informationen darüber, was das Standard-Docker-Image enthält, finden Sie im Abschnitt [Vorinstallierte Ressourcen](/docs/services/ContinuousDelivery/pipeline_deploy_var.html#deliverypipeline_resources){: new_window}. Wenn für Ihren Job Entwicklungstools erforderlich sind, die im Standardimage nicht verfügbar sind, oder Sie unterschiedliche Versionen dieser Tools benötigen, können Sie ein angepasstes Image verwenden. Weitere Informationen zu angepassten Images finden Sie im Abschnitt [Mit benutzerdefinierten Docker-Images arbeiten](/docs/services/ContinuousDelivery/pipeline_custom_docker_images.html#custom_docker_images){: new_window}.

Wenn die Pipeline Scripts ausführt, werden die Eigenschaften, die den Kontext beschreiben, in dem der Job ausgeführt wird, an das Script übergeben, und zwar mithilfe von Umgebungsvariablen. Beispiel: Die URL des Repositorys, das die Eingabe für die Stage ist, der Name der Stage und der Job, der ausgeführt wird, die Parameter, die durch den Jobtyp angegeben werden, usw. Informationen zum Anzeigen einer Liste der verfügbaren Umgebungsvariablen finden Sie unter [Vorinstallierte Ressourcen](/docs/services/ContinuousDelivery/pipeline_deploy_var.html#deliverypipeline_envprop){: new_window}. 

Sie können Eigenschaften sowohl auf der Pipeline- als auch auf der Stage-Ebene definieren. Pipeline-Eigenschaften werden über alle Stages und Jobs in einer Pipeline gemeinsam genutzt. Stage-Eigenschaften sind für eine bestimmte Stage eindeutig und werden von allen Jobs dieser Stage gemeinsam genutzt. Weitere Informationen zu Eigenschaften finden Sie unter [Umgebungseigenschaften (Umgebungsvariablen)](/docs/services/ContinuousDelivery/pipeline_about.html#environment_properties).

## Stages
{: #deliverypipeline_stages}

Stages organisieren Eingabe- und Ausgabejobs während ein Build für den Code erstellt, dieser implementiert und getestet wird. Stages akzeptieren Eingaben von den Quellcodeverwaltungsrepositorys (SCM-Repositorys) oder von Build-Jobs in anderen Stages. Bei SCM-Repositorys ist die Eingabe der Inhalt eines bestimmten Zweigs im Repository; bei Build-Jobs handelt es sich bei der Eingabe um die Artefakte, die der Job produziert. Wenn Sie Ihre erste Stage erstellen, sind auf der Registerkarte **EINGABE** die Standardeinstellungen festgelegt.

Wenn eine Stage ausgeführt wird, wird die Eingabe der Stage an die einzelnen Jobs in der Stage übergeben. Jeder Job wird in einem bereinigten Container ausgeführt. Daher können die Jobs in einer Stage einander keine Artefakte übergeben. Um Artefakte zwischen Jobs zu übergeben, unterteilen Sie die Jobs in zwei Stages und verwenden Sie die Ausgabe des Jobs in der ersten Stage als Eingabe für die zweite Stage.
{: tip}

Ähnlich wie Sie Pipeline-Eigenschaften definieren können, können Sie auch Stage-Eigenschaften definieren, die in allen Jobs in einer bestimmten Stage verwendet werden sollen. Sie könnten zum Beispiel die Eigenschaft `TEST_URL` definieren, die eine URL an die Bereitstellungs- und Testjobs in einer Stage übergibt. Der Bereitstellungsjob führt an dieser URL eine Bereitstellung aus und der Testjob testet die App, die an dieser URL ausgeführt wird. Stage-Eigenschaften werden außerdem mithilfe von Umgebungsvariablen an Job-Scripts übergeben. Wenn dieselbe Eigenschaft sowohl auf der Pipeline- als auch auf der Stage-Ebene definiert ist, wird der Wert der Stage-Eigenschaft verwendet.

In einer Stage werden standardmäßig Builds und Bereitstellungen automatisch ausgeführt, sobald Änderungen an ein SCM-Repository des Projekts übermittelt werden. Phasen und Jobs werden seriell ausgeführt. Sie ermöglichen die Ablaufsteuerung für Ihre Arbeit. Sie können zum Beispiel eine Stage für den Test vor einer Stage für die Bereitstellung anordnen. Falls die Tests in der Stage für den Test fehlschlagen, wird die Stage für die Bereitstellung nicht ausgeführt.

Möglicherweise wünschen Sie eine engere Steuerung einer bestimmten Stage. Wenn Sie nicht möchten, dass eine Stage immer dann ausgeführt wird, wenn eine Änderung bei ihrer Eingabe auftritt, können Sie diese Funktion inaktivieren. Klicken Sie auf der Registerkarte **EINGABE** im Abschnitt für Auslöser von Stages auf **Jobs nur ausführen, wenn diese Stage manuell ausgeführt wird**.

![Die Registerkarte EINGABE](images/input_tab_only_execute.png)


### Build-Stage
{: #build_stage}

Die Build-Stage gibt einen **Builder-Typ** an, um darzustellen, wie Artefakte erstellt werden sollen.  

Viele Felder, die in Build-Jobs verfügbar sind, treten buildertypunabhängig auf.
{: tip}

Folgende Builder-Typen sind verfügbar:

* **Einfach** - Jobs, die den Builder-Typ **Einfach** verwenden, nehmen die Eingabe der aktuellen Stage unverändert und archivieren sie für die Verwendung durch zukünftige Stages. In der Regel ist der Buildertyp **Einfach** nur dann nützlich, wenn die Eingabe der Stage aus einem SCM-Repository erfolgt.
* **Ant** - Verwenden Sie diesen Builder-Typ zur Nutzung von Apache Ant-Dateien für die Verwaltung des Build-Jobs.
  * **Build-Script** - Dieser Builder-Typ kann ein beliebtes gültiges Build-Script sein. Standardmäßig ist dieser Builder-Typ auf 'ant' gesetzt.
  * **Arbeitsverzeichnis** - Gibt das Verzeichnis an, in dem das Script ausgeführt wird.
  * **Archivverzeichnis erstellen** - Gibt das Verzeichnis an, das die zu archivierende Ausgabe des Jobs enthält, die von einer nachfolgenden Stage verwendet werden soll.
  * **Testbericht aktivieren** - Wählen Sie dieses Kontrollkästchen aus, um anzugeben, dass der Erstellungsjob Tests ausführt, die Ergebnisdateien im JUnit-XML-Format erzeugen. Auf der Registerkarte 'Tests' auf der Seite 'Jobergebnisse' wird ein Bericht auf der Basis der Ergebnisdateien angezeigt. Wenn ein Test fehlgeschlagen ist, wird der Job als fehlgeschlagen markiert.
  * **Codeabdeckungsbericht aktivieren** - Wählen Sie dieses Kontrollkästchen aus, um weitere Felder anzuzeigen, die Sie für den Codeabdeckungsbericht verwenden können. Sie können den Coverage Runner (z. B. Istanbul, JaCoCo oder Cobertura), die Position der Abdeckungsergebnisdatei sowie das Abdeckungsergebnisverzeichnis angeben; dieses verhält sich zum Arbeitsverzeichnis relativ.
* **Container-Registry**
* **Gradle (Artifactory, Nexus oder SonarQube)**
* **Grunt**
* **IBM Globalization Pipeline**
* **Maven (Artifactory, Nexus oder SonarQube)**
* **npm (Artifactory oder Nexus)**
* **Shell-Script**

### Stage für die Bereitstellung
Die Stage für die Bereitstellung gibt die Eingabe von einer Build-Stage an.  Die Jobs in der Stage für die Bereitstellung geben einen **Deployer-Typ** an.  Folgende Deployer-Typen sind verfügbar:

1. **Cloud Foundry**
2. **Kubernetes**

## Jobs
{: #deliverypipeline_jobs}

Ein Job ist eine Ausführungseinheit innerhalb einer Stage. Eine Stage kann mehrere Jobs enthalten und die Jobs in einer Stage werden nacheinander ausgeführt. Falls ein Job fehlschlägt, werden nachfolgende Jobs in der Stage nicht ausgeführt.

![Build- und Testjobs innerhalb einer Stage](images/jobs.png)

Jobs werden in diskreten Arbeitsverzeichnissen innerhalb von Docker-Containern ausgeführt, die für jede Pipelineausführung erstellt werden. Vor der Ausführung eines Jobs wird sein Arbeitsverzeichnis mit Eingaben gefüllt, die auf der Ebene der Stage definiert wurden. Sie haben beispielsweise eine Stage, die einen Testjob und einen Bereitstellungsjob enthält. Wenn Sie Abhängigkeiten in einem Job installieren, so sind diese für den anderen Job nicht verfügbar. Falls Sie die Abhängigkeiten in der Eingabe der Stage verfügbar machen, stehen Sie beiden Jobs zur Verfügung.

Wenn Sie einen Job konfigurieren, können Sie mit Ausnahme von Buildjobs vom einfachen Typ (Simple), UNIX-Shell-Scripts einbeziehen, die Build-, Test- oder Bereitstellungsbefehle einschießen. Da Jobs in Ad-hoc-Containern ausgeführt werden, können die Aktionen eines Jobs nicht die Ausführungsumgebungen anderer Jobs beeinflussen, selbst wenn diese Jobs Teil derselben Stage sind.

Beispiele für Build- und Bereitstellungsscripts finden Sie in [https://github.com/open-toolchain/commons](https://github.com/open-toolchain/commons).

Darüber hinaus können Pipeline-Jobs nur die folgenden Befehle als `sudo` ausführen:
  * `/usr/sbin/service`
  * `/usr/bin/apt-get`
  * `/usr/bin/apt-key`
  * `/usr/bin/dpkg`
  * `/usr/bin/add-apt-repository`
  * `/opt/IBM/node-v0.10.40-linux-x64/npm`
  * `/opt/IBM/node-v0.12.7-linux-x64/npm`
  * `/opt/IBM/node-v4.2.2-linux-x64/npm`
  * `/usr/bin/Xvfb`
  * `/usr/bin/pip`


Nachdem ein Job ausgeführt wurde, wird der Container, der für ihn erstellt worden ist, gelöscht. Die Ergebnisse eines Jobs können erhalten bleiben, die Umgebung, in der der Job ausgeführt wurde, kann jedoch nicht erhalten bleiben.

Jobs können für eine Dauer von bis zu 60 Minuten ausgeführt werden. Wenn Jobs diesen Grenzwert überschreiten, schlagen sie fehl. Falls ein Job den Grenzwert überschreitet, teilen Sie ihn in mehrere Jobs auf. Wenn ein Job zum Beispiel drei Aufgaben ausführt, können Sie ihn möglicherweise in drei Jobs aufteilen: Ein Job für jede Aufgabe.
{: tip}

Informationen dazu, wie Sie einen Job zu einer Stage hinzufügen, enthält das Thema [Einen Job zu einer Stage hinzufügen](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_add_job){: new_window}.

### Buildjobs

Buildjobs kompilieren Ihr Projekt in Vorbereitung auf die Bereitstellung. Sie generieren Artefakte, die an ein Buildarchivverzeichnis gesendet werden können, obwohl die Artefakte standardmäßig in das Stammverzeichnis des Projekts gestellt werden.

Jobs, die Eingaben von Buildjobs erhalten, müssen Buildartefakte in derselben Struktur referenzieren, in der sie erstellt wurden. Wenn ein Buildjob zum Beispiel Buildartefakte in das Verzeichnis `output` archiviert, würde ein Bereitstellungsscript auf das Verzeichnis `output` und nicht auf das Projektstammverzeichnis verweisen, um das kompilierte Projekt zu implementieren. Sie können das zu archivierende Verzeichnis angeben, indem Sie den Verzeichnisnamen in das Feld **Archivverzeichnis erstellen** eingeben. Wenn Sie das Feld leer lassen, wird das Stammverzeichnis archiviert.

Wenn Sie den Buildertyp **Simple** verwenden, wird Ihr Code nicht kompiliert oder erstellt; er wird gepackt und für zukünftige Stages zur Verfügung gestellt.
{: tip}

Wenn Sie die Bereitstellung mithilfe von Cloud Foundry durchführen, enthält Cloud Foundry die richtigen Artefakte, damit Ihre App ausgeführt werden kann. Weitere Informationen finden Sie unter [Bereitstellung von Anwendungen mit dem Befehl 'cf'](/docs/cloud-foundry/deploy-apps.html#dep_apps). Die Pipeline für eine Cloud Foundry-App enthält eine Stage für die Bereitstellung, die einen Befehl 'cf' ausführt.

Cloud Foundry versucht, das zu [verwendende Buildpack zu erkennen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://docs.cloudfoundry.org/buildpacks/detection.html). Sie können das [Buildpack](/docs/cfapps/byob.html#using-community-buildpacks) angeben, das in der Manifestdatei im Stammordner Ihrer App verwendet werden soll. Buildpacks prüfen in der Regel die vom Benutzer bereitgestellten Artefakte, um festzustellen, welche Abhängigkeiten heruntergeladen werden müssen und wie die Anwendungen für die Kommunikation mit gebundenen Services konfiguriert werden müssen. Weitere Informationen zu Anwendungsmanifesten finden Sie unter [Anwendungsmanifest](/docs/cloud-foundry/deploy-apps.html#appmanifest).

### Bereitstellungsjobs

Bereitstellungsjobs laden Ihr Projekt als eine App in {{site.data.keyword.Bluemix_notm}} hoch und sind über eine URL zugänglich. Nach der Bereitstellung eines Projekts finden Sie die bereitgestellte App in Ihrem {{site.data.keyword.Bluemix_notm}}-Dashboard.

Bereitstellungsjobs können neue Apps bereitstellen oder vorhandene Apps aktualisieren. Auch wenn Sie eine App zuerst mit einer anderen Methode wie beispielsweise über die Cloud Foundry-Befehlszeilenschnittstelle oder die Ausführungsleiste in der Web IDE bereitgestellt haben, können Sie die App mithilfe eines Bereitstellungsjobs aktualisieren. Verwenden Sie den Namen der App, um eine App in einem Bereitstellungsjob zu aktualisieren.

Es ist eine Bereitstellung für eine oder mehrere Regionen bzw. einen oder mehrere Services möglich. Sie können Ihre {{site.data.keyword.deliverypipeline}} beispielsweise so einrichten, dass sie mindestens einen Service verwendet, in einer einzigen Region getestet oder und in mehreren Regionen für die Produktion bereitgestellt wird. Weitere Informationen hierzu finden Sie unter [Regionen](/docs/overview/ibm-cloud.html#ov_intro-reg){: new_window}.

### Testjobs
Wenn Bedingungen eingehalten werden sollen, schließen Sie Testjobs vor oder nach Ihren Build- und Bereitstellungsjobs ein. Sie können Testjobs anpassen, damit diese so einfach oder so komplex wie erforderlich sind. Möglicherweise erwarten Sie eine bestimmte Antwort auf die Ausgabe eine cURL-Befehls. Möglicherweise möchten Sie eine Reihe von Komponententests ausführen oder Funktionstests mit Testservices Dritter wie beispielsweise Sauce Labs ausführen.

Wenn Ihre Tests Ergebnisdateien im JUnit XML-Format erzeugen, wird ein Bericht auf Grundlage der Ergebnisdateien auf der Registerkarte **Tests** jeder Seite mit Testergebnissen angezeigt. Wenn ein Test fehlschlägt, schlägt der Job ebenfalls fehl.

## Umgebungseigenschaften (Umgebungsvariablen)
{: #environment_properties}

Eine Reihe vordefinierter Umgebungseigenschaften bietet Zugriff auf Informationen zur Ausführungsumgebung des Jobs. Eine vollständige Liste der vordefinierten Umgebungseigenschaften finden Sie im Abschnitt zu [Umgebungseigenschaften und Ressourcen](/docs/services/ContinuousDelivery/pipeline_deploy_var.html).

Sie können auch Ihre eigenen Umgebungseigenschaften definieren. Sie können z. B. die Eigenschaft `API_KEY` definieren, mit der ein API-Schlüssel übergeben wird, der für den Zugriff auf {{site.data.keyword.Bluemix_notm}}-Ressourcen durch alle Scripts in der Pipeline verwendet wird.

Sie können die folgenden Typen von Eigenschaften hinzufügen:

* **Text** (Text): Ein Eigenschaftsschlüssel mit einem einzeiligen Wert.
* **Text Area** (Textbereich): Ein Eigenschaftsschlüssel mit einem mehrzeiligen Wert.
* **Secure** (Sicher): Ein Eigenschaftsschlüssel mit einem einzeiligen Wert, der mit der AES-128-Verschlüsselung gesichert ist. Der Wert wird in Form von Sternen angezeigt.
* **Properties** (Eigenschaften): Eine Datei im Projektrepository. Diese Datei kann mehrere Eigenschaften enthalten. Jede Eigenschaft muss in einer eigenen Zeile stehen. Verwenden Sie Gleichheitszeichen (=), um Schlüssel und Werte der Paare zu trennen. Schließen Sie alle Zeichenfolgewerte in Anführungszeichen ein. Beispiel: `MY_STRING="SOME STRING VALUE"`.

Sie können die Umgebungseigenschaften für einen Pipeline-Job prüfen, indem Sie den Befehl `env` im Job-Script ausführen.
{:tip}

### Pipeline-Eigenschaften
Wählen Sie die Option **Pipeline konfigurieren** im Überlaufmenü auf der Seite 'Pipeline' aus, um Pipeline-Eigenschaften zu definieren.

![Überlaufmenü 'Pipeline'](images/OverflowMenu.png)

Geben Sie auf der Registerkarte **Umgebungseigenschaften** auf der Seite 'Pipelinekonfiguration' die Umgebungseigenschaften auf Pipeline-Ebene an.

![Seite mit Pipeline-Eigenschaften](images/PipelineProperties.png)

### Stage-Eigenschaften
Öffnen Sie zur Definition der Stage-Eigenschaften die Seite für die Stage-Konfiguration und klicken Sie auf die Registerkarte **Umgebungseigenschaften**.

![Seite mit Stage-Eigenschaften](images/StageProperties.png)

Sie können die Umgebungseigenschaften auch zwischen Jobs in derselben Stage übergeben, indem Sie die Eigenschaften exportieren. Sie können beispielsweise den folgenden Befehl eingeben, um die Eigenschaft `$API_KEY` in einem weiteren Job in der Stage zu verwenden: `export API_KEY=<API-Schlüssel hier einfügen>`
{:tip}

### Berechnete Eigenschaften
Sie können die Umgebungseigenschaftswerte berechnen, die von mehreren Stages gemeinsam genutzt werden, indem Sie während er Ausführung der Stage eine Datei des Typs `build.properties` erstellen und die nächste Stage diese Datei ausführen lassen. Ihr Build-Job könnte beispielsweise den folgenden Befehl im Build-Script einbeziehen:

  `echo "IMAGE_NAME=${FULL_REPOSITORY_NAME}" >> $ARCHIVE_DIR/build.properties`

Alle Jobs beginnen mit der Ausführung der Datei `build.properties`, sofern sie vorhanden ist.

## Artefakte erstellen und verwenden
{: #artifacts}

Build-Jobs rufen automatisch den Inhalt in dem aktuellen Ordner ab, in dem das Benutzerscript ausgeführt wird.  Wenn Sie nicht den gesamten Git-Repo-Inhalt für eine spätere Bereitstellung benötigen, sollten Sie ein explizites Ausgabeverzeichnis konfigurieren und anschließend die relevanten Artefakte dort kopieren oder erstellen.  Job-Scripts werden im Buildergebnis (Ausgabeverzeichnis) ausgeführt.

Jobs, die Bereitstellungen auf Cloud Foundry ausführen, müssen den Plattform-API-Schlüssel eines Benutzers, mit dessen Berechtigung Jobs ausgeführt werden, sowie die Region, die Organisation und den Bereich angeben, wo die Artefakte bereitgestellt werden sollen. Wenn zur Ausführung Ihrer App weitere Services notwendig sind, müssen Sie sie in der Datei `manifest.yml` angeben.

Bereitstellungsjobs, die Bereitstellungen für den {{site.data.keyword.containerlong_notm}} ausführen, müssen den Plattform-API-Schlüssel eines Benutzers, mit dessen Berechtigung Jobs ausgeführt werden, sowie eine Dockerfile und optional ein Helm-Diagramm angeben.  

Das Job-Script wird ausgeführt, nachdem sich der Job in der Zielumgebung unter Verwendung des ihm zugeordneten Plattform-API-Schlüssels angemeldet hat (damit Sie die Befehle `cf push` oder `kubectl` im Script ausführen können).

## Eine Beispielpipeline
{: #deliverypipeline_example}

Eine einfache Pipeline kann drei Stages enthalten:

1. Eine Stage für den Build, die Erstellungsprozesse auf einer App kompiliert und einen Build ausführt.
2. Eine Stage für den Test, die eine Instanz der App bereitstellt und in dieser Instanz anschließend Tests ausführt.
3. Eine Stage für die Produktion, die eine Produktionsinstanz der getesteten App bereitstellt.

Diese Pipeline wird im folgenden Konzeptionsdiagramm dargestellt:

![Ein Konzeptionsdiagramm der Stages und Jobs in einer Pipeline](images/diagram.jpg)

*Ein konzeptionelles Modell einer Pipeline mit drei Stages*

Stages bekommen Ihre Eingaben von Repositorys und Buildjobs. Jobs innerhalb einer Stage werden nacheinander und unabhängig voneinander ausgeführt. In der Beispielpipeline werden die Stages nacheinander ausgeführt, obwohl die Stages für den Test und die Produktion beide die Ausgabe
der Stage für den Build als Eingabe verwenden.

## Cloud Foundry-Manifestdateien
{: #deliverypipeline_manifest}

Manifestdateien, die den Namen `manifest.yml` tragen und in einem Projektstammverzeichnis gespeichert sind, steuern, wie Ihr Projekt in {{site.data.keyword.Bluemix_notm}} implementiert ist. Informationen zur Erstellung von Manifestdateien für ein Projekt enthält die [{{site.data.keyword.Bluemix_notm}}-Dokumentation zu Anwendungsmanifesten](/docs/cloud-foundry/deploy-apps.html#appmanifest). Für die Integration in {{site.data.keyword.Bluemix_notm}} muss Ihr Projekt über eine Manifestdatei im Stammverzeichnis verfügen. Es ist jedoch nicht erforderlich, dass Sie eine Bereitstellung auf Grundlage der Informationen in der Datei vornehmen.

Sie können in der Pipeline alles angeben, was eine Manifestdatei bei `cf push`-Befehlsargumenten verwenden kann. Die `cf push`-Befehlsargumente sind bei Projekten hilfreich, die über mehrere Bereitstellungsziele verfügen. Falls mehrere Implementierungsjobs versuchen, die Route zu verwenden, die in der Manifestdatei des Projekts angegeben ist, tritt ein Konflikt auf.

Um Konflikte zu vermeiden, können Sie eine Route mithilfe von `cf push` gefolgt vom Hostnamenargument, `-n` und einem Routennamen angeben. Bei der Änderungen des Bereitstellungsscripts für einzelne Stages können Sie Weiterleitungskonflikte vermeiden, wenn Sie mehrere Ziele implementieren.

Öffnen Sie die Konfigurationseinstellungen für einen Bereitstellungsjob und ändern Sie das Feld **Bereitstellungsscript**, um `cf push`-Befehlsargumente zu verwenden. Weitere Informationen enthält die [Dokumentation zur Push-Operation von Cloud Foundry![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html#push){: new_window}.
