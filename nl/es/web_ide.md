---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-19"

keywords: Eclipse Orion {{site.data.keyword.webide}}, file types, Local Editor Settings icon

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:important: .important}
{:note: .note}
{:tip: .tip}
{:download: .download}

# Desarrollo con Eclipse Orion Web IDE
{: #web_ide}

Eclipse Orion {{site.data.keyword.webide}} es un entorno de desarrollo basado en navegador donde puede desarrollar para la web en JavaScript, HTML y CSS con la ayuda de asistencia de contenido, finalización del código y comprobación de errores. {{site.data.keyword.webide}} funciona con casi cualquier idioma y puede resaltar la sintaxis de la mayoría de los tipos de archivo. El control de origen está integrado y puede desplegar código de forma local para probar y depurar las apps.
{:shortdesc}

Lo mejor de todo es que {{site.data.keyword.webide}} está basado en la web. No tiene que instalar, mantener ni escalar nada. Puede desarrollar en cualquier lugar donde tenga conexión a Internet.

No almacene datos regulados en archivos dentro de {{site.data.keyword.webide}}. Actualmente, los procedimientos para los datos regulados no están en vigor.
{: tip}

{{site.data.keyword.webide}} es accesible con el teclado y funciona correctamente con un lector de pantalla. Puede utilizar {{site.data.keyword.webide}} para editar código o, si lo prefiere, puede editar código utilizando su editor de código o de texto favorito. También puede utilizar las prestaciones de Git que se proporcionan con {{site.data.keyword.webide}}; como alternativa, puede utilizar la línea de mandatos de Git o github.com para acceder a las prestaciones de Git de {{site.data.keyword.webide}}.
{: note}

## Configuración del IDE
{: #editorsetup}

{{site.data.keyword.webide}} se puede personalizar para que pueda elegir los esquemas de colores, las herramientas técnicas y los valores que cumplan sus necesidades de desarrollo. Para ver y modificar los valores, desde la barra lateral de navegación de la izquierda, pulse el icono **Valores** <img class="inline" src="images/webide_settings_icon_light_small.png"  alt="El icono Valores">.

Si necesita a menudo cambiar determinados valores mientras edita, puede acceder a dichos valores rápidamente desde el icono **Valores de editor local** <img class="inline" src="images/webide_local_settings_icon_light_small.png"  alt="Icono Valores de editor local">.

![Valores de editor local](images/webide_local_editor_settings_light.png)

De forma predeterminada, siempre se muestran los valores para el estilo del editor y el tamaño de fuente. Para incluir otros valores de editor en el menú, siga estos pasos:

1. Pulse el icono **Valores de editor local** <img class="inline" src="images/webide_local_settings_icon_light_small.png"  alt="Icono valores de editor local">.

2. Pulse **Valores del editor**.

3. Para incluir o excluir un valor del menú **Valores del editor local**, pulse la estrella que hay en cada valor.

![Conmutador Valores de editor](images/webide_editor_settings_toggle_light.png)


## Edición de código
{: #editcode}

{{site.data.keyword.webide}} tiene dos secciones principales. La primera sección es el navegador de archivos, que muestra los archivos del proyecto en una estructura de árbol. Desde el navegador de archivos, puede crear, cambiar el nombre, suprimir y gestionar los archivos y carpetas.

Para cargar archivos en el navegador de archivos, arrástrelos desde el sistema al navegador de archivos.
{: tip}

La segunda sección es el panel del editor. El editor proporciona varias características de codificación, incluida la asistencia de contenido y la validación de sintaxis.

![Web IDE](images/webide_light.png)

### Cómo trabajar con varios archivos
1. Para trabajar con dos archivos a la vez, pulse el icono **Cambiar modo de editor de división** <img class="inline" src="images/webide_split_editor_icon_light_small.png"  alt="Icono Editor de división">.
2. Desde el menú que se abre, seleccione una vista.

 Tras seleccionar una vista, si ya se ha abierto un archivo en el editor, se mostrará en ambas vistas de editor.

 Para abrir o cambiar un archivo que se muestra en una de las vistas del editor:
 1. Mueva el cursor a la vista de editor que desee cambiar.
 2. En el navegador de archivos, pulse un archivo.

### Accesos directos de teclado
Muchos de los mandatos de {{site.data.keyword.webide}} son accesibles a través de atajos de teclado.

Para ver una lista de los atajos de teclado en el editor, pulse **Herramientas** > **Mostrar claves**. Como alternativa, puede ver la lista pulsando Alt+Mayús+?, o en MacOS, Control+Mayús+?. Puede personalizar un atajo pasando el ratón sobre la clave, pulsando el lápiz y escribiendo el nuevo enlace clave.

## Gestión del código fuente
{: #sourcecontrol}

{{site.data.keyword.webide}} se integra con herramientas de gestión de código fuente. Para trabajar con el repositorio de Git, pulse el icono **Repositorio de Git** <img class="inline" src="images/webide_git_icon_light_small.png"  alt="El icono Repositorio de Git">.  Para obtener más información, consulte [Cómo trabajar con Git en Eclipse Orion Web IDE](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_web_ide#git_web_ide).

## Despliegue de una app desde el espacio de trabajo
{: #deploy}

1. Para desplegar la app, desde la barra de ejecución, seleccione o cree una configuración de lanzamiento.
   ![Barra de ejecución](images/webide_runbar_light.png)   
1. Pulse el icono de despliegue <img class="inline" src="images/webide_deploy_button_light_small.png"  alt="icono de despliegue">. Se desplegará una instancia de la app utilizando el contenido actual del espacio de trabajo y del entorno definido en la configuración de lanzamiento.
2. Una vez que se despliegue la app, puede utilizar la barra de ejecución para detener, reiniciar o depurar la app, ver registros, etc.

<table role="presentation">
<tr><td><img src="./images/stop_button.png"  alt="Icono detener"></td><td>Detiene la app.</td></tr>
<tr><td> <img src="./images/open_app_url.png"  alt="Icono abrir URL de app"></td><td> Abre la app desplegada.</td></tr>
<tr><td><img src="./images/view_logs.png"  alt="Icono ver registros"></td><td>Visualiza los registros de la app desplegada.</td></tr>
<tr><td><img src="./images/open_dashboard.png"  alt="Icono abrir panel de control"></td><td>Abre el panel de control de la app.</td></tr>
</table>

Si está desarrollando una app Node.js, habilite la modalidad de Edición en directo: <img  src="./images/enable_live_edit.png"  alt="Graduador para habilitar edición en directo">

<table role="presentation"><tr><td><img src="./images/live_edit_restart.png"  alt="Icono reiniciar edición en directo"></td><td>Con la modalidad de edición en directo, reinicia con rapidez la app, sin volver a desplegar.</td></tr>
<tr><td> <img src="./images/debug_icon.png"  alt="Icono depurar"></td>
<td>Con la modalidad de edición en directo, accede al depurador.
</td></tr>
</table>

## Lenguajes soportados
{: #supported_languages}

Eclipse Orion {{site.data.keyword.webide}} proporciona ayuda de contenido, ayudas contextuales, vistas previas, validación y resaltado de sintaxis para archivos JavaScript, HTML, CSS y Markdown. También puede resultar la sintaxis de estos tipos de archivos:

<table role="presentation">
<tr>
<td>
<ul><li>Arduino
</li><li>C</li>
<li>C#
</li><li>C++
</li><li>CoffeeScript
</li><li>CSHTML
</li><li>Embedded JavaScript (ejs)
</li><li>Erlang
</li><li>Go
</li><li>HTML Abstraction Markup Language (Haml)
</li><li>Jade
</li><li>Java
</li><li>JSON
</li><li>Less  
</li><li>Lua  
</li><li>Objective-C
</li><li>PHP
</li><li>Python</li></ul>
</td>
<td>
<ul><li>Ruby
</li><li>Sass/SCSS
</li><li>SQL
</li><li>Swift
</li><li>TypeScript
</li><li>Visual Basic (vb)
</li><li>VMHTML
</li><li>XHTML
</li><li>XML
</li><li>XQuery
</li><li>YAML
</li><li>Archivo de lanzamiento 	
</li><li>Dockerfile
</li><li>gitignore
</li><li>git config
</li><li>cfignore
</li><li>properties
</li></ul>
</td>
</tr>
</table>

## Realice una guía de aprendizaje: Eclipse Orion Web IDE
{: #toolchain_web_ide_tutorials}

Consulte una de estas guías de aprendizaje sobre [IBM&reg; Cloud Garage Method](https://www.ibm.com/cloud/garage){: external}:

  * [Cree y utilice su primera cadena de herramientas utilizando la cadena de herramientas "Desarrollar una app de Cloud Foundry"](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){: external}.

  * [Utilice la cadena de herramientas "Desarrollar y probar microservicios en Cloud Foundry"](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){: external}. 
