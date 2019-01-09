---

copyright:
  years: 2018
lastupdated: "2018-10-10"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:table: .aria-labeledby="caption"}

<!-- Name your file `at-events.md` and include it in the Reference nav group in your toc file. -->

# {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse
{: #at_events}

Verwenden Sie den Service {{site.data.keyword.cloudaccesstrailfull}}, um zu verfolgen, wie Benutzer und Anwendungen mit dem Service ?{{site.data.keyword.contdelivery_short}} in {{site.data.keyword.Bluemix}} interagieren. 
{: shortdesc}

Der Service {{site.data.keyword.cloudaccesstrailfull_notm}} zeichnet benutzerinitiierte Aktivitäten auf, die den Status eines Service in {{site.data.keyword.Bluemix_notm}} ändern. Weitere Informationen finden Sie unter [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla).

<!-- You can create different sections to group events by area. -->

## Ereignisliste
{: #events}

In der folgenden Tabelle sind die Aktionen aufgelistet, die ein Ereignis generieren:

| Aktion | Beschreibung | 
|:-----------------|:-----------------|
| continuous-delivery.toolchain.create | Toolchain erstellen | 
| continuous-delivery.toolchain.delete | Toolchain löschen |
| toolchain.tool-instance.deploy | Toolintegration erstellen |
| toolchain.tool-instance.undeploy | Toolintegration löschen |
{: caption="Tabelle 1. Aktionen, die Ereignisse generieren" caption-side="top"}

## Wo die Ereignisse angezeigt werden
{: #ui}

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

{{site.data.keyword.cloudaccesstrailshort}}-Ereignisse sind in der {{site.data.keyword.cloudaccesstrailshort}}-**Kontodomäne** verfügbar, die in der {{site.data.keyword.Bluemix_notm}}-Region verfügbar ist, in der die Ereignisse generiert werden.
