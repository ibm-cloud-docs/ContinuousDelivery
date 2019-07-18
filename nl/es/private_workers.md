---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: IBM Cloud Continuous Delivery, private workers integration

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}


# Cómo trabajar con trabajadores privados de {{site.data.keyword.deliverypipeline}}
{: #private-workers}

{{site.data.keyword.deliverypipeline}} utiliza trabajadores públicos y privados para ejecutar trabajos de conducto. De forma predeterminada, los trabajos de conducto se ejecutan utilizando trabajadores públicos en una infraestructura compartida pública gestionada por IBM. 
{: shortdesc}

En determinados casos de ejemplo, es posible que {{site.data.keyword.deliverypipeline}} requiera acceso a recursos internos o locales. En estas situaciones, puede conectarse e integrar un trabajador privado de {{site.data.keyword.deliverypipeline}} para que se ejecute en su propia infraestructura de Kubernetes.

## Requisitos previos
{: #private_workers_prereqs}

Antes de configurar un trabajador privado, asegúrese de que tiene los recursos siguientes en su lugar:

* Un clúster Kubernetes. Debe tener un clúster para instalar un trabajador privado. Puede proporcionar su propio clúster o puede [configurar un clúster](https://cloud.ibm.com/kubernetes/clusters){:external} desde {{site.data.keyword.containerlong_notm}}.

* Una cadena de herramientas con un conducto que contenga al menos una etapa. Puede utilizar una cadena de herramientas existente o [crear una cadena de herramientas](https://cloud.ibm.com/devops/create){:external}.

## Configuración de un trabajador privado de {{site.data.keyword.deliverypipeline}}
{: #set_up_private_worker}

Realice los pasos siguientes para configurar un trabajador privado:

1. Configure la integración de las herramientas de trabajador privado de {{site.data.keyword.deliverypipeline}} para su cadena de herramientas.
2. Configure su clúster Kubernetes con un trabajador privado.
3. Utilice el trabajador privado en su conducto.

### Configuración de la integración de herramientas de trabajador privado de {{site.data.keyword.deliverypipeline}}
{: #configure_private_worker_integration}

Realice los pasos siguientes para configurar la integración de herramientas de trabajador privado de {{site.data.keyword.deliverypipeline}} para su cadena de herramientas:

1. Si configura la integración de esta herramienta al crear la cadena de herramientas, en la sección Integraciones configurables, pulse **Trabajador privado de {{site.data.keyword.deliverypipeline}}**.
1. Si tiene una cadena de herramientas y le está añadiendo esta integración de herramientas, en el panel de control de DevOps, en la página Cadenas de herramientas, pulse la cadena de herramientas para abrir su página Visión general. Si lo prefiere, en la página Visión general de la app, en la tarjeta de Entrega continua, pulse **Ver cadena de herramientas** y luego **Visión general**.

 a. Pulse **Añadir una herramienta**.

 b. En la sección Integraciones de herramientas, pulse **Trabajador privado de {{site.data.keyword.deliverypipeline}}**.

1. Escriba un nombre para la integración de herramientas. Este nombre identifica una agrupación de trabajadores privados en el separador **Trabajadores** de la etapa del conducto.
1. Escriba su clave de API de ID de servicio para autenticar el acceso a la cola de trabajo, en la que uno o más trabajadores privados pueden buscar trabajo. Si no tiene una clave de API de ID de servicio, pulse **Crear** para generar una para este trabajador privado.
1. Pulse **Crear integración**.
1. Desde su cadena de herramientas, pulse **Trabajador privado de {{site.data.keyword.deliverypipeline}}** para ver una lista de todos los trabajadores registrados utilizando una clave de API asociada con este ID de servicio.

Para obtener más información sobre la integración de herramientas de **Trabajador privado de {{site.data.keyword.deliverypipeline}}**, consulte [Configuración del trabajador privado de {{site.data.keyword.deliverypipeline}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations#privateworker).

### Configuración del clúster Kubernetes
{: #configure_kubernetes_cluster}

Configure su clúster Kubernetes con un trabajador privado:

1. En el panel de control de DevOps, en la página **Cadenas de herramientas**, pulse una cadena de herramientas para abrir la página Visión general correspondiente. Si lo prefiere, en la página Visión general de la app, tarjeta Entrega continua, pulse **Ver cadena de herramientas** y, a continuación, **Visión general**.
1. Pulse la tarjeta de la integración de herramientas de trabajador privado de {{site.data.keyword.deliverypipeline}} que desee configurar.
1. Pulse **Iniciación** y luego siga los pasos para instalar y registrar un trabajador privado en su clúster Kubernetes.

### Utilización del trabajador privado de {{site.data.keyword.deliverypipeline}} en su conducto
{: #use_private_worker_pipeline}

Realice los pasos siguientes para utilizar el trabajador privado en su conducto:

1. En el panel de control de DevOps, en la página **Cadenas de herramientas**, pulse una cadena de herramientas para abrir la página Visión general correspondiente. Si lo prefiere, en la página Visión general de la app, tarjeta Entrega continua, pulse **Ver cadena de herramientas** y, a continuación, **Visión general**.
1. Pulse la tarjeta del conducto con el que desee utilizar el trabajador privado.
1. En la página Conducto, en la etapa, pulse el icono **Configuración de etapa** y, a continuación, pulse **Configurar etapa**.
1. Pulse el separador **Trabajadores**.
1. Seleccione el trabajador privado que desee utilizar en el conducto. 

 De forma predeterminada, los trabajos de una etapa del conducto se ejecutan utilizando una agrupación de trabajadores compartidos gestionados por IBM en la región donde se define el conducto.
 {: tip}
 
1. Pulse **Guardar**.
1. Puede ejecutar la etapa manualmente o esperar a que un desencadenante ejecute los trabajos en la etapa utilizando el trabajador privado especificado en el clúster Kubernetes asociado. Puede ver la salida del archivo de registro de los trabajos para determinar qué trabajador se ha utilizado.  


## Modificación de las credenciales de la integración de herramientas de trabajador privado de {{site.data.keyword.deliverypipeline}}
{: #modify_private_worker}

Tras configurar el trabajador privado, puede actualizar las credenciales que se utilizan para la integración de herramientas. Es posible que desee cambiar estas credenciales si se suprimen, si caducan o si se ven comprometidas. Puede actualizar las credenciales creando un nuevo ID de servicio o actualizando la clave de API.

### Creación de un ID de servicio
{: #create_service_id}

Realice los pasos siguientes para crear un ID de servicio:

1. En el panel de control de DevOps, en la página **Cadenas de herramientas**, pulse una cadena de herramientas para abrir la página Visión general correspondiente. Si lo prefiere, en la página Visión general de la app, tarjeta Entrega continua, pulse **Ver cadena de herramientas** y, a continuación, **Visión general**.
1. En la tarjeta para la integración de herramientas de trabajadores privados que desee modificar, pulse el menú para acceder a las opciones de configuración.
1. Pulse **Crear**.
1. Especifique un nombre y una descripción para el ID de servicio.
1. Pulse **Guardar integración**.
1. En el panel de control de DevOps, en la página **Cadenas de herramientas**, pulse una cadena de herramientas para abrir la página Visión general correspondiente. Si lo prefiere, en la página Visión general de la app, tarjeta Entrega continua, pulse **Ver cadena de herramientas** y, a continuación, **Visión general**.
1. Pulse la tarjeta de la integración de herramientas de trabajador privado de {{site.data.keyword.deliverypipeline}} para la que desee especificar nuevas credenciales de usuario.
1. Pulse **Iniciación** y realice los pasos 2 y 3 para registrar y verificar el trabajador privado en el clúster.

### Actualización de la clave de API
{: #update_api_key}

Realice los pasos siguientes para actualizar la clave de API a utilizar con la integración de herramientas de trabajador privado de {{site.data.keyword.deliverypipeline}}:

1. En el panel de control de DevOps, en la página **Cadenas de herramientas**, pulse una cadena de herramientas para abrir la página Visión general correspondiente. Si lo prefiere, en la página Visión general de la app, tarjeta Entrega continua, pulse **Ver cadena de herramientas** y, a continuación, **Visión general**.
1. En la tarjeta para la integración de herramientas de trabajador privado de {{site.data.keyword.deliverypipeline}} que desee modificar, pulse el menú para acceder a las opciones de configuración.
1. Especifique la nueva clave de API. 
1. Pulse **Guardar integración**.

## Supresión de un trabajador privado de {{site.data.keyword.deliverypipeline}}
{: #delete_private_worker}

Realice los pasos siguientes para suprimir un trabajador privado:

1. Suprima el trabajador privado de la agrupación de trabajadores.
1. Suprima el trabajador privado de su clúster Kubernetes.

### Supresión de un trabajador privado de {{site.data.keyword.deliverypipeline}} de la agrupación de trabajadores

Realice los pasos siguientes para suprimir el trabajador privado de la agrupación de trabajadores:

1. En el panel de control de DevOps, en la página **Cadenas de herramientas**, pulse una cadena de herramientas para abrir la página Visión general correspondiente. Si lo prefiere, en la página Visión general de la app, tarjeta Entrega continua, pulse **Ver cadena de herramientas** y, a continuación, **Visión general**.
1. Pulse la tarjeta de la integración de herramientas de trabajador privado de {{site.data.keyword.deliverypipeline}} que desee configurar.
1. Pulse **Visión general**.
1. Pulse el menú del trabajador privado que desee suprimir para acceder a las opciones de configuración.
1. Pulse **Eliminar** y, a continuación, pulse **Confirmar**.

### Supresión de un trabajador privado de {{site.data.keyword.deliverypipeline}} de su clúster Kubernetes

Realice los pasos siguientes para suprimir el trabajador privado del clúster:

1. Pulse la tarjeta de la integración de herramientas de trabajador privado de {{site.data.keyword.deliverypipeline}} que desee configurar.
1. Pulse **Iniciación** y siga los pasos para suprimir el trabajador privado del clúster.

## Supresión de la integración de herramientas de trabajador privado de {{site.data.keyword.deliverypipeline}}
{: #delete_private_workers_tool_integration}

Si suprime una integración de herramientas de trabajador privado de {{site.data.keyword.deliverypipeline}} de la cadena de herramientas, la supresión no se puede deshacer.
{: important}

Realice los pasos siguientes para suprimir una integración de herramientas de trabajador privado de {{site.data.keyword.deliverypipeline}}:

1. En el panel de control de DevOps, en la página **Cadenas de herramientas**, pulse una cadena de herramientas para abrir la página Visión general correspondiente. Si lo prefiere, en la página Visión general de la app, tarjeta Entrega continua, pulse **Ver cadena de herramientas** y, a continuación, **Visión general**.
1. En la tarjeta para la integración de herramientas de trabajador privado de {{site.data.keyword.deliverypipeline}} que desee suprimir, pulse el menú para acceder a las opciones de configuración.
1. Para suprimir la integración de herramienta de su cadena de herramientas, pulse **Suprimir**.
1. Confirme la acción pulsando **Suprimir**. La integración de herramientas de trabajador privado de {{site.data.keyword.deliverypipeline}} se eliminará de la cadena de herramientas y ya no estará disponible en el separador **Trabajadores** de la página Configuración de etapa del conducto de entrega.

Si suprime la integración de herramientas de trabajador privado de {{site.data.keyword.deliverypipeline}} de una cadena de herramientas y el trabajador privado está configurado para una etapa del conducto, seguirá apareciendo en el separador **Trabajadores** de la página Configuración de etapa. No obstante, el trabajador privado estará inhabilitado y etiquetado con REMOVED (eliminado). Debe seleccionar un trabajador privado distinto (si existe alguno) o utilizar un trabajador público en su lugar.
{: tip}
