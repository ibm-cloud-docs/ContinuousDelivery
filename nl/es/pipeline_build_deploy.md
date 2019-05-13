---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-12"

keywords: ADD STAGE, Run Stage icon, JOBS tab

subcollection: ContinuousDelivery

---
<!-- Copyright info at top of file: REQUIRED
    The copyright info is YAML content that must occur at the top of the MD file, before attributes are listed.
    It must be surrounded by 3 dashes.
    The value "years" can contain just one year or a two years separated by a comma. (years: 2014, 2016)
    Indentation as per the previous template must be preserved.
-->

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Compilación y despliegue
{: #deliverypipeline_build_deploy}

{{site.data.keyword.contdelivery_full}} incluye Delivery Pipeline, que puede utilizar para implementar una integración continua repetible y un proceso de entrega continuo.
{:shortdesc}

Complete las tareas siguientes para configurar un conducto.

## Adición de una etapa
{: #deliverypipeline_add_stage}

1. En la página Conducto, pulse **AÑADIR ETAPA**. Se abrirá la página Configuración de etapa.
2. Configurar la etapa.
  1. En el separador **ENTRADA**, seleccione una entrada para la etapa.  En las etapas de compilación, el separador de entrada incluye un campo **Rama** para especificar la rama del repositorio que se debe utilizar para la entrada.
  2. En el separador **TRABAJOS**, añada y configure al menos un trabajo. La primera etapa normalmente tiene como mínimo un trabajo de compilación.
3. Pulse **GUARDAR**.

## Adición de un trabajo a una etapa
{: #deliverypipeline_add_job}

1. En la etapa, pulse el icono **Configuración de etapa** y, a continuación, pulse **Configurar etapa**.
2. Pulse el separador **TRABAJOS**.
3. Pulse **AÑADIR TRABAJO**. Seleccione el tipo de trabajo para añadir.
4. Configurar el trabajo.
5. Pulse **GUARDAR**.

![Adición de un trabajo a una etapa](images/AddJob2.png)

## Ejecución de una etapa
{: #deliverypipeline_run_stage}

Puede ejecutar de manera manual una etapa pulsando el icono **Ejecutar etapa** en la página Conducto.

![Al pulsar el icono Run Stage en una etapa](images/RunStage.png)

También puede solicitar compilaciones y despliegues a demanda desde la página de historial de compilaciones de una de estas dos formas:
* Arrastre una compilación al recuadro que hay bajo una etapa configurada.
* En la sección LAST EXECUTION RESULT, pulse el icono **Enviar a** y, a continuación, seleccione un espacio en el que desplegarlo.
  ![La etapa Ejecutar con este icono de compilación](images/deploy_to.png)

Para cancelar una etapa de ejecución, en la etapa, pulse **Ver registros e historial**. En la lista de trabajos, pulse el número del trabajo en ejecución y, a continuación, pulse **CANCELAR**. También puede cancelar trabajos individualmente pulsando un trabajo y, a continuación, pulsando **CANCELAR**, o pulsando el icono **Detener** de un trabajo en su etapa.

## Despliegue de una app
{: #deliverypipeline_deploy}

Un trabajo de despliegue configurado correctamente despliega la app al destino siempre que se ejecute el trabajo. Para ejecutar manualmente un trabajo de despliegue, pulse el icono **Etapa de ejecución** de la etapa en la que se encuentra el trabajo.

### Revisiones de entrada
{: #deliverypipeline_input_revisions}

Al ejecutar una etapa manualmente, o si la ejecuta porque la etapa anterior se ha completado, la etapa de ejecución selecciona su revisión de entrada. Normalmente, la revisión de entrada es un número de compilación. Para seleccionar la revisión de entrada, la etapa seguirá estas condiciones:

* Si se selecciona una revisión específica, utilícela.
* Si no se especifica una revisión específica, busque etapas anteriores hasta que se encuentre una etapa que utilice la misma entrada. Busque y utilice la última revisión de ejecución correcta de dicha entrada.
* Si no se especifica una revisión específica y ninguna otra etapa utiliza el origen especificado como entrada, utilice la revisión más reciente de la entrada.

Puede desplegar una compilación anterior. En la etapa que contiene la compilación, pulse **Ver registros e historial**. En la página que se abre, pulse para expandir el número de ejecución y, a continuación, pulse el trabajo de compilación. Pulse **ENVIAR A**, y seleccione un destino.
{: tip}

### Adición de servicios a apps
{: #deliverypipeline_add_services}

Puede añadir servicios a las apps y gestionar los servicios desde el panel de control de {{site.data.keyword.Bluemix_notm}} o la interfaz de línea de mandatos (CLI) de Cloud Foundry. También puede emitir mandatos de CLI de Cloud Foundry en scripts para trabajos de conductos. Por ejemplo, puede añadir un servicio a una app en el script de un trabajo de despliegue. Para obtener más información sobre cómo añadir servicios, consulte [Conexión de servicios a apps externas](/docs/resources?topic=resources-externalapp).

## Visualización de registros
{: #deliverypipeline_view_logs}

Puede ver los registros para trabajos y ver etapas a medida que se ejecutan en la página Historial de etapas.

1. Para ver el registro de un trabajo, pulse el trabajo. Como alternativa, en una etapa, pulse **Ver registros e historial**.

2. Para ver el registro de tiempo de ejecución de una aplicación desplegada, pulse **Ver registro de tiempo de ejecución**.

Además de los registros de trabajos, puede ver resultados de pruebas de unidades, artefactos generados y cambios de códigos para cualquier trabajo de compilación.

También puede ejecutar, volver a desplegar, cancelar o configurar una etapa desde la página Historial de etapas. Pulse **EJECUTAR** para ejecutar la etapa, **VOLVER A DESPLEGAR** para volver a desplegar si se trata de un trabajo de despliegue o **CONFIGURAR** para configurar una etapa. Mientras una etapa está en ejecución, puede cancelarla pulsando el número de ejecución y, a continuación, pulsando **CANCELAR**.

### Descarga de registros de un script
{: #deliverypipeline_download_logs}

Puede descargar el archivo de registro para un trabajo de conducto a partir de un script y guardar el `PIPELINE_LOG_URL` que se proporciona mientras se ejecuta el trabajo de conducto. En el ejemplo siguiente se muestran los pasos para cargar el archivo de registro del trabajo de conducto en un sistema distinto.


1. Configure una propiedad del entorno `JOB_LOG` para la etapa.

1. En el trabajo de conducto, guarde `PIPELINE_LOG_URL`.

   ```shell
   export JOB_LOG="$PIPELINE_LOG_URL"
   ```
1. Utilice `PIPELINE_LOG_URL` en un trabajo posterior dentro de la misma etapa para descargar el archivo de registro para exportarlo a un sistema distinto. Utilice una señal portadora de IBM Cloud para acceder al archivo de registro.

   ```shell
   ibmcloud login -a api.ng.bluemix.net \
     --apikey <INSERT API KEY HERE>

   BEARER=$( ibmcloud iam oauth-tokens | grep "IAM token" | sed 's/^.*Bearer //g' )

   curl -H "Authorization: Bearer $BEARER"  \
     -H "Accept: text/plain" \
     -D /tmp/headers.txt \
     -o job_log.txt \
     "$JOB_LOG"
   ```
1. Compruebe la cabecera `X-More-Data`. Si la cabecera se establece en `true`, el archivo de registro se está generando o procesando. Si la cabecera se establece en `false`, el archivo de registro está listo para su uso.

   ```shell
   grep X-More-Data /tmp/headers.txt
   X-More-Data: false
   ```
1. Suba el archivo de registro a su sistema.

   ```shell
   scp job_log.txt user@example.org:/job1/logs
   ```


### Descarga de artefactos de un script
{: #deliverypipeline_download_artifacts}

Puede descargar los artefactos para un trabajo de compilación de conducto a partir de un script y guardar el `PIPELINE_ARTIFACT_URL` que se proporciona mientras se ejecuta el trabajo de conducto. En el ejemplo siguiente se muestran los pasos para cargar los artefactos del trabajo de conducto en un sistema distinto.


1. Configure una propiedad de entorno `JOB_ARTIFACT` para la etapa.

1. En el trabajo de conducto, guarde `PIPELINE_ARTIFACT_URL`.

   ```shell
   export JOB_ARTIFACT="$PIPELINE_ARTIFACT_URL"
   ```
   
1. Utilice `PIPELINE_ARTIFACT_URL` en un trabajo posterior dentro de la misma etapa para descargar los artefactos para exportarlos a un sistema distinto. Utilice una señal portadora de IBM Cloud para acceder a los artefactos.

   ```shell
   ibmcloud login -a api.ng.bluemix.net \
     --apikey <INSERT API KEY HERE>

   BEARER=$( ibmcloud iam oauth-tokens | grep "IAM token" | sed 's/^.*Bearer //g' )

   DOWNLOAD_URL=$( curl -H "Authorization: Bearer $BEARER"  \
     "$JOB_ARTIFACT" )

   curl -O  "$DOWNLOAD_URL"
   ```
   
1. Cargue los artefactos en el sistema.

   ```shell
   scp $(basename "$DOWNLOAD_URL") user@example.org:/job1/artifacts
   ```
