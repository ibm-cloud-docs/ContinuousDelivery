---

copyright:
  years: 2016, 2017
lastupdated: "2017-5-17"
---
<!-- Copyright info at top of file: REQUIRED
    The copyright info is YAML content that must occur at the top of the MD file, before attributes are listed.
    It must be surrounded by 3 dashes.
    The value "years" can contain just one year or a two years separated by a comma. (years: 2014, 2016)
    Indentation as per the previous template must be preserved.
-->

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Limitaciones y uso del plan
{: #deliverypipeline_plans}
{: #free_deprecation}

El uso de {{site.data.keyword.contdelivery_full}} está limitado a la creación, despliegue, prueba y operaciones en curso de aplicaciones en la plataforma {{site.data.keyword.Bluemix_notm}} o en otras ofertas compatibles de plataforma como servicio o de infraestructura como servicio.

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

## Servicios en desuso
{: #deprecated_services}

{{site.data.keyword.trackplan}} y {{site.data.keyword.deliverypipeline}} Classic, que son parte de IBM Bluemix {{site.data.keyword.jazzhub_short}} (JazzHub), están siendo retirados. Para obtener más información, consulte [Retirada de Track & Plan ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/blogs/bluemix/2017/04/track-plan-retirement/){: new_window} y [Retirada de Delivery Pipeline ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/blogs/bluemix/2017/04/delivery-pipeline-retirement/){: new_window}.

Desde el 25 de mayo, ya no era posible crear proyectos de JazzHub. A través de las actualizaciones de despliegues automatizados, los proyectos JazzHub se actualizarán a cadenas de herramientas {{site.data.keyword.contdelivery_short}}. 
El sitio de JazzHub será eliminado a principios de Julio. Para obtener más información sobre la actualización, consulte [Actualización de proyectos JazzHub a cadenas de herramientas Bluemix Continuous Delivery ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/devops-services/2017/4/18/upgrading-jazzhub-projects-bluemix-continuous-delivery-toolchains/){: new_window}
