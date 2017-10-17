---

copyright:
  years: 2015, 2017
lastupdated: "2017-6-8"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:screen:.screen}
{:codeblock:.codeblock}

# {{site.data.keyword.gitrepos}}
{: #git_working}

Colabore con su equipo y gestione su código fuente con un repositorio Git (repositorio) y un rastreador de problemas alojado en IBM que se basa en [GitLab Community Edition ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://about.gitlab.com/){:new_window}.
{: shortdesc}

La integración de la herramienta {{site.data.keyword.gitrepos}} permite a los equipos gestionar código y colaborar de varias formas:
   * Gestionar repositorios Git a través de controles de acceso que mantienen el código seguro
   * Revisar el código y mejorar la colaboración mediante solicitudes de fusión
   * Hacer un seguimiento de problemas y compartir ideas mediante el rastreador de problemas
   * Documentar proyectos en el sistema de wiki

**Nota:** Dado que esta integración de herramientas se basa en GitLab Community Edition y está alojada en IBM en Bluemix, algunas opciones de GitLab no están disponibles. Por ejemplo, Delivery Pipeline proporciona integración continua y entrega continua para Bluemix; por lo tanto, las funciones de integración continua de GitLab no reciben soporte. Además, las funciones de administración no están disponibles las gestiona IBM.

## Uso de {{site.data.keyword.gitrepos}} de forma local
{: #git_local}

Puede acceder localmente a los repositorios Git almacenados en {{site.data.keyword.gitrepos}}. Para ver instrucciones sobre cómo configurar Git localmente, consulte [Empezar a utilizar Git en la línea de mandatos ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://git.ng.bluemix.net/help/gitlab-basics/start-using-git){:new_window}.

**Sugerencia**: {{site.data.keyword.gitrepos}} da soporte únicamente a conexiones HTTPS que utilicen TLS1.2. Si utiliza Eclipse para conectarse, podría necesitar especificar este protocolo para su versión de Java añadiendo `-Dhttps.protocols=TLSv1.2` a su archivo eclipse.ini y, a continuación, reiniciar Eclipse.

## Autenticación con {{site.data.keyword.gitrepos}}  
{: #git_authentication}

El inicio de sesión y la contraseña de {{site.data.keyword.Bluemix_notm}} sólo se utilizan para autenticarse con {{site.data.keyword.gitrepos}} en un navegador web. No es posible utilizar sus credenciales de usuario de {{site.data.keyword.Bluemix_notm}} para autenticarse desde clientes Git externos. Para realizar operaciones Git remotas, como `clone` o `push`, desde su repositorio local de Git, debe utilizar una señal de acceso personal o una clave SSH para autenticarse con {{site.data.keyword.gitrepos}}.

### Creación de una señal de acceso personal
{: #create_pat}

**Importante**: Para autenticarse en el repositorio Git a través de HTTPS, debe crear una señal de acceso personal.

1. En el panel de control de Valores de usuario de {{site.data.keyword.gitrepos}}, en la [página de Señales de acceso ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://git.ng.bluemix.net/profile/personal_access_tokens?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window}, escriba su nombre de su aplicación para la que desea crear una señal de acceso. Por ejemplo, `Git CLI`.
1. Opcional: Elija una fecha de caducidad para la señal de acceso.
1. Seleccione el recuadro de selección **api** para crear una señal de acceso personal que utilice como ámbito a la api.
1. Pulse **Crear señal de acceso personal**. Conserve su señal de acceso en una ubicación segura para utilizarla en el futuro.
1. En la [página de Cuenta ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://git.ng.bluemix.net/profile/account?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window}, en la sección de Cambiar nombre de usuario, busque su nombre de usuario de {{site.data.keyword.gitrepos}}. El nombre de usuario también se visualiza como el primer segmento del URL para cualquier repositorio Git personal que cree.
1. Utilice su nombre de usuario y contraseña de {{site.data.keyword.gitrepos}} y la señal de acceso personal con su repositorio Git desde un cliente Git externo.

Para obtener más información, consulte [Señales de acceso personal ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://git.ng.bluemix.net/help/api/README.html#personal-access-tokens){:new_window}.

### Creación de una clave SSH  
{:create_ssh }

Para crear una clave SSH, consulte [Cómo crear claves SSH ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://git.ng.bluemix.net/help/gitlab-basics/create-your-ssh-keys){:new_window}. Para acceder a los repositorios con autenticación SSH es posible que se requiera configuración adicional para proxies y cortafuegos.

Para obtener más información, consulte [SSH ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://git.ng.bluemix.net/help/ssh/README){:new_window}.

## Límites en el tamaño de archivos y repositorios
{: #git_limits}

Los archivos están estrictamente limitados a 100 MB. El límite recomendado de tamaño de repositorios es 1 GB. Si el repositorio supera 1 GB, es posible que reciba un mensaje de correo electrónico con una solicitud para reducir el tamaño del repositorio.

## Guía de aprendizaje: {{site.data.keyword.gitrepos}}
{: #git_tutorials}

Consulte uno de estas guías de aprendizaje en [IBM&reg; Cloud Garage Method ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/devops/method){:new_window}:

  * [Cree una cadena de herramientas que utiliza {{site.data.keyword.gitrepos}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_cfv2){:new_window}
  * [Cree y utilice una cadena de herramientas con DevOps Insights (v2) ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/devops/method/tutorials/tutorial_toolchain_microservices_cd){:new_window}
