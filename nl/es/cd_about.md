---

Copyright:
  years: 2015, 2019
lastupdated: "2019-03-27"

keywords: IBM Cloud Public, Use Developer Insights, US South

subcollection: ContinuousDelivery

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


# Disponibilidad, plantillas y guías de aprendizaje de cadenas de herramientas  
{: #cd_about}  

Las cadenas de herramientas están disponibles en {{site.data.keyword.Bluemix_notm}} público y dedicado. Las plantillas sirven como punto de partida para crear una cadena de herramientas.
{:shortdesc}

## Disponibilidad de cadenas de herramientas en {{site.data.keyword.Bluemix_notm}} público en comparación con {{site.data.keyword.Bluemix_notm}} dedicado
{: #public_and_dedicated}

{{site.data.keyword.Bluemix_notm}} público es una plataforma basada en la nube de estándares abiertos con la que puede crear, ejecutar y gestionar aplicaciones a las que accede [http://cloud.ibm.com ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://cloud.ibm.com){:new_window}. {{site.data.keyword.Bluemix_notm}} dedicado ofrece las funciones de {{site.data.keyword.Bluemix_notm}} en un entorno SoftLayer dedicado conectado de forma segura tanto al entorno de {{site.data.keyword.Bluemix_notm}} público como a la red. Es posible que el entorno {{site.data.keyword.Bluemix_notm}} dedicado de la empresa no contenga las mismas integraciones de herramientas que el sitio de {{site.data.keyword.Bluemix_notm}} público.

Para la gestión de código fuente y el seguimiento de problemas, {{site.data.keyword.Bluemix_notm}} público utiliza generalmente {{site.data.keyword.gitrepos}} (alojado en IBM y basado en [GitLab Community Edition ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://about.gitlab.com/){:new_window}) o GitHub (github.com). {{site.data.keyword.Bluemix_notm}} dedicado también puede utilizar github.com, aunque normalmente utiliza {{site.data.keyword.ghe_short}} instalado por la empresa o gestionado por IBM.

{{site.data.keyword.contdelivery_short}} está disponible en {{site.data.keyword.Bluemix_notm}} público determinadas regiones y en {{site.data.keyword.Bluemix_notm}} dedicado. Las cadenas de herramientas difieren en función de si utiliza {{site.data.keyword.contdelivery_short}} en {{site.data.keyword.Bluemix_notm}} público o en {{site.data.keyword.Bluemix_notm}} dedicado.

Aunque las cadenas de herramientas no están disponibles actualmente en todas las regiones, puede configurar la cadena de herramientas para que despliegue las apps en todas las regiones. Para saber más, vea la guía de aprendizaje [Desplegar una aplicación web segura en varias regiones](/docs/tutorials?topic=solution-tutorials-multi-region-webapp){: new_window}.
{: tip}

|Cadenas de herramientas |{{site.data.keyword.Bluemix_notm}} público	|{{site.data.keyword.Bluemix_notm}} dedicado |
|:----------|:------------------------------|:------------------|
|Integraciones de herramientas 		|Para ver una lista de las integraciones de herramientas admitidas, consulte [Configurar integraciones de herramientas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations){: new_window}. 		|Las integraciones de herramientas disponibles dependen de cómo se haya configurado {{site.data.keyword.contdelivery_short}} en el entorno.			|
|Creación de una cadena de herramientas a partir de una plantilla		|Inicie sesión en [{{site.data.keyword.Bluemix_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://cloud.ibm.com/devops){:new_window}		|Inicie la sesión en el entorno dedicado en {{site.data.keyword.Bluemix_notm}}.			|
|Creación de una cadena de herramientas desde una app		|La app se configura para una entrega continuada desde un nuevo repositorio de GitHub que ya contiene el código de inicio de la app.		|La app se configura para una entrega continua desde un nuevo repositorio de GitHub o GitHub Enterprise que ya contiene el código de inicio de la app.		|  
|Regiones de despliegue de conducto de entrega		|Todas las regiones de {{site.data.keyword.Bluemix_notm}} público están disponibles para los trabajos de despliegue de Cloud Foundry. 		|La región de {{site.data.keyword.Bluemix_notm}} dedicado está disponible. Otras regiones dedicadas o locales dentro de la misma cuenta de cliente también pueden estar disponibles en función de cómo se haya configurado {{site.data.keyword.contdelivery_short}} en el entorno específico.		|
|Trabajos de despliegue de conducto de entrega		|Todos los [tipos de trabajos](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_jobs) están disponibles.		|Los tipos de trabajos que dependen de servicios de {{site.data.keyword.Bluemix_notm}} que no estén instalados en el entorno dedicado pueden no estar disponibles.	Por ejemplo, los tipos de trabajos de despliegue y compilación de contenedores pueden no estar disponibles en entornos que no tengan el {{site.data.keyword.containerlong_notm}}.	|
{: caption="Tabla 1. Diferencias entre cadenas de herramientas en {{site.data.keyword.Bluemix_notm}} dedicado y {{site.data.keyword.Bluemix_notm}} público" caption-side="top"}


## Plantillas de cadenas de herramientas
{: #templates}

Puede utilizar una plantilla como punto de partida para [crear una cadena de herramientas ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/devops/create){: new_window}. Las plantillas de cadenas de herramientas incluyen conjuntos específicos de integraciones de herramientas que admiten tareas de desarrollo, despliegue y operaciones.

Es posible que el entorno {{site.data.keyword.Bluemix_notm}} dedicado de la empresa no contenga las mismas plantillas de cadena de herramientas que el sitio de {{site.data.keyword.Bluemix_notm}} público. Las plantillas de cadenas de herramientas que están disponibles tanto en {{site.data.keyword.Bluemix_notm}} público como en {{site.data.keyword.Bluemix_notm}} dedicado pueden contener un conjunto distinto de integraciones de herramientas en {{site.data.keyword.Bluemix_notm}} dedicado.
{: note}

Algunas plantillas de cadenas de herramientas incluyen integraciones que forman parte del servicio {{site.data.keyword.contdelivery_short}}. Si su organización o grupo de recursos aún no tiene ninguna instancia de dicho servicio, cuando pulse **Crear** para crear la cadena de herramientas, el servicio se añade automáticamente con el plan Lite gratuito seleccionado. Para obtener más información y ver las condiciones, consulte el [Catálogo de {{site.data.keyword.Bluemix_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/catalog/services/continuous-delivery/){:new_window}.

La cadena de herramientas "Desarrollar y probar microservicios en Cloud Foundry" despliega una app con las API de catálogo y de pedidos que se han copiado en un almacén de Cloudant. Como parte del despliegue de la app, se crea una instancia del servicio Cloudant sin coste alguno. Para obtener más información y ver las condiciones, consulte el [Catálogo de {{site.data.keyword.Bluemix_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/catalog/services/cloudant-nosql-db/){:new_window}.

Las plantillas de cadena de herramientas de DevOps predefinidas son ejemplos recomendados que resuelven situaciones del mundo real. Cada una contiene una app de ejemplo.  Puede utilizar su propia app especificando el repositorio git al crear la cadena de herramientas a partir de la plantilla.

<table valign="top" padding="2px">
  <caption>Tabla 2. Plantillas de cadenas de herramientas</caption>
  <tr>
    <th style="width:25%; text-align:left; vertical-align:top">Plantilla y regiones disponibles</th>
    <th style="width:50%; text-align:left; vertical-align:top">Descripción y guías de aprendizaje disponibles</th>
    <th style="text-align:left; vertical-align:top">Herramientas incluidas</th>
  </tr>
  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-toolchain" target="_blank">Cadena de herramientas “Desarrollar una app de Cloud Foundry” <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> <br><br>

  Disponible en EE.UU. sur, EE.UU. este, Alemania, Tokio y Reino Unido

  </td><td>
  Con esta cadena de herramientas puede desarrollar y desplegar una app de Cloud Foundry. De forma predeterminada, esta cadena de herramientas utiliza una app Node.js "Hello world" de ejemplo, pero puede enlazar en su lugar con su propio repositorio GitHub. La cadena de herramientas está preconfigurada para entrega continua, control de código fuente, seguimiento de problemas y edición en línea.	<br><br>

  Consulte la guía de aprendizaje: <a href="https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain" target="_blank">Incorpore cadenas de herramientas mediante la cadena de herramientas “Desarrollar una app de Cloud Foundry” <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> <br><br>
  </td><td><ul><li>
  {{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub y problemas
  </li><li>{{site.data.keyword.Bluemix_notm}}
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsecure-kube-toolchain" target="_blank">Cadena de herramientas "Desarrollar una app de Kubernetes" <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> <br><br>

  Disponible en EE.UU. sur, EE.UU. este, Alemania, Tokio y Reino Unido

  </td><td>
  Con esta cadena de herramientas, puede desarrollar y desplegar una aplicación de forma segura en un clúster Kubernetes gestionado por {{site.data.keyword.containerlong_notm}}. De forma predeterminada, la cadena de herramientas utiliza una app de muestra Node.js "Hello World", pero puede enlazar a su propio repositorio GitHub en su lugar. La cadena de herramientas está preconfigurada para la entrega continua con Vulnerability Advisor, control de origen, seguimiento de problemas y edición en línea. <br><br>
  Consulte la guía de aprendizaje: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-toolchain" target="_blank">Utilice la cadena de herramientas "Desarrollar una app de Kubernetes" <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>  
  <br><br>
  </td><td><ul><li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub y problemas
  </li><li>{{site.data.keyword.containerlong_notm}} (clúster de Kubernetes)
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-helm-toolchain" target="_blank">Cadena de herramientas "Desarrollar una app de Kubernetes con Helm"
   <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> <br><br>

  Disponible en EE.UU. sur, EE.UU. este, Alemania, Tokio y Reino Unido

  </td><td>
  Con esta cadena de herramientas, puede desarrollar una aplicación Docker y su diagrama de Helm de forma conjunta en el control de origen y compilarlos y desplegarlos automáticamente en un clúster de Kubernetes. La cadena de herramientas realiza pruebas aleatorias antes de compilar o desplegar y garantiza la privacidad mediante un registro de contenedores privado y espacios de nombres para el registro de contenedores y el clúster de Kubernetes. Esta cadena también utiliza Vulnerability Advisor para garantizar que sólo se desplieguen imágenes seguras. <br><br>
  Consulte la guía de aprendizaje: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-with-helm-toolchain" target="_blank">Utilice la cadena de herramientas "Desarrollar una app de Kubernetes con Helm" <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>	 <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>Git Repos and Issue Tracking
  </li><li>{{site.data.keyword.containerlong_notm}} (clúster de Kurbernetes) con un diagrama Helm
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdra-toolchain-demo" target="_blank">Cadena de herramientas "Desarrollar y probar una app de Cloud Foundry"
   <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> <br><br>

  Disponible en EE.UU. sur, Alemania y Reino Unido

  </td><td>
  Con esta cadena de herramientas nativa de la nube, puede utilizar DevOps Insights para controlar el despliegue de una aplicación sencilla de Cloud Foundry. De forma predeterminada, la cadena de herramientas utiliza una app de meteorología Node.js, pero puede enlazar con su propio repositorio GitHub. La cadena de herramientas ejecuta pruebas de unidad mediante Mocha y comprueba la cobertura de código mediante Istanbul.<br><br>
  Consulte la guía de aprendizaje: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain" target="_blank">Utilice la cadena de herramientas "Desarrollar y probar una app de Cloud Foundry" <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>  <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>Git Repos and Issue Tracking
  </li><li>{{site.data.keyword.DRA_full}}
  </li></ul>
  </td></tr>


  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fmicroservices-toolchain-hosted" target="_blank">
  Cadena de herramientas "Desarrollar y probar microservicios en Cloud Foundry" <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> <br><br>

  Disponible en EE.UU. sur, Alemania y Reino Unido

  </td><td>
  Con esta cadena de herramientas nativa de la nube puede utilizar una muestra para crear un almacén en línea compuesto por tres microservicios: una API de catálogo, una API de pedidos y una IU que realiza llamadas a ambas API. La cadena de herramientas está preconfigurada para entrega continua, control de código fuente, pruebas funcionales, seguimiento de problemas, edición en línea y notificación de alertas. <br><br>
  Consulte la guía de aprendizaje: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain" target="_blank">Utilice la cadena de herramientas "Desarrollar y probar microservicios en Cloud Foundry" <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a><br><br>
  </td><td>
  <ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub y problemas
  </li><li>{{site.data.keyword.Bluemix_notm}}
  </li><li>{{site.data.keyword.DRA_full}}
  </li><li>PagerDuty
  </li><li>Sauce Labs
  </li><li>Slack
  </li></ul>
 </td>
</tr>

  <tr>
  <td><a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fcloud-native-toolchain-tutorial" targe="_blank">
Cadena de herramientas "Guía de aprendizaje de Garage Method con Cloud Foundry" <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> <br><br>

  Disponible en EE.UU. sur, EE.UU. este, Alemania, Tokio y Reino Unido

</td><td>
Esta cadena de herramientas muestra prácticas de DevOps integradas en el método Garage. La cadena de herramientas está preconfigurada para entrega continua, control de código fuente, automatización de pruebas y para supervisión y operaciones automatizadas. Se suministra con una app de ejemplo escrita en Node.js Express 4, que puede ampliar. <br><br>Consulte el curso: <a href="https://www.ibm.com/cloud/garage/content/course/gm_advocate" target="_blank">Conviértase en un defensor de Garage Method <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>
</td><td>
<ul>
<li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion {{site.data.keyword.webide}}
</li><li>GitHub y problemas
</li><li>Google Analytics
</li><li>{{site.data.keyword.Bluemix_notm}}
</li><li>New Relic
</li><li>PagerDuty
</li><li>Sauce Labs
</li><li>Slack
</li></ul>
</td></tr>

<tr><td>
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fdevops-insights%2FDevOpsInsights_Demo_Toolchain_Template" target="_blank">Cadena de herramientas "Demo de inicio rápido de DevOps Insights" <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> <br><br>

  Disponible en EE.UU. sur, Alemania y Reino Unido

</td><td>
Con esta cadena de herramientas, puede explorar {{site.data.keyword.DRA_short}}, sin que sea necesario realizar ninguna configuración. Para empezar, inicie sesión en {{site.data.keyword.Bluemix}}. Esta demostración contiene datos de una cadena de herramientas de referencia y tres repositorios de GitHub. Explore cómo organizar, probar, crear y desplegar datos para todas las aplicaciones, desde todos los equipos, dentro del Panel de control de calidad. Evalúe las tendencias y conozca las áreas que necesitan mejoras, para saber dónde centrar sus recursos. Revise cómo colaboran los miembros del equipo por release dentro de Team Dynamics.<br><br>
Consulte la guía de aprendizaje: <a href="https://www.ibm.com/cloud/garage/tutorials/explore-ibm-cloud-devops-insights" target="_blank">Explore {{site.data.keyword.DRA_full}} <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> <br><br>
</td><td><ul><li>
GitHub y problemas
</li><li>{{site.data.keyword.DRA_full}}
</li></ul>
</td></tr>

<tr><td>
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fempty-toolchain" target="_blank">Cree su propia cadena de herramientas <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> <br><br>

  Disponible en EE.UU. sur, EE.UU. este, Alemania, Tokio y Reino Unido

</td><td>
Esta cadena de herramientas no tiene herramientas preconfiguradas. Si ya está familiarizado con las cadenas de herramientas, puede configurar su propia cadena de herramientas. <br><br>
Consulte la guía de aprendizaje: <a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">Cree una cadena de herramientas personalizada  <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>
</td><td> &nbsp;&nbsp; Ninguna
</td></tr>

<tr><td>Cadena de herramientas de Continuous Delivery <br><br>

 Disponible en EE.UU. sur, EE.UU. este, Alemania, Tokio y Reino Unido

</td><td>
Esta cadena se utiliza cuando se habilita la entrega continua en una app. <br><br>
Consulte las guías de aprendizaje:

<ul><li><a href="https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app" target="_blank">Añada una cadena de herramientas a una app <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a></li>
<li><a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">Cree una cadena de herramientas personalizada <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a></li>
</ul></td>
<td><ul><li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion {{site.data.keyword.webide}}
</li><li>
GitHub y problemas
</li>
<li>{{site.data.keyword.Bluemix_notm}}</li></ul>
</td></tr>

<tr><td>Plantilla de cadena de herramientas personalizada <br><br>

 Disponible en EE.UU. sur, EE.UU. este, Alemania, Tokio y Reino Unido

</td><td>
<br><br>
Puede crear una plantilla de cadena de herramientas personalizada que pueden utilizar otros usuarios. <br><br>

Consulte la documentación:
<a href="https://github.com/open-toolchain/sdk/wiki" target="_blank">Creación de plantillas de cadenas de herramientas personalizadas <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a>
 <br><br>
Consulte la guía de aprendizaje:
<a href="https://www.ibm.com/cloud/garage/tutorials/create-a-template-for-a-custom-toolchain" target="_blank">Cree una plantilla para una cadena de herramientas personalizado <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a></td>
<td>Ninguna
</td></tr>

</table>
