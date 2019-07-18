---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-20"

keywords: troubleshoot, IBM Cloud Continuous Delivery

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:tip: .tip}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# Resolución de problemas de {{site.data.keyword.contdelivery_short}}
{: #troubleshoot-cd}

Los problemas generales que se pueden producir al utilizar {{site.data.keyword.contdelivery_full}} incluyen autenticación de GitHub, creación del conducto, configuración de integración de herramientas o problemas de Cloud Foundry. En muchos de los casos, puede solucionar estos problemas siguiendo unos sencillos pasos.
{:shortdesc}

## He intentado añadir la integración de herramientas de GitHub a la cadena de herramientas. ¿Por qué no se añade la integración de herramientas?
{: troubleshoot-cannot-authorize-github}
{: troubleshoot}

Debe autorizar en GitHub para que {{site.data.keyword.Bluemix_notm}} esté autorizado para acceder a la cuenta de GitHub.

La integración de herramientas de GitHub no se ha añadido a la cadena de herramientas.
{: tsSymptoms}

Si {{site.data.keyword.Bluemix_notm}} no está autorizado para acceder a la cuenta de GitHub, la integración de herramientas no se añade a la cadena de herramientas.
{: tsCauses}

Si configura la integración de herramientas de GitHub mientras crea la cadena de herramientas, siga estos pasos para autorizar a GitHub:
{: tsResolve}

  1. En la sección Integraciones configurables, pulse **GitHub**.
  1. Si está creando la cadena de herramientas en {{site.data.keyword.Bluemix_notm}} Público y {{site.data.keyword.Bluemix_notm}} no está autorizado para acceder a GitHub, pulse **Autorizar** para ir al sitio web de GitHub.
  1. Si no tiene ninguna sesión de GitHub activa, se le solicitará que inicie sesión. Pulse **Autorizar aplicación** para permitir que {{site.data.keyword.Bluemix_notm}} acceda a su cuenta de GitHub.

Si ya tiene una cadena de herramientas, actualice la configuración de la integración de herramientas de GitHub:

 1. En el panel de control de DevOps, en la página **Cadenas de herramientas**, pulse sobre la cadena de herramientas para abrir la página Visión general correspondiente. Si lo prefiere, en la página Visión general de la app, tarjeta Entrega continua, pulse **Ver cadena de herramientas** y, a continuación, **Visión general**.
 1. En la tarjeta GitHub, pulse el menú y pulse **Configurar**.
 1. Actualice los valores de configuración para autorizar a {{site.data.keyword.Bluemix_notm}} para acceder a GitHub. Pulse **Autorizar** para ir al sitio web de GitHub. Si no tiene ninguna sesión de GitHub activa, se le solicitará que inicie sesión. Pulse **Autorizar aplicación** para permitir que {{site.data.keyword.Bluemix_notm}} acceda a su cuenta de GitHub.
 1. Cuando haya terminado de configurar los ajustes, pulse **Guardar integración**.
 

## ¿Por qué no puedo utilizar la integración de herramientas de {{site.data.keyword.gitrepos}} en mi cadena de herramientas en una región de una cadena de herramientas dentro de una región distinta?
{: troubleshoot-cd-grit-integration}
{: troubleshoot}

No se puede utilizar una instancia de {{site.data.keyword.gitrepos}} en varias regiones.

Cuando intento añadir la integración de herramientas de {{site.data.keyword.gitrepos}} a mi cadena de herramientas, recibo el siguiente mensaje de error:
{: tsSymptoms}

`El URL del repositorio no es válido. El repositorio debe estar en {local GitLab URL}.`

Donde `{local GitLab URL}` es el URL de la integración de herramientas de {{site.data.keyword.gitrepos}}, en la región en la que reside la cadena de herramientas.
   
Puesto que {{site.data.keyword.gitrepos}} se integra estrechamente con el servicio de {{site.data.keyword.contdelivery_short}} en la región en la que se ejecuta, no se puede utilizar una instancia de {{site.data.keyword.gitrepos}} en varias regiones.
{: tsCauses}

En lugar de crear una integración de herramientas de {{site.data.keyword.gitrepos}}, cree una integración de GitLab genérica y utilice esta integración para que apunte al repositorio (repo) de {{site.data.keyword.gitrepos}} en una región distinta.
{: tsResolve}

1. En el panel de control de DevOps, en la página Cadenas de herramientas, pulse la cadena de herramientas a la que desea añadir esta integración. Si lo prefiere, en la página Visión general de la app, en la tarjeta de Entrega continua, pulse **Ver cadena de herramientas** y luego **Visión general**.
1. Pulse **Añadir una herramienta**.
1. En la sección Integraciones de herramientas, pulse **GitLab**.
1. Pulse el servidor de GitLab que desee utilizar. Si el servidor de GitLab en el que reside el repositorio al que desea acceder no aparece en esta lista, añada un servidor personalizado:

 a. Pulse **Añadir servidor personalizado**.

 b. Escriba un nombre para el servidor. Este nombre de servidor aparecerá en la lista de servidores de GitLab disponibles.
 
 c. Escriba el URL raíz del servidor de GitLab personalizado.
 
 d. Especifique una señal de acceso personal para el servidor de GitLab personalizado. Si no tiene una señal de acceso personal, [cree una](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat).
 
 e. Pulse **Guardar integración personalizada**.
 
1. Si tiene un repositorio de GitLab y desea utilizarlo, para el tipo de repositorio, pulse **Existente** y escriba el URL.
1. Si desea utilizar un repositorio de GitLab nuevo, escriba un nombre para el repositorio, escriba el URL para el repositorio que esté clonando o bifurcando, y seleccione el tipo de repositorio:

 a. Para crear un repositorio vacío, pulse **Nuevo**.

 b. Para crear una copia de un repositorio de GitLab, pulse **Clonar**.

 c. Para bifurcar un repositorio de GitLab para que pueda aportar cambios a través de solicitudes de fusión, pulse **Bifurcar**.

1. Si desea crear un repositorio público en el servidor, desmarque el recuadro de selección **Convertir este repositorio en privado**.
1. Si desea utilizar los problemas de GitLab para el seguimiento de problemas, marque el recuadro de selección **Habilitar problemas de GitLab**.
1. Si desea realizar un seguimiento del despliegue de cambios en el código mediante la creación de etiquetas y comentarios en las confirmaciones, y etiquetas y comentarios en los problemas a los que hacen referencia las confirmaciones, marque el recuadro de selección **Hacer un seguimiento del despliegue cambios de código**. Para obtener más información, consulte
[Seguimiento de dónde se despliega el código con cadenas de herramientas](https://www.ibm.com/cloud/blog/announcements/track-code-deployed-toolchains/){: external}.
1. Pulse **Crear integración**.

Para obtener más información sobre la configuración de una integración de herramientas de GitLab, consulte [Configuración de GitLab](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#gitlab).


## ¿Por qué no puedo crear una cadena de herramientas a partir de una plantilla que utilice un repositorio privado en una región distinta?
{: troubleshoot-cd-grit-integration-private}
{: troubleshoot}

La plantilla de cadena de herramientas que está utilizando hace referencia a un repositorio privado de {{site.data.keyword.gitrepos}}.

{{site.data.keyword.gitrepos}} es específico de la región. Cuando intenta crear una cadena de herramientas a partir de una plantilla y elige como objetivo una región en la que no se encuentra el repositorio privado, la configuración de la integración de Git falla.
{: tsSymptoms}
   
Cuando añade un repositorio de {{site.data.keyword.gitrepos}} a una cadena de herramientas en una región específica, el ID de IBM se correlaciona con un nombre de usuario de GitLab que le da acceso a GitLab en dicha región. Aunque el nombre de usuario de GitLab que aparece es el mismo en todas las regiones, el usuario de GitLab asociado es diferente en cada región porque cada región tiene una instalación independiente de GitLab. El acceso a los usuarios de GitLab en otras regiones no se otorga automáticamente a las cadenas de herramientas, incluso cuando el nombre de usuario de GitLab que aparece es el mismo.
{: tsCauses}

Haga público el repositorio de {{site.data.keyword.gitrepos}} para que se pueda acceder a él desde cualquier lugar, incluidas otras regiones de {{site.data.keyword.Bluemix_notm}}.
{: tsResolve}

Si el repositorio debe ser privado, el propietario del repositorio puede otorgar acceso a él creando una [señal de acceso personal](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat) en el servidor de GitLab donde se encuentra el repositorio de origen. Solo necesita acceso al repositorio privado para clonar el contenido durante la creación de la cadena de herramientas. La señal de acceso personal se puede crear con una fecha de caducidad para limitar su ciclo de vida para que caduque después de un día. 

Una vez que tenga una señal de acceso personal, puede crear un URL para acceder al repositorio desde otras regiones. Mientras configure la integración de herramientas, en el campo **URL de repositorio de origen**, actualice el URL de repositorio para utilizar el nombre de usuario y la señal de acceso.

`https://user:XXXXXXX@us-south.git.cloud.ibm.com/group/node-hello-world`

Donde `user` es su nombre de usuario de GitLab, `XXXXXXX` es la señal de acceso,
[`group`](https://us-south.git.cloud.ibm.com/help/user/group/index.md){: external} es el grupo donde se almacena el repositorio y `node-hello-world` es el nombre del repositorio.

Si su repositorio de GitLab no se encuentra dentro de un grupo de GitLab, el valor de `group` es el mismo que el nombre de usuario.
{: tip}


## ¿Por qué no puedo clonar mi repositorio de {{site.data.keyword.gitrepos}} a través de https?
{: #troubleshoot-grit-clone-repo}
{: troubleshoot}

Debe utilizar una señal de acceso personal o una clave SSH para realizar operaciones de Git.

Intenta enviar por push o clonar un repositorio desde la línea de mandatos utilizando https y no puede autenticarse aunque haya especificado la contraseña correcta.
{: tsSymptoms}
   
{{site.data.keyword.gitrepos}} utiliza un mecanismo de inicio de sesión único que no da soporte a la autenticación de Git que utiliza un nombre de usuario y una contraseña en la línea de mandatos.
{: tsCauses}

Para realizar operaciones de Git como, por ejemplo, clonar o enviar por push, debe utilizar una señal de acceso personal o una clave SSH. Para obtener más información sobre la creación de una señal de acceso personal o una clave SSH, consulte la [Guía de aprendizaje de iniciación](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication).
{: tsResolve}

## ¿Por qué se me solicita que me autentique cuando intento clonar mi repositorio de {{site.data.keyword.gitrepos}} mediante SSH?
{: troubleshoot-cd-grit-ssh}
{: troubleshoot}

Es posible que haya problemas con la ubicación o los permisos para la clave SSH privada, o que la línea de mandatos de Git no esté utilizando la clave SSH privada para la autenticación con {{site.data.keyword.gitrepos}}.

He añadido mi clave pública SSH mediante la interfaz de usuario de {{site.data.keyword.gitrepos}}. Cuando intento clonar un repositorio mediante SSH, se me solicita una contraseña o un código de seguridad, o se muestra un mensaje de error que indica que la autenticación ha fallado.
{: tsSymptoms}
   
A raíz de los problemas de SSH siguientes, puede recibir una solicitud de autenticación o puede aparecer un mensaje de error:
{: tsCauses}

* Es posible que la línea de mandatos de Git no esté utilizando la clave SSH privada para la autenticación con {{site.data.keyword.gitrepos}}.

* Es posible que la clave SSH privada no esté en la ubicación ~/.ssh/id_rsa predeterminada.

* Es posible que la clave SSH privada no tenga los permisos correctos (600).


Utilice cualquiera de los métodos siguientes para resolver este problema:
{: tsResolve}

* Si utiliza la ubicación de clave SSH privada predeterminada, verifique los permisos de la carpeta ~/.ssh/ y el archivo de claves privadas ~/.ssh/id_rsa. Si los permisos son demasiado amplios, de forma predeterminada SSH no utiliza una clave privada. Asegúrese de que los permisos de la carpeta ~/.ssh/ se establecen en 700 y los permisos de la carpeta ~/.ssh/id_rsa se establecen en 600.

* Si la clave privada no se encuentra en la ubicación predeterminada, utilice el mandato siguiente para especificarlo en una variable de entorno:

```
  GIT_SSH_COMMAND='ssh -i/path/to/private_key_file' git clone git@host:owner/repo.git
```

* Para depurar este problema mediante la información de conexión, añada el distintivo -v o -vvv a la variable de entorno `GIT_SSH_COMMAND`:

```
  GIT_SSH_COMMAND='ssh -vvv git clone git@host:owner/repo.git
```
```
  GIT_SSH_COMMAND='ssh -vvv -i/path/to/private_key_file' git clone git@host:owner/repo.git
```


## He intentado añadir un usuario a mi proyecto de GitLab por correo electrónico, pero no ha recibido la invitación. ¿Cómo puedo añadirlo a mi proyecto?
{: #troubleshoot-gitlab-add-user}
{: troubleshoot}

La invitación puede estar bloqueada por el correo electrónico del usuario.

He invitado a un usuario a mi proyecto de GitLab utilizando su dirección de correo electrónico, que aparece en {{site.data.keyword.gitrepos}}, pero no ha recibido el correo electrónico.
{: tsSymptoms}
   
El correo electrónico puede estar bloqueado por los filtros de correo no deseado de la bandeja de entrada de usuario. 
{: tsCauses}

Para resolver este problema, puede utilizar cualquiera de los métodos siguientes:
{: tsResolve}

* Compruebe la carpeta de correo no deseado del correo electrónico para determinar si la invitación de correo electrónico se ha marcado como correo no deseado. Los correos electrónicos se envían desde una dirección noreply@. Actualice los filtros de correo no deseado para permitir correos electrónicos de esta dirección.

* Investigue si los filtros corporativos de correo no deseado que están fuera del control del usuario están bloqueando el correo electrónico. Solicite al usuario que inicie la sesión en la interfaz de usuario de {{site.data.keyword.gitrepos}} y que le envíe su ID de usuario. Puede añadir el usuario al proyecto de GitLab utilizando su ID de usuario.


## ¿Por qué no se crea el conducto correctamente cuando creo una cadena de herramientas a partir de la plantilla que estoy escribiendo? 
{: troubleshoot-cd-pipeline-creation}
{: troubleshoot}

Es posible que el conducto no tenga recursos, como trabajos y etapas, debido a un error en la definición de pipeline.yaml.

Cuando intento crear una cadena de herramientas a partir de una plantilla que estoy escribiendo, recibo el siguiente mensaje de error en la página Conducto:
{: tsSymptoms}

`This pipeline was created, but might be missing jobs, stages, or other resources. You can use this pipeline, or if you prefer, you can delete it and create another pipeline.`

Por lo general, este problema se debe a un error en la definición de pipeline.yaml.
{: tsCauses}
   
Para depurar este error, puede utilizar cualquiera de los métodos siguientes:
{: tsResolve}

* Utilice la interfaz de usuario del conducto para crear un conducto de ejemplo que replique el conducto que está intentando crear con la plantilla. Añada `/yaml` al URL de conducto para generar un archivo pipeline.yaml similar que se puede utilizar para buscar diferencias obvias. Por ejemplo, `https://cloud.ibm.com/devops/pipelines/<your pipeline id>/yaml?env_id=<your region>`.

* Utilice el mecanismo de creación de cadena de herramientas de modalidad autónoma. En la página **Crear una cadena de herramientas**, abra el depurador y evalúe la expresión `window.Testflags = {1}`. Cuando pulsa **Crear una cadena de herramientas** en esta modalidad, la cadena de herramientas no se crea. En su lugar, la información que se pasa a la API se devuelve a la consola, donde puede revisarla.


## Al intentar desplegar en Kubernetes utilizando Delivery Pipeline, ¿por qué obtengo un error sobre un objeto no válido? 
{: troubleshoot-cd-pipeline-kubernetes}
{: troubleshoot}

La imagen base del conducto 1.0 incluye kubectl v1.14.2. Es posible que reciba un error si el clúster Kubernetes al que se conecta ejecuta una versión más reciente de Kubernetes. 

Al intentar desplegar en Kubernetes utilizando Delivery Pipeline, recibo el mensaje de error siguiente:
{: tsSymptoms}

`error:SchemaeError(io.k8s.api.core.v1.SecretProjection): el objeto no válido no tiene propiedades adicionales`

Por lo general, este problema se produce cuando la versión del mandato kubectl de la imagen base del conducto es incompatible con la versión de Kubernetes que se ejecuta en el clúster.
{: tsCauses}
   
Para resolver este problema, puede utilizar cualquiera de los métodos siguientes:
{: tsResolve}

* Utilice una versión más reciente de la imagen base del conducto, que incluya la versión más actual publicada de kubectl cuando se cree. Para obtener información sobre cómo especificar la versión de imagen más reciente, consulte
[Especificación de la versión de la imagen](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-pipeline_versioned_base_images#specify_base_image_version).

* Asegúrese de que el trabajo de conducto ejecuta la versión correcta de kubectl. Por ejemplo, añada las líneas siguientes al principio del trabajo de conducto para ejecutar kubectl v1.14.2:

```
  curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.14.2/bin/linux/amd64/kubectl
  chmod +x ./kubectl
  sudo mv ./kubectl /usr/local/bin/kubectl
```

Si ejecuta kubectl v1.14.2 desde una imagen base de conducto 1.0, la opción sudo no estará disponible. Sustituya la línea sudo por el mandato siguiente para añadir kubectl a la vía de acceso (path):
```
   mkdir ~/.bin && export PATH=~/.bin:$PATH && mv ./kubectl ~/.bin/kubectl 
```

Para obtener más información sobre cómo acceder a la versión exacta de kubectl que necesita, consulte
[Instalar y configurar kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-linux){: external}.
{: tip}


## He configurado una integración de herramientas para mi cadena de herramientas. ¿Por qué no se ha configurado?
{: troubleshoot-tool-integration-error}
{: troubleshoot}

Si se produce un error durante el proceso de configuración o si la comunicación entre la cadena de herramientas y la herramienta no se establece correctamente, la configuración falla.

Después de añadir y configurar una integración de herramientas para la cadena de herramientas, se visualiza un mensaje de error para indicar que la configuración ha fallado.
{: tsSymptoms}

Cuando añade una integración de herramientas, la cadena de herramientas se comunica con la herramienta representada mediante la integración de herramientas para suministrar los recursos necesarios y asociarlos con la cadena de herramientas. Si se produce un error durante el proceso de configuración o si la comunicación entre la cadena de herramientas y la herramienta no se establece correctamente, la integración de herramientas se coloca en un estado de error.
{: tsCauses}

 ![Error de configuración](images/tool_setup_failed.png)

Puede intentar configurar de nuevo la integración de herramientas:
{: tsResolve}

1. En su tarjeta de herramienta, mueva el cursor sobre el mensaje `Error de configuración` y pulse **Volver a configurar**.

 ![Botón Volver a configurar](images/tool_reconfigure.png)

1. Asegúrese de utilizar parámetros de configuración válidos. Si el error está causado por una configuración no válida, se muestra un mensaje de error; por ejemplo, `La integración se ha podido configurar. Compruebe la configuración y vuelva a intentarlo. Razón: api_key:fakeKey no válido`. Actualice los valores de la integración de herramientas y pulse **Guardar integración**.
1. Si el error está causado por un problema de comunicación, pulse **Guardar integración** para intentarlo de nuevo.


## ¿Por qué no puedo añadir {{site.data.keyword.contdelivery_short}} a una organización de Cloud Foundry?
{: troubleshoot-resource_groups}
{: troubleshoot}

Ya no puede crear instancias del servicio de {{site.data.keyword.contdelivery_short}} en las organizaciones de Cloud Foundry. 

Se muestra el mensaje siguiente en la página Cadenas de herramientas de la cadena de herramientas en una organización de Cloud Foundry:
{: tsSymptoms}

`Continuous Delivery service required: Add the service to your organization to ensure uninterrupted use of the service capabilities.` 

Cuando pulsa **Añadir el servicio**, no hay ninguna opción para crear {{site.data.keyword.contdelivery_short}} en una organización de Cloud Foundry. Solo puede crear {{site.data.keyword.contdelivery_short}} en un grupo de recursos.

Los grupos de recursos han sustituido a las organizaciones de Cloud Foundry como contenedores preferidos para las instancias de servicio. Sin embargo, todavía puede crear cadenas de herramientas en las organizaciones de Cloud Foundry para dar soporte a las instancias preexistentes de {{site.data.keyword.contdelivery_short}} en las organizaciones de Cloud Foundry.
{: tsCauses}

Vuelva a crear la cadena de herramientas en los grupos de recursos y, a continuación, elimine la cadena de herramientas original de la organización de Cloud Foundry. De forma alternativa, puede ignorar el mensaje de error hasta que se proporcione un método para migrar las cadenas de herramientas existentes de las organizaciones de Cloud Foundry a los grupos de recursos.
{: tsResolve}


## ¿Por qué no puedo suprimir las cadenas de herramientas utilizando la CLI de `ibmcloud`?
{: troubleshoot-delete_toolchains_cli}
{: troubleshoot}

Actualmente, no se pueden suprimir las cadenas de herramientas utilizando la CLI de recursos de ibmcloud. 

He intentado suprimir una cadena de herramientas de la línea de mandatos utilizando el mandato `ibmcloud resource service-instance-delete` y el mandato falla con el siguiente mensaje de error:
{: tsSymptoms}

Código de error: RC-ServiceBrokerErrorResponse
Descripción del mensaje: La supresión de la cadena de herramientas se debe realizar desde el panel de control de la cadena de herramientas

Las cadenas de herramientas son un tipo especial de recurso en la plataforma en la nube que actualmente no puede suprimir mediante la CLI de `ibmcloud resource`.
{: tsCauses}

Para suprimir una cadena de herramientas:
{: tsResolve}

1. En el panel de control de DevOps, en la página **Cadenas de herramientas**, pulse sobre la cadena de herramientas que desea suprimir. Como alternativa, en la página Visión general de la app, en la tarjeta de Entrega continua, pulse **Ver cadena de herramientas**.
1. Pulse el menú **Más acciones**, que se encuentra junto a **Ver app**.
1. Pulse **Suprimir**. Cuando se suprime una cadena de herramientas, también se suprimen todas sus integraciones de herramienta, lo que podría dar lugar a la supresión de los recursos que dichas integraciones gestionan.
1. Para confirmar la supresión, escriba el nombre de la cadena de herramientas y pulse **Suprimir**.  


## ¿Por qué no está disponible la característica Edición en directo después de confirmar y enviar por push a un repositorio?
{: #troubleshoot-liveedit}
{: troubleshoot}

Cuando se despliega fuera de Eclipse Orion {{site.data.keyword.webide}}, se borra la modalidad de edición en directo.

Confirma y envía por push un cambio desde la línea de mandatos o {{site.data.keyword.webide}} y la característica Edición en directo no está disponible.
{: tsSymptoms}
   
Cuando se crea una cadena de herramientas que contiene un conducto de {{site.data.keyword.contdelivery_short}} y {{site.data.keyword.webide}}, ambas integraciones de herramientas pueden desplegar la aplicación (app). De forma predeterminada, tanto el conducto como {{site.data.keyword.webide}} se despliegan en la misma organización y el mismo espacio de Cloud Foundry, utilizando la misma app y el mismo URL de Cloud Foundry. Cuando se despliega fuera de {{site.data.keyword.webide}}, se borra la modalidad de edición en directo.
{: tsCauses}

Para desarrollar rápidamente una versión de prueba de la app mediante la característica Edición en directo, realice el despliegue en una app, espacio y URL diferentes de Cloud Foundry desde {{site.data.keyword.webide}}. Cuando se hayan completado los cambios de código, puede confirmar y enviar por push el código para activar el conducto para crear y desplegar la versión de producción de la app.
{: tsResolve}

1. En la barra de ejecución, seleccione la configuración de lanzamiento que desea editar.
2. Edite los valores que se especifican para el espacio y el host.
3. Pulse **Guardar** y **Salir**.
4. Pulse el botón **Ejecutar** en la barra de ejecución. Es posible que tenga que desplegar varias veces para habilitar el botón Edición en directo.

Para obtener más información sobre la característica Edición en directo, consulte [Edición en directo](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-live-syn#live-edit).


## ¿Qué significa "no sincronizado" en la barra de ejecución de {{site.data.keyword.webide}}?
{: #troubleshoot-web-ide-sync}
{: troubleshoot}

El sistema de archivos del espacio de trabajo no está sincronizado.

En la modalidad de edición en directo, {{site.data.keyword.webide}} sincroniza los archivos del espacio de trabajo con la app de Cloud Foundry en ejecución y los archivos están sin sincronizar.
{: tsSymptoms}
   
Es posible que el sistema de archivos del espacio de trabajo no esté sincronizado si la app se modifica fuera de {{site.data.keyword.webide}}. También puede estar sin sincronizar si {{site.data.keyword.webide}} no puede recuperar el estado de sincronización de la app.
{: tsCauses}

El estado puede borrarse después de un minuto o dos cuando se restablecen las comunicaciones normales y se sincronizan los archivos. De lo contrario, puede iniciar y detener la app con la modalidad de edición en directo habilitada.
{: tsResolve}
