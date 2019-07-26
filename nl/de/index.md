---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-18"

keywords: IBM Cloud Continuous Delivery, tool integration, toolchain template

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


# Lernprogramm zur Einführung
{: #getting-started}

Nutzen Sie DevOps-Verfahren durch Verwendung von {{site.data.keyword.contdelivery_full}}, das offene Toolchains zur Automatisierung der Erstellung und Bereitstellung von Anwendungen enthält. Beginnen Sie mit der Erstellung einer einfachen Toolchain für die Bereitstellung, die Entwicklungs-, Bereitstellungs- und Operationstasks unterstützt. 
{: shortdesc}


Wenn Sie bereits über eine Instanz von {{site.data.keyword.contdelivery_short}} verfügen, können Sie [eine Toolchain erstellen](https://cloud.ibm.com/devops/create){:external} oder [vorhandene Toolchains anzeigen](https://cloud.ibm.com/devops/toolchains){:external}.
{: tip}


##Voraussetzungen
{: #cd_prereqs}

Bevor Sie eine Continuous Delivery-Toolchain aus einer Vorlage erstellen können, müssen Sie eine Instanz von {{site.data.keyword.contdelivery_short}} erstellen, indem Sie sie aus dem {{site.data.keyword.Bluemix_notm}}-Katalog auswählen. Die Toolchain integriert Tools für Planung, Entwicklung und Bereitstellung von Pipelines sowie für die Verwaltung Ihrer Anwendungen. Tools können jederzeit in eine Toolchain eingefügt oder daraus entfernt werden. Wenn Sie bereits Toolchains haben, können Sie [vorhandene Toolchains anzeigen](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#viewing_a_toolchain). Weitere Informationen zum Arbeiten mit Toolchains enthält [Toolchains verwenden](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using).


##Schritt 1: Eine Toolchain-Vorlage auswählen
{: #select_a_toolchain_template}

Wenn Sie schnell die für Ihre spezifischen Anforderungen geeignete Toolchain-Vorlage finden möchten, wählen Sie die entsprechenden Kontrollkästchen aus, um nach Bereitstellungsziel und Tools zu filtern.
{: tip}

1. Klicken Sie auf der Seite **Toolchain erstellen** auf eine [Toolchain-Vorlage](https://cloud.ibm.com/devops/create){:external}.
1. Überprüfen Sie das Diagramm der Toolchain, die Sie gerade erstellen. In dem Diagramm wird jede Toolintegration in ihrer aktuellen Lebenszyklusphase in der Toolchain angezeigt.

 Für einige der Toolchain-Vorlagen sind mehrere Instanzen einer Toolintegration vorhanden. Die Vorlage für die Microservice-Toolchain unter {{site.data.keyword.Bluemix_notm}} Public enthält beispielsweise drei Instanzen von GitHub und drei Instanzen von Delivery Pipeline - jeweils eine Instanz für jeden der drei Microservices.
 {: tip}

 Das Diagramm in der folgenden Abbildung ist ein Beispiel. Wenn Sie eine Toolchain erstellen, zeigt das Diagramm jede Toolintegration an, die Teil der Toolchain ist.
 ![Toolchain-Diagramm](images/toolchain_diagram2.png)
 
##Schritt 2: Toolchain erstellen 
{: #create_a_toolchain}
 
1. Überprüfen Sie die Standardinformationen für die Toolchain-Einstellungen:

 * Der Name der Toolchain macht sie in {{site.data.keyword.Bluemix_notm}} identifizierbar. Wenn Sie einen anderen Namen verwenden möchten, ändern Sie den Namen der Toolchain.
 * Die Region, in der die Toolchain erstellt wird. Wenn Sie eine andere Region verwenden möchten, wählen Sie eine Region aus der Liste verfügbarer Regionen aus.
 * Die Ressourcengruppe oder Organisation, in der die Toolchain erstellt wird. Klicken Sie auf den Link, um zwischen der Auswahl von Ressourcengruppen und Organisationen zu wechseln. Wenn Sie eine andere Ressourcengruppe oder Organisation verwenden möchten, wählen Sie sie aus der Liste verfügbarer Ressourcengruppen bzw. Organisationen aus.
 
   Ressourcengruppen sind in den Regionen 'Vereinigte Staaten (Süden)', 'Vereinigte Staaten (Osten)', 'Vereinigtes Königreich', 'Deutschland' und 'Tokio' verfügbar. Cloud Foundry-Organisationen werden in den Regionen 'Vereinigten Staaten (Süden)', 'Vereinigtes Königreich' und 'Deutschland' unterstützt.
   {: important}
 
1. Wählen Sie im Abschnitt mit den Toolintegrationen jede Toolintegration aus, die Sie für Ihre Toolchain konfigurieren möchten. Einige Toolintegrationen erfordern keine Konfiguration. Informationen zum Konfigurieren der Toolintegrationen finden Sie unter [Toolintegrationen konfigurieren](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations).
1. Klicken Sie auf **Erstellen**. Zum Einrichten Ihrer Toolchain werden mehrere verschiedene Schritte automatisch ausgeführt. Die Toolintegrationen, die eingerichtet werden, unterscheiden sich voneinander, je nachdem, welche Toolchain-Vorlage Sie ausgewählt haben und ob Sie {{site.data.keyword.Bluemix_notm}} Public oder {{site.data.keyword.Bluemix_notm}} Dedicated verwenden. Wenn Sie eine Microservice-Toolchain unter {{site.data.keyword.Bluemix_notm}} Public erstellen, werden zum Beispiel die folgenden Schritte ausgeführt:

 * Die Toolchain wird erstellt.
 * Wenn Sie Delivery Pipeline konfiguriert haben, werden die Pipelines erstellt und ausgeführt.
 * Wenn Sie Sauce Labs konfiguriert haben, wird die Toolchain so eingerichtet, dass Sauce Labs-Testjobs zu den Pipelines hinzugefügt werden.
 * Wenn Sie PagerDuty konfiguriert haben, wird die Toolchain so eingerichtet, dass sie Alertbenachrichtigungen an den von Ihnen angegebenen PagerDuty-Service sendet.
 * Wenn Sie Slack konfiguriert haben, wird die Toolchain so konfiguriert, dass sie Benachrichtigungen zum Bereitstellungsstatus an den von Ihnen angegebenen Kanal sendet.
 * Wenn Sie eine Quellcode-Toolintegration wie GitHub konfiguriert haben, wird das GitHub-Beispielrepository in Ihr GitHub-Konto geklont.

##Nächste Schritte
{: #next_steps}

Informieren Sie sich in einem dieser Lernprogramme in [IBM&reg; Cloud Garage Method](https://www.ibm.com/cloud/garage){:external}:

  * [Erste Toolchain mithilfe der Toolchain zum Entwickeln einer Cloud Foundry-App erstellen und verwenden](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:external}.

  * [Einer App eine Toolchain hinzufügen](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:external}.
