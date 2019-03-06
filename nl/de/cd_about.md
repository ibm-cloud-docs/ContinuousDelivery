---

Copyright:
  years: 2015, 2019
lastupdated: "2019-2-5"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}


# Toolchain-Verfügbarkeit, -Vorlagen und -Lernprogramme  
{: #cd_about}  

Toolchains sind in {{site.data.keyword.Bluemix_notm}} Public und in Dedicated verfügbar. Als Ausgangspunkt zum Erstellen einer Toolchain können Sie eine Vorlage verwenden.
{:shortdesc}

## Toolchain-Verfügbarkeit auf {{site.data.keyword.Bluemix_notm}} Public im Vergleich zu {{site.data.keyword.Bluemix_notm}} Dedicated
{: #public_and_dedicated}

{{site.data.keyword.Bluemix_notm}} Public ist eine cloudbasierte Plattform mit offenen Standards, mit der Sie Anwendungen, auf die über [http://cloud.ibm.com ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://cloud.ibm.com){:new_window} zugegriffen wird, erstellen, ausführen und verwalten können. {{site.data.keyword.Bluemix_notm}} Dedicated stellt die Funktionalität von {{site.data.keyword.Bluemix_notm}} in einer dedizierten SoftLayer-Umgebung bereit, die sowohl mit der {{site.data.keyword.Bluemix_notm}} Public-Umgebung als auch mit Ihrem Netz sicher verbunden ist. Die {{site.data.keyword.Bluemix_notm}} Dedicated-Umgebung Ihres Unternehmens enthält möglicherweise nicht dieselben Toolintegrationen wie die {{site.data.keyword.Bluemix_notm}} Public-Site.

Für die Quellcodeverwaltung und Problemverfolgung verwendet {{site.data.keyword.Bluemix_notm}} Public in der Regel {{site.data.keyword.gitrepos}} (gehostet von IBM und basierend auf [GitLab Community Edition ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://about.gitlab.com/){:new_window}) oder GitHub (github.com). {{site.data.keyword.Bluemix_notm}} Dedicated ist zwar auch in der Lage, github.com zu nutzen, verwendet aber generell {{site.data.keyword.ghe_short}}, das entweder von Ihrem Unternehmen installiert oder von IBM verwaltet wird.

{{site.data.keyword.contdelivery_short}} ist auf {{site.data.keyword.Bluemix_notm}} Public in ausgewählten Regionen sowie auf {{site.data.keyword.Bluemix_notm}} Dedicated verfügbar. Die einzelnen Toolchains unterscheiden sich je nachdem, ob Sie {{site.data.keyword.contdelivery_short}} auf {{site.data.keyword.Bluemix_notm}} Public oder auf {{site.data.keyword.Bluemix_notm}} Dedicated verwenden.

Obwohl Toolchains derzeit nicht in allen Regionen verfügbar sind, können Sie Ihre Toolchain so konfigurieren, dass Ihre Apps in allen Regionen bereitgestellt werden. Einen detaillierteren Einblick vermittelt das [Lernprogramm zur Bereitstellung einer sicheren Webanwendung in mehreren Regionen](/docs/tutorials?topic=solution-tutorials-multi-region-webapp){: new_window}.
{: tip}

|Toolchains |{{site.data.keyword.Bluemix_notm}} Public	|{{site.data.keyword.Bluemix_notm}} Dedicated |
|:----------|:------------------------------|:------------------|
|Toolintegrationen 		|Eine Liste der unterstützten Toolintegrationen enthält [Toolintegrationen konfigurieren](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations){: new_window}. 		|Welche Toolintegrationen verfügbar sind, richtet sich danach, wie {{site.data.keyword.contdelivery_short}} in Ihrer Umgebung eingerichtet wurde.			|
|Toolchain aus einer Vorlage erstellen		|Melden Sie sich bei [{{site.data.keyword.Bluemix_notm}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://cloud.ibm.com/devops){:new_window} an.		|Melden Sie sich bei Ihrer dedizierten Umgebung (Dedicated) auf {{site.data.keyword.Bluemix_notm}} an.			|
|Toolchain aus einer App erstellen		|Die App wird für die kontinuierliche Bereitstellung aus einem neuen GitHub-Repository konfiguriert, das den Startcode für die App enthält.		|Die App wird für die kontinuierliche Bereitstellung aus einem neuen GitHub oder GitHub Enterprise-Repository konfiguriert, das den Startcode für die App enthält.		|  
|Delivery Pipeline-Bereitstellungsregionen		|Alle {{site.data.keyword.Bluemix_notm}} Public-Regionen stehen Cloud Foundry-Bereitstellungsjobs zur Verfügung. 		|Die {{site.data.keyword.Bluemix_notm}} Dedicated-Region ist verfügbar. Gegebenenfalls sind weitere dedizierte oder lokale Regionen innerhalb desselben Kundenkontos verfügbar, je nachdem, wie {{site.data.keyword.contdelivery_short}} für Ihre spezielle Umgebung eingerichtet wurde.		|
|Delivery Pipeline-Bereitstellungsjobs		|Es sind alle [Jobtypen](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_jobs) verfügbar.		|Jobtypen, die von {{site.data.keyword.Bluemix_notm}}-Services abhängen, die nicht in der dedizierten Umgebung installiert sind, stehen möglicherweise nicht zur Verfügung.	Beispielsweise stehen in Umgebungen, die nicht über den {{site.data.keyword.containerlong_notm}} verfügen, die Jobtypen zum Ausführen eines Container-Builds und zum Bereitstellen möglicherweise nicht zur Verfügung.	|
{: caption="Tabelle 1. Unterschiede zwischen Toolchains unter {{site.data.keyword.Bluemix_notm}} Dedicated und {{site.data.keyword.Bluemix_notm}} Public" caption-side="top"}


## Vorlagen für Toolchains
{: #templates}

Als Ausgangspunkt zum [Erstellen einer Toolchain ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/devops/create){: new_window} können Sie eine Vorlage verwenden. Toolchain-Vorlagen umfassen bestimmte Gruppen von Toolintegrationen, die Entwicklungs-, Bereitstellungs- und Systemtasks unterstützen.

Die {{site.data.keyword.Bluemix_notm}} Dedicated-Umgebung Ihres Unternehmens enthält möglicherweise nicht dieselben Toolchain-Vorlagen wie die {{site.data.keyword.Bluemix_notm}} Public-Site. Toolchain-Vorlagen, die sowohl auf {{site.data.keyword.Bluemix_notm}} Public als auch auf {{site.data.keyword.Bluemix_notm}} Dedicated verfügbar sind, enthalten möglicherweise jeweils verschiedene Gruppen von Toolintegrationen auf {{site.data.keyword.Bluemix_notm}} Dedicated.
{: note}

Manche Toolchain-Vorlagen beinhalten Toolintegrationen, die Teil des {{site.data.keyword.contdelivery_short}}-Service sind. Falls Ihre Ressourcengruppe oder Organisation nicht bereits eine Instanz dieses Service enthält, wenn Sie zum Erstellen der Toolchain auf **Erstellen** klicken, wird der Service automatisch mit dem ausgewählten kostenlosen Lite-Plan hingezufügt. Weitere Informationen und die Bedingungen enthält der [{{site.data.keyword.Bluemix_notm}}-Katalog ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/catalog/services/continuous-delivery/){:new_window}.

Die Toolchain zum Entwickeln und Testen von Microservices auf Cloud Foundry bietet eine App mit Katalog- und Bestell-APIs, die von einem Cloudant Store unterstützt werden. Im Rahmen der Bereitstellung der App wird eine kostenlose Instanz des Cloudant-Service erstellt. Weitere Informationen und die Bedingungen enthält der [{{site.data.keyword.Bluemix_notm}}-Katalog ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/catalog/services/cloudant-nosql-db/){:new_window}.

Die vordefinierten DevOps-Toolchain-Vorlagen sind empfohlene Beispiele, die reale Szenarien lösen und jeweils eine Beispiel-App enthalten.  Sie können Ihre eigene App verwenden, indem Sie Ihr Git-Repository beim Erstellen der Toolchain aus der Vorlage angeben.

<table valign="top" padding="2px">
  <caption>Tabelle 2. Toolchain-Vorlagen</caption>
  <tr>
    <th style="width:25%; text-align:left; vertical-align:top">Vorlage und verfügbare Regionen</th>
    <th style="width:50%; text-align:left; vertical-align:top">Beschreibung und verfügbare Lernprogramme</th>
    <th style="text-align:left; vertical-align:top">Eingeschlossene Tools</th>
  </tr>
  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-toolchain" target="_blank">Toolchain zum Entwickeln einer Cloud Foundry-App <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a> <br><br>

  Verfügbar in: Vereinigte Staaten (Süden), Vereinigte Staaten (Osten), Deutschland, Tokio und Vereinigtes Königreich

  </td><td>
  Mit dieser Toolchain können Sie eine Cloud Foundry-App entwickeln und bereitstellen. Standardmäßig verwendet diese Toolchain eine Node.js-Beispielapp vom Typ 'Hello World'. Sie können aber auch eine Verknüpfung zu Ihrem eigenen GitHub-Repository herstellen. Die Toolchain ist für Continuous Delivery, Quellcodeverwaltung, Problemverfolgung und Onlinebearbeitung vorkonfiguriert.	<br><br>

  Verwenden Sie das Lernprogramm: <a href="https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain" target="_blank">Einführung in Toolchains durch die Nutzung der Toolchain zum Entwickeln einer Cloud Foundry-App <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a> <br><br>
  </td><td><ul><li>
  {{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion-{{site.data.keyword.webide}}
  </li><li>GitHub Issues
  </li><li>{{site.data.keyword.Bluemix_notm}}
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsecure-kube-toolchain" target="_blank">Toolchain zum Entwickeln einer Kubernetes-App <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a> <br><br>

  Verfügbar in: Vereinigte Staaten (Süden), Vereinigte Staaten (Osten), Deutschland, Tokio und Vereinigtes Königreich

  </td><td>
  Mit dieser Toolchain können Sie eine Anwendung sicher in einem vom {{site.data.keyword.containerlong_notm}} verwalteten Kubernetes-Cluster entwickeln und bereitstellen. Standardmäßig verwendet die Toolchain eine Node.js-Beispielapp vom Typ 'Hello World'. Sie können aber auch eine Verknüpfung zu Ihrem eigenen GitHub-Repository herstellen. Die Toolchain ist für Continuous Delivery mit Vulnerability Advisor, Quellcodeverwaltung, Problemverfolgung und Onlinebearbeitung vorkonfiguriert. <br><br>
  Verwenden Sie das Lernprogramm: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-toolchain" target="_blank">Toolchain zum Entwickeln einer Kubernetes-App verwenden <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a>  
  <br><br>
  </td><td><ul><li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion-{{site.data.keyword.webide}}
  </li><li>GitHub Issues
  </li><li>{{site.data.keyword.containerlong_notm}} (Kubernetes-Cluster)
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-helm-toolchain" target="_blank">Toolchain zum Entwickeln einer Kubernetes-App mit Helm
   <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a> <br><br>

  Verfügbar in: Vereinigte Staaten (Süden), Vereinigte Staaten (Osten), Deutschland, Tokio und Vereinigtes Königreich

  </td><td>
  Mit dieser Toolchain können Sie eine Docker-Anwendung und ihr Helm-Diagramm zusammen in der Quellcodeverwaltung erstellen und automatisch in einem Kubernetes-Cluster erstellen und bereitstellen. Die Toolchain führt Smoketests vor dem Erstellen oder Bereitstellen durch und stellt den Datenschutz sicher, indem eine private Container-Registry und Namespaces für die Container-Registry und der Kubernetes-Cluster verwendet werden. Diese Toolchain verwendet außerdem Vulnerability Advisor, um sicherzustellen, dass nur sichere Images bereitgestellt werden. <br><br>
  Verwenden Sie das Lernprogramm: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-with-helm-toolchain" target="_blank">Toolchain zum Entwickeln einer Kubernetes-App mit Helm verwenden <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a>	 <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion-{{site.data.keyword.webide}}
  </li><li>Git Repos and Issue Tracking
  </li><li>{{site.data.keyword.containerlong_notm}} (Kurbernetes-Cluster) mit Helm-Diagramm
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdra-toolchain-demo" target="_blank">Toolchain zum Entwickeln und Testen einer Cloud Foundry-App
   <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a> <br><br>

  Verfügbar in den Vereinigten Staaten (Süden), in Deutschland, im Vereinigten Königreich

  </td><td>
  Mit dieser cloudnativen Toolchain können Sie DevOps Insights für die Bereitstellung einer einfachen Cloud Foundry-App über ein Gateway nutzen. Standardmäßig verwendet die Toolchain eine Node.js-Wetterapp. Sie können auch eine Verknüpfung zu Ihrem eigenen GitHub-Repository herstellen. Die Toolchain führt mit Mocha Komponententests durch und prüft die Codeabdeckung mithilfe von Istanbul.<br><br>
  Verwenden Sie das Lernprogramm: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain" target="_blank">Toolchain zum Entwickeln einer Kubernetes-App verwenden <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a>  <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion-{{site.data.keyword.webide}}
  </li><li>Git Repos and Issue Tracking
  </li><li>{{site.data.keyword.DRA_full}}
  </li></ul>
  </td></tr>


  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fmicroservices-toolchain-hosted" target="_blank">
  Toolchain zum Entwickeln und Testen von Microservices auf Cloud Foundry <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a> <br><br>

  Verfügbar in den Vereinigten Staaten (Süden), in Deutschland, im Vereinigten Königreich

  </td><td>
  Mit dieser cloudnativen Toolchain können Sie ein Beispiel verwenden, um ein Onlinegeschäft zu erstellen, das aus drei Microservices besteht: einer Katalog-API, einer Auftrags-API und einer Benutzerschnittstelle, die beide API aufruft. Die Toolchain ist für Continuous Delivery, Quellcodeverwaltung, Funktionstests, Problemverfolgung, Onlinebearbeitung und Alertbenachrichtigung vorkonfiguriert. <br><br>
  Verwenden Sie das Lernprogramm: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain" target="_blank">Toolchain zum Entwickeln und Testen von Microservices auf Cloud Foundry <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a><br><br>
  </td><td>
  <ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion-{{site.data.keyword.webide}}
  </li><li>GitHub Issues
  </li><li>{{site.data.keyword.Bluemix_notm}}
  </li><li>{{site.data.keyword.DRA_full}}
  </li><li>PagerDuty
  </li><li>Sauce Labs
  </li><li>Slack
  </li></ul>
 </td>
</tr>

  <tr>
  <td><a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fcloud-native-toolchain-tutorial" targe="_blank">
Toolchain für das Garage Method-Lernprogramm mit Cloud Foundry <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a> <br><br>

  Verfügbar in: Vereinigte Staaten (Süden), Vereinigte Staaten (Osten), Deutschland, Tokio und Vereinigtes Königreich

</td><td>
Diese Toolchain veranschaulicht die DevOps-Verfahren, die Garage Method bietet. Die Toolchain ist für Continuous Delivery, Quellcodeverwaltung, Testautomatisierung, automatisierte Überwachung und automatisierten Betrieb vorkonfiguriert. Sie wird mit einer Beispielapp bereitgestellt, die in Node.js Express 4 geschrieben ist und von Ihnen weiter erweitert werden kann. <br><br>Verwenden Sie den Kurs: <a href="https://www.ibm.com/cloud/garage/content/course/gm_advocate" target="_blank">Garage Method Advocate-Kurs <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a>.
</td><td>
<ul>
<li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion-{{site.data.keyword.webide}}
</li><li>GitHub Issues
</li><li>Google Analytics
</li><li>{{site.data.keyword.Bluemix_notm}}
</li><li>New Relic
</li><li>PagerDuty
</li><li>Sauce Labs
</li><li>Slack
</li></ul>
</td></tr>

<tr><td>
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdevopsinsights-toolchain" target="_blank">Toolchain für Deployment Risk Analytics mit GitHub und Jenkins <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a> <br><br>

  Verfügbar in Region 'US South'

</td><td>Mit dieser Toolchain können Sie sich Einblicke in Ihren Jenkins-Prozess für kontinuierliche Integration und Lieferung verschaffen. Sie können den Jenkins-Server so konfigurieren, dass er Daten an {{site.data.keyword.DRA_short}} sendet, wenn die Jobs von Jenkins ausgeführt werden. Sie können auch Qualitätsgateways implementieren, um Bereitstellungen richtlinienbasiert zu blockieren. Ergebnis können Sie im Deployment Risk-Dashboard in {{site.data.keyword.DRA_short}} anzeigen. Wenn Sie ein GitHub-Repository konfigurieren, um das Quellenrepository anzugeben, das Jenkins verwendet, so steht die Verfolgbarkeit von Änderungen zur Verfügung.  
<br><br>
Verwenden Sie das Lernprogramm: <a href="https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain" target="_blank">Qualitativ hochwertige Bereitstellungen mit der Toolchain für Deployment Risk Analytics mit GitHub und Jenkins <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a>  <br><br>
</td><td><ul><li>
GitHub Issues
</li><li>Jenkins
</li><li>{{site.data.keyword.DRA_full}}
</li><li>Slack
</li></ul>
</td></tr>

<tr><td>
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdevteaminsights-toolchain" target="_blank">Toolchain für Developer Insights und Team Dynamics mit GitHub und JIRA <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a> <br><br>

  Verfügbar in Region 'US South'

</td><td>
Mit dieser Toolchain können Sie das Entwicklungsrisiko für Ihr Projekt untersuchen und die Analyse für Social Coding nutzen, um Interaktionsmuster zwischen den Entwicklern zu verstehen. Sie können GitHub-Quellcode along Verbindung mit GitHub-Problemen, JIRA-Problemen oder beidem analysieren. Verwenden Sie Developer Insights, um diejenigen Dateien ausfindig zu machen, die hochgradig fehlerträchtig sind, und erfahren Sie, inwieweit das Projekt mit DevOps-Verfahren konform ist. Die Analyse für Social Coding in Team Dynamics ermittelt den Grad der Interaktion zwischen Teammitgliedern, sodass das Team bei unproduktiven Verfahren entsprechend korrigierend eingreifen kann.<br><br>
Verwenden Sie das Lernprogramm: <a href="https://www.ibm.com/cloud/garage/tutorials/gain-insights-developer-insights-and-team-dynamics-with-github-and-jira-toolchain" target="_blank">Einblicke erhalten mit der Toolchain für Developer Insights und Team Dynamics mit GitHub und JIRA <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a> <br><br>
</td><td><ul><li>
GitHub Issues
</li><li>{{site.data.keyword.DRA_full}}
</li><li>JIRA
</li><li>Slack
</li></ul>
</td></tr>

<tr><td>
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fempty-toolchain" target="_blank">Eigene Toolchain erstellen <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a> <br><br>

  Verfügbar in: Vereinigte Staaten (Süden), Vereinigte Staaten (Osten), Deutschland, Tokio und Vereinigtes Königreich

</td><td>
Für diese Toolchain sind keine Tools vorkonfiguriert. Wenn Sie bereits mit Toolchains vertraut sind, können Sie Ihre eigene Toolchain einrichten. <br><br>
Verwenden Sie das Lernprogramm: <a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">Eigene benutzerdefinierte Toolchain erstellen <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a>
</td><td> &nbsp;&nbsp; Keine
</td></tr>

<tr><td>Continuous Delivery-Toolchain <br><br>

 Verfügbar in: Vereinigte Staaten (Süden), Vereinigte Staaten (Osten), Deutschland, Tokio und Vereinigtes Königreich

</td><td>
Diese Toolchain wird verwendet, wenn Sie Continuous Delivery für eine App aktivieren. <br><br>
Verwenden Sie diese Lernprogramme:

<ul><li><a href="https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app" target="_blank">Toolchain zu einer App hinzufügen <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a></li>
<li><a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">Eigene benutzerdefinierte Toolchain erstellen <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a></li>
</ul></td>
<td><ul><li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion-{{site.data.keyword.webide}}
</li><li>
GitHub Issues
</li>
<li>{{site.data.keyword.Bluemix_notm}}</li></ul>
</td></tr>

<tr><td>Benutzerdefinierte Toolchain-Vorlage <br><br>

 Verfügbar in: Vereinigte Staaten (Süden), Vereinigte Staaten (Osten), Deutschland, Tokio und Vereinigtes Königreich

</td><td>
<br><br>
Sie können eine benutzerdefinierte Toolchain-Vorlage erstellen, die von anderen Benutzern verwendet werden kann. <br><br>

Siehe dazu folgende Dokumentation:
<a href="https://github.com/open-toolchain/sdk/wiki" target="_blank">Benutzerdefinierte Toolchain-Vorlagen erstellen <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a>
 <br><br>
Verwenden Sie das Lernprogramm:
<a href="https://www.ibm.com/cloud/garage/tutorials/create-a-template-for-a-custom-toolchain" target="_blank">Vorlage für eine benutzerdefinierte Toolchain erstellen <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link"></a></td>
<td>Keine
</td></tr>

</table>
