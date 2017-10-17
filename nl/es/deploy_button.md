---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-19"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# Creación del botón Desplegar en {{site.data.keyword.Bluemix_notm}} {: #deploy-button} 

El botón Desplegar en {{site.data.keyword.Bluemix_notm}} es una manera fácil de compartir la app de origen Git público con otras personas para que puedan experimentar con el código y desplegarla en IBM {{site.data.keyword.Bluemix_notm}} mediante una cadena de herramientas. Este botón requiere una configuración mínima y puede insertarse en cualquier lugar que admita la marcación. El usuario que pulse el botón creará una copia del código en un nuevo repositorio Git (repo), de manera que la app original no se verá afectada.
{: shortdesc}

Cuando el usuario pulsa el botón tienen lugar las siguientes acciones: 

1. El usuario deberá crear una cuenta de {{site.data.keyword.Bluemix_notm}} si no dispone de una cuenta activa. Puede crear una cuenta de prueba o una cuenta real. 

2. El usuario puede seleccionar una región, organización, espacio y nombre de app pulsando el icono {{site.data.keyword.deliverypipeline}}. El nombre de app sugerido es el mismo que el nombre de la cadena de herramientas, que se crea a partir del nombre del repositorio Git original y de la hora. El nombre de la cadena de herramientas también se puede editar.

3. Se crea una cadena de herramientas que incluye un nuevo clon privado del repositorio Git, un conducto para crear y desplegar cambios de código, Eclipse Orion {{site.data.keyword.webide}} para editar código en la nube y un rastreador de problemas. 

  **Sugerencia**: Si el directorio `.bluemix` contiene un archivo `toolchain.yml`, el archivo se utilizará para especificar las integraciones de herramientas para la cadena de herramientas. Para obtener más información sobre el archivo `toolchain.yml`, consulte [Creación de cadenas de herramientas personalizadas](/docs/services/ContinuousDelivery/toolchains_custom.html#toolchains_custom){: new_window}.
 
4. Si la app requiere un archivo de compilación, este se detectará automáticamente y se compilará la app. 

5. Si se configura un conducto para el proceso de compilación y de despliegue, se utilizará un archivo `pipeline.yml` para desplegar la app.

6. Si la app necesita un contenedor, se utilizan un archivo `pipeline.yml` que defina el servicio IBM Containers y un Dockerfile que defina una imagen, para desplegar la app en un contenedor {{site.data.keyword.Bluemix_notm}}. 

7. Se desplegará la app en la organización de {{site.data.keyword.Bluemix_notm}} que haya seleccionado el usuario. 

## Ejemplos del botón {: #button-examples} 

Ejemplo del botón de la app de un repositorio {{site.data.keyword.gitrepos}} público:

[![Desplegar en Bluemix](images/deploy_buttonx2.png)](https://bluemix.net/deploy?repository=https://git.ng.bluemix.net/idsorg/sample-java-cloudant){:new_window}

Ejemplo del botón de la app de un repositorio GitHub público: 

[![Desplegar en Bluemix](images/deploy_buttonx2.png)](https://bluemix.net/deploy?repository=https://github.com/ibmjstart/bluemix-node-mysql-uploader){:new_window}

Vea un
botón de ejemplo para una app que se despliega en un contenedor {{site.data.keyword.Bluemix_notm}}: 

[![Desplegar en Bluemix](images/deploy_buttonx2.png)](https://bluemix.net/deploy?repository=https://github.com/Puquios/hello-containers){:new_window}

## Creación de un botón {: #create-button}

Para crear el botón Desplegar en {{site.data.keyword.Bluemix_notm}}, copie y modifique una de las siguientes plantillas de fragmento de código. Especifique un repositorio de Git y una rama en el URL.

### Creación de un botón en HTML

Para crear un botón en HTML, copie este fragmento de código e inserte un URL y una rama de repositorio de Git públicos.

```HTML
<a href="https://bluemix.net/deploy?repository=<git_repository_URL>&branch=<git_branch>"><img src="https://bluemix.net/deploy/button.png" alt="Desplegar en Bluemix"></a>
```

Si no incluye el parámetro `branch` en el URL de repositorio del fragmento de código, el botón Desplegar en Bluemix tendrá como valor predeterminado la rama maestra del repositorio.

### Creación de un botón en Markdown

Para crear un botón en Markdown, copie este fragmento de código e inserte un URL y una rama de repositorio de Git públicos.

```Markdown
[![Desplegar en Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=<URL_repositorio_git>&branch=<rama_git>)
```

Si no incluye el parámetro `branch` en el URL de repositorio del fragmento de código, el botón Desplegar en Bluemix tendrá como valor predeterminado la rama maestra del repositorio.

### Uso del fragmento de código del botón {: #button-snippet}

Una vez que cree un fragmento de código del botón Desplegar en Bluemix, puede insertarlo en blogs, artículos, wikis, archivos léame, o en cualquier otro lugar que desee para promocionar su app.

Cuando personalice el fragmento de código para el botón Desplegar en {{site.data.keyword.Bluemix_notm}}, tenga en cuenta que ambas plantillas utilizan una vía de acceso predeterminada a una imagen de botón externo en formato PNG y en inglés. 

* Si prefiere utilizar una imagen SVG para el botón en lugar de un PNG, cambie la vía de acceso a la imagen de botón que se utiliza en el fragmento de código a `https://bluemix.net/deploy/button.svg`.
	
* Si prefiere utilizar una imagen para el botón, cambie la vía de acceso de la imagen de botón que se utiliza en el fragmento de código a `https://bluemix.net/deploy/button_x2.png`. Esta imagen tiene el doble de tamaño de la predeterminada.
	
* Si prefiere almacenar la imagen localmente, puede descargarla y almacenarla en el repositorio de Git. Ajuste la vía de acceso para utilizar la ubicación relativa de la imagen.
	
* Si desea utilizar una versión traducida del botón, puede hacer referencia a la misma remotamente o descargarla desde [ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button){:new_window}. 
	
## Consideraciones sobre el repositorio {: #button-repo} 

Revise estas consideraciones del repositorio que se utiliza en el botón Desplegar en {{site.data.keyword.Bluemix_notm}}. 

### Requisitos del archivo de manifiesto

No es necesario que haya un archivo `manifest.yml` en el repositorio. Sin embargo, deberá proporcionar un archivo de manifiesto que declare otros servicios en el caso de que la app los necesite para ejecutarse.

En el archivo de manifiesto puede especificar: 

* Un nombre de app exclusivo.

* Servicios declarados, una extensión de manifiesto que crea o busca los servicios necesarios u opcionales que se espera que se configuren antes de que se despliegue la app, como por ejemplo un servicio de caché de datos. Puede encontrar una lista de los servicios, etiquetas y planes de {{site.data.keyword.Bluemix_notm}} elegibles utilizando la [Interfaz de línea de mandatos CF ![Icono de enlace externo](../../icons/launch-glyph.svg)](https://github.com/cloudfoundry/cli/releases) para ejecutar el mandato `cf marketplace` o examinando el [catálogo de {{site.data.keyword.Bluemix_notm}}](https://console.bluemix.net/catalog?ssoLogout=true&cm_mmc=developerWorks-_-dWdevcenter-_-devops-services-_-lp#/store).

Los servicios declarados son una extensión de IBM del formato de manifiesto estándar de Cloud Foundry. Es posible que se vaya revisando dicha extensión en posteriores releases a medida que se desarrolle y mejore la característica.

Si no sabe cómo crear archivos de manifiesto, [aprenda cómo crearlos aquí ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html#minimal-manifest){:new_window}.

```YAML
---
    #Plantilla manifest.yml

  declared-services:
    nombre_instancia_servicio_arbitrario:  # [required]
      label: nombre_servicio_real # [required] El nombre de servicio real del plan de mercado
      plan: Compartido # [opcional] Si se proporciona, se utiliza para captar el servicio declarado. De lo contrario, se establece el valor predeterminado 'Free' o 'free'.
  applications:
  - services
    - nombre_instancia_servicio_arbitrario
    name: nombreapp
    host: nombrehostapp
```

```YAML
---
    #Ejemplo manifest.yml

  declared-services:
      sample-java-cloudant-cloudantNoSQLDB:
        label: cloudantNoSQLDB
        plan: Compartido
  applications:
  - services
    - sample-java-cloudant-cloudantNoSQLDB
    name: Mi app
    host: miapp
```


### Requisitos del archivo de compilación

Si la app debe compilarse antes de que se pueda desplegar, debe incluir un archivo de compilación en el repositorio. Si se detecta un archivo script de construcción en el directorio raíz del repositorio, se desencadenará una compilación automatizada del código antes del despliegue. 

Entre los compiladores soportados se incluye:

* [Ant ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo"):](http://ant.apache.org/manual/using.html){:new_window} `build.xml`, que crea la salida a la carpeta `./output/`
* [Gradle ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo"):](http://docs.cloudfoundry.org/buildpacks/java/build-tool-int.html#gradle){:new_window} `/build.gradle`, que crea la salida a la carpeta `.`
* [Grunt ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo"):](http://gruntjs.com/getting-started#the-gruntfile){:new_window} `/Gruntfile.js`, que crea la salida a la carpeta `.`
* [Maven ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo"):](http://docs.cloudfoundry.org/buildpacks/java/build-tool-int.html#maven){:new_window} `/pom.xml`, que crea la salida a la carpeta `./target/`

### Requisitos del archivo de conducto

Para configurar el conducto para la cadena de herramientas en un directorio `.bluemix`, incluya un archivo `pipeline.yml`. Para cada archivo `pipeline.yml` del directorio, se creará un conducto cuando se cree una instancia de la cadena de herramientas. 

Para crear un archivo de conducto, consulte el archivo de ejemplo en las [instrucciones de conducto de la cadena de herramientas personalizada](toolchains_custom.html#toolchains_custom_pipeline_yml). En el momento en que defina un conducto en la interfaz web, defina un conducto en el texto creando etapas y trabajos, estableciendo entradas y variables de entorno y añadiendo scripts. También puede ver varios archivos de conducto más complejos en [este proyecto de demostración](https://github.com/open-toolchain/toolchain-demo/tree/master/.bluemix).

### Requisitos del dockerfile del contenedor

Para desplegar una app en un contenedor utilizando IBM Containers, debe incluir un Dockerfile en el directorio raíz del repositorio y, en un directorio `.bluemix`, incluya un archivo `pipeline.yml`. 

El Dockerfile actúa como un tipo de script de construcción para la app. Si se detecta un Dockerfile en el repositorio, la app se creará automáticamente en una imagen antes de que se despliegue en un contenedor. Si la propia app debe compilarse antes de que la app se compile en una imagen, incluya un script de compilación para la app y un Dockerfile.

Para obtener más información sobre cómo crear Dockerfiles, consulte la [documentación de Docker ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://docs.docker.com/reference/builder/){:new_window}.

Para crear un `pipeline.yml` manualmente que sea específicamente para contenedores, consulte los [ejemplos de GitHub ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/Puquios/){:new_window}.
