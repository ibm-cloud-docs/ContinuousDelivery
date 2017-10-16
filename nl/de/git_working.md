---

copyright:
  years: 2015, 2017
lastupdated: "2017-6-8"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:screen:.screen}
{:codeblock:.codeblock}

# {{site.data.keyword.gitrepos}}
{: #git_working}

Arbeiten Sie mit Ihrem Team zusammen und verwalten Sie Ihren Quellcode mit einem Git-Repository- und Problemtracker, der von IBM gehostet wird und auf [GitLab Community Edition ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://about.gitlab.com/){:new_window} basiert.
{: shortdesc}

Die {{site.data.keyword.gitrepos}}-Toolintegration unterstützt Teams auf zahlreiche verschiedene Arten bei der Verwaltung von Code und der Zusammenarbeit:
   * Verwalten Sie Git-Repositorys mittels differenzierter Zugriffssteuerungsmechanismen, durch die der Code geschützt bleibt.
   * Überprüfen Sie den Code und verbessern Sie die Zusammenarbeit durch Zusammenführungsanforderungen (Merge).
   * Verfolgen Sie Probleme und teilen Sie Ihre Ideen durch den Tracker für Probleme mit Anderen.
   * Dokumentieren Sie Projekte auf dem Wiki-System.

**Hinweis:** Da diese Toolintegration auf GitLab Community Edition basiert und von IBM auf Bluemix gehostet wird, sind einige wenige GitLab-Optionen nicht verfügbar. Delivery Pipeline stellt zum Beispiel die kontinuierliche Integration und Continuous Delivery für Bluemix bereit. Aus diesem Grund werden die Features für die kontinuierliche Integration in GitLab nicht unterstützt. Außerdem stehen die Administratorfunktionen nicht zur Verfügung, denn ihre Verwaltung erfolgt durch IBM.

## {{site.data.keyword.gitrepos}} lokal verwenden
{: #git_local}

Sie können auf die Git-Repositorys, die in {{site.data.keyword.gitrepos}} gespeichert sind, lokal zugreifen. Anweisungen zum lokalen Einrichten von Git finden Sie in [Mit der Verwendung von Git über die Befehlszeile beginnen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/help/gitlab-basics/start-using-git){:new_window}. 

**Tipp**: {{site.data.keyword.gitrepos}} unterstützt nur HTTPS-Verbindungen, die TLS1.2 verwenden. Wenn Sie Eclipse für die Verbindungsherstellung verwenden, müssen Sie dieses Protokoll gegebenenfalls für Ihre Java&trade;-Version angeben, indem Sie zu Ihrer Datei 'eclipse.ini' den Eintrag `-Dhttps.protocols=TLSv1.2` hinzufügen und Eclipse anschließend erneut starten.

## Bei {{site.data.keyword.gitrepos}} authentifizieren
{: #git_authentication}

Ihre {{site.data.keyword.Bluemix_notm}}-Anmelde-ID und das Kennwort werden nur zur Authentifizierung bei {{site.data.keyword.gitrepos}} in einem Web-Browser verwendet. Sie können Ihre Benutzerberechtigungsnachweise für {{site.data.keyword.Bluemix_notm}} nicht zum Authentifizieren von externen Git-Clients aus verwenden. Zum Ausführen ferner Git-Operationen wie etwa `Klonen` oder `Push`-Operationen von Ihrem lokalen Git-Repository aus müssen Sie ein persönliches Zugriffstoken oder einen SSH-Schlüssel für die Authentifizierung bei {{site.data.keyword.gitrepos}} verwenden.

### Persönliches Zugriffstoken erstellen
{: #create_pat}

**Wichtig**: Für die Authentifizierung bei Ihrem Git-Repository über HTTPS müssen Sie ein persönliches Zugriffstoken erstellen. 

1. Geben Sie im {{site.data.keyword.gitrepos}}-Dashboard für Benutzereinstellungen auf der [Seite 'Zugriffstoken' ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/profile/personal_access_tokens?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window} den Namen der Anwendung ein, für die Sie ein Zugriffstoken erstellen wollen. Beispiel: `Git-CLI`.
1. Optional: Wählen Sie ein Ablaufdatum für das Zugriffstoken aus.
1. Wählen Sie das Kontrollkästchen **api** aus, um ein persönliches Zugriffstoken zu erstellen, in dem als Bereich 'api' verwendet wird.
1. Klicken Sie auf **Persönliches Zugriffstoken erstellen**. Notieren Sie zur späteren Verwendung den Namen Ihres Zugriffstokens an einem sicheren Ort.
1. Suchen Sie auf der [Seite für das Konto ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/profile/account?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window} im  Abschnitt für Änderungen des Benutzernamens ihren für {{site.data.keyword.gitrepos}} geltenden Benutzernamen. Ihr Benutzername wird außerdem für alle persönlichen Git-Repositorys, die Sie erstellen, als erstes Segment der URL angezeigt.
1. Verwenden Sie Ihren {{site.data.keyword.gitrepos}}-Benutzernamen und Ihr persönliches Zugriffstoken, um sich von einem externen Git-Client aus bei Ihrem Git-Repository zu authentifizieren.

Weitere Informationen enthält [Persönliche Zugriffstoken ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/help/api/README.html#personal-access-tokens){:new_window}.

### SSH-Schlüssel erstellen  
{:create_ssh }

Informationen dazu, wie Sie einen SSH-Schlüssel erstellen, finden Sie in [Vorgehensweise zum Erstellen Ihrer SSH-Schlüssel ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/help/gitlab-basics/create-your-ssh-keys){:new_window}. Wenn Sie mit SSH-Authentifizierung auf Ihre Repositorys zugreifen, sind gegebenenfalls weitere Konfigurationsschritte für Proxys und Firewalls erforderlich.

Weitere Informationen finden Sie in [SSH ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/help/ssh/README){:new_window}.

## Größenbegrenzung für Dateien und Repositorys
{: #git_limits}

Dateien sind grundsätzlich auf 100 MB begrenzt. Für Repositorys gilt eine Größenbegrenzung von 1 GB. Wenn Ihr Repository die Größe von 1 GB überschreitet, erhalten Sie unter Umständen eine E-Mail-Nachricht mit der Aufforderung, die Größe des Repositorys entsprechend zu reduzieren.

## Relevantes Lernprogramm: {{site.data.keyword.gitrepos}}
{: #git_tutorials}

Informieren Sie sich in einem der Lernprogramme zu [IBM&reg; Cloud Garage Method ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/devops/method){:new_window}:

  * [Toolchain erstellen, die {{site.data.keyword.gitrepos}} verwendet ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_cfv2){:new_window}
  * [Microservice-Toolchain mit DevOps Insights (v2) erstellen und verwenden ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_microservices_cd){:new_window}
