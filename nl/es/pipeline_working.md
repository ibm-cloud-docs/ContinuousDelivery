---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-27"

keywords: IBM Cloud, build types, build script

subcollection: ContinuousDelivery

---


{:screen: .screen}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:shortdesc: .shortdesc}

# Cómo trabajar con conductos 
{: #pipeline-working}

Para automatizar las compilaciones y los despliegues en {{site.data.keyword.Bluemix}}, utilice los conductos de {{site.data.keyword.contdelivery_full}}.
{: shortdesc}

Con los conductos, puede elegir entre distintos tipos de compilación. Proporcione el script de compilación y {{site.data.keyword.contdelivery_short}} lo ejecutará; no es necesario configurar sistemas de compilación. A continuación, con una sola pulsación, puede desplegar automáticamente la app en uno o más espacios de {{site.data.keyword.Bluemix_notm}}, servidores de Cloud Foundry públicos o contenedores Docker en el {{site.data.keyword.containerlong}}.

Los trabajos de compilación compilan y empaquetan el código fuente de su app desde repositorios Git. Los trabajos de compilación generan artefactos desplegables, como archivos WAR o contenedores Docker para el {{site.data.keyword.containerlong_notm}}. Además, puede ejecutar automáticamente pruebas de unidad en su compilación. Puede configurar sus trabajos de compilación de modo que cada vez que se envíe una confirmación se desencadene una compilación.

Un trabajo de despliegue toma la salida de un trabajo de compilación y lo despliega en el {{site.data.keyword.containerlong_notm}} o en servidores de Cloud Foundry como {{site.data.keyword.Bluemix_notm}}.

Puede desplegar en una o más regiones y servicios. Por ejemplo, puede configurar {{site.data.keyword.deliverypipeline}} para que utilice uno o varios servicios, realice pruebas en una región y despliegue a producción en varias regiones.

##Creación de un conducto

Puede utilizar cualquiera de los métodos siguientes para crear un conducto:

   * [Crear una cadena de herramientas a partir de una aplicación Cloud Foundry existente](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_an_app){: new_window}. La cadena de herramientas resultante contiene un conducto.

   * [Crear una cadena de herramientas a partir de una plantilla](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_a_template){: new_window} que incluya al menos un conducto.

   * [Añadir la integración de herramientas de {{site.data.keyword.deliverypipeline}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#deliverypipeline){: new_window} a una cadena de herramientas existente.
   
En {{site.data.keyword.deliverypipeline}}, puede cambiar la configuración, comprobar el estado de las compilaciones, la app desplegada y los despliegues recientes, consultar los registros y detalles de despliegue más recientes o suprimir el conducto.
