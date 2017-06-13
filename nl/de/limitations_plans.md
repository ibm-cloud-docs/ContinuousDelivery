---

copyright:
  years: 2016, 2017
lastupdated: "2017-5-17"
---
<!-- Copyright info at top of file: REQUIRED
    The copyright info is YAML content that must occur at the top of the MD file, before attributes are listed.
    It must be surrounded by 3 dashes.
    The value "years" can contain just one year or a two years separated by a comma. (years: 2014, 2016)
    Indentation as per the previous template must be preserved.
-->

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Einschränkungen beim Plan und bei der Nutzung
{: #deliverypipeline_plans}
{: #free_deprecation}

Die Verwendung von {{site.data.keyword.contdelivery_full}} ist auf das Erstellen, Bereitstellen, Testen und auf den laufenden Betrieb von Anwendungen auf der {{site.data.keyword.Bluemix_notm}}-Plattform oder anderen kompatiblen Platform-as-a-Service- (PaaS) oder Infrastructure-as-a-Service-Angeboten (IaaS) beschränkt.

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
  2. Private Projekte, die nur für ausgewählte Benutzer sichtbar sind. Detaillierte Informationen dazu, wie Sie Benutzern den Zugriff auf ein Projekt erteilen, finden Sie in [Projektbenutzer ![Symbol für externen Link icon](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/help/workflow/add-user/add-user.md){: new_window}.
  3. Interne Projekte, die für alle angemeldeten Benutzer sichtbar sind. Alle Benutzer, die über ein {{site.data.keyword.Bluemix_notm}}-Konto verfügen, können derartige Projekte anzeigen.

In den Projekteinstellungen können Sie den jeweiligen Projekttyp ändern. Weitere Informationen enthält [Vorgehensweise zum Ändern der Projektsichtbarkeit ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://git.ng.bluemix.net/help/public_access/public_access#how-to-change-project-visibility){: new_window}.

Bei Verwendung von {{site.data.keyword.gitrepos}} ist der von Ihnen zu einem Projekt beigetragene Inhalt unter allen in diesem Projekt angegebenen Bedingungen lizenziert. Wenn Sie ein Projekt erstellen, beziehen Sie eine Datei mit einer Beschreibung der Lizenz ein, die für den Inhalt gültig ist. Bei Beiträgen zu einem Projekt sind Ihr Name und die E-Mail-Adresse, die den von Ihnen vorgenommenen Festschreibungen zugeordnet ist, unter Umständen öffentlich sichtbar. Wenn Sie Festschreibungen über die Webschnittstelle von {{site.data.keyword.gitrepos}} erstellen, wird die E-Mail-Adresse verwendet, die Ihrem {{site.data.keyword.Bluemix_notm}}-Konto zugeordnet.

<!-- ###Privacy with Git Repos and Issue Tracking profiles -->

<!-- A few features of {{site.data.keyword.gitrepos}} require the use of a profile page that publicly displays information that you provide. You give IBM the following permissions: -->

  <!-- a. Make the information in your profile&mdash;such as your name, email, picture, bio, social media links, and user activity&mdash;visible to other users of the service. -->

  <!-- b. Publicly disclose your name and other public information and activities that are associated with your use of the service, or otherwise publicize the fact that you are a user of the service, without any further notice to you. -->

<!-- The email address that is associated with your profile page is derived from your {{site.data.keyword.Bluemix_notm}} account details. To modify the email address that is displayed on your profile page, modify your {{site.data.keyword.Bluemix_notm}} account. -->

## Veraltete Services
{: #deprecated_services}

{{site.data.keyword.trackplan}} und {{site.data.keyword.deliverypipeline}} Classic, die jeweils ein Bestandteil von IBM Bluemix {{site.data.keyword.jazzhub_short}} (JazzHub) sind, werden zurückgezogen. Weitere Informationen finden Sie in [Zurückziehung von Track & Plan ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/blogs/bluemix/2017/04/track-plan-retirement/){: new_window} und [Zurückziehung von Delivery Pipeline ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/blogs/bluemix/2017/04/delivery-pipeline-retirement/){: new_window}.

Ab dem 25. Mai können keine neuen JazzHub-Projekte mehr erstellt werden. Anhand automatischer schrittweiser Upgrades wird für JazzHub-Projekte ein Upgrade auf {{site.data.keyword.contdelivery_short}}-Toolchains durchgeführt. Die JazzHub-Site wird Anfang Juli außer Betrieb genommen. Weitere Informationen zum Upgrade erhalten Sie in [Upgrade eines JazzHub-Projekts auf Bluemix Continuous Delivery-Toolchains durchführen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/devops-services/2017/4/18/upgrading-jazzhub-projects-bluemix-continuous-delivery-toolchains/){: new_window}.
