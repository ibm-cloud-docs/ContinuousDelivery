---

copyright:
  years: 2015, 2018
lastupdated: "2018-1-15"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Iniciación a la entrega continua
{: #cd_getting_started}

Puede adoptar un enfoque DevOps mediante {{site.data.keyword.contdelivery_full}}, que incluye cadenas de herramientas abiertas que automatizan la creación y despliegue de aplicaciones. Puede empezar creando una sencilla cadena de herramientas que dé soporte a las tareas de desarrollo, despliegue y operaciones.
{: shortdesc}

Después de crear una instancia de {{site.data.keyword.contdelivery_short}} seleccionándola en el catálogo de {{site.data.keyword.Bluemix_notm}}, puede crear una cadena de herramientas de entrega continua a partir de una plantilla o trabajar con cadenas de herramientas existentes.
 ![Página de bienvenida de Continuous Delivery](images/cd_landing_page2.png)

* Para crear y configurar una cadena de herramientas de entrega continua a partir de una plantilla, pulse **[Empezar aquí](#starting_from_a_toolchain_template)**. La cadena de herramientas integra herramientas para la planificación, despliegue de conductos y gestión de aplicaciones. Siempre puede añadir o eliminar herramientas de sus cadenas de herramientas.
* Si ya tiene cadenas de herramientas, en la sección "Inicio desde una plantilla de cadena de herramientas" pulse **Ver sus cadenas de herramientas**. Para obtener más información sobre cómo trabajar con cadenas de herramientas, consulte el apartado sobre [Utilización de cadenas de herramientas](/docs/services/ContinuousDelivery/toolchains_using.html){: new_window}.

##Visión
general de {{site.data.keyword.contdelivery_short}}
{: #cd_overview}

Con {{site.data.keyword.contdelivery_short}} puede crear, probar y entregar aplicaciones mediante las herramientas más utilizadas de la industria y prácticas de DevOps.
{:shortdesc}

El servicio {{site.data.keyword.contdelivery_short}} da soporte a los flujos de trabajo de DevOps:

 * Puede crear [cadenas de herramientas](/docs/services/ContinuousDelivery/toolchains_about.html){: new_window} abiertas integradas de DevOps para habilitar las integraciones de herramientas que dan soporte a las tareas de desarrollo, despliegue y operaciones.

  Una cadena de herramientas es un conjunto integrado de herramientas que sirve para desarrollar, crear, desplegar, probar y gestionar aplicaciones para repetir estas operaciones de forma cíclica de forma que se fácil gestionarlas. Las cadenas de herramientas pueden incluir herramientas de código abierto, servicios {{site.data.keyword.Bluemix_notm}} como [{{site.data.keyword.DRA_full}}](/docs/services/ContinuousDelivery/di_working.html){: new_window} y herramientas de terceros como GitHub, PagerDuty o Slack. 
  
  **Nota**: {{site.data.keyword.DRA_short}} está disponible sólo en la región EE.UU. Sur.

 * Entrega continua mediante [conductos](/docs/services/ContinuousDelivery/pipeline_about.html){: new_window} automatizados.

  Automatice compilaciones, pruebas de unidad, despliegues y más. Cree, pruebe y despliegue de manera repetitiva con una mínima intervención humana. Esté listo para pasar a producción en cualquier momento.

 * Edite y envíe el código desde cualquier lugar utilizando el [IDE basado en web](/docs/services/ContinuousDelivery/web_ide.html){: new_window}.

  Cree, edite, ejecute, depure y complete tareas de control de código fuente en GitHub. Puede pasar fácilmente de editar el código a desplegarlo en producción. 
  
 * Colabore con su equipo y gestione su código fuentes con [Git Repository and Issue Tracker](/docs/services/ContinuousDelivery/git_working.html#git_working){: new_window} alojado en IBM y que se basa en GitLab Community Edition.

  Gestione repositorios Git a través de controles de acceso precisos que mantienen el código seguro. Revise el código y mejore la colaboración mediante solicitudes de fusión. Realice un seguimiento de los problemas y comparta ideas mediante el rastreador de problemas. Documente sus proyectos con un sistema wiki.


##Inicio desde una plantilla de cadena de herramientas
{: #starting_from_a_toolchain_template}

Para crear y configurar una cadena de herramientas de entrega continua desde una [plantilla ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/devops/create){: new_window}:

1. En la página **Crear una cadena de herramientas**, pulse una plantilla de cadena de herramientas.
1. Revise el diagrama de la cadena de herramientas que se dispone a crear. El diagrama muestra cada integración de herramientas en la fase del ciclo de vida correspondiente en la cadena de herramientas.

 **Consejo**: Algunas de las plantillas de cadena de herramientas tienen varias instancias de una integración de herramientas. Por ejemplo, la plantilla de la cadena de herramientas de microservicios de {{site.data.keyword.Bluemix_notm}} público contiene tres instancias de GitHub y tres instancias de Delivery Pipeline, una para cada uno de los tres microservicios.

 El diagrama de la imagen siguiente es un ejemplo. Cuando cree una cadena de herramientas, el diagrama mostrará cada integración de herramientas que forma parte de la cadena de herramientas.
 ![Diagrama_cadena_herramientas](images/toolchain_diagram2.png)
1. Revise la información predeterminada de los valores de la cadena de herramientas:

 * El nombre de la cadena de herramientas la identifica en {{site.data.keyword.Bluemix_notm}}. Si desea utilizar otro nombre, cambie el nombre de la cadena de herramientas.
 * La región en la que se va crear la cadena de herramientas. Si desea utilizar otra región, selecciónela en la lista de regiones disponibles.
 * La organización en la que se va crear la cadena de herramientas. Si desea utilizar una organización diferente, selecciónela en la lista de organizaciones disponibles.
 
1. En la sección Integraciones de herramientas, seleccione las integraciones de herramientas que desee configurar para su cadena de herramientas. Algunas integraciones de herramientas no necesitan configuración. Para obtener información sobre cómo configurar las integraciones de herramientas, consulte [Configurar integraciones de herramientas](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}.
1. Pulse **Crear**. Para configurar la cadena de herramientas, se ejecutan varios pasos automáticamente. Las integraciones de herramientas que se configuran varían en función de la plantilla de cadena de herramientas que haya seleccionado y de si utiliza {{site.data.keyword.Bluemix_notm}} público o {{site.data.keyword.Bluemix_notm}} dedicado. Por ejemplo, si crea una cadena de herramientas de microservicios en {{site.data.keyword.Bluemix_notm}} público, se ejecutan estos pasos:

 * Se crea la cadena de herramientas.
 * Si ha configurado Delivery Pipeline, los conductos se crean y se activan.
 * Si ha configurado Sauce Labs, la cadena de herramientas se configura para añadir trabajos de prueba de Sauce Labs a los conductos.
 * Si ha configurado PagerDuty, la cadena de herramientas se configura para enviar notificaciones de alerta al servicio de PagerDuty que ha especificado.
 * Si ha configurado Slack, la cadena de herramientas se configura para enviar notificaciones sobre el estado de despliegue al canal Slack que ha especificado.
 * Si ha configurado la integración de una herramienta de código fuente como GitHub, el repositorio de ejemplo de GitHub se clona en su cuenta de GitHub.
