---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-19"

keywords: IBM Cloud Continuous Delivery, GitHub tool integration, error message

subcollection: ContinuousDelivery

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:faq: data-hd-content-type='faq'}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# Preguntas más frecuentes
{: #ts_cd}

Aquí encontrará respuestas a las preguntas más frecuentes sobre el uso de {{site.data.keyword.contdelivery_full}}.
{:shortdesc}

## ¿Por qué la página Cadenas de herramientas muestra que se ha excedido el plan Lite del servicio de {{site.data.keyword.contdelivery_short}}?
{: #plan_exceeded}
{: faq}

{{site.data.keyword.contdelivery_short}} ofrece dos planes: Lite y Professional. Si tiene el plan Lite de {{site.data.keyword.contdelivery_short}}, puede utilizar cadenas de herramientas de forma gratuita, hasta los límites del plan. El mensaje de error indica que ha sobrepasado uno o más límites del plan Lite. Por ejemplo, puede superar el plan si tiene demasiados usuarios autorizados que están asociados a la instancia de servicio de {{site.data.keyword.contdelivery_short}}, o si ha ejecutado el número máximo de trabajos de {{site.data.keyword.deliverypipeline}}. Para obtener más información sobre los términos del plan, consulte [Limitaciones y uso del plan](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).


## El servicio My {{site.data.keyword.contdelivery_short}} indica que los servicios de plan Lite se suprimen después de 30 días de inactividad. ¿Qué significa inactividad?
{: #plan_inactivity}
{: faq}

Una instancia del servicio de {{site.data.keyword.contdelivery_short}} se considera activa cuando una o varias de las cadenas de herramientas dentro del mismo grupo de recursos o la organización (org) de Cloud Foundry están activas. Se considera que una cadena de herramientas está activa si los usuarios interactúan con ella mediante la interfaz de usuario, se desencadenan trabajos de conducto de entrega, se accede a repositorios gestionados por {{site.data.keyword.gitrepos}} o hay espacios de trabajo de Eclipse Orion {{site.data.keyword.webide}} en uso. Para que se considere como inactiva, todas estas condiciones deben estar ausentes para todas las cadenas de herramientas asociadas con el servicio de {{site.data.keyword.contdelivery_short}}, durante 30 días.


## He creado una cadena de herramientas, ¿por qué la página Cadenas de herramientas muestra que se necesita un servicio de Continuous Delivery?
{: #service_required_resource_group}
{: faq}

Los términos del plan para la instancia de servicio de {{site.data.keyword.contdelivery_short}} que se encuentra en el mismo grupo de recursos u organización que la cadena de herramientas gestiona el uso de algunas de las integraciones de herramientas ({{site.data.keyword.deliverypipeline}}, Eclipse Orion {{site.data.keyword.webide}} y {{site.data.keyword.gitrepos}}) contenidas en el servicio. El mensaje de error indica que el grupo de recursos o la organización no contiene la instancia necesaria del servicio de {{site.data.keyword.contdelivery_short}}. Para obtener más información sobre los términos del plan, consulte [Limitaciones y uso del plan](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).


## He actualizado información de una cadena de herramientas desde una organización de Cloud Foundry. ¿Por qué no veo mis cambios en la cadena de herramientas?
{: #updates_in_cloud_foundry}
{: faq}

Cuando actualiza la información de la cadena de herramientas directamente desde Cloud Foundry, el servicio de {{site.data.keyword.contdelivery_short}} puede tardar unos minutos en renovarse y mostrar los cambios. Por ejemplo, si añade o elimina un usuario desde una organización de Cloud Foundry, {{site.data.keyword.contdelivery_short}} puede tardar unos minutos en descubrir que hay un nuevo usuario y permitir que el usuario acceda a la cadena de herramientas.


## He creado una cadena de herramientas en una organización de Cloud Foundry, ¿por qué la página Cadenas de herramientas muestra que se necesita un servicio de Continuous Delivery?
{: #service_required_cloud_foundry}
{: faq}

Cuando se crea una cadena de herramientas en un grupo de recursos u organización que no tiene una instancia del servicio de {{site.data.keyword.contdelivery_short}}, la plataforma de la cadena de herramientas intenta crear automáticamente una instancia del servicio utilizando el plan Lite. El mensaje de error indica que la plataforma de la cadena de herramientas no ha podido crear la instancia de servicio.

Este error se puede producir al crear una cadena de herramientas en la región EE.UU. sur y en una organización de Cloud Foundry que no tenga todavía una instancia de {{site.data.keyword.contdelivery_short}}. En la región EE.UU. sur, debe crear todas las instancias nuevas del servicio {{site.data.keyword.contdelivery_short}} en grupos de recursos. 

Puede crear la cadena de herramientas en un grupo de recursos o crear la cadena de herramientas en una organización que ya tenga una instancia de {{site.data.keyword.contdelivery_short}}.
  

## ¿Cómo puedo mover mi cadena de herramientas desde una organización de Cloud Foundry a un grupo de recursos?
{: #toolchain_move_to_resource_group}
{: faq}

Todavía no hay disponible ninguna característica para migrar automáticamente las cadenas de herramientas desde una organización de Cloud Foundry a un grupo de recursos. En su lugar, puede volver a crear manualmente la cadena de herramientas en un grupo de recursos y, a continuación, eliminar la cadena de herramientas original de la organización de Cloud Foundry.


## He intentado desplegar una app en {{site.data.keyword.Bluemix_notm}}. ¿Por qué aparece un error?
{: #org_outofmemory}
{: faq}

Al intentar desplegar una app en {{site.data.keyword.Bluemix_notm}}, si obtiene el siguiente mensaje de error, la cantidad de memoria que queda en la organización es menor que la cantidad de memoria que necesita la app que quiere desplegar.

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.`

Puede aumentar la cuota de memoria de su cuenta o reducir la memoria que utilizan las apps. El máximo de cuota de memoria para una cuenta de prueba es de 2 GB. Para aumentar la cuota de memoria de su cuenta, convierta su cuenta de prueba en una cuenta de pago. Para obtener más información sobre cómo convertir su cuenta de prueba en una cuenta de pago, consulte [¿Cómo actualizo o cambio mi cuenta?](/docs/account?topic=account-accountfaqs#changeacct). Para reducir la memoria que utilizan las apps, utilice la consola de {{site.data.keyword.Bluemix_notm}} o la interfaz de línea de mandatos cf.

Si utiliza la consola de {{site.data.keyword.Bluemix_notm}}, siga estos pasos:

1. En el panel de control Apps, seleccione su app. Se abre la página de detalles de la app.
1. En el panel tiempo de ejecución, puede reducir el límite máximo de memoria o el número de instancias de la app, o ambos, para la app que desee.

Si utiliza la interfaz de la línea de mandatos cf, efectúe los pasos siguientes:

1. Compruebe cuánta memoria están utilizando las apps. El mandato cf apps lista todas las apps desplegadas en el espacio actual. También se visualiza el estado de cada app.

	  ```
	  cf apps
	  ```

1. Para reducir la cantidad de memoria que utiliza la app, puede reducir el número de instancias de la app, el límite máximo de memoria o ambos:

	  ```
	  cf push appname -p vía_acceso_app -i número_instancia -m límite_memoria
      ```
    
1. Reinicie la app para que se apliquen los cambios.


## He creado una app. ¿Por qué no se muestran los iconos de {{site.data.keyword.Bluemix_notm}} Live Sync en la barra de ejecución de {{site.data.keyword.webide}}?
{: #ts_llz_lkb_3r}
{: faq}

![Barra de ejecución](images/webide_runbar_light.png)   

Al editar una app de Node.js en {{site.data.keyword.webide}}, los iconos de {{site.data.keyword.Bluemix_notm}} de edición en directo, reinicio rápido y depuración no están disponibles en la barra de ejecución en estas circunstancias:


* El archivo `manifest.yml` no está almacenado en el nivel superior del proyecto.
* La app está almacenada en un subdirectorio en lugar de en la raíz, pero la vía de acceso al subdirectorio no está especificada en el archivo `manifest.yml`.
* La app no contiene un archivo `package.json`.


Si el archivo `manifest.yml` no está almacenado en la raíz, almacénelo allí. Si la app está almacenada en un subdirectorio, especifique la vía de acceso al subdirectorio en el archivo `manifest.yml`. Si la app no contiene un archivo `package.json`, cree uno que esté en el mismo directorio que la app.


## He pulsado el botón de ejecución de {{site.data.keyword.webide}}. ¿Dónde están los archivos de registro? 
{: #web_ide_log_files}
{: faq}  

Cuando pulsa el botón Ejecutar, el contenido del espacio de trabajo se envía por push a Cloud Foundry de la misma forma en la que se despliega si escribe `cf push` desde el escritorio. Puede encontrar los archivos de registro desde el panel de control de Cloud Foundry.

Para obtener más información sobre el despliegue del contenido del espacio de trabajo, consulte [Despliegue de una app desde el espacio de trabajo](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#deploy).


## ¿Cómo puedo evitar que {{site.data.keyword.webide}} seleccione automáticamente todos los cambios en la vista de Git? 
{: #web_ide_git_view}
{: faq} 

{{site.data.keyword.webide}} presupone de forma predeterminada que desea enviar por push los cambios salientes al repositorio de código cada vez que va a la página de Git. Si desea seleccionar manualmente qué recursos se van a confirmar, sincronizar, restablecer y sustituir, en la página de preferencias de GIT, desmarque el recuadro de selección **Seleccionar siempre archivos modificados**.


## ¿Por qué {{site.data.keyword.webide}} no soporta el idioma que utilizo? 
{: #web_ide_language_support}
{: faq}  

{{site.data.keyword.webide}} proporciona amplias herramientas y soporte para JavaScript, HTML y CSS. También proporciona realce de la sintaxis para los idiomas más populares. No se puede ampliar {{site.data.keyword.webide}} para dar soporte a un idioma determinado. Para ver una lista completa de los idiomas a los que da soporte {{site.data.keyword.webide}}, consulte [Idiomas soportados](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#supported_languages).


## ¿Cómo puedo encontrar el estado de {{site.data.keyword.Bluemix_notm}} y el servicio de {{site.data.keyword.contdelivery_short}}?
{: #toolchains_load}
{: faq}

Consulte la página Estado de {{site.data.keyword.Bluemix_notm}} para determinar si hay problemas conocidos que afecten a la plataforma {{site.data.keyword.Bluemix_notm}} y a los principales servicios en {{site.data.keyword.Bluemix_notm}}.

Para ver la página Estado, seleccione una de las dos opciones siguientes:

  * Inicie la sesión en la consola de {{site.data.keyword.Bluemix_notm}}. En la barra de menús, pulse **Soporte** y seleccione **Estado**. Compruebe la lista de recursos en busca del icono ![algunos problemas](../../get-support/images/some_issues.svg). Este icono podría indicar una parada.
  * Acceda directamente a [{{site.data.keyword.Bluemix_notm}} - Estado del sistema](https://cloud.ibm.com/status){: external}.

Para obtener más información sobre la página Estado de {{site.data.keyword.Bluemix_notm}}, consulte [Visualización del estado de {{site.data.keyword.Bluemix_notm}}](/docs/get-support?topic=get-support-viewing-cloud-status#viewing-cloud-status).


## ¿Cómo puedo pasar artefactos entre trabajos de conducto?
{: #artifacts_pipeline_jobs}
{: faq}

Puesto que todos los trabajos de conducto de una etapa reciben la misma entrada de etapa, no se pueden pasar artefactos entre trabajos que se encuentran en la misma etapa. Sin embargo, los trabajos de compilación generan artefactos que pueden utilizar los trabajos en otras etapas. Para pasar artefactos entre dos trabajos, mueva cada trabajo a una etapa distinta. Para obtener más información sobre los trabajos de conducto, consulte [Trabajos](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_jobs).


## ¿Hay un límite de tiempo máximo durante el que se pueden ejecutar los trabajos de conducto?
{: #pipeline_jobs_time_limit}
{: faq}

Cada trabajo de conducto se puede ejecutar durante un máximo de 60 minutos. Si un trabajo supera este límite de tiempo, el trabajo falla. Examine si el trabajo que realiza el trabajo de conducto se puede dividir en pasos más pequeños. Puede dividir el trabajo de conducto en varios trabajos de conducto más cortos que se ejecuten durante menos de 60 minutos.


## ¿Qué grado de seguridad tienen las propiedades seguras de conducto?
{: #pipeline_secure_properties}
{: faq}

Las propiedades seguras de conducto se cifran mediante AES-128 y se descifran inmediatamente antes de pasarse al script de conducto. Estas propiedades también se ocultan utilizando asteriscos en la interfaz de usuario de propiedades y en los archivos de registro de conducto. Antes de que se escriban los datos en el archivo de registro del trabajo de conducto, se explora para buscar coincidencias exactas con todos los valores de las propiedades seguras de conducto. Si se encuentra una coincidencia, se oculta utilizando asteriscos. Tenga cuidado al trabajar con archivos de registro y propiedades seguras, ya que sólo se ocultan las coincidencias exactas. 
