---

copyright:
  years: 2015, 2019
lastupdated: "2019-2-1"

---


{:screen: .screen}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:shortdesc: .shortdesc}

# Mit Pipelines arbeiten 
{: #pipeline-working}

Um Ihre Builds und Bereitstellungen für {{site.data.keyword.Bluemix}} zu automatisieren, verwenden Sie {{site.data.keyword.contdelivery_full}}-Pipelines.
{: shortdesc}

Bei Pipelines können Sie unter verschiedenen Buildtypen auswählen. Sie stellen das Build-Script bereit und {{site.data.keyword.contdelivery_short}} führt es aus. Es müssen keine Buildsysteme eingerichtet werden. Anschließend können Sie mit einem einzigen Mausklick Ihre App automatisch in einem oder mehreren {{site.data.keyword.Bluemix_notm}}-Bereichen, öffentlichen Cloud Foundry-Servern oder Docker-Containern im {{site.data.keyword.containerlong}} bereitstellen.

Über Build-Jobs wird Ihr App-Quellcode aus Git-Repositorys heraus kompiliert und paketiert. Bei den Build-Jobs werden bereitstellbare Artefakte wie WAR-Dateien oder Docker-Container für den {{site.data.keyword.containerlong_notm}} erstellt. Sie können außerdem innerhalb Ihres Builds automatisch Komponententests ausführen. Sie können Ihre Buildjobs so konfigurieren, dass bei jedem mit Push-Operation übertragenen Commit ein Build ausgelöst wird.

Ein Bereitstellungsjob erhält Output von einem Build-Job und stellt ihn entweder im {{site.data.keyword.containerlong_notm}} oder auf Cloud Foundry-Servern bereit, z. B. {{site.data.keyword.Bluemix_notm}}.

Es ist eine Bereitstellung für eine oder mehrere Regionen bzw. einen oder mehrere Services möglich. Sie können Ihre {{site.data.keyword.deliverypipeline}} beispielsweise so einrichten, dass sie mindestens einen Service verwendet, in einer einzigen Region getestet oder und in mehreren Regionen für die Produktion bereitgestellt wird.

##Eine Pipeline erstellen

Sie können jede der folgenden Methoden zum Erstellen einer Pipeline verwenden:

   * [Erstellen einer Toolchain aus einer vorhandenen Cloud Foundry-Anwendung](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_an_app){: new_window}. Die resultierende Toolchain enthält eine Pipeline.

   * [Erstellen einer Toolchain aus einer Vorlage](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_a_template){: new_window}, die mindestens eine Pipeline enthält.

   * [Hinzufügen der {{site.data.keyword.deliverypipeline}}-Toolintegration](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#deliverypipeline){: new_window} zu einer vorhandenen Toolchain.
   
Von {{site.data.keyword.deliverypipeline}} aus können Sie Ihre Konfiguration ändern, den Status von Builds, der bereitgestellten App und von kürzlich erfolgten Bereitstellungen überprüfen, die aktuellen Protokolle und Bereitstellungsdetails anzeigen und Ihre Pipeline löschen.
