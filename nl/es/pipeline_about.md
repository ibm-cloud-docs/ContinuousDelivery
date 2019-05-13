---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-08"

keywords: run jobs, sequences of stages, job types

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


# Visión general de Delivery Pipeline
{: #deliverypipeline_about}

{{site.data.keyword.contdelivery_full}} incluye Delivery Pipeline para crear, probar y desplegar de manera repetitiva con una mínima intervención humana. En un conducto, las secuencias de etapas recuperan la entrada y los trabajos de ejecución, como compilaciones, pruebas y despliegues.
{:shortdesc}

Los permisos para ver, modificar o ejecutar un conducto se basan en el control de accesos de la cadena de herramientas que es propietaria del conducto. Para obtener más información sobre el control de accesos para las cadenas de herramientas, consulte [Gestión del acceso a cadenas de herramientas en grupos de recursos](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_resource_groups){: new_window} y [Gestión del acceso a cadenas de herramientas en organizaciones de Cloud Foundry](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs){: new_window}.
{: important}

Puede especificar los scripts para que se ejecute en muchos de los tipos de trabajo que proporciona el conducto, lo que le proporciona un control directo sobre lo que ejecuta el trabajo. Estos scripts se ejecutan en una imagen de Docker que contiene un número de herramientas de desarrollo estándar, incluidas las herramientas necesarias para interactuar con los tiempos de ejecución de {{site.data.keyword.Bluemix_notm}}. Para obtener más información sobre lo que contiene el Docker estándar, consulte [Recursos preinstalados](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources){: new_window}. Si el job requiere herramientas de desarrollo que no están disponibles en la imagen estándar o si necesita diferentes versiones de estas herramientas, puede utilizar una imagen personalizada. Para obtener más información sobre las imágenes personalizadas, consulte [Trabajar con imágenes de Docker personalizadas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-custom_docker_images#custom_docker_images){: new_window}.

Cuando el conducto ejecuta scripts, las propiedades que describen el contexto en el que se ejecuta el trabajo se pasan al script utilizando variables de entorno. Por ejemplo, el URL del repo que es la entrada a la etapa, el nombre de la etapa y el trabajo que se está ejecutando, los parámetros especificados por el tipo de trabajo, etc. Para ver una lista de las variables de entorno disponibles, consulte [Recursos preinstalados](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment#deliverypipeline_resources). 

Puede definir propiedades tanto en el nivel de conducto como en el nivel de etapa. Las propiedades de conducto se comparten en todas las etapas y trabajos de un conducto. Las propiedades de la etapa son exclusivas de una determinada etapa y se comparten en todos los trabajos de dicha etapa. Para obtener más información sobre las propiedades, consulte [Propiedades de entorno (variables de entorno)](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#environment_properties).

## Etapas
{: #deliverypipeline_stages}

Las etapas organizan la entrada y los trabajos a medida que se compila, se despliega y se prueba el código. Las etapas aceptan la entrada de repositorios de control de origen (repositorios SCM) o compilan trabajos en otras etapas. Para repositorios SCM, la entrada es el contenido de una sucursal en concreto del repositorio; para los trabajos de compilación, la entrada son los artefactos producidos por el trabajo. Al crear la primera etapa, el separador **INPUT** contiene los valores predeterminados por defecto.

Cuando se ejecuta una etapa, la entrada de la etapa se pasa a cada uno de los trabajos de la etapa. A cada trabajo se le proporciona un contenedor limpio en el que ejecutarse. Como resultado, los trabajos de una etapa no se pueden pasar artefactos entre sí. Para pasar artefactos entre trabajos, separe los trabajos en dos etapas y utilice la salida del trabajo en la primera etapa como entrada a la segunda etapa.
{: tip}

De forma similar a cómo puede definir las propiedades del conducto, también puede definir las propiedades de la etapa para su uso en todos los trabajos de una etapa determinada. Por ejemplo, podría definir una propiedad `TEST_URL` que pasa un URL a los trabajos de prueba y despliegue en una etapa. El trabajo de despliegue se despliega en dicho URL y el trabajo de prueba realiza una prueba de la app en ejecución en el URL. Las propiedades de etapa también se pasan a scripts de trabajo utilizando variables de entorno. Si se define la misma propiedad tanto en el nivel de conducto como en el nivel de etapa, se utiliza el valor de la propiedad de la etapa.

De forma predeterminada en una etapa, las compilaciones y los despliegues se ejecutan automáticamente cada vez que se entreguen cambios a un repositorio SCM del proyecto. Las etapas y los trabajos se ejecutan en serie; permiten el control de flujo para el trabajo. Por ejemplo, puede situar una etapa de prueba antes de una etapa de despliegue. Si las pruebas de la etapa de pruebas fallan, la etapa de despliegue no se ejecuta.

Puede que desee un control más estricto de una etapa específica. Si no desea que se ejecute una etapa cada vez que se produzca un cambio en su entrada, puede inhabilitar la prestación. En el separador **ENTRADA**, en la sección Desencadenante de etapa, pulse **Ejecutar trabajos sólo cuando esta etapa se ejecute manualmente**.

![El separador ENTRADA](images/input_tab_only_execute.png)


### Etapa de compilación
{: #build_stage}

En la etapa de compilación se especifica un **Tipo de compilador** para indicar cómo compilar los artefactos.  

Muchos de los campos disponibles en trabajos de compilación son comunes en varios tipos de compilador.
{: tip}

Están disponibles los siguientes tipos de compilador:

* **Simple** - Trabajos que utilizan el tipo de compilador **Simple** toman la entrada de la etapa actual y, sin modificarla, la archivan para su uso en etapas futuras. Normalmente, el tipo de compilador **Simple** solo es útil cuando la entrada de la etapa procede de un repositorio de SCM.
* **Ant** - Utilice este tipo de compilador para utilizar archivos de Apache Ant para gestionar el trabajo de compilación.
  * **Script de compilación** - Este tipo de compilador puede ser cualquier script de compilación válido. De forma predeterminada, el tipo de compilador se establece en 'ant'.
  * **Directorio de trabajo** - Especifica el directorio en el que se ejecuta el script.
  * **Directorio de archivado de compilación** - Especifica el directorio que contiene la salida del trabajo que se archivará para que la utilice una etapa posterior.
  * **Habilitar informe de prueba** - Seleccione este recuadro de selección para especificar que el trabajo de compilación ejecuta pruebas que generan archivos de resultados en formato XML JUnit. Se visualiza un informe basado en los archivos de resultados en el separador Pruebas de la página Resultados del trabajo. Si ha fallado alguna prueba, el trabajo se marcará como fallido.
  * **Habilitar informe de cobertura de código** - Seleccione este recuadro de selección para mostrar más campos que puede utilizar en el informe de cobertura de código. Puede especificar el ejecutor de cobertura (como la cobertura Istanbul, JaCoCo, ore), la ubicación del archivo de resultados de Cobertura y el directorio de resultados de Cobertura, con relación al directorio de trabajo.
* **Container Registry**
* **Gradle (Artifactory, Nexus o SonarQube)**
* **Grunt**
* **IBM Globalization Pipeline**
* **Maven (Artifactory, Nexus o SonarQube)**
* **npm (Artifactory o Nexus)**
* **Shell Script**

### Fase de despliegue
En la fase de despliegue se especifica la entrada de una etapa de compilación.  En los trabajos de la etapa de despliegue se especifica un **Tipo de desplegador**.  Están disponibles los siguientes tipos de desplegador:

1. **Cloud Foundry**
2. **Kubernetes**

## Trabajos
{: #deliverypipeline_jobs}

Un trabajo es una unidad de ejecución dentro de una etapa. Una etapa puede contener varios trabajos, y los trabajos de una etapa se ejecutan secuencialmente. De forma predeterminada, si falla un trabajo, no se ejecutarán los trabajos posteriores de la etapa.

![Compilar y probar trabajos en una etapa](images/jobs.png)

Los trabajos se ejecutan en directorios de trabajo discretos dentro de los contenedores Docker creados para cada ejecución de conducto. Antes de que se ejecute un trabajo, su directorio de trabajo se rellena con la entrada definida en el nivel de etapa. Por ejemplo, es posible que tenga una etapa que contenga un trabajo de prueba y un trabajo de despliegue. Si instala dependencias en un trabajo, no estarán disponibles en el otro trabajo. Sin embargo, si convierte en disponibles las dependencias en la entrada de la etapa, estarán disponibles para ambos trabajos.

Excepto para los trabajos de compilación simples, al configurar un trabajo, puede incluir scripts shell UNIX que incluyan mandatos de compilación, prueba o despliegue. Dado que los trabajos se ejecutan en contenedores ad hoc, las acciones de un trabajo no pueden afectar a los entornos de ejecución de otros trabajos, incluso aunque estos trabajos formen parte de la misma etapa.

Encontrará ejemplos de scripts de creación y despliegue en [https://github.com/open-toolchain/commons](https://github.com/open-toolchain/commons).

Además, los trabajos de conducto sólo pueden ejecutar los siguientes mandatos como `sudo`:
  * `/usr/sbin/service`
  * `/usr/bin/apt-get`
  * `/usr/bin/apt-key`
  * `/usr/bin/dpkg`
  * `/usr/bin/add-apt-repository`
  * `/opt/IBM/node-v0.10.40-linux-x64/npm`
  * `/opt/IBM/node-v0.12.7-linux-x64/npm`
  * `/opt/IBM/node-v4.2.2-linux-x64/npm`
  * `/usr/bin/Xvfb`
  * `/usr/bin/pip`


Una vez que se ejecute un trabajo, el contenedor creado para él se descartará. Los resultados de una ejecución de trabajo pueden continuar, pero el entorno en el que se ha ejecutado no.

Los trabajos se pueden ejecutar durante un máximo de 60 minutos. Cuando los trabajos superan dicho límite, fallarán. Si un trabajo está superando el límite, divídalo en varios trabajos. Por ejemplo, si un trabajo lleva a cabo tres tareas, puede dividirlo en tres trabajos: uno para cada tarea.
{: tip}

Para obtener más información sobre cómo añadir un trabajo a una etapa, consulte [Adición de un trabajo a una etapa](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy#deliverypipeline_add_job){: new_window}.

### Trabajos de compilación

Los trabajos de compilación compilan el proyecto en preparación para el despliegue. Generan artefactos que se pueden enviar a un directorio de archivado de compilación, aunque de forma predeterminada, los artefactos se colocan en el directorio raíz del proyecto.

Los trabajos que toman entrada de trabajos de compilación deben hacer referencia a los artefactos de compilación en la misma estructura en la que se crearon. Por ejemplo, si un trabajo de compilación archiva artefactos de compilación en un directorio de `salida`, un script de despliegue podría hacer referencia al directorio de `salida` en lugar de al directorio raíz del proyecto para desplegar el proyecto compilado. Puede especificar el directorio en el que archivar escribiendo el nombre del directorio en el campo **Directorio de archivado de compilación**. Si deja el campo en blanco, se archiva en el directorio raíz.

Si utiliza el tipo de constructor **Simple**, el código no se compilará ni creará; se empaquetará y quedará disponible para futuras etapas.
{: tip}

Cuando se despliega utilizando Cloud Foundry, Cloud Foundry incluirá los artefactos correctos para permitir que se ejecute la app. Para obtener más información, consulte [Despliegue de apps mediante el mandato cf](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#deploy_apps). El conducto para una app de Cloud Foundry contiene una etapa de Despliegue que ejecuta un mandato cf.

Cloud Foundry intenta [detectar el paquete de compilación para utilizar ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://docs.cloudfoundry.org/buildpacks/detection.html). Puede especificar el [paquete de compilación](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_buildpacks#using_buildpacks) que se utilizará en el archivo de manifiesto en la carpeta raíz de la app. Los paquetes de compilación normalmente examinan los artefactos proporcionados por los usuarios para determinar qué dependencias se descargarán y cómo configurar las aplicaciones para que se comuniquen con servicios enlazados. Para obtener más información sobre los archivos de manifiesto, consulte [Manifiesto de aplicación](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest).

### Trabajos de despliegue

Los trabajos de despliegue cargan el proyecto a {{site.data.keyword.Bluemix_notm}} como una app y son accesibles desde un URL. Una vez que se despliegue un proyecto, puede encontrar la app desplegada en el panel de control de {{site.data.keyword.Bluemix_notm}}.

Los trabajos de despliegue pueden desplegar nuevas apps o actualizar apps existentes. Incluso si despliega por primera vez una app utilizando otro método, como por ejemplo la interfaz de línea de mandatos de Cloud Foundry o la barra de ejecución en el IDE de web, puede actualizar la app utilizando un trabajo de despliegue. Para actualizar una app, en el trabajo de despliegue, utilice el nombre de dicha app.

Puede desplegar en una o más regiones y servicios. Por ejemplo, puede configurar {{site.data.keyword.deliverypipeline}} para que utilice uno o varios servicios, realice pruebas en una región y despliegue a producción en varias regiones.

### Trabajos de prueba
Si desea solicitar que se cumplan las condiciones, incluya trabajos de prueba antes o después de los trabajos de compilación y despliegue. Puede personalizar trabajos de prueba para que sean tan simples o tan complejos como se necesite. Por ejemplo, puede emitir un mandato cURL y esperar una respuesta determinada. También puede ejecutar una suite de pruebas de unidad o ejecutar pruebas funcionales con servicios de prueba de terceros, como por ejemplo Sauce Labs.

Si sus pruebas generan archivos de resultados en formato XML JUnit, se mostrará un informe basado en los archivos de resultados en el separador **Pruebas** de cada página de resultados de prueba. Si falla una prueba, el trabajo también fallará.

## Propiedades de entorno (Variables de entorno)
{: #environment_properties}

Un conjunto de propiedades de entorno predefinidas proporcionan acceso a información sobre el entorno de ejecución del trabajo. Para obtener una lista completa de propiedades de entorno predefinidas, consulte [Recursos y propiedades de entorno](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_environment).

También puede definir sus propias propiedades de entorno. Por ejemplo, puede definir una propiedad `API_KEY` que pase una clave de API que se utiliza para que todos los scripts del conducto accedan a los recursos de {{site.data.keyword.Bluemix_notm}}.

Puede añadir los siguientes tipos de propiedades:

* **Texto**: Una clave de propiedad con un valor de línea única.
* **Área de texto**: Una clave de propiedad con un valor de varias líneas.
* **Seguro**: Una clave de propiedad con un valor de línea única que esté protegido con cifrado AES-128. El valor se visualiza como asteriscos.
* **Propiedades**: Un archivo del repositorio del proyecto. Este archivo puede contener varias propiedades. Cada propiedad debe estar en su propia línea. Para pares de clave-valor independientes, utilice el signo igual (=). Coloque todos los valores de serie entre comillas. Por ejemplo, `MY_STRING="SOME STRING VALUE"`.

Puede examinar las propiedades del entorno para un trabajo de conducto ejecutando el mandato `env` en el script del trabajo.
{:tip}

### Propiedades de conducto
Para definir las propiedades del conducto, desde el menú de desbordamiento de la página Conducto, seleccione **Configurar conducto**.

![Menú de desbordamiento del conducto](images/OverflowMenu.png)

En el separador **ENVIRONMENT PROPERTIES** en la página de configuración Conducto, establezca las propiedades del entorno a nivel de conducto.

![Página de propiedades de conducto](images/PipelineProperties.png)

### Propiedades de la etapa
Para definir las propiedades de la etapa, abra la página de configuración Etapa y pulse el separador **ENVIRONMENT PROPERTIES**.

![Página de propiedades de la etapa](images/StageProperties.png)

También puede pasar propiedades de entorno entre trabajo en la misma etapa exportando las propiedades. Por ejemplo, puede incluir el mandato siguiente para utilizar la propiedad `$API_KEY` en otro trabajo de la etapa: `export API_KEY=<insert API key here>`
{:tip}

### Propiedades calculadas
Puede calcular los valores de propiedad de entorno que se comparten entre etapas creado un archivo `build.properties` mientras se ejecuta la etapa y, a continuación, hacer que la etapa siguiente ejecute el archivo. Por ejemplo, el trabajo de compilación podría incluir el mandato siguiente en el script de compilación:

  `echo "IMAGE_NAME=${FULL_REPOSITORY_NAME}" >> $ARCHIVE_DIR/build.properties`

Todos los trabajos empiezan ejecutando el archivo `build.properties`, si existe.

## Creación y uso de artefactos
{: #artifacts}

Los trabajos de compilación captan automáticamente el contenido en la carpeta actual donde se ejecuta el script de usuario.  Si no necesita todo el contenido del repositorio git todo para el despliegue posterior, es preferible que configure un directorio de salida explícito y se copien o se creen los artefactos relevantes allí.  Los scripts de trabajos se ejecutan en el resultado de la compilación (directorio de salida).

Los trabajos que se despliegan en Cloud Foundry, es necesario especificar la clave de API de Plataforma de un usuario en donde se ejecutan los trabajos de autorización, y la región, la organización y el espacio en los que se deben desplegar los artefactos. Si se necesitan servicios adicionales para ejecutar la app, debe especificarlos en el archivo `manifest.yml`.

En los trabajos de despliegue que se despliegan en el {{site.data.keyword.containerlong_notm}} es necesario especificar la clave de API de Plataforma de un usuario en donde se ejecutan los trabajos de autorización, un Dockerfile y, opcionalmente, un diagrama de Helm.  

El script del trabajo se ejecuta después de que el trabajo inicie sesión en el entorno de destino utilizando la clave de API de la Plataforma que se le ha asignado (por lo tanto, puede ejecutar mandatos `cf push` o `kubectl` en el script).

## Un conducto de ejemplo
{: #deliverypipeline_example}

Un conducto de ejemplo puede contener tres etapas:

1. Una etapa de compilación que compila y ejecuta procesos de compilación en una app.
2. Una etapa de prueba que despliega una instancia de la app y, a continuación, ejecuta pruebas en esta.
3. Una etapa de producción que despliega una instancia de producción de la app probada.

Este conducto se muestra en el siguiente diagrama conceptual:

![Un diagrama conceptual de etapas y trabajos en un conducto](images/diagram.jpg)

*Un modelo conceptual de un conducto de tres etapas*

Las etapas toman su entrada de repositorios y trabajos de compilación, y los trabajos de una etapa se ejecutan de forma secuencial e independiente entre sí. En el conducto de ejemplo, las etapas se ejecutan secuencialmente, aunque las etapas de Prueba y de Producción tomen la salida de la etapa de Compilación como su entrada.

## Archivos de manifiesto de Cloud Foundry
{: #deliverypipeline_manifest}

Los archivos de manifiesto, que se denominan `manifest.yml` y se almacenan en el directorio raíz de un proyecto, controlan la forma en que se despliega el proyecto en {{site.data.keyword.Bluemix_notm}}. Para obtener información sobre cómo crear archivos de manifiesto para un proyecto, consulte la [documentación de {{site.data.keyword.Bluemix_notm}} sobre manifiestos de aplicaciones](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest). Para integrarse con {{site.data.keyword.Bluemix_notm}}, el proyecto debe tener un archivo de manifiesto en su directorio raíz. Sin embargo, no es necesario que realice el despliegue en función de la información del archivo.

En el conducto, puede especificar todo lo que puede hacer un archivo de manifiesto utilizando argumentos del mandato `cf push`. Los argumentos del mandato `cf push` son útiles en los proyectos que tienen varios destinos de despliegue. Si varios trabajos de despliegue intentan utilizar la ruta especificada en el archivo de manifiesto del proyecto, se producirá un conflicto.

Para evitar conflictos, puede especificar una ruta utilizando `cf push` seguido del argumento del nombre de host, `-n`, y un nombre de ruta. Al modificar el script de despliegue para etapas individuales, puede evitar conflictos de ruta al desplegar en varios destinos.

Para utilizar los argumentos del mandato `cf push`, abra los valores de configuración para un trabajo de despliegue y modifique el campo **Desplegar script**. Para obtener más información, consulte la [documentación de Push de Cloud Foundry ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html#push){: new_window}.
