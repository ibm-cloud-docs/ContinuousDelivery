---

Copyright:
 years: 2015, 2018
lastupdated: "2018-8-2"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# {{site.data.keyword.Bluemix_notm}} DevOps
{: #devops_intro}

Para suministrar software y servicios a la velocidad que exige el mercado, es necesario que los equipos iteren y experimentar rápidamente. Deben desplegar nuevas versiones con frecuencia, con base en comentarios y datos. Los equipos de desarrollo de nube más exitosos adoptan la cultura y las prácticas modernas de DevOps, emplean arquitecturas nativas de nube y ensamblan cadenas de herramientas de las mejores herramientas para desatar su productividad. Ser capaz de realizar estas acciones rápidamente es una ventaja competitiva clave.

 
<a href="https://www.ibm.com/cloud/garage">IBM Cloud Garage Method <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo"></a> describe arquitecturas, prácticas y cadenas de herramientas de DevOps para permitir a las empresas innovar en escala transformando la cultura y el uso de las herramientas de forma eficaz y rápida.

Los desarrolladores de aplicaciones empresariales pueden empezar a compilar y desplegar aplicaciones nativas de nube en cuestión de minutos. Pueden utilizar un completo grupo de servicios para compilar aplicaciones cognitivas, de IoT, blockchain, móviles y con un uso intensivo de datos. Con IBM Cloud App Service, un solo desarrollador puede crear un proyecto, seleccionar un kit de iniciación de aplicación y desplegar una aplicación en {{site.data.keyword.Bluemix_notm}} lista para la producción. La tecnología de generación de código de la plataforma crea una aplicación de iniciación en la infraestructura y el lenguaje preferidos por el desarrollador que se adapta a sus necesidades y casos de uso. Los servicios que son necesarios para dar soporte al caso de uso, como Watson Conversation, se suministran automáticamente. Los desarrolladores pueden depurar y probar en su estación de trabajo local o en la nube, y utilizar una cadena de herramientas de DevOps para colaborar con otros usuarios y automatizar el proceso de entrega.

A medida que se unen miembros del equipo a un proyecto, se necesita un conjunto integrado de herramientas que abarquen las operaciones de desarrollo, despliegue y producción. La arquitectura Open Toolchain de IBM permite a los equipos suministrar rápidamente las mejores herramientas de DevOps de IBM y código abierto, entre otras opciones. Las integraciones entre estas herramientas se configuran automáticamente. Las cadenas de herramientas son un concepto de primera clase en la plataforma, de modo que los desarrolladores pueden organizar rápidamente todo lo que necesitan en un lugar y desarrollar la cadena a lo largo del tiempo. Las cadenas de herramientas están adoptando Identity and Access Management (IAM), inicialmente en la región del sur de Estados Unidos, para proporcionar control de acceso. IBM proporciona plantillas de cadena de herramientas que dan soporte a las mejores prácticas de Garage Method, que puede personalizar para promover patrones de cadenas de herramientas probadas en toda la empresa.

{{site.data.keyword.contdelivery_full}} proporciona un conjunto básico de herramientas para cualquier cadena de herramientas de DevOps: {{site.data.keyword.gitrepos}}, Delivery Pipeline y Eclipse Orion {{site.data.keyword.webide}}. {{site.data.keyword.gitrepos}} se basa en GitLab Community Edition, e incluye paneles de planificación y colaboración de código fuente mediante solicitudes de fusión. Delivery Pipeline orquesta los trabajos de compilación, prueba y despliegue en varios entornos a medida que los cambios pasan del desarrollo a la producción. Las aplicaciones pueden desplegarse en cuestión de en el entorno Cloud Foundry o un clúster de Kubernetes en {{site.data.keyword.Bluemix_notm}}, para nubes públicas o privadas. Eclipse Orion {{site.data.keyword.webide}} ofrece a los desarrolladores acceso rápido al código desde cualquier navegador.

La cadena de herramientas abierta integra herramientas adicionales en {{site.data.keyword.contdelivery_short}}, como Slack, Atlassian JIRA, Sonatype Nexus, JFrog Artifactory, Sauce Labs, PagerDuty, IBM Cloud Availability Monitoring, IBM Cloud Alert Notification, IBM Vulnerability Advisor e IBM Globalization Pipeline. También puede sustituir otras herramientas por las prestaciones de {{site.data.keyword.contdelivery_short}}, incluido GitHub, GitHub Enterprise y Jenkins. Los desarrolladores también pueden utilizar sus IDE y editores preferidos, como Visual Studio Code o Eclipse, entre otros.

Los repositorios de código, los sistemas de seguimiento de problemas, los sistemas de compilación y los sistemas de despliegue representan una gran cantidad de datos que pueden utilizarse para ofrecer apps de forma más eficiente y eficaz. {{site.data.keyword.DRA_full}} utiliza el análisis de Big Data para proporcionar información útil para ejecutivos, directores y desarrolladores. {{site.data.keyword.DRA_short}} agrupa y analiza los datos de la cadena de herramientas de DevOps para comunicarle los riesgos de desplegar cambios específicos, así como áreas de mejora del codebase y la productividad del equipo. Delivery Pipeline puede programar automáticamente el despliegue en un entorno basado en el riesgo de un cambio.

{{site.data.keyword.DRA_short}} solo está disponible en la región sur de Estados Unidos.
{: tip}

{{site.data.keyword.Bluemix_notm}} DevOps ofrece prácticas y arquitecturas concretas para el desarrollo en la nube, permite a los desarrolladores iniciar rápidamente nuevos proyectos que emplean el completo catálogo de servicios de {{site.data.keyword.Bluemix_notm}} y proporciona a los desarrolladores un conjunto abierto e integrado de herramientas para automatizar la entrega con rapidez y control.
