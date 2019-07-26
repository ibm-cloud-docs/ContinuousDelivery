---

copyright:
  years: 2015, 2019

lastupdated: "2019-06-18"

keywords: set of tool integrations, collective power of a toolchain, IBM Cloud

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# Toolchains erstellen
{: #toolchains_getting_started}

Eine *Toolchain* ist eine Gruppe von Toolintegrationen, die Entwicklungs-, Bereitstellungs- und Systemtasks unterstützen. Die kollektive Leistung einer Toolchain ist höher als die Summe der zugehörigen einzelnen Toolintegrationen.
{: shortdesc}

Offene Toolchains stehen in den öffentlichen und den dedizierten Umgebungen von {{site.data.keyword.Bluemix}} (Public bzw. Dedicated) zur Verfügung. Sie können eine Toolchain auf zwei Arten erstellen: Entweder Sie verwenden eine Vorlage zum Erstellen einer Toolchain oder Sie erstellen eine Toolchain aus einer App.

Jede Toolchain ist einer bestimmten Ressourcengruppe oder Organisation zugeordnet. Wenn eine Toolchain einer Ressourcengruppe zugeordnet ist, kann jeder Benutzer mit einer IAM-Berechtigung (Identity and Access Management) als Anzeigeberechtigter für die Toolchain-Ressource oder die Ressourcengruppe, in der sie enthalten ist, auf die Toolchain zugreifen. Wenn die Toolchain einer Organisation zugeordnet ist, kann jeder Benutzer, der Mitglied dieser Organisation ist, der Zugriffssteuerungsliste für jede der ihr zugeordneten Toolchains hinzugefügt werden. Weitere Informationen zur Zugriffssteuerung für Toolchains in Cloud Foundry-Organisationen finden Sie im Abschnitt [Zugriff auf Toolchains in Cloud Foundry-Organisationen verwalten](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs). Weitere Informationen zur Zugriffssteuerung für Toolchains in Ressourcengruppen finden Sie im Abschnitt [Zugriff auf Toolchains in Ressourcengruppen verwalten](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_resource_groups).

##Toolchain aus einer Vorlage erstellen   
{: #creating_a_toolchain_from_a_template}

Sie können eine Vorlage als Ausgangspunkt zum [Erstellen einer Toolchain](https://cloud.ibm.com/devops/create){:external} verwenden, die eine bestimmte Gruppe von Toolintegrationen enthält. Weitere Informationen zur Verwendung von Vorlagen finden Sie in [IBM Cloud Garage Method](https://www.ibm.com/cloud/garage/category/tools){:external}.

1. Wenn Sie {{site.data.keyword.Bluemix_notm}} Public verwenden, melden Sie sich bei [{{site.data.keyword.Bluemix_notm}}](http://cloud.ibm.com){:external} an.
1. Wenn Sie {{site.data.keyword.Bluemix_notm}} Dedicated verwenden, melden Sie sich bei Ihrer dedizierten Umgebung auf {{site.data.keyword.Bluemix_notm}} an.
1. Klicken Sie im Menü in der {{site.data.keyword.Bluemix_notm}}-Menüleiste auf **DevOps**.
1. Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf **Toolchain erstellen**.
1. Klicken Sie auf der Seite **Toolchain erstellen** auf eine Toolchain-Vorlage.
1. Überprüfen Sie das Diagramm der Toolchain, die Sie gerade erstellen. In dem Diagramm wird jede Toolintegration in ihrer aktuellen Lebenszyklusphase in der Toolchain angezeigt.

 Für einige der Toolchain-Vorlagen sind mehrere Instanzen einer Toolintegration vorhanden. Die Vorlage für die Microservice-Toolchain unter {{site.data.keyword.Bluemix_notm}} Public enthält beispielsweise drei Instanzen von GitHub und drei Instanzen von Delivery Pipeline - jeweils eine Instanz für jeden der drei Microservices.
 {: tip}

 Das Diagramm in der folgenden Abbildung ist ein Beispiel. Wenn Sie eine Toolchain erstellen, zeigt das Diagramm jede Toolintegration an, die Teil der Toolchain ist.
![Toolchain-Diagramm](images/toolchain_diagram2.png)

1. Überprüfen Sie die Standardinformationen für die Toolchain-Einstellungen:

 * Der Name der Toolchain macht sie in {{site.data.keyword.Bluemix_notm}} identifizierbar. Wenn Sie einen anderen Namen verwenden möchten, ändern Sie den Namen der Toolchain.
 * Die Region, in der die Toolchain erstellt wird. Wenn Sie eine andere Region verwenden möchten, wählen Sie eine Region aus der Liste verfügbarer Regionen aus.
 * Die Ressourcengruppe oder Organisation, in der die Toolchain erstellt wird. Klicken Sie auf den Link, um zwischen der Auswahl von Ressourcengruppen und Organisationen zu wechseln. Wenn Sie eine andere Ressourcengruppe oder Organisation verwenden möchten, wählen Sie sie aus der Liste verfügbarer Ressourcengruppen bzw. Organisationen aus.
 
   Ressourcengruppen sind in den Regionen 'Vereinigte Staaten (Süden)', 'Vereinigte Staaten (Osten)', 'Vereinigtes Königreich', 'Deutschland' und 'Tokio' verfügbar. Cloud Foundry-Organisationen werden in den Regionen 'Vereinigten Staaten (Süden)', 'Vereinigtes Königreich' und 'Deutschland' unterstützt.
   {: important}

1. Wählen Sie im Abschnitt mit den Toolintegrationen jede Toolintegration aus, die Sie für Ihre Toolchain konfigurieren möchten. Einige Toolintegrationen erfordern keine Konfiguration. Informationen zum Konfigurieren der Toolintegrationen finden Sie unter [Toolintegrationen konfigurieren](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations).
1. Klicken Sie auf **Erstellen**. Zum Einrichten Ihrer Toolchain werden mehrere verschiedene Schritte automatisch ausgeführt. Die Toolintegrationen, die eingerichtet werden, unterscheiden sich voneinander, je nachdem, welche Toolchain-Vorlage Sie ausgewählt haben und ob Sie {{site.data.keyword.Bluemix_notm}} Public oder {{site.data.keyword.Bluemix_notm}} Dedicated verwenden. Wenn Sie eine Microservice-Toolchain unter {{site.data.keyword.Bluemix_notm}} Public erstellen, werden zum Beispiel die folgenden Schritte ausgeführt:

 * Die Toolchain wird erstellt.
 * Wenn Sie Delivery Pipeline konfiguriert haben, werden die Pipelines erstellt und aktiviert.
 * Wenn Sie Sauce Labs konfiguriert haben, wird die Toolchain so eingerichtet, dass Sauce Labs-Testjobs zu den Pipelines hinzugefügt werden.
 * Wenn Sie PagerDuty konfiguriert haben, wird die Toolchain so eingerichtet, dass sie Alertbenachrichtigungen an den von Ihnen angegebenen PagerDuty-Service sendet.
 * Wenn Sie Slack konfiguriert haben, wird die Toolchain so konfiguriert, dass sie Benachrichtigungen zum Bereitstellungsstatus an den von Ihnen angegebenen Kanal sendet.
 * Wenn Sie eine Quellcode-Toolintegration wie GitHub konfiguriert haben, wird das GitHub-Beispielrepository in Ihr GitHub-Konto geklont.


##Toolchain aus einer App erstellen
{: #creating_a_toolchain_from_an_app}

Sie können eine Toolchain aus Ihrer App erstellen. Die Toolchain kann kontinuierliche Entwicklung, Bereitstellung, Überwachung und mehr unterstützen und sie ist Ihrer App zugeordnet. Jede App kann einer Toolchain zugeordnet sein. Wenn Sie Änderungen per Push-Operation an das GitHub- oder das {{site.data.keyword.ghe_short}}-Repository der Toolchain übertragen, erstellt die Pipeline automatisch Builds der App und stellt die App bereit.

Wenn Sie Ihre App unter Verwendung Ihres eigenen Code-Repositorys erstellt haben, klicken Sie auf der Detailseite Ihrer App auf **Continuous Delivery konfigurieren**. Führen Sie anschließend die Schritte aus, die im Abschnitt zur [Erstellung von Apps aus Ihrem eigenen Code-Repository](/docs/apps?topic=creating-apps-tutorial-byoc#tutorial-byoc) beschrieben sind.
{: note}

1. Wenn Sie Ihre App unter Verwendung eines Starter-Kits erstellt haben, klicken Sie auf der Detailseite Ihrer App auf **Continuous Delivery konfigurieren**. Wählen Sie anschließend ein Bereitstellungsziel aus. Wenn Sie {{site.data.keyword.Bluemix_notm}} Public verwenden, wird Ihre App für die kontinuierliche Bereitstellung aus einem neuen GitHub-Repository konfiguriert, das den Startcode für die App enthält. Wenn Sie {{site.data.keyword.Bluemix_notm}} Dedicated verwenden, wird Ihre App für die kontinuierliche Bereitstellung aus einem neuen GitHub- oder {{site.data.keyword.ghe_short}}-Repository konfiguriert, das den Startcode für die App enthält.
1. Überprüfen Sie auf der Seite zum Konfigurieren der Toolchain das Diagramm der Toolchain, die Sie gerade erstellen. In dem Diagramm wird jede Toolintegration in ihrer aktuellen Lebenszyklusphase in der Toolchain angezeigt.
1. Überprüfen Sie die Standardinformationen für die Toolchain-Einstellungen. Der Name der Toolchain macht sie in {{site.data.keyword.Bluemix_notm}} identifizierbar. Wenn Sie einen anderen Namen verwenden möchten, ändern Sie den Namen der Toolchain.
1. Wählen Sie im Abschnitt mit den Toolintegrationen jede Toolintegration aus, die Sie für Ihre Toolchain konfigurieren möchten. Einige Toolintegrationen erfordern keine Konfiguration. Informationen zum Konfigurieren der Toolintegrationen finden Sie unter [Toolintegrationen konfigurieren](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations).
1. Klicken Sie auf **Erstellen**. Zum Einrichten Ihrer Toolchain werden mehrere verschiedene Schritte automatisch ausgeführt. Die Toolintegrationen, die eingerichtet werden, unterscheiden sich voneinander, je nachdem, ob Sie Toolchains unter {{site.data.keyword.Bluemix_notm}} Public oder unter {{site.data.keyword.Bluemix_notm}} Dedicated verwenden. Wenn Sie eine Toolchain aus einer App unter {{site.data.keyword.Bluemix_notm}} Public erstellen, werden zum Beispiel die folgenden Schritte ausgeführt:

 * Die Toolchain wird erstellt.
 * Wenn Sie Delivery Pipeline konfiguriert haben, werden die Pipelines erstellt und aktiviert.
 * Wenn Sie GitHub konfiguriert haben, wird das GitHub-Beispielrepository in Ihr GitHub-Konto geklont.


##Toolchain anzeigen
{: #viewing_a_toolchain}

Nachdem Sie die Toolchain und die zugehörigen Toolintegrationen konfiguriert haben, können Sie eine grafische Darstellung der Toolchain anzeigen.

Sie können eine Toolchain über eine App anzeigen, indem Sie auf der Detailseite der App auf **Toolchain anzeigen ** klicken.
{: tip}

1. Wählen Sie im DevOps-Dashboard auf der Seite **Toolchains** eine **RESSOURCENGRUPPE** oder **CLOUD FOUNDRY-ORGANISATION** aus. Alle Toolchains, die in der ausgewählten Ressourcengruppe bzw. Cloud Foundry-Organisation enthalten sind, werden angezeigt. Klicken Sie auf die Toolchain, die Sie anzeigen möchten, um die zugehörige Übersichtsseite zu öffnen. Alternativ können Sie auf der Übersichtsseite der App auf der Karte für Continuous Delivery auf **Toolchain anzeigen** klicken. Klicken Sie anschließend auf **Übersicht**.
2. Um auf eine Toolintegration in Ihrer Toolchain zuzugreifen, klicken Sie auf das entsprechende Tool.

 Wenn Sie über mehr als ein GitHub-, {{site.data.keyword.ghe_short}}- oder Git-Repository verfügen, sind möglicherweise mehrere Karten für dieselbe Toolintegration vorhanden, da jedes Repository durch eine eigene Karte dargestellt wird. Wenn Sie über mehrere Pipelines verfügen, sind gegebenenfalls mehrere Karten für dieselbe Toolintegration vorhanden, da jede Pipeline durch ihre eigene Karte dargestellt wird. Wenn Sie eine Microservice-Toolchain erstellen, besitzt jeder dieser drei Microservices sein eigenes GitHub-, {{site.data.keyword.ghe_short}}- oder Git-Repository und seine eigene Pipeline.
 {: tip}

## Relevantes Lernprogramm: Toolchains verwenden
{: #toolchain_tutorials}

Informieren Sie sich in einem dieser Lernprogramme in [IBM&reg; Cloud Garage Method](https://www.ibm.com/cloud/garage){:external}:

  * [Erste Toolchain mithilfe der Toolchain zum Entwickeln einer Cloud Foundry-App erstellen und verwenden](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:external}.

  * [Einer App eine Toolchain hinzufügen](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:external}.

  * [Toolchain zum Entwickeln und Testen von Microservices auf Cloud Foundry verwenden](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:external}.
