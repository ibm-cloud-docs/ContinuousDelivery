---

copyright:
  years: 2015, 2017
lastupdated: "2017-8-17"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Iniciación a las cadenas de herramientas una vez que haya actualizado el proyecto de {{site.data.keyword.jazzhub_short}}
{: #toolchains_post_upgrade}

Los proyectos de {{site.data.keyword.jazzhub}} en hub.jazz.net se han actualizado a cadenas de herramientas en el servicio de {{site.data.keyword.contdelivery_short}} de IBM Bluemix. 

{{site.data.keyword.jazzhub_short}} en hub.jazz.net se ha retirado. 

Para los proyectos de DevOps, utilice el [servicio de {{site.data.keyword.contdelivery_short}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/devops){:new_window}. Si es nuevo en {{site.data.keyword.Bluemix_notm}}, asegúrese de comprobar la [visión general de Bluemix](/docs/overview/whatisbluemix.html#bluemixoverview).

{: shortdesc}

## Busque la cadena de herramientas que se ha creado desde el proyecto
{: #find_toolchain}

Confirme que la actualización se haya completado yendo a la [página de Cadenas de herramientas ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/devops/toolchains){: new_window} y verificando que ve cadenas de herramientas con nombres que coincidan con los de los proyectos de hub.jazz.net. Si se actualizan automáticamente sus proyectos, tenga en cuenta estas advertencias:
   - Si cadena de herramientas ya ha utilizado el nombre del proyecto antes de que éste se actualizara, la nueva cadena de herramientas que se ha creado para el proyecto podría no tener el nombre exacto del proyecto. 
   - Si no ve cadenas de herramientas para los proyectos, cambie a cualquier otra organización a la que pertenezca y compruebe las cadenas de herramientas allí.
   - Si todavía no puede encontrar la cadena de herramientas para uno de los proyectos, la actualización para la misma podría estar todavía en curso. Si necesita acceso inmediato a dicha cadena de herramientas, póngase en contacto con el [soporte ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}.

## Visión general de las cadenas de herramientas
{: #compare_toolchains}

Si tenía uno o varios proyectos en hub.jazz.net, se utilizaron en cadenas de herramientas en el servicio de {{site.data.keyword.contdelivery_short}}. Si no ve la cadena de herramientas para el proyecto y necesita acceso inmediato a la misma, póngase en contacto con el [soporte ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. 

Las cadenas de herramientas son como proyectos, con algunas diferencias importantes:

- Los proyectos solo pueden tener un repositorio (repo) y un conducto. Las cadenas de herramientas pueden tener tantos repositorios y conductos como sea necesario.
- Las cadenas de herramientas pueden incluir herramientas que no están disponibles en proyectos, como por ejemplo Slack, Sauce Labs, PagerDuty y {{site.data.keyword.DRA_full}}.
- En los proyectos, la pertenencia se ha mantenido a nivel de proyecto. El acceso a las cadenas de herramientas se gestiona mediante la organización (org) y la cadena de herramientas de {{site.data.keyword.Bluemix_notm}}. Para trabajar con una cadena de herramientas, debe ser un miembro de la organización que contiene la cadena de herramientas. El propietario de la cadena de herramientas tiene más control sobre quién puede acceder a la cadena de herramientas y lo que pueden hacer. Para obtener detalles, consulte el paso 2 in [Iniciación a la cadena de herramientas](#upgrade_next_steps).
- En función del tipo de repositorio que haya utilizado en el proyecto en hub.jazz.net, la cadena de herramientas puede contener un repositorio de GitHub.com o un repositorio de {{site.data.keyword.gitrepos}}.

Puede obtener más información sobre las cadenas de herramientas en [YouTube ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://youtu.be/2SIPE1e7NJ4){: new_window} o desde [Iniciación a {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery/index.html).
[![Enlace externo a YouTube](images/CD_video.png)](https://youtu.be/2SIPE1e7NJ4){: new_window}


## Iniciación a la cadena de herramientas
{: #upgrade_next_steps}

1. Asigne a los miembros del equipo acceso a la cadena de herramientas.
    - Cada miembro del equipo debe tener una cuenta de {{site.data.keyword.Bluemix_notm}} válida. Los miembros del equipo que no tienen cuentas deben [registrarse ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/registration){:new_window}.
    - Otorgue acceso a los miembros de la organización a la cadena de herramientas desde la página Gestionar de la cadena de herramientas. Los miembros del proyecto existentes se añaden como miembros de la cadena de herramientas como parte del proceso de actualización. Para obtener más información sobre el control de accesos para cadenas de herramientas, consulte [Gestión de acceso ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access){:new_window}.
    - Si un usuario no es miembro de la organización a la que pertenece la cadena de herramientas, añádalo a la organización desde la página Gestionar organizaciones.
    - Si la cadena de herramientas utiliza {{site.data.keyword.gitrepos}}, todos los miembros del proyecto de JazzHub que tengan un ID de Bluemix válido se añadirán al repositorio de {{site.data.keyword.gitrepos}} con los mismos privilegios que tenían en el proyecto de JazzHub. Si el proyecto de JazzHub incluye miembros que no tienen un ID de Bluemix válido, pueden registrarse para obtenerlo. Una vez que se registren, podrá añadirlos al repositorio.
      Para obtener más información sobre la gestión de organizaciones, consulte [Gestión de organizaciones y espacios ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/admin/orgs_spaces.html#orgsspacesusers){:new_window}.

2. Si utiliza {{site.data.keyword.gitrepos}}, debe autenticarlo mediante una señal de acceso personal o una clave SSH. Para obtener más información sobre las claves SSH, consulte [Creación de una señal de acceso o clave SSH clave para la autenticación](/docs/services/ContinuousDelivery/git_working.html#git_authentication). Para autenticar desde un cliente Git externo a través de https, siga estos pasos:
    1. Vaya a la [página Señales de acceso ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window} de los valores de usuario de {{site.data.keyword.gitrepos}}.
    2. Cree una señal de acceso personal que utilice **api** como ámbito.
    3. Vaya a la [página Cuenta ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://git.ng.bluemix.net/profile/account){:new_window} y busque su nombre de usuario correspondiente a {{site.data.keyword.gitrepos}}. El nombre de usuario aparece en la lista de la sección "Cambiar nombre de usuario" y se muestra como la primera parte del URL de cualquier repositorio personal que cree.
    4. Para autenticarse con {{site.data.keyword.gitrepos}} desde un cliente Git externo a través de HTTPS, utilice su nombre de usuario y su señal de acceso personal.
    5. Si desea reutilizar el repositorio local de su repositorio Git JazzHub, haga que el repositorio apunte al nuevo repositorio en {{site.data.keyword.gitrepos}}. Desde un shell de un terminal, cambie al directorio donde se clona el repositorio Git JazzHub. Escriba el mandato `git remote set-url`: `git remote set-url origin https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

        **Consejo:** para comprobar los URL definidos y sus nombres remotos, utilice el mandato `git remote -v`. El nombre remoto predeterminado es `origin`. Si tiene una configuración más avanzada, el formato del mandato es el siguiente: `git remote set-url <remote-name-that-uses-jazzhub-repo> https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

3. Opcional: para ver la madurez del desarrollo de un proyecto, las prácticas del equipo y la calidad del código base, añada IBM Cloud {{site.data.keyword.DRA_short}} a la cadena de herramientas. {{site.data.keyword.DRA_short}} aplica analíticas de desarrollador, de equipo y de despliegue a los proyectos DevOps. Para obtener más información, consulte [Iniciación a {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights/index.html).


## Resolución de problemas
{: #upgrade_troubleshoot}

Si encuentra problemas que están relacionados con la actualización de su proyecto, publique una pregunta en el [foro de soporte ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. En su publicación en el foro, incluya los URL del proyecto {{site.data.keyword.jazzhub_short}} y de la cadena de herramientas de {{site.data.keyword.contdelivery_short}} y marque la publicación con la etiqueta `devops-services`.


## Preguntas más frecuentes
{: #upgrade_faq}

### Mi proyecto JazzHub estaba asociado a la región del Reino Unido, pero mi cadena de herramientas está en la región EE.UU. Sur. ¿Cómo se procederá?
{: #faq_region}

Los proyectos de hub.jazz.net y de cadenas de herramientas están alojados en la región EE.UU. Sur. Si el proyecto se ha configurado para desplegar apps en otra región, por ejemplo el Reino Unido, las apps se seguirán desplegando en dicha región después de que se haya actualizado a una cadena de herramientas. Por lo tanto, nada cambia realmente con respecto a dónde se alojan los datos. En el futuro, las cadenas de herramientas estarán disponibles en más regiones.

### ¿Qué ha pasado con mis paneles de control y elementos de trabajo en Track &amp; Plan cuando realice la actualización?
{: #faq_tp}

El servicio {{site.data.keyword.contdelivery_short}} proporciona funcionalidades de seguimiento de problemas a través de {{site.data.keyword.gitrepos}}, que IBM aloja y se basa en GitLab Community Edition. {{site.data.keyword.contdelivery_short}} también da soporte a las integraciones con otras herramientas de seguimiento de problemas y planificación como, por ejemplo, GitHub Issues y JIRA.

Durante el proceso de actualización, puede elegir migrar sus elementos de Track &amp; Plan a Git Issues. Tanto GitHub Issues como {{site.data.keyword.gitrepos}} proporcionan paneles kanban y seguimiento de problemas para realizar la planificación. Para obtener más información sobre los Paneles de problemas, una característica kanban en Git Repos and Issue Tracking, consulte [Paneles de problemas ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://git.ng.bluemix.net/help/user/project/issue_board.md){: new_window}.

Si necesita la misma funcionalidad que la ofrecida por JazzHub Track &amp; Plan, ahora en desuso, hay disponible el nuevo servicio IBM Track and Plan on Cloud para comprar aparte en algunos países en base a un uso por usuario y por mes. Con este servicio en la nube, obtendrá la funcionalidad completa, equivalente a la que se ofrece para licencias de contribuidor de Rational Team Concert, en una suscripción en la nube de arrendatario único.

Este nuevo servicio IBM Track and Plan on Cloud proporciona una mayor funcionalidad que JazzHub Track &amp; Plan, ahora en desuso, dando soporte a la personalización de procesos, a jerarquías de proceso, a SAFe o a muchos otros métodos híbridos y ágiles y además ofrece la escalabilidad para crecer más allá de un proyecto individual. Se basa en la última versión de Rational Team Concert 6.0.3 y en los próximos 60 días estará en la versión 6.0.4, mientras que JazzHub Track &amp; Plan se basaba en Rational Team Concert 5.x. Es posible una migración de datos a IBM Track and Plan on Cloud a través de servicios adicionales. Puede ponerse en contacto con [Tom Hollowell ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](mailto:trhollow@us.ibm.com){:new_window}, responsable de ventas de Connected Products SaaS para obtener más información.

Para obtener información sobre IBM Track and Plan on Cloud, o para comprar en línea, visite [IBM Marketplace ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window}.

Es una opción adquirir software de automatización de compilaciones y gestión de código fuente, [Rational Team Concert on Cloud ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/us-en/marketplace/change-and-configuration-management/purchase#product-header-top){: new_window}.

### ¿Qué le ha ocurrido a mi repositorio de código después de la actualización?
{: #faq_repo}

Después de la actualización, el nuevo servicio Git será comparable al que tenía con anterioridad. Si ha utilizado github.com con el proyecto de JazzHub, su cadena de herramientas estará conectada con el mismo repositorio de GitHub. Si el proyecto JazzHub ha utilizado Git alojado en IBM, el contenido de dicho repositorio se clonará en un repositorio nuevo en {{site.data.keyword.gitrepos}}, que forma parte de {{site.data.keyword.contdelivery_short}} y está alojado por IBM.

Para obtener más información sobre cómo se trata cada tipo de repositorio en el proceso de actualización, consulte la tabla siguiente.

|Repo proyecto |Tipo de proyecto	|Repo cadena de herramientas |
|:----------|:------------------------------|:------------------|
|github.com 		|Privado o público 		|El mismo repo github.com con {{site.data.keyword.Bluemix_notm}} público.	|
|hub.jazz.net/git		|Privado o público 		|Un nuevo repositorio público o privado en {{site.data.keyword.gitrepos}} con {{site.data.keyword.Bluemix_notm}} público.	|
|Jazz SCM		|Privado o público 		|Un nuevo repositorio público o privado en {{site.data.keyword.gitrepos}} con {{site.data.keyword.Bluemix_notm}} público.	|
{: caption="Tabla 1. Repositorios de proyecto correlacionados con repositorios de cadena de herramientas" caption-side="top"}


### ¿Qué ha ocurrido a mis definiciones de compilación en mi proyecto después de la actualización?
{: #faq_build}

Si está compilando su código fuente utilizando Jazz en lugar de Delivery Pipeline, debe migrar de forma manual sus definiciones de compilación a Delivery Pipeline en su cadena de herramientas.

Si utiliza Jazz SCM como repositorio de código fuente y utiliza Delivery Pipeline para compilar su código fuente, el código fuente en Jazz SCM se moverá de forma automática a un repositorio Git. Su configuración de Delivery Pipeline permanecerá inalterada excepto que consumirá el código fuente desde el repositorio Git en lugar de hacerlo desde Jazz SCM.

### He tenido que crear una organización para mi proyecto que se ha actualizado a una cadena de herramientas, por lo que he añadido una tarjeta de crédito a mi cuenta. ¿Se realizarán cargos en mi tarjeta de crédito?
{: #faq_charges}

Como [cliente de Pago según uso ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window}, si utiliza un tiempo de ejecución, servicio o componente más allá de las concesiones gratuitas que tiene en el catálogo de Bluemix, se le realizarán cargas. Para una estimación de la utilización, consulte la [hoja de cálculos de precios ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window}. Para conocer los precios actuales para Continuous Delivery, consulte el [catálogo de Bluemix ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/catalog/services/continuous-delivery){: new_window}.

Si es un empleado de IBM, los proyectos internos de IBM se pueden facturar a los departamentos en lugar de hacerlo a su tarjeta de crédito personal. Si necesita recursos más allá de los asignados de forma gratuita a los empleados de IBM, cree una incidencia de soporte.

### No puedo encontrar o acceder a mi cadena de herramientas. ¿Qué debo hacer?
{: #faq_find}

Las cadenas de herramientas están alojadas en organizaciones de Bluemix. El proceso de actualización añade todos los miembros del proyecto de JazzHub a la cadena de herramientas. Sin embargo, a menos que el propietario de la organización Bluemix añada dichos usuarios a la organización, no podrán ver la cadena de herramientas.

Para acceder a su cadena de herramientas, vaya a Bluemix, pulse el icono de menú y pulse **Servicios &gt; DevOps**. Se abrirá la página de Cadenas de herramientas. Asegúrese de que se encuentre en la región EE.UU. Sur y de que se encuentra en la organización que contiene la cadena de herramientas. Si la cadena de herramientas no está listada en la página Cadenas de herramientas, consulte [esta entrada de preguntas más frecuentes](#faq_uk).

### Mi proyecto está asociado con la región Reino Unido. Después de la actualización, veo mensajes de error, mis colegas no pueden acceder a la cadena de herramientas, y no veo mi cadena de herramientas en la página Cadenas de herramientas en Bluemix. ¿Qué ocurre?
{: #faq_uk}

**Pregunta completa:**

Mi proyecto de JazzHub está asociado con la región Reino Unido de {{site.data.keyword.Bluemix_notm}} según los valores del proyecto. He verificado los valores de mi proyecto yendo a su página de visión general en JazzHub, pulsando el icono **Valores**, que parece un engranaje, y pulsando **Opciones &gt; Convertir esto en un proyecto de Bluemix: Región**. Una vez que haya actualizado el proyecto a la cadena de herramientas de EE.UU., se producen estos problemas:

   1. Cuando selecciono la organización estadounidense, veo un mensaje que dice que la organización no tiene un espacio en la región EE.UU. Sur, y se me solicita que cree un espacio. No quiero ejecutar nada en Estados Unidos.
   
   2. Algunos de mis colegas no pueden acceder a la cadena de herramientas, aunque estaban listados como miembros en el proyecto de JazzHub original. Si intentan abrir la cadena de herramientas desde la página de visión general de la app en la región Reino Unido pulsando **Ver cadena de herramientas**, verán un mensaje "acceso denegado".
   
   3. No veo la cadena de herramientas listada en mi página Cadenas de herramientas en [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window}, aunque puedo acceder a la cadena de herramientas directamente desde la página de visión general de la app en la región Reino Unido pulsando **Ver cadena de herramientas**. Obtengo un error de que no puedo modificar la cadena de herramientas u obtengo un error de que no tengo ninguna cadena de herramientas y de que necesito crear una. 

**Respuesta:**

Estos problemas se pueden producir si procede de una organización de {{site.data.keyword.Bluemix_notm}} que no sea de EE.UU. y si no ha expandido explícitamente su organización a la región EE.UU. Sur antes de actualizar. Puede confirmarlo de dos formas:

   - Al abrir el URL de la cadena de herramientas, compruebe la cabecera de {{site.data.keyword.Bluemix_notm}}. Probablemente, verá el nombre de organización y no habrá indicado ningún espacio.
   
   - En la página Visión general de la cadena de herramientas, pulse **Gestionar**. En la página Control de acceso, pulse el enlace **Gestores de organización**. La organización que contiene la cadena de herramientas se lista en la página principal.

Lo que sucedió es que en el momento de la actualización, la organización que no es de EE.UU. no existía en EE.UU., por lo que la actualización seleccionó otra organización automáticamente buscando otra a la que tiene acceso.

Si cambia a dicha organización de {{site.data.keyword.Bluemix_notm}} de EE.UU., encontrará la cadena de herramientas. Si añade sus colegas a dicha organización, se les otorgará acceso. Esta cadena de herramientas puede seguir desplegándose en su organización no de EE.UU. El único problema es que estas dos organizaciones son distintas; no puede realizar la gestión de usuarios entre ellas automáticamente.

Si desea que la cadena de herramientas se encuentre en una organización de EE.UU. que coincida con su organización que no sea de EE.UU., siga estos pasos:

   1. Inicie sesión en [https://console.bluemix.net ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net){: new_window} y seleccione la región que no sea EE.UU. y la organización de la que proviene.
   
   2. En la cabecera {{site.data.keyword.Bluemix_notm}}, cambie a la región EE.UU. Sur. Se le solicitará que cree un espacio en dicha región.
   
   3. Cree un espacio en a región EE.UU. Sur para expandir su organización a esa región. 
   
   4. Suprima la cadena de herramientas que se ha creado mediante el proceso de actualización. 
   
      **Nota:** El repositorio Git no se suprime automáticamente. Puede que desee suprimirlo manualmente o renombrarlo por ahora. Si ya ha realizado cambios en él, puede cambiar la cadena de herramientas futura para utilizarla más adelante.

   5. Vuelva al proyecto de JazzHub. Se debe restablecer a sí mismo para otro intento de actualización. Si no se restablece, póngase en contacto con hub@jazz.net y proporcione el URL del proyecto.
   
   6. Reinicie el proceso de actualización y asegúrese de seleccionar la organización correcta en EE.UU., que coincida con el nombre de la organización en la región que no sea EE.UU.
   
   7. Si mantiene o cambia el nombre del repositorio Git desde el intento de actualización de la cadena de herramientas anterior (consulte el paso 4), puede volver a configurar la tarjeta Git en su cadena de herramientas para que apunte a este URL de repositorio Git en su lugar. El cambio se reflejará automáticamente en el conducto. Para confirmar, compruebe el separador Entrada en la etapa de compilación.
