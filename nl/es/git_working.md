---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-20"

keywords: Git Repos, Issue Tracking, Collaborate, Git repository

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# {{site.data.keyword.gitrepos}}
{: #git_working}

Colabore con su equipo y gestione su código fuente con un repositorio Git (repositorio) y un rastreador de problemas alojado en IBM que se basa en [GitLab Community Edition](https://about.gitlab.com/){: external}.
{: shortdesc}

Invitar solo a los usuarios con los que tiene una relación personal o empresarial para colaborar en un proyecto. Es posible que el acceso al servicio se suspenda o revoque para los usuarios que utilicen una invitación a un repositorio Git para fines que no sean colaborar en un proyecto.
{: important}

Tanto GitHub como la línea de mandatos de Git son alternativas accesibles a GitLab.
{: note}

No almacene datos regulados en archivos o problemas en el repositorio Git. Actualmente, los procedimientos para los datos regulados no están en vigor.
{: tip}

La integración de la herramienta {{site.data.keyword.gitrepos}} permite a los equipos gestionar código y colaborar de varias formas:
   * Gestionar repositorios Git a través de controles de acceso que mantienen el código seguro
   * Revisar el código y mejorar la colaboración mediante solicitudes de fusión
   * Hacer un seguimiento de problemas y compartir ideas mediante el rastreador de problemas
   * Documentar proyectos en el sistema de wiki

Dado que esta integración de herramientas se basa en GitLab Community Edition y está alojada en IBM en la plataforma {{site.data.keyword.Bluemix_notm}}, algunas opciones de GitLab no están disponibles. Por ejemplo, Delivery Pipeline proporciona integración continua y entrega continua para {{site.data.keyword.Bluemix_notm}}; por lo tanto, las funciones de integración continua de GitLab no reciben soporte. Además, las funciones de administración no están disponibles las gestiona IBM.
{: tip}


## Uso de {{site.data.keyword.gitrepos}} de forma local
{: #git_locally}

Puede acceder localmente a los repositorios Git almacenados en {{site.data.keyword.gitrepos}}. Para obtener instrucciones sobre cómo configurar Git de manera local, consulte
[Empezar a utilizar Git en la línea de mandatos](https://us-south.git.cloud.ibm.com/help/gitlab-basics/start-using-git){: external}.

{{site.data.keyword.gitrepos}} da soporte únicamente a conexiones HTTPS que utilicen TLS1.2. Si utiliza Eclipse para conectarse, podría necesitar especificar este protocolo para su versión de Java añadiendo `-Dhttps.protocols=TLSv1.2` a su archivo eclipse.ini y, a continuación, reiniciar Eclipse.
{: tip}

## Autenticación con {{site.data.keyword.gitrepos}}
{: #git_authentication}

El inicio de sesión y la contraseña de {{site.data.keyword.Bluemix_notm}} sólo se utilizan para autenticarse con {{site.data.keyword.gitrepos}} en un navegador web. No es posible utilizar sus credenciales de usuario de {{site.data.keyword.Bluemix_notm}} para autenticarse desde clientes Git externos. Para realizar operaciones Git remotas, como `clone` o `push`, desde su repositorio local de Git, debe utilizar una señal de acceso personal o una clave SSH para autenticarse con {{site.data.keyword.gitrepos}}.

### Creación de una señal de acceso personal
{: #create_pat}

Para autenticarse en el repositorio Git a través de HTTPS, debe crear una señal de acceso personal.
{: tip}

1. En el panel de control de Valores de usuario de {{site.data.keyword.gitrepos}}, en la
[página Señales de acceso](https://us-south.git.cloud.ibm.com/profile/personal_access_tokens){: external}, escriba el nombre de la aplicación para la que desee crear una señal de acceso. Por ejemplo, `Git CLI`.
1. Opcional: Elija una fecha de caducidad para la señal de acceso.
1. Seleccione el recuadro de selección **api** para crear una señal de acceso personal que utilice como ámbito a la api.
1. Pulse **Crear señal de acceso personal**. Conserve su señal de acceso en una ubicación segura para utilizarla en el futuro.
1. En la [página Cuenta](https://us-south.git.cloud.ibm.com/profile/account){: external}, en la sección Cambiar nombre de usuario, busque su nombre de usuario de {{site.data.keyword.gitrepos}}. El nombre de usuario también se visualiza como el primer segmento del URL para cualquier repositorio Git personal que cree.
1. Utilice su nombre de usuario y contraseña de {{site.data.keyword.gitrepos}} y la señal de acceso personal con su repositorio Git desde un cliente Git externo.

Para obtener más información, consulte
[Señales de acceso personal](https://us-south.git.cloud.ibm.com/help/api/README.html#personal-access-tokens){: external}.

### Creación de una clave SSH  
{:create_ssh }

Para crear una clave SSH, consulte [Cómo crear claves SSH](https://us-south.git.cloud.ibm.com/help/gitlab-basics/create-your-ssh-keys){: external}. Para acceder a los repositorios con autenticación SSH es posible que se requiera configuración adicional para proxies y cortafuegos.

Para obtener más información, consulte [SSH](https://us-south.git.cloud.ibm.com/help/ssh/README){: external}.

## Límites en el tamaño de archivos y repositorios físicos
{: #git_limits}

Los archivos están estrictamente limitados a 100 MB. El límite recomendado de tamaño de repositorios es 1 GB. Si el repositorio supera 1 GB, es posible que reciba un mensaje de correo electrónico con una solicitud para reducir el tamaño del repositorio.

## Guía de aprendizaje: {{site.data.keyword.gitrepos}}
{: #git_tutorials}

Consulte una de estas guías de aprendizaje sobre [IBM&reg; Cloud Garage Method](https://www.ibm.com/cloud/garage){: external}:

  * [Cree y utilice su primera cadena de herramientas utilizando la cadena de herramientas "Desarrollar una app de Cloud Foundry"](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){: external}. Aprenda a crear una cadena de herramientas abierta a partir de una plantilla y a utilizar la cadena de herramientas para conseguir una entrega continua de la app "Hello World".

  * [Utilice la cadena de herramientas "Desarrollar y probar microservicios en Cloud Foundry"](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){: external}. Aprenda a crear una cadena de herramientas a partir de una plantilla con tres microservicios y a utilizar la cadena de herramientas para conseguir una entrega continua de un almacén en línea.
