---

copyright:
  years: 2016, 2018
lastupdated: "2018-7-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Limitaciones y uso del plan
{: #limitations_usage}

El uso de {{site.data.keyword.contdelivery_full}} está limitado a la creación, despliegue, prueba y operaciones en curso de aplicaciones en la plataforma {{site.data.keyword.Bluemix_notm}} o en otras ofertas compatibles de plataforma como servicio o de infraestructura como servicio.

## Usuarios autorizados
{: #authorized_users}

Los planes de servicio de {{site.data.keyword.contdelivery_short}} y sus precios se definen con base en el número de usuarios autorizados de una instancia de servicio. Cualquier persona que participe en una tarea se debe contar como usuario autorizado, incluidos:

 * Los usuarios que interactúan con problemas, paneles de problemas, código fuente u otros artefactos en un repositorio de {{site.data.keyword.gitrepos}}.
 * Los usuarios que manipulan, activan (directamente en la interfaz de usuario o indirectamente al confirmar un repositorio) o ven el estado de un conducto de entrega.
 * Los usuarios que interactúan con Eclipse Orion {{site.data.keyword.webide}}.
 
### ¿Cómo se cuentan los usuarios para instancias de {{site.data.keyword.contdelivery_short}} en organizaciones?

Los usuarios autorizados se cuentan teniendo en cuenta todos los usuarios de la organización de la nube (org) que contiene el servicio de {{site.data.keyword.contdelivery_short}}. 

Para ver la lista de usuarios de la organización en un entorno de {{site.data.keyword.Bluemix_notm}} público, desde la barra de menús, pulse **Gestionar > Cuenta > Organizaciones de Cloud Foundry**.

Para ver la lista de usuarios de su organización en un entorno dedicado de {{site.data.keyword.Bluemix_notm}}, desde la barra de menús, pulse **Cuenta > Gestionar organizaciones**.

También puede ver todas las instancias del servicio de {{site.data.keyword.contdelivery_short}} de la cuenta y el número de usuarios que se notifican en cada instancia en un entorno de {{site.data.keyword.Bluemix_notm}} público.

1. En la barra de menús, pulse **Gestionar > Facturación y uso > Uso**.
2. Pulse **Panel de control de uso**.
3. En el menú Cuenta, pulse **Organizaciones de Cloud Foundry**.
4. Pulse la organización para la que desea ver información de uso.

Para ver todas las instancias del servicio {{site.data.keyword.contdelivery_short}} en su cuenta y el número de usuarios que se notifican en cada instancia en un entorno dedicado de {{site.data.keyword.Bluemix_notm}}:

1. En la barra de menús, pulse **Cuenta > Gestionar organizaciones**.
2. Pulse **Panel de control de uso**.

### ¿Cómo se cuentan los usuarios para las instancias de {{site.data.keyword.contdelivery_short}} en grupos de recursos?

Los usuarios autorizados se cuentan teniendo en cuenta la lista de usuarios del separador Gestionar dentro de la instancia de servicio de {{site.data.keyword.contdelivery_short}}. 

Para ver la lista de usuarios autorizados, abra el panel de control de la instancia de servicio y pulse el separador Gestionar.

También puede ver todas las instancias del servicio de {{site.data.keyword.contdelivery_short}} de la cuenta y el número de usuarios notificados en cada instancia.

1. En la barra de menús, pulse **Gestionar > Facturación y uso > Uso**.
2. Pulse **Panel de control de uso**.
3. En el menú Cuenta, pulse **Grupos de recursos**.
4. Pulse el grupo de recursos para el que desea ver información de uso.

### ¿Qué ocurre cuando se superan los límites del plan de servicio? 

Algunos planes de servicio podrían tener otras limitaciones, como por ejemplo el número de trabajos de Delivery Pipeline que pueden ejecutarse o el consumo de almacenamiento. Para obtener más información, consulte la descripción del plan en el catálogo. Si se supera cualquiera de las limitaciones del plan en un período de facturación, el servicio se puede suspender. Por ejemplo, los trabajos de Delivery Pipeline podrían no ejecutarse durante el resto del período de facturación.

## Uso de Delivery Pipeline
{: #pipeline_usage}

Los comportamientos aceptables de uso incluyen los siguientes, aunque no se limitan a los mismos:

* La compilación y el ensamblaje de artefactos para los lenguajes de programación admitidos
* El despliegue automático de artefactos de aplicación, configuraciones y recursos o servicios de soporte
* La prueba, validación y otros comportamientos generados por sucesos de desarrollo que se activen como resultado del proceso de desarrollo

Los comportamientos de uso no permitidos incluyen estos comportamientos, aunque no se limitan a los mismos:

* El uso de trabajos o trabajadores de conductos para comportamientos generales de cálculo, como minería de Bitcoin, ataques distribuidos de tipo denegación de servicio y comportamiento malicioso u ofensivo para otros clientes o usuarios de la plataforma IBM Cloud o usuarios de Internet general
* El uso, en el proceso de desarrollo normal, de sitios o servicios que promuevan discursos que ensalcen el odio u otras actividades que violen las directrices de conducta empresarial de IBM
* El uso de comportamiento generado por sucesos relacionado con intrusiones maliciosas o ataques contra {{site.data.keyword.Bluemix_notm}} u otros sitios

A discreción de IBM, los usuarios que vulneren los comportamientos aceptables de uso de los servicios de {{site.data.keyword.contdelivery_short}} o [directrices de conducta empresarial de IBM ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){: new_window} pueden quedar inhabilitados sin previo aviso. A discreción de IBM, algunos servicios se pueden restaurar si los usuarios corrigen sus comportamientos de uso después de recibir una notificación de acción ofensiva. Si no es así, las cuentas pueden quedar suspendidas o se pueden cancelar.

## Limitaciones en Git Repos and Issue Tracking
{: #git_limitations}

{{site.data.keyword.gitrepos}} se basa en GitLab Community Edition que IBM aloja en {{site.data.keyword.Bluemix_notm}}, sin embargo, algunas opciones de GitLab no están disponibles:

 * Puesto que {{site.data.keyword.deliverypipeline}} proporciona integración continua y entrega continua para {{site.data.keyword.Bluemix_notm}}, no se da soporte a las funciones de integración continua de GitLab.
 * Las funciones de administración de GitLab no están disponibles porque IBM las gestiona.
 * {{site.data.keyword.gitrepos}} podría no ser totalmente accesible.

## Contenido e información de usuario de Git Repos and Issue Tracking
{: #git_projects}

Hay disponibles tres tipos de proyectos {{site.data.keyword.gitrepos}}:

  1. Los proyectos públicos son visibles a todos los visitantes del sitio. El contenido en un proyecto público es visible para todo el mundo que acceda a {{site.data.keyword.contdelivery_short}}, incluso si no han sido invitados al proyecto.
  2. Los proyectos privados únicamente son visibles a usuarios seleccionados. Para obtener información detallada sobre cómo otorgar acceso al proyecto a los usuarios, consulte [Usuarios de proyecto ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://git.ng.bluemix.net/help/workflow/add-user/add-user.md){: new_window}.
  3. Los proyectos internos son visibles a todos los usuarios que han iniciado una sesión. Cualquier usuario con una cuenta de {{site.data.keyword.Bluemix_notm}} podrá ver estos proyectos.

Puede modificar el tipo de proyecto en los valores del proyecto. Para obtener más información, consulte [Cómo cambiar la visibilidad de un proyecto ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://git.ng.bluemix.net/help/public_access/public_access#how-to-change-project-visibility){: new_window}.

Cuando se utiliza {{site.data.keyword.gitrepos}}, el contenido con el que contribuye al proyecto se licencia bajo todos los términos especificados en dicho proyecto. Cuando crea un proyecto, incluya un archivo que describa la licencia que se aplica al contenido. Cuando contribuye a un proyecto, su nombre y la dirección de correo electrónica asociada con sus confirmaciones podría ser visible de forma pública. Al crear confirmaciones a través de la interfaz web de {{site.data.keyword.gitrepos}} se utilizará la dirección de correo electrónica asociada a su cuenta de {{site.data.keyword.Bluemix_notm}}.

<!-- ###Privacy with Git Repos and Issue Tracking profiles -->

<!-- A few features of {{site.data.keyword.gitrepos}} require the use of a profile page that publicly displays information that you provide. You give IBM the following permissions: -->

  <!-- a. Make the information in your profile&mdash;such as your name, email, picture, bio, social media links, and user activity&mdash;visible to other users of the service. -->

  <!-- b. Publicly disclose your name and other public information and activities that are associated with your use of the service, or otherwise publicize the fact that you are a user of the service, without any further notice to you. -->

<!-- The email address that is associated with your profile page is derived from your {{site.data.keyword.Bluemix_notm}} account details. To modify the email address that is displayed on your profile page, modify your {{site.data.keyword.Bluemix_notm}} account. -->

<!-- ## Deprecated services
{: #deprecated_services} -->

<!--{{site.data.keyword.trackplan}} and {{site.data.keyword.deliverypipeline}} Classic, which are part of IBM Bluemix {{site.data.keyword.jazzhub_short}} (JazzHub), are being retired. For more information, see [Track & Plan Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/track-plan-retirement/){: new_window} and [Delivery Pipeline Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/delivery-pipeline-retirement/){: new_window}. -->

<!-- Starting on May 25, no new JazzHub projects can be created. Through automatic rolling upgrades, JazzHub projects will be upgraded to {{site.data.keyword.contdelivery_short}} toolchains. The JazzHub site will be removed from service in early July. For more information about the upgrade, see [Upgrading JazzHub project to Bluemix Continuous Delivery toolchains ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/devops-services/2017/4/18/upgrading-jazzhub-projects-bluemix-continuous-delivery-toolchains/){: new_window} -->
