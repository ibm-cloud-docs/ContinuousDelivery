---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-26"

keywords: Git source control, personal access token, Git repos

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Configuración de clientes locales para trabajar con el control de origen de Git
{: #git_local}


Puede gestionar y trabajar con el código fuente en un GitHub, GitHub Enterprise o el repositorio (repo) de {{site.data.keyword.gitrepos}}, localmente o en Eclipse Orion {{site.data.keyword.webide}}. Para trabajar localmente, clone el repositorio con un cliente de Git como por ejemplo la interfaz de línea de mandatos de Git y edite el código con su editor favorito. Si trabaja en Eclipse, puede instalar el plug-in de EGit para el control de versiones.

## Clonar el proyecto de Git desde la línea de mandatos


## Antes de empezar
{: #git_before_clone}

1. Para acceder al servidor Git fuera del navegador, debe crear una señal de acceso personal o una clave SSH para la autenticación. La tabla siguiente muestra lo que debe hacer para configurar la autenticación.

| Tipo de Git  | Configuración HTTPS | Uso de HTTPS |  Configuración de SSH |
|:-----------|:-------------|:------------|:-------------|
| Git Repos and Issue Tracking  | [Señal de acceso personal](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat) | Nombre de usuario de Git Repos and Issue Tracking (no su ID de IBM) y señal de acceso personal | [Configure la clave SSH](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#creating-an-ssh-key) |
| GitHub pública (github.com) | La señal de acceso personal no es necesaria, pero puede configurar una y utilizarla | Nombre de usuario y contraseña de GitHub, o nombre de usuario de GitHub y señal de Acceso personal, o sólo la señal de acceso personal como nombre de usuario | [Configurar una clave SSH de GitHub](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/) |
| GitHub Enterprise | [Señal de acceso personal](/docs/services/ghededicated?topic=ghededicated-getting-started#ghe_auth) | Nombre de usuario de GitHub Enterprise (no su ID de IBM) y señal de acceso personal | [Configure la clave SSH de GitHub Enterprise](/docs/services/ghededicated?topic=ghededicated-getting-started#ghe_auth) |

Si prefiere utilizar SSH, puede reutilizar una clave única en todos los servidores de Git. Cree o localice la clave y configúrela en cada servidor como se describe en los enlaces anteriores. Si crea su clave con una contraseña, se le solicitará cuando utilice la clave.
{: tip}

2. Si va a utilizar la línea de mandatos de Git, efectúe los pasos siguientes:

    a. Compruebe si Git está instalado. En una línea de mandatos, escriba `git version`. Si Git está instalado, se mostrará el número de versión y puede empezar.

    b. Si Git no está instalado, [vaya al sitio web de Git ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://git-scm.com/downloads){: new_window}.

    c. Descargue e instale la versión para el sistema operativo. Puede aceptar los valores de instalación predeterminados.


### Clonar el proyecto
{: #git_clone}

Cree una copia local de los archivos del proyecto clonando el repositorio de Git para que pueda acceder al contenido del repositorio fuera del Web IDE utilizando cualquier herramienta de escritorio.

1. En la página Visión general de la cadena de herramientas, pulse la tarjeta para el repositorio que desee clonar.

2. Recopile el URL del repositorio:

   a. En GitHub, pulse **Clonar o descargar**. Para utilizar HTTPS, seleccione **Utilizar HTTPS**.  Para utilizar SSH, pulse **Utilizar SSH**. Pulse el icono de portapapeles para copiar el URL.

   b. En Git Repos and Issue Tracking, seleccione **HTTPS** o **SSH** y copie el URL en el campo.

3. Abra una línea de mandatos.

4. Cambie el directorio en el que desea que esté la copia local del repositorio de Git.

5. Escriba `git clone`, pegue el URL y pulse Intro.

6. Si se le solicita autenticación, especifique la información adecuada, tal como se define en la tabla anterior.


Una vez que se haya completado la descarga, tendrá una versión local de los archivos en el repositorio. Para obtener más información sobre cómo utilizar Git, consulte la [documentación de Git ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")]](http://git-scm.com/doc){: new_window}.


## Acceso a su repositorio mediante el plug-in de Eclipse y de EGit
{: #git_egit}

Si utiliza Eclipse y tiene un proyecto que utiliza Git para el control de origen, puede utilizar el plug-in de EGit para gestionar su repositorio desde Eclipse. Para obtener más información sobre cómo instalar y configurar EGit, consulte la [guía de aprendizaje de EGit ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")]](http://eclipsesource.com/blogs/tutorials/egit-tutorial/){: new_window}.

Si utiliza {{site.data.keyword.gitrepos}} y tiene algún problema, consulte la [documentación de {{site.data.keyword.gitrepos}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_local).
