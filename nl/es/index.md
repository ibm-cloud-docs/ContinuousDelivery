---

copyright:
  years: 2015, 2019
lastupdated: "2019-2-7"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}


# Guía de aprendizaje de iniciación
{: #cd_getting_started}

Puede adoptar un enfoque DevOps mediante {{site.data.keyword.contdelivery_full}}, que incluye cadenas de herramientas abiertas que automatizan la creación y despliegue de aplicaciones. Puede empezar creando una sencilla cadena de herramientas que dé soporte a las tareas de desarrollo, despliegue y operaciones. 
{: shortdesc}

##Requisitos previos
{: #cd_prereqs}

Antes de poder crear una cadena de herramientas de entrega continua a partir de una plantilla, debe crear una instancia de {{site.data.keyword.contdelivery_short}} seleccionándola en el catálogo de {{site.data.keyword.Bluemix_notm}}. La cadena de herramientas integra herramientas para la planificación, despliegue de conductos y gestión de aplicaciones. Siempre puede añadir o eliminar herramientas de sus cadenas de herramientas. Si ya tiene cadenas de herramientas, puede [ver cadenas de herramientas existentes](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#viewing_a_toolchain){: new_window}. Para obtener más información sobre cómo trabajar con cadenas de herramientas, consulte el apartado sobre [Utilización de cadenas de herramientas](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using){: new_window}.

Si ya tiene una instancia de {{site.data.keyword.contdelivery_short}}, puede [crear una cadena de herramientas ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/devops/create){: new_window} o [visualizar cadenas de herramientas existentes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/devops/toolchains){: new_window}.
{: tip}

##Paso 1: Seleccionar una plantilla de cadena de herramientas
{: #select_a_toolchain_template}

1. En la página **Crear una cadena de herramientas**, pulse una [plantilla de cadena de herramientas ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/devops/create){: new_window}.
1. Revise el diagrama de la cadena de herramientas que se dispone a crear. El diagrama muestra cada integración de herramientas en la fase del ciclo de vida correspondiente en la cadena de herramientas.

 Algunas de las plantillas de cadena de herramientas tienen varias instancias de una integración de herramientas. Por ejemplo, la plantilla de la cadena de herramientas de microservicios de {{site.data.keyword.Bluemix_notm}} público contiene tres instancias de GitHub y tres instancias de Delivery Pipeline, una para cada uno de los tres microservicios.
 {: tip}

 El diagrama de la imagen siguiente es un ejemplo. Cuando cree una cadena de herramientas, el diagrama mostrará cada integración de herramientas que forma parte de la cadena de herramientas.
 ![Diagrama_cadena_herramientas](images/toolchain_diagram2.png)
 
##Paso 2: Crear una cadena de herramientas 
{: #create_a_toolchain}
 
1. Revise la información predeterminada de los valores de la cadena de herramientas:

 * El nombre de la cadena de herramientas la identifica en {{site.data.keyword.Bluemix_notm}}. Si desea utilizar otro nombre, cambie el nombre de la cadena de herramientas.
 * La región en la que se va crear la cadena de herramientas. Si desea utilizar otra región, selecciónela en la lista de regiones disponibles.
 * El grupo de recursos u organización en la que crear la cadena de herramientas. Pulse el enlace para conmutar entre la selección de grupos de recursos y organizaciones. Si desea utilizar un grupo de recursos u organización distinto, selecciónelo desde la lista de grupos de recursos u organizaciones disponibles.
 
   Los grupos de recursos están disponibles en las regiones EE.UU. sur, EE.UU. este, Reino Unido, Alemania y Tokio. Las organizaciones de Cloud Foundry están soportadas en las regiones EE.UU. sur, EE.UU. este, Reino Unido y Alemania.
   {: important}
 
1. En la sección Integraciones de herramientas, seleccione las integraciones de herramientas que desee configurar para su cadena de herramientas. Algunas integraciones de herramientas no necesitan configuración. Para obtener información sobre cómo configurar las integraciones de herramientas, consulte [Configurar integraciones de herramientas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations){: new_window}.
1. Pulse **Crear**. Para configurar la cadena de herramientas, se ejecutan varios pasos automáticamente. Las integraciones de herramientas que se configuran varían en función de la plantilla de cadena de herramientas que haya seleccionado y de si utiliza {{site.data.keyword.Bluemix_notm}} público o {{site.data.keyword.Bluemix_notm}} dedicado. Por ejemplo, si crea una cadena de herramientas de microservicios en {{site.data.keyword.Bluemix_notm}} público, se ejecutan estos pasos:

 * Se crea la cadena de herramientas.
 * Si ha configurado Delivery Pipeline, los conductos se crean y se activan.
 * Si ha configurado Sauce Labs, la cadena de herramientas se configura para añadir trabajos de prueba de Sauce Labs a los conductos.
 * Si ha configurado PagerDuty, la cadena de herramientas se configura para enviar notificaciones de alerta al servicio de PagerDuty que ha especificado.
 * Si ha configurado Slack, la cadena de herramientas se configura para enviar notificaciones sobre el estado de despliegue al canal Slack que ha especificado.
 * Si ha configurado la integración de una herramienta de código fuente como GitHub, el repositorio de ejemplo de GitHub se clona en su cuenta de GitHub.

##Siguientes pasos
{: #next_steps}

Consulte uno de estas guías de aprendizaje en [IBM&reg; Cloud Garage Method ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud/garage){:new_window}:

  * [Cree y utilice su primera cadena de herramientas utilizando la cadena de herramientas "Desarrollar una app de Cloud Foundry" ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}.

  * [Añada una cadena de herramientas para una app ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:new_window}.
