---

copyright:
  years: 2018
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

# Persönliche Daten in Continuous Delivery verwalten
{: #cd_personal_data}

Sie können mit {{site.data.keyword.contdelivery_full}} persönliche Daten ändern, exportieren oder löschen.
{: shortdesc}

Persönliche Daten sind Informationen, die sich auf eine natürliche Person beziehen oder diese identifizieren. Persönliche Daten können beispielsweise ein Name, eine E-Mail-Adresse, ein Avatar, ein Token oder eine beliebige Anzahl von Kennungen sein, die mit {{site.data.keyword.contdelivery_short}} verwendet werden. Die folgenden {{site.data.keyword.contdelivery_short}}-Komponenten enthalten persönliche Daten:

 * Die Eclipse Orion-{{site.data.keyword.webide}}
 * {{site.data.keyword.gitrepos}}
 * {{site.data.keyword.contdelivery_short}}-Pipelines
 * Toolchains und Toolintegrationen
 * [GitHub Enterprise on IBM Cloud ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/services/ghededicated/ghe_personal_data.html){: new_window}
 * [{{site.data.keyword.DRA_full}} ![Symbol zum externen Link](../../icons/launch-glyph.svg "Symbol zum externen Link")](/docs/services/DevOpsInsights/insights_personal_data.html){: new_window}
 
IBM verwaltet keine Daten im Service {{site.data.keyword.contdelivery_short}}. Bevor Sie den Service {{site.data.keyword.contdelivery_short}}, der in {{site.data.keyword.Bluemix_notm}} Public gehostet wird, verlassen, müssen Sie Ihre eigenen Daten löschen.
{: important}

{{site.data.keyword.contdelivery_short}} bietet die entsprechenden Berechtigungen zum Verwalten von Daten in einer Ressourcengruppe oder Cloud Foundry-Organisation. Ihr Unternehmen verfügt möglicherweise über Richtlinien, die diese Berechtigungen einschränken. Wenn Sie nicht über die entsprechenden Berechtigungen verfügen, wenden Sie sich an den Administrator Ihres {{site.data.keyword.Bluemix_notm}}-Kontos.

Um Ihre persönlichen Daten zu verwalten, müssen Sie IBM Cloud-Konten, die Verwendung dieser Konten und die zugehörigen Zugriffsberechtigungen verstehen.
 
## Konten und Zugriffsberechtigungen
{: #accounts_access_rights}

Um mit IBM Cloud arbeiten zu können, müssen Sie sich mit einem Benutzernamen und einem Kennwort anmelden. IBM Cloud weist bei Ihrer Anmeldung Ihrer Benutzerberechtigung mindestens ein IBM Cloud-Konto zu. Wenn Sie Ressourcen erstellen, wie Cloud Foundry-Organisationen, Ressourcengruppen, Toolchains und {{site.data.keyword.contdelivery_short}}-Objekte, werden diese einem IBM Cloud-Konto zugewiesen.

Die IBM Cloud-Anmeldestruktur bietet Ihnen die Möglichkeit, in verschiedenen Konten zu arbeiten. Mit der IBM Cloud-Benutzerschnittstelle können Sie zwischen den Konten wechseln. Wenn Sie sich anmelden, sind möglicherweise folgende Kontotypen mit Ihren Benutzerberechtigungen zugewiesen: 

 * Persönliches Konto
 * Unternehmenskonto
 * Individuelles Unternehmenskonto

###Persönliche Konten

In der Regel hat jeder Benutzer sein eigenes Konto, das sein persönliches Konto ist. Sie können Ihr persönliches Konto leicht identifizieren, da es normalerweise Ihren Namen enthält. Beispiel *Konto von John Smith*. 

Sie haben volle Berechtigungen für alle Objekte, die in Ihrem persönlichen Konto erstellt wurden. Sie können andere Benutzer einladen, an Ihrem Konto teilzunehmen, ihnen Berechtigungen für die von Ihnen erstellten Objekte zuweisen und ihnen Berechtigungen zum Erstellen von Objekten in Ihrem Konto geben. Dies bedeutet, dass sich die persönlichen Daten anderer Nutzer möglicherweise in Ihrem Konto befinden und dass Ihre persönlichen Daten in den Konten anderer Nutzer enthalten sein können. 

Wenn Sie die Berechtigung zum Erstellen eines Objekts in einem Konto haben, haben Sie auch die Berechtigung, es zu ändern und zu löschen, unabhängig davon, in welchem Konto das Objekt gespeichert ist. Wenn zwei Benutzer zusammenarbeiten, teilen sie sich meistens ein persönliches Konto.

###Unternehmenskonten

Ein Unternehmenskonto wird von Ihrem Unternehmen eingerichtet. Sie werden in der Regel automatisch zum Konto hinzugefügt und nicht eingeladen. Unternehmenskonten bieten Benutzern einen Ort zum Arbeiten, Kommunizieren und Teilen von Ressourcen und Gebühren. Dies ist jedoch nur eine Konvention. Ein Unternehmenskonto unterscheidet sich kaum von einem persönlichen Konto. Objekte, die in einem Unternehmenskonto erstellt wurden, werden dem Konto zugewiesen und Benutzer können zum Konto eingeladen werden.

Teams aus mehreren Personen, die für ein Unternehmen arbeiten, arbeiten oft über ein Unternehmenskonto zusammen.

###Individuelle Unternehmenskonten

Wenn Sie für ein Unternehmen arbeiten, ist die Arbeit in Ihrem Konto möglicherweise rechtmäßig im Besitz des Unternehmens. Viele Benutzer, die für ein Unternehmen arbeiten, haben deshalb ein individuelles Unternehmenskonto. Wenn Sie sich bei Ihrem Konto anmelden, indem Sie Ihre Berechtigungsnachweise verwenden, die den Namen Ihres Unternehmens enthalten, und möglicherweise auch ein persönliches Konto hat, kann die Arbeit in Ihrem persönlichen Konto zum Unternehmen gehören.

Ein individuelles Unternehmenskonto unterscheidet sich nicht von anderen Konten. Sie können Benutzer zu einem individuellen Unternehmenskonto einladen. Objekte, die in einem individuellen Unternehmenskonto erstellt werden, gehören zu diesem Konto.

Wenn Sie für ein Unternehmen arbeiten, dem Ihre Arbeit gehört, wird ein persönliches Konto, das normalerweise Ihren Namen enthält, als individuelles Unternehmenskonto bezeichnet. 

## Persönliche Daten ändern, exportieren und löschen
{: #managing_personal_data}

Unabhängig davon, welcher Typ von IBM Cloud-Konto verwendet wird, können Sie die Objekte im Konto ändern, exportieren und löschen, wenn Sie Rechte an den Objekten im Konto besitzen. Bevor Sie Änderungen vornehmen, sprechen Sie sich mit anderen Benutzern ab, um sicherzustellen, dass Sie Daten nicht versehentlich ändern oder löschen.

Bevor Sie Daten aus einem Konto löschen, müssen Sie prüfen, ob es sich um ein persönliches Konto oder ein individuelles Unternehmenskonto handelt.

###Persönliches Konto

Wenn Sie ein persönliches Konto besitzen, können Sie Änderungen vornehmen und Daten löschen. Wenn Sie Ihr Konto für einen anderen Benutzer freigeben, besitzen Sie die Daten. Sie können sich jedoch mit den anderen Benutzern über die gemeinsame Arbeit austauschen. 

Wenn Sie sich bei Ihrem IBM Cloud-Konto nicht anmelden können, [wenden Sie sich an den IBM Support ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/cloud/support){:new_window}.
 
###Individuelles Unternehmenskonto

Wenn Sie ein individuelles Unternehmenskonto besitzen, müssen Sie Änderungen mit Ihrem Unternehmen und anderen Mitgliedern Ihres Teams koordinieren. Löschen Sie Ihre persönlichen Daten, unabhängig davon, ob sie in einem Unternehmenskonto oder einem individuellen Unternehmenskonto gespeichert sind. Achten Sie darauf, dass Sie keine Arbeit löschen, die Sie mit anderen Benutzern gemeinsam nutzen.

Bevor Sie Ihre persönlichen Daten für die {{site.data.keyword.contdelivery_short}}-Komponenten verwalten, stellen Sie sicher, dass Sie mit Ihrem IBM Cloud-Konto arbeiten. Um das IBM Cloud-Konto anzuzeigen, in dem Sie gerade arbeiten, klicken Sie in der Menüleiste auf den Avatar Ihres Profils. 

Wenn Sie sich bei Ihrem IBM Cloud-Konto nicht anmelden können, wenden Sie sich an Ihr Unternehmen und löschen Sie gemeinsam Ihre persönlichen Daten.

Wenn Sie alle Ihre persönlichen Daten aus {{site.data.keyword.contdelivery_short}} löschen möchten, ist die Reihenfolge wichtig, in der Sie diese Daten löschen. Löschen Sie zuerst Ihre {{site.data.keyword.webide}}-Arbeitsbereiche. Dann löschen Sie Ihre {{site.data.keyword.gitrepos}}-Daten. Löschen Sie anschließend Ihr {{site.data.keyword.gitrepos}}-Konto. Löschen Sie zuletzt Ihre Delivery Pipelines, Toolintegrationen und Toolchains.
{: tip}

## Web-IDE-Daten exportieren und löschen
{: #managing_web_ide_data}

Die {{site.data.keyword.webide}} stellt einen persönlichen Arbeitsbereich in der Cloud bereit. Mit der {{site.data.keyword.webide}} können Sie Git-Repositorys klonen und Dateien bearbeiten. Ihr {{site.data.keyword.webide}}-Arbeitsbereich gehört Ihnen und wird von keinem anderen Konto genutzt.

Bevor Sie Ihre {{site.data.keyword.webide}}-Daten löschen, sollten Sie Ihre Arbeit exportieren. Wenn Sie Ihre Arbeitsbereiche gelöscht haben, werden Sie aus {{site.data.keyword.contdelivery_short}} entfernt und alle Dateien sind gelöscht.
{: important}

###Web-IDE-Arbeitsbereiche exportieren

Gehen Sie wie folgt vor, um einen {{site.data.keyword.webide}}-Arbeitsbereich zu exportieren:

1. Wählen Sie **Datei > Exportieren > Zip** aus.
1. Wiederholen Sie dies für jeden Arbeitsbereich, den Sie exportieren möchten.

###Web-IDE-Arbeitsbereiche löschen

Gehen Sie wie folgt vor, um Ihren {{site.data.keyword.webide}}-Arbeitsbereich und alle persönlichen Daten zu löschen:

1. Navigieren Sie von jeder Toolchain aus zur {{site.data.keyword.webide}}.
1. Klicken Sie in der Navigationsseitenleiste links auf das Symbol **Einstellungen** <img class="inline" src="images/webide_settings_icon_light_small.png"  alt="Symbol 'Einstellungen'">.
1. Klicken Sie auf **BENUTZERPROFIL**.
1. Klicken Sie auf **Löschen**, um alle Daten aus der {{site.data.keyword.webide}} zu entfernen.

Die {{site.data.keyword.webide}} verwendet einen Single Sign-on. Wenn Sie das erste Mal auf diese Toolintegration zugreifen, wird ein entsprechendes ausgeblendetes {{site.data.keyword.webide}}-Konto für Ihr IBM Cloud-Konto erstellt. Wenn Sie alle Arbeitsbereiche gelöscht haben, greifen Sie nicht auf die {{site.data.keyword.webide}} zu. Denn wenn Sie erneut auf die {{site.data.keyword.webide}} zugreifen, wird automatisch ein neues Konto erstellt, das Sie dann wieder löschen müssen.
{: important}

## Git Repos and Issue Tracking-Daten ändern, exportieren und löschen
{: #managing_grit_data}

{{site.data.keyword.gitrepos}} bietet einen gehosteten Git-Service in der Cloud. Mit einem Single-Sign-On wird Ihr IBM Cloud-Konto einem Git-Konto zugeordnet. Für Sie werden in Ihrem Git-Konto ein vollständiger Name und ein Kurzname erstellt. Andere Benutzer können Ihren Kurznamen verwenden, um in einem Kommentar zu einem Git-Problem auf Sie zu verweisen. Sie können Ihr Git-Konto anpassen und persönliche Daten hinzufügen, wie z. B. eine Beschreibung von sich selbst oder ein Bild. 

{{site.data.keyword.gitrepos}} bietet eine leistungsfähige, aber komplexe Social-Coding-Umgebung, in der Benutzer zu verschiedenen Projekten beitragen und Objekte gemeinsam nutzen. Diese Umgebung kann das Suchen und Löschen Ihrer persönlichen Daten schwierig machen.

Ihre Kontoprofile und Einstellungen, persönlichen Projekte, Gruppen und Snippets sind mit Ihrem Git-Konto verbunden. Wenn Sie Ihr Git-Konto löschen, löschen Sie auch diese Objekte. Um persönliche Daten in einem anderen Projekt zu löschen, navigieren Sie zu diesem Projekt. Ändern Sie es, um Ihre persönlichen Daten zu löschen, oder löschen Sie das ganze Projekt. Sprechen Sie sich auf jeden Fall mit den anderen Mitgliedern Ihres Teams ab, bevor Sie ein gemeinsam genutztes Projekt löschen.

Löschen Sie erst Ihre persönlichen Daten aus anderen Projekten, bevor Sie Ihr Git-Konto löschen. Wenn Sie Ihr Git-Konto gelöscht haben, kann es schwierig oder unmöglich sein, alle Projekte zu finden, an denen Sie mitgewirkt haben.
{: tip}

###Persönliche und gemeinsam genutzte Projekte

Sie können andere Benutzer für eine Zusammenarbeit an Projekten einladen. Git-Projekte, die Sie in Ihrem Konto erstellen, werden als persönliche Projekte bezeichnet. Sie können auch Git-Gruppen erstellen, in denen Projekte mehrere Git-Besitzer haben. Sie können für die Gruppe neue Projekte erstellen oder die Eigentumsrechte für persönliche Projekte an die Gruppe übertragen. Eine Git-Gruppe wird häufig zur Darstellung eines IBM Cloud-Unternehmenskontos verwendet, um die Eigentumsrechte an Projekten des Unternehmens anzuzeigen.

###Git Repos and Issue Tracking-Projekte exportieren

Bevor Sie ein {{site.data.keyword.gitrepos}}-Projekt löschen, können Sie das Projekt für eine Archivierung exportieren. 

1. Klicken Sie in der Navigationsseitenleiste links auf das Symbol **Einstellungen** <img class="inline" src="images/webide_settings_icon_light_small.png"  alt="Symbol 'Einstellungen'">.
1. Klicken Sie auf **Allgemein**.
1. Klicken Sie auf **Einblenden**, um den Abschnitt zum Exportieren von Projekten einzublenden.
1. Klicken Sie auf **Projekt exportieren**.

Nachdem das Projekt archiviert wurde, können Sie es in eine andere GitLab-Instanz importieren. 

###Ihr Git Repos and Issue Tracking-Konto löschen

Sie können Ihr {{site.data.keyword.gitrepos}}-Konto und alles, was zu diesem Konto gehört, löschen.

1. Klicken Sie im {{site.data.keyword.gitrepos}}-Dashboard für Benutzereinstellungen auf der [Seite für das Konto ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/profile/account?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window} im Abschnitt zum Löschen des Kontos auf **Konto löschen**.
1. Alle Git-Projekte sowie Repositorys und Probleme werden gelöscht. Sie werden außerdem aus allen {{site.data.keyword.gitrepos}}-Gruppen entfernen, denen Sie angehören.

Nachdem Ihr Konto gelöscht wurde, bleiben einige Inhalte erhalten. Dieser Inhalt wird einem systemweiten Ghost-Benutzer zugewiesen. Weitere Informationen zum Löschen eines {{site.data.keyword.gitrepos}}-Kontos finden Sie in [Benutzerkonten löschen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/profile/account/delete_account#associated-records){:new_window}.
{: tip}

{{site.data.keyword.gitrepos}} verwendet einen Single-Sign-On, der automatisch ein entsprechendes Git-Konto für Ihr IBM Cloud-Konto erstellt, wenn Sie das erste Mal auf die Toolintegration zugreifen. Wenn Sie Ihr Konto gelöscht haben, greifen Sie nicht auf {{site.data.keyword.gitrepos}} zu. Denn wenn Sie erneut auf {{site.data.keyword.gitrepos}} zugreifen, wird automatisch ein neues Konto erstellt, das Sie dann wieder löschen müssen.
{: important}

## Continuous Delivery-Pipeline-Daten ändern, exportieren und löschen
{: #managing_pipeline_data}

{{site.data.keyword.contdelivery_short}}-Pipelines führen Scripts zum Erstellen, Testen und Bereitstellen Ihrer Anwendung in IBM Cloud aus. Zu diesem Zweck stellen Pipelines Stages, Jobs, Umgebungsvariablen und andere Objekte bereit, die möglicherweise persönliche Daten enthalten. Sie können diese Objekte einzeln oder eine gesamte Pipeline löschen.

Sprechen Sie sich auf jeden Fall mit den anderen Mitgliedern Ihres Teams ab, bevor Sie gemeinsam genutzte Objekte oder Pipelines löschen. Das Löschen einer Stage kann dazu führen, dass eine Pipeline fehlschlägt.

Eine Pipeline kann nicht außerhalb einer Toolchain existieren. Wenn Sie eine Toolchain löschen, werden auch alle Pipelines gelöscht, die der Toolchain zugeordnet sind. Wenn Sie eine gesamte Toolchain löschen möchten, muss nicht jede Pipeline einzeln gelöscht werden. Befolgen Sie stattdessen die Anweisungen im Abschnitt "Toolchains und Toolintegrationen ändern und löschen", um eine Toolchain zu löschen.
{: important}

Pipeline-Stages können persönliche Daten enthalten wie Berechtigungsnachweise in der Form von Umgebungseigenschaften und eine Pipelinedefinition, die den aktuellen Status der Pipeline anzeigt. Stages können auch Scripts innerhalb von Jobs enthalten, die Sie ändern oder löschen möchten, sowie Artefakte und Protokolle für die aktuellsten Pipelineausführungen, die Sie exportieren möchten. Verwenden Sie die Aktionen zum Konfigurieren oder zum Löschen von Stages, um eine Stage zu ändern oder zu löschen. Verwenden Sie die Aktion 'Download', um Artefakte oder Protokolle aus einer Stage zu exportieren.

  ![Menü 'Stages'](images/pipeline_stages.png)

###Eine Pipeline-Stage ändern

Gehen Sie wie folgt vor, um eine Pipeline-Stage zu ändern:

1. Klicken Sie auf der Pipeline-Seite auf das Symbol **Einstellungen**.
1. Klicken Sie auf **Stage konfigurieren**.
1. Bearbeiten oder löschen Sie auf der Registerkarte **UMGEBUNGSEIGENSCHAFTEN** die Eigenschaften.
1. Ändern Sie das Job-Script in der Pipeline-Stage. Wählen Sie den Job aus und ändern Sie die Werte, die Teil der Build-, Bereitstellungs- oder Testkonfiguration sind.
   
   ![Job-Script ändern](images/job_script.png)
  
1. Löschen Sie einen Job aus der Pipeline-Stage. Wählen Sie auf der Registerkarte **JOBS** den Job aus, den Sie löschen möchten, und klicken Sie auf **Entfernen**.
 
###Eine Pipeline-Stage exportieren

Fügen Sie zum Exportieren der Definition einer Pipeline-Stage `/yaml` an die Pipeline-URL an:

`http(s)://<DevOps Services domain>/pipeline/user/project/yaml`


Gehen Sie wie folgt vor, um Artefakte und Protokolle für eine Pipeline-Stage zu exportieren:

1. Klicken Sie auf der Pipeline-Seite auf **Protokolle und Verlauf anzeigen**.
1. Klicken Sie auf die Buildnummer, für die Sie Artefakte und Protokolle exportieren wollen.
1. Klicken Sie auf **DOWNLOAD** > **Artefakte**, um die Artefakte für den ausgewählten Build zu exportieren.
1. Klicken Sie auf **DOWNLOAD** > **Protokolle**, um die Protokolle für den ausgewählten Build zu exportieren.  

###Eine Pipeline-Stage löschen

Gehen Sie wie folgt vor, um eine Pipeline-Stage zu löschen:

1. Klicken Sie auf der Pipeline-Seite auf das Symbol **Einstellungen**.
1. Klicken Sie auf **Stage löschen**.

## Toolchains und Toolintegrationen ändern und löschen
{: #managing_toolchains}

Mithilfe von Toolchains können Teams zusammenarbeiten und gemeinsam verschiedene Toolintegrationen nutzen. 

Es wird empfohlen, alle {{site.data.keyword.contdelivery_short}}-Integrationen zu konfigurieren, indem Sie Daten verwenden, die Ihrem Team oder Unternehmen zugeordnet sind. Verwenden Sie nicht die Daten, die Ihnen zugeordnet sind. Ihre persönlichen Daten könnten sonst versehentlich verwendet werden. In solchen Fällen müssen Sie Ihre eigenen Daten identifizieren und löschen.

Wenn eine Toolintegration erstellt wird, kann {{site.data.keyword.contdelivery_short}} nicht die Herkunft aller Daten aufzeichnen. Beispielsweise kann ein anderes Teammitglied für Sie eine Toolintegration erstellen, indem er persönliche Daten verwendet, die Sie in einer E-Mail mitteilen. Sie müssen wissen, welche Daten ihnen gehören, und sicherstellen, dass sie gelöscht werden.

Sprechen Sie sich mit den anderen Mitgliedern Ihres Teams ab, bevor Sie gemeinsam genutzte Toolintegrationen oder Toolchains löschen.

###Toolintegrationen ändern und löschen

Wenn Sie eine Toolintegration erstellen, müssen Sie Benutzerberechtigungen und andere Kontoinformationen bereitstellen, die sich auf die Integration beziehen. Wenn Sie Ihre persönlichen Berechtigungsnachweise und Kontoinformationen verwendet haben, ersetzen Sie diese Informationen durch andere Werte oder löschen Sie die Toolintegration.

Gehen Sie wie folgt vor, um eine Toolintegration zu ändern:

1. Klicken Sie auf der Karte des Tools auf das Menü, um auf die Konfigurationsoptionen zuzugreifen.

  ![Menü für die Toolkonfiguration](images/toolchain_tile_menu.png)

1. Wenn Sie die Aktualisierung der Einstellungen abgeschlossen haben, klicken Sie auf **Integration speichern**.

Gehen Sie wie folgt vor, um eine Toolintegration zu löschen:

1. Um eine Toolintegration aus Ihrer Toolchain zu löschen, klicken Sie auf **Löschen**.
1. Bestätigen Sie dies, indem Sie nochmals auf **Löschen** klicken.

###Toolchains löschen

Wenn Sie eine Toolchain löschen, kann diese Löschung nicht mehr rückgängig gemacht werden.

1. Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf die Toolchain, die gelöscht werden soll. Alternativ können Sie auf der Übersichtsseite der App auf der Karte für Continuous Delivery auf **Toolchain anzeigen** klicken.
1. Klicken Sie neben **App anzeigen** auf das Menü **Weitere Aktionen**.
1. Klicken Sie auf **Löschen**. Beim Löschen einer Toolchain werden auch alle zugehörigen Toolintegrationen und Pipelines entfernt, was unter Umständen bewirkt, dass von diesen Integrationen verwaltete Ressourcen ebenfalls gelöscht werden.
1. Bestätigen Sie das Löschen, indem Sie den Namen der Toolchain eingeben und auf **Löschen** klicken. 

Wenn Sie eine Toolchain löschen, werden die zugeordneten {{site.data.keyword.gitrepos}}-Repositorys nicht gelöscht. Benutzer, die Zugriff auf diese Repositorys haben, verfügen möglicherweise über Kopien der Daten, falls sie `git clone` ausgeführt oder einen {{site.data.keyword.webide}}-Arbeitsbereich erstellt haben. Um sicherzustellen, dass alle Daten gelöscht werden, müssen Sie diese Benutzer bitten, ihre Kopien der Daten zu löschen.
{: tip}

###Alle Toolchains löschen

Sie können nicht alle Toolchains in einer Ressourcengruppe oder Organisation gleichzeitig löschen. Sie müssen jede Toolchain einzeln löschen.

Toolchains werden nach IBM Cloud-Region und Ressourcengruppe oder Cloud Foundry-Organisation verwaltet. Stellen Sie sicher, dass Sie jede Region und Ressourcengruppe oder Organisation in der Region auswählen, um jede von Ihnen erstellte Toolchain zu löschen.
{: tip}
