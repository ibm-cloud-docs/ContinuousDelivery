---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Actualice su proyecto {{site.data.keyword.jazzhub_short}} a una cadena de herramientas
{: #upgrade_projects}

{{site.data.keyword.jazzhub}} está evolucionando hacia {{site.data.keyword.contdelivery_full}}. Como parte de este cambio, los proyectos se actualizan a cadenas de herramientas.

Puede actualizar su proyecto o esperar a que se actualice automáticamente. Asegúrese de cumplir los [requisitos previos](#upgrade_prereqs) y de actualizar el proyecto lo antes posible para poder controlar el nombre de la cadena de herramientas y la organización para la que se crea.
{: shortdesc}

**Preguntas más frecuentes**

- [Mi proyecto JazzHub está asociado a la región del Reino Unido, pero mi cadena de herramientas está en la región EE.UU. sur. ¿Cómo se procederá?](#faq_region)
- [¿Qué ocurre con mis paneles de control y elementos de trabajo en Track &amp; Plan cuando realice la actualización?](#faq_tp)
- [¿Qué le ocurre al código del repositorio cuando realice la actualización?](#faq_repo)
- [¿Qué le ocurre a mis definiciones de compilación en mi proyecto cuando actualice a una cadena de herramientas? ](#faq_build)
- [Necesito crear una organización para mi proyecto que se actualiza a una cadena de herramientas. Entiendo que necesito añadir una tarjeta de crédito a mi cuenta antes de que pueda crear una organización. ¿Se realizarán cargos en mi tarjeta de crédito? ](#faq_charges)
- [No puedo encontrar o acceder a mi cadena de herramientas. ¿Qué puedo hacer?](#faq_find)
- [Mi proyecto está asociado con la región Reino Unido. Después de la actualización, veo mensajes de error, mis colegas no pueden acceder a la cadena de herramientas, y no veo mi cadena de herramientas en la página Cadenas de herramientas de la plataforma {{site.data.keyword.Bluemix_notm}}. ¿Qué ocurre?](#faq_uk)

## Cadenas de herramientas
{: #compare_toolchains}

Las cadenas de herramientas son como proyectos, con algunas diferencias importantes:

- Los proyectos solo pueden tener un repositorio (repo) y un conducto. Las cadenas de herramientas pueden tener tantos repositorios y conductos como sea necesario.
- Las cadenas de herramientas pueden incluir herramientas que no están disponibles en proyectos, como por ejemplo Slack, Sauce Labs, PagerDuty y {{site.data.keyword.DRA_full}}.
- El acceso a las cadenas de herramientas se gestiona mediante organizaciones estándares de {{site.data.keyword.Bluemix_notm}}. La condición de miembro se mantiene a nivel de organización, a diferencia de los proyectos, donde los miembros se mantienen a nivel de proyecto.

Puede obtener información sobre cadenas de herramientas en [YouTube ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://youtu.be/2SIPE1e7NJ4){: new_window} o desde [Iniciación a {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery/index.html).
[![Enlace externo a YouTube](images/CD_video.png)](https://youtu.be/2SIPE1e7NJ4){: new_window}

## Requisitos previos
{: #upgrade_prereqs}

- Para acceder a la cadena de herramientas actualizada del proyecto, necesita un ID de {{site.data.keyword.Bluemix_notm}}. Antes de actualizar, debe verificar que tiene un ID de {{site.data.keyword.Bluemix_notm}} activo. Si no dispone de uno, [regístrese](https://console.ng.bluemix.net/registration/).
- Asegúrese de que el propietario del proyecto de {{site.data.keyword.jazzhub_short}} sea correcto. La cadena de herramientas que se crea a partir del proyecto forma parte de la organización de {{site.data.keyword.Bluemix_notm}} de dicho propietario.
- Asegúrese de que la organización y el espacio donde desea crear la cadena de herramientas estén en {{site.data.keyword.Bluemix_notm}} Público en la región EE.UU. sur. Para confirmar que tiene una organización y un espacio válidos en EE.UU. sur, inicie sesión en [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window} y cree un espacio si se le solicita que cree uno.
- Si está planeando iniciar la actualización, asegúrese de que es miembro de cada organización y espacio en el que se despliega el conducto. Cualquier administrador de proyecto puede iniciar la actualización. Sin embargo, si el administrador que inicia la actualización no es miembro de cada organización y espacio en el que se despliega el conducto, éste último no se podrá crear. La persona que inicia la actualización se convierte en el propietario del repositorio en la cadena de herramientas.
- Eclipse Orion {{site.data.keyword.webide}} en la cadena de herramientas no es el {{site.data.keyword.webide}} asociado al proyecto. Si utiliza el {{site.data.keyword.webide}} y tiene cambios sin confirmar, confírmelos antes de actualizar.


## Actualización de un proyecto a una cadena de herramientas
{: #project_to_toolchain}

Los proyectos de hub.jazz.net y de cadenas de herramientas están alojados en la región EE.UU. sur. Si el proyecto se ha configurado para desplegar apps en otra región, se siguen desplegando apps en dicha región después de que se haya actualizado a una cadena de herramientas.
{: tip}

Cuando el proyecto esté listo para actualizarse, se mostrará un mensaje en la tarjeta del proyecto y en la página Visión general.

![Imagen de la tarjeta con la etiqueta Listo para actualizar](images/card-project-to-upgrade.png)

![Mensaje Momento de actualizar](images/banner-ready-to-upgrade.png)

Encontrará proyectos que están preparados para la actualización en el menú de la página Mis proyectos:

![Imagen del elemento de menú Proyectos para actualizar](images/menu-projects-to-upgrade.png)
{: tip}

Cuando inicia la actualización, las transmisiones de conducto del proyecto se bloquean. No puede ejecutarlas ni modificarlas. Si revierte la actualización mediante la supresión de la cadena de herramientas, el conducto es desbloquea.

Si el proyecto utiliza un repositorio Git alojado en JazzHub, después de iniciar la actualización el repositorio se bloquea para garantizar la integridad de los datos que se mueven a la cadena de herramientas. Si revierte la actualización mediante la supresión de la cadena de herramientas, el repositorio de JazzHub es desbloquea.

Para ver detalles sobre cómo se trata cada tipo de repositorio en el proceso de actualización, consulte la siguiente tabla.

|Repo proyecto |Tipo de proyecto	|Repo cadena de herramientas |
|:----------|:------------------------------|:------------------|
|github.com 		|Privado o público 		|El mismo repo github.com con {{site.data.keyword.Bluemix_notm}} público.	|
|hub.jazz.net/git		|Privado o público 		|Un nuevo repo en {{site.data.keyword.gitrepos}} con {{site.data.keyword.Bluemix_notm}} público.	|
{: caption="Tabla 1. Repositorios de proyecto correlacionados con repositorios de cadena de herramientas" caption-side="top"}

## Inicio del proceso de actualización
{: #start_upgrade}

Antes de iniciar el proceso de actualización, puede verlo en acción en [YouTube ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://youtu.be/LSr2e3uvyLs){: new_window}.
[![Enlace externo a YouTube](images/migration-video2.png)](https://youtu.be/LSr2e3uvyLs){: new_window}

Para actualizar el proyecto a una cadena de herramientas, siga estos pasos:

1. Para iniciar el proceso de actualización, en el mensaje de cabecera pulse **actualizar ahora**. Se abrirá la página "Cadena de herramientas de actualización de proyecto".

   ![Ejemplo de una página de actualización](images/project-upgrade-toolchain.png)

   Para obtener una visión general del proceso de actualización, lea la descripción de esta página. La cadena de herramientas incluye un nuevo conducto que contiene las mismas etapas y trabajos que el conducto del proyecto. Además, la cadena de herramientas contiene un puntero a Eclipse Orion {{site.data.keyword.webide}} que se ejecuta en {{site.data.keyword.contdelivery_short}}.

   En este ejemplo, como el proyecto utiliza un repositorio público en github.com, la cadena de herramientas se conecta al mismo repositorio GitHub. Si el proyecto utiliza un repositorio Git que se aloja en JazzHub, el contenido de dicho repositorio se clona en un repositorio nuevo en {{site.data.keyword.gitrepos}}, que forma parte de {{site.data.keyword.contdelivery_short}}.

2. Para personalizar la cadena de herramientas, puede configurar algunos valores:

   - Para cambiar el nombre de la cadena de herramientas, edite el campo **Nombre**.

      ![Campo Nombre](images/name-change.png)

   - Para cambiar la organización de {{site.data.keyword.Bluemix_notm}} en la que se creará la cadena de herramientas, seleccione la organización en el menú de la cuenta:

      ![Selector de organización de {{site.data.keyword.Bluemix_notm}}](images/bluemix-organization-chooser.png)

   Puesto que las cadenas de herramientas se gestionan a nivel de organización, asegúrese de seleccionar una organización donde existan los miembros del proyecto que necesiten acceder a la cadena de herramientas, o se puedan añadir.

3. Si ha utilizado Track & Plan en el proyecto, puede transferir datos de Track & Plan a GitHub Issues.

   ![Opciones de Track and Plan](images/upgrade-tutorial-track-and-plan.png)

   - Indique si desea migrar los datos de Track & Plan.
   - De forma predeterminada, se migran todos los datos de Track & Plan. Si prefiere migrar solo los elementos de trabajo que forman parte de una determinada consulta, especifique la consulta.
   - Seleccione los atributos de elementos de trabajo que desea correlacionar con etiquetas en GitHub Issues.

4. Pulse **Crear**. Se crea la nueva cadena de herramientas y se muestra su página Visión general.

   ![Visión general de la cadena de herramientas actualizada](images/new-toolchain-page.png)

   - Para acceder al repositorio GitHub o al rastreador de problemas asociado, pulse **GitHub** o **Problemas**.
   - Para acceder al conducto, pulse **Conducto de entrega**.
   - Para acceder al {{site.data.keyword.webide}}, que aloja el contenido del repositorio que se ha extraído en el espacio de trabajo, pulse **Eclipse Orion {{site.data.keyword.webide}}**.

   Si vuelve al proyecto durante la actualización, el mensaje de cabecera puede indicar que la actualización está en curso, especialmente si el proceso de actualización implica importar código fuente en un repositorio nuevo o importar elementos de trabajo de Track &amp; Plan como problemas.

   ![Mensaje sobre el proyecto que se actualiza a una cadena de herramientas](images/project-being-upgraded-banner.png)

## Cómo revisitar el proyecto
{: #revisit_projects}

Está preparado para utilizar la nueva cadena de herramientas. Ahora el proyecto está etiquetado como "Actualizado" y se muestra un mensaje de configuración en la página Visión general.

![Imagen de tarjeta de proyecto con la etiqueta Actualizado](images/card-upgraded-project.png)

![Proyecto actualizado](images/banner-upgraded.png)

Puede ver los que los proyectos que se han actualizado seleccionando **Proyectos actualizados** en el menú de la página Mis proyectos:

![Imagen del elemento de menú Proyectos actualizados](images/menu-upgraded-projects.png)

Si tiene que revertir la actualización, suprima la cadena de herramientas. Puede suprimir su cadena de herramientas desde el menú **Más acciones** de la página visión general de la cadena de herramientas:

![imagen de la acción Suprimir del menú Más acciones](images/upgrade-tutorial-delete-toolchain.png)

Cuando vuelva al proyecto, se volverá a mostrar el mensaje de actualización y podrá volver a actualizar cuando esté preparado.

## Siguientes pasos
{: #upgrade_next_steps}

1. Confirme que la actualización se ha completado renovando el navegador y comprobando que aparezca el mensaje que indica que el proyecto se ha "actualizado a esta cadena de herramientas" en la página Visión general del proyecto:

   ![Mensaje de cabecera que indica que el proyecto se ha actualizado](images/banner-upgraded.png)

   Si el mensaje indica "actualice ahora", significa que la actualización ha fallado. Pulse el enlace **actualizar ahora** para volverlo a intentar.
   {: tip}

   ![Mensaje de cabecera que indica que el proyecto está listo para la actualización](images/banner-ready-to-upgrade.png)

2. Asigne a los miembros del equipo acceso a la cadena de herramientas.
    - Cada miembro del equipo debe tener una cuenta de {{site.data.keyword.Bluemix_notm}} válida. Los miembros del equipo que no tienen cuentas deben [registrarse ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/registration){:new_window}.
    - Otorgue acceso a los miembros de la organización a la cadena de herramientas desde la página Gestionar de la cadena de herramientas. Los miembros del proyecto existentes se añaden como miembros de la cadena de herramientas como parte del proceso de actualización. Para obtener más información sobre el control de accesos para cadenas de herramientas, consulte [Gestión de acceso ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access){:new_window}.
    - Si un usuario no es miembro de la organización a la que pertenece la cadena de herramientas, añádalo a la organización desde la página Gestionar organizaciones.
    - Si la cadena de herramientas utiliza {{site.data.keyword.gitrepos}}, todos los miembros del proyecto de JazzHub que tengan un ID de {{site.data.keyword.Bluemix_notm}} válido se añadirán al repositorio de {{site.data.keyword.gitrepos}} con los mismos privilegios que tenían en el proyecto de JazzHub. Si el proyecto de JazzHub incluye miembros que no tienen un ID de {{site.data.keyword.Bluemix_notm}} válido, deben registrarse para uno y ser añadidos al repositorio.
      Para obtener más información sobre la gestión de organizaciones, consulte [Gestión de organizaciones y espacios ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/admin/orgs_spaces.html#orgsspacesusers){:new_window}.

3. Utilice las herramientas de la cadena de herramientas en lugar de las herramientas del proyecto de {{site.data.keyword.jazzhub_short}}. Por ejemplo, para editar código desde un navegador, utilice el IDE Web de la cadena de herramientas.

4. Si utiliza {{site.data.keyword.gitrepos}}, debe autenticarlo mediante una señal de acceso personal o una clave SSH. Para obtener más información sobre las claves SSH, consulte [Creación de una señal de acceso o clave SSH clave para la autenticación](/docs/services/ContinuousDelivery/git_working.html#git_authentication). Para autenticar desde un cliente Git externo a través de https, siga estos pasos:
    1. Vaya a la [página Señales de acceso ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window} de los valores de usuario de {{site.data.keyword.gitrepos}}.
    2. Cree una señal de acceso personal que utilice **api** como ámbito.
    3. Vaya a la [página Cuenta ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://git.ng.bluemix.net/profile/account){:new_window} y busque su nombre de usuario correspondiente a {{site.data.keyword.gitrepos}}. El nombre de usuario aparece en la lista de la sección "Cambiar nombre de usuario" y se muestra como la primera parte del URL de cualquier repositorio personal que cree.
    4. Para autenticarse con {{site.data.keyword.gitrepos}} desde un cliente Git externo a través de HTTPS, utilice su nombre de usuario y su señal de acceso personal.
    5. Si desea reutilizar el repositorio local de su repositorio Git JazzHub, haga que el repositorio apunte al nuevo repositorio en {{site.data.keyword.gitrepos}}. Desde un shell de un terminal, vaya al directorio en el que se ha clonado el repositorio Git JazzHub. Escriba el mandato `git remote set-url`: `git remote set-url origin https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

        Para comprobar los URL definidos y sus nombres remotos, utilice el mandato `git remote -v`. El nombre remoto predeterminado es `origin`. Si tiene una configuración más avanzada, el formato del mandato es el siguiente: `git remote set-url <remote-name-that-uses-jazzhub-repo> https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`
        {: tip}

5. Cuando la cadena de herramientas esté configurada y empiece a utilizarla, tenga en cuenta la posibilidad de llevar a cabo alguno de los siguientes pasos, o todos ellos, para asegurarse de que nadie utilice su proyecto:
    - Añada un sufijo al nombre del proyecto para indicar que no se debe utilizar. Puede añadir `_NO_UTILIZAR` al final del nombre del proyecto.
    - Actualice la descripción del proyecto para indicar que ya no se utiliza y añada un puntero a la cadena de herramientas.
    - Elimine los miembros del proyecto.
    - Cuando ya no necesite el proyecto, suprímalo.

6. Opcional: para ver la madurez del desarrollo de un proyecto, las prácticas del equipo y la calidad del código base, añada IBM Cloud {{site.data.keyword.DRA_short}} a la cadena de herramientas. {{site.data.keyword.DRA_short}} aplica analíticas de desarrollador, de equipo y de despliegue a los proyectos DevOps. Para obtener más información, consulte [Iniciación a {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights/index.html).


## Resolución de problemas
{: #upgrade_troubleshoot}

Si encuentra un problema durante el proceso de actualización, intente uno o varios de estos pasos de resolución de problemas:

- Consulte los [requisitos previos](#upgrade_prereqs) para asegurarse de que los cumple. En particular, asegúrese de que es miembro de cada organización y espacio en el que se despliega el conducto.
- Si el problema se ha producido durante el primer intento de actualización y se cumplen todos los requisitos previos, intente la actualización de nuevo.
- Si el proyecto utiliza Jazz SCM o Git alojado por IBM para el control de origen, compruebe el tamaño del repositorio. Si es mayor que 500 MB, [póngase en contacto con el equipo de servicios de DevOps ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}.
- Si no puede encontrar la cadena de herramientas o el acceso a su cadena de herramientas, consulte [esta entrada de preguntas más frecuentes](#faq_find).
- Si sigue teniendo problemas, publique una pregunta en el [foro de soporte ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. En su publicación en el foro, incluya los URL del proyecto {{site.data.keyword.jazzhub_short}} y de la cadena de herramientas de {{site.data.keyword.contdelivery_short}} y marque la publicación con la etiqueta `devops-services`.


## Preguntas más frecuentes
{: #upgrade_faq}

### Mi proyecto JazzHub está asociado a la región del Reino Unido, pero mi cadena de herramientas está en la región EE.UU. sur. ¿Cuál es el funcionamiento?
{: #faq_region}

Los proyectos de hub.jazz.net y de cadenas de herramientas están alojados en la región EE.UU. sur. Si el proyecto está configurado para desplegar apps en otra región, por ejemplo el Reino Unido, seguirá desplegando apps en dicha región después de que se haya actualizado a una cadena de herramientas. Por lo tanto, nada cambia realmente con respecto a dónde se alojan los datos. En el futuro, las cadenas de herramientas estarán disponibles en más regiones.

### ¿Qué ocurre con mis paneles de control y elementos de trabajo en Track &amp; Plan cuando realice la actualización?
{: #faq_tp}

El servicio {{site.data.keyword.contdelivery_short}} proporciona funcionalidades de seguimiento de problemas a través de {{site.data.keyword.gitrepos}}, que IBM aloja y se basa en GitLab Community Edition. {{site.data.keyword.contdelivery_short}} también da soporte a las integraciones con otras herramientas de seguimiento de problemas y planificación como, por ejemplo, GitHub Issues y JIRA.

Durante el proceso de actualización, puede elegir migrar sus elementos de Track &amp; Plan a Git Issues. Tanto GitHub Issues como {{site.data.keyword.gitrepos}} proporcionan paneles kanban y seguimiento de problemas para realizar la planificación. Para obtener más información sobre los Paneles de problemas, una característica kanban en Git Repos and Issue Tracking, consulte [Paneles de problemas ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://git.ng.bluemix.net/help/user/project/issue_board.md){: new_window}.

Para aquellos usuarios que necesiten la misma funcionalidad que la ofrecida por JazzHub Track &amp; Plan, ahora en desuso, hay disponible el nuevo servicio IBM Track and Plan on Cloud para comprar aparte en algunos países en base a un uso por usuario y por mes. Con este servicio en la nube, obtendrá la funcionalidad completa, equivalente a la que se ofrece para licencias de contribuidor de Rational Team Concert, en una suscripción en la nube de arrendatario único.

Este nuevo servicio IBM Track and Plan on Cloud proporciona una mayor funcionalidad que JazzHub Track &amp; Plan, ahora en desuso, dando soporte a la personalización de procesos, a jerarquías de proceso, a SAFe o a muchos otros métodos híbridos y ágiles y además ofrece la escalabilidad para crecer más allá de un proyecto individual. Se basa en la última versión de Rational Team Concert 6.0.3 y en los próximos 60 días estará en la versión 6.0.4, mientras que JazzHub Track &amp; Plan se basaba en Rational Team Concert 5.x. Es posible una migración de datos a IBM Track and Plan on Cloud a través de servicios adicionales. Puede ponerse en contacto con [Tom Hollowell ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](mailto:trhollow@us.ibm.com){:new_window}, responsable de ventas de Connected Products SaaS para obtener más información.

Para obtener información sobre IBM Track and Plan on Cloud, o para comprar en línea, vaya a [IBM Marketplace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window}.

Además, es una opción adquirir software de automatización de compilaciones y gestión de código fuente, [Rational Team Concert on Cloud ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/us-en/marketplace/change-and-configuration-management/purchase#product-header-top){: new_window}.

### ¿Qué le ocurre al código del repositorio cuando realice la actualización?
{: #faq_repo}

Después de la actualización, el nuevo servicio Git es comparable al que tenía con anterioridad. Si ha utilizado github.com con el proyecto de JazzHub, su cadena de herramientas estará conectada con el mismo repositorio de GitHub. Si el proyecto JazzHub ha utilizado Git alojado en IBM, el contenido de dicho repositorio se clonará en un repositorio nuevo en {{site.data.keyword.gitrepos}}, que forma parte de {{site.data.keyword.contdelivery_short}} y está alojado por IBM.

Para ver detalles sobre cómo se trata cada tipo de repositorio en el proceso de actualización, consulte la siguiente tabla.

|Repo proyecto |Tipo de proyecto	|Repo cadena de herramientas |
|:----------|:------------------------------|:------------------|
|github.com 		|Privado o público 		|El mismo repo github.com con {{site.data.keyword.Bluemix_notm}} público.	|
|hub.jazz.net/git		|Privado o público 		|Un nuevo repositorio público o privado en {{site.data.keyword.gitrepos}} con {{site.data.keyword.Bluemix_notm}} público.	|
{: caption="Tabla 1. Repositorios de proyecto correlacionados con repositorios de cadena de herramientas" caption-side="top"}


### ¿Qué le ocurre a mis definiciones de compilación en mi proyecto cuando actualice a una cadena de herramientas?
{: #faq_build}

Si está compilando su código fuente utilizando Jazz en lugar de Delivery Pipeline, debe migrar de forma manual sus definiciones de compilación a Delivery Pipeline en su cadena de herramientas.

Si utiliza Jazz SCM como repositorio de código fuente y utiliza Delivery Pipeline para compilar su código fuente, el código fuente en Jazz SCM se mueve de forma automática a un repositorio Git. Su configuración de Delivery Pipeline permanece inalterada, excepto que consume el código fuente desde el repositorio Git en lugar de hacerlo desde Jazz SCM.

### Necesito crear una organización para mi proyecto que se actualizará a una cadena de herramientas. Entiendo que necesito añadir una tarjeta de crédito a mi cuenta antes de que pueda crear una organización. ¿Se realizarán cargos en mi tarjeta de crédito?
{: #faq_charges}

Como [cliente de Pago según uso ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window}, si utiliza un tiempo de ejecución, servicio o componente más allá de las concesiones gratuitas que tiene en el catálogo de {{site.data.keyword.Bluemix_notm}}, se le cobrará por ello. Para una estimación de la utilización, consulte la [hoja de cálculos de precios ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window}. Para conocer los precios actuales para Continuous Delivery, consulte el [catálogo de {{site.data.keyword.Bluemix_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/catalog/services/continuous-delivery){: new_window}.

Si es un empleado de IBM, los proyectos internos de IBM se pueden facturar a los departamentos en lugar de hacerlo a su tarjeta de crédito personal. Si necesita recursos más allá de los asignados de forma gratuita a los empleados de IBM, cree una incidencia de soporte.

### No puedo encontrar o acceder a mi cadena de herramientas. ¿Qué puedo hacer?
{: #faq_find}

Las cadenas de herramientas están alojadas en organizaciones de {{site.data.keyword.Bluemix_notm}}. El proceso de actualización añade todos los miembros del proyecto de JazzHub a la cadena de herramientas. Sin embargo, a menos que el propietario de la organización {{site.data.keyword.Bluemix_notm}} añada dichos usuarios a la organización, no podrán ver la cadena de herramientas.

Para acceder a su cadena de herramientas, vaya a la plataforma {{site.data.keyword.Bluemix_notm}}, pulse el icono de menú y pulse **Servicios &gt; DevOps**. Se abrirá la página de Cadenas de herramientas. Asegúrese de que se encuentre en la región EE.UU. sur y de que se encuentra en la organización que contiene la cadena de herramientas. Si la cadena de herramientas no está listada en la página Cadenas de herramientas, consulte [esta entrada de preguntas más frecuentes](#faq_uk).

Como alternativa, mientras que el sitio JazzHub todavía esté disponible, puede ir a la cadena de herramientas pulsando el enlace en el banner de la página Visión general del proyecto.

### Mi proyecto está asociado con la región Reino Unido. Después de la actualización, veo mensajes de error, mis colegas no pueden acceder a la cadena de herramientas, y no veo mi cadena de herramientas en la página Cadenas de herramientas en {{site.data.keyword.Bluemix_notm}}. ¿Qué ocurre?
{: #faq_uk}

**Pregunta completa:**

Mi proyecto de JazzHub está asociado con la región Reino Unido de {{site.data.keyword.Bluemix_notm}} según los valores del proyecto. He verificado los valores de mi proyecto yendo a su página de visión general en JazzHub, pulsando el icono **Valores**, que parece un engranaje, y pulsando **Opciones &gt; Convertir esto en un proyecto de {{site.data.keyword.Bluemix_notm}}: Región**. Una vez que haya actualizado el proyecto a la cadena de herramientas de EE.UU., se producen estos problemas:

   1. Cuando selecciono la organización estadounidense, veo un mensaje que dice que la organización no tiene un espacio en la región EE.UU. sur, y se me solicita que cree un espacio. No quiero ejecutar nada en Estados Unidos.
   
   2. Algunos de mis colegas no pueden acceder a la cadena de herramientas, aunque estaban listados como miembros en el proyecto de JazzHub original. Si intentan abrir la cadena de herramientas desde la página de visión general de la app en la región Reino Unido pulsando **Ver cadena de herramientas**, verán un mensaje "acceso denegado".
   
   3. No veo la cadena de herramientas listada en mi página Cadenas de herramientas en [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window}, aunque puedo acceder a la cadena de herramientas directamente desde la página de visión general de la app en la región Reino Unido pulsando **Ver cadena de herramientas**. Obtengo un error de que no puedo modificar la cadena de herramientas u obtengo un error de que no tengo ninguna cadena de herramientas y de que necesito crear una. 

**Respuesta:**

Estos problemas se pueden producir si procede de una organización de {{site.data.keyword.Bluemix_notm}} que no sea de EE.UU. y si no ha expandido explícitamente su organización a la región EE.UU. sur antes de actualizar. Puede confirmar este caso de ejemplo de dos formas:

   * Al abrir el URL de la cadena de herramientas, compruebe la cabecera de {{site.data.keyword.Bluemix_notm}}. Lo más probable es que vea el nombre de organización y no habrá indicado ningún espacio.
   
   * En la página Visión general de la cadena de herramientas, pulse **Gestionar**. En la página Control de acceso, pulse el enlace **Gestores de organización**. La organización que contiene la cadena de herramientas se lista en la página principal.

Lo que sucedió es que en el momento de la actualización, la organización que no es de EE.UU. no existía en EE.UU., por lo que la actualización seleccionó otra organización automáticamente buscando otra a la que tiene acceso.

Si cambia a dicha organización de {{site.data.keyword.Bluemix_notm}} de EE.UU., encontrará la cadena de herramientas. Si añade sus colegas a dicha organización, se les otorgará acceso. Esta cadena de herramientas puede seguir desplegándose en su organización no de EE.UU. El único problema es que estas dos organizaciones son distintas; no puede realizar la gestión de usuarios entre ellas automáticamente.

Si desea que la cadena de herramientas se encuentre en una organización de EE.UU. que coincida con su organización que no sea de EE.UU., siga estos pasos:

   1. Inicie sesión en [https://console.bluemix.net ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net){: new_window} y seleccione la región que no sea EE.UU. y la organización de la que proviene.
   
   2. En la cabecera {{site.data.keyword.Bluemix_notm}}, cambie a la región EE.UU. sur. Se le solicitará que cree un espacio en dicha región.
   
   3. Cree un espacio en a región EE.UU. sur para expandir su organización a esa región. 
   
   4. Suprima la cadena de herramientas que se ha creado mediante el proceso de actualización. 
   
      El repositorio Git no se suprime automáticamente. Puede que desee suprimirlo manualmente o renombrarlo por ahora. Si ya ha modificado el repositorio, puede actualizar la cadena de herramientas futura para utilizarla más adelante.
      {: tip}

   5. Vuelva al proyecto de JazzHub. Se debe restablecer a sí mismo para otro intento de actualización. Si no se restablece, póngase en contacto con hub@jazz.net y proporcione el URL del proyecto.
   
   6. Reinicie el proceso de actualización y asegúrese de seleccionar la organización correcta en EE.UU., que coincida con el nombre de la organización en la región que no sea EE.UU.
   
   7. Si mantiene o cambia el nombre del repositorio Git desde el intento de actualización de la cadena de herramientas anterior (consulte el paso 4), puede volver a configurar la tarjeta Git en su cadena de herramientas para que apunte a este URL de repositorio Git en su lugar. El cambio se reflejará automáticamente en el conducto. Para confirmar, compruebe el separador Entrada en la etapa de compilación.
