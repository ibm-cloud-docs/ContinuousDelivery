---

copyright:
  years: 2015, 2019

lastupdated: "2019-2-8"


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

# Creación de cadenas de herramientas
{: #toolchains_getting_started}

Una *cadena de herramientas* es un conjunto de integraciones de herramientas que dan soporte a tareas de desarrollo, despliegue, y operaciones. La potencia en conjunto de una cadena de herramientas es superior a la suma de las integraciones de las herramientas individuales.
{: shortdesc}

Las cadenas de herramientas abiertas están disponibles en los entornos Público y Dedicado en {{site.data.keyword.Bluemix}}. Una cadena de herramientas se puede crear de dos formas: mediante una plantilla o a partir de una app.

Cada cadena de herramientas está asociada a un grupo de recursos u organización específico (org). Si una cadena de herramientas está asociada a un grupo de recursos, cualquier usuario que tenga permiso de Identity and Access Management (IAM) Viewer para el recurso de la cadena de herramientas o el grupo de recursos que lo contiene puede acceder a la cadena de herramientas. Si la cadena de herramientas está asociada con una organización, cualquier usuario que sea miembro de esa organización se puede añadir a la lista de control de accesos para cualquiera de sus cadenas de herramientas asociadas. Para obtener más información sobre el control de accesos para las cadenas de herramientas de organizaciones de Cloud Foundry, consulte [Gestión del acceso a cadenas de herramientas de las organizaciones de Cloud Foundry](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs){: new_window}. Para obtener más información sobre el control de accesos para las cadenas de herramientas de los grupos de recursos, consulte [Gestión del acceso a cadenas de herramientas de grupos de recursos](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_resource_groups){: new_window}.

##Creación de una cadena de herramientas a partir de una plantilla   
{: #creating_a_toolchain_from_a_template}

Puede utilizar una plantilla como punto de partida para [crear una cadena de herramientas ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/devops/create){: new_window} que incluya un conjunto específico de integraciones de herramientas. Obtenga más información sobre cómo utilizar las plantillas en el [Método IBM Cloud Garage ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud/garage/category/tools){:new_window}.

1. Si utiliza {{site.data.keyword.Bluemix_notm}} público, inicie la sesión en [{{site.data.keyword.Bluemix_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://cloud.ibm.com){:new_window}.
1. Si utiliza {{site.data.keyword.Bluemix_notm}} dedicado, inicie la sesión en el entorno dedicado en {{site.data.keyword.Bluemix_notm}}.
1. En el menú de la barra de menús de {{site.data.keyword.Bluemix_notm}}, pulse **DevOps**.
1. En el panel de control de DevOps, en la página **Cadenas de herramientas**, pulse **Crear una cadena de herramientas**.
1. En la página **Crear una cadena de herramientas**, pulse una plantilla de cadena de herramientas.
1. Revise el diagrama de la cadena de herramientas que se dispone a crear. El diagrama muestra cada integración de herramientas en la fase del ciclo de vida correspondiente en la cadena de herramientas.

 Algunas de las plantillas de cadena de herramientas tienen varias instancias de una integración de herramientas. Por ejemplo, la plantilla de la cadena de herramientas de microservicios de {{site.data.keyword.Bluemix_notm}} público contiene tres instancias de GitHub y tres instancias de Delivery Pipeline, una para cada uno de los tres microservicios.
 {: tip}

 El diagrama de la imagen siguiente es un ejemplo. Cuando cree una cadena de herramientas, el diagrama mostrará cada integración de herramientas que forma parte de la cadena de herramientas.
![Diagrama de la cadena de herramientas](images/toolchain_diagram2.png)

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


##Creación de una cadena de herramientas desde una app
{: #creating_a_toolchain_from_an_app}

Puede crear una cadena de herramientas desde su app. La cadena de herramientas puede admitir tareas continuadas de desarrollo, despliegue, supervisión, etc., y está asociada con su app. Cada app puede asociarse a una cadena de herramientas. Cuando se envían los cambios al repositorio de GitHub o {{site.data.keyword.ghe_short}} de la cadena de herramientas, el conducto crea y despliega automáticamente la app.

Si ha creado la app utilizando su propio repositorio de código, pulse **Conectarse a la cadena de herramientas de DevOps** en la página de detalles de su app. A continuación, siga los pasos que se describen en [Creación de apps a partir de su propio repositorio de código](/docs/apps?topic=creating-apps-tutorial-byoc#tutorial-byoc).
{: note}

1. Si ha creado la app utilizando un kit de inicio, pulse **Desplegar en la nube** en la página de detalles de la app. Si utiliza {{site.data.keyword.Bluemix_notm}} público, la app se configura para una entrega continua desde un nuevo repositorio de GitHub que ya contiene el código de inicio de la app. Si utiliza {{site.data.keyword.Bluemix_notm}} dedicado, la app se configura para una entrega continua desde un nuevo repositorio de GitHub o {{site.data.keyword.ghe_short}} que ya contiene el código de inicio de la app.
1. En la página de creación de cadenas de herramientas, revise el diagrama de la cadena de herramientas que está a punto de crear. El diagrama muestra cada integración de herramientas en la fase del ciclo de vida correspondiente en la cadena de herramientas.
1. Revise la información predeterminada para la configuración de la cadena de herramientas. El nombre de la cadena de herramientas la identifica en {{site.data.keyword.Bluemix_notm}}. Si desea utilizar otro nombre, cambie el nombre de la cadena de herramientas.
1. En la sección Integraciones de herramientas, seleccione las integraciones de herramientas que desee configurar para su cadena de herramientas. Algunas integraciones de herramientas no necesitan configuración. Para obtener información sobre cómo configurar las integraciones de herramientas, consulte [Configurar integraciones de herramientas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations){: new_window}.
1. Pulse **Crear**. Para configurar la cadena de herramientas, se ejecutan varios pasos automáticamente. Las integraciones de herramientas que se configuran dependen de si utiliza cadenas de herramientas en {{site.data.keyword.Bluemix_notm}} Público o {{site.data.keyword.Bluemix_notm}} Dedicado. Por ejemplo, si crea una cadena de herramientas a partir de una app en {{site.data.keyword.Bluemix_notm}} público, se ejecutan estos pasos:

 * Se crea la cadena de herramientas.
 * Si ha configurado Delivery Pipeline, los conductos se crean y se activan.
 * Si ha configurado GitHub, el repositorio de ejemplo de GitHub se clona en su cuenta de GitHub.


##Visualización de una cadena de herramientas
{: #viewing_a_toolchain}

Una vez que se ha configurado la cadena de herramientas y sus integraciones de herramientas, es posible obtener una representación visual de la cadena de herramientas.

Puede visualizar una cadena de herramientas desde una app pulsando **Visualizar cadena de herramientas** desde la página de detalles de la app.
{: tip}

1. En el panel de control de DevOps, en la página **Cadenas de herramientas**, seleccione un **GRUPO DE RECURSOS** u **ORGANIZACIÓN DE CLOUD FOUNDRY**. Se visualizan todas las cadenas de herramientas contenidas en el grupo de recursos seleccionado o en la organización de Cloud Foundry. Pulse la cadena de herramientas que desea ver para abrir su página Visión general. Como alternativa, en la página Visión general de la app, en la tarjeta de Entrega continua, pulse **Ver cadena de herramientas**. A continuación, pulse **Visión general**.
2. Para acceder a una integración de herramienta de su cadena de herramientas, pulse la herramienta.

 Si tiene más de un repositorio de GitHub, {{site.data.keyword.ghe_short}} o Git, puede tener varias tarjetas para la misma integración de herramientas porque cada repositorio se representa mediante su propia tarjeta. Si tiene más de un conducto, puede tener varias tarjetas para la misma integración de herramientas porque cada conducto se representa mediante su propia tarjeta. Por ejemplo, cuando se crea una cadena de herramientas de microservicios, cada uno de los tres microservicios tiene su propio repositorio GitHub, {{site.data.keyword.ghe_short}} o Git y su propio conducto.
 {: tip}

## Realice una guía de aprendizaje: Uso de las cadenas de herramientas
{: #toolchain_tutorials}

Consulte uno de estas guías de aprendizaje en [IBM&reg; Cloud Garage Method ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud/garage){:new_window}:

  * [Cree y utilice su primera cadena de herramientas utilizando la cadena de herramientas "Desarrollar una app de Cloud Foundry" ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}.

  * [Añada una cadena de herramientas para una app ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:new_window}.

  * [Utilice la cadena de herramientas "Desarrollar y probar microservicios en Cloud Foundry" ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}.
