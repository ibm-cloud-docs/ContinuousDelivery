---

copyright:
  years: 2017, 2018
lastupdated: "2018-8-2"

---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# Creación de plantillas de cadenas de herramientas personalizadas
{: #toolchains_custom}

Mejore su flujo de trabajo de DevOps creando una plantilla de cadena de herramientas personalizada. Puede empezar rápidamente con una plantilla de cadena de herramientas existente, o crear una plantilla de cadena de herramientas que incluya sólo las integraciones que necesita. Puede añadir o eliminar las integraciones de la cadena de herramientas en cualquier momento.
{:shortdesc}

Puede [crear una cadena de herramientas](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started){: new_window} de varias formas. Una vez que cree una plantilla de cadena de herramientas personalizada, puede compartirla [creando un botón de despliegue en {{site.data.keyword.Bluemix_notm}}](/docs/services/ContinuousDelivery/deploy_button.html#deploy-button){: new_window}.   Encontrará más detalles sobre el SDK de la plantilla de cadena de herramientas en el [SDK de Open Toolchain](https://github.com/open-toolchain/sdk/wiki/){:new_window}. En el [sitio de Garage Method](https://www.ibm.com/cloud/garage/tutorials/create-a-template-for-a-custom-toolchain/){:new_window} hay disponible una guía de aprendizaje paso a paso.


## Iniciación
{: #toolchains_custom_gettingstarted}

Para crear una plantilla de cadena de herramientas personalizada, comience por clonar la plantilla de cadena de herramientas sencilla de Cloud Foundry. Clonar una plantilla existente le proporciona el punto de partida para su cadena de herramientas personalizada.

1. Mediante el cliente Git que elija, escriba el siguiente mandato para clonar la plantilla [Cadena de herramientas simple](https://github.com/open-toolchain/simple-toolchain){: new_window} en GitHub.

 ```
 git clone https://github.com/open-toolchain/simple-toolchain.git
 ```
 {: pre}

 Esta plantilla despliega una aplicación Hello World básica desde un único repositorio GitHub e incluye una cadena de herramientas simple preconfigurada para entrega continuada, control de código fuente, seguimiento de problemas y edición en línea.

2. Si prefiere comenzar con una plantilla de cadena de herramientas más compleja, puede empezar por clonar la [Cadena de herramientas nativa de Microservices](https://github.com/open-toolchain/toolchain-demo){: new_window}.

 ```
 git clone https://github.com/open-toolchain/toolchain-demo.git
 ```
 {: pre}

La plantilla de microservicios despliega un almacén en línea que se compone de tres microservicios, cada uno contenido en su propio repositorio de GitHub. También es una cadena de herramientas más compleja preconfigurada para:
* Entrega continua
* Control de origen
* Despliegues azul-verde
* Pruebas funcionales
* Seguimiento de problemas
* Edición en línea
* Mensajería

Independientemente de la plantilla que elija, el proceso para personalizar la cadena de herramientas que cree es generalmente el mismo.

Después de clonar la plantilla, tendrá un repositorio GitHub básico que contiene un archivo readme y un directorio `.bluemix`. El directorio contiene todos los archivos de configuración que necesita la cadena de herramientas para funcionar. Como mínimo, el directorio `.bluemix` debe contener los archivos siguientes:

* `toolchain.yml`
* `deploy.json`
* `pipeline.yml`

![Archivos mínimos necesarios para definir una cadena de herramientas](images/min_files_for_a_toolchain.png)


Cada uno de estos archivos se explica en las secciones siguientes. Cada sección contiene información de configuración que puede consultar a medida que evoluciona la cadena de herramientas.
YAML es un lenguaje de serialización de datos que es un superconjunto estricto de JSON, con la adición de sangrías y saltos de línea sintácticamente significativos. Sin embargo, YAML no permite caracteres de tabulación literales.

## Visión general de los archivos de configuración
{: #toolchains_custom_config_files}


Los archivos de configuración de la cadena de herramientas se componen principalmente de archivos en formato YAML. Cada archivo contiene metadatos que describen distintos aspectos de la cadena de herramientas. Los metadatos incluyen:
* Información sobre la cadena de herramientas y los repositorios.
* Detalles sobre cómo se crea y despliega el código.
* Propiedades de configuración para las herramientas que están en la cadena de herramientas.

A medida que la cadena de herramientas pasa a ser más compleja, los archivos de configuración también pueden crecer en complejidad.

Estas son algunas directrices a tener en cuenta al trabajar con archivos YAML:

* Sólo utilizan espacios los espacios. No se permiten tabuladores.
* Todas las propiedades y listas debe especificarse con un sangrado de uno o varios espacios.
* Todas las claves y propiedades son sensibles a mayúsculas y minúsculas.

Preste atención al formato del archivo YAML para reducir la posibilidad de encontrar errores.
Para comprobar si hay errores, puede que desee utilizar un validador sencillo, como [este analizador](http://wiki.ess3.net/yaml/){: new_window}.
{: tip}

## Planificación de la sección de servicios
Cada subsección de servicio contiene la información siguiente:

* Nombre: una serie generada por el usuario que se utiliza para identificar este servicio en el contexto del archivo actual. Este nombre puede utilizarse para marcar un servicio como necesario.

* Service_id: una serie exclusiva que identifica el servicio. Esta serie procede directamente del [catálogo de servicios](https://github.com/open-toolchain/sdk/wiki/services.md){: new_window}.

* Parámetros: cero o más parámetros de configuración para el servicio. Estos parámetros varían entre servicios: los usuarios necesitan consultar el catálogo para averiguar qué parámetros necesita un servicio concreto.

### Inclusión de texto de otros archivos

Toda la información de la cadena de herramientas puede estar en el archivo `toolchain.yml`.  Sin embargo, es posible que desee crear archivos independientes para cada interfaz de usuario de integración de herramientas mediante `$text`. De esta forma, se facilita el mantenimiento de las cadenas de herramientas y se minimiza el tiempo invertido en editar los archivos de configuración.  Este fragmento de código de ejemplo de un `toolchain.yml` muestra cómo utilizar el contenido del archivo `pipeline.yml` como el valor de `content`.

```
  configuration:
    content:
      $text: pipeline.yml
```

### Localización de la plantilla de cadena de herramientas

Puede localizar la cadena de herramientas externalizando las series de IU en el directorio `nls`, de modo que las series de la cadena de herramientas se visualicen en el idioma preferido del usuario.
El archivo `toolchain.yml` debe incluir una referencia `$i18n`.  
El ejemplo siguiente muestra una referencia `$i18n` a un archivo `messages.yml`:

```
messages:
  $i18n: messages.yml
```

  Las series en inglés están en `messages.yml` y para otros idiomas se utiliza el código de idioma, por ejemplo `messages_de.yml`.   La lista de códigos de idioma puede encontrarse en [Tags for Identifying Languages](https://tools.ietf.org/html/rfc5646){: new_window}.

   Para hacer referencia a la serie de externalizar, utilice `$ref` para recuperar la serie.  Por ejemplo,

```
  template:
    name:
      $ref: "#/messages/template.name"
```

  Si no utiliza series externalizadas, puede utilizar:

```
  template:
    name: my_template
```

Para obtener más información, consulte la [sección de mensajes del SDK de Open Toolchain](https://github.com/open-toolchain/sdk/wiki/Template-File-Format#messages-section){: new_window}.

## Configuración del archivo de cadena de herramientas
{: #toolchains_custom_toolchain_yml}

El archivo `toolchain.yml` es la base de la cadena de herramientas. Las características específicas de la cadena de herramientas, incluidos repositorios que obtener, servicios que incluir y detalles de la compilación, se describen en este archivo. Para facilitar la estructura de su contenido, se puede dividir en varias secciones.

1\. **Información de introducción de la cadena de herramientas:**

 En esta sección del archivo se proporcionan detalles sobre la cadena de herramientas que el usuario puede ver en la página de creación de la cadena de herramientas. Incluya un nombre para su cadena de herramientas, junto con una descripción que explique la finalidad de la cadena de herramientas. También puede incluir una imagen, como un logotipo o una representación visual de la cadena de herramientas.

 Además de proporcionar contenido de introducción para su cadena de herramientas, esta sección también incluye una clave que se denomina `required` que define las herramientas que forman parte de la cadena de herramientas. El creador de la cadena de herramientas configura estas herramientas al crear la cadena de herramientas desde su plantilla. Para cada herramienta que se pueda configurar en la página de creación de la cadena de herramientas, añada la clave padre de la herramienta como está definida en el archivo `toolchain.yml` como una propiedad de la clave `required`.

 Este fragmento de código muestra un ejemplo de esta sección:

 ```
 ---
template
  name: "Simple Toolchain"
  description: "Esta aplicación Hello World utiliza Node.js e incluye una cadena de herramientas preconfigurada para entrega continua, control de origen, seguimiento de problemas y edición en línea.\n\nPara comenzar, pulse **Crear**."
  header: '![](toolchain.svg)'
  icon: icon.svg
  required:
   - sample-build
   - sample-repo
  info:
    git url: >-
      [https://github.com/my-toolchain/simple-toolchain](https://github.com/open-toolchain/simple-toolchain)
    git branch: >-
      [master](https://github.com/my-toolchain/simple-toolchain/tree/master)
  ```
 {: codeblock}

En el ejemplo anterior, el URL de Git y la rama de Git son para una nueva plantilla de cadena de herramientas.

2\. **Definiciones de repositorio:**

 Una cadena de herramientas puede proporcionar entrega continua para tantos repositorios Git como se desee, incluidos GitHub, GitHub Enterprise, Git Repos, Issue Tracking y GitLab. Esta sección del archivo `toolchain.yml` es donde está definido cada repositorio.

 Para cada repositorio añadido a la cadena de herramientas, añada una clave padre que represente el nombre del repositorio con las propiedades siguientes:

| Elemento | Clave/propiedad | Valor | Descripción |
|------|--------------|-------|-------------|
| repo-name | clave |  | Nombre de repositorio. Esta clave coincide con el nombre (sample-repo) |
| service_id | propiedad | <`githubpublic`, `githubprivate`, `hostedgit`, `gitlab`> | Tipo de repositorio |
| parameters: | clave |  |  |
| repo_name | propiedad |  | Patrón para repo-name. El ejemplo siguiente utiliza el nombre de la cadena de herramientas como nombre de repositorio |
| repo_url | propiedad |  | URL del repositorio |
| type | propiedad | <`new` , `fork` , `clone` , `link`> | Cómo crear el repositorio nuevo |
| has_issues | propiedad | <`true` , `false`> | Problemas de uso |
| enable_traceability | properties |  <`true` , `false`> | Determina si se realiza el seguimiento del despliegue de cambios de código creando marcas, etiquetas y comentarios sobre las confirmaciones, solicitudes de extracción y problemas a los que se hace referencia.|

 Si define varios repositorios y los configura como `has_issues: true`, se añade una única instancia del rastreador de problemas de GitHub a la cadena de herramientas. El rastreador seguirá problemas para todos los repositorios establecidos en `true`.
 {: tip}

 Este fragmento de código muestra un ejemplo de esta sección:

 ```
 # Github repos
 services:
  sample-repo:
    service_id: githubpublic
    parameters:
      repo_name: '{{toolchain.name}}'
      repo_url: 'https://github.com/open-toolchain/node-hello-world'
      type: clone
      has_issues: true
      enable_traceability: true
 ```
 {: codeblock}

3\. **Información del conducto: **

 Puede entregar continuamente el proyecto con un conducto. Esta sección del archivo define los detalles de configuración que se utilizan para crear y desplegar el código en cada uno de los repositorios de GitHub, Git Repo e Issue Tracking.

 Para empezar, para cada repositorio que esté definido en la cadena de herramientas, añada una clave padre que represente un nombre de su conducto. Considere la posibilidad de deducir esta clave a partir del nombre del repositorio de GitHub, Git Repo e Issue Tracking. Añada las siguientes propiedades:

| Elemento | Clave/propiedad | Valor | Descripción |
|------|--------------|-------|-------------|
| pipeline-name | clave |  | Nombre del conducto (sample-build) |
| service_id | propiedad | <`pipeline`> | Nombre del servicio que se va a utilizar |
| parameters | clave |  |  |
| name | propiedad | <`repo_name`> | Igual que el nombre definido en la sección repos |
| ui-pipeline | propiedad | <`true` , `false`> |True si las aplicaciones que despliega este conducto se muestran en el menú **Ver app** de la página de la cadena de herramientas  |
| configuration | clave |  |  |
| content | propiedad | <`$ref(pipeline.yml)`> | Archivo que contiene la definición del conducto |
| env | clave |  |  |
| SAMPLE_REPO | clave | <`repo-name-key`> | El mismo nombre que su clave padre del repositorio |
| CF_APP_NAME |  propiedad | <`'{{form.pipeline.parameters.prod-app-name}}'`> | Nombre que utiliza Cloud Foundry. Considere la posibilidad de incorporar el nombre de clave padre del repositorio en esta propiedad. |
| PROD_SPACE_NAME | propiedad | <`'{{form.pipeline.parameters.prod-space}}'`> | Nombre del espacio de {{site.data.keyword.Bluemix_notm}} en el que se va a desplegar |
| PROD_ORG_NAME | propiedad | <`'{{form.pipeline.parameters.prod-organization}}'`> | Nombre de la organización de {{site.data.keyword.Bluemix_notm}} en la que se va a desplegar |
| PROD_REGION_ID | propiedad | <`'{{form.pipeline.parameters.prod-region}}'`> | Nombre de la región de {{site.data.keyword.Bluemix_notm}} en la que se va a desplegar |
| execute | propiedad | <`true` , `false`> | Iniciar conducto después de la creación |

<!--| services | property | <`repo-name-key`> |  GitHub repository parent key |
| hidden | property | <`[form, description]`> |  |
-->

 Encontrará información sobre cómo crear un archivo `pipeline.yml` en una [sección posterior](#toolchains_custom_pipeline_yml)

 Este fragmento de código muestra un ejemplo de esta sección del archivo:

 ```
 # Pipelines
  sample-build:
    service_id: pipeline
    parameters:
      services:
        - sample-repo
      name: '{{services.sample-repo.parameters.repo_name}}'
      ui-pipeline: true
      configuration:
        content:
          $ref: pipeline.yml
        env:
          SAMPLE_REPO: sample-repo
          CF_APP_NAME: '{{form.pipeline.parameters.prod-app-name}}'
          PROD_SPACE_NAME: '{{form.pipeline.parameters.prod-space}}'
          PROD_ORG_NAME: '{{form.pipeline.parameters.prod-organization}}'
          PROD_REGION_ID: '{{form.pipeline.parameters.prod-region}}'
       execute: true
 ```
 {: codeblock}

4\. **Destalles del despliegue:**

 Como parte del proceso de entrega continua, puede configurar una cadena de herramientas para desplegar una aplicación en cualquier región, organización o espacio de {{site.data.keyword.Bluemix_notm}} al que tenga acceso el usuario. Los detalles específicos sobre dónde desplegar la aplicación se pueden seleccionar en la página de creación de la cadena de herramientas.

 ![Valores de configuración del conducto de entrega](images/deploy_configuration.png)

 En esta sección del archivo `toolchain.yml` se definen las etapas del conducto que se puede configurar en la página de creación de la cadena de herramientas.

 Para empezar, se utiliza la clave padre `deploy` para identificar las propiedades de configuración del despliegue. Las siguientes propiedades componen el resto de la sección:

| Elemento | Clave/propiedad | Valor | Descripción |
|------|--------------|-------|-------------|
| desplegar | clave |  | Nombre de la sección de despliegue |
| schema | propiedad | <`deploy.json`> | Archivo que define el diseño de la IU para configurar los detalles del despliegue |
| service-category | propiedad | <`pipeline`> | Servicio que utiliza las configuraciones de despliegue |
| parameters | clave |  |  |
| prod-region | propiedad | <`"{{region}}"`> | Define la región de {{site.data.keyword.Bluemix_notm}} para la etapa de producción |
| prod-organization | propiedad | <`"{{organization}}"`> | Define la organización de {{site.data.keyword.Bluemix_notm}} para la etapa de producción |
| prod-space | propiedad | <`prod`> | Define el espacio de {{site.data.keyword.Bluemix_notm}} para la etapa de producción |
| github-repo-name | propiedad | <`"{{repo-name-key.parameters.repo_name}}"`> | Variable para pasar el nombre del repositorio GitHub a la página de creación de la cadena de herramientas |

Para obtener más información sobre cómo crear un archivo `deploy.json`, consulte [esta sección] (#toolchains_custom_deploy_json).

 En el ejemplo siguiente se define una sola etapa que se despliega en un entorno de producción.

 ```
 ## Configuring a deployment stage
 deploy:
   schema: deploy.json
   service-category: pipeline
   parameters:
 	prod-region: "{{region}}"
 	prod-organization: "{{organization}}"
 	prod-space: prod
 	hello-world-name: "{{hello-world-repo.parameters.repo_name}}"
 ```
 {: codeblock}

 Básicamente el ejemplo de código se puede utilizar tal cual y sólo requiere una ligera modificación. Para personalizar esta sección, establezca `github-repo-name` para ser coherente con el nombre de su repositorio. También es necesario actualizar la información del archivo [`deploy.json`](#toolchains_custom_deploy_json).

 Para crear un conducto más complejo que incluya etapas de desarrollo, control de calidad y producción, se podrán sustituir las siguientes propiedades bajo la clave `parameters`.

 ```
   parameters:
 	dev-region: "{{region}}"
 	qa-region: "{{region}}"
 	prod-region: "{{region}}"
 	dev-organization: "{{organization}}"
 	qa-organization: "{{organization}}"
 	prod-organization: "{{organization}}"
 	dev-space: dev
 	qa-space: qa
 	prod-space: prod
 ```
 {: codeblock}

 ## Configuración de un conducto
 {: #toolchains_custom_pipeline_yml}

 El archivo `pipeline.yml` contiene todos los detalles de la configuración correspondientes a las etapas del conducto. Puede empezar con un pipeline.yml existente y personalizarlo para que se ajuste a sus necesidades.

 Si la cadena de herramientas contiene más de un conducto, proporcione nombres exclusivos para cada archivo `pipeline.yml`.

 A continuación puede ver un ejemplo de archivo `pipeline.yml`:

 ```
 ---
stages:
- name: BUILD
  inputs:
  - type: git
    branch: master
    service: ${SAMPLE_REPO}
  triggers:
  - type: commit
  jobs:
  - name: Build
    type: builder
- name: DEPLOY
  inputs:
  - type: job
    stage: BUILD
    job: Build
  triggers:
  - type: stage
  properties:
  - name: CF_APP_NAME
    value: undefined
    type: text
  - name: APP_URL
    value: undefined
    type: text
  jobs:
  - name: Blue-Green Deploy
    type: deployer
    target:
      region_id: ${PROD_REGION_ID}
      organization: ${PROD_ORG_NAME}
      space: ${PROD_SPACE_NAME}
      application: ${CF_APP_NAME}
    script: |
      #!/bin/bash
      # Push app
      if ! cf app $CF_APP; then  
        cf push $CF_APP
      else
        OLD_CF_APP=${CF_APP}-OLD-$(date +"%s")
        rollback() {
          set +e  
          if cf app $OLD_CF_APP; then
            cf logs $CF_APP --recent
            cf delete $CF_APP -f
            cf rename $OLD_CF_APP $CF_APP
          fi
          exit 1
        }
        set -e
        trap rollback ERR
        cf rename $CF_APP $OLD_CF_APP
        cf push $CF_APP
        cf delete $OLD_CF_APP -f
      fi
      # Export app name and URL for use in later Pipeline jobs
      export CF_APP_NAME="$CF_APP"
      export APP_URL=http://$(cf app $CF_APP_NAME | grep urls: | awk '{print $2}')
      # View logs
      #cf logs "${CF_APP}" --recent
 ```
 {: codeblock}		


 ## Configuración de la interfaz del conducto
 {: #toolchains_custom_deploy_json}

 En la página de creación de la cadena de herramientas, cuando se seleccionas Delivery Pipeline en la sección Integraciones configurables, la sección se expande para mostrar los siguientes elementos:

 	* El nombre de la aplicación
 	* La región, la organización y el espacio en los que se despliegan las etapas del conducto.

Puede configurar dichos elementos para cada herramienta.

 ![Valores de configuración del conducto de entrega](images/deploy_configuration.png)

 El diseño de esta sección en la interfaz de usuario se define mediante el esquema `deploy.json`.

 Dentro del esquema, se deben actualizar las siguientes propiedades para que se ajusten a los detalles de la aplicación:

 	* Título
 	* Descripción
 	* Descripción larga
 	* Todas las instancias de `hello-world-name` y los detalles asociados se deben modificar para que se ajusten a la aplicación.

 El siguiente fragmento de código es un ejemplo de archivo `deploy.json`:

 ```
 {
    "$schema": "http://json-schema.org/draft-04/schema#",
    "messages": {
        "$i18n": "locales.yml"
    },
    "title": {
        "$ref": "#/messages/deploy.title"
    },
    "description": {
        "$ref": "#/messages/deploy.description"
    },
    "longDescription": {
        "$ref": "#/messages/deploy.longDescription"
    },
    "type": "object",
    "properties": {
        "prod-region": {
            "description": "The {{site.data.keyword.Bluemix_notm}} region",
            "type": "string"
        },
        "prod-organization": {
            "description": "The {{site.data.keyword.Bluemix_notm}} org",
            "type": "string"
        },
       "prod-space": {
            "description": "The {{site.data.keyword.Bluemix_notm}} space",
            "type": "string"
        },
        "prod-app-name": {
            "description": {
                "$ref": "#/messages/deploy.appDescription"
            },
            "type": "string",
            "pattern": "\\S"
        }
    },
    "required": [
        "prod-region",
        "prod-organization",
        "prod-space",
        "prod-app-name"
    ],
    "form": [
        {
            "type": "validator",
          "url": "/devops/setup/bm-helper/helper.html"
        },
        {
            "type": "text",
            "readonly": false,
            "title": {
                "$ref": "#/messages/deploy.appName"
            },
            "key": "prod-app-name"
        },
        {
            "type": "table",
            "columnCount": 4,
            "widths": [
                "15%",
                "28%",
                "28%",
                "28%"
            ],
            "items": [
                {
                    "type": "label",
                  "title": ""
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/region"
                    }
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/organization"
                    }
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/space"
                    }
                },
                {
                    "type": "label",
                    "title": {
                        "$ref": "#/messages/prodStage"
                    }
                },
                {
                    "type": "select",
                  "key": "prod-region"
                },
                {
                    "type": "select",
                  "key": "prod-organization"
                },
                {
                    "type": "select",
                  "key": "prod-space",
                  "readonly": false
                }
            ]
        }
    ]
}
 ```
 {: codeblock}


## Configuraciones de otras herramientas

 Una vez que configure los componentes principales de la cadena de herramientas, podrá incluir integraciones de otras herramientas que añadan funciones a su cadena de herramientas. Todas las herramientas adicionales requieren su propia entrada en el archivo `toolchain.yml`. Algunas herramientas también necesitan que añada un archivo de configuración YAML independiente al directorio `.bluemix`.

 ![Archivos necesarios para definir una cadena de herramientas](images/files_for_toolchain_with_additional_tools.png)

Para ver la lista de integraciones de herramientas disponibles, consulte <a href="https://github.com/open-toolchain/sdk/wiki/services.md" target="_blank">Servicios disponibles en una plantilla de cadena de herramientas</a>. Los ejemplos siguientes muestran cómo dar formato a las adiciones a un archivo YAML de cadena de herramientas.

### **Slack**

#### toolchain.yml
{: #slack_toolchain_yaml}

```
messaging:
	  service_id: slack
	  $ref: slack.yml
```
{: codeblock}

#### slack.yml
{: #slack_slack_yaml}

```
---YAML
parameters:
  api_token: ""
  channel_name: ""
```
{: codeblock}

### **Sauce Labs**

#### toolchain.yml
{: #sauce_toolchain_yaml}

```YAML
test:
	  service_id: saucelabs
	  $ref: saucelabs.yml
```
{: codeblock}

#### saucelabs.yml
{: #sauce_slack_yaml}

```YAML
---
	parameters:
	  username: ""
  key: ""
```
{: codeblock}

### **Eclipse Orion Web IDE**

####	toolchain.yml
{: #eclipse_toolchain_yaml}

```YAML
webide:
	  service_id: orion
```
{: codeblock}
