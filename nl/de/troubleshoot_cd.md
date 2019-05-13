---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-11"

keywords: troubleshoot, IBM Cloud Continuous Delivery

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:tip: .tip}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# Fehlerbehebung für {{site.data.keyword.contdelivery_short}}
{: #troubleshoot-cd}

Allgemeine Probleme bei der Verwendung von {{site.data.keyword.contdelivery_full}} können die GitHub-Authentifizierung, die Pipelineerstellung, die Konfiguration der Toolintegration oder Cloud Foundry betreffen. In vielen Fällen können Sie diese Probleme ohne großen Aufwand beheben.
{:shortdesc}

## Beim Versuch, die GitHub-Toolintegration zu meiner Toolchain hinzuzufügen, wurde die Toolintegration nicht hinzugefügt. Warum?
{: troubleshoot-cannot-authorize-github}
{: troubleshoot}

Sie müssen sich bei GitHub authentifizieren, sodass {{site.data.keyword.Bluemix_notm}} autorisiert ist, auf Ihr GitHub-Konto zuzugreifen. 

Die GitHub-Toolintegration wurde nicht zu Ihrer Toolchain hinzugefügt.
{: tsSymptoms}

Wenn {{site.data.keyword.Bluemix_notm}} nicht für den Zugriff auf Ihr GitHub-Konto autorisiert ist, kann die Toolintegration nicht zur Toolchain hinzugefügt werden.
{: tsCauses}

Wenn Sie die GitHub-Toolintegration beim Erstellen Ihrer Toolchain konfigurieren, befolgen Sie diese Schritte, um eine Autorisierung mit GitHub durchzuführen:
{: tsResolve}

  1. Klicken Sie im Abschnitt mit den konfigurierbaren Integrationen auf **GitHub**.
  1. Wenn Sie die Toolchain unter {{site.data.keyword.Bluemix_notm}} Public erstellen und {{site.data.keyword.Bluemix_notm}} nicht für den Zugriff auf GitHub autorisiert ist, klicken Sie auf **Autorisieren**, um zur GitHub-Website zu wechseln.
  1. Wenn keine aktive GitHub-Sitzung existiert, werden Sie aufgefordert, sich anzumelden. Klicken Sie auf **Anwendung autorisieren**, um {{site.data.keyword.Bluemix_notm}} den Zugriff auf Ihr GitHub-Konto zu erlauben.

Wenn Sie bereits über eine Toolchain verfügen, aktualisieren Sie die Konfiguration der GitHub-Toolintegration wie folgt:

 1. Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf die Toolchain, um die zugehörige Übersichtsseite zu öffnen. Alternativ können Sie auf der Übersichtsseite der App auf der Karte für Continuous Delivery auf **Toolchain anzeigen** und dann auf **Übersicht** klicken.
 1. Klicken Sie auf der Karte für GitHub auf das Menü und klicken Sie dann auf **Konfigurieren**.
 1. Aktualisieren Sie die Konfigurationseinstellungen so, dass {{site.data.keyword.Bluemix_notm}} die Autorisierung für den Zugriff auf GitHub erhält. Klicken Sie auf **Autorisieren**, um zur GitHub-Website zu wechseln. Wenn keine aktive GitHub-Sitzung existiert, werden Sie aufgefordert, sich anzumelden. Klicken Sie auf **Anwendung autorisieren**, um {{site.data.keyword.Bluemix_notm}} den Zugriff auf Ihr GitHub-Konto zu erlauben.
 1. Wenn Sie die Aktualisierung der Einstellungen abgeschlossen haben, klicken Sie auf **Integration speichern**.
 

## Warum kann ich die {{site.data.keyword.gitrepos}}-Toolintegration aus meiner Toolchain in einer Region nicht in einer Toolchain einer anderen Region verwenden? 
{: troubleshoot-cd-grit-integration}
{: troubleshoot}

Sie können nicht dieselbe Instanz von {{site.data.keyword.gitrepos}} in mehreren Regionen verwenden. 

Wenn ich versuche, die {{site.data.keyword.gitrepos}}-Toolintegration zu meiner Toolchain hinzuzufügen, wird die folgende Fehlernachricht angezeigt:
{: tsSymptoms}

`Die Repository-URL ist nicht gültig. Das Repository muss sich in {local GitLab URL} befinden.`

Dabei ist `{local GitLab URL}` die URL der {{site.data.keyword.gitrepos}}-Toolintegration in der Region, in der sich die Toolchain befindet. 
   
Da {{site.data.keyword.gitrepos}} nahtlos mit dem {{site.data.keyword.contdelivery_short}}-Service in der Region integriert ist, in der sie ausgeführt werden, können Sie eine Instanz von {{site.data.keyword.gitrepos}} nicht in mehreren Regionen verwenden.
{: tsCauses}

Erstellen Sie statt einer {{site.data.keyword.gitrepos}}-Toolintegration eine generische GitLab-Integration und verwenden Sie diese Integration, um auf das {{site.data.keyword.gitrepos}}-Repository in einer anderen Region zu verweisen.
{: tsResolve}

1. Klicken Sie im DevOps-Dashboard auf der Seite 'Toolchains' auf die Toolchain, zu der Sie diese Integration hinzufügen wollen. Alternativ können Sie auf der Übersichtsseite der App auf der Karte für Continuous Delivery auf **Toolchain anzeigen** und dann auf **Übersicht** klicken.
1. Klicken Sie auf **Tool hinzufügen**.
1. Klicken Sie im Abschnitt mit den Toolintegrationen auf **GitLab**.
1. Klicken Sie auf den GitLab-Server, den Sie verwenden wollen. Wenn der GitLab-Server, auf dem sich das Repository befindet, auf das Sie zugreifen möchten, in dieser Liste nicht angezeigt wird, fügen Sie einen angepassten Server hinzu: 

 a. Klicken Sie auf **Angepassten Server hinzufügen**. 

 b. Geben Sie einen Namen für den Server ein. Dieser Servername wird in der Liste verfügbarer GitLab-Server angezeigt. 
 
 c. Geben Sie die Root-URL des angepassten GitLab-Servers ein. 
 
 d. Geben Sie ein persönliches Zugriffstoken für Ihren angepassten GitLab-Server ein. Wenn Sie kein persönliches Zugriffstoken haben, [erstellen Sie eines](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat). 
 
 e. Klicken Sie auf **Angepasste Integration speichern**. 
 
1. Falls Sie über ein GitLab-Repository verfügen und dieses verwenden möchten, klicken Sie beim Repository-Typ auf **Vorhanden** und geben Sie die URL ein.
1. Falls Sie ein neues GitLab-Repository verwenden möchten, geben Sie einen Namen für das Repository ein, geben Sie die URL für das Repository ein, das Sie klonen oder verzweigen, und wählen Sie den Repository-Typ aus:

 a. Klicken Sie auf **Neu**, um ein leeres Repository zu erstellen.

 b. Klicken Sie auf **Klonen**, um eine Kopie eines GitLab-Repositorys zu erstellen.

 c. Klicken Sie auf **Verzweigen**, um ein GitLab-Repository zu verzweigen, sodass Sie Änderungen per Zusammenführungsanforderungen (Merge) beitragen können.

1. Wenn Sie ein öffentliches Repository auf dem Server erstellen wollen, inaktivieren Sie das Kontrollkästchen **Repository als privat definieren**.
1. Wenn Sie GitLab Issues für die Verfolgung von Problemen verwenden möchten, wählen Sie das Kontrollkästchen **GitLab Issues aktivieren** aus.
1. Wenn Sie die Bereitstellung von Codeänderungen bei Commits durch Erstellen von Tags und Kommentaren und bei Problemen, die über die Commits referenziert werden, mit Bezeichnungen und Kommentaren verfolgen wollen, wählen Sie das Kontrollkästchen **Bereitstellung von Codeänderungen verfolgen** aus. Weitere Informationen enthält der Bluemix-Blog im Abschnitt [Mit Toolchains verfolgen, wo Ihr Code bereitgestellt wird ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}.
1. Klicken Sie auf **Integration erstellen**.

Weitere Informationen zur Konfiguration einer GitLab-Toolintegration finden Sie unter [GitLab konfigurieren](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#gitlab). 


## Warum kann ich keine Toolchain aus einer Vorlage erstellen, die ein privates Repository in einer anderen Region verwendet? 
{: troubleshoot-cd-grit-integration-private}
{: troubleshoot}

Die Toolchain-Vorlage, die Sie verwenden, verweist auf ein privates {{site.data.keyword.gitrepos}}-Repository. 

{{site.data.keyword.gitrepos}} ist regionsspezifisch. Wenn Sie versuchen, eine Toolchain aus einer Vorlage zu erstellen und eine Region als Ziel zu verwenden, in der sich das private Repository nicht befindet, schlägt die Einrichtung der Git-Integration fehl.
{: tsSymptoms}
   
Wenn Sie ein {{site.data.keyword.gitrepos}}-Repository zu einer Toolchain in einer bestimmten Region hinzufügen, wird Ihre IBM ID einem GitLab-Benutzernamen zugeordnet, der Ihnen Zugriff auf GitLab in dieser Region erteilt. Auch wenn Ihr GitLab-Benutzername in allen Regionen gleich angezeigt wird, ist der zugehörige GitLab-Benutzer in jeder Region ein anderer, da jede Region eine separate Installation von GitLab enthält. Der Zugriff auf GitLab-Benutzer in anderen Regionen wird Toolchains nicht automatisch gewährt, selbst wenn der GitLab-Benutzername identisch zu sein scheint.
{: tsCauses}

Machen Sie das {{site.data.keyword.gitrepos}}-Repository öffentlich, sodass von überall darauf zugegriffen werden kann, einschließlich anderer {{site.data.keyword.Bluemix_notm}}-Regionen.
{: tsResolve}

Wenn das Repository privat sein muss, kann der Eigner des Repositorys Zugriff darauf gewähren, indem er ein [persönliches Zugriffstoken](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat) auf dem GitLab-Server erstellt, auf dem sich das Quellenrepository befindet. Sie benötigen nur Zugriff auf das private Repository, um während der Erstellung der Toolchain den Inhalt zu klonen. Das persönliche Zugriffstoken kann mit einem Ablaufdatum erstellt werden, um seine Lebensdauer auf einen Tag zu begrenzen.  

Nachdem Sie über ein persönliches Zugriffstoken verfügen, können Sie eine URL für den Zugriff auf das Repository aus anderen Regionen erstellen. Während Sie die Toolintegration konfigurieren, aktualisieren Sie im Feld **Quellenrepository-URL** die Repository-URL so, dass Ihre Benutzername und Ihr Zugriffstoken verwendet werden. 

`https://user:XXXXXXX@git.ng.bluemix.net/group/node-hello-world`

Dabei ist `user` Ihr GitLab-Benutzername, `XXXXXXX` ist das Zugriffstoken, [`group` ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/help/user/group/index.md){:new_window} ist die Gruppe, in der das Repository gespeichert ist, und `node-hello-world` ist der Repositoryname. 

Wenn sich Ihr GitLab-Repository nicht in einer GitLab-Gruppe befindet, entspricht der Wert von `group` Ihrem Benutzernamen.
{: tip}


## Warum kann ich mein {{site.data.keyword.gitrepos}}-Repository nicht über HTTPS klonen? 
{: #troubleshoot-grit-clone-repo}
{: troubleshoot}

Sie müssen ein persönliches Zugriffstoken oder einen SSH-Schlüssel verwenden, um Git-Operationen auszuführen. 

Sie versuchen, ein Repository über die Befehlszeile mithilfe von HTTPS zu übertragen oder zu klonen, und können sich nicht authentifizieren, obwohl Sie das richtige Kennwort eingegeben haben.
{: tsSymptoms}
   
{{site.data.keyword.gitrepos}} verwendet einen Single Sign-on-Mechanismus, der eine Git-Authentifizierung anhand eines Benutzernamens und eines Kennworts über die Befehlszeile nicht unterstützt.
{: tsCauses}

Um Git-Operationen wie Klonen oder Übertragen auszuführen, müssen Sie ein persönliches Zugriffstoken oder einen SSH-Schlüssel verwenden. Weitere Informationen zum Erstellen eines persönlichen Zugriffstokens oder eines SSH-Schlüssels finden Sie im [Lernprogramm zur Einführung](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication).
{: tsResolve}

## Warum werde ich aufgefordert, mich zu authentifizieren, wenn ich versuche, mein {{site.data.keyword.gitrepos}}-Repository mithilfe von SSH zu klonen? 
{: troubleshoot-cd-grit-ssh}
{: troubleshoot}

Möglicherweise gibt es Probleme mit der Position oder den Berechtigungen für Ihren privaten SSH-Schlüssel, oder die Git-Befehlszeile verwendet nicht Ihren privaten SSH-Schlüssel für die Authentifizierung bei {{site.data.keyword.gitrepos}}. 

Ich habe meinen öffentlichen SSH-Schlüssel über die {{site.data.keyword.gitrepos}}-Benutzerschnittstelle hinzugefügt. Wenn ich versuche, ein Repository mithilfe von SSH zu klonen, werde ich aufgefordert, ein Kennwort oder einen Sicherheitscode einzugeben, oder es wird eine Fehlernachricht angezeigt, die besagt, dass die Authentifizierung fehlgeschlagen ist.
{: tsSymptoms}
   
Alle folgenden SSH-Probleme können dazu führen, dass Sie sich authentifizieren müssen oder dass eine Fehlernachricht angezeigt wird.
{: tsCauses}

* Die Git-Befehlszeile verwendet möglicherweise nicht Ihren privaten SSH-Schlüssel zur Authentifizierung bei {{site.data.keyword.gitrepos}}. 

* Ihr privater SSH-Schlüssel befindet sich möglicherweise nicht an der Standardposition '~/.ssh/id_rsa'. 

* Ihr privater SSH-Schlüssel verfügt möglicherweise nicht über die korrekten Berechtigungen (600). 


Verwenden Sie eine der folgenden Methoden, um dieses Problem zu lösen:
{: tsResolve}

* Wenn Sie die Standardposition für den privaten SSH-Schlüssel verwenden, überprüfen Sie die Berechtigungen für den Ordner '~/.ssh/' und für die private Schlüsseldatei '~/.ssh/id_rsa'. Wenn die Berechtigungen zu unspezifisch sind, verwendet SSH standardmäßig keinen privaten Schlüssel. Stellen Sie sicher, dass die Berechtigungen für den Ordner '~/.ssh/' auf 700 und die Berechtigungen für den Ordner '~/.ssh/id_rsa' auf 600 festgelegt sind. 

* Wenn sich Ihr privater Schlüssel nicht an der Standardposition befindet, verwenden Sie den folgenden Befehl, um ihn in einer Umgebungsvariablen anzugeben. 

`GIT_SSH_COMMAND='ssh -i/path/to/private_key_file' git clone git@host:owner/repo.git`

* Um dieses Problem anhand von Verbindungsinformationen zu debuggen, fügen Sie das Flag '-v' oder '-vvv' zur Umgebungsvariablen `GIT_SSH_COMMAND` hinzu: 

`GIT_SSH_COMMAND='ssh -vvv git clone git@host:owner/repo.git`

`GIT_SSH_COMMAND='ssh -vvv -i/path/to/private_key_file' git clone git@host:owner/repo.git`


## Ich habe versucht, meinem GitLab-Projekt einen Benutzer per E-Mail hinzuzufügen, aber er hat die Einladung nicht erhalten. Wie füge ich ihn zu meinem Projekt hinzu?
{: #troubleshoot-gitlab-add-user}
{: troubleshoot}

Möglicherweise wurde die Einladung vom E-Mail-Programm des Benutzers blockiert. 

Ich habe einen Benutzer zu meinem GitLab-Projekt eingeladen, indem ich eine E-Mail an seine in {{site.data.keyword.gitrepos}} aufgelistete E-Mail-Adresse gesendet habe, aber er hat die E-Mail nicht erhalten.
{: tsSymptoms}
   
Die E-Mail wurde möglicherweise vom Posteingang des Benutzers als Spam erkannt.
{: tsCauses}

Verwenden Sie eine der folgenden Methoden, um dieses Problem zu lösen:
{: tsResolve}

* Prüfen Sie in Ihrem E-Mail-Spamordner, ob die E-Mail-Einladung als Spam markiert wurde. E-Mails werden von einer noreply@-Adresse gesendet. Aktualisieren Sie Ihre Spamfilter, um E-Mails von dieser Adresse zuzulassen. 

* Untersuchen Sie, ob unternehmensweite Spamfilter, die nicht vom Benutzer eingestellt werden, die E-Mail blockieren. Bitten Sie den Benutzer, sich bei der {{site.data.keyword.gitrepos}}-Schnittstelle anzumelden, und Ihnen seine Benutzer-ID zu senden. Dann können Sie den Benutzer mithilfe seiner Benutzer-ID zum GitLab-Projekt hinzufügen. 


## Warum wird die Pipeline nicht ordnungsgemäß erstellt, wenn ich eine Toolchain aus meiner eigenen Vorlage erstelle?  
{: troubleshoot-cd-pipeline-creation}
{: troubleshoot}

Möglicherweise fehlen in Ihrer Pipeline aufgrund eines Fehlers in Ihrer 'pipeline.yaml'-Definition Ressourcen wie Jobs und Stages. 

Wenn ich versuche, eine Toolchain aus einer eigenen Vorlage zu erstellen, wird mir die folgende Fehlernachricht auf der Seite 'Pipeline' angezeigt:
{: tsSymptoms}

`Diese Pipeline wurde erstellt, möglicherweise fehlen ihr jedoch Jobs, Stages oder andere Ressourcen. Sie können diese Pipeline verwenden, oder wenn Sie es bevorzugen, können Sie sie löschen und eine andere Pipeline erstellen.`

Dieses Problem wird typischerweise durch einen Fehler in der 'pipeline.yaml'-Definition verursacht.
{: tsCauses}
   
Verwenden Sie eine der folgenden Methoden, um diesen Fehler zu debuggen:
{: tsResolve}

* Verwenden Sie die Pipelinebenutzerschnittstelle, um eine Beispielpipeline zu erstellen, die die Pipeline repliziert, die Sie mit Ihrer Vorlage zu erstellen versuchen. Hängen Sie `/yaml` an die Pipeline-URL an, um eine identische 'pipeline.yaml'-Datei zu generieren, die Sie verwenden können, um nach offensichtlichen Unterschieden zu suchen. Beispiel: `https://cloud.ibm.com/devops/pipelines/<your pipeline id>/yaml?env_id=<your region>`. 

* Verwenden Sie Mechanismus zur Erstellung von Toolchains ohne GUI. Öffnen Sie auf der Seite **Toolchain erstellen** den Debugger und werten Sie den Ausdruck `window.Testflags = {nocreate: 1}` aus. Wenn Sie in diesem Modus auf **Toolchain erstellen** klicken, wird die Toolchain nicht erstellt. Stattdessen werden die Informationen, die an die API übergeben werden, an die Konsole zurückgegeben, wo Sie sie überprüfen können. 


## Es wurde eine Toolintegration für meine Toolchain konfiguriert, aber die Konfiguration wird nicht angezeigt. Warum?
{: troubleshoot-tool-integration-error}
{: troubleshoot}

Wenn während der Einrichtung ein Fehler auftritt oder die Kommunikation zwischen der Toolchain und dem Tool nicht ordnungsgemäß abgeschlossen wird, schlägt die Konfiguration fehl. 

Nachdem Sie eine Toolintegration für Ihre Toolchain hinzugefügt und konfiguriert haben, wird eine Fehlernachricht angezeigt, dass die Konfiguration fehlgeschlagen ist.
{: tsSymptoms}

Wenn Sie eine Toolintegration hinzufügen, kommuniziert die Toolchain mit dem Tool, das durch die Toolintegration dargestellt wird, um alle notwendigen Ressourcen bereitzustellen und diese der Toolchain zuzuordnen. Wenn während der Einrichtung ein Fehler auftritt oder die Kommunikation zwischen der Toolchain und dem Tool nicht ordnungsgemäß abgeschlossen wird, so wird die Toolintegration in einen Fehlerstatus versetzt.
{: tsCauses}

 ![Fehler 'Einrichtung fehlgeschlagen'](images/tool_setup_failed.png)

Versuchen Sie, die Toolintegration erneut zu konfigurieren:
{: tsResolve}

1. Bewegen Sie auf der Karte des Tools den Mauszeiger über die Nachricht `Einrichtung fehlgeschlagen` und klicken Sie auf **Neu konfigurieren**.

 ![Schaltfläche 'Neu konfigurieren'](images/tool_reconfigure.png)

1. Stellen Sie sicher, dass Sie gültige Konfigurationsparameter verwenden. Wenn der Fehler durch eine ungültige Konfiguration verursacht wurde, wird eine Fehlermeldung angezeigt, wie zum Beispiel `Die Integration konnte nicht eingerichtet werden. Überprüfen Sie die Einstellungen und wiederholen Sie die Operation. Ursache: Ungültiger api_key:fakeKey`. Aktualisieren Sie die Einstellungen für die Toolintegration und klicken Sie auf **Integration speichern**.
1. Wenn der Fehler durch einen Kommunikationsfehler verursacht wurde, klicken Sie auf **Integration speichern**, um einen erneuten Versuch zu starten.


## Warum kann ich {{site.data.keyword.contdelivery_short}} nicht zu einer Cloud Foundry-Organisation hinzufügen? 
{: troubleshoot-resource_groups}
{: troubleshoot}

Es ist nicht länger möglich, Instanzen des {{site.data.keyword.contdelivery_short}}-Service in Cloud Foundry-Organisationen zu erstellen.  

Die folgende Nachricht wird auf der Seite 'Toolchains' für Ihre Toolchain in einer Cloud Foundry-Organisation angezeigt:
{: tsSymptoms}

`Continuous Delivery-Service erforderlich: Fügen Sie den Service zu Ihrer Organisation hinzu, um eine unterbrechungsfreie Verwendung der Servicefunktionen sicherzustellen.` 

Wenn Sie auf **Service hinzufügen** klicken, gibt es keine Möglichkeit, {{site.data.keyword.contdelivery_short}} in einer Cloud Foundry-Organisation zu erstellen. Sie können nur {{site.data.keyword.contdelivery_short}} in einer Ressourcengruppe erstellen. 

Ressourcengruppen haben Cloud Foundry-Organisationen als bevorzugte Container für Serviceinstanzen ersetzt. Sie können aber weiterhin Toolchains in Cloud Foundry-Organisationen erstellen, um bereits vorhandene {{site.data.keyword.contdelivery_short}}-Instanzen in Cloud Foundry-Organisationen zu unterstützen.
{: tsCauses}

Erstellen Sie Ihre Toolchain erneut in Ressourcengruppen und entfernen Sie dann die ursprüngliche Toolchain aus der Cloud Foundry-Organisation. Alternativ können Sie die Fehlernachricht ignorieren, bis eine Methode zur Migration vorhandener Toolchains aus Cloud Foundry-Organisationen zu Ressourcengruppen eingeführt wird.
{: tsResolve}


## Warum kann ich Toolchains nicht über die `ibmcloud`-Befehlszeilenschnittstelle löschen? 
{: troubleshoot-delete_toolchains_cli}
{: troubleshoot}

Derzeit können Toolchains nicht über die 'ibmcloud resource'-Befehlszeilenschnittstelle gelöscht werden.  

Ich habe versucht, eine Toolchain unter Angabe des Befehls `ibmcloud resource service-instance-delete` über die Befehlszeile zu löschen, aber der Befehl ist mit der folgenden Fehlernachricht fehlgeschlagen:
{: tsSymptoms}

`Fehlercode: RC-ServiceBrokerErrorResponse
Nachricht: Beschreibung: Das Löschen der Toolchain muss über das Toolchain-Dashboard erfolgen`

Toolchains sind ein spezieller Typ von Ressource auf der Cloudplattform, den Sie derzeit nicht über die Befehlszeilenschnittstelle `ibmcloud resource` löschen können.
{: tsCauses}

Gehen Sie wie folgt vor, um eine Toolchain zu löschen:
{: tsResolve}

1. Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf die Toolchain, die gelöscht werden soll. Alternativ können Sie auf der Übersichtsseite der App auf der Karte für Continuous Delivery auf **Toolchain anzeigen** klicken.
1. Klicken Sie neben **App anzeigen** auf das Menü **Weitere Aktionen**.
1. Klicken Sie auf **Löschen**. Beim Löschen einer Toolchain werden auch alle zugehörigen Toolintegrationen entfernt, was unter Umständen bewirkt, dass von diesen Integrationen verwaltete Ressourcen ebenfalls gelöscht werden.
1. Bestätigen Sie das Löschen, indem Sie den Namen der Toolchain eingeben und auf **Löschen** klicken.  


## Warum ist Live Edit nach dem Festschreiben und Übertragen in einer Repository nicht verfügbar? 
{: #troubleshoot-liveedit}
{: troubleshoot}

Bei einer Bereitstellung außerhalb der {{site.data.keyword.webide}} von Eclipse Orion wird der Live Edit-Modus gelöscht. 

Sie schreiben eine Änderung fest und übertragen sie über die Befehlszeile oder die {{site.data.keyword.webide}} und Live Edit ist nicht verfügbar.
{: tsSymptoms}
   
Wenn Sie eine Toolchain erstellen, die sowohl eine {{site.data.keyword.contdelivery_short}}-Pipeline als auch die {{site.data.keyword.webide}} enthält, können beide Toolintegrationen Ihre Anwendung (App) bereitstellen. Standardmäßig stellen die Pipeline und die {{site.data.keyword.webide}} in derselben Cloud Foundry-Organisation und im selben Bereich unter Verwendung derselben Cloud Foundry-App und -URL bereit. Bei einer Bereitstellung außerhalb der {{site.data.keyword.webide}} wird der Live Edit-Modus gelöscht.
{: tsCauses}

Um mithilfe von Live Edit schnell eine Testversion Ihrer App zu entwickeln, stellen Sie über die {{site.data.keyword.webide}} eine andere Cloud Foundry-App, einen anderen Bereich und eine andere URL bereit. Wenn Ihre Codeänderungen abgeschlossen sind, können Sie den Code festschreiben und übertragen, um die Pipeline zu triggern, die Produktionsversion Ihrer App zu erstellen und bereitzustellen.
{: tsResolve}

1. Wählen Sie in der Ausführungsleiste die Startkonfiguration aus, die Sie bearbeiten möchten. 
2. Bearbeiten Sie die Werte, die für 'Space' und 'Host' angegeben sind. 
3. Klicken Sie auf **Speichern** und **Beenden**. 
4. Klicken Sie auf die Schaltfläche **Ausführen** in der Ausführungsleiste. Es kann sein, dass Sie dies mehrfach wiederholen müssen, um die Schaltfläche 'Live Edit' zu aktivieren. 

Weitere Informationen zu Live Edit finden Sie unter [Live Edit](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-live-syn#live-edit). 


## Was bedeutet 'nicht synchronisiert' in der {{site.data.keyword.webide}}-Ausführungsleiste? 
{: #troubleshoot-web-ide-sync}
{: troubleshoot}

Das Dateisystem in Ihrem Arbeitsbereich ist nicht synchron. 

Im Live Edit-Modus synchronisiert die {{site.data.keyword.webide}} Dateien aus Ihrem Arbeitsbereich mit der aktiven Cloud Foundry-App und die Dateien sind nicht synchron.
{: tsSymptoms}
   
Möglicherweise ist das Dateisystem in Ihrem Arbeitsbereich nicht synchron, wenn die App außerhalb der {{site.data.keyword.webide}} geändert wird. Oder es ist nicht synchron, wenn die {{site.data.keyword.webide}} den Synchronisationsstatus nicht aus der App abrufen kann.
{: tsCauses}

Der Status kann sich nach ein oder zwei Minuten normalisieren, wenn wieder eine Verbindung hergestellt wurde und die Dateien synchronisiert wurden. Andernfalls können Sie die App mit aktiviertem Live Edit-Modus starten und stoppen.
{: tsResolve}
