---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-25"

keywords: users of a service instance, a-service, Git Repos

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Einschränkungen beim Plan und bei der Nutzung
{: #limitations_usage}

Die Verwendung von {{site.data.keyword.contdelivery_full}} ist auf das Erstellen, Bereitstellen, Testen und auf den laufenden Betrieb von Anwendungen auf der {{site.data.keyword.Bluemix_notm}}-Plattform oder anderen kompatiblen Platform-as-a-Service- (PaaS) oder Infrastructure-as-a-Service-Angeboten (IaaS) beschränkt.

## Berechtigte Benutzer
{: #authorized_users}

{{site.data.keyword.contdelivery_short}}-Servicepläne werden anhand der Anzahl der autorisierten Benutzer einer Serviceinstanz definiert und berechnet. Jeder Benutzer, der etwas zu einer Leistung beiträgt, zählt als berechtigter Benutzer, einschließlich:

 * Benutzer, die mit Problemen, Issue-Boards, Quellcodes oder anderen Artefakten in einem {{site.data.keyword.gitrepos}}-Repository arbeiten.
 * Benutzer, die Bearbeitungen oder Trigger (entweder direkt in der Benutzeroberfläche oder indirekt, indem sie einen Repository-Vorgang ausführen) durchführen oder den Status einer Delivery Pipeline anzeigen.
 * Benutzer, die mit der Eclipse Orion-{{site.data.keyword.webide}} arbeiten.

### Wie werden Benutzer für Instanzen von {{site.data.keyword.contdelivery_short}} in Organisationen gezählt?

Berechtigte Benutzer werden gezählt, indem alle Benutzer in der Cloud-Organisation, die den {{site.data.keyword.contdelivery_short}}-Service enthält, berücksichtigt werden.

Um die Liste der Benutzer in Ihrer Organisation in einer {{site.data.keyword.Bluemix_notm}} Public-Umgebung anzuzeigen, klicken Sie in der Menüleiste auf **Verwalten > Konto**. Klicken Sie dann auf **Cloud Foundry-Organisationen**. 

Um die Liste der Benutzer in Ihrer Organisation in einer {{site.data.keyword.Bluemix_notm}} Dedicated-Umgebung anzuzeigen, klicken Sie in der Menüleiste auf **Konto > Organisationen verwalten**.

Sie können auch alle Instanzen des Service {{site.data.keyword.contdelivery_short}} in Ihrem Konto und die Anzahl der Benutzer anzeigen, die für jede Instanz in einer {{site.data.keyword.Bluemix_notm}} Public-Umgebung gemeldet werden.

1. Klicken Sie in der Menüleiste auf **Verwalten > Abrechnung und Nutzung**. 
2. Klicken Sie auf **Nutzung**. 
3. Klicken Sie im Abschnitt **Services** für den {{site.data.keyword.contdelivery_short}}-Service auf **Pläne anzeigen**. 
4. Klicken Sie für den Plan, zu dem Sie Informationen anzeigen möchten, auf **Details anzeigen**. 
5. Klicken Sie für die Instanz von {{site.data.keyword.contdelivery_short}}, zu der Sie Nutzungsinformationen anzeigen möchten, auf **Instanzdetails anzeigen**. 

Um alle Instanzen des Service {{site.data.keyword.contdelivery_short}} in Ihrem Konto und die Anzahl der Benutzer anzuzeigen, die für jede Instanz in einer {{site.data.keyword.Bluemix_notm}} Dedicated-Umgebung gemeldet werden:

1. Klicken Sie in der Menüleiste auf **Konto > Organisationen verwalten**.
2. Klicken Sie auf **Nutzungsdashboard**.

### Wie werden Benutzer für Instanzen von {{site.data.keyword.contdelivery_short}} in Ressourcengruppen gezählt?

Berechtigte Benutzer werden gezählt, indem Sie die Liste der Benutzer auf der Registerkarte 'Verwalten' in der Instanz des Service {{site.data.keyword.contdelivery_short}} anzeigen.

Um die Liste der berechtigten Benutzer anzuzeigen, öffnen Sie das Dashboard der Serviceinstanz und klicken Sie auf die Registerkarte 'Verwalten'.

Sie können auch alle Instanzen des {{site.data.keyword.contdelivery_short}}-Service in Ihrem Konto und die Anzahl der Benutzer anzeigen, die für jede Instanz gemeldet werden.

1. Klicken Sie in der Menüleiste auf **Verwalten > Abrechnung und Nutzung**. 
2. Klicken Sie auf **Nutzung**. 
3. Klicken Sie im Abschnitt **Services** für den {{site.data.keyword.contdelivery_short}}-Service auf **Pläne anzeigen**. 
4. Klicken Sie für den Plan, zu dem Sie Informationen anzeigen möchten, auf **Details anzeigen**. 
5. Klicken Sie für die Ressourcengruppe, zu der Sie Nutzungsinformationen anzeigen möchten, auf **Instanzdetails anzeigen**. 

### Was passiert, wenn Sie die Grenzwerte Ihres Serviceplans überschreiten?

Einige Servicepläne haben möglicherweise andere Einschränkungen, z. B. die Anzahl der auszuführenden Delivery Pipeline-Jobs oder die Speicherbelegung. Weitere Informationen finden Sie in der Planbeschreibung im Katalog. Wenn eine der Planbeschränkungen in einem Abrechnungszeitraum überschritten wird, kann der Service ausgesetzt werden. Beispiel: Aufträge für die Delivery Pipeline werden möglicherweise nicht für den Rest des Abrechnungszeitraums ausgeführt.

## Delivery Pipeline-Verwendung
{: #pipeline_usage}

Das akzeptable Nutzungsverhalten umfasst die folgenden Verhaltensweisen, ist aber nicht auf diese beschränkt:

* Die Kompilierung und Assemblierung von Artefakten für unterstützte Programmiersprachen
* Die automatisierte Bereitstellung von Anwendungsartefakten, Konfigurationen und unterstützenden Ressourcen oder Services
* Das Testen, Validieren oder sonstiges durch Entwicklungsereignisse generierte Verhalten, das als Ergebnis eines Entwicklungsprozesses ausgelöst wird

Das nicht zulässige Nutzungsverhalten umfasst die folgenden Verhaltensweisen, ist aber nicht auf diese beschränkt:

* Die Verwendung von Pipeline-Jobs oder Workern für allgemeines Berechnungsverhalten, wie Bitcoin-Mining, verteilte Denial-of-Service-Angriffe (DoS) und böswilliges oder anstößiges Verhalten gegenüber anderen Clients oder Benutzern innerhalb der IBM Cloud-Plattform oder gegenüber allgemeinen Internetbenutzern
* Die Verwendung im normalen Entwicklungsprozess für Websites oder Services, die zum Hass anstacheln (Hassreden) oder andere Aktivitäten, die gegen die IBM Geschäftsgrundsätze verstoßen
* Die Verwendung von ereignisgeneriertem Verhalten für böswillige Angriffe von außen oder Angriffe gegen {{site.data.keyword.Bluemix_notm}} oder andere Sites

Nach dem Ermessen von IBM können Benutzer, die gegen das akzeptable Nutzungsverhalten der {{site.data.keyword.contdelivery_short}}-Services oder gegen die [IBM Geschäftsgrundsätze ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){: new_window} verstoßen, ohne vorherige Ankündigung inaktiviert werden. Nach dem Ermessen von IBM können einige Services wiederhergestellt werden, sofern Benutzer ihr Nutzungsverhalten entsprechend korrigieren, nachdem sie von der offensiven Aktion in Kenntnis gesetzt wurden. Andernfalls können Konten ausgesetzt oder gekündigt werden.

## Einschränkungen bei Git Repos and Issue Tracking
{: #git_limitations}

{{site.data.keyword.gitrepos}} basiert auf GitLab Community Edition und wird von IBM auf {{site.data.keyword.Bluemix_notm}} gehostet. Trotzdem sind einige wenige GitLab-Optionen nicht verfügbar:

 * Da {{site.data.keyword.deliverypipeline}} die kontinuierliche Integration und Continuous Delivery für {{site.data.keyword.Bluemix_notm}} bereitstellt, werden die Features für die kontinuierliche Integration in GitLab nicht unterstützt.
 * Die Administratorfunktionen von GitLab stehen nicht zur Verfügung, denn ihre Verwaltung erfolgt durch IBM.
 * {{site.data.keyword.gitrepos}} ist möglicherweise nicht uneingeschränkt für die behindertengerechte Bedienung geeignet.

## Benutzerinformationen zu Git Repos and Issue Tracking und Inhalt
{: #git_projects}

Es stehen drei Typen von {{site.data.keyword.gitrepos}}-Projekten zur Verfügung:

  1. Öffentliche Projekte, die für alle Websitebesucher sichtbar sind. Der Inhalt eines öffentlichen Projekts ist für jeden Benutzer sichtbar, der auf {{site.data.keyword.contdelivery_short}} zugreift, selbst wenn der betreffende Benutzer nicht zu dem Projekt eingeladen wurde.
  2. Private Projekte, die nur für ausgewählte Benutzer sichtbar sind. Weitere Informationen dazu, wie Sie Benutzern den Zugriff auf ein Projekt erteilen, finden Sie unter [Projektbenutzer ![Symbol für externen Link icon](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/help/workflow/add-user/add-user.md){: new_window}. 
  3. Interne Projekte, die für alle angemeldeten Benutzer sichtbar sind. Alle Benutzer, die über ein {{site.data.keyword.Bluemix_notm}}-Konto verfügen, können derartige Projekte anzeigen.

In den Projekteinstellungen können Sie den jeweiligen Projekttyp ändern. Weitere Informationen enthält [Vorgehensweise zum Ändern der Projektsichtbarkeit ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/help/public_access/public_access#how-to-change-project-visibility){: new_window}.

Bei Verwendung von {{site.data.keyword.gitrepos}} ist der von Ihnen zu einem Projekt beigetragene Inhalt unter allen in diesem Projekt angegebenen Bedingungen lizenziert. Wenn Sie ein Projekt erstellen, beziehen Sie eine Datei mit einer Beschreibung der Lizenz ein, die für den Inhalt gültig ist. Bei Beiträgen zu einem Projekt sind Ihr Name und die E-Mail-Adresse, die den von Ihnen vorgenommenen Commits zugeordnet ist, unter Umständen öffentlich sichtbar. Wenn Sie Commits über die Webschnittstelle von {{site.data.keyword.gitrepos}} erstellen, wird die E-Mail-Adresse verwendet, die Ihrem {{site.data.keyword.Bluemix_notm}}-Konto zugeordnet.

<!-- ###Privacy with Git Repos and Issue Tracking profiles -->

<!-- A few features of {{site.data.keyword.gitrepos}} require the use of a profile page that publicly displays information that you provide. You give IBM the following permissions: -->

  <!-- a. Make the information in your profile&mdash;such as your name, email, picture, bio, social media links, and user activity&mdash;visible to other users of the service. -->

  <!-- b. Publicly disclose your name and other public information and activities that are associated with your use of the service, or otherwise publicize the fact that you are a user of the service, without any further notice to you. -->

<!-- The email address that is associated with your profile page is derived from your {{site.data.keyword.Bluemix_notm}} account details. To modify the email address that is displayed on your profile page, modify your {{site.data.keyword.Bluemix_notm}} account. -->

<!-- ## Deprecated services
{: #deprecated_services} -->

<!--{{site.data.keyword.trackplan}} and {{site.data.keyword.deliverypipeline}} Classic, which are part of IBM Bluemix {{site.data.keyword.jazzhub_short}} (JazzHub), are being retired. For more information, see [Track & Plan Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/track-plan-retirement/){: new_window} and [Delivery Pipeline Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/delivery-pipeline-retirement/){: new_window}. -->

<!-- Starting on May 25, no new JazzHub projects can be created. Through automatic rolling upgrades, JazzHub projects will be upgraded to {{site.data.keyword.contdelivery_short}} toolchains. The JazzHub site will be removed from service in early July. For more information about the upgrade, see [Upgrading JazzHub project to Bluemix Continuous Delivery toolchains ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/devops-services/2017/4/18/upgrading-jazzhub-projects-bluemix-continuous-delivery-toolchains/){: new_window} -->
