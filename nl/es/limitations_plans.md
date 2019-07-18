---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-27"

keywords: users of a service instance, a-service, Git Repos

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}


# Limitaciones y uso del plan
{: #limitations_usage}

El uso de {{site.data.keyword.contdelivery_full}} está limitado a la creación, despliegue, prueba y operaciones en curso de aplicaciones en la plataforma {{site.data.keyword.Bluemix_notm}} o en otras ofertas compatibles de plataforma como servicio o de infraestructura como servicio.

## Ámbito de una instancia de servicio
{: #service_scope}

Debe tener una [instancia de servicio](https://cloud.ibm.com/catalog/services/continuous-delivery){:external} de {{site.data.keyword.contdelivery_short}} para poder crear y utilizar cadenas de herramientas de DevOps. Una instancia de servicio puede pertenecer a un [grupo de recursos](/docs/services/resources?topic=resources-rgs) de {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) o a una organización de {{site.data.keyword.Bluemix_notm}} (org).

Puede crear *nuevas* instancias del servicio {{site.data.keyword.contdelivery_short}} únicamente en grupos de recursos. Actualmente no hay soporte para la migración de cadenas de herramientas de organizaciones a grupos de recursos. Si le falta servicio {{site.data.keyword.contdelivery_short}} para una organización que contiene cadenas de herramientas, puede crear de nuevo las cadenas de herramientas en un grupo de recursos o ponerse en contacto con el [Soporte de IBM](https://cloud.ibm.com/unifiedsupport){:external} para obtener ayuda.

Solo puede tener un servicio Lite por cuenta. Se recomienda que utilice el plan Profesional si desea trabajar con cadenas de herramientas en varias organizaciones o grupos de recursos, o dentro de varias regiones.
{: tip}


## Usuarios autorizados
{: #authorized_users}

Los [planes de servicio](https://cloud.ibm.com/catalog/services/continuous-delivery){:external} de {{site.data.keyword.contdelivery_short}} y sus precios se definen en función del número de usuarios autorizados de una instancia de servicio. Cualquier persona que participe en una tarea se debe contar como usuario autorizado, incluidos:

 * Los usuarios que interactúan con problemas, paneles de problemas, código fuente u otros artefactos en un repositorio de {{site.data.keyword.gitrepos}}.
 * Los usuarios que manipulan, activan (directamente en la interfaz de usuario o indirectamente al confirmar un repositorio) o ven el estado de un conducto de entrega.
 * Los usuarios que interactúan con Eclipse Orion {{site.data.keyword.webide}}.
 
El plan Lite está sujeto a limitaciones. Para obtener más información sobre el plan Lite y el plan Profesional, consulte el [catálogo de servicios](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}.
{: tip}
 
### ¿Cómo se cuentan los usuarios para las instancias de {{site.data.keyword.contdelivery_short}} en grupos de recursos?

Se cuentan y gestionan los usuarios autorizados para cada instancia de servicio mirando la lista de usuarios autorizados para ver la facturación y los límites del plan Lite. Los usuarios del servicio {{site.data.keyword.contdelivery_short}} se añaden automáticamente a esta lista. Puede evitar que los usuarios accedan a las cadenas de herramientas y se añadan automáticamente a una instancia del servicio {{site.data.keyword.contdelivery_short}}. Para obtener más información sobre cómo utilizar IAM para eliminar el acceso de usuario del Grupo de recursos que contiene la cadena de herramientas (o de la propia cadena de herramientas), consulte [Gestión del acceso de usuario a {{site.data.keyword.contdelivery_short}} con Identity and Access Management](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security). 

El método que utilice para organizar las cadenas de herramientas dentro de los grupos de recursos afectará directamente al acceso de usuario y a la facturación. Cuando un usuario utiliza cadenas de herramientas en varios grupos de recursos, se cuentan y se facturan para cada servicio de dichos grupos de recursos.
{: tip}

Puede gestionar la lista de usuarios autorizados en el separador **Gestionar** de la instancia del servicio {{site.data.keyword.contdelivery_short}}.

1. Vaya a la [Lista de recursos](https://cloud.ibm.com/resources){:external} de su cuenta de {{site.data.keyword.Bluemix_notm}}.
2. En la columna **Nombre**, en el recuadro de texto de filtro, escriba **Entrega continua** para mostrar los servicios existentes.
3. Para cada servicio, pulse el hiperenlace de la columna **Nombre**.
4. En el separador **Gestionar**, puede ver, añadir o eliminar usuarios de la lista de usuarios autorizados, según sea necesario.

Los usuarios se añadirán automáticamente o se volverán a añadir cuando utilicen el servicio {{site.data.keyword.contdelivery_short}}.
{: tip}

### ¿Cómo se cuentan los usuarios para instancias de {{site.data.keyword.contdelivery_short}} en organizaciones?

Los usuarios autorizados se cuentan examinando todos los usuarios de la organización de {{site.data.keyword.Bluemix_notm}} que contiene el servicio {{site.data.keyword.contdelivery_short}}. Para obtener más información sobre organizaciones y espacios, consulte [Creación de organizaciones y espacios](/docs/cloud-foundry?topic=cloud-foundry-create_orgs).

Para ver la lista de usuarios de la organización en un entorno de {{site.data.keyword.Bluemix_notm}} público, desde la barra de menús, pulse **Gestionar > Cuenta**. A continuación, pulse **Organizaciones de Cloud Foundry**.

### ¿Cómo puede ver la información de facturación y uso?

Puede ver todas las instancias del servicio de {{site.data.keyword.contdelivery_short}} de la cuenta y el número de usuarios y ejecuciones del conducto que se notifican en cada instancia en un entorno de {{site.data.keyword.Bluemix_notm}} público.

1. En la barra de menús, pulse **Gestionar > Facturación y uso**.
2. Pulse **Uso**.
3. En la sección **Servicios**, pulse **Ver planes** para el servicio de {{site.data.keyword.contdelivery_short}}.
4. Pulse **Ver detalles** para ver el plan sobre el que desea ver información.
5. Pulse **Ver detalles de instancia** para ver la instancia de {{site.data.keyword.contdelivery_short}} cuya información de uso desea ver.

La métrica `AUTHORIZED_USERS_PER_MONTH` se calcula en base al promedio mensual de usuarios que se cuentan diariamente. 
{: tip}

### ¿Qué ocurre cuando se superan los límites del plan de servicio?

El plan de servicio Lite tiene otras limitaciones, como el número de trabajos de Delivery Pipeline que se pueden ejecutar o el consumo de almacenamiento. Para obtener más información sobre la descripción del plan, consulte el [catálogo de servicios](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}. Si se supera cualquiera de las limitaciones del plan en un período de facturación, el servicio se suspenderá. Por ejemplo, los trabajos de Delivery Pipeline podrían no ejecutarse durante el resto del periodo de facturación.

## Uso de Delivery Pipeline
{: #pipeline_usage}

Los comportamientos aceptables de uso incluyen los siguientes, aunque no se limitan a los mismos:

* La compilación y el ensamblaje de artefactos para los lenguajes de programación admitidos.
* El despliegue automático de artefactos de aplicación, configuraciones y recursos o servicios de soporte.
* La prueba, validación y otros comportamientos generados por sucesos de desarrollo que se activen como resultado del proceso de desarrollo.

Los comportamientos de uso no permitidos incluyen estos comportamientos, aunque no se limitan a los mismos:

* El uso de trabajos o trabajadores de conductos para comportamientos generales de cálculo, como minería de Bitcoin, ataques distribuidos de tipo denegación de servicio y comportamiento malicioso u ofensivo para otros clientes o usuarios de la plataforma {{site.data.keyword.Bluemix_notm}} o usuarios de Internet general.
* El uso, en el proceso de desarrollo normal, de sitios o servicios que promuevan discursos que ensalcen el odio u otras actividades que violen las directrices de conducta empresarial de IBM.
* El uso de comportamiento generado por sucesos relacionado con intrusiones maliciosas o ataques contra {{site.data.keyword.Bluemix_notm}} u otros sitios.

A discreción de IBM, los usuarios que vulneren los comportamientos aceptables de uso de los servicios de {{site.data.keyword.contdelivery_short}} o [directrices de conducta empresarial de IBM](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){:external} pueden quedar inhabilitados sin previo aviso. A discreción de IBM, algunos servicios se pueden restaurar si los usuarios corrigen sus comportamientos de uso después de recibir una notificación de acción ofensiva. Si no es así, las cuentas pueden quedar suspendidas o se pueden cancelar.

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
  2. Los objetos privados son visibles solo para los usuarios seleccionados. Para obtener más información sobre cómo otorgar a los usuarios acceso a un proyecto, consulte [Usuarios del proyecto](https://us-south.git.cloud.ibm.com/help/user/project/members/index.md){:external}.
  3. Los proyectos internos son visibles a todos los usuarios que han iniciado una sesión. Cualquier usuario con una cuenta de {{site.data.keyword.Bluemix_notm}} podrá ver estos proyectos.

Puede modificar el tipo de proyecto en los valores del proyecto. Para obtener más información sobre los valores del proyecto, consulte [Cómo cambiar la visibilidad de un proyecto](https://us-south.git.cloud.ibm.com/help/public_access/public_access#how-to-change-project-visibility){:external}.

Cuando se utiliza {{site.data.keyword.gitrepos}}, el contenido con el que contribuye al proyecto se licencia bajo todos los términos especificados en dicho proyecto. Cuando crea un proyecto, incluya un archivo que describa la licencia que se aplica al contenido. Cuando contribuye a un proyecto, su nombre y la dirección de correo electrónica asociada con sus confirmaciones podría ser visible de forma pública. Al crear confirmaciones a través de la interfaz web de {{site.data.keyword.gitrepos}} se utilizará la dirección de correo electrónica asociada a su cuenta de {{site.data.keyword.Bluemix_notm}}.
