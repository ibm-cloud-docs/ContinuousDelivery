---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-27"

keywords: users of a service instance, a-service, Git Repos

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}


# Einschränkungen beim Plan und bei der Nutzung
{: #limitations_usage}

Die Verwendung von {{site.data.keyword.contdelivery_full}} ist auf das Erstellen, Bereitstellen, Testen und auf den laufenden Betrieb von Anwendungen auf der {{site.data.keyword.Bluemix_notm}}-Plattform oder anderen kompatiblen Platform-as-a-Service- (PaaS) oder Infrastructure-as-a-Service-Angeboten (IaaS) beschränkt.

## Geltungsbereich einer Serviceinstanz
{: #service_scope}

Sie müssen über eine {{site.data.keyword.contdelivery_short}}-[Serviceinstanz](https://cloud.ibm.com/catalog/services/continuous-delivery){:external} verfügen, um DevOps-Toolchains zu erstellen und zu verwenden. Eine Serviceinstanz kann entweder zu einer {{site.data.keyword.Bluemix_notm}}-IAM-[Ressourcengruppe](/docs/services/resources?topic=resources-rgs) (IAM - Identity and Access Management) oder einer {{site.data.keyword.Bluemix_notm}}-Organisation gehören.

Sie können *neue* Instanzen des {{site.data.keyword.contdelivery_short}}-Service nur in Ressourcengruppen erstellen. Die Migration von Toolchains von Organisationen zu Ressourcengruppen wird derzeit nicht unterstützt. Wenn Ihnen ein {{site.data.keyword.contdelivery_short}}-Service für eine Organisation, die Toolchains enthält, fehlt, können Sie entweder die Toolchains erneut in einer Ressourcengruppe erstellen oder den [IBM Support](https://cloud.ibm.com/unifiedsupport){:external} um Hilfe bitten.

Sie können pro Konto nur einen einzigen Lite-Service haben. Es wird empfohlen, den Professional-Plan zu verwenden, wenn Sie mit Toolchains in mehreren Organisationen oder Ressourcengruppen oder in mehreren Regionen arbeiten möchten.
{: tip}


## Berechtigte Benutzer
{: #authorized_users}

{{site.data.keyword.contdelivery_short}}-[Servicepläne](https://cloud.ibm.com/catalog/services/continuous-delivery){:external} werden anhand der Anzahl der berechtigten Benutzer einer Serviceinstanz definiert und berechnet. Jeder Benutzer, der etwas zu einer Leistung beiträgt, zählt als berechtigter Benutzer, einschließlich:

 * Benutzer, die mit Problemen, Issue-Boards, Quellcodes oder anderen Artefakten in einem {{site.data.keyword.gitrepos}}-Repository arbeiten.
 * Benutzer, die eine Delivery Pipeline bearbeiten, auslösen (entweder direkt in der Benutzeroberfläche oder indirekt durch ein Commit an das Repository) oder deren Status anzeigen.
 * Benutzer, die mit der Eclipse Orion-{{site.data.keyword.webide}} arbeiten.
 
Für den Lite-Plan gibt es Einschränkungen. Weitere Informationen zum Lite- und zum Professional-Plan finden Sie im [Servicekatalog](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}.
{: tip}
 
### Wie werden Benutzer für Instanzen von {{site.data.keyword.contdelivery_short}} in Ressourcengruppen gezählt?

Berechtigte Benutzer werden für jede Serviceinstanz gezählt und verwaltet, indem die Liste der berechtigten Benutzer für die Rechnungsstellung und die Lite-Plan-Grenzwerte berücksichtigt wird. {{site.data.keyword.contdelivery_short}}-Servicebenutzer werden automatisch dieser Liste hinzugefügt. Sie können verhindern, dass Benutzer auf Toolchains zugreifen und automatisch einer {{site.data.keyword.contdelivery_short}}-Serviceinstanz hinzugefügt werden. Weitere Informationen zur Verwendung von IAM zum Entfernen des Benutzerzugriffs aus der Ressourcengruppe, die die Toolchain enthält (oder aus der Toolchain selbst), finden Sie unter [Benutzerzugriff auf {{site.data.keyword.contdelivery_short}} mit Identity and Access Management verwalten](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security). 

Die Methode, die Sie zum Organisieren von Toolchains innerhalb von Ressourcengruppen verwenden, wirkt sich direkt auf den Benutzerzugriff und die Rechnungsstellung aus. Wenn ein Benutzer Toolchains in mehreren Ressourcengruppen verwendet, werden sie für jeden Service in diesen Ressourcengruppen gezählt und in Rechnung gestellt.
{: tip}

Sie können die Liste der berechtigten Benutzer auf der Registerkarte **Verwalten** in der {{site.data.keyword.contdelivery_short}}-Serviceinstanz verwalten.

1. Wechseln Sie in die [Ressourcenliste](https://cloud.ibm.com/resources){:external} für Ihr {{site.data.keyword.Bluemix_notm}}-Konto.
2. Geben Sie in der Spalte **Name** im Filtertextfeld **Continuous Delivery** ein, um Ihre vorhandenen Services anzuzeigen.
3. Klicken Sie für jeden Service auf den Hyperlink in der Spalte **Name**.
4. Auf der Registerkarte **Verwalten** können Sie nach Bedarf Benutzer in der Liste der berechtigten Benutzer anzeigen, hinzufügen oder entfernen.

Benutzer werden automatisch hinzugefügt oder erneut hinzugefügt, wenn sie den {{site.data.keyword.contdelivery_short}}-Service verwenden.
{: tip}

### Wie werden Benutzer für Instanzen von {{site.data.keyword.contdelivery_short}} in Organisationen gezählt?

Berechtigte Benutzer werden gezählt, indem alle Benutzer in der {{site.data.keyword.Bluemix_notm}}-Organisation, die den {{site.data.keyword.contdelivery_short}}-Service enthält, berücksichtigt werden. Weitere Informationen zu Organisationen und Bereichen finden Sie unter [Organisationen und Bereiche erstellen](/docs/cloud-foundry?topic=cloud-foundry-create_orgs).

Um die Liste der Benutzer in Ihrer Organisation in einer {{site.data.keyword.Bluemix_notm}} Public-Umgebung anzuzeigen, klicken Sie in der Menüleiste auf **Verwalten > Konto**. Klicken Sie dann auf **Cloud Foundry-Organisationen**.

### Wie können Sie Rechnungsstellungs- und Nutzungsinformationen anzeigen?

Sie können alle Instanzen des {{site.data.keyword.contdelivery_short}}-Service in Ihrem Konto und die Anzahl der Benutzer und Pipelineausführungen anzeigen, die für jede Instanz in einer {{site.data.keyword.Bluemix_notm}} Public-Umgebung gemeldet werden.

1. Klicken Sie in der Menüleiste auf **Verwalten > Abrechnung und Nutzung**.
2. Klicken Sie auf **Nutzung**.
3. Klicken Sie im Abschnitt **Services** für den {{site.data.keyword.contdelivery_short}}-Service auf **Pläne anzeigen**.
4. Klicken Sie für den Plan, zu dem Sie Informationen anzeigen möchten, auf **Details anzeigen**.
5. Klicken Sie für die Instanz von {{site.data.keyword.contdelivery_short}}, zu der Sie Nutzungsinformationen anzeigen möchten, auf **Instanzdetails anzeigen**.

Die Metrik `AUTHORIZED_USERS_PER_MONTH` wird basierend auf einem täglich errechneten monatlichen Durchschnitt von Benutzern berechnet.
{: tip}

### Was passiert, wenn Sie die Grenzwerte Ihres Serviceplans überschreiten?

Der Lite-Serviceplan hat andere Einschränkungen, z. B. die Anzahl der ausführbaren Delivery Pipeline-Jobs oder die Speicherbelegung. Weitere Informationen zur Planbeschreibung finden Sie im [Servicekatalog](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}. Wenn eine der Planbeschränkungen in einem Abrechnungszeitraum überschritten wird, wird der Service ausgesetzt. Beispiel: Aufträge für die Delivery Pipeline werden für den Rest des Abrechnungszeitraums nicht ausgeführt.

## Delivery Pipeline-Verwendung
{: #pipeline_usage}

Das akzeptable Nutzungsverhalten umfasst die folgenden Verhaltensweisen, ist aber nicht auf diese beschränkt:

* Die Kompilierung und Assemblierung von Artefakten für unterstützte Programmiersprachen.
* Die automatisierte Bereitstellung von Anwendungsartefakten, Konfigurationen und unterstützenden Ressourcen oder Services.
* Das Testen, Validieren oder sonstiges durch Entwicklungsereignisse generiertes Verhalten, das als Ergebnis eines Entwicklungsprozesses ausgelöst wird.

Das nicht zulässige Nutzungsverhalten umfasst die folgenden Verhaltensweisen, ist aber nicht auf diese beschränkt:

* Die Verwendung von Pipelinejobs oder Workern für allgemeines Computerverhalten, wie Bitcoin-Mining, verteilte Denial-of-Service-Attacken (DoS) und böswilliges oder anstößiges Verhalten gegenüber anderen Kunden oder Benutzern innerhalb der {{site.data.keyword.Bluemix_notm}}-Plattform oder gegenüber allgemeinen Internetbenutzern.
* Die Verwendung im normalen Entwicklungsprozess für Sites oder Services, die zum Hass anstacheln (Hassreden), oder andere Aktivitäten, die gegen die IBM Geschäftsgrundsätze verstoßen.
* Die Verwendung ereignisgenerierten Verhaltens für böswillige Manipulationen oder Angriffe gegen {{site.data.keyword.Bluemix_notm}} oder andere Sites.

Nach dem Ermessen von IBM können Benutzer, die gegen das akzeptable Nutzungsverhalten der {{site.data.keyword.contdelivery_short}}-Services oder gegen die [IBM Geschäftsgrundsätze](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){:external} verstoßen, ohne vorherige Ankündigung inaktiviert werden. Nach dem Ermessen von IBM können einige Services wiederhergestellt werden, sofern Benutzer ihr Nutzungsverhalten entsprechend korrigieren, nachdem sie von der offensiven Aktion in Kenntnis gesetzt wurden. Andernfalls können Konten ausgesetzt oder gekündigt werden.

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
  2. Private Projekte, die nur für ausgewählte Benutzer sichtbar sind. Weitere Informationen dazu, wie Benutzern Zugriff auf ein Projekt erteilt wird, finden Sie unter [Projektbenutzer](https://us-south.git.cloud.ibm.com/help/user/project/members/index.md){:external}.
  3. Interne Projekte, die für alle angemeldeten Benutzer sichtbar sind. Alle Benutzer, die über ein {{site.data.keyword.Bluemix_notm}}-Konto verfügen, können diese Projekte anzeigen.

In den Projekteinstellungen können Sie den jeweiligen Projekttyp ändern. Weitere Informationen zu den Projekteinstellungen finden Sie unter [Vorgehensweise zum Ändern der Projekttransparenz](https://us-south.git.cloud.ibm.com/help/public_access/public_access#how-to-change-project-visibility){:external}.

Bei Verwendung von {{site.data.keyword.gitrepos}} ist der von Ihnen zu einem Projekt beigetragene Inhalt unter allen in diesem Projekt angegebenen Bedingungen lizenziert. Wenn Sie ein Projekt erstellen, beziehen Sie eine Datei mit einer Beschreibung der Lizenz ein, die für den Inhalt gültig ist. Bei Beiträgen zu einem Projekt sind Ihr Name und die E-Mail-Adresse, die den von Ihnen vorgenommenen Commits zugeordnet ist, unter Umständen öffentlich sichtbar. Wenn Sie Commits über die Webschnittstelle von {{site.data.keyword.gitrepos}} erstellen, wird die E-Mail-Adresse verwendet, die Ihrem {{site.data.keyword.Bluemix_notm}}-Konto zugeordnet.
