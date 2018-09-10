---

copyright:
  years: 2018
lastupdated: "2018-6-22"

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

# Sucesos de {{site.data.keyword.cloudaccesstrailshort}}
{: #at_events}

Utilice el servicio {{site.data.keyword.cloudaccesstrailfull}} para realizar el seguimiento de cómo interactúan los usuarios y las aplicaciones con el servicio {{site.data.keyword.contdelivery_short}} en {{site.data.keyword.Bluemix}}. 
{: shortdesc}

El servicio {{site.data.keyword.cloudaccesstrailfull_notm}} registra las actividades iniciadas por el usuario que cambian el estado de un servicio en {{site.data.keyword.Bluemix_notm}}. Para más información, consulte la
publicación [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla).

<!-- You can create different sections to group events by area. -->

## Lista de sucesos
{: #events}

En la tabla siguiente se listan las acciones que generan un suceso:

| Acción | Descripción | 
|:-----------------|:-----------------|
| Crear cadena de herramientas | Crear una cadena de herramientas | 
| Suprimir la cadena de herramientas | Suprimir una cadena de herramientas |
| Crear herramienta | Crear una integración de herramientas |
| Suprimir herramienta | Suprimir una integración de herramientas |
{: caption="Tabla 1. Acciones que generan sucesos" caption-side="top"}

## Dónde ver los sucesos
{: #ui}

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

Los sucesos {{site.data.keyword.cloudaccesstrailshort}} están disponibles en el **dominio de cuenta** de {{site.data.keyword.cloudaccesstrailshort}} que está disponible en la región {{site.data.keyword.Bluemix_notm}} en la que se generan los sucesos.
