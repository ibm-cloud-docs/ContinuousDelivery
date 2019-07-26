---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: IBM Cloud Continuous Delivery, private workers integration

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


# Mit privaten {{site.data.keyword.deliverypipeline}}-Workern arbeiten
{: #private-workers}

{{site.data.keyword.deliverypipeline}} verwendet öffentliche und private Worker für die Ausführung von Pipelinejobs. Standardmäßig werden Pipelinejobs ausgeführt, indem öffentliche Worker in einer öffentlichen von IBM verwalteten und gemeinsam genutzten Infrastruktur verwendet werden.
{: shortdesc}

In bestimmten Szenarios benötigt {{site.data.keyword.deliverypipeline}} möglicherweise Zugriff auf interne oder lokale Ressourcen. In diesen Situationen können Sie eine Verbindung zu einem privaten {{site.data.keyword.deliverypipeline}}-Worker herstellen und ihn für die Ausführung in Ihrer eigenen Kubernetes-Infrastruktur integrieren.

## Voraussetzungen
{: #private_workers_prereqs}

Stellen Sie vor der Einrichtung eines privaten Workers sicher, dass die folgenden Ressourcen vorhanden sind:

* Ein Kubernetes-Cluster. Sie müssen über einen Cluster verfügen, um einen privaten Worker zu installieren. Sie können Ihren eigenen Cluster bereitstellen oder Sie können aus dem {{site.data.keyword.containerlong_notm}} [einen Cluster einrichten](https://cloud.ibm.com/kubernetes/clusters){:external}.

* Eine Toolchain mit einer Pipeline, die mindestens eine Stage enthält. Sie können eine vorhandene Toolchain verwenden oder [eine Toolchain erstellen](https://cloud.ibm.com/devops/create){:external}.

## Privaten {{site.data.keyword.deliverypipeline}}-Worker einrichten
{: #set_up_private_worker}

Führen Sie die folgenden Schritte aus, um einen privaten Worker einzurichten:

1. Konfigurieren Sie die Toolintegration {{site.data.keyword.deliverypipeline}} Private Worker für Ihre Toolchain.
2. Konfigurieren Sie Ihren Kubernetes-Cluster mit einem privaten Worker.
3. Verwenden Sie den privaten Worker in Ihrer Pipeline.

### Toolintegration {{site.data.keyword.deliverypipeline}} Private Worker konfigurieren
{: #configure_private_worker_integration}

Führen Sie die folgenden Schritte aus, um die Toolintegration {{site.data.keyword.deliverypipeline}} Private Worker für Ihre Toolchain zu konfigurieren:

1. Wenn Sie diese Toolintegration konfigurieren, während Sie die Toolchain erstellen, klicken Sie im Abschnitt mit den konfigurierbaren Integrationen auf **{{site.data.keyword.deliverypipeline}} Private Worker**.
1. Wenn Sie eine Toolchain haben und diese Toolintegration hinzufügen, klicken Sie im DevOps-Dashboard auf der Seite 'Toolchains' auf die Toolchain, um die zugehörige Übersichtsseite zu öffnen. Alternativ können Sie auf der Übersichtsseite Ihrer App auf der Karte für Continuous Delivery auf **Toolchain anzeigen** und dann auf **Übersicht** klicken.

 a. Klicken Sie auf **Tool hinzufügen**.

 b. Klicken Sie im Abschnitt mit den Toolintegrationen auf **{{site.data.keyword.deliverypipeline}} Private Worker**.

1. Geben Sie einen Namen für die Toolintegration ein. Dieser Name identifiziert einen Pool privater Worker auf der Registerkarte **Worker** der Pipeline-Stage.
1. Geben Sie Ihren Service-ID-API-Schlüssel ein, um den Zugriff auf die Arbeitswarteschlange zu authentifizieren, in der ein oder mehrere private Worker auf Arbeit warten können. Wenn Sie keinen Service-ID-API-Schlüssel haben, klicken Sie auf **Erstellen**, um einen für diesen privaten Worker zu generieren.
1. Klicken Sie auf **Integration erstellen**.
1. Klicken Sie in Ihrer Toolchain auf **{{site.data.keyword.deliverypipeline}} Private Worker**, um eine Liste aller Worker anzuzeigen, die unter Verwendung eines API-Schlüssels registriert sind, der dieser Service-ID zugeordnet ist.

Weitere Informationen zur Toolintegration **{{site.data.keyword.deliverypipeline}} Private Worker** finden Sie unter [{{site.data.keyword.deliverypipeline}} Private Worker konfigurieren](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations#privateworker).

### Kubernetes-Cluster konfigurieren
{: #configure_kubernetes_cluster}

Konfigurieren Sie Ihren Kubernetes-Cluster mit einem privaten Worker:

1. Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf eine Toolchain, um die zugehörige Übersichtsseite anzuzeigen. Alternativ können Sie auf der Übersichtsseite der App auf der Karte für Continuous Delivery auf **Toolchain anzeigen** und dann auf **Übersicht** klicken.
1. Klicken Sie auf die Karte für die Toolintegration {{site.data.keyword.deliverypipeline}} Private Worker, die Sie konfigurieren möchten.
1. Klicken Sie auf **Einführung** und befolgen Sie dann die Schritte zum Installieren und Registrieren eines privaten Workers in Ihrem Kubernetes-Cluster.

### {{site.data.keyword.deliverypipeline}} Private Worker in Ihrer Pipeline verwenden
{: #use_private_worker_pipeline}

Führen Sie die folgenden Schritte aus, um den privaten Worker in Ihrer Pipeline zu verwenden:

1. Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf eine Toolchain, um die zugehörige Übersichtsseite anzuzeigen. Alternativ können Sie auf der Übersichtsseite der App auf der Karte für Continuous Delivery auf **Toolchain anzeigen** und dann auf **Übersicht** klicken.
1. Klicken Sie auf die Karte für die Pipeline, mit der Sie den privaten Worker verwenden möchten.
1. Klicken Sie auf der Pipelineseite in der Stage auf das Symbol **Stagekonfiguration** und dann auf **Stage konfigurieren**.
1. Klicken Sie auf die Registerkarte **Worker**.
1. Wählen Sie den privaten Worker aus, den Sie in Ihrer Pipeline verwenden möchten. 

 Standardmäßig werden Jobs in einer Pipeline-Stage ausgeführt, indem ein Pool gemeinsam genutzter von IBM verwalteter Worker in der Region verwendet wird, in der die Pipeline definiert ist.{: tip}
 
1. Klicken Sie auf **Speichern**.
1. Sie können Ihre Stage manuell ausführen oder auf einen Auslöser warten, um die Jobs der Stage unter Verwendung des angegebenen privaten Workers auf dem zugehörigen Kubernetes-Cluster auszuführen. Sie können die Protokolldateiausgabe für die Jobs anzeigen, um festzustellen, welcher Worker verwendet wurde.  


## Berechtigungsnachweise der Toolintegration {{site.data.keyword.deliverypipeline}} Private Worker ändern
{: #modify_private_worker}

Nachdem Sie Ihren privaten Worker eingerichtet haben, können Sie die Berechtigungsnachweise aktualisieren, die für die Toolintegration verwendet werden. Möglicherweise möchten Sie diese Berechtigungsnachweise ändern, wenn sie gelöscht, abgelaufen oder gefährdet sind. Sie können die Berechtigungsnachweise aktualisieren, indem Sie eine neue Service-ID erstellen oder den API-Schlüssel aktualisieren.

### Service-ID erstellen
{: #create_service_id}

Führen Sie die folgenden Schritte aus, um eine Service-ID zu erstellen:

1. Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf eine Toolchain, um die zugehörige Übersichtsseite anzuzeigen. Alternativ können Sie auf der Übersichtsseite der App auf der Karte für Continuous Delivery auf **Toolchain anzeigen** und dann auf **Übersicht** klicken.
1. Klicken Sie auf der Karte für die Toolintegration für private Worker, die Sie ändern möchten, auf das Menü, um auf die Konfigurationsoptionen zuzugreifen.
1. Klicken Sie auf **Erstellen**.
1. Geben Sie einen Namen und eine Beschreibung für die Service-ID ein.
1. Klicken Sie auf **Integration speichern**.
1. Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf eine Toolchain, um die zugehörige Übersichtsseite anzuzeigen. Alternativ können Sie auf der Übersichtsseite der App auf der Karte für Continuous Delivery auf **Toolchain anzeigen** und dann auf **Übersicht** klicken.
1. Klicken Sie auf die Karte für die Toolintegration {{site.data.keyword.deliverypipeline}} Private Worker, für die Sie neue Benutzerberechtigungsnachweise angeben möchten.
1. Klicken Sie auf **Einführung** und führen Sie die Schritte 2 und 3 aus, um den privaten Worker in Ihrem Cluster zu registrieren und zu überprüfen.

### API-Schlüssel aktualisieren
{: #update_api_key}

Führen Sie die folgenden Schritte aus, um den API-Schlüssel für die Verwendung mit der Toolintegration {{site.data.keyword.deliverypipeline}} Private Worker zu aktualisieren:

1. Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf eine Toolchain, um die zugehörige Übersichtsseite anzuzeigen. Alternativ können Sie auf der Übersichtsseite der App auf der Karte für Continuous Delivery auf **Toolchain anzeigen** und dann auf **Übersicht** klicken.
1. Klicken Sie auf der Karte für die Toolintegration {{site.data.keyword.deliverypipeline}} Private Worker, die Sie ändern möchten, auf das Menü, um auf die Konfigurationsoptionen zuzugreifen.
1. Geben Sie Ihren neuen API-Schlüssel an. 
1. Klicken Sie auf **Integration speichern**.

## Privaten {{site.data.keyword.deliverypipeline}}-Worker löschen
{: #delete_private_worker}

Führen Sie die folgenden Schritte aus, um einen privaten Worker zu löschen:

1. Löschen Sie den privaten Worker aus dem Pool der Worker.
1. Löschen Sie den privaten Worker aus Ihrem Kubernetes-Cluster.

### Privaten {{site.data.keyword.deliverypipeline}}-Worker aus dem Pool der Worker löschen

Führen Sie die folgenden Schritte aus, um den privaten Worker aus dem Pool der Worker zu löschen:

1. Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf eine Toolchain, um die zugehörige Übersichtsseite anzuzeigen. Alternativ können Sie auf der Übersichtsseite der App auf der Karte für Continuous Delivery auf **Toolchain anzeigen** und dann auf **Übersicht** klicken.
1. Klicken Sie auf die Karte für die Toolintegration {{site.data.keyword.deliverypipeline}} Private Worker, die Sie konfigurieren möchten.
1. Klicken Sie auf **Übersicht**.
1. Klicken Sie auf das Menü für den privaten Worker, den Sie löschen möchten, um auf die Konfigurationsoptionen zuzugreifen.
1. Klicken Sie auf **Entfernen** und dann auf **Bestätigen**.

### Privaten {{site.data.keyword.deliverypipeline}}-Worker aus Ihrem Kubernetes-Cluster löschen

Führen Sie die folgenden Schritte aus, um den privaten Worker aus Ihrem Cluster zu löschen:

1. Klicken Sie auf die Karte für die Toolintegration {{site.data.keyword.deliverypipeline}} Private Worker, die Sie konfigurieren möchten.
1. Klicken Sie auf **Einführung** und befolgen Sie die Schritte zum Löschen des privaten Workers aus Ihrem Cluster.

## Toolintegration {{site.data.keyword.deliverypipeline}} Private Worker löschen
{: #delete_private_workers_tool_integration}

Wenn Sie die Toolintegration {{site.data.keyword.deliverypipeline}} Private Worker aus Ihrer Toolchain löschen, kann diese Löschung nicht mehr rückgängig gemacht werden.
{: important}

Führen Sie die folgenden Schritte aus, um eine Toolintegration {{site.data.keyword.deliverypipeline}} Private Worker zu löschen:

1. Klicken Sie im DevOps-Dashboard auf der Seite **Toolchains** auf eine Toolchain, um die zugehörige Übersichtsseite anzuzeigen. Alternativ können Sie auf der Übersichtsseite der App auf der Karte für Continuous Delivery auf **Toolchain anzeigen** und dann auf **Übersicht** klicken.
1. Klicken Sie auf der Karte für die Toolintegration {{site.data.keyword.deliverypipeline}} Private Worker, die Sie löschen möchten, auf das Menü, um auf die Konfigurationsoptionen zuzugreifen.
1. Klicken Sie auf **Löschen**, um die Toolintegration aus Ihrer Toolchain zu löschen.
1. Bestätigen Sie dies, indem Sie nochmals auf **Löschen** klicken. Die Toolintegration {{site.data.keyword.deliverypipeline}} Private Worker wird aus der Toolchain entfernt und ist auf der Registerkarte **Worker** auf der Seite für die Delivery Pipeline-Stage-Konfiguration nicht mehr verfügbar.

Wenn Sie die Toolintegration {{site.data.keyword.deliverypipeline}} Private Worker aus einer Toolchain löschen und der private Worker für eine Pipeline-Stage konfiguriert ist, wird sie weiterhin auf der Registerkarte **Worker** auf der Stage-Konfigurationsseite aufgelistet. Der private Worker ist jedoch inaktiviert und mit REMOVED (entfernt) gekennzeichnet. Sie müssen einen anderen privaten Worker auswählen (sofern vorhanden) oder stattdessen einen öffentlichen Worker verwenden.
{: tip}
