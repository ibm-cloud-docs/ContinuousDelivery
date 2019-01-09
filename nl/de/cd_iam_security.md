---

copyright:
  years:  2018
lastupdated: "2018-7-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Benutzerzugriff auf Continuous Delivery mit Identity and Access Management verwalten

Der Zugriff auf {{site.data.keyword.contdelivery_full}}-Serviceinstanzen in Ressourcengruppen für Benutzer in Ihrem Konto wird von {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) gesteuert. 

**Hinweise**: 

* Der Benutzerzugriff für {{site.data.keyword.contdelivery_short}}-Serviceinstanzen und Toolchaininstanzen wird separat verwaltet. Weitere Informationen zum Verwalten des Benutzerzugriffs auf Toolchains in Ressourcengruppen finden Sie im Abschnitt [Benutzerzugriff auf Toolchains mit Identity and Access Management verwalten](/docs/services/ContinuousDelivery/toolchains_iam_security.html){: new_window}.

* Der Benutzerzugriff für Toolchains in Cloud Foundry-Organisationen wird anders verwaltet als der Benutzerzugriff auf Toolchains in Ressourcengruppen. Weitere Informationen zum Verwalten des Benutzerzugriffs auf Toolchains in Cloud Foundry-Organisationen finden Sie im Abschnitt [Zugriff auf Toolchains in Cloud Foundry-Organisationen verwalten](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_orgs){: new_window}.

Jedem Benutzer, der auf den Service {{site.data.keyword.contdelivery_short}} in Ihrem Konto zugreift, muss eine Zugriffsrichtlinie mit einer definierten IAM-Benutzerrolle zugeordnet werden. Diese Richtlinie bestimmt, welche Aktionen der Benutzer im Kontext des ausgewählten Service oder der ausgewählten Instanz ausführen kann. Die zulässigen Aktionen werden durch den {{site.data.keyword.Bluemix_notm}}-Service angepasst und als Operationen definiert, die für den Service ausgeführt werden dürfen. Die Aktionen werden dann IAM-Benutzerrollen zugeordnet.

Richtlinien ermöglichen den Zugriff auf verschiedenen Ebenen. Einige der Optionen beinhalten Folgendes: 

* Zugriff auf alle Instanzen des Service in Ihrem Konto
* Zugriff auf eine einzelne Serviceinstanz in Ihrem Konto
* Zugriff auf eine bestimmte Ressource in einer Instanz
* Zugriff auf alle IAM-fähigen Services in Ihrem Konto

Nachdem Sie den Bereich der Zugriffsrichtlinie definiert haben, ordnen Sie eine Rolle zu. Sehen Sie sich die folgenden Tabellen an, in denen beschrieben wird, welche Aktionen die einzelnen Rollen im Service {{site.data.keyword.contdelivery_short}} ausführen können.

In der folgenden Tabelle werden Aktionen aufgeführt, die Plattformmanagementrollen zugeordnet sind. Plattformmanagementrollen ermöglichen Benutzern die Durchführung von Tasks für Serviceressourcen auf Plattformebene, beispielsweise die Zuordnung des Benutzerzugriffs für den Service, das Erstellen oder Löschen von Service-IDs, das Erstellen von Instanzen und das Binden von Instanzen an Anwendungen.

| Plattformmanagementrolle | Beschreibung der Aktionen | Beispielaktionen|
|:-----------------|:-----------------|:-----------------|
| Anzeigeberechtigter, Operator (Bediener) | Instanzen des Service {{site.data.keyword.contdelivery_short}} anzeigen. | <ul><li>Anklicken einer {{site.data.keyword.contdelivery_short}}-Serviceinstanz, um das entsprechende Dashboard zu öffnen.</li>|</ul>
| Editor (Bearbeiter), Administrator | Den Plan für den Service {{site.data.keyword.contdelivery_short}} erstellen, anzeigen, aktualisieren oder ändern und Instanzen des Service löschen. |<ul><li>Bereitstellen einer Instanz von {{site.data.keyword.contdelivery_short}} in einer Ressourcengruppe.</li><li>Löschen einer Instanz von {{site.data.keyword.contdelivery_short}} aus einer Ressourcengruppe.</li><li>Ändern eines {{site.data.keyword.contdelivery_short}}-Instanzenplans von Lite in Professional.</li></ul> |
| Administrator | Die Liste der berechtigten Benutzer aktualisieren.| <ul><li>Hinzufügen eines Benutzers zur Liste der berechtigten Benutzer.</li><li>Entfernen eines Benutzers aus der Liste der berechtigten Benutzer.</li></ul> |
{: caption="Tabelle 1. IAM-Benutzerrollen und -aktionen" caption-side="top"}

 Für {{site.data.keyword.contdelivery_short}} gibt es die folgenden Aktionen:

| Aktion | Operation im Service | Rolle
|:-----------------|:-----------------|:--------------|
| create | Eine {{site.data.keyword.contdelivery_short}}-Serviceinstanz in einer Ressourcengruppe bereitstellen. | Administrator, Editor (Bearbeiter) |
| update | Eine {{site.data.keyword.contdelivery_short}}-Serviceinstanz in einer Ressourcengruppe aktualisieren. Beispiel: Die Serviceinstanz umbenennen. | Administrator, Editor (Bearbeiter) |
| update_plan | Den Plan für die {{site.data.keyword.contdelivery_short}}-Serviceinstanz in einer Ressourcengruppe ändern. | Administrator, Editor (Bearbeiter) |
| delete | Eine {{site.data.keyword.contdelivery_short}}-Serviceinstanz aus einer Ressourcengruppe löschen. | Administrator, Editor (Bearbeiter) |
| retrieve | Eine {{site.data.keyword.contdelivery_short}}-Serviceinstanz in einer Ressourcengruppe anzeigen. | Administrator, Editor (Bearbeiter), Operator (Bediener), Anzeigeberechtigter |
| add-auth-users | Der Liste der berechtigten Benutzer auf der Registerkarte 'Verwalten' in der {{site.data.keyword.contdelivery_short}}-Serviceinstanz Einträge hinzufügen. | Administrator, Schreibberechtigter, Manager |
| remove-auth-users | Einträge aus der Liste der berechtigten Benutzer auf der Registerkarte 'Verwalten' in der {{site.data.keyword.contdelivery_short}}-Serviceinstanz entfernen. | Administrator, Schreibberechtigter, Manager |
{: caption="Tabelle 2. Serviceaktionen und -operationen" caption-side="top"}

In der folgenden Tabelle werden Aktionen aufgeführt, die Servicezugriffsrollen zugeordnet sind. Servicezugriffsrollen ermöglichen Benutzern den Zugriff auf {{site.data.keyword.contdelivery_short}} sowie das Aufrufen der {{site.data.keyword.contdelivery_short}}-API.

| Servicezugriffsrolle | Beschreibung der Aktionen | Beispielaktionen|
|:-----------------|:-----------------|:-----------------|
| Schreibberechtigter, Manager | In der Liste der berechtigten Benutzer auf der Registerkarte 'Verwalten' in einer {{site.data.keyword.contdelivery_short}}-Serviceinstanz Benutzer hinzufügen und entfernen. | <ul><li>Hinzufügen eines berechtigten Benutzers.</li><li>Entfernen eines berechtigten Benutzers.</li></ul>|
{: caption="Tabelle 3. IAM-Servicezugriffsrollen und -aktionen" caption-side="top"}

Weitere Informationen zum Zuordnen von Benutzerrollen in der Benutzerschnittstelle finden Sie im Abschnitt [IAM-Zugriff verwalten](/docs/iam/mngiam.html#iammanidaccser).

<!--This link is not live in production yet. Use https://console.bluemix.net/docs/iam/iamusermanage.html#iamusermanage until the link above is available in production.-->
