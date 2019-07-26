---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-20"

keywords: Git Repos, Issue Tracking, Collaborate, Git repository

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# {{site.data.keyword.gitrepos}}
{: #git_working}

Arbeiten Sie mit Ihrem Team zusammen und verwalten Sie Ihren Quellcode mit einem Git-Repository- und Problemtracker, der von IBM gehostet wird und auf [GitLab Community Edition](https://about.gitlab.com/){: external} basiert.
{: shortdesc}

Laden Sie nur Personen für eine Zusammenarbeit an einem Projekt ein, mit denen Sie eine persönliche oder geschäftlicher Beziehung haben. Benutzern, die eine Einladung zu einem Git-Repository nicht für eine Zusammenarbeit an einem Projekt verwenden, wurde der Zugriff auf den Service möglicherweise entzogen oder sie pausieren ihren Zugriff auf den Service.
{: important}

GitHub und die Git-Befehlszeile sind barrierefreie Alternativen zu GitLab.
{: note}

Speichern Sie keine regulierten Daten in Dateien oder Issues in Git-Repositorys. Derzeit sind keine Prozeduren für regulierte Daten in Kraft.
{: tip}

Die {{site.data.keyword.gitrepos}}-Toolintegration unterstützt Teams auf zahlreiche verschiedene Arten bei der Verwaltung von Code und der Zusammenarbeit:
   * Verwalten Sie Git-Repositorys mittels differenzierter Zugriffssteuerungsmechanismen, durch die der Code geschützt bleibt.
   * Überprüfen Sie den Code und verbessern Sie die Zusammenarbeit durch Zusammenführungsanforderungen (Merge).
   * Verfolgen Sie Probleme und teilen Sie Ihre Ideen durch den Tracker für Probleme mit Anderen.
   * Dokumentieren Sie Projekte auf dem Wiki-System.

Da diese Toolintegration auf GitLab Community Edition basiert und von IBM auf der {{site.data.keyword.Bluemix_notm}}-Plattform gehostet wird, sind einige wenige GitLab-Optionen nicht verfügbar. Delivery Pipeline stellt zum Beispiel die kontinuierliche Integration und Continuous Delivery für {{site.data.keyword.Bluemix_notm}} bereit. Aus diesem Grund werden die Features für die kontinuierliche Integration in GitLab nicht unterstützt. Außerdem stehen die Administratorfunktionen nicht zur Verfügung, denn ihre Verwaltung erfolgt durch IBM.
{: tip}


## {{site.data.keyword.gitrepos}} lokal verwenden
{: #git_locally}

Sie können auf die Git-Repositorys, die in {{site.data.keyword.gitrepos}} gespeichert sind, lokal zugreifen. Anweisungen zum lokalen Einrichten von Git finden Sie in [Mit der Verwendung von Git über die Befehlszeile beginnen](https://us-south.git.cloud.ibm.com/help/gitlab-basics/start-using-git){: external}.

{{site.data.keyword.gitrepos}} unterstützt nur HTTPS-Verbindungen, die TLS1.2 verwenden. Wenn Sie Eclipse für die Verbindungsherstellung verwenden, müssen Sie dieses Protokoll gegebenenfalls für Ihre Java&trade;-Version angeben, indem Sie zu Ihrer Datei 'eclipse.ini' den Eintrag `-Dhttps.protocols=TLSv1.2` hinzufügen und Eclipse anschließend erneut starten.
{: tip}

## Authentifizierung mit {{site.data.keyword.gitrepos}}
{: #git_authentication}

Ihre {{site.data.keyword.Bluemix_notm}}-Anmelde-ID und das Kennwort werden nur zur Authentifizierung bei {{site.data.keyword.gitrepos}} in einem Web-Browser verwendet. Sie können Ihre Benutzerberechtigungsnachweise für {{site.data.keyword.Bluemix_notm}} nicht zum Authentifizieren von externen Git-Clients aus verwenden. Zum Ausführen ferner Git-Operationen wie etwa `Klonen` oder `Push`-Operationen von Ihrem lokalen Git-Repository aus müssen Sie ein persönliches Zugriffstoken oder einen SSH-Schlüssel für die Authentifizierung bei {{site.data.keyword.gitrepos}} verwenden.

### Persönliches Zugriffstoken erstellen
{: #create_pat}

Für die Authentifizierung bei Ihrem Git-Repository über HTTPS müssen Sie ein persönliches Zugriffstoken erstellen.
{: tip}

1. Geben Sie im {{site.data.keyword.gitrepos}}-Dashboard für Benutzereinstellungen auf der [Seite für Zugriffstokens](https://us-south.git.cloud.ibm.com/profile/personal_access_tokens){: external} den Namen der Anwendung ein, für die Sie ein Zugriffstoken erstellen möchten. Beispiel: `Git-CLI`.
1. Optional: Wählen Sie ein Ablaufdatum für das Zugriffstoken aus.
1. Wählen Sie das Kontrollkästchen **api** aus, um ein persönliches Zugriffstoken zu erstellen, in dem als Bereich 'api' verwendet wird.
1. Klicken Sie auf **Persönliches Zugriffstoken erstellen**. Notieren Sie zur späteren Verwendung den Namen Ihres Zugriffstokens an einem sicheren Ort.
1. Suchen Sie auf der [Seite für das Konto](https://us-south.git.cloud.ibm.com/profile/account){: external} im Abschnitt für Änderungen des Benutzernamens Ihren für {{site.data.keyword.gitrepos}} geltenden Benutzernamen. Ihr Benutzername wird außerdem für alle persönlichen Git-Repositorys, die Sie erstellen, als erstes Segment der URL angezeigt.
1. Verwenden Sie Ihren {{site.data.keyword.gitrepos}}-Benutzernamen und Ihr persönliches Zugriffstoken, um sich von einem externen Git-Client aus bei Ihrem Git-Repository zu authentifizieren.

Weitere Informationen finden Sie unter [Persönliche Zugriffstokens](https://us-south.git.cloud.ibm.com/help/api/README.html#personal-access-tokens){: external}.

### SSH-Schlüssel erstellen  
{:create_ssh }

Informationen zum Erstellen eines SSH-Schlüssels finden Sie in [Vorgehensweise beim Erstellen Ihrer SSH-Schlüssel](https://us-south.git.cloud.ibm.com/help/gitlab-basics/create-your-ssh-keys){: external}. Wenn Sie mit SSH-Authentifizierung auf Ihre Repositorys zugreifen, sind gegebenenfalls weitere Konfigurationsschritte für Proxys und Firewalls erforderlich.

Weitere Informationen finden Sie unter [SSH](https://us-south.git.cloud.ibm.com/help/ssh/README){: external}.

## Größenbegrenzung für physische Dateien und Repositorys
{: #git_limits}

Dateien sind grundsätzlich auf 100 MB begrenzt. Für Repositorys gilt eine Größenbegrenzung von 1 GB. Wenn Ihr Repository die Größe von 1 GB überschreitet, erhalten Sie unter Umständen eine E-Mail-Nachricht mit der Aufforderung, die Größe des Repositorys entsprechend zu reduzieren.

## Relevantes Lernprogramm: {{site.data.keyword.gitrepos}}
{: #git_tutorials}

Informieren Sie sich in einem dieser Lernprogramme in [IBM&reg; Cloud Garage Method](https://www.ibm.com/cloud/garage){: external}:

  * [Erste Toolchain mithilfe der Toolchain zum Entwickeln einer Cloud Foundry-App erstellen und verwenden](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){: external}. Erfahren Sie, wie Sie eine offene Toolchain aus einer Vorlage erstellen und die Toolchain für die fortlaufende Bereitstellung einer 'Hello World'-App verwenden.

  * [Toolchain zum Entwickeln und Testen von Microservices auf Cloud Foundry verwenden](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){: external}. Erfahren Sie, wie Sie mithilfe einer Vorlage mit drei Microservices eine Toolchain erstellen und mithilfe der Toolchain ein Onlinegeschäft kontinuierlich bereitstellen.
