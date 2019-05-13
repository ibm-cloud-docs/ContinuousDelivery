---

Copyright:
  years: 2015, 2019
lastupdated: "2019-03-27"

keywords: IBM Cloud Public, Use Developer Insights, US South

subcollection: ContinuousDelivery

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


# Disponibilidade, modelos e tutoriais de cadeia de ferramentas  
{: #cd_about}  

As cadeias de ferramentas estão disponíveis no {{site.data.keyword.Bluemix_notm}} Public e Dedicated. É possível usar um modelo como um ponto de início para criar uma cadeia de ferramentas.
{:shortdesc}

## Disponibilidade de cadeia de ferramentas no {{site.data.keyword.Bluemix_notm}} Public comparado ao {{site.data.keyword.Bluemix_notm}} Dedicated
{: #public_and_dedicated}

O {{site.data.keyword.Bluemix_notm}} Public é uma plataforma baseada em nuvem de padrão aberto na qual é possível construir, executar e gerenciar aplicativos que são acessados por [http://cloud.ibm.com ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://cloud.ibm.com){:new_window}. O {{site.data.keyword.Bluemix_notm}} Dedicated fornece os recursos do {{site.data.keyword.Bluemix_notm}} em um ambiente dedicado do SoftLayer que está firmemente conectado ao ambiente do {{site.data.keyword.Bluemix_notm}} Public e à sua rede. O ambiente do {{site.data.keyword.Bluemix_notm}} Dedicated de sua empresa pode não conter as mesmas integrações de ferramentas do site do {{site.data.keyword.Bluemix_notm}} Public.

Para gerenciamento de código-fonte e rastreamento de problemas, o {{site.data.keyword.Bluemix_notm}} Public geralmente usa o {{site.data.keyword.gitrepos}} (hospedado pela IBM e construído no [GitLab Community Edition ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://about.gitlab.com/){:new_window}) ou o GitHub (github.com). O {{site.data.keyword.Bluemix_notm}} Dedicated também pode usar github.com, mas geralmente usa o {{site.data.keyword.ghe_short}}, que é instalado por sua empresa ou gerenciado pela IBM.

O {{site.data.keyword.contdelivery_short}} está disponível no {{site.data.keyword.Bluemix_notm}} Public em regiões selecionadas e no {{site.data.keyword.Bluemix_notm}} Dedicated. As cadeias de ferramentas são diferentes, dependendo de se você usa o {{site.data.keyword.contdelivery_short}} no {{site.data.keyword.Bluemix_notm}} Public ou no {{site.data.keyword.Bluemix_notm}} Dedicated.

Embora as cadeias de ferramentas não estejam atualmente disponíveis em todas as regiões, é possível configurar a sua cadeia de ferramentas para implementar os seus apps em todas as regiões. Para saber mais, experimente o [tutorial Implementar um aplicativo da web seguro em diversas regiões](/docs/tutorials?topic=solution-tutorials-multi-region-webapp){: new_window}.
{: tip}

|Cadeias de ferramentas |{{site.data.keyword.Bluemix_notm}} Public	|{{site.data.keyword.Bluemix_notm}} Dedicated |
|:----------|:------------------------------|:------------------|
|Integrações de ferramenta 		|Para obter uma lista de integrações de ferramentas suportadas, veja [Configurando integrações de ferramentas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations){: new_window}. 		|As integrações de ferramentas que estão disponíveis dependem de como o {{site.data.keyword.contdelivery_short}} foi configurado em seu ambiente.			|
|Criando uma cadeia de ferramentas com base em um modelo		|Efetue login no [{{site.data.keyword.Bluemix_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://cloud.ibm.com/devops){:new_window}		|Efetue login no ambiente Dedicated no {{site.data.keyword.Bluemix_notm}}.			|
|Criando uma cadeia de ferramentas com base em um aplicativo		|O app é configurado para entrega contínua por meio de um novo repositório GitHub que é preenchido com o código de início do app.		|O app é configurado para entrega contínua por meio de um novo repositório GitHub ou GitHub Enterprise que é preenchido com o código de início do app.		|  
|Regiões de implementação do pipeline de entrega		|Todas as regiões do {{site.data.keyword.Bluemix_notm}} Public estão disponíveis para as tarefas de implementação do Cloud Foundry. 		|A região do {{site.data.keyword.Bluemix_notm}} Dedicated está disponível. Outras regiões Dedicated ou Local na mesma conta de cliente também poderão estar disponíveis, dependendo de como o {{site.data.keyword.contdelivery_short}} tiver sido configurado em seu ambiente específico.		|
|Tarefas de implementação do pipeline de entrega		|Todos os [tipos de tarefas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_jobs) estão disponíveis.		|Os tipos de tarefas que dependem de serviços do {{site.data.keyword.Bluemix_notm}} que não estão instalados no ambiente Dedicated podem não estar disponíveis.	Por exemplo, os tipos de tarefa de construção e implementação de contêiner podem não estar disponíveis em ambientes que não têm o {{site.data.keyword.containerlong_notm}}.	|
{: caption="Tabela 1. Diferenças entre cadeias de ferramentas no {{site.data.keyword.Bluemix_notm}} Dedicated e {{site.data.keyword.Bluemix_notm}} Public" caption-side="top"}


## Modelos de cadeias de ferramentas
{: #templates}

É possível usar um modelo como um ponto de início para [criar uma cadeia de ferramentas ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/devops/create){: new_window}. Os modelos de cadeia de ferramentas incluem conjuntos específicos de integrações de ferramentas que suportam as tarefas de desenvolvimento, implementação e operações.

O ambiente do {{site.data.keyword.Bluemix_notm}} Dedicated de sua empresa pode não conter os mesmos modelos de cadeia de ferramentas que o site do {{site.data.keyword.Bluemix_notm}} Public. Os modelos de cadeias de ferramentas que estão disponíveis no {{site.data.keyword.Bluemix_notm}} Public e no {{site.data.keyword.Bluemix_notm}} Dedicated podem conter um conjunto diferente de integrações de ferramentas no {{site.data.keyword.Bluemix_notm}} Dedicated.
{: note}

Alguns modelos de cadeias de ferramentas incluem integrações de ferramentas que fazem parte do serviço {{site.data.keyword.contdelivery_short}}. Se uma instância desse serviço ainda não estiver em seu grupo de recursos ou em sua organização, quando você clicar em **Criar** para criar a cadeia de ferramentas, o serviço será incluído automaticamente com o plano Lite grátis selecionado. Para obter mais informações e termos, veja o [Catálogo do {{site.data.keyword.Bluemix_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/catalog/services/continuous-delivery/){:new_window}.

A cadeia de ferramentas "Microsserviços de desenvolvimento e teste no Cloud Foundry" implementa um app com APIs de catálogo e de solicitações que são suportadas por um armazenamento do Cloudant. Como parte da implementação do app, uma instância de serviço do Cloudant gratuita é criada. Para obter mais informações e termos, veja o [Catálogo do {{site.data.keyword.Bluemix_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/catalog/services/cloudant-nosql-db/){:new_window}.

Os modelos de cadeia de ferramentas predefinidos do DevOps são exemplos recomendados que resolvem os cenários do mundo real e cada um contém um app de amostra.  É possível usar seu próprio app especificando seu repositório git ao criar a cadeia de ferramentas por meio do modelo.

<table valign="top" padding="2px">
  <caption>Tabela 2. Modelos de cadeia de ferramentas</caption>
  <tr>
    <th style="width:25%; text-align:left; vertical-align:top">Modelo e regiões disponíveis</th>
    <th style="width:50%; text-align:left; vertical-align:top">Descrição e tutoriais disponíveis</th>
    <th style="text-align:left; vertical-align:top">Ferramentas incluídas</th>
  </tr>
  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-toolchain" target="_blank">Cadeia de ferramentas "Desenvolver um app do Cloud Foundry" <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a> <br><br>

  Disponível no Sul dos EUA, no Leste dos EUA, na Alemanha, em Tóquio e no Reino Unido

  </td><td>
  Com essa cadeia de ferramentas, é possível desenvolver e implementar um app Cloud Foundry. Por padrão, essa cadeia de ferramentas usa um app de amostra "Hello world" Node.js, mas é possível se vincular a seu próprio repositório GitHub, como alternativa. A cadeia de ferramentas é pré-configurada para entrega contínua, controle de fonte, rastreamento de problemas e edição on-line.	<br><br>

  Veja o tutorial: <a href="https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain" target="_blank">Introduzir cadeias de ferramentas usando a cadeia de ferramentas "Desenvolver um app do Cloud Foundry" <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a> <br><br>
  </td><td><ul><li>
  {{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub and Issues
  </li><li>{{site.data.keyword.Bluemix_notm}}
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsecure-kube-toolchain" target="_blank">Cadeia de ferramentas "Desenvolver um app do Kubernetes" <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a> <br><br>

  Disponível no Sul dos EUA, no Leste dos EUA, na Alemanha, em Tóquio e no Reino Unido

  </td><td>
  Com essa cadeia de ferramentas, é possível desenvolver e implementar um aplicativo de forma segura em um cluster do Kubernetes gerenciado pelo {{site.data.keyword.containerlong_notm}}. Por padrão, a cadeia de ferramentas usa um app de amostra "Hello World" do Node.js, mas é possível vincular ao seu próprio repositório GitHub. Essa cadeia de ferramentas é pré-configurada para entrega contínua com o Vulnerability Advisor, controle de fonte, rastreamento de problemas e edição on-line. <br><br>
  Veja o tutorial: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-toolchain" target="_blank">Usar a cadeia de ferramentas "Desenvolver um app do Kubernetes" <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a>  
  <br><br>
  </td><td><ul><li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub and Issues
  </li><li>{{site.data.keyword.containerlong_notm}} (cluster do Kubernetes)
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-helm-toolchain" target="_blank">Cadeia de ferramentas "Desenvolver um app do Kubernetes com o Helm"
   <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a> <br><br>

  Disponível no Sul dos EUA, no Leste dos EUA, na Alemanha, em Tóquio e no Reino Unido

  </td><td>
  Com essa cadeia de ferramentas, é possível desenvolver um aplicativo Docker e seu gráfico do Helm juntos no controle de fonte e construí-lo e implementá-lo automaticamente em um cluster do Kubernetes. A cadeia de ferramentas executa testes fumaça antes da construção ou da implementação e assegura a privacidade usando um registro de contêiner privado e namespaces para o registro de contêiner e para o cluster do Kubernetes. Essa cadeia de ferramentas também usa o Vulnerability Advisor para assegurar que apenas imagens seguras sejam implementadas. <br><br>
  Experimente o tutorial: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-with-helm-toolchain" target="_blank">Usar a cadeia de ferramentas "Desenvolver um app do Kubernetes com o Helm" <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a>	 <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>Git Repos and Issue Tracking
  </li><li>{{site.data.keyword.containerlong_notm}}  (Cluster Kurbernetes) com um Gráfico de Helm
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdra-toolchain-demo" target="_blank">Cadeia de ferramentas "Desenvolver e testar um app do Cloud Foundry"
   <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a> <br><br>

  Disponível no Sul dos EUA, na Alemanha e no Reino Unido

  </td><td>
  Com essa cadeia de ferramentas nativa de nuvem, é possível usar o DevOps Insights como uma porta para a implementação de um aplicativo simples do Cloud Foundry. Por padrão, a cadeia de ferramentas usa um app de clima Node.js de amostra ou é possível vincular ao seu próprio repositório GitHub. A cadeia de ferramentas executa testes de unidade usando o Mocha e verifica a cobertura de código usando o Istambul.<br><br>
  Experimente o tutorial: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain" target="_blank">Usar a cadeia de ferramentas "Desenvolver e testar um app Cloud Foundry" <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a>  <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>Git Repos and Issue Tracking
  </li><li>{{site.data.keyword.DRA_full}}
  </li></ul>
  </td></tr>


  <tr><td>
  <a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fmicroservices-toolchain-hosted" target="_blank">
  Cadeia de ferramentas "Desenvolver e testar microsserviços no Cloud Foundry" <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a> <br><br>

  Disponível no Sul dos EUA, na Alemanha e no Reino Unido

  </td><td>
  Com essa cadeia de ferramentas de nuvem nativa, é possível usar uma amostra para criar uma loja on-line que consista em três microsserviços: uma API de Catálogo, uma API de Ordens e uma UI que chame ambas as APIs. A cadeia de ferramentas é pré-configurada para entrega contínua, controle de fonte, teste funcional, rastreamento de problemas, edição on-line e notificação de alerta. <br><br>
  Veja o tutorial: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain" target="_blank">Usar a cadeia de ferramentas "Desenvolver e testar microsserviços no Cloud Foundry" <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a><br><br>
  </td><td>
  <ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub and Issues
  </li><li>{{site.data.keyword.Bluemix_notm}}
  </li><li>{{site.data.keyword.DRA_full}}
  </li><li>PagerDuty
  </li><li>Sauce Labs
  </li><li>Slack
  </li></ul>
 </td>
</tr>

  <tr>
  <td><a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fcloud-native-toolchain-tutorial" targe="_blank">Cadeia de ferramentas
"Tutorial do Garage Method com Cloud Foundry" <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a> <br><br>

  Disponível no Sul dos EUA, no Leste dos EUA, na Alemanha, em Tóquio e no Reino Unido

</td><td>
Essa cadeia de ferramentas demonstra as práticas de DevOps apresentadas no Garage Method. A cadeia de ferramentas é pré-configurada para entrega contínua, controle de fonte, automação de teste, bem como monitoramento e operações automatizados. Ela vem com um app de amostra que é escrito em Node.js Express 4, que pode ser ampliado posteriormente. <br><br>Experimente o curso: <a href="https://www.ibm.com/cloud/garage/content/course/gm_advocate" target="_blank">Torne-se um porta-voz do Garage Method <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a>
</td><td>
<ul>
<li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion {{site.data.keyword.webide}}
</li><li>GitHub and Issues
</li><li>Google Analytics
</li><li>{{site.data.keyword.Bluemix_notm}}
</li><li>New Relic
</li><li>PagerDuty
</li><li>Sauce Labs
</li><li>Slack
</li></ul>
</td></tr>

<tr><td>
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fdevops-insights%2FDevOpsInsights_Demo_Toolchain_Template" target="_blank">Cadeia de ferramentas da "Demo de iniciação rápida do DevOps Insights" <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a> <br><br>

  Disponível no Sul dos EUA, na Alemanha e no Reino Unido

</td><td>
Com essa cadeia de ferramentas, é possível explorar o {{site.data.keyword.DRA_short}}, sem a necessidade de configuração. Para iniciar, efetue login no {{site.data.keyword.Bluemix}}. Esta demonstração contém dados de uma cadeia de ferramentas de referência e três repositórios do GitHub. Explore como organizar, testar, construir e implementar dados para todos os aplicativos, de todas as equipes, dentro do Painel de qualidade. Avalie as tendências e entenda as áreas que precisam de melhorias para que você saiba onde focar seus recursos. Revise como os membros da equipe colaboram por liberação dentro do Team Dynamics.<br><br>
Experimente o tutorial: <a href="https://www.ibm.com/cloud/garage/tutorials/explore-ibm-cloud-devops-insights" target="_blank">Explore o {{site.data.keyword.DRA_full}} <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a> <br><br>
</td><td><ul><li>
GitHub and Issues
</li><li>{{site.data.keyword.DRA_full}}
</li></ul>
</td></tr>

<tr><td>
<a href="https://cloud.ibm.com/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fempty-toolchain" target="_blank">Construir sua própria cadeia de ferramentas <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a> <br><br>

  Disponível no Sul dos EUA, no Leste dos EUA, na Alemanha, em Tóquio e no Reino Unido

</td><td>
Essa cadeia de ferramentas não possui ferramentas pré-configuradas. Se você já estiver familiarizado com as cadeias de ferramentas, será possível configurar sua própria cadeia de ferramentas. <br><br>
Veja o tutorial: <a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">Criar uma cadeia de ferramentas customizada <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a>
</td><td> &nbsp;&nbsp; Nenhum
</td></tr>

<tr><td>Cadeia de ferramentas de entrega contínua <br><br>

 Disponível no Sul dos EUA, no Leste dos EUA, na Alemanha, em Tóquio e no Reino Unido

</td><td>
Essa cadeia de ferramentas é usada ao ativar a entrega contínua para um app. <br><br>
Tente os tutoriais:

<ul><li><a href="https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app" target="_blank">Incluir uma cadeia de ferramentas em um app <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a></li>
<li><a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">Criar uma cadeia de ferramentas customizada <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a></li>
</ul></td>
<td><ul><li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion {{site.data.keyword.webide}}
</li><li>
GitHub and Issues
</li>
<li>{{site.data.keyword.Bluemix_notm}}</li></ul>
</td></tr>

<tr><td>Modelo customizado de cadeia de ferramentas <br><br>

 Disponível no Sul dos EUA, no Leste dos EUA, na Alemanha, em Tóquio e no Reino Unido

</td><td>
<br><br>
É possível criar um modelo customizado de cadeia de ferramentas que possa ser usado por outros. <br><br>

Consulte a documentação:
<a href="https://github.com/open-toolchain/sdk/wiki" target="_blank">Criando modelos customizados de cadeia de ferramentas <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a>
 <br><br>
Veja o tutorial:
<a href="https://www.ibm.com/cloud/garage/tutorials/create-a-template-for-a-custom-toolchain" target="_blank">Criar um modelo para uma cadeia de ferramentas customizada <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo"></a></td>
<td>Nenhum
</td></tr>

</table>
