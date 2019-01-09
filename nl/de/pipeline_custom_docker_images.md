---

Copyright:
  years: 2018
lastupdated: "2018-12-6"

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


# Mit benutzerdefinierten Docker-Images arbeiten
{: #custom_docker_images}

Das Pipeline-Basisimage unterstützt möglicherweise nicht alle Anforderungen Ihres Builds. Sie brauchen zum Beispiel eine feinere Kontrolle über die Versionen von Node, Java oder anderen Tools. Sie können dieses Problem beheben, indem Sie einen ersten Schritt in Ihre Pipeline-Jobs einfügen, der eine Reihe neuer Pakete installiert und Umgebungsvariablen (wie `PATH`) korrekt konfiguriert, um Ihre Umgebung einzurichten. Ein besserer Ansatz besteht jedoch darin, die Unterstützung der Pipeline zu verwenden, um ein "benutzerdefiniertes Docker-Image" als Grundlage für Ihre Arbeit auszuführen.

Unabhängig davon, ob Sie den Jobtyp "Erstellen", "Test" oder "Bereitstellen" verwenden, können Sie einen untergeordneten Typ des benutzerdefinierten Docker-Images auswählen, um den bereitzustellenden Docker-Imagenamen und das auszuführende Skript anzugeben. Verwenden Sie beispielsweise die folgenden Optionen, um einen Build-Job mit Maven 3.5.3 und IBM Java auszuführen:

 ![Maven-Build mit benutzerdefiniertem Image](images/custom-image-maven-build.png)


## Namen des Docker-Images angeben
{: #docker_image_name}

Der Docker-Imagename in benutzerdefinierten Docker-Imagejobs funktioniert genauso wie Imagenamen mit der Docker-CLI. Das Format für einen Namen eines Docker-Images ist: `[repository][:][tag]`. Beispiel: Für `docker run maven:3.5.3-ibmjava` lautet der Name des Docker-Images `maven:3.5.3-ibmjava`, wobei `maven` das Repository und `3.5.3-ibmjava` das Tag ist. Für Docker-Imagenamen gibt es keine Einschränkungen. Jedes gültige Docker-Image funktioniert.

Wenn das Feld **Docker-Imagename** nicht ausgefüllt wird, wird das standardmäßige Pipeline-Basisimage verwendet. 
{: tip}

Standardmäßig wird Ihr Repository auf [Docker Hub ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://hub.docker.com/){: new_window} durchsucht. Wenn Sie eine andere Docker-Registry verwenden, z. B. {{site.data.keyword.registrylong}}, können Sie den vollständigen DNS-Namen verwenden. Sie können auch den vollständig qualifizierten Namen für Images auf Docker Hub verwenden. Beispiel: `registry.hub.docker.com/library/maven:3.5.3-ibmjava`.

Der `Tag` ist für ein Docker-Image optional. Wenn Sie keinen Tag angeben, wird standardmäßig `latest` festgelegt. Der Standardwert von `latest` ist nur ein Tag-Name, den der Repository-Eigner verwalten muss. Dies bedeutet nicht, dass dieses Docker-Image chronologisch das neueste Image ist.

Eine riesige Community an Repositorys finden Sie unter Docker Hub. IBM hostet zahlreiche öffentliche Repositorys, die das IBM Cloud-Team unter [https://hub.docker.com/u/ibmcom/ ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://hub.docker.com/u/ibmcom/){: new_window} nutzt. Die Repositorys `ibmcom/ibmjava` und `ibmcom/ibmnode` sind gute Basis-Repositorys. 

## Private Image-Registry verwenden
{: #private_image_registry}

Wenn Sie eine private Registry verwenden, für die eine Authentifizierung erforderlich ist, müssen Sie zwei weitere Umgebungseigenschaften festlegen: `DOCKER_USERNAME` und `DOCKER_PASSWORD`. Sie können eine sichere Eigenschaft verwenden, um `DOCKER_PASSWORD` zu maskieren. Bevor Ihr Image abgerufen wird, verwendet der benutzerdefinierte Docker-Imagejob Ihren Benutzer- und Kennwortberechtigungsnachweis, um eine Docker-Anmeldung (`docker login`) abzuschließen.

Für die meisten Registrys können Sie den Benutzernamen und das Passwort verwenden, die Ihnen zur Verfügung gestellt wurden. Wenn Sie {{site.data.keyword.registrylong_notm}} zum Speichern Ihrer privaten Images verwenden, müssen Sie einen Plattform-API-Schlüssel für die Authentifizierung verwenden. 

1. [Fordern Sie einen Plattform-API-Schlüssel ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/iam/#/apikeys){: new_window} an und speichern Sie den API-Schlüssel. 
1. Erstellen Sie zwei Stage-Umgebungseigenschaften, indem Sie `iamapikey` für `DOCKER_USERNAME` sowie den Plattform-API-Schlüssel verwenden, den Sie für `DOCKER_PASSWORD` gespeichert haben.

 ![{{site.data.keyword.registrylong_notm}}-Berechtigungsnachweise](images/custom-image-private-repository.png)


## Script angeben
{: #specify_script}

Sie können den **script**-Block in benutzerdefinierten Docker-Imagejobs verwenden, um eine Scriptdatei zu erstellen, die in einem Task-Ordner ausgeführt wird (so wie bei normalen Pipeline-Jobs). 

`ENTRYPOINT` und `CMD` aus der Dockerfile Ihres Docker-Images werden überschrieben und nicht aufgerufen. In einigen Fällen müssen Sie Ihrem Script möglicherweise Initialisierungsschritte hinzufügen.
{: tip}

Mit benutzerdefinierten Docker-Imagejobs sind Sie bei der Ausführung Ihres Skripts flexibler, vor allem, weil Sie den Befehlsinterpreter steuern können. Wenn die erste Zeile des Scripts und der Name des Befehlsinterpreters mit `#!` beginnen, wird dieser Eintrag verwendet, um die Befehle im Job auszuführen. Wenn Sie keinen Befehlsinterpreter angeben, wird die Standardshell für das Docker-Image verwendet. In der Regel gilt Folgendes: `#!/bin/bash` oder `#!/bin/sh` werden verwendet; Image-Befehlsinterpreter für `awk`, `node` und `ruby` funktionieren auch, wenn Sie ein entsprechendes Docker-Image angeben.
