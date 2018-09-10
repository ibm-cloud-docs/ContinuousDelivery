---

copyright:
  years: 2016, 2018
lastupdated: "2018-8-2"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# Visión general de Delivery Pipeline
{: #deliverypipeline_about}

{{site.data.keyword.contdelivery_full}} incluye Delivery Pipeline para crear, probar y desplegar de manera repetitiva con una mínima intervención humana. En un conducto, las secuencias de etapas recuperan la entrada y los trabajos de ejecución, como compilaciones, pruebas y despliegues.
{:shortdesc}

Los permisos para ver, modificar o ejecutar una interconexión se basan en el control de accesos de la cadena de herramientas que es propietaria de la interconexión. Para obtener más información sobre el control de accesos para las cadenas de herramientas, consulte [Gestión del acceso a cadenas de herramientas en grupos de recursos](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_resource_groups){: new_window} y [Gestión del acceso a cadenas de herramientas en organizaciones de Cloud Foundry](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_orgs){: new_window}.
{: tip}

## Etapas
{: #deliverypipeline_stages}

Las etapas organizan la entrada y los trabajos a medida que se compila, se despliega y se prueba el código. Las etapas aceptan la entrada de repositorios de control de código fuente (repositorios SCM) o compilan trabajos (compilan artefactos) en otras etapas. Al crear la primera etapa, se establecerán los valores predeterminados en el separador **INPUT**.

La entrada de una etapa se pasa a los trabajos que contiene la etapa, y a cada trabajo se le da un contenedor limpio para ejecutarla.

Los trabajos de una etapa no se pueden pasar artefactos entre sí. Puesto que no puede pasar artefactos entre trabajos, necesita una etapa de compilación independiente de la etapa de despliegue si la etapa de despliegue va a utilizar los artefactos de la etapa de compilación.
{: tip}

Puede definir propiedades del entorno de etapas que se pueden utilizar en todos los trabajos. Por ejemplo, podría definir una propiedad `TEST_URL` que pasa un único URL para desplegar y probar trabajos en una sola etapa. El trabajo de despliegue podría desplegarse en dicho URL, y el trabajo de prueba podría probar la app en ejecución en el URL.

De forma predeterminada en una etapa, las compilaciones y los despliegues se ejecutan automáticamente cada vez que se entreguen cambios a un repositorio SCM del proyecto. Las etapas y los trabajos se ejecutan en serie; permiten el control de flujo para el trabajo. Por ejemplo, puede situar una etapa de prueba antes de una etapa de despliegue. Si fallan las pruebas en la etapa de prueba, no se ejecutará la etapa de despliegue.

Puede que desee un control más estricto de una etapa específica. Si no desea que se ejecute una etapa cada vez que se produzca un cambio en su entrada, puede inhabilitar la prestación. En el separador **ENTRADA**, en la sección Desencadenante de etapa, pulse **Ejecutar trabajos sólo cuando esta etapa se ejecute manualmente**.

![El separador ENTRADA](images/input_tab_only_execute.png)


### Etapa de compilación
{: #build_stage}

<!-- Need the Pipeline team to fill out what each builder does and possible add an example -->
En la etapa de compilación se especifica un **Tipo de compilador** para indicar cómo compilar los artefactos.  Están disponibles los siguientes tipos de compilador:

1. **Simple**. Si utiliza el tipo de compilador **Simple**, el código no se compilará ni se creará; se empaquetará y quedará disponible para futuras etapas.
2. **Ant**
3. **Container Registry**
4. **Gradle**
5. **Gradle (Artifactory, Nexus o SonarQube)**
6. **Grunt**
7. **IBM Globalization Pipeline**
8. **Maven**
9. **Maven (Artifactory, Nexus o SonarQube)**
10. **npm**
11. **npm (Artifactory o Nexus)**
12. **Shell Script**

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

Para obtener más información sobre cómo añadir un trabajo a una etapa, consulte [Adición de un trabajo a una etapa](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_add_job){: new_window}.

### Trabajos de compilación

Los trabajos de compilación compilan el proyecto en preparación para el despliegue. Generan artefactos que se pueden enviar a un directorio de archivado de compilación, aunque de forma predeterminada, los artefactos se colocan en el directorio raíz del proyecto.

Los trabajos que toman entrada de trabajos de compilación deben hacer referencia a los artefactos de compilación en la misma estructura en la que se crearon. Por ejemplo, si un trabajo de compilación archiva artefactos de compilación en un directorio de `salida`, un script de despliegue podría hacer referencia al directorio de `salida` en lugar de al directorio raíz del proyecto para desplegar el proyecto compilado. Puede especificar el directorio en el que archivar escribiendo el nombre del directorio en el campo **Directorio de archivado de compilación**. Si deja el campo en blanco, se archiva en el directorio raíz.

Si utiliza el tipo de constructor **Simple**, el código no se compilará ni creará; se empaquetará y quedará disponible para futuras etapas.
{: tip}

Cuando se despliega utilizando Cloud Foundry, Cloud Foundry incluirá los artefactos correctos para permitir que se ejecute la app. Para obtener más información, consulte [Despliegue de apps mediante el mandato cf](/docs/cloud-foundry/deploy-apps.html#dep_apps). El conducto para una app de Cloud Foundry contiene una etapa de Despliegue que ejecuta un mandato cf.

Cloud Foundry intenta [detectar el paquete de compilación para utilizar ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://docs.cloudfoundry.org/buildpacks/detection.html). Puede especificar el [paquete de compilación](/docs/cfapps/byob.html#using-community-buildpacks) que se utilizará en el archivo de manifiesto en la carpeta raíz de la app. Los paquetes de compilación normalmente examinan los artefactos proporcionados por los usuarios para determinar qué dependencias se descargarán y cómo configurar las aplicaciones para que se comuniquen con servicios enlazados. Para obtener más información sobre los archivos de manifiesto, consulte [Manifiesto de aplicación](/docs/cloud-foundry/deploy-apps.html#appmanifest).

### Trabajos de despliegue

Los trabajos de despliegue cargan el proyecto a {{site.data.keyword.Bluemix_notm}} como una app y son accesibles desde un URL. Una vez que se despliegue un proyecto, puede encontrar la app desplegada en el panel de control de {{site.data.keyword.Bluemix_notm}}.

Los trabajos de despliegue pueden desplegar nuevas apps o actualizar apps existentes. Incluso si despliega por primera vez una app utilizando otro método, como por ejemplo la interfaz de línea de mandatos de Cloud Foundry o la barra de ejecución en el IDE de web, puede actualizar la app utilizando un trabajo de despliegue. Para actualizar una app, en el trabajo de despliegue, utilice el nombre de dicha app.

Puede desplegar en una o más regiones y servicios. Por ejemplo, puede configurar {{site.data.keyword.deliverypipeline}} para que utilice uno o varios servicios, realice pruebas en una región y despliegue a producción en varias regiones. Para obtener más información, consulte [Regiones](/docs/overview/ibm-cloud.html#ov_intro-reg){: new_window}.

### Trabajos de prueba
Si desea solicitar que se cumplan las condiciones, incluya trabajos de prueba antes o después de los trabajos de compilación y despliegue. Puede personalizar trabajos de prueba para que sean tan simples o tan complejos como se necesite. Por ejemplo, puede emitir un mandato cURL y esperar una respuesta determinada. También puede ejecutar una suite de pruebas de unidad o ejecutar pruebas funcionales con servicios de prueba de terceros, como por ejemplo Sauce Labs.

Si sus pruebas generan archivos de resultados en formato XML JUnit, se mostrará un informe basado en los archivos de resultados en el separador **Pruebas** de cada página de resultados de prueba. Si falla una prueba, el trabajo también fallará.

## Propiedades de entorno (Variables de entorno)
{: #environment_properties}

Puede incluir propiedades de entorno dentro de los mandatos shell de un trabajo. Las propiedades proporcionan acceso a información sobre el entorno de ejecución del trabajo. Para obtener más información, consulte [Propiedades y recursos del entorno para el servicio {{site.data.keyword.deliverypipeline}}](/docs/services/ContinuousDelivery/pipeline_deploy_var.html).  Las propiedades de entorno pueden pasarse entre trabajos en la misma etapa exportando las propiedades.  Para pasar propiedades entre etapas, cree un archivo `build.properties` en el repositorio en la etapa y luego ejecute `build.properties` en la siguiente etapa.  Por ejemplo, el trabajo de compilación podría incluir este mandato en el script de compilación:

    `echo "IMAGE_NAME=${FULL_REPOSITORY_NAME}" >> $ARCHIVE_DIR/build.properties`

    Todos los trabajos empiezan ejecutando el archivo `build.properties`, si existe.

## Creación y uso de artefactos
{: #artifacts}

Los trabajos de compilación captan automáticamente el contenido en la carpeta actual donde se ejecuta el script de usuario.  Si no necesita todo el contenido del repositorio git todo para el despliegue posterior, es preferible que configure un directorio de salida explícito y se copien o se creen los artefactos relevantes allí.  Los scripts de trabajos se ejecutan en el resultado de la compilación (directorio de salida).

En los trabajos de despliegue que se despliegan en Cloud Foundry, es necesario especificar la clave de API de Plataforma de un usuario en donde se ejecutan los trabajos de autorización, y la región, la organización y el espacio en los que se deben desplegar los artefactos. Si se necesitan servicios adicionales para ejecutar la app, debe especificarlos en el archivo `manifest.yml`.

En los trabajos de despliegue que se despliegan en el {{site.data.keyword.containerlong_notm}} para ejecutarse en un clúster de Kubernetes, es necesario especificar la clave de API de Plataforma de un usuario en donde se ejecutan los trabajos de autorización, un Dockerfile y, opcionalmente, un diagrama de Helm.  

El script del trabajo se ejecuta después de que el trabajo inicie sesión en el entorno de destino utilizando la clave de API de la Plataforma que se le ha asignado (por lo tanto, puede realizar mandatos `cf push` o `kubectl` en el script).

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

Los archivos de manifiesto, que se denominan `manifest.yml` y se almacenan en el directorio raíz de un proyecto, controlan la forma en que se despliega el proyecto en {{site.data.keyword.Bluemix_notm}}. Para obtener información sobre cómo crear archivos de manifiesto para un proyecto, consulte la [documentación de {{site.data.keyword.Bluemix_notm}} sobre manifiestos de aplicaciones](/docs/cloud-foundry/deploy-apps.html#appmanifest). Para integrarse con {{site.data.keyword.Bluemix_notm}}, el proyecto debe tener un archivo de manifiesto en su directorio raíz. Sin embargo, no es necesario que realice el despliegue en función de la información del archivo.

En el conducto, puede especificar todo lo que puede hacer un archivo de manifiesto utilizando argumentos del mandato `cf push`. Los argumentos del mandato `cf push` son útiles en los proyectos que tienen varios destinos de despliegue. Si varios trabajos de despliegue intentan utilizar la ruta especificada en el archivo de manifiesto del proyecto, se producirá un conflicto.

Para evitar conflictos, puede especificar una ruta utilizando `cf push` seguido del argumento del nombre de host, `-n`, y un nombre de ruta. Al modificar el script de despliegue para etapas individuales, puede evitar conflictos de ruta al desplegar en varios destinos.

Para utilizar los argumentos del mandato `cf push`, abra los valores de configuración para un trabajo de despliegue y modifique el campo **Desplegar script**. Para obtener más información, consulte la [documentación de Push de Cloud Foundry ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html#push){: new_window}.
