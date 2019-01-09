---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-11"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Einführung in Toolchains nach dem Upgrade Ihres {{site.data.keyword.jazzhub_short}}-Projekts
{: #toolchains_post_upgrade}

Für {{site.data.keyword.jazzhub}}-Projekte unter hub.jazz.net wurde ein Upgrade auf Toolchains im {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.contdelivery_short}}-Service durchgeführt. 

{{site.data.keyword.jazzhub_short}} unter hub.jazz.net wurde zurückgezogen. 

Verwenden Sie für Ihre DevOps-Projekte den [{{site.data.keyword.contdelivery_short}}-Service ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/devops){:new_window}. Wenn Sie noch nicht mit {{site.data.keyword.Bluemix_notm}} vertraut sind, informieren Sie sich anhand der [{{site.data.keyword.Bluemix_notm}}-Übersicht](/docs/overview/ibm-cloud.html#overview).

{: shortdesc}

## Toolchain suchen, die aus Ihrem Projekt erstellt wurde
{: #find_toolchain}

Vergewissern Sie sich über die [Seite 'Toolchains' ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link") ](https://console.bluemix.net/devops/toolchains){: new_window}, dass das Upgrade vollständig durchgeführt wurde, und prüfen Sie, ob Toolchains mit Namen angezeigt werden, die den Namen Ihrer hub.jazz.net-Projekte entsprechen. Wenn Ihre Projekte automatisch aktualisiert wurden, müssen Sie diese Einschränkungen beachten:
   - Wenn eine Toolchain den Namen Ihres Projekts schon verwendet hat, bevor Ihr Projekt aktualisiert wurde, hat die neue Toolchain, die für Ihr Projekt erstellt wurde, möglicherweise nicht genau denselben Namen wie Ihr Projekt. 
   - Wenn Sie keine Toolchains für Ihre Projekte finden, wechseln Sie zu anderen Organisationen, zu denen Sie gehören, und überprüfen Sie die Toolchains dort.
   
## Toolchains - Übersicht
{: #compare_toolchains}

Wenn Sie ein oder mehr Projekte unter hub.jazz.net hatten, wurde für diese ein Upgrade auf Toolchains im {{site.data.keyword.contdelivery_short}}-Service automatisch durchgeführt, es sei denn, das Upgrade ist fehlgeschlagen. Upgrades können aufgrund ungültiger IBM Cloud-Konten oder -Organisationen fehlschlagen. Diese Konto- und Organisationsinhaber wurden per E-Mail über die Fehler und spezifischen Maßnahmen informiert, die sie durchführen müssen, um die Fehler zu beheben. Wenn Sie Hilfe beim Lokalisieren der Toolchain für Ihr aktualisiertes Projekt benötigen, wenden Sie sich an den [Support ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. 

Toolchains ähneln Projekten, weisen jedoch einige wichtige Unterschiede auf:

- Projekte können nur über ein Repository (repo) und eine Pipeline verfügen. Toolchains können so viele Repositorys und Pipelines besitzen wie nötig.
- Toolchains können Tools enthalten, die in Projekten nicht verfügbar sind, wie zum Beispiel Slack, Sauce Labs, PagerDuty und {{site.data.keyword.DRA_full}}.

 {{site.data.keyword.DRA_short}} ist in den Regionen 'Vereinigten Staaten (Süden)', 'Vereinigtes Königreich' und 'Deutschland' verfügbar.
 {: tip}
 
- Bei Projekten erfolgte die Pflege von Mitgliedschaften auf Projektebene. Der Zugriff auf Toolchains wird durch die {{site.data.keyword.Bluemix_notm}}-Organisation und die Toolchain verwaltet. Um mit einer Toolchain arbeiten zu können, müssen Sie Mitglied der Organisation sein, die die Toolchain enthält. Der Toolchain-Eigner hat mehr Kontrolle darüber, wer auf die Toolchain zugreifen und welche Aktionen er ausführen kann. Weitere Informationen zur Zugriffssteuerung finden Sie unter Schritt 2 in [Einführung in Ihre Toolchain](#upgrade_next_steps).
- Abhängig vom Typ des Repositorys, das Sie in Ihrem Projekt unter hub.jazz.net verwendet haben, kann Ihre Toolchain ein GitHub.com-Repository oder ein {{site.data.keyword.gitrepos}}-Repository enthalten.

Mehr zu Toolchains erfahren Sie in [YouTube ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://youtu.be/2SIPE1e7NJ4){: new_window} oder in der [Einführung in {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery/index.html).

## Einführung in Ihre Toolchain
{: #upgrade_next_steps}

1. Erteilen Sie den Mitgliedern Ihres Teams Zugriff auf die Toolchain.
    - Jedes Teammitglied muss über ein gültiges {{site.data.keyword.Bluemix_notm}}-Konto verfügen. Teammitglieder, die kein solches Konto besitzen, müssen sich entsprechend [anmelden ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/registration){:new_window}.
    - Erteilen Sie Mitgliedern der Organisation Zugriff auf die Toolchain über die Toolchain-Seite 'Verwalten'. Vorhandene Projektmitglieder werden im Rahmen des Upgradeprozesses als Mitglieder der Toolchain hinzugefügt. Weitere Informationen zur Zugriffssteuerung für Toolchains finden Sie in [Zugriff verwalten ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access){:new_window}.
    - Wenn ein Benutzer nicht Mitglied der Organisation ist, zu der die Toolchain gehört, fügen Sie ihn über die Seite 'Organisationen
verwalten' der Organisation hinzu.
    - Wenn Ihre Toolchain {{site.data.keyword.gitrepos}} verwendet, werden alle JazzHub-Projektmitglieder mit gültiger {{site.data.keyword.Bluemix_notm}}-ID mit denselben Berechtigungen zum {{site.data.keyword.gitrepos}}-Repository hinzugefügt, die sie im JazzHub-Projekt hatten. Wenn Ihr JazzHub-Projekt Mitglieder enthält, die keine gültige {{site.data.keyword.Bluemix_notm}}-ID haben, können sie sich für eine ID registrieren lassen. Nachdem sie registriert wurden, können Sie sie zum Repository hinzufügen.
      Weitere Informationen zum Verwalten von Organisationen finden Sie in [Organisationen und Bereiche verwalten![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/account/orgs_spaces.html#orgsspacesusers){:new_window}.

2. Wenn Sie {{site.data.keyword.gitrepos}} verwenden, führen Sie die Authentifizierung mithilfe eines persönlichen Zugriffstokens oder eines SSH-Schlüssels durch. Weitere Informationen zu SSH-Schlüsseln finden Sie in [Persönliches Zugriffstoken oder SSH-Schlüssel für die Authentifizierung erstellen](/docs/services/ContinuousDelivery/git_working.html#git_authentication). Um eine Authentifizierung von einem externen Git-Client über HTTPS durchzuführen, führen Sie folgende Schritte aus:
    1. Wechseln Sie zur [Seite 'Zugriffstoken' ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window} in Ihren {{site.data.keyword.gitrepos}}-Benutzereinstellungen.
    2. Erstellen Sie ein persönliches Zugriffstoken, in dem als Bereich **API** verwendet wird.
    3. Rufen Sie die [Seite mit dem Konto ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/profile/account){:new_window} auf und suchen Sie Ihren für {{site.data.keyword.gitrepos}} geltenden Benutzernamen. Ihr Benutzername wird im Abschnitt für Änderungen des Benutzernamens aufgelistet und er wird bei allen persönlichen Repositorys, die Sie erstellen, auf der ersten Seite der URL angezeigt.
    4. Für die Authentifizierung mit {{site.data.keyword.gitrepos}} von einem externen Git-Client aus über HTTPS verwenden Sie Ihren Benutzernamen und Ihr persönliches Zugriffstoken.
    5. Wenn Sie das lokale Repository Ihres JazzHub Git-Repositorys wiederverwenden wollen, verweisen Sie von diesem Repository aus auf das neue Repository in {{site.data.keyword.gitrepos}}. Wechseln Sie von einer Terminal-Shell aus in das Verzeichnis, in dem das JazzHub Git-Repository geklont wird. Geben Sie den Befehl `git remote set-url` wie folgt ein: `git remote set-url origin https://git.ng.bluemix.net/<Benutzer-ID>/<Name_des_neuen_Repositorys>`

        Verwenden Sie den Befehl `git remote -v`, um zu überprüfen, welche fernen Namen für welche fernen URLs festgelegt sind. Der standardmäßig verwendete ferne Name lautet `origin`. Wenn Sie eine erweiterte Konfiguration haben, lautet das Format des Befehls wie folgt: `git remote set-url <ferner_Name_der_JazzHub_Repo_verwendet> https://git.ng.bluemix.net/<Benutzer-ID>/<Name_des_neuen_Repositorys>`
        {: tip}

3. Optional: Um die Entwicklungsreife Ihres Projekts, die von Ihrem Team verwendeten Verfahren und die Qualität Ihrer Codebasis zu untersuchen, fügen Sie Ihrer Toolchain IBM Cloud {{site.data.keyword.DRA_short}} hinzu. {{site.data.keyword.DRA_short}} wendet auf DevOps-Projekte Verfahren für die Analyse der Entwickler, des Teams und der Bereitstellung an. Weitere Informationen finden Sie in [Einführung in {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights/index.html).

  {{site.data.keyword.DRA_short}} ist in den Regionen 'Vereinigten Staaten (Süden)', 'Vereinigtes Königreich' und 'Deutschland' verfügbar.
  {: tip}


## Fehlerbehebung
{: #upgrade_troubleshoot}

Wenn Probleme im Zusammenhang mit dem Upgrade Ihres Projekts auftreten, stellen Sie eine Frage im [Unterstützungsforum ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. Schließen Sie in Ihren Forumpost die URLs für Ihr {{site.data.keyword.jazzhub_short}}-Projekt sowie Ihre {{site.data.keyword.contdelivery_short}}-Toolchain ein und taggen Sie Ihren Post mit dem Tag `devops-services`.


## Häufig gestellte Fragen
{: #upgrade_faq}

### Mein JazzHub-Projekt wurde Großbritannien (GB) als geografischer Region zugeordnet, die Toolchain wird sich jedoch im Süden der USA befinden. Wie funktioniert das?
{: #faq_region}

Projekte unter hub.jazz.net und Toolchains werden im Süden der USA gehostet. Wenn Ihr Projekt für die Bereitstellung von Apps in anderen Regionen (wie zum Beispiel 'Vereinigtes Königreich') konfiguriert wurde, wird die Toolchain auch weiterhin Apps in diesen Regionen bereitstellen. Daher gibt es im Grunde genommen keine Änderungen, was den Ort des Hostings der Daten betrifft. Toolchains werden in Zukunft in mehr Regionen zur Verfügung stehen.

### Was ist beim Durchführen eines Upgrades mit meinen Arbeitselementen und Dashboards in Track &amp; Plan geschehen?
{: #faq_tp}

Der {{site.data.keyword.contdelivery_short}}-Service stellt Funktionalität für die Verfolgung von Problemen über {{site.data.keyword.gitrepos}} bereit. {{site.data.keyword.gitrepos}} wird von IBM gehostet und basiert auf GitLab Community Edition. {{site.data.keyword.contdelivery_short}} unterstützt außerdem Integrationen mit anderen Tools für die Planung und Verfolgung von Problemen wie etwa GitHub Issues und JIRA.

Während des automatisierten Upgradeprozesses wurden Ihre Track & Plan-Arbeitselemente in Git-Probleme migriert. Sowohl GitHub Issues als auch {{site.data.keyword.gitrepos}} stellen Kanban-Tafeln und Problemverfolgungsfunktionen für die Planung bereit. Weitere Informationen zu Issue Boards, die Kanban-Funktion in Git Repos and Issue Tracking, finden Sie in [Issue Board ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/help/user/project/issue_board.md){: new_window}.

Wenn Sie die gleiche Funktion benötigen, die von dem veralteten Feature JazzHub Track &amp; Plan bereitgestellt wurde, ist ein neuer. cloudbasierter IBM Track and Plan-Service verfügbar, der in ausgewählten Ländern pro Benutzer auf Monatsbasis erworben werden kann. Mit diesem Cloud-Service erhalten Sie ähnlich wie bei Lizenzen für Mitwirkende für Rational Team Concert&trade; den vollen Funktionsumfang in einem Einzel-Tenant-Cloud-Abonnement.

Dieser neue Service - IBM Track and Plan on Cloud - stellt eine weitaus umfangreichere Funktionalität zur Verfügung als die veraltete Funktion JazzHub Track &amp; Plan und unterstützt die Anpassung von Prozessen, Projekthierarchien, SAFe&reg; sowie zahlreiche andere agile und Hybridmethoden. Seine Skalierbarkeit ermöglicht ein Wachstum über die Grenzen von Einzelprojekten hinaus. Er basiert auf der neuesten Version von Rational Team Concert 6.0.3 und wird in den kommenden 60 Tagen Version 6.0.4 erreichen, wohingegen JazzHub Track &amp; Plan auf Rational Team Concert 5.x basierte. Mittels zusätzlicher Services ist die Datenmigration auf IBM Track and Plan on Cloud möglich. Weitere Informationen erhalten Sie über [Tom Hollowell ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](mailto:trhollow@us.ibm.com){:new_window}, Connected Products SaaS Sales Leader.

Wenn Sie Informationen zu IBM Track and Plan on Cloud suchen oder IBM Track and Plan on Cloud online kaufen möchten, rufen Sie den [IBM Marketplace ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window} auf.

Wenn Sie Funktionen für die Buildautomation und die Quellcodeverwaltung erwerben möchten, stellt [Rational Team Concert on Cloud ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/us-en/marketplace/change-and-configuration-management/purchase#product-header-top){: new_window} eine Option dar.

### Was ist mit meinem Code-Repository nach dem Upgrade geschehen?
{: #faq_repo}

Nach dem Upgrade ist Ihr neuer Git-Service vergleichbar mit dem, was Sie bisher hatten. Wenn Sie github.com mit Ihrem JazzHub-Projekt verwendet haben, wird Ihre Toolchain mit demselben GitHub-Repository verbunden. Wenn Ihr JazzHub-Projekt jedoch IBM Hosted Git verwendet hat, so wird der Inhalt dieses Repositorys in ein neues Repository in {{site.data.keyword.gitrepos}} geklont, einer von IBM gehosteten Komponente von {{site.data.keyword.contdelivery_short}}.

Weitere Informationen zur Handhabung der einzelnen Repository-Typen im Rahmen des Upgradeprozesses finden Sie in der folgenden Tabelle.

|Projektrepository |Projekttyp	|Toolchain-Repository |
|:----------|:------------------------------|:------------------|
|github.com 		|Privat oder öffentlich 		|Dasselbe github.com-Repository mit {{site.data.keyword.Bluemix_notm}} Public.	|
|hub.jazz.net/git		|Privat oder öffentlich 		|Ein neues privates oder öffentliches Repository in {{site.data.keyword.gitrepos}} mit {{site.data.keyword.Bluemix_notm}} Public.	|
|Jazz SCM		|Privat oder öffentlich 		|Ein neues privates oder öffentliches Repository in {{site.data.keyword.gitrepos}} mit {{site.data.keyword.Bluemix_notm}} Public.	|
{: caption="Tabelle 1. Zuordnung von Projektrepositorys zu Toolchain-Repositorys" caption-side="top"}


### Was ist nach dem Upgrade mit den Builddefinitionen in meinem Projekt geschehen?
{: #faq_build}

Wenn Sie Ihren Quellcode mit Jazz anstatt mit Delivery Pipeline erstellt haben, müssen Sie Ihre Builddefinitionen manuell in Ihrer Toolchain auf Delivery Pipeline migrieren.

Wenn Sie Jazz SCM als Quellenrepository eingesetzt und Delivery Pipeline für die Codeerstellung verwendet haben, wird die Quelle in Jazz SCM automatisch in ein Git-Repository verschoben. Die Konfiguration Ihrer Delivery Pipeline bleibt unverändert. Es wird nur die Quelle aus dem Git-Repository statt der Jazz SCM-Quelle verwendet.

### Ich musste für mein Projekt, für das ein Upgrade auf eine Toolchain durchgeführt wurde, eine Organisation erstellen. Deshalb habe ich eine Kreditkarte zu meinem Konto hinzugefügt. Wird diese Kreditkarte belastet?
{: #faq_charges}

Als [nutzungsabhängiger Kunde ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window} werden Ihnen bei der Nutzung von Laufzeiten, Services oder Komponenten, die über die im {{site.data.keyword.Bluemix_notm}}-Katalog aufgeführten kostenlosen Zuteilungen hinausgehen, jeweils entsprechende Gebühren berechnet. Einen Voranschlag der Kosten für die Nutzung können Sie der [Preisliste ![Symbol für externen Link ](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window} entnehmen. Die aktuellen Preise für Continuous Delivery finden Sie im [{{site.data.keyword.Bluemix_notm}}-Katalog ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/catalog/services/continuous-delivery){: new_window}.

Wenn Sie ein IBM Mitarbeiter sind, können interne IBM Projekte den entsprechenden Abteilungen in Rechnung gestellt werden, sodass keine privaten Kreditkarten erforderlich sind. Sollten Sie Ressourcen benötigen, die über die kostenlosen Zuteilungen für IBM Mitarbeiter hinausgehen, erstellen Sie ein Support-Ticket.

### Ich kann meine Toolchain nicht finden oder auf sie zugreifen. Was soll ich tun?
{: #faq_find}

Toolchains werden in {{site.data.keyword.Bluemix_notm}}-Organisationen gehostet. Der Upgradeprozess fügt alle Mitglieder des JazzHub-Projekts der Toolchain hinzu. Allerdings muss der Eigner der {{site.data.keyword.Bluemix_notm}}-Organisation die Benutzer zur Organisation hinzufügen, damit diese die Toolchain sehen können.

Um auf Ihre Toolchain zuzugreifen, rufen Sie {{site.data.keyword.Bluemix_notm}} auf, klicken Sie auf das Menüsymbol und klicken Sie auf **Services &gt; DevOps**. Die Seite 'Toolchains' wird geöffnet. Stellen Sie sicher, dass Sie sich in der Region 'Vereinigte Staaten (Süden)' und in der Organisation befinden, die die Toolchain enthält. Wenn Ihre Toolchain auf der Seite "Toolchains" nicht aufgeführt ist, lesen Sie [diesen FAQ-Eintrag](#faq_uk).

### Mein Projekt ist Großbritannien (GB) als geografischer Region zugeordnet. Nach dem Upgrade werden Fehlernachrichten angezeigt, meine Kollegen können nicht auf die Toolchain zugreifen und ich sehe meine Toolchain nicht auf der Seite 'Toolchains' in {{site.data.keyword.Bluemix_notm}}. Was stimmt nicht?
{: #faq_uk}

**Vollständige Frage:**

Mein JazzHub-Projekt ist entsprechend den Projekteinstellungen der {{site.data.keyword.Bluemix_notm}}-Region Großbritannien (GB) zugeordnet. Ich habe meine Projekteinstellungen geprüft. Dazu habe ich die zugehörige Übersichtsseite unter JazzHub aufgerufen, auf das Symbol **Einstellungen** (Zahnradsymbol) geklickt und auf **Optionen &gt; Als {{site.data.keyword.Bluemix_notm}}-Projekt definieren: Region** geklickt. Nachdem ich ein Upgrade für das Projekt auf Toolchain in den Vereinigten Staaten durchgeführt hatte, sind diese Probleme auftreten:

   1. Wenn ich die Organisation in den Vereinigten Staaten auswähle, wird eine Nachricht angezeigt, die angibt, dass die Organisation über keinen Bereich in der Region 'Vereinigte Staaten (Süden)' verfügt, und ich werde aufgefordert, einen Bereich zu erstellen. Ich möchte aber keine Aktivitäten in den USA ausführen.
   
   2. Einige meiner Kollegen können nicht auf die Toolchain zugreifen, obwohl sie als Mitglieder im ursprünglichen JazzHub-Projekt aufgeführt sind. Wenn sie versuchen, die Toolchain über die Seite mit der App-Übersicht in der Region 'Großbritannien' durch Anklicken von **Toolchain anzeigen** zu öffnen, wird die Nachricht "Zugriff verweigert" angezeigt.
   
   3. Die Toolchain wird nicht auf meiner Seite 'Toolchains' unter [https://cloud.ibm.com/devops/toolchains?env_id=ibm:yp:us-south ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/devops/toolchains?env_id=ibm:yp:us-south){: new_window} angezeigt, obwohl ich direkt über die Seite mit der App-Übersicht in der Region 'Großbritannien' auf die Toolchain zugreifen kann, indem ich auf **Toolchain anzeigen** klicke. Es wird eine Fehlernachricht angezeigt, die besagt, dass ich die Toolchain nicht ändern kann oder dass ich keine Toolchain habe und eine erstellen muss. 

**Antwort:**

Diese Probleme können auftreten, wenn Sie von einer {{site.data.keyword.Bluemix_notm}}-Organisation außerhalb der Vereinigten Staaten kommen und Ihre Organisation vor dem Upgrade nicht explizit auf die Region 'Vereinigte Staaten (Süden)' erweitert haben. Sie können dieses Problem bestätigen, indem Sie die Toolchains-Seite öffnen. Die Region und die Organisation werden auf der Seite oben angezeigt. 

Zum Zeitpunkt des Upgrades war Ihre Nicht-US-Organisation nicht in den Vereinigten Staaten vorhanden. Deshalb wählte das Upgrade eine andere Organisation für Sie aus, auf die Sie Zugriff haben.

Wenn Sie zu dieser {{site.data.keyword.Bluemix_notm}}-Organisation in den USA wechseln, finden Sie die Toolchain. Wenn Sie Ihre Kollegen zu dieser Organisation hinzufügen, wird ihnen der Zugriff erteilt. Diese Toolchain kann weiterhin Bereitstellungsaktivitäten für Ihre Nicht-US-Organisation ausführen. Das einzige Problem ist, dass sich diese beiden Organisationen unterscheiden. Sie können die Benutzerverwaltung nicht automatisch für beide ausführen.

Wenn sich Ihre Toolchain in der US-Organisation befinden soll, die Ihrer Nicht-US-Organisation entspricht, führen Sie die folgenden Schritte aus:

   1. Melden Sie sich bei [https://cloud.ibm.com ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com){: new_window} an und wählen Sie die Nicht-US-Region und die Organisation aus, von der Sie kommen.
   
   2. Wechseln Sie im {{site.data.keyword.Bluemix_notm}}-Header zu der Region 'Vereinigte Staaten (Süden)'. Sie werden aufgefordert, einen Bereich in dieser Region zu erstellen.
   
   3. Erstellen Sie einen Bereich in der Region 'Vereinigte Staaten (Süden)', um Ihre Organisation auf diese Region zu erweitern. 
   
   4. Löschen Sie die Toolchain, die durch den Upgradeprozess erstellt wurde. 
   
      Das Git-Repository wird nicht automatisch gelöscht. Möglicherweise möchten Sie es manuell löschen oder vorläufig umbenennen. Wenn Sie das Git-Repository bereits umbenannt haben, können Sie die zukünftige Toolchain aktualisieren, um es zu einem späteren Zeitpunkt zu verwenden.
      {: tip}

   5. Kehren Sie zum JazzHub-Projekt zurück. Das Projekt setzt sich für einen weiteren Upgradeversuch zurück. Wenn das Projekt nicht zurückgesetzt wird, wenden Sie sich an hub@jazz.net und geben Sie die URL des Projekts an.
   
   6. Starten Sie den Upgradeprozess erneut und stellen Sie sicher, dass Sie die richtige Organisation in den Vereinigten Staaten auswählen, dem mit dem Namen Ihrer Organisation in der Nicht-US-Region übereinstimmt.
   
   7. Wenn Sie das Git-Repository vom vorherigen Toolchain-Upgrade-Versuch (siehe Schritt 4) aktualisiert oder umbenannt haben, können Sie die Git-Karte in Ihrer Toolchain umkonfigurieren, um stattdessen auf diese Git-Repository-URL zu verweisen. Die Änderung wird automatisch in der Pipeline nachvollzogen. Prüfen Sie zur Bestätigung die Registerkarte 'Eingabe' in der Build-Stage.
