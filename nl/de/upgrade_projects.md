---

copyright:
  years: 2015, 2018
lastupdated: "2018-8-2"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Upgrade Ihres {{site.data.keyword.jazzhub_short}}-Projekts zu einer Toolchain durchführen
{: #upgrade_projects}

Aus {{site.data.keyword.jazzhub}} wird künftig {{site.data.keyword.contdelivery_full}}. Als Teil dieser Änderungen wird für Projekte ein Upgrade auf Toolchains durchgeführt.

Sie können ein Upgrade für Ihr Projekt durchführen oder warten, bis das Upgrade automatisch vorgenommen wird. Die optimale
Benutzererfahrung ergibt sich, wenn Sie sicherstellen, dass die [Voraussetzungen](#upgrade_prereqs) erfüllt sind und Sie für
Ihr Projekt so bald wie möglich das Upgrade durchführen, damit Sie steuern können, wie der Name Ihrer Toolchain lautet und in welcher
Organisation sie erstellt wird.
{: shortdesc}

**Häufig gestellte Fragen**

- [Mein JazzHub-Projekt ist Großbritannien (GB) als geografischer Region zugeordnet, die Toolchain wird sich jedoch im Süden der USA befinden. Wie wird das funktionieren?](#faq_region)
- [Was geschieht beim Durchführen eines Upgrades mit meinen Arbeitselementen und Dashboards in Track &amp; Plan?](#faq_tp)
- [Was geschieht beim Durchführen eines Upgrades mit meinem Code-Repository?](#faq_repo)
- [Was geschieht beim Durchführen eines Upgrades auf eine Toolchain mit den Builddefinitionen in meinem Projekt?](#faq_build)
- [Ich muss für mein Projekt, für das ein Upgrade auf eine Toolchain durchgeführt wird, eine Organisation erstellen. Mir ist bewusst, dass ich eine Kreditkarte zu meinem Konto hinzufügen muss, bevor ich die Organisation erstellen kann. Wird diese Kreditkarte belastet?](#faq_charges)
- [Ich kann meine Toolchain nicht finden oder auf sie zugreifen. Was soll ich tun? ](#faq_find)
- [Mein Projekt ist Großbritannien (GB) als geografischer Region zugeordnet. Nach dem Upgrade werden Fehlernachrichten angezeigt, meine Kollegen können nicht auf die Toolchain zugreifen und ich sehe meine Toolchain nicht auf der Seite 'Toolchains' in der {{site.data.keyword.Bluemix_notm}} Plattform. Was stimmt nicht?](#faq_uk)

## Toolchains
{: #compare_toolchains}

Toolchains ähneln Projekten, weisen jedoch einige wichtige Unterschiede auf:

- Projekte können nur über ein Repository (repo) und eine Pipeline verfügen. Toolchains können so viele Repositorys und Pipelines besitzen wie nötig.
- Toolchains können Tools enthalten, die in Projekten nicht verfügbar sind, wie zum Beispiel Slack, Sauce Labs, PagerDuty und {{site.data.keyword.DRA_full}}.
- Der Zugriff auf Toolchains wird über standardmäßige {{site.data.keyword.Bluemix_notm}}-Organisationen verwaltet. Die Mitgliedschaft wird auf Organisationsebene gepflegt, wohingegen bei Projekten die Pflege von Mitgliedschaften auf Projektebene erfolgt.

Mehr zu Toolchains erfahren Sie in [YouTube![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://youtu.be/2SIPE1e7NJ4){: new_window} oder in der [Einführung in {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery/index.html).
[![Externer Link zu YouTube](images/CD_video.png)](https://youtu.be/2SIPE1e7NJ4){: new_window}

## Voraussetzungen
{: #upgrade_prereqs}

- Für den Zugriff auf die Toolchain Ihres aktualisierten Projekts benötigen Sie eine {{site.data.keyword.Bluemix_notm}}-ID. Vor der Durchführung des Upgrades müssen Sie daher sicherstellen, dass Sie über eine aktive {{site.data.keyword.Bluemix_notm}}-ID verfügen. Sollte das nicht der Fall sein, müssen Sie sich [anmelden](https://console.ng.bluemix.net/registration/).
- tellen Sie sicher, dass die Angabe für Ihren {{site.data.keyword.jazzhub_short}}-Projekteigner richtig ist. Die Toolchain, die auf der Grundlage Ihres Projekts erstellt wird, ist künftig Teil der {{site.data.keyword.Bluemix_notm}}-Organisation dieses Eigners.
- Stellen Sie sicher, dass sich die Organisation und der Bereich, in der/dem Sie Ihre Toolchain erstellen wollen, unter {{site.data.keyword.Bluemix_notm}} Public in der Region 'Vereinigte Staaten (Süden)' befinden. Um zu bestätigen, dass Sie eine gültige Organisation und einen gültigen Bereich in der Region 'Vereinigte Staaten (Süden)' haben, melden Sie sich unter [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window} an und erstellen Sie einen Bereich, wenn Sie dazu aufgefordert werden.
- Stellen Sie bei der Planung für den Start des Upgrades sicher, dass Sie in jeder Organisation und jedem Bereich, in dem die Bereitstellung durch die Pipeline erfolgt, Mitglied sind. Die Durchführung des Upgrades kann von einem beliebigen Projektadministrator
gestartet werden. Wenn jedoch der Administrator, der die Durchführung des Upgrades startet, nicht Mitglied aller Organisationen und Bereiche ist, in denen die Bereitstellung durch die Pipeline erfolgt, kann die Pipeline nicht erstellt werden. Die Person, die die Durchführung des Upgrades startet, wird Eigner des Repositorys in der Toolchain.
- Die Eclipse Orion-Web-IDE in der Toolchain funktioniert gesondert von der Web-IDE, die Ihrem Projekt zugeordnet ist. Wenn Sie die {{site.data.keyword.webide}} verwenden und nicht festgeschriebene Änderungen vorliegen, führen Sie einen Commit für diese Änderungen aus, bevor Sie das Upgrade durchführen.


## Upgrade eines Projekts zu einer Toolchain durchführen
{: #project_to_toolchain}

Projekte unter hub.jazz.net und Toolchains werden im Süden der USA gehostet. Wenn Ihr Projekt
für die Bereitstellung von Apps in anderen Regionen konfiguriert wurde, wird es auch nach dem Upgrade auf eine Toolchain weiterhin Apps
in diesen Regionen bereitstellen.
{: tip}

Wenn Ihr Projekt bereit für das Upgrade ist, wird eine Nachricht auf der Karte des Projekts und auf seiner Übersichtsseite angezeigt.

![Abbildung der Karte mit der Bezeichnung 'Bereit für Upgrade'](images/card-project-to-upgrade.png)

![Nachricht 'Es ist an der Zeit für das Upgrade'](images/banner-ready-to-upgrade.png)

Im Menü auf der Seite 'Meine Projekte' finden Sie Projekte, die bereit für das Upgrade sind:

![Abbildung des Menüelements 'Projekte für Upgrade'](images/menu-projects-to-upgrade.png)
{: tip}

Wenn Sie die Durchführung des Upgrades starten, sind die Pipeline-Stages in Ihrem Projekt gesperrt. Sie können sie weder ausführen noch ändern. Wenn Sie das Upgrade durch Löschen der Toolchain zurücksetzen, wird die Pipeline entsperrt.

Wenn in Ihrem Projekt ein Git-Repository verwendet wird, das unter JazzHub gehostet wird, wird das Repository nach dem Start des Upgrades
gesperrt, um die Integrität der Daten sicherzustellen, die in die Toolchain verschoben werden. Wenn Sie das Upgrade durch Löschen der Toolchain
zurücksetzen, wird das Repository unter JazzHub entsperrt.

Vollständige Details zur Handhabung der einzelnen Repository-Typen im Rahmen des Upgradeprozesses finden Sie in der
folgenden Tabelle.

|Projektrepository |Projekttyp	|Toolchain-Repository |
|:----------|:------------------------------|:------------------|
|github.com 		|Privat oder öffentlich 		|Dasselbe github.com-Repository mit {{site.data.keyword.Bluemix_notm}} Public.	|
|hub.jazz.net/git		|Privat oder öffentlich 		|Ein neues Repository in {{site.data.keyword.gitrepos}} mit {{site.data.keyword.Bluemix_notm}} Public.	|
{: caption="Tabelle 1. Zuordnung von Projektrepositorys zu Toolchain-Repositorys" caption-side="top"}

## Upgradeprozess starten
{: #start_upgrade}

Bevor Sie den Upgradeprozess starten, können Sie ihn sich auf [YouTube![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://youtu.be/LSr2e3uvyLs){: new_window} in Aktion ansehen.
[![Externer Link zu YouTube](images/migration-video2.png)](https://youtu.be/LSr2e3uvyLs){: new_window}

Führen Sie die folgenden Schritte aus, um für Ihr Projekt das Upgrade auf eine Toolchain durchzuführen:

1. Starten Sie den Upgradeprozess. Klicken Sie dazu in der Bannernachricht auf **Jetzt Upgrade durchführen**. Die Seite für das Upgrade des Projekts zu einer Toolchain wird angezeigt.

   ![Beispiel für eine Upgradeseite](images/project-upgrade-toolchain.png)

   Einen Überblick über den Upgradeprozess können Sie sich verschaffen, indem Sie die Beschreibung auf dieser Seite lesen. Die Toolchain wird eine neue Pipeline enthalten, die dieselben Stages und Jobs wie die Pipeline des Projekts enthält. Außerdem enthält die Toolchain einen Verweis auf die Eclipse Orion-{{site.data.keyword.webide}}, die in {{site.data.keyword.contdelivery_short}} ausgeführt wird.

   Da das Projekt ein öffentliches Repository unter github.com verwendet, wird für die Toolchain in diesem Beispiel eine Verbindung zum
selben
GitHub-Repository hergestellt. Wenn Ihr Projekt ein Git-Repository verwendet, das unter JazzHub gehostet wird, werden die Inhalte dieses
Repositorys durch Klonen in einem neuen Repository in {{site.data.keyword.gitrepos}} bereitgestellt, das Teil von
{{site.data.keyword.contdelivery_short}} ist.

2. Durch Konfigurieren einiger Einstellungen können Sie die Toolchain anpassen:

   - Wenn Sie den Namen der Toolchain ändern wollen, bearbeiten Sie das Feld **Name**.

      ![Feld 'Name'](images/name-change.png)

   - Wenn Sie ändern wollen, in welcher {{site.data.keyword.Bluemix_notm}}-Organisation die Toolchain erstellt wird, wählen Sie die gewünschte Organisation im Menü Ihres Kontos aus:

      ![{{site.data.keyword.Bluemix_notm}} Auswahlfunktion für Organisation](images/bluemix-organization-chooser.png)

   Da die Verwaltung von Toolchains auf Organisationsebene erfolgt, müssen Sie unbedingt eine Organisation auswählen, bei der die Projektmitglieder, die Zugriff auf die Toolchain benötigen, entweder vorhanden sind oder aber hinzugefügt werden können.

3. Falls Sie in Ihrem Projekt Track & Plan verwendet haben, können Sie Ihre Track & Plan-Daten an GitHub Issues übertragen.

   ![Track and Plan - Optionen](images/upgrade-tutorial-track-and-plan.png)

   - Geben Sie an, ob Sie Ihre Track & Plan-Daten migrieren möchten.
   - Standardmäßig werden alle Ihre Track & Plan-Daten migriert. Wenn Sie es vorziehen, nur die Arbeitselemente zu migrieren,
die Teil einer bestimmten Abfrage sind, müssen Sie diese Abfrage angeben.
   - Wählen Sie alle Arbeitselementattribute aus, die Sie Bezeichnungen in GitHub Issues zuordnen wollen.

4. Klicken Sie auf **Erstellen**. Die neue Toolchain wird erstellt und ihre Übersichtsseite wird angezeigt.

   ![Übersicht über die Toolchain, für die das Upgrade durchgeführt wurde](images/new-toolchain-page.png)

   - Wenn Sie auf Ihr GitHub-Repository oder den Tracker für zugehörige Probleme zugreifen wollen, klicken Sie auf **GitHub** oder auf **Probleme**.
   - Wenn Sie auf die Pipeline zugreifen wollen, klicken Sie auf **Delivery Pipeline**.
   - Wenn Sie auf die {{site.data.keyword.webide}} zugreifen wollen, die diejenigen Inhalte Ihres Repositorys enthält, die in den Arbeitsbereich ausgecheckt waren, klicken Sie auf **Eclipse Orion-{{site.data.keyword.webide}}**.

   Wenn Sie während der Durchführung des Upgrades zu Ihrem Projekt zurückkehren, wird in der Bannernachricht möglicherweise angezeigt,
dass das Upgrade in Bearbeitung ist, insbesondere, wenn der Upgradeprozess das Importieren von Quellcode in ein neues Repository oder das
Importieren von Track &amp; Plan-Arbeitselementen als Arbeitsschritte umfasst.

   ![Nachricht, dass für ein Projekt ein Upgrade auf eine Toolchain durchgeführt wird](images/project-being-upgraded-banner.png)

## Projekt nochmals bearbeiten
{: #revisit_projects}

Sie können jetzt Ihre neue Toolchain verwenden. Ihr Projekt ist jetzt mit der Bezeichnung 'Upgrade durchgeführt' versehen und auf der Übersichtsseite wird eine Bestätigungsnachricht angezeigt.

![Abbildung der Projektkarte mit der Bezeichnung 'Upgrade durchgeführt'](images/card-upgraded-project.png)

![Projekt mit erfolgtem Upgrade](images/banner-upgraded.png)

Durch Auswahl der Option **Projekte mit erfolgtem Upgrade** im Menü auf der Seite 'Meine Projekte' können Sie anzeigen, für welche Projekte das Upgrade bereits durchgeführt wurde:

![Abbildung des Menüelements 'Projekte mit erfolgtem Upgrade'](images/menu-upgraded-projects.png)

Falls es erforderlich ist, das Upgrade zurückzusetzen, löschen Sie die Toolchain. Sie können Ihre Toolchain im Menü **Weitere Aktionen** auf der Toolchain-Seite 'Übersicht' löschen:

![Abbildung für die Löschaktion im Menü 'Weitere Aktionen'](images/upgrade-tutorial-delete-toolchain.png)

Wenn Sie zu Ihrem Projekt zurückkehren, wird die Upgradenachricht erneut angezeigt, und Sie können erneut ein Upgrade durchführen, wenn
Sie bereit sind.

## Nächste Schritte
{: #upgrade_next_steps}

1. Bestätigen Sie, dass das Upgrade vollständig durchgeführt wurde. Aktualisieren Sie dazu Ihren Browser und überprüfen Sie auf der
Übersichtsseite des Projekts, ob die entsprechende Nachricht, dass für Ihr Projekt ein Upgrade auf diese Toolchain durchgeführt wurde,
angezeigt wird:

   ![Nachricht im Banner, dass das Upgrade für das Projekt durchgeführt wurde](images/banner-upgraded.png)

   Wenn in der Nachricht 'Jetzt Upgrade durchführen' steht, ist das Durchführen des Upgrades fehlgeschlagen. Klicken Sie auf den Link **Jetzt Upgrade durchführen**, um es erneut zu versuchen.
   {: tip}

   ![Nachricht im Banner, die angibt, dass das Projekt für die Durchführung eines Upgrades bereit ist](images/banner-ready-to-upgrade.png)

2. Erteilen Sie den Mitgliedern Ihres Teams Zugriff auf die Toolchain.
    - Jedes Teammitglied muss über ein gültiges {{site.data.keyword.Bluemix_notm}}-Konto verfügen. Teammitglieder, die kein solches Konto besitzen, müssen sich entsprechend [anmelden ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.ng.bluemix.net/registration){:new_window}.
    - Erteilen Sie Mitgliedern der Organisation Zugriff auf die Toolchain über die Toolchain-Seite 'Verwalten'. Vorhandene Projektmitglieder werden im Rahmen des Upgradeprozesses als Mitglieder der Toolchain hinzugefügt. Weitere Informationen zur Zugriffssteuerung für Toolchains finden Sie in [Zugriff verwalten ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access){:new_window}.
    - Wenn ein Benutzer nicht Mitglied der Organisation ist, zu der die Toolchain gehört, fügen Sie ihn über die Seite 'Organisationen verwalten' der Organisation hinzu.
    - Wenn Ihre Toolchain {{site.data.keyword.gitrepos}} verwendet, werden alle JazzHub-Projektmitglieder mit gültiger {{site.data.keyword.Bluemix_notm}}-ID mit denselben Berechtigungen zum {{site.data.keyword.gitrepos}}-Repository hinzugefügt, die sie im JazzHub-Projekt hatten. Wenn Ihr JazzHub-Projekt Mitglieder enthält, die keine gültige {{site.data.keyword.Bluemix_notm}}-ID haben, sollten sie für eine ID registriert und zum Repository hinzugefügt werden.
      Weitere Informationen zum Verwalten von Organisationen finden Sie in [Organisationen und Bereiche verwalten![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/admin/orgs_spaces.html#orgsspacesusers){:new_window}.

3. Verwenden Sie anstatt der Tools aus Ihrem {{site.data.keyword.jazzhub_short}}-Projekt die Tools aus Ihrer Toolchain. Verwenden Sie zum Bearbeiten von Code über einen Browser zum Beispiel die Web-IDE aus Ihrer Toolchain.

4. Wenn Sie {{site.data.keyword.gitrepos}} verwenden, führen Sie die Authentifizierung mithilfe eines persönlichen
Zugriffstokens oder
eines SSH-Schlüssels durch. Weitere Informationen zu SSH-Schlüsseln finden Sie in
[Persönliches Zugriffstoken oder SSH-Schlüssel für die
Authentifizierung erstellen](/docs/services/ContinuousDelivery/git_working.html#git_authentication). Um eine Authentifizierung von einem externen Git-Client über HTTPS durchzuführen, führen Sie folgende
Schritte aus:
    1. Wechseln Sie zur [Seite 'Zugriffstoken' ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window} in Ihren {{site.data.keyword.gitrepos}}-Benutzereinstellungen.
    2. Erstellen Sie ein persönliches Zugriffstoken, in dem als Bereich **api** verwendet wird.
    3. Rufen Sie die [Seite mit dem Konto ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/profile/account){:new_window} auf und suchen Sie Ihren für {{site.data.keyword.gitrepos}} geltenden Benutzernamen. Ihr Benutzername wird im Abschnitt für Änderungen des Benutzernamens aufgelistet und er wird bei allen persönlichen Repositorys, die Sie erstellen, auf der ersten Seite der URL angezeigt.
    4. Für die Authentifizierung bei {{site.data.keyword.gitrepos}} von einem externen Git-Client aus über HTTPS verwenden Sie Ihren Benutzernamen und Ihr persönliches Zugriffstoken.
    5. Wenn Sie das lokale Repository Ihres JazzHub Git-Repositorys wiederverwenden wollen, verweisen Sie von diesem Repository aus auf das neue Repository in {{site.data.keyword.gitrepos}}. Wechseln Sie von einer Shell in einem Terminal in das Verzeichnis, in dem das JazzHub Git-Repository geklont wird. Geben Sie den Befehl `git remote set-url` wie folgt ein: `git remote set-url origin https://git.ng.bluemix.net/<Benutzer-ID>/<Name_des_neuen_Repositorys>`

        Verwenden Sie den Befehl `git remote -v`, um zu überprüfen, welche fernen Namen für welche fernen URLs festgelegt sind. Der standardmäßig verwendete ferne Name lautet `origin`. Wenn Sie eine erweiterte Konfiguration haben, lautet das Format des Befehls wie folgt: `git remote set-url <ferner_Name_der_JazzHub_Repo_verwendet> https://git.ng.bluemix.net/<Benutzer-ID>/<Name_des_neuen_Repositorys>`
        {: tip}

5. Überlegen Sie nach dem Einrichten und der anfänglichen Verwendung Ihrer Toolchain, ob Sie folgende Schritte ausführen wollen, damit sichergestellt ist, dass Ihr Projekt ausschließlich von Ihnen verwendet wird:
    - Fügen Sie Ihrem Projektnamen ein Suffix hinzu, um anzugeben, dass es nicht verwendet werden darf. Sie können beispielsweise `_DO_NOT_USE` (nicht verwenden) an das Ende des Projektnamens anfügen.
    - Aktualisieren Sie die Beschreibung des Projekts, um deutlich zu machen, dass es nicht mehr verwendet wird, und fügen Sie der Toolchain einen Verweis hinzu.
    - Entfernen Sie die Mitglieder aus dem Projekt.
    - Löschen Sie das Projekt, wenn Sie es nicht mehr benötigen.

6. Optional: Um die Entwicklungsreife Ihres Projekts, die von Ihrem Team verwendeten Verfahren und die Qualität Ihrer Codebasis zu
untersuchen, fügen Sie Ihrer Toolchain IBM Cloud {{site.data.keyword.DRA_short}} hinzu. {{site.data.keyword.DRA_short}} wendet
auf DevOps-Projekte Verfahren für die
Analyse der Entwickler, des Teams und der Bereitstellung an. Weitere Informationen finden Sie in
[Einführung in {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights/index.html).


## Fehlerbehebung
{: #upgrade_troubleshoot}

Wenn während des Upgradeprozesses ein Problem auftritt, führen Sie einen oder mehrere der folgenden Schritte zur Fehlerbehebung aus:

- Überprüfen Sie die [Voraussetzungen](#upgrade_prereqs), um sicherzustellen, dass sie erfüllt werden. Stellen Sie sicher, dass Sie in jeder Organisation und jedem Bereich, in dem die Bereitstellung durch die Pipeline erfolgt, Mitglied sind.
- Wenn das Problem beim ersten Upgradeversuch aufgetreten ist und alle Voraussetzungen erfüllt sind, versuchen Sie das Upgrade erneut.
- Wenn Ihr Projekt Jazz SCM oder von IBM gehostetes Git für die Quellcodeverwaltung verwendet, überprüfen Sie die Größe des Repositorys. Wenn es größer als 500 MB ist, [wenden Sie sich an das DevOps-Service-Team ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}.
- Wenn Sie Ihre Toolchain nicht finden oder auf sie zuzugreifen können, finden Sie weitere Informationen dazu unter [diesem FAQ-Eintrag](#faq_find).
- Wenn weiterhin Probleme auftreten, stellen Sie eine Frage im [Unterstützungsforum ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. Fügen Sie in Ihren Forumpost die URLs für Ihr {{site.data.keyword.jazzhub_short}}-Projekt sowie Ihre {{site.data.keyword.contdelivery_short}}-Toolchain ein und taggen Sie Ihren Post mit dem Tag `devops-services`.


## Häufig gestellte Fragen
{: #upgrade_faq}

### Mein JazzHub-Projekt ist Großbritannien (GB) als geografischer Region zugeordnet, die Toolchain wird sich jedoch im Süden der USA befinden. Wie wird das funktionieren?
{: #faq_region}

Projekte unter hub.jazz.net und Toolchains werden im Süden der USA gehostet. Wenn Ihr Projekt für die Bereitstellung von Apps in anderen Regionen (wie zum Beispiel Großbritannien) konfiguriert wurde, wird es auch nach dem Upgrade auf eine Toolchain weiterhin Apps in diesen Regionen bereitstellen. Daher gibt es im Grunde genommen keine Änderungen, was den Ort des Hostings betrifft. Toolchains werden in Zukunft in mehr Regionen zur Verfügung stehen.

### Was geschieht beim Durchführen eines Upgrades mit meinen Arbeitselementen und Dashboards in Track &amp; Plan?
{: #faq_tp}

Der {{site.data.keyword.contdelivery_short}}-Service stellt Funktionalität für die Verfolgung von Problemen über {{site.data.keyword.gitrepos}} bereit. {{site.data.keyword.gitrepos}} wird von IBM gehostet und basiert auf GitLab Community Edition. {{site.data.keyword.contdelivery_short}} unterstützt außerdem Integrationen mit anderen Tools für die Planung und Verfolgung von Problemen wie etwa GitHub Issues und JIRA.

Bei dem eigentlichen Upgradeprozess können Sie entscheiden, ob Sie für Ihre Track &amp; Plan-Arbeitselemente ein Upgrade auf Git Issues durchführen wollen. Sowohl GitHub Issues als auch {{site.data.keyword.gitrepos}} stellen Kanban-Tafeln und Problemverfolgungsfunktionen für die Planung bereit. Weitere Informationen zu Issue Boards, die Kanban-Funktion in Git Repos and Issue Tracking, finden Sie in [Issue Board ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/help/user/project/issue_board.md){: new_window}.

Für diejenigen Kunden, die die gleiche Funktion benötigen, wie von dem veralteten Feature JazzHub Track &amp; Plan bereitgestellt wurde, ist ein neuer. cloudbasierter IBM Track and Plan-Service verfügbar, der in ausgewählten Ländern separat pro Benutzer auf Monatsbasis erworben werden kann. Mit diesem Cloud-Service erhalten Sie ähnlich wie bei Lizenzen für Mitwirkende für Rational Team Concert&trade; den vollen Funktionsumfang in einem Einzel-Tenant-Cloud-Abonnement.

Dieser neue Service - IBM Track and Plan on Cloud - stellt eine weitaus umfangreichere Funktionalität zur Verfügung als die veraltete Funktion JazzHub Track &amp; Plan und unterstützt die Anpassung von Prozessen, Projekthierarchien, SAFe&reg; sowie zahlreiche andere agile und Hybridmethoden. Seine Skalierbarkeit ermöglicht ein Wachstum über die Grenzen von Einzelprojekten hinaus. Er basiert auf der neuesten Version von Rational Team Concert 6.0.3 und wird in den kommenden 60 Tagen Version 6.0.4 erreichen, wohingegen JazzHub Track &amp; Plan auf Rational Team Concert 5.x basierte. Mittels zusätzlicher Services ist die Datenmigration auf IBM Track and Plan on Cloud möglich. Weitere Informationen erhalten Sie über [Tom Hollowell ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](mailto:trhollow@us.ibm.com){:new_window}, Connected Products SaaS Sales Leader.

Wenn Sie Informationen zu IBM Track and Plan on Cloud suchen oder IBM Track and Plan on Cloud online kaufen möchten, gehen Sie zu [IBM Marketplace ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window}.

Wenn Sie zusätzlich Funktionen für die Buildautomation und die Quellcodeverwaltung erwerben möchten, stellt [Rational Team Concert on Cloud ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/us-en/marketplace/change-and-configuration-management/purchase#product-header-top){: new_window} eine Option dar.

### Was geschieht beim Durchführen eines Upgrades mit meinem Code-Repository?
{: #faq_repo}

Nach dem Upgrade ist Ihr neuer Git-Service vergleichbar mit dem, was Sie bisher hatten. Wenn Sie github.com mit Ihrem JazzHub-Projekt verwendet haben, ist Ihre Toolchain mit demselben GitHub-Repository verbunden. Wenn Ihr JazzHub-Projekt jedoch IBM Hosted Git verwendet hat, so wird der Inhalt dieses Repositorys in ein neues Repository in {{site.data.keyword.gitrepos}} geklont, einer von IBM gehosteten Komponente von {{site.data.keyword.contdelivery_short}}.

Vollständige Details zur Handhabung der einzelnen Repository-Typen im Rahmen des Upgradeprozesses finden Sie in der
folgenden Tabelle.

|Projektrepository |Projekttyp	|Toolchain-Repository |
|:----------|:------------------------------|:------------------|
|github.com 		|Privat oder öffentlich 		|Dasselbe github.com-Repository mit {{site.data.keyword.Bluemix_notm}} Public.	|
|hub.jazz.net/git		|Privat oder öffentlich 		|Ein neues privates oder öffentliches Repository in {{site.data.keyword.gitrepos}} mit {{site.data.keyword.Bluemix_notm}} Public.	|
{: caption="Tabelle 1. Zuordnung von Projektrepositorys zu Toolchain-Repositorys" caption-side="top"}


### Was geschieht beim Durchführen eines Upgrades zu einer Toolchain mit den Builddefinitionen in meinem Projekt?
{: #faq_build}

Wenn Sie Ihren Quellcode mit Jazz anstatt mit Delivery Pipeline erstellen, müssen Sie Ihre Builddefinitionen manuell in Ihrer Toolchain auf Delivery Pipeline migrieren.

Wenn Sie Jazz SCM als Quellenrepository einsetzen und Delivery Pipeline für die Erstellung von Code Delivery verwenden, wird die Quelle in Jazz SCM automatisch in ein Git-Repository verschoben. Ihre Delivery Pipeline-Konfiguration verwendet künftig die Quelle des Git-Repositorys anstatt der Quelle von Jazz SCM, bleibt aber ansonsten unverändert.

### Ich muss für mein Projekt, für das ein Upgrade auf eine Toolchain durchgeführt wird, eine Organisation erstellen. Mir ist bewusst, dass ich eine Kreditkarte zu meinem Konto hinzufügen muss, bevor ich die Organisation erstellen kann. Wird diese Kreditkarte belastet?
{: #faq_charges}

Als [nutzungsabhängiger Kunde ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window} werden Ihnen bei der Nutzung von Laufzeiten, Services oder Komponenten, die über die im {{site.data.keyword.Bluemix_notm}}-Katalog aufgeführten kostenlosen Zuteilungen hinausgehen, jeweils entsprechende Gebühren berechnet. Einen Voranschlag der Kosten für die Nutzung können Sie der [Preisliste ![Symbol für externen Link ](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.ng.bluemix.net/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window} entnehmen. Die aktuellen Preise für Continuous Delivery finden Sie im [{{site.data.keyword.Bluemix_notm}}-Katalog ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/catalog/services/continuous-delivery){: new_window}.

Wenn Sie ein IBM Mitarbeiter sind, können interne IBM Projekte den entsprechenden Abteilungen in Rechnung gestellt werden, sodass keine privaten Kreditkarten erforderlich sind. Sollten Sie Ressourcen benötigen, die über die kostenlosen Zuteilungen für IBM Mitarbeiter hinausgehen, erstellen Sie ein Support-Ticket.

### Ich kann meine Toolchain nicht finden oder auf sie zugreifen. Was soll ich tun?
{: #faq_find}

Toolchains werden in {{site.data.keyword.Bluemix_notm}}-Organisationen gehostet. Der Upgradeprozess fügt alle Mitglieder des JazzHub-Projekts der Toolchain hinzu. Allerdings muss der Eigner der {{site.data.keyword.Bluemix_notm}}-Organisation die Benutzer zur Organisation hinzufügen, damit diese die Toolchain sehen können.

Um auf Ihre Toolchain zuzugreifen, rufen Sie die {{site.data.keyword.Bluemix_notm}}-Plattform auf, klicken Sie auf das Menüsymbol und klicken Sie auf **Services &gt; DevOps**. Die Seite 'Toolchains' wird geöffnet. Stellen Sie sicher, dass Sie sich in der Region 'Vereinigte Staaten (Süden)' und in der Organisation befinden, die die Toolchain enthält. Wenn Ihre Toolchain auf der Seite 'Toolchains' nicht aufgeführt ist, lesen Sie [diesen FAQ-Eintrag](#faq_uk).

Alternativ können Sie - während die JazzHub-Site noch verfügbar ist - zu Ihrer Toolchain wechseln, indem Sie auf den Link im Banner auf der Übersichtsseite des Projekts klicken.

### Mein Projekt ist Großbritannien (GB) als geografischer Region zugeordnet. Nach dem Upgrade werden Fehlernachrichten angezeigt, meine Kollegen können nicht auf die Toolchain zugreifen und ich sehe meine Toolchain nicht auf der Seite 'Toolchains' in {{site.data.keyword.Bluemix_notm}}. Was stimmt nicht?
{: #faq_uk}

**Vollständige Frage:**

Mein JazzHub-Projekt ist entsprechend den Projekteinstellungen der {{site.data.keyword.Bluemix_notm}}-Region Großbritannien (GB) zugeordnet. Ich habe meine Projekteinstellungen geprüft. Dazu habe ich die zugehörige Übersichtsseite unter JazzHub aufgerufen, auf das Symbol **Einstellungen** (Zahnradsymbol) geklickt und auf **Optionen &gt; Als {{site.data.keyword.Bluemix_notm}}-Projekt definieren: Region** geklickt. Nachdem ich ein Upgrade für das Projekt auf Toolchain in den Vereinigten Staaten durchgeführt hatte, sind diese Probleme auftreten:

   1. Wenn ich die Organisation in den Vereinigten Staaten auswähle, wird eine Nachricht angezeigt, die angibt, dass die Organisation über keinen Bereich in der Region 'Vereinigte Staaten (Süden)' verfügt, und ich werde aufgefordert, einen Bereich zu erstellen. Ich möchte aber keine Aktivitäten in den USA ausführen.
   
   2. Einige meiner Kollegen können nicht auf die Toolchain zugreifen, obwohl sie als Mitglieder im ursprünglichen JazzHub-Projekt aufgeführt sind. Wenn sie versuchen, die Toolchain über die Seite mit der App-Übersicht in der Region 'Großbritannien' durch Anklicken von **Toolchain anzeigen** zu öffnen, wird die Nachricht "Zugriff verweigert" angezeigt.
   
   3. Die Toolchain wird nicht auf meiner Seite 'Toolchains' unter [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window} angezeigt, obwohl ich direkt über die Seite mit der App-Übersicht in der Region 'Großbritannien' auf die Toolchain zugreifen kann, indem ich auf **Toolchain anzeigen** klicke. Es wird eine Fehlernachricht angezeigt, die besagt, dass ich die Toolchain nicht ändern kann oder dass ich keine Toolchain habe und eine erstellen muss. 

**Antwort:**

Diese Probleme können auftreten, wenn Sie von einer {{site.data.keyword.Bluemix_notm}}-Organisation außerhalb der Vereinigten Staaten kommen und Ihre Organisation vor dem Upgrade nicht explizit auf die Region 'Vereinigte Staaten (Süden)' erweitert haben. Sie können dies auf zwei Arten bestätigen:

   * Wenn Sie die Toolchain-URL öffnen, schauen Sie sich den {{site.data.keyword.Bluemix_notm}}-Header an. Sehr wahrscheinlich sehen Sie dort den Namen Ihrer Organisation und es ist kein Bereich angegeben.
   
   * Klicken Sie auf der Übersichtsseite Ihrer Toolchain auf **Verwalten**. Klicken Sie auf der Seite 'Zugriffssteuerung' auf **Organisationsmanager**. Die Organisation, die die Toolchain enthält, wird auf der Hauptseite aufgeführt.

Zum Zeitpunkt des Upgrades war Ihre Nicht-US-Organisation nicht in den Vereinigten Staaten vorhanden. Deshalb wählte das Upgrade eine andere Organisation für Sie aus, auf die Sie zufällig Zugriff haben.

Wenn Sie zu dieser {{site.data.keyword.Bluemix_notm}}-Organisation in den Vereinigten Staaten (US) wechseln, finden Sie die Toolchain. Wenn Sie Ihre Kollegen zu dieser Organisation hinzufügen, wird ihnen der Zugriff erteilt. Diese Toolchain kann weiterhin Bereitstellungsaktivitäten für Ihre Nicht-US-Organisation ausführen. Das einzige Problem ist, dass sich diese beiden Organisationen unterscheiden. Sie können die Benutzerverwaltung nicht automatisch für beide ausführen.

Wenn sich Ihre Toolchain in einer US-Organisation befinden soll, die Ihrer Nicht-US-Organisation entspricht, führen Sie die folgenden Schritte aus:

   1. Melden Sie sich bei [https://console.bluemix.net![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net){: new_window} an und wählen Sie die Nicht-US-Region und die Organisation aus, von der Sie kommen.
   
   2. Wechseln Sie im {{site.data.keyword.Bluemix_notm}}-Header zu der Region 'Vereinigte Staaten (Süden)'. Sie werden aufgefordert, einen Bereich in dieser Region zu erstellen.
   
   3. Erstellen Sie einen Bereich in der Region 'Vereinigte Staaten (Süden)', um Ihre Organisation auf diese Region zu erweitern. 
   
   4. Löschen Sie die Toolchain, die durch den Upgradeprozess erstellt wurde. 
   
      Das Git-Repository wird nicht automatisch gelöscht. Möglicherweise möchten Sie es manuell löschen oder vorläufig umbenennen. Wenn Sie das Repository bereits geändert haben, können Sie die zukünftige Toolchain aktualisieren, um es zu einem späteren Zeitpunkt zu verwenden.
      {: tip}

   5. Kehren Sie zum JazzHub-Projekt zurück. Es sollte für einen weiteren Upgradeversuch zurückgesetzt werden. Wenn es nicht zurückgesetzt wird, wenden Sie sich an hub@jazz.net und geben Sie die URL des Projekts an.
   
   6. Starten Sie den Upgradeprozess erneut und stellen Sie sicher, dass Sie die richtige Organisation in den Vereinigten Staaten auswählen, dem mit dem Namen Ihrer Organisation in der Nicht-US-Region übereinstimmt.
   
   7. Wenn Sie das Git-Repository vom vorherigen Toolchain-Upgrade-Versuch (siehe Schritt 4) aktualisiert oder umbenannt haben, können Sie die Git-Karte in Ihrer Toolchain umkonfigurieren, um stattdessen auf diese Git-Repository-URL zu verweisen. Die Änderung wird automatisch in der Pipeline nachvollzogen. Prüfen Sie zur Bestätigung die Registerkarte 'Eingabe' in der Build-Stage.
