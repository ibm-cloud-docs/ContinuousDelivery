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

Si {{site.data.keyword.Bluemix_notm}} no está autorizado para acceder a la cuenta de GitHub, se puede producir cualquiera de estos problemas:
{: tsSymptoms}

 * Cuando intente añadir la integración de herramientas de GitHub a la cadena de herramientas, la integración de herramientas no se añade.
 * El conducto no se ejecuta automáticamente cuando se envían cambios en el repositorio de GitHub o GitHub Enterprise.

{{site.data.keyword.Bluemix_notm}} no está autorizado para acceder a GitHub.  
{: tsCauses}

Si configura la integración de esta herramienta de GitHub mientras crea la cadena de herramientas, siga estos pasos:
{: tsResolve}

  1. En la sección Integraciones configurables, pulse **GitHub**.
  1. Si está creando la cadena de herramientas en {{site.data.keyword.Bluemix_notm}} Público y {{site.data.keyword.Bluemix_notm}} no está autorizado para acceder a GitHub, pulse **Autorizar** para ir al sitio web de GitHub.
  1. Si no tiene ninguna sesión de GitHub activa, se le solicitará que inicie sesión. Pulse **Autorizar aplicación** para permitir que {{site.data.keyword.Bluemix_notm}} acceda a su cuenta de GitHub. 

Si ya tiene una cadena de herramientas, actualice la configuración de la integración de herramientas de GitHub:

 1. En el panel de control de DevOps, en la página **Cadenas de herramientas**, pulse sobre la cadena de herramientas para abrir la página Visión general correspondiente. Si lo prefiere, en la página Visión general de la app, tarjeta Entrega continua, pulse **Ver cadena de herramientas** y, a continuación, **Visión general**.
 1. En la tarjeta GitHub, pulse el menú y pulse **Configurar**.
 1. Actualice los valores de configuración para autorizar a {{site.data.keyword.Bluemix_notm}} para acceder a GitHub. Pulse **Autorizar** para ir al sitio web de GitHub. Si no tiene ninguna sesión de GitHub activa, se le solicitará que inicie sesión. Pulse **Autorizar aplicación** para permitir que {{site.data.keyword.Bluemix_notm}} acceda a su cuenta de GitHub. 
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

Es posible que no pueda desplegar una app en {{site.data.keyword.Bluemix_notm}} si supera el límite de memoria de su organización. Puede reducir la memoria que utilizan las apps o aumentar la cuota de memoria de su cuenta. El máximo de cuota de memoria para una cuenta de prueba es de 2 GB. La cuota se puede incrementar al actualizar a una cuenta de pago.

Al desplegar una app en {{site.data.keyword.Bluemix_notm}}, verá el siguiente mensaje de error:
{: tsSymptoms}

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.`

Este error se produce cuando la cantidad de memoria que queda para la organización es menos que la cantidad de memoria que la app que quiere desplegar necesita. El máximo de cuota de memoria para una cuenta de prueba es de 2 GB.
{: tsCauses}

Puede aumentar la cuota de memoria de su cuenta o reducir la memoria que utilizan las apps.
{: tsResolve}

  * Para aumentar la cuota de memoria de su cuenta, convierta su cuenta de prueba en una cuenta de pago. Para obtener más información sobre cómo convertir su cuenta de prueba en una cuenta de pago, consulte [Cuentas de pago](/docs/pricing/index.html#pay-accounts).
  * Para reducir la memoria que utilizan las apps, utilice la consola de {{site.data.keyword.Bluemix_notm}} o la interfaz de línea de mandatos de cf.

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


## La barra de ejecución no mostrará los iconos de Bluemix Live Sync en Eclipse Orion Web IDE
{: #ts_llz_lkb_3r}

Ha creado una app, pero los iconos de IBM Bluemix Live Sync no se muestran en la barra de ejecución de Eclipse Orion Web IDE. No verá la barra de ejecución completa con los iconos de Live Edit:

![Barra de ejecución](images/webide_runbar_light.png)   

Al editar una app de Node.js en Web IDE, los iconos de {{site.data.keyword.Bluemix_notm}} Live de editar, reinicio rápido y depurar no se muestran en la barra de ejecución.
{: tsSymptoms}

Los iconos no estarán disponibles en estas circunstancias:
{: tsCauses}

* El archivo `manifest.yml` no está almacenado en el nivel superior del proyecto.
* La app está almacenada en un subdirectorio en lugar de en la raíz, pero la vía de acceso al subdirectorio no está especificada en el archivo `manifest.yml`.
* La app no contiene un archivo `package.json`.

Utilice uno de los métodos siguientes:
{: tsResolve}

* Si el archivo `manifest.yml` no está almacenado en la raíz, almacénelo allí.
* Si la app está almacenada en un subdirectorio, especifique la vía de acceso al subdirectorio en el archivo `manifest.yml`.
   ```
    path: path_to_application
    ```
* Cree un archivo `package.json` que esté en el directorio de la app.


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



<!-- ## Pipeline job failures
{: #cannot_authorize_github}

A pipeline job failed.
{:shortdesc}

Your pipeline job failed.
{: tsSymptoms}

 * Some reasons

Many reasons  
{: tsCauses}

If you are configuring the GitHub tool integration while you are creating your toolchain, follow these steps:
{: tsResolve}

  1. In the Configurable Integrations section, click **GitHub**.
  1. If you are creating the toolchain on {{site.data.keyword.Bluemix_notm}} Public and you have not authorized {{site.data.keyword.Bluemix_notm}} to access GitHub, click **Authorize** to go to the GitHub website.
  1. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account. If you have an active GitHub session but you haven't entered your password recently, you might be prompted to enter your GitHub password to confirm.

If you already have a toolchain, update the GitHub tool integration's configuration:

 1. On the DevOps dashboard, on the **Toolchains** page, click the toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**, and then click **Overview**.
 1. On the GitHub card, click the menu and click **Configure**.
 1. Update the configuration settings to authorize {{site.data.keyword.Bluemix_notm}} to access GitHub. Click **Authorize** to go to the GitHub website. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account. If you have an active GitHub session but you haven't entered your password recently, you might be prompted to enter your GitHub password to confirm.
 1. When you are finished updating the settings, click **Save Integration**.  -->




<!-- This is the template for a problem topic.  -->

<!-- The short description section contains a brief description of problem. For example:  

After you create an app on the Dashboard, you click *ADD GIT* to create a Git repository, but you cannot proceed.
{:shortdesc} -->

<!-- The symptoms section contains a description of problem symptoms. For example:  
When you click ADD GIT, a window opens and one of these issues occur:
- The window hangs with a blank screen.
- A message states that a problem exists with 3rd party cookies.
{: tsSymptoms} -->

<!-- The causes section contains a brief explanation of what causes the problem. For example:  
Your browser might be configured to prevent a cookie from being set. That cookie must be set from the IBM Bluemix DevOps Services site in the hub.jazz.net internet domain from within the context of the Bluemix console.
{: tsCauses} -->

<!-- The resolve section contains steps to resolve the problem. For example:  
You can fix this problem in one of three ways:
- Follow the instructions that are in the window that opens from the Bluemix console. Click the button. Another browser window opens temporarily. In that window, DevOps Services sets the authentication cookie.
- In another browser tab, go to https://hub.jazz.net and log in. Return to the Bluemix console and refresh the page. Click ADD GIT again.
- Change your browser settings to enable 3rd party cookies and click ADD GIT again.
{: tsResolve} -->
