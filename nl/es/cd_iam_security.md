---

copyright:
  years:  2018, 2019
lastupdated: "2019-05-27"

keywords: Administrator Create, Administrator Update, Editor Update, Update

subcollection: ContinuousDelivery

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Gestión del acceso de usuario a Continuous Delivery con Identity and Access Management
{: #cd-iam-security}

El acceso a las instancias de servicio de {{site.data.keyword.contdelivery_full}} en grupos de recursos para los usuarios de la cuenta está controlado por {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM). 

**Notas**: 

* El acceso de usuario para las instancias de servicio de {{site.data.keyword.contdelivery_short}} y las instancias de la cadena de herramientas se gestiona por separado. Para obtener más información sobre la gestión del acceso de usuario a las cadenas de herramientas de los grupos de recursos, consulte [Gestión del acceso de usuario a las cadenas de herramientas con Identity and Access Management](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security).

* El acceso de usuario para las cadenas de herramientas de organizaciones de Cloud Foundry se gestiona de forma distinta que el acceso de usuario a las cadenas de herramientas en grupos de recursos. Para obtener más información sobre cómo gestionar el acceso de usuario a las cadenas de herramientas de organizaciones de Cloud Foundry, consulte [Gestión del acceso a cadenas de herramientas de las organizaciones de Cloud Foundry](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs).

Todos los usuarios que acceden al servicio de {{site.data.keyword.contdelivery_short}} en su cuenta deben tener asignada una política de acceso con un rol de usuario IAM definido. Esta política determina qué acciones puede realizar el usuario dentro del contexto del servicio o instancia que seleccione. Las acciones permitidas se personalizan y definen mediante el servicio {{site.data.keyword.Bluemix_notm}} como operaciones que se permiten que se realicen en el servicio. A continuación, las acciones se correlacionan con los roles de usuario de IAM.

Las políticas permiten otorgar el acceso en distintos niveles. Algunas de las opciones son las siguientes: 

* Acceso a todas las instancias del servicio de su cuenta
* Acceso a una instancia de servicio individual de su cuenta
* Acceso a un recurso específico dentro de una instancia
* Acceso a todos los servicios habilitados para IAM de su cuenta

Después de definir el ámbito de la política de acceso, debe asignar un rol. Revise las tablas siguientes que describen las acciones que cada rol permite dentro del servicio de {{site.data.keyword.contdelivery_short}}.

En la tabla siguiente se detallan las acciones que se correlacionan con los roles de gestión de plataforma. Los roles de gestión de plataforma permiten a los usuarios realizar tareas en los recursos de servicio a nivel de plataforma, por ejemplo, asignar acceso de usuario para el servicio, crear o suprimir ID de servicio, crear instancias y enlazar instancias a las aplicaciones.

| Rol de gestión de plataforma | Descripción de acciones | Acciones de ejemplo|
|:-----------------|:-----------------|:-----------------|
| Visor, Operador | Ver instancias del servicio de {{site.data.keyword.contdelivery_short}}. | <ul><li>Pulse una instancia de servicio de {{site.data.keyword.contdelivery_short}} para abrir su panel de control.</li></ul>|
| Editor, Administrador | Crear, ver, actualizar, modificar el plan y suprimir instancias del servicio de {{site.data.keyword.contdelivery_short}}. |<ul><li>Suministrar una instancia de {{site.data.keyword.contdelivery_short}} en un grupo de recursos.</li><li>Suprimir una instancia de {{site.data.keyword.contdelivery_short}} de un grupo de recursos.</li><li>Cambiar un plan de instancias de {{site.data.keyword.contdelivery_short}} de Lite a Professional.</li></ul> |
| Administrador | Actualizar la lista Usuarios autorizados.| <ul><li>Añada un usuario a la lista Usuarios autorizados.</li><li>Eliminar un usuario de la lista Usuarios autorizados.</li></ul> |
{: caption="Tabla 1. Roles de usuario y acciones de IAM" caption-side="top"}

 Para {{site.data.keyword.contdelivery_short}}, existen las acciones siguientes:

| Acción | Funcionamiento en servicio | Rol
|:-----------------|:-----------------|:--------------|
| create | Suministrar una instancia de servicio de {{site.data.keyword.contdelivery_short}} en un grupo de recursos. | Administrador, Editor |
| update | Actualizar una instancia de servicio de {{site.data.keyword.contdelivery_short}} en un grupo de recursos. Por ejemplo, cambie el nombre de la instancia de servicio. | Administrador, Editor |
| update_plan | Cambiar el plan para la instancia de servicio de {{site.data.keyword.contdelivery_short}} en un grupo de recursos. | Administrador, Editor |
| delete | Suprimir una instancia de servicio de {{site.data.keyword.contdelivery_short}} de un grupo de recursos. | Administrador, Editor |
| retrieve | Ver una instancia de servicio de {{site.data.keyword.contdelivery_short}} en un grupo de recursos. | Administrador, Editor, Operador, Visor |
| add-auth-users | Añadir entradas a la lista Usuarios autorizados en el separador Gestionar dentro de la instancia de servicio de {{site.data.keyword.contdelivery_short}}. | Administrador, Escritor, Gestor |
| remove-auth-users | Eliminar entradas de la lista Usuarios autorizados en el separador Gestionar dentro de la instancia de servicio de {{site.data.keyword.contdelivery_short}}. | Administrador, Escritor, Gestor |
{: caption="Tabla 2. Acciones y operaciones de servicio" caption-side="top"}

En la tabla siguiente se detallan las acciones que se correlacionan con los roles de acceso al servicio. Los roles de acceso al servicio permiten a los usuarios acceder a {{site.data.keyword.contdelivery_short}} así como a la posibilidad de llamar a la API de {{site.data.keyword.contdelivery_short}}.

| Rol de acceso al servicio | Descripción de acciones | Acciones de ejemplo|
|:-----------------|:-----------------|:-----------------|
| Escritor, Gestor | Añadir y eliminar usuarios de la lista Usuarios autorizados en el separador Gestionar dentro de una instancia de servicio de {{site.data.keyword.contdelivery_short}}. | <ul><li>Añadir usuario autorizado.</li><li>Eliminar usuario autorizado.</li></ul>|
{: caption="Tabla 3. Acciones y roles de acceso al servicio de IAM" caption-side="top"}

Para obtener información sobre la asignación de roles de usuario en la interfaz de usuario, consulte [Gestión del acceso de IAM](/docs/iam?topic=iam-iammanidaccser).
