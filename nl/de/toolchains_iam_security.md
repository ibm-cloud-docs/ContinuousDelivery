---

copyright:
  years:  2018, 2019
lastupdated: "2019-06-14"

keywords: Administrator Create, Editor Update, Update, user access

subcollection: ContinuousDelivery

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Benutzerzugriff auf Toolchains mit Identity and Access Management verwalten
{: #toolchains-iam-security}

Der Zugriff auf Toolchains in Ressourcengruppen für Benutzer in Ihrem Konto wird von {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) gesteuert. 

**Hinweise**: 

* Der Benutzerzugriff für Toolchaininstanzen und Instanzen des Service {{site.data.keyword.contdelivery_short}} wird separat verwaltet. Weitere Informationen zum Verwalten des Benutzerzugriffs auf Instanzen des Service {{site.data.keyword.contdelivery_short}} in Ressourcengruppen finden Sie im Abschnitt [Benutzerzugriff auf {{site.data.keyword.contdelivery_short}} mit Identity and Access Management verwalten](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security).

* Der Benutzerzugriff für Toolchains in Cloud Foundry-Organisationen wird anders verwaltet als der Benutzerzugriff auf Instanzen des Service {{site.data.keyword.contdelivery_short}} in Ressourcengruppen. Weitere Informationen zum Verwalten des Benutzerzugriffs auf Toolchains in Cloud Foundry-Organisationen finden Sie im Abschnitt [Zugriff auf Toolchains in Cloud Foundry-Organisationen verwalten](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs).

Jedem Benutzer, der auf Toolchains in Ihrem Konto zugreift, muss eine Zugriffsrichtlinie mit einer definierten IAM-Benutzerrolle zugeordnet werden. Diese Richtlinie bestimmt, welche Aktionen der Benutzer im Kontext des ausgewählten Service oder der ausgewählten Instanz ausführen kann. Die zulässigen Aktionen werden durch den {{site.data.keyword.Bluemix_notm}}-Service angepasst und als Operationen definiert, die für den Service ausgeführt werden dürfen. Die Aktionen werden dann IAM-Benutzerrollen zugeordnet.

Richtlinien ermöglichen den Zugriff auf verschiedenen Ebenen; dazu gehören die folgenden: 

* Zugriff auf alle Instanzen des Service in Ihrem Konto
* Zugriff auf eine einzelne Serviceinstanz in Ihrem Konto
* Zugriff auf eine bestimmte Ressource in einer Instanz
* Zugriff auf alle IAM-fähigen Services in Ihrem Konto

Nachdem Sie den Bereich der Zugriffsrichtlinie definiert haben, ordnen Sie eine Rolle zu. Sehen Sie sich die folgenden Tabellen an, in denen beschrieben wird, welche Aktionen die einzelnen Rollen in Toolchains ausführen können.

In der folgenden Tabelle werden Aktionen aufgeführt, die Plattformmanagementrollen zugeordnet sind. Plattformmanagementrollen ermöglichen Benutzern die Durchführung von Tasks für Serviceressourcen auf Plattformebene, beispielsweise die Zuordnung des Benutzerzugriffs für den Service, das Erstellen oder Löschen von Service-IDs, das Erstellen von Instanzen und das Binden von Instanzen an Anwendungen.

| Plattformmanagementrolle | Beschreibung der Aktionen | Beispielaktionen|
|:-----------------|:-----------------|:-----------------|
| Anzeigeberechtigter, Operator (Bediener) | Toolchains und Delivery Pipelines anzeigen. Delivery Pipelines ausführen. | <ul><li>Klicken Sie auf eine Toolchain, um die zugehörige Übersichtsseite zu öffnen.</li><li>Klicken Sie auf das Symbol **Stage ausführen** der Stage, in der sich Ihr Pipelinejob befindet.</li></ul> |
| Editor (Bearbeiter), Administrator | Toolchains und Delivery Pipelines erstellen, anzeigen, aktualisieren und löschen. |<ul><li>Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf **Toolchain erstellen**.</li><li>Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf die Toolchain, um die zugehörige Übersichtsseite zu öffnen.</li><li>Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf die Toolchain, die gelöscht werden soll. Klicken Sie neben **App anzeigen** auf das Menü **Weitere Aktionen**. Klicken Sie auf **Löschen**.</li></ul> |
{: caption="Tabelle 1. IAM-Benutzerrollen und -aktionen" caption-side="top"}

 Für Toolchains gibt es die folgenden Aktionen:

| Aktion | Operation im Service | Rolle
|:-----------------|:-----------------|:--------------|
| create | Eine Toolchain in einer Ressourcengruppe erstellen. | Administrator, Editor (Bearbeiter) |
| update | Eine Toolchain in einer Ressourcengruppe aktualisieren. Beispiel: Die Toolchain umbenennen. Delivery Pipelines ändern, die an Toolchains in einer Ressourcengruppe gebunden sind. | Administrator, Editor (Bearbeiter) |
| update_plan | Nicht zutreffend. | Administrator, Editor (Bearbeiter) |
| delete | Eine Toolchain aus einer Ressourcengruppe löschen. | Administrator, Editor (Bearbeiter) |
| retrieve | Die Details einer Toolchain in einer Ressourcengruppe anzeigen. Delivery Pipelines anzeigen und ausführen, die an Toolchains in einer Ressourcengruppe gebunden sind. | Administrator, Editor (Bearbeiter), Operator (Bediener), Anzeigeberechtigter |
| list-bindings | Die Toolintegrationen anzeigen, die an eine Toolchain in einer Ressourcengruppe gebunden sind. | Administrator, Editor (Bearbeiter), Anzeigeberechtigter |
| create-bindings | Eine Toolintegration einer Toolchain in einer Ressourcengruppe hinzufügen. | Administrator, Editor (Bearbeiter) |
| delete-bindings | Eine Toolintegration aus einer Toolchain in einer Ressourcengruppe entfernen. | Administrator, Editor (Bearbeiter) |
{: caption="Tabelle 2. Serviceaktionen und -operationen" caption-side="top"}

Weitere Informationen zum Zuordnen von Benutzerrollen in der Benutzerschnittstelle finden Sie im Abschnitt [IAM-Zugriff verwalten](/docs/iam?topic=iam-iammanidaccser).
