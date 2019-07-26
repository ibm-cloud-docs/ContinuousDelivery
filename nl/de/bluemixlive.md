---



copyright:
  years: 2015，2019
lastupdated: "2019-06-19"

keywords: IBM Cloud Live Synch, Use IBM Cloud Live Sync

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

# {{site.data.keyword.Bluemix_notm}} Live Sync
{: #live-sync}

Wenn Sie eine Node.js-Anwendung erstellen, können Sie {{site.data.keyword.Bluemix}} Live Sync verwenden, um die Anwendungsinstanz unter {{site.data.keyword.Bluemix_notm}} rasch zu aktualisieren und Entwicklungsarbeiten ohne manuelle Neubereitstellung auszuführen.   
{: shortdesc}

Wenn Sie eine Änderung vornehmen, ist diese Änderung sofort in Ihrer aktiven {{site.data.keyword.Bluemix_notm}}-Anwendung sichtbar. {{site.data.keyword.Bluemix_notm}} Live Sync wird
<!--from both the command line and -->
in der Eclipse Orion {{site.data.keyword.webide}} ({{site.data.keyword.webide}}) ausgeführt. 

##Live Edit
{: #live-edit}

Sie können eine Node.js-Anwendung, die unter {{site.data.keyword.Bluemix_notm}} ausgeführt wird, bearbeiten und direkt in Ihrem Browser testen. Alle Änderungen, die Sie in der {{site.data.keyword.webide}} vornehmen, werden umgehend an das Dateisystem der Anwendung weitergegeben.

Wenn Sie eine Node.js-Anwendung erstellen, die unter {{site.data.keyword.Bluemix_notm}} ausgeführt wird, kann das Live Edit-Feature von {{site.data.keyword.Bluemix_notm}} Live Sync die Anwendungsinstanz schnell aktualisieren. Live Edit steht nur in der {{site.data.keyword.webide}} zur Verfügung. Mithilfe von Live Edit können Sie Entwicklungsprozesse wie auf dem Desktop durchführen, ohne dass eine erneute Bereitstellung erforderlich ist.

Live Edit wird nur für Node.js-Anwendungen unterstützt.
{: important}

Klicken Sie in der {{site.data.keyword.webide}} in der Ausführungsleiste auf **Live Edit**.

![Abbildung der Ausführungsleiste mit Live Edit](images/cloud-live-sync-light.png)

Mit Live Edit erhalten Sie in kürzester Zeit eine Vorschau der Änderungen an Node.js-Anwendungen, die unter {{site.data.keyword.Bluemix_notm}} ausgeführt werden. Wenn Sie den Code bei aktiviertem Live Edit-Feature ändern, können Sie das Browserfenster Ihrer Webanwendung aktualisieren und die vorgenommenen Änderungen sind wenige Sekunden später sichtbar.

Ein Lernprogramm zur Verwendung der Live Edit-Funktion von {{site.data.keyword.Bluemix_notm}} Live Sync finden Sie in [{{site.data.keyword.Bluemix_notm}} Live Sync zum Entwickeln, Debuggen und Bereitstellen Ihrer App verwenden](https://www.ibm.com/cloud/garage/tutorials/use-live-sync-to-develop-debug-and-deploy-your-app){: external}.

Wenn Sie die Dateien in Ihrer {{site.data.keyword.webide}} ändern, werden sie automatisch für Ihre Anwendungsinstanz unter {{site.data.keyword.Bluemix_notm}} erneut bereitgestellt. Wenn Sie die Node-Anwendung erneut starten müssen, klicken Sie in der Ausführungsleiste auf die Schaltfläche **Erneut starten**.

Für ein möglichst konsistentes Verarbeitungsverhalten bei Verwendung des Live Edit-Features von {{site.data.keyword.Bluemix_notm}} Live Sync ist eine zusätzliche Speicherkapazität von 256 MB erforderlich und wird hinzugefügt.
{: tip}
