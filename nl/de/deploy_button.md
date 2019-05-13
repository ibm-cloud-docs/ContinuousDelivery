---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-27"

keywords: IBM Cloud button, yml file, build file

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# Schaltfläche zum Bereitstellen in {{site.data.keyword.Bluemix_notm}} erstellen {: #deploy-button}

Die Schaltfläche zum Bereitstellen in {{site.data.keyword.Bluemix_notm}} bietet ein effizientes Verfahren, Ihre öffentliche Git-basierte App für die gemeinsame Nutzung bereitzustellen, sodass andere Anwender mit dem Code experimentieren und ihn in {{site.data.keyword.Bluemix_notm}} unter Verwendung einer Toolchain bereitstellen können. Die Schaltfläche erfordert nur minimalen Konfigurationsaufwand und Sie können sie überall dort einfügen, wo Markup unterstützt wird. Beim Anklicken dieser Schaltfläche wird eine geklonte Kopie des Codes in einem neuen Git-Repository (Repo) erstellt, d. h., Ihre ursprüngliche App bleibt unverändert.  
{: shortdesc}

Wenn ein Benutzer auf die Schaltfläche klickt, werden die folgenden Aktionen ausgeführt:

1. Wenn der Benutzer nicht über ein aktives {{site.data.keyword.Bluemix_notm}}-Konto verfügt, muss er ein Konto erstellen. Es kann ein Testkonto oder ein reales Konto erstellt werden.

2. Der Benutzer kann eine Region, eine Ressourcengruppe (verfügbar in den Regionen 'Vereinigte Staaten (Süden)', 'Vereinigte Staaten (Osten)', Vereinigtes Königreich, Deutschland und Tokio) oder eine Organisation und einen Bereich (verfügbar in den Regionen 'Vereinigte Staaten (Süden)', Vereinigtes Königreich und Deutschland) sowie einen App-Namen durch Anklicken des {{site.data.keyword.deliverypipeline}}-Symbols auswählen. Der empfohlene App-Name ist identisch mit dem Toolchain-Namen, der sich aus dem Namen Ihres ursprünglichen Git-Repositorys und einer Zeitangabe zusammensetzt. Der Name der Toolchain kann auch bearbeitet werden.

3. Es wird eine Toolchain erstellt, die einen neuen privaten Klon Ihres Git-Repositorys, eine Pipeline für das Erstellen und Bereitstellen von Änderungen, die Eclipse Orion-{{site.data.keyword.webide}} für die Codebearbeitung in der Cloud und einen Tracker für Probleme umfasst.

  Wenn das Verzeichnis `.bluemix` eine Datei `toolchain.yml` enthält, wird die Datei verwendet, um die Toolintegrationen für die Toolchain anzugeben. Weitere Informationen zur Datei `toolchain.yml` finden Sie unter [Angepasste Toolchains erstellen](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_custom){: new_window}.
  {: tip}

4. Wenn für die App eine Builddatei erforderlich ist, wird die Builddatei automatisch erkannt und die App wird erstellt.

5. Wenn eine Pipeline für den Erstellungs- und Bereitstellungsprozess konfiguriert ist, wird eine Datei `pipeline.yml` verwendet, um die App bereitzustellen.

6. Wenn für die App ein Container erforderlich ist, werden eine Datei `pipeline.yml`, die den {{site.data.keyword.containerlong_notm}} definiert, und eine Dockerfile, die ein Image definiert, zur Bereitstellung der App im {{site.data.keyword.containerlong_notm}} verwendet.

7. Die App wird in der {{site.data.keyword.Bluemix_notm}}-Organisation bereitgestellt, die der Benutzer ausgewählt hat.

## Beispiele für die Schaltfläche {: #button-examples}

Das folgende Beispiel zeigt eine App-Schaltfläche für ein öffentliches {{site.data.keyword.gitrepos}}-Repository:

[![In IBM Cloud bereitstellen](https://cloud.ibm.com/devops/setup/deploy/button.png)](https://cloud.ibm.com/devops/setup/deploy?repository=https://git.ng.bluemix.net/idsorg/sample-java-cloudant){:new_window}

Das folgende Beispiel zeigt eine App-Schaltfläche für ein öffentliches GitHub-Repository:

[![In IBM Cloud bereitstellen](https://cloud.ibm.com/devops/setup/deploy/button.png)](https://cloud.ibm.com/devops/setup/deploy?repository=https://github.com/open-toolchain/starfighter){:new_window}

## Schaltfläche erstellen {: #create-button}

Um eine Schaltfläche für das Bereitstellen in {{site.data.keyword.Bluemix_notm}} zu erstellen, kopieren und ändern Sie eine der folgenden Snippetvorlagen. Geben Sie ein Git-Repository und eine Verzweigung in der URL ein.

### Schaltfläche in HTML erstellen

Um eine Schaltfläche in HTML zu erstellen, kopieren Sie dieses Snippet und fügen Sie eine öffentliche Git-Repository-URL und eine Verzweigung ein.

```HTML
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=<git_repository_URL>&branch=<git_branch>"><img src="https://cloud.ibm.com/devops/setup/deploy/button.png" alt="In IBM Cloud bereitstellen"></a>
```
{: codeblock}

Wenn Sie den Parameter `branch` nicht in die Repository-URL Ihres Snippets einfügen, wird für die Schaltfläche für die Bereitstellung in {{site.data.keyword.Bluemix_notm}} standardmäßig der Masterzweig des Repositorys verwendet.

### Schaltfläche in Markdown erstellen

Um eine Schaltfläche in Markdown zu erstellen, kopieren Sie dieses Snippet und fügen Sie eine öffentliche Git-Repository-URL und eine Verzweigung ein.

```Markdown
[![Deploy to IBM Cloud](https://cloud.ibm.com/devops/setup/deploy/button.png)](https://cloud.ibm.com/devops/setup/deploy?repository=<git_repository_URL>&branch=<git_branch>)
```
{: codeblock}

Wenn Sie den Parameter `branch` nicht in die Repository-URL Ihres Snippets einfügen, wird für die Schaltfläche für die Bereitstellung in {{site.data.keyword.Bluemix_notm}} standardmäßig der Masterzweig des Repositorys verwendet.

### Snippets für Schaltflächen verwenden {: #button-snippet}

Nachdem Sie ein Snippet für eine Schaltfläche für die Bereitstellung in {{site.data.keyword.Bluemix_notm}} erstellt haben, können Sie es in Blogs, Artikel, Wikis, Readme-Dateien oder anderswo einfügen, um für Ihre App zu werben.

Wenn Sie das Snippet für die Schaltfläche zur Bereitstellung in {{site.data.keyword.Bluemix_notm}} anpassen, müssen Sie beachten, dass die beiden Vorlagen einen Standardpfad zu einer externen Schaltflächengrafik im PNG-Format und in englischer Sprache verwenden.

* Wenn Sie für die Schaltfläche lieber eine SVG- als eine PNG-Grafik verwenden möchten, ändern Sie den Pfad zur Schaltflächengrafik im Snippet in `https://cloud.ibm.com/devops/setup/deploy/button.svg`.

* Wenn Sie für die Schaltfläche lieber eine Abbildung verwenden möchten, ändern Sie den Pfad der Schaltflächengrafik im Snippet in `https://cloud.ibm.com/devops/setup/deploy/button_x2.png`. Diese Abbildung ist zweimal so groß wie die Standardabbildung.

* Wenn Sie die Abbildung lieber lokal speichern möchten, können Sie die Abbildung herunterladen und in Ihrem Git-Repository speichern. Passen Sie den Pfad an die relative Position der Abbildung an.

* Wenn Sie eine übersetzte Version der Schaltfläche verwenden möchten, können Sie über Fernzugriff auf sie verweisen oder sie von folgender Site herunterladen: [ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button){:new_window}.

## Hinweise zum Repository {: #button-repo}

Beachten Sie die folgenden Hinweise zu dem Repository, das Sie in Ihrer Schaltfläche für die Bereitstellung in {{site.data.keyword.Bluemix_notm}} verwenden.


### Erfordernis einer Builddatei
{: build_file}

Wenn ein Build der App erforderlich ist, bevor sie bereitgestellt werden kann, müssen Sie eine Builddatei in Ihr Repository einfügen. Wenn eine Build-Script-Datei im Stammverzeichnis des Repositorys erkannt wird, wird ein automatisierter Build des Codes vor der Bereitstellung ausgelöst.

Unterstützte Buildprogramme:

* [Ant ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link"):](http://ant.apache.org/manual/using.html){:new_window} `build.xml` erstellt Ausgabe im Ordner `./output/`
* [Gradle ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link"):](https://docs.gradle.org/current/userguide/getting_started.html){:new_window} `/build.gradle` erstellt Ausgabe im Ordner `.` .
* [Grunt ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link"):](http://gruntjs.com/getting-started#the-gruntfile){:new_window} `/Gruntfile.js` erstellt Ausgabe im Ordner `.` .
* [Maven ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link"):](http://maven.apache.org/guides/introduction/introduction-to-the-pom.html){:new_window} `/pom.xml` erstellt Ausgabe im Ordner `./target/`.

### Erfordernis einer Pipelinedatei
{: pipeline_file}

Um die Pipeline für die Toolchain in einem Verzeichnis `.bluemix` zu konfigurieren, fügen Sie eine Datei `pipeline.yml` ein. Für jede Datei `pipeline.yml` in diesem Verzeichnis wird eine Pipeline erstellt, wenn die Toolchain instanziiert wird.

Wenn die Datei `pipeline.yml` sich nicht im `.bluemix`-Verzeichnis befindet, erstellt die Schaltfläche für die Bereitstellung zu {{site.data.keyword.Bluemix_notm}} eine Standard-Pipeline mit zwei Stages: eine Build-Stage und eine Stage für eine Bereitstellung auf Cloud Foundry.

Beim Erstellen einer Pipelinedatei können Sie sich an dem Beispiel bei den [Anweisungen zum Erstellen einer angepassten Toolchain-Pipeline](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_custom#toolchains_custom_pipeline_yml) orientieren. Genau wie beim Definieren einer Pipeline in der Webschnittstelle definieren Sie eine Pipeline im Text, indem Sie Stages und Jobs erstellen, Eingaben und Umgebungsvariablen festlegen und Scripts hinzufügen. In [diesem Demonstrationsprojekt](https://github.com/open-toolchain/toolchain-demo/tree/master/.bluemix) wird auch eine Reihe komplexerer Pipelinedateien angezeigt.

### Erfordernis einer Container-Dockerfile
{: container_dockerfile}

Um eine App in einem Container mithilfe von {{site.data.keyword.containerlong_notm}} bereitzustellen, müssen Sie eine Dockerfile in das Stammverzeichnis des Repositorys einfügen und eine Datei `pipeline.yml` in ein Verzeichnis `.bluemix` stellen.

Die Dockerfile fungiert als eine Art Build-Script für die App. Wenn eine Dockerfile im Repository festgestellt wird, wird die App automatisch in einem Image erstellt, bevor sie in einem Container bereitgestellt wird. Wenn ein Build der App erforderlich ist, bevor sie in einem Image erstellt werden kann, fügen Sie ein Build-Script für die App und eine Dockerfile hinzu.

Informationen zum Erstellen von Dockerfiles enthält die [Docker-Dokumentation ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://docs.docker.com/reference/builder/){:new_window}. Schritt-für-Schritt-Anweisungen zur Verwendung einer Toolchain-Vorlage für die Bereitstellung in Kubernetes finden Sie in [Lernprogramm: Toolchain zur Entwicklung einer Kubernetes-App verwenden ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-toolchain?task=0){:new_window} oder [Lernprogramm: Toolchain zur Entwicklung einer Kubernetes-App mit Helm verwenden ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-with-helm-toolchain?task=0){:new_window}.

Informationen zum Portieren Ihrer Cloud Foundry-App zu einem Kubernetes-Cluster finden Sie in [Lernprogramm: Eine Cloud Foundry-App zur Bereitstellung in Kubernetes in einer Toolchain portieren ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/cloud/garage/tutorials/port-a-cf-app-to-deploy-to-kubernetes-in-a-toolchain?task=0){:new_window}.  

Informationen zum manuellen Erstellen einer Datei `pipeline.yml` speziell für Container finden Sie unter [Beispiele in GitHub ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/Puquios/){:new_window}.

### Anforderungen an Manifestdateien (für Apps, die auf Cloud Foundry bereitgestellt werden)<²
{: #manifest_files}

In Ihrem Repository muss keine Datei `manifest.yml` enthalten sein. Wenn Ihre App aber die Ausführung anderer Services voraussetzt, müssen Sie eine Manifestdatei zur Verfügung stellen, die diese Services deklariert.

Mehr zu Manifestdateien erfahren Sie unter [Anwendungsmanifest](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest).
