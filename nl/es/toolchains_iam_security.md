---

copyright:
  years:  2018
lastupdated: "2018-11-14"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Gestión del acceso de usuario a las cadenas de herramientas con Identity and Access Management

El acceso a las cadenas de herramientas de los grupos de recursos para los usuarios de la cuenta está controlado por {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM). 

**Notas**: 

* El acceso de usuario para las instancias de la cadena de herramientas y las instancias de servicio de {{site.data.keyword.contdelivery_short}} se gestiona por separado. Para obtener más información sobre la gestión del acceso de usuario a instancias de servicio de {{site.data.keyword.contdelivery_short}} en grupos de recursos, consulte [Gestión del acceso de usuario a {{site.data.keyword.contdelivery_short}} con Identity and Access Management](/docs/services/ContinuousDelivery/cd_iam_security.html){: new_window}.

* El acceso de usuario para las cadenas de herramientas de organizaciones de Cloud Foundry se gestiona de forma distinta que el acceso de usuario a las instancias de servicio de {{site.data.keyword.contdelivery_short}} de los grupos de recursos. Para obtener más información sobre cómo gestionar el acceso de usuario a las cadenas de herramientas de organizaciones de Cloud Foundry, consulte [Gestión del acceso a cadenas de herramientas de las organizaciones de Cloud Foundry](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_orgs.html){: new_window}.

A cada usuario que acceda a las cadenas de herramientas de su cuenta se le debe asignar una política de acceso con un rol de usuario IAM definido. Esta política determina qué acciones puede realizar el usuario dentro del contexto del servicio o instancia que seleccione. Las acciones permitidas se personalizan y definen mediante el servicio {{site.data.keyword.Bluemix_notm}} como operaciones que se permiten que se realicen en el servicio. A continuación, las acciones se correlacionan con los roles de usuario de IAM.

Las políticas permiten otorgar acceso en distintos niveles, incluidos: 

* Acceso en todas las instancias del servicio en su cuenta
* Acceso a una instancia de servicio individual en su cuenta
* Acceso a un recurso específico dentro de una instancia
* Acceso a todos los servicios habilitados para IAM en su cuenta

Después de definir el ámbito de la política de acceso, debe asignar un rol. Revise las tablas siguientes que describen las acciones que cada rol permite dentro de las cadenas de herramientas.

En la tabla siguiente se detallan las acciones que se correlacionan con los roles de gestión de plataforma. Los roles de gestión de plataforma permiten a los usuarios realizar tareas en los recursos de servicio a nivel de plataforma, por ejemplo, asignar acceso de usuario para el servicio, crear o suprimir ID de servicio, crear instancias y enlazar instancias a las aplicaciones.

| Rol de gestión de plataforma | Descripción de acciones | Acciones de ejemplo|
|:-----------------|:-----------------|:-----------------|
| Visor, Operador | Ver las cadenas de herramientas y las interconexiones de entrega. Ejecutar interconexiones de entrega. | <ul><li>Pulse en una cadena de herramientas para abrir su página Visión general.</li><li>Pulse el icono **Etapa de ejecución** de la etapa en la que se encuentra el trabajo de interconexión.</li></ul> |
| Editor, Administrador | Cree, visualice, actualice y suprima las cadenas de herramientas y las interconexiones de entrega. |<ul><li>En el panel de control de DevOps, en la página **Cadenas de herramientas**, pulse **Crear una cadena de herramientas**.</li><li>En el panel de control de DevOps, en la página **Cadenas de herramientas**, pulse sobre la cadena de herramientas para abrir la página Visión general correspondiente.</li><li>En el panel de control de DevOps, en la página **Cadenas de herramientas**, pulse sobre la cadena de herramientas que desea suprimir. Pulse el menú **Más acciones**, que se encuentra junto a **Ver app**. Pulse **Suprimir**.</li></ul> |
{: caption="Tabla 1. Roles y acciones de usuario IAM" caption-side="top"}

 Para las cadenas de herramientas, existen las acciones siguientes:

| Acción | Funcionamiento en servicio | Rol
|:-----------------|:-----------------|:--------------|
| create | Crear una cadena de herramientas en un grupo de recursos. | Administrador, Editor |
| update | Actualizar una cadena de herramientas en un grupo de recursos. Por ejemplo, cambie el nombre de la cadena de herramientas. Cambie las interconexiones de entrega que están enlazadas a las cadenas de herramientas de un grupo de recursos. | Administrador, Editor |
| update_plan | No aplicable. | Administrador, Editor |
| delete | Suprimir una cadena de herramientas de un grupo de recursos. | Administrador, Editor |
| retrieve | Ver los detalles de una cadena de herramientas en un grupo de recursos. Ver y ejecutar las interconexiones de entrega que están enlazadas a las cadenas de herramientas de un grupo de recursos. | Administrador, Editor, Operador, Visor |
| list-bindings | Ver las integraciones de herramientas que están enlazadas a una cadena de herramientas en un grupo de recursos. | Administrador, Editor, Visor |
| create-bindings | Añadir una integración de herramientas a una cadena de herramientas en un grupo de recursos. | Administrador, Editor |
| delete-bindings | Eliminar una integración de herramientas de una cadena de herramientas en un grupo de recursos. | Administrador, Editor |
{: caption="Tabla 2. Acciones y operaciones de servicio" caption-side="top"}

Para obtener información sobre la asignación de roles de usuario en la IU, consulte [Gestión del acceso IAM](/docs/iam/mngiam.html#iammanidaccser).

<!--This link is not live in production yet. Use https://console.bluemix.net/docs/iam/iamusermanage.html#iamusermanage until the link above is available in production.-->
