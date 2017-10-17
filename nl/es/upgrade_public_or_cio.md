---

copyright:
  years: 2015, 2017
lastupdated: "2017-5-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Actualización de proyectos IBM Confidencial para cadenas de herramientas 
{: #upgrade_public_or_cio}

{{site.data.keyword.jazzhub}} está evolucionando a IBM Bluemix {{site.data.keyword.contdelivery_short}}. Como parte de este cambio, los proyectos se actualizarán a cadenas de herramientas.

Cuando el proyecto esté listo para ser actualizado, se mostrará un mensaje en la página de Visión general. Podrá, a continuación, actualizar el proyecto a una cadena de herramientas en {{site.data.keyword.Bluemix_notm}} público. La cadena de herramientas incluirá un repositorio Whitewater {{site.data.keyword.ghe_short}} para su código fuente. Se proporciona Whitewater {{site.data.keyword.ghe_short}} a los equipos de IBM para promocionar y habilitar la codificación social dentro de IBM. 
{: shortdesc}

Las cadenas de herramientas **{{site.data.keyword.contdelivery_short}} han sido aprobadas para material IBM Confidencial cuando se utilizan con Whitewater {{site.data.keyword.ghe_short}}.** Los conductos de entrega que reciben entradas desde el repositorio de Whitewater {{site.data.keyword.ghe_short}} pueden realizar el despliegue en entornos de transferencia (YS1) y públicos (YP).

Durante la actualización, se le pedirá autorizar a {{site.data.keyword.contdelivery_short}} para acceder a Whitewater {{site.data.keyword.ghe_short}} en su nombre.

## Adición de miembros a su repositorio de Whitewater {{site.data.keyword.ghe_short}} después de la actualización

Si el proyecto utiliza un repositorio alojado en JazzHub, durante la actualización se creará un nuevo repositorio en Whitewater {{site.data.keyword.ghe_short}}. Después de la actualización, la persona que inició la actualización debe añadir miembros del equipo al repositorio de Whitewater {{site.data.keyword.ghe_short}} y asegurarse de que tienen los permisos adecuados antes de poder acceder al nuevo repositorio.

## Resolución de problemas

A veces se produce un problema intermitente al intentar cambiar el destino de una etapa de despliegue del conducto. Cuando se produce este problema, se muestra un error en los campos **Organización** y **Espacio**.

Este problema habitualmente se produce cuando cambia el destino desde el conducto de forma que el conducto que se crea durante la actualización desplegará correctamente a los mismos destinos que los utilizados con anterioridad.

Si intenta cambiar el destino, y se produce este error, conmute entre destinos un par de veces hasta que se cumplimenten los campos **Organización** y **Espacio**.

Un problema relacionado ocasionalmente hace que fallen los despliegues a destinos YS1. Este caso no es nada habitual y, si ocurre, vuelva a ejecutar el conducto.

El equipo de IBM DevOps Services está trabajando activamente para resolver estos problemas.
