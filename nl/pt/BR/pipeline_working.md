---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-27"

keywords: IBM Cloud, build types, build script

subcollection: ContinuousDelivery

---


{:screen: .screen}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:shortdesc: .shortdesc}

# Trabalhando com pipelines 
{: #pipeline-working}

Para automatizar suas construções e implementações para o {{site.data.keyword.Bluemix}}, use pipelines do {{site.data.keyword.contdelivery_full}}.
{: shortdesc}

Com pipelines, é possível escolher entre diversos tipos de construção. Forneça o script de construção
e o {{site.data.keyword.contdelivery_short}} o executará; não é necessário
configurar sistemas de construção. Em seguida, com um clique, é possível implementar automaticamente o seu app em um ou muitos espaços do {{site.data.keyword.Bluemix_notm}}, servidores do Cloud Foundry públicos ou contêineres do Docker no {{site.data.keyword.containerlong}}.

Tarefas de construção compilam e compactam o código-fonte do app a partir de
repositórios Git. As tarefas de compilação produzem artefatos implementáveis, como arquivos WAR ou contêineres do Docker para o {{site.data.keyword.containerlong_notm}}. Além disso,
é possível executar testes de unidade automaticamente em sua construção. É possível configurar suas tarefas de construção para que a cada confirmação enviada por push, uma construção seja acionada.

Uma tarefa de implementação obtém a saída de uma tarefa de compilação e implementa-a no {{site.data.keyword.containerlong_notm}} ou em servidores do Cloud Foundry como o {{site.data.keyword.Bluemix_notm}}.

É possível implementar para uma ou várias regiões e serviços. Por exemplo, é
possível configurar seu {{site.data.keyword.deliverypipeline}} para usar um ou
mais serviços, testar em uma região e implementar para produção em múltiplas regiões.

##Criando um pipeline

É possível usar qualquer um dos métodos a seguir para criar um pipeline:

   * [Crie uma cadeia de ferramentas por meio de um aplicativo do Cloud Foundry existente](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_an_app){: new_window}. A cadeia de ferramentas resultante contém um pipeline.

   * [Crie uma cadeia de ferramentas por meio de um modelo](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_a_template){: new_window} que inclua pelo menos um pipeline.

   * [Inclua a integração de ferramenta do {{site.data.keyword.deliverypipeline}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#deliverypipeline){: new_window} em uma cadeia de ferramentas existente.
   
No {{site.data.keyword.deliverypipeline}}, mude a configuração, verifique o status das construções, o app implementado e as implementações recentes; veja os logs mais recentes e os detalhes da implementação ou exclua seu pipeline.
