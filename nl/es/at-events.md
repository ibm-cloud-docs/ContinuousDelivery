---

copyright:
  years: 2018, 2019
lastupdated: "2019-2-1"

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

El servicio {{site.data.keyword.cloudaccesstrailfull_notm}} registra las actividades iniciadas por el usuario que cambian el estado de un servicio en {{site.data.keyword.Bluemix_notm}}. Para obtener más información, consulte [{{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla).

<!-- You can create different sections to group events by area. -->

## Lista de sucesos
{: #events}

En la tabla siguiente se listan las acciones que generan un suceso:

| Acción | Descripción | 
|:-----------------|:-----------------|
| continuous-delivery.toolchain.create | Crear una cadena de herramientas | 
| continuous-delivery.toolchain.delete | Suprimir una cadena de herramientas |
| toolchain.tool-instance.deploy | Crear una integración de herramientas |
| toolchain.tool-instance.undeploy | Suprimir una integración de herramientas |
{: caption="Tabla 1. Acciones que generan sucesos" caption-side="top"}

## Dónde ver los sucesos
{: #ui}

<!-- Option 2: Add the following sentence if your service sends events to the account domain. -->

Los sucesos {{site.data.keyword.cloudaccesstrailshort}} están disponibles en el **dominio de cuenta** de {{site.data.keyword.cloudaccesstrailshort}} que está disponible en la región {{site.data.keyword.Bluemix_notm}} en la que se generan los sucesos.
