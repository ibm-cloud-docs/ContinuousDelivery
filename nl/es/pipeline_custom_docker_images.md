---

Copyright:
  years: 2018
lastupdated: "2018-8-2"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# Cómo trabajar con imágenes de Docker personalizadas
{: #custom_docker_images}

Puede que la imagen base del conducto no admita todos los requisitos de su compilación. Por ejemplo, es posible que necesite un control más preciso sobre las versiones de node, java u otras herramientas. Puede resolver este problema incluyendo un primer paso en los trabajos de conducto que instale una serie de paquetes nuevos y configure variables de entorno cuidadosamente, como `PATH`, para configurar el entorno. Sin embargo, un mejor enfoque es utilizar el soporte del conducto para ejecutar una "Imagen de Docker personalizada" como base para su trabajo.

Tanto si utiliza un tipo de trabajo de compilación, como si es de prueba o despliegue, puede seleccionar un subtipo de imagen de Docker personalizada para proporcionar el nombre de imagen de Docker que desea utilizar y especificar el script que desea ejecutar. Por ejemplo, utilice las opciones siguientes para ejecutar un trabajo de compilación con Maven 3.5.3 e IBM Java:

 ![Compilación Maven con imagen personalizada](images/custom-image-maven-build.png)


## Cómo especificar el nombre de imagen de Docker
{: #docker_image_name}

El nombre de imagen de Docker en trabajos de imagen de Docker personalizada está diseñado para funcionar de la misma forma que los nombres de imágenes con la CLI de Docker. El formato de un nombre de imagen de Docker es: `[repository][:][tag]`. Por ejemplo, para `docker run maven:3.5.3-ibmjava`, el nombre de imagen de Docker es `maven:3.5.3-ibmjava`, donde `maven` es el repositorio y `3.5.3-ibmjava` es la etiqueta. No hay restricciones sobre el nombre de imagen de Docker que puede utilizar; vale cualquier imagen de Docker válida.

Si no se rellena el campo de **nombre de imagen de Docker**, se utiliza la imagen base del conjunto estándar. 
{: tip}

De forma predeterminada, se busca en el repositorio en [Docker Hub ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://hub.docker.com/){: new_window}. Si utiliza otro registro de Docker, como IBM Cloud Registry, puede utilizar el nombre de DNS completo. También puede utilizar el nombre completo para imágenes en Docker Hub. Por ejemplo, `registry.hub.docker.com/library/maven:3.5.3-ibmjava`.

La `etiqueta` de una imagen de Docker es opcional. Si no especifica una etiqueta, se establece de forma predeterminada en `latest`. El valor predeterminado `latest` es sólo un nombre de etiqueta que debe gestionar el propietario del repositorio. No significa que, cronológicamente, esta imagen de Docker sea la imagen más reciente.

En Docker Hub hay disponible una amplia comunidad de repositorios. IBM aloja una serie de repositorios públicos que el equipo de IBM Cloud utiliza en [https://hub.docker.com/u/ibmcom/ ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://hub.docker.com/u/ibmcom/){: new_window}. Los repositorios `ibmcom/ibmjava` e `ibmcom/ibmnode` son útiles para utilizarlos como base. 

## Uso de un registro de imagen privado
{: #private_image_registry}

Si va a utilizar un registro privado que requiere autenticación, debe establecer dos propiedades de entorno de etapa adicionales: `DOCKER_USERNAME` y `DOCKER_PASSWORD`. Puede utilizar una propiedad segura para enmascarar su `DOCKER_PASSWORD`. Antes de extraer la imagen, el trabajo de imagen de Docker personalizada utiliza las credenciales de nombre de usuario y contraseña para realizar una operación de `docker login`.

Para la mayoría de los registros, puede utilizar el nombre de usuario y la contraseña que se le han proporcionado. Si utiliza IBM Cloud Registry para almacenar las imágenes privadas, debe utilizar una clave de API de plataforma para la autenticación. 

1. [Solicite una clave de API de plataforma ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/iam/#/apikeys){: new_window} y asegúrese de guardar la clave. 
1. Cree dos propiedades de entorno de etapa utilizando `iamapikey` para `DOCKER_USERNAME` y la clave de API de plataforma que ha guardado para `DOCKER_PASSWORD`.

 ![Credenciales de IBM Cloud Registry](images/custom-image-private-repository.png)


## Cómo especificar el script
{: #specify_script}

Puede utilizar el bloque de **script** en los trabajos de imagen de Docker personalizada para crear un archivo de script que se ejecute en una carpeta de tareas, de forma similar al funcionamiento de los trabajos normales de conducto. 

Los valores `ENTRYPOINT` y `CMD` del Dockerfile de la imagen de Docker se sustituyen y no se invocan. En algunos casos, esto podría significar que necesita añadir pasos de inicialización al script.
{: tip}

Los trabajos de imagen de Docker personalizada aportan una mayor flexibilidad sobre cómo ejecutar el script; concretamente, puede controlar el intérprete de mandatos. Normalmente, si la primera línea del script empieza por `#!` seguido del nombre de un intérprete de mandatos, dicha entrada se utiliza para ejecutar los mandatos en el trabajo. Si no se especifica un intérprete de mandatos, se utiliza el shell predeterminado para la imagen de Docker. Normalmente, se utilizan `#!/bin/bash` o `#!/bin/sh`; los intérpretes de mandatos de imagen para `awk`, `node` y `ruby` también sirven si se especifica una imagen de Docker apropiada.
