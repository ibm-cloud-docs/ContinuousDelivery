---

copyright:
  years: 2015, 2017
lastupdated: "2017-5-25"

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Resolución de problemas de {{site.data.keyword.contdelivery_short}}
{: #ts_cd}

Aquí encontrará respuestas a preguntas comunes sobre la resolución de problemas al utilizar {{site.data.keyword.contdelivery_full}}.
{:shortdesc}


## No se puede autorizar con GitHub
{: #cannot_authorize_github}

No está autorizado con GitHub.
{:shortdesc}

Si tiene está autorizado por {{site.data.keyword.Bluemix_notm}} para acceder a la cuenta de GitHub, puede producirse uno de estos problemas:
{: tsSymptoms}

 * Cuando intente añadir la integración de herramientas de GitHub a la cadena de herramientas, la integración de herramientas no se añade.
 * El conducto no se ejecuta automáticamente cuando se envían cambios en el repositorio de GitHub o GitHub Enterprise.

{{site.data.keyword.Bluemix_notm}} no está autorizado para acceder a GitHub.  
{: tsCauses}

Si configura la integración de esta herramienta de GitHub mientras crea la cadena de herramientas, siga estos pasos:
{: tsResolve}

  1. En la sección Integraciones configurables, pulse **GitHub**.
  1. Si está creando la cadena de herramientas en {{site.data.keyword.Bluemix_notm}} Público y no ha autorizado a {{site.data.keyword.Bluemix_notm}} acceso a GitHub, pulse **Autorizar** para ir al sitio web de GitHub.
  1. Si no tiene ninguna sesión de GitHub activa, se le solicitará que inicie sesión. Pulse **Autorizar aplicación** para permitir que {{site.data.keyword.Bluemix_notm}} acceda a su cuenta de GitHub. Si tiene una sesión activa de GitHub pero no ha introducido recientemente su contraseña, es posible que se le solicite que introduzca la contraseña de GitHub para confirmarla.

Si ya tiene una cadena de herramientas, actualice la configuración de la integración de herramientas de GitHub:

 1. En el panel de control de DevOps, en la página **Cadenas de herramientas**, pulse sobre la cadena de herramientas para abrir la página Visión general correspondiente. Si lo prefiere, en la página Visión general de la app, tarjeta Entrega continua, pulse **Ver cadena de herramientas** y, a continuación, **Visión general**.
 1. En la tarjeta GitHub, pulse el menú y pulse **Configurar**.
 1. Actualice los valores de configuración para autorizar a {{site.data.keyword.Bluemix_notm}} para acceder a GitHub. Pulse **Autorizar** para ir al sitio web de GitHub. Si no tiene ninguna sesión de GitHub activa, se le solicitará que inicie sesión. Pulse **Autorizar aplicación** para permitir que {{site.data.keyword.Bluemix_notm}} acceda a su cuenta de GitHub. Si tiene una sesión activa de GitHub pero no ha introducido recientemente su contraseña, es posible que se le solicite que introduzca la contraseña de GitHub para confirmarla.
 1. Cuando haya terminado de configurar los ajustes, pulse **Guardar integración**.


## No se puede crear una cadena de herramientas
{: #cannot_create_toolchain}

Se muestra un error al crear una cadena de herramientas.
{:shortdesc}

Cuando crea una cadena de herramientas, ve el siguiente mensaje de error:
{: tsSymptoms}

`Esta organización contiene 200 cadenas de herramientas, que es el límite máximo. Antes de que pueda añadir otra cadena de herramientas, elimine una o varias cadenas de herramientas de la organización.`


No puede tener más de 200 cadenas de herramientas en una organización (org).  
{: tsCauses}

Elimine una o varias cadenas de herramientas de su organización y, a continuación, cree la cadena de herramientas de nuevo.
{: tsResolve}


## Se ha superado el límite memoria de la organización
{: #org_outofmemory}

Es posible que no pueda desplegar una app en {{site.data.keyword.Bluemix_notm}} si supera el límite de memoria de su organización. Puede reducir la memoria que utilizan las apps o aumentar la cuota de memoria de su cuenta. El máximo de cuota de memoria para una cuenta de prueba es de 2 GB y únicamente se puede incrementar pasando a una cuenta de pago.

Al desplegar una app en {{site.data.keyword.Bluemix_notm}}, verá el siguiente mensaje de error:
{: tsSymptoms}

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.`

Este error se produce cuando la cantidad de memoria que queda para la organización es menos que la cantidad de memoria que la app que quiere desplegar necesita. El máximo de cuota de memoria para una cuenta de prueba es de 2 GB.
{: tsCauses}

Puede aumentar la cuota de memoria de su cuenta o reducir la memoria que utilizan las apps.
{: tsResolve}

  * Para aumentar la cuota de memoria de su cuenta, convierta su cuenta de prueba en una cuenta de pago. Para obtener más información sobre cómo convertir su cuenta de prueba en una cuenta de pago, consulte [Cuentas de pago](/docs/pricing/index.html#pay-accounts).
  * Para reducir la memoria que utilizan las apps, utilice la consola de {{site.data.keyword.Bluemix_notm}} o la interfaz de línea de mandatos cf.
    

    Si utiliza la consola de {{site.data.keyword.Bluemix_notm}}, siga estos pasos:

    1. En el panel de control Apps, seleccione su app. Se abre la página de detalles de la app.
    2. En el panel tiempo de ejecución, puede reducir el límite máximo de memoria o el número de instancias de la app, o ambos, para la app que desee.

    Si utiliza la interfaz de la línea de mandatos cf, efectúe los pasos siguientes:

    1. Compruebe cuánta memoria están utilizando las apps:

	  ```
	  cf apps
	  ```

	  El mandato cf apps lista todas las apps desplegadas en el espacio actual. También se visualiza el estado de cada app.

    2. Para reducir la cantidad de memoria que utiliza la app, puede reducir el número de instancias de la app, el límite máximo de memoria o ambos:

	  ```
	  cf push appname -p vía_acceso_app -i número_instancia -m límite_memoria
      ```

    3. Reinicie la app para que se apliquen los cambios.

Para obtener más información sobre los problemas generales al gestionar sus apps, consulte [Resolución de problemas de gestión de apps](https://console.bluemix.net/docs/troubleshoot/ts_apps.html#managingapps).


## La cadena de herramientas no se carga
{: #toolchains_load}

Cuando pulsa sobre una cadena de herramientas para ver su página de Visión general, no se carga.
{:shortdesc}

En el panel de control de DevOps, en la página **Cadenas de herramientas**, pulsa sobre la cadena de herramientas para abrir su página Visión general. Como alternativa, en la página Visión general de la app, en la tarjeta de Entrega continua, pulse **Ver cadena de herramientas**. A continuación, pulse **Visión general**. La página de Visión general para la cadena de herramientas no se abre.
{: tsSymptoms}

Compruebe el estado de {{site.data.keyword.Bluemix_notm}} para ver si el problema está originado por una interrupción en el servicio.
{: tsCauses}

Consulte la página Estado de {{site.data.keyword.Bluemix_notm}} para determinar si hay problemas conocidos que afecten a la plataforma {{site.data.keyword.Bluemix_notm}} y a los principales servicios en {{site.data.keyword.Bluemix_notm}}.
{: tsResolve}

Para ver la página Estado, seleccione una de las dos opciones siguientes:

  * Inicie la sesión en la consola de {{site.data.keyword.Bluemix_notm}}. En la barra de menús, pulse **Soporte** y seleccione **Estado**. Compruebe la lista de recursos en busca del icono ![algunos problemas](../../support/images/some_issues.svg). Este icono podría indicar una parada.
  * Acceda directamente a [IBM {{site.data.keyword.Bluemix_notm}} - Estado del sistema ![icono de enlace externo](../../icons/launch-glyph.svg "icono de enlace externo")](http://ibm.biz/bluemixstatus){: new_window}.

Para obtener más información sobre la página Estado de {{site.data.keyword.Bluemix_notm}}, consulte [
Visualización del estado de {{site.data.keyword.Bluemix_notm}}](https://console.bluemix.net/docs/support/index.html#viewing-bluemix-status).


## La integración de herramientas no está configurada
{: #tool_integration_error}

Después de configurar una integración de herramientas para su cadena de herramientas, se muestra el error `Error de configuración` en su tarjeta de la herramienta.
{:shortdesc}

Después de configurar una integración de herramientas, puede ver su tarjeta de herramienta en la página Visión general de la cadena de herramientas y ver que la configuración ha fallado.
{: tsSymptoms}

 ![Error de configuración](images/tool_setup_failed.png)

Cuando añade una integración de herramientas, la cadena de herramientas se comunica con la herramienta representada mediante la integración de herramientas para suministrar los recursos necesarios y asociarlos con la cadena de herramientas. Si se produce un error durante el proceso de configuración o si la comunicación entre la cadena de herramientas y la herramienta no se establece correctamente, la integración de herramientas se coloca en un estado de error.
{: tsCauses}

Vuelva a configurar la integración de herramientas:
{: tsResolve}

1. En su tarjeta de herramienta, mueva el cursor sobre el mensaje `Error de configuración` y pulse **Volver a configurar**.

 ![Botón Volver a configurar](images/tool_reconfigure.png)

1. Asegúrese de utilizar parámetros de configuración válidos. Si el error está causado por una configuración no válida, se muestra un mensaje de error; por ejemplo, `La integración se ha podido configurar. Compruebe la configuración y vuelva a intentarlo. Razón: api_key:fakeKey no válido`. Actualice los valores de la integración de herramientas y pulse **Guardar integración**.
1. Si el error está causado por un problema de comunicación, pulse **Guardar integración** para intentarlo de nuevo.
