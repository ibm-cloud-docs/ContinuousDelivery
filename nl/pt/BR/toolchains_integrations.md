---

copyright:
  years: 2015, 2019
lastupdated: "2019-2-15"

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

# Configurando integrações de ferramenta
{: #integrations}

É possível configurar integrações de ferramentas que suportam tarefas de desenvolvimento, implementação e operações ao criar uma cadeia de ferramentas aberta ou é possível incluir e configurar integrações de ferramentas para customizar uma cadeia de ferramentas existente.  
{:shortdesc}

As integrações de ferramentas que estão disponíveis para incluir e configurar para a sua cadeia de ferramentas são diferentes, dependendo de você estar usando cadeias de ferramentas no {{site.data.keyword.Bluemix_notm}} Public ou no {{site.data.keyword.Bluemix_notm}} Dedicated. Se você está usando cadeias de ferramentas no {{site.data.keyword.Bluemix_notm}} Public, as
integrações de ferramentas que estão disponíveis para você dependem da região de sua cadeia de ferramentas e da
disponibilidade das integrações de ferramentas nessa região. Se estiver usando cadeias de ferramentas no {{site.data.keyword.Bluemix_notm}} Dedicated, as integrações de ferramenta disponíveis para você dependerão de como o {{site.data.keyword.contdelivery_full}} foi configurado em seu ambiente específico.

|Integração de ferramentas |Disponível no {{site.data.keyword.Bluemix_notm}} Public	|Disponível no {{site.data.keyword.Bluemix_notm}} Dedicated (ambiente dependente)|
|:----------|:------------------------------|:------------------|
|{{site.data.keyword.alertnotificationshort}}		|Sul dos EUA		|Não		|
|Artifactory		|Sul dos EUA, Leste dos EUA, Alemanha, Tóquio, Reino Unido		|Sim		|
|Availability Monitoring		|Sul dos EUA		|Não		|
|Bitbucket		|Sul dos EUA, Leste dos EUA, Alemanha, Tóquio, Reino Unido		|Não		|
|Cloud Event Management		|Sul dos EUA		|Não		|
|{{site.data.keyword.deliverypipeline}} 		|Sul dos EUA, Leste dos EUA, Alemanha, Tóquio, Reino Unido	   	|Sim  		|
|{{site.data.keyword.DRA_short}} 		|Sul dos EUA, Alemanha, Reino Unido		|Não			|
|Eclipse Orion {{site.data.keyword.webide}}		|Sul dos EUA, Leste dos EUA, Alemanha, Tóquio, Reino Unido		|Sim			|
|{{site.data.keyword.gitrepos}}	|Sul dos EUA, Leste dos EUA, Alemanha, Tóquio, Reino Unido		|Não		|
|GitHub		|Sul dos EUA, Leste dos EUA, Alemanha, Tóquio, Reino Unido		|Sim		|
|Dedicated {{site.data.keyword.ghe_short}} and Issues			|Não		|Sim		|
|GitLab		|Sul dos EUA, Leste dos EUA, Alemanha, Tóquio, Reino Unido		|Não		|
|Jenkins		|Sul dos EUA, Leste dos EUA, Alemanha, Tóquio, Reino Unido		|Sim		|
|JIRA		|Sul dos EUA, Leste dos EUA, Alemanha, Tóquio, Reino Unido		|Sim		|
|Nexus			|Sul dos EUA, Leste dos EUA, Alemanha, Tóquio, Reino Unido		|Sim		|
|Outra ferramenta			|Sul dos EUA, Leste dos EUA, Alemanha, Tóquio, Reino Unido		|Sim		|
|PagerDuty			|Sul dos EUA, Leste dos EUA, Alemanha, Tóquio, Reino Unido		|Sim		|
|Rational
Team Concert			|Sul dos EUA, Leste dos EUA, Alemanha, Tóquio, Reino Unido		|Sim		|
|Sauce Labs		|Sul dos EUA, Leste dos EUA, Alemanha, Tóquio, Reino Unido		|Não		|
|Slack			|Sul dos EUA, Leste dos EUA, Alemanha, Tóquio, Reino Unido		|Sim		|
|SonarQube			|Sul dos EUA, Leste dos EUA, Alemanha, Tóquio, Reino Unido		|Sim		|
{: caption="Tabela 1. Integrações de ferramenta disponíveis para cadeias de ferramentas no {{site.data.keyword.Bluemix_notm}} Public e Dedicated" caption-side="top"}

Se você desejar iniciar o desenvolvimento com o seu código-fonte no {{site.data.keyword.Bluemix_notm}} Public, configure a integração da ferramenta do GitHub ou a integração da ferramenta do {{site.data.keyword.gitrepos}} antes de configurar o {{site.data.keyword.deliverypipeline}}. Se você deseja começar a desenvolver com o seu código no {{site.data.keyword.Bluemix_notm}} Dedicated, configure a integração de ferramenta {{site.data.keyword.ghe_short}} ou a integração de ferramenta GitHub antes de configurar o {{site.data.keyword.deliverypipeline}}.
{: tip}


## Configurando o Alert Notification
{: #alertnotification}

O {{site.data.keyword.alertnotificationfull}} é uma solução híbrida baseada em nuvem que pode ser usada para centralizar e simplificar sua estratégia de notificação. Ele funciona com outros aplicativos baseados em nuvem e no local. Os alertas são encaminhados para o {{site.data.keyword.alertnotificationshort}} usando uma API RESTful segura.

Configure o {{site.data.keyword.alertnotificationshort}} para receber notificações sobre problemas durante o processo do DevOps.

### Pré-requisitos

1. Se você não tiver uma conta do {{site.data.keyword.alertnotificationshort}}, inscreva-se para uma:

 a. Abra a página [IBM {{site.data.keyword.alertnotificationshort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/us-en/marketplace/alert-notification){: new_window} no IBM Marketplace.

 b. Compre uma assinatura ou inscreva-se para a avaliação grátis de 90 dias.

1. Após a configuração de sua conta do {{site.data.keyword.alertnotificationshort}}, abra o [Painel Minha IBM ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://myibm.ibm.com/dashboard/){: new_window}.
1. Próximo ao IBM {{site.data.keyword.alertnotificationshort}}, clique em **Ativar**.
1. Clique em **Gerenciar chaves API** e clique em **Criar chave API**.
1. No campo **Criar chave API**, digite uma descrição.
1. Clique em **Gerar**. As novas informações da chave API, incluindo o nome e a senha, são exibidas. Essas informações serão necessárias para a configuração da integração de ferramenta, portanto, mantenha a janela Nova chave API aberta. Para propósitos de segurança, não será possível recuperar a senha da chave API mais tarde.

### Configurando o Alert Notification

1. Se você estiver configurando essa integração de ferramenta durante a criação da cadeia de ferramentas, na seção Integrações configuráveis, clique em **{{site.data.keyword.alertnotificationshort}}**.
1. Se você tiver uma cadeia de ferramentas e estiver incluindo essa integração de ferramenta nela, no painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas**. Em seguida, clique em **Visão geral**.  

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramentas, clique em **{{site.data.keyword.alertnotificationshort}}**.

1. Digite a URL para a API do {{site.data.keyword.alertnotificationshort}} que desejar usar. É possível localizar a URL na página Gerenciar chaves API do serviço {{site.data.keyword.alertnotificationshort}}; por exemplo, `https://ibmnotifybm.mybluemix.net/api/alerts/v1`.
1. Digite o nome da chave API do {{site.data.keyword.alertnotificationshort}}. É possível localizar o nome da chave API na janela Nova chave API.
1. Digite a senha gerada pelo {{site.data.keyword.alertnotificationshort}} para a chave API. É possível localizar a senha da chave API na janela Nova chave API.
1. Clique em
**Criar integração**.
1. Na cadeia de ferramentas, clique em **{{site.data.keyword.alertnotificationshort}}**.

### Saiba mais sobre Notificação de alerta

Para saber mais sobre o {{site.data.keyword.alertnotificationshort}}, consulte o artigo [IBM {{site.data.keyword.alertnotificationshort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/manage/tool_alert_notification/){: new_window} no IBM Cloud Garage Method ou execute estes tutoriais:

  * [Incluir uma integração de ferramenta em uma cadeia de ferramentas ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/add-a-tool-integration-to-a-toolchain){:new_window}

  * [Gerenciar seu aplicativo {{site.data.keyword.Bluemix_notm}} usando o {{site.data.keyword.Bluemix_notm}} Availability Monitoring e o Alert Notification ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/tutorial_gm_advocate_bam_and_an){:new_window}


## Configurando o Artifactory
{: #artifactory}

Configure o gerenciador de repositório do Artifactory para armazenar artefatos de construção no repositório (repo) Artifactory:

1. Se você estiver configurando essa integração de ferramenta durante a criação da cadeia de ferramentas, na seção Integrações configuráveis, clique em **Artifactory**.
1. Se você tiver uma cadeia de ferramentas e estiver incluindo essa integração de ferramenta nela, no painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas**. Em seguida, clique em **Visão geral**.  

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramentas, clique em **Artifactory**.

1. Digite a URL do repositório Artifactory que você deseja abrir ao clicar no cartão do Artifactory.
1. Selecione o tipo de repositório ao qual deseja se conectar.
1. Se estiver usando um registro npm do Artifactory, siga estas etapas:

 a. Digite o endereço de e-mail que está associado ao seu registro.

 b. Digite o token de autenticação que está associado ao seu registro.

 c. Digite a URL do repositório de liberação do Artifactory, que é seu registro privado no servidor Artifactory.

 d. Digite a URL para o registro de Espelho ou Público que você usa para combinar múltiplos registros npm públicos e privados. Por exemplo, essa URL pode ser a URL do registro virtual no servidor Artifactory que pode acessar seu registro privado e um cache do registro global npm.

1. Se estiver usando um repositório Maven do Artifactory, siga estas etapas:

 a. Digite o ID do usuário que está associado ao seu repositório.

 b. Digite a senha que está associada ao seu repositório.

 c. Digite a URL para seu repositório de liberação do Artifactory, que é seu repositório de liberação privada no servidor Artifactory.

 d. Digite a URL para seu repositório de captura instantânea do Artifactory, que é seu repositório de captura instantânea privada no servidor Artifactory.

 e. Digite a URL para o repositório de Espelho ou Público que você usa para combinar múltiplos repositórios Maven públicos e privados. Por exemplo, essa URL pode ser a URL do repositório virtual no servidor Artifactory que pode acessar seu repositório privado e um cache do repositório central Maven.

1. Clique em
**Criar integração**.
1. Clique no cartão do repositório do Artifactory com o qual deseja trabalhar. O website do Artifactory é aberto, no qual é possível visualizar os conteúdos do repositório.
1. Opcional: se você estiver usando uma cadeia de ferramentas no {{site.data.keyword.Bluemix_notm}} Public e desejar construir seu app usando o Artifactory com npm, configure seu pipeline para incluir uma tarefa de construção npm. Para obter instruções para configurar a tarefa de construção, veja a seção [Configurando uma tarefa de construção npm do Artifactory em seu pipeline](#config_artifactory_npm).
1. Opcional: se você estiver usando uma cadeia de ferramentas no {{site.data.keyword.Bluemix_notm}} Public e desejar construir seu app usando o Artifactory com Maven, configure seu pipeline para incluir uma tarefa de construção Maven. Para obter instruções para configurar a tarefa de construção, veja a seção [Configurando uma tarefa de construção Maven do Artifactory em seu pipeline](#config_artifactory_maven).

### Configurando uma tarefa de construção npm do Artifactory em seu pipeline
{: #config_artifactory_npm}

Antes de configurar uma tarefa de construção npm em seu pipeline, deve-se ter um pipeline de trabalho que possa usar o repositório SCM de construção como entrada. Deve-se também configurar o Artifactory para sua cadeia de ferramentas. Para obter instruções para configurar o Artifactory, veja a seção [Artifactory](#artifactory).

Configure o {{site.data.keyword.deliverypipeline}} para incluir uma tarefa de construção npm:

1. Crie um estágio e configure a entrada para o repositório SCM apropriado.
1. No estágio, inclua uma tarefa de construção.
1. Configure a tarefa de construção:
  ![tarefa de construção npm](images/artifactory_npm_job.png)

  a. Para o tipo de construtor, selecione **Construção NPM**.

  b. Se você configurou múltiplas instâncias da integração de ferramenta Artifactory, insira o nome da integração de ferramenta Artifactory para a qual deseja configurar a tarefa de construção npm.

  c. Para o tipo de integração de ferramenta, selecione **Artifactory**.

  d. Para o comando de construção, insira os comandos para construir seu módulo npm ou publicá-lo em seu registro. Este exemplo mostra os comandos para construir o módulo ou publicá-lo.
     ```
     npm install
     # or
     npm publish --registry "${NPM_RELEASE_URL}"
     ```
  É possível localizar a URL e as credenciais do usuário que você usou para se conectar ao seu registro nas definições de configuração para a integração de ferramenta Artifactory.
  {: tip}

  e. Se a sua tarefa de construção publicar no registro do Artifactory e o formato da versão do módulo do nó for `x.y.z-SNAPSHOT.w`, marque a caixa de seleção **Incrementar versão do módulo de captura instantânea**. A tarefa de construção atualiza automaticamente a versão do módulo antes de a tarefa publicar no registro do Artifactory. A tarefa seleciona a versão mais alta do módulo do registro npm e o arquivo local `package.json` e incrementa a versão do módulo usando semver. A tarefa de construção não entrega as mudanças para o repositório SCM.

1. Clique em **SALVAR**. Sempre que o pipeline for executado, essa tarefa de construção usará as informações de configuração da integração de ferramenta Artifactory para se conectar ao registro npm.

### Configurando uma tarefa de construção Maven do Artifactory em seu pipeline
{: #config_artifactory_maven}

Antes de configurar uma tarefa de construção Maven em seu pipeline, será necessário um pipeline funcional que possa usar seu repositório SCM de construção como entrada e o Artifactory deverá ser configurado para sua cadeia de ferramentas. Para obter instruções para configurar o Artifactory, veja a seção [Artifactory](#artifactory).

Configure o {{site.data.keyword.deliverypipeline}} para incluir uma tarefa de construção Maven:

1. Crie um estágio e configure a entrada para o repositório SCM apropriado.
1. No estágio, inclua uma tarefa de construção.
1. Configure a tarefa de construção:
  ![Tarefa de construção Maven](images/artifactory_maven_job.png)

  a. Para o tipo de construtor, selecione **Construção Maven**.

  b. Se você configurou múltiplas instâncias da integração de ferramenta Artifactory, insira o nome da integração de ferramenta Artifactory para a qual deseja configurar a tarefa de construção Maven.

  c. Para o tipo de integração de ferramenta, selecione **Artifactory**.

  d. Para o comando de construção, insira os comandos para construir seu módulo Maven ou publicá-lo em seu registro de captura instantânea. Este exemplo mostra os comandos para construir o módulo ou publicá-lo em um registro de captura instantânea.
     ```
     mvn -B clean package
     # or
     mvn -DaltDeploymentRepository="snapshots::default::${MAVEN_SNAPSHOT_URL}" deploy
     ```
  É possível localizar a URL e as credenciais do usuário que você usou para se conectar ao seu registro nas definições de configuração para a integração de ferramenta Artifactory.
  {: tip}

1. Clique em **SALVAR**. Sempre que o pipeline for executado, essa tarefa de construção usará as informações de configuração da integração de ferramenta Artifactory para se conectar ao repositório Maven.

### Saiba mais sobre o Artifactory

Para saber mais sobre o Artifactory, veja o [artigo Artifactory ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/deliver/tool_artifactory/){: new_window} no IBM Cloud Garage Method.


## Incluindo monitoramento de disponibilidade
{: #availabilitymonitoring}

O {{site.data.keyword.prf_hublong}} isola problemas, identifica padrões e melhora o desempenho antes que os usuários sejam afetados. É possível testar seu app em locais ao redor do mundo, integrar com pipelines de entrega e obter insights sobre como otimizar continuamente seu código.

Essa integração de ferramenta é pré-configurada e não requer nenhum parâmetro de configuração. Não é possível reconfigurar essa integração de ferramenta.
{: tip}

Para testar, monitorar e melhorar o funcionamento do app ao construí-lo, inclua a ferramenta de integração {{site.data.keyword.prf_hubshort}}:

1. No painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas na qual deseja incluir o {{site.data.keyword.prf_hubshort}}. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, em **Visão geral**.

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramentas, clique em **{{site.data.keyword.prf_hubshort}}**.

1. Clique em
**Criar integração**.
1. Clique em **{{site.data.keyword.prf_hubshort}}** para abrir o painel do {{site.data.keyword.prf_hubshort}}, selecionar um app e configurar o monitoramento para o app.

### Saiba mais sobre o Availability Monitoring

Para saber mais sobre o {{site.data.keyword.prf_hubshort}}, consulte o artigo [{{site.data.keyword.prf_hublong}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/manage/tool_bluemix_availability_monitoring/){: new_window} no IBM Cloud Garage Method ou execute este tutorial:

  * [Gerenciar seu aplicativo {{site.data.keyword.Bluemix_notm}} usando o {{site.data.keyword.Bluemix_notm}} Availability Monitoring e o Alert Notification ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/tutorial_gm_advocate_bam_and_an){:new_window}


## Configurando o Bitbucket
{: #bitbucket}

Armazene seu código-fonte em um repositório novo ou existente em bitbucket.org e participe da codificação social por meio de wikis, rastreamento de problemas e solicitações pull.

Configure o Bitbucket para colaborar no código com sua equipe:

1. No painel do DevOps, clique em **Cadeias de ferramentas**. Clique na cadeia de ferramentas na qual você deseja incluir o Bitbucket. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, em **Visão geral**.

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramentas, clique em **Bitbucket**.

   Se você está configurando essa integração de ferramenta no {{site.data.keyword.Bluemix_notm}} Public e não autorizou o {{site.data.keyword.Bluemix_notm}} a acessar o Bitbucket, clique em **Autorizar** para acessar o website do Bitbucket. Se você não tiver uma sessão ativa do Bitbucket, será solicitado a efetuar login. Clique em **Conceder acesso** para permitir que as cadeias de ferramentas do {{site.data.keyword.Bluemix_notm}} acessem as partes a seguir de sua conta do Bitbucket:
   
   * ** Leia as informações da conta **. Obtenha informações básicas sobre o usuário para preencher a interface com o usuário.
   
   * ** Leia e modifique os problemas de seus repositórios **. Permita que o {{site.data.keyword.contdelivery_short}} atualize os problemas para indicar quando o pipeline implementará confirmações que estiverem conectadas a esses problemas. 
   
   * **Leia as configurações do projeto de sua equipe e leia os repositórios que estão contidos nos projetos da sua equipe**. Permita que o {{site.data.keyword.contdelivery_short}} se integre com os repositórios que são de propriedade de equipes.
   
   * **Leia e modifique os seus repositórios e as suas solicitações pull**. Permita que o {{site.data.keyword.contdelivery_short}} envie por push o código de amostra nos repositórios, quando os usuários solicitarem o código.
   
   * ** Administrar seus repositórios **. Permita que o {{site.data.keyword.contdelivery_short}} crie novos repositórios, quando solicitados pelos usuários.
   
   * ** Leia as informações de associação da equipe **. Permita que o {{site.data.keyword.contdelivery_short}} mostre uma lista de suas equipes no menu **Proprietário** que é mostrado quando você cria um novo repositório.
   
   * **Leia e modifique os webhooks de seus repositórios**. Permita que o pipeline acione as construções quando as confirmações forem enviadas por push para um repositório.
   {: tip}
   
   Se você tiver uma sessão do Bitbucket ativa, mas não inseriu sua senha recentemente, poderá ser solicitado a inserir a senha do Bitbucket para confirmar.

1. Clique no servidor Bitbucket que você deseja usar.
1. Se você tiver um repositório do Bitbucket que deseja usar, digite a URL para o repositório. Para o tipo de repositório, clique em **Existente**.
1. Se você desejar usar um novo repositório do Bitbucket, digite um nome para o repositório, digite a URL para o repositório que você está clonando ou bifurcando e selecione o tipo de repositório:

 a. Para criar um repositório vazio, clique em **Novo**.

 b. Para criar uma cópia de um repositório, clique em **Clonar**.

 c. Para bifurcar um repositório para que seja possível contribuir com as mudanças por meio de solicitações pull, clique em **Bifurcar**.

1. Para criar um repositório privado no servidor, marque a caixa de seleção **Tornar este repositório privado**.
1. Para usar o Bitbucket Issues para rastreamento de problemas, marque a caixa de seleção **Ativar o Bitbucket Issues**.
1. Para rastrear a implementação de mudanças de código criando tags e comentários sobre confirmações e rótulos e comentários sobre problemas que são referenciados pelas confirmações, marque a caixa de seleção **Rastrear implementação de mudança de código**. Para obter mais informações, veja [Rastrear onde seu código é implementado com cadeias de ferramentas ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}.
1. Clique em
**Criar integração**.
1. Em sua cadeia de ferramentas, clique no cartão para o repositório Bitbucket com o qual você deseja trabalhar. O website do Bitbucket é aberto no qual é possível visualizar o conteúdo do repositório.
1. Se você ativou o Bitbucket Issues, clique em **Bitbucket Issues** para abri-lo. É possível usar essa instância do Bitbucket Issues para toda a sua cadeia de ferramentas, mesmo se a cadeia de ferramentas contém múltiplos repositórios do Bitbucket.    

Se você não tiver privilégios de proprietário ou de mestre para o repositório ao qual está vinculando, sua integração será limitada porque não será possível usar um webhook. Webhooks são necessários para executar automaticamente um pipeline quando uma confirmação é enviada por push para o repositório. Sem um webhook, os pipelines deverão ser iniciados manualmente.
{: tip}

### Saiba mais sobre o Bitbucket

Para saber mais sobre o Bitbucket, consulte o [Artigo do Bitbucket ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/code/tool_bitbucket/){: new_window} no IBM Cloud Garage Method.


## Incluindo o Cloud Event Management
{: #cloudeventmanagement}

O {{site.data.keyword.evtmgt_full}} fornece uma visualização consolidada de problemas que ocorrem com seus serviços, aplicativos e infraestrutura. É possível configurar o gerenciamento de incidente em tempo real para resolver os problemas de maneira mais eficiente.

Essa integração de ferramenta é pré-configurada e não requer nenhum parâmetro de configuração. Não é possível reconfigurá-la.
{: tip}

Para ajudar sua equipe do DevOps a alcançar saúde operacional confiável, qualidade de serviço e objetivos de melhoria contínua, inclua o Cloud Event Management em sua cadeia de ferramentas:

1. No painel do DevOps, clique em **Cadeias de ferramentas**. Clique na cadeia de ferramentas na qual você deseja incluir o Cloud Event Management. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, em **Visão geral**.

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramentas, clique em **Cloud Event Management**.

1. Clique em
**Criar integração**.
1. Na cadeia de ferramentas, clique em qualquer um dos cartões de ferramenta a seguir:

 * **Cloud Event Management** para começar a usar o Cloud Event Management.

 * **{{site.data.keyword.alertnotificationshort}}** para criar políticas que determinem quando os usuários receberão notificações de incidente.

 * **Runbook Automation** para gerenciar seu catálogo de runbooks no Cloud Event Management.

### Saiba mais sobre o Cloud Event Management

Para saber mais sobre o Cloud Event Management, veja o [artigo Cloud Event Management ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/manage/tool_cloud_event_mgt/){: new_window} no IBM Cloud Garage Method.


## Configurando o Delivery Pipeline
{: #deliverypipeline}

O {{site.data.keyword.deliverypipeline}} automatiza a implementação contínua de seus projetos por meio de sequências de estágios que recuperam tarefas de entrada e de execução, como construções, testes e implementações.

Configure o {{site.data.keyword.deliverypipeline}} para automatizar a construção, o teste e a implementação contínua de seus apps:

1. Se você estiver configurando essa integração de ferramenta durante a criação da cadeia de ferramentas, na seção Integrações configuráveis, clique em **{{site.data.keyword.deliverypipeline}}**. Dependendo do modelo que usar, campos diferentes poderão estar disponíveis. Revise os valores de campo padrão e, se necessário, mude essas configurações.
1. Se você tiver uma cadeia de ferramentas e estiver incluindo essa integração de ferramenta nela, no painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, em **Visão geral**.

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramentas, clique em **{{site.data.keyword.deliverypipeline}}**.

1. Especifique um nome para seu novo pipeline.
1. Se você planejar usar seu pipeline para implementar uma interface com o usuário, marque a caixa de seleção **Mostrar apps no menu VISUALIZAR APP**. Todos os apps que seu pipeline criar serão mostrados na lista **Visualizar app** na página Visão geral da cadeia de ferramentas.
1. Clique em **Criar integração** para incluir o {{site.data.keyword.deliverypipeline}} em sua cadeia de ferramentas.
1. Clique em **{{site.data.keyword.deliverypipeline}}** para visualizar o pipeline e configurá-lo. Para aprender os fundamentos da configuração de um pipeline, consulte [Construindo e implementando pipelines](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy){: new_window}.

  Se você desejar que o pipeline seja executado automaticamente quando uma confirmação for enviada por push para o seu GitHub, o {{site.data.keyword.ghe_short}} ou o repositório do Git (repositório), siga estas etapas:

   a. Configure o GitHub, {{site.data.keyword.ghe_short}} ou {{site.data.keyword.gitrepos}} para sua cadeia de ferramentas antes de definir os estágios para seu pipeline. Os estágios de pipeline precisam das URLs do Git para os seus repositórios. Cada estágio de pipeline pode se referir a somente um dos repositórios GitHub, {{site.data.keyword.ghe_short}} ou Git que estão associados à sua cadeia de ferramentas. Para obter instruções para configurar o GitHub, consulte a seção [GitHub](#github). Para obter instruções para configurar o Dedicated {{site.data.keyword.ghe_short}}, veja [Introdução ao {{site.data.keyword.ghe_long}}](/docs/services/ghededicated?topic=ghededicated-gheded_getting_started){: new_window}. Para obter instruções para configurar o {{site.data.keyword.gitrepos}}, consulte a seção [{{site.data.keyword.gitrepos}}](#gitbluemix).

   b. Use um webhook. Sem um webhook, só será possível executar pipelines manualmente. Para usar um webhook ao vincular-se a um repositório GitHub ou {{site.data.keyword.ghe_short}}, é preciso ter privilégios do administrador. Para vincular-se a um proprietário do {{site.data.keyword.gitrepos}}, é preciso ter privilégios de Principal ou Proprietário.

1. Opcional: se você estiver usando uma cadeia de ferramentas no {{site.data.keyword.Bluemix_notm}} Public e desejar que os Sauce Labs sigam testes em seu aplicativo, configure o {{site.data.keyword.deliverypipeline}} para incluir uma tarefa de teste dos Sauce Labs. Para obter instruções para configurar a tarefa de teste, consulte a seção
[Configurando uma tarefa de teste Sauce Labs em seu pipeline](#config_saucelabs).

### Configurando uma tarefa de teste Sauce Labs em seu pipeline
{: #config_saucelabs}

Antes de configurar uma tarefa de teste do Sauce Labs em seu pipeline, é necessário um pipeline de trabalho que tenha estágios para construir e implementar seu app. Deve-se também configurar o Sauce Labs para sua cadeia de ferramentas. Para obter instruções para configurar o Sauce Labs, consulte a seção [Sauce Labs](#saucelabs).

Configure o {{site.data.keyword.deliverypipeline}} para incluir uma tarefa de teste Sauce Labs:

1. Se você não tiver um estágio que implemente uma versão de teste de seu app, crie um.
1. No estágio, inclua uma tarefa de teste após a tarefa de implementação. Ao colocar essas tarefas no mesmo estágio, elas poderão acessar o mesmo conjunto de propriedades do ambiente.   
  ![Tarefa de teste](images/toolchain_test_job.png)

1. Configure o estágio. Na guia **PROPRIEDADES DO AMBIENTE**, crie a propriedade CF_APP_NAME.

  O nome do usuário e a chave de acesso dos Sauce Labs estão disponíveis no script da tarefa de teste como as variáveis de ambiente SAUCE_USERNAME e SAUCE_ACCESS_KEY. Ao escrever seus testes, deve-se usar essas variáveis de ambiente para autenticar com Sauce Labs.
  {: tip}

1. Configure a tarefa de implementação. No campo **Implementar script**, inclua esse comando: `export CF_APP_NAME="$CF_APP"`. Esse comando exporta o nome do app como uma propriedade do ambiente.
1. Configure a tarefa de teste. 

  Os campos **Instância de serviço**, **Destino**, **Organização** e **Espaço** são preenchidos com o nome do usuário, a região, a organização e o espaço dos Sauce Labs que você estiver usando.
  {: tip}

  a. Para o tipo de testador, selecione **Sauce Labs**.

  b. Para a instância de serviço, selecione o nome do usuário do Sauce Labs que você usou quando configurou o Sauce Labs para sua cadeia de ferramentas.

   Para ver o nome do usuário e a chave de acesso que você usou quando configurou os Sauce Labs para a sua cadeia de ferramentas, clique em **Configurar**.
   {: tip}

  c. No campo **Comando de execução de teste**, insira os comandos que instalam as dependências que são requeridas por seus testes e, em seguida, execute os testes. Por exemplo, para um aplicativo Node.js, você pode inserir esses comandos:
     ```
     npm install
     node_modules/grunt-cli/bin/grunt test:sauce:parallel
     ```

    d. Se você desejar ver seus relatórios de teste nos logs de tarefa de teste, marque a caixa de seleção **Ativar relatório de teste** e configure o Padrão de arquivo de resultado de teste para `teste/*.xml`.

1. Clique em **SALVAR**. Sempre que a sua pipeline for executada, os seus testes dos Sauce Labs serão executados.

### Saiba mais sobre o Delivery Pipeline

Para saber mais sobre o {{site.data.keyword.deliverypipeline}}, consulte os artigos [Trabalhando com pipelines](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-pipeline-working){: new_window} e [Delivery Pipeline ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/deliver/tool_delivery_pipeline/){: new_window} no IBM Cloud Garage Method ou execute estes tutoriais:

  * [Criar um pipeline ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/create-a-pipeline){:new_window}

  * [Criar e usar sua primeira cadeia de ferramentas usando a cadeia de ferramentas "Desenvolver um app Cloud Foundry" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}


## Incluindo o DevOps Insights
{: #dra}

{{site.data.keyword.DRA_full}} coleta e analisa os resultados dos testes de unidade, testes funcionais e ferramentas de cobertura de código para determinar se seu código atende a critérios predefinidos em gates especificados em seu processo de implementação. Se seu código não atender ou exceder os critérios, a implementação será interrompida para evitar riscos de serem liberados. É possível usar o {{site.data.keyword.DRA_short}} como uma rede de segurança para o seu ambiente de entrega contínua ou como uma forma de implementar e melhorar os padrões de qualidade.

 Essa integração de ferramenta está disponível somente no {{site.data.keyword.Bluemix_notm}} Public. Ela é pré-configurada e não requer parâmetros de configuração. Não é possível reconfigurar essa integração de ferramenta.
 {: tip}

Inclua o {{site.data.keyword.DRA_short}} para manter e melhorar a qualidade de seu código no {{site.data.keyword.Bluemix_notm}} monitorando as suas implementações para identificar riscos antes de serem liberadas.

1. Se você estiver configurando essa integração de ferramenta durante a criação da cadeia de ferramentas, na seção Integrações configuráveis, clique em **{{site.data.keyword.DRA_short}}**.
1. Se você tiver uma cadeia de ferramentas e estiver incluindo essa integração de ferramenta nela, no painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, em **Visão geral**.

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramentas, clique em **{{site.data.keyword.DRA_short}}**.

1. Clique em
**Criar integração**.
1. Clique no **{{site.data.keyword.DRA_short}}** e, em seguida, conclua as etapas de introdução: criar critérios, conectar os critérios ao pipeline e executar o pipeline.

### Saiba mais sobre o DevOps Insights

Para saber mais sobre o {{site.data.keyword.DRA_short}}, consulte o artigo [{{site.data.keyword.DRA_short}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/learn/tool_devops_insights/){: new_window} no IBM Cloud Garage Method ou execute estes tutoriais:

  * [Usar a cadeia de ferramentas "Desenvolver e testar um app Cloud Foundry" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain){:new_window}

  * [Usar a cadeia de ferramentas "Desenvolver e testar microsserviços no Cloud Foundry" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}

  * [Assegurar implementações de qualidade usando a cadeia de ferramentas "Deployment Risk Analytics com o GitHub e Jenkins" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain){:new_window}


## Incluindo o Eclipse Orion Web IDE
{: #webide}

O Eclipse Orion {{site.data.keyword.webide}} é um ambiente baseado na web integrado em que é possível criar, editar, executar, depurar e concluir tarefas de controle de fonte. É possível mover perfeitamente da edição para execução, do envio para implementação.

 Essa integração de ferramenta é pré-configurada. Ela não requer nenhum parâmetro de configuração e não é possível reconfigurá-la.
 {: tip}

Para concluir tarefas de controle de fonte, inclua a integração de ferramenta Eclipse Orion {{site.data.keyword.webide}}:

1. Se você estiver configurando essa integração de ferramenta conforme estiver criando a cadeia de ferramentas, na seção Integrações configuráveis, clique em **Eclipse Orion {{site.data.keyword.webide}}**.
1. Se você tiver uma cadeia de ferramentas e estiver incluindo essa integração de ferramenta nela, no painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, em **Visão geral**.

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramentas, clique em **Eclipse Orion {{site.data.keyword.webide}}**.

1. Clique em
**Criar integração**.
1. Clique em **Eclipse Orion {{site.data.keyword.webide}}**. A sua área de trabalho é previamente preenchida com seus repositórios GitHub ou do {{site.data.keyword.ghe_short}}. Os repos associados a sua cadeia de ferramentas atual são destacados.

### Saiba mais sobre o Eclipse Orion Web IDE

Para saber mais sobre o Eclipse Orion {{site.data.keyword.webide}}, consulte [Editando códigos com o Eclipse Orion {{site.data.keyword.webide}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide). Também é possível ler o artigo [Eclipse Orion {{site.data.keyword.webide}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/code/tool_eclipse_orion_web_ide/){: new_window} no IBM Cloud Garage Method. Siga estes tutoriais para tentar usar o Eclipse Orion {{site.data.keyword.webide}}:

  * [Criar e usar sua primeira cadeia de ferramentas usando a cadeia de ferramentas "Desenvolver um app Cloud Foundry" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}

  * [Usar a cadeia de ferramentas "Desenvolver e testar microsserviços no Cloud Foundry" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}


## Configurando o Git Repos and Issue Tracking
{: #gitbluemix}

A integração de ferramenta {{site.data.keyword.gitrepos}} baseia-se no GitLab Community Edition, que é um serviço de hospedagem baseada na web para repositórios Git. É possível ter ambas as cópias local e remota de seus repositórios. Para saber mais, veja [{{site.data.keyword.gitrepos}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/help){:new_window}.

Se você estiver configurando o {{site.data.keyword.gitrepos}} enquanto estiver criando a cadeia de ferramentas, siga estas etapas:    

1. Na seção Integrações configuráveis, clique em **Git Repos and Issue Tracking**.
1. Revise os locais de destino padrão do repositório Git. Esses repos são clonados a partir dos mesmos
repos de amostra. Se necessário, mude os nomes dos repos de destino.

Se você tiver uma cadeia de ferramentas e desejar migrar um repositório Git em sua cadeia de ferramentas para o {{site.data.keyword.gitrepos}}, siga estas etapas:

Essas instruções se aplicarão às cadeias de ferramentas que já contiverem o repositório do Git que você desejar migrar para o {{site.data.keyword.gitrepos}}. Para obter informações sobre como incluir diferentes tipos de repositórios Git em sua cadeia de ferramentas, consulte as seções [Configurando o GitHub](#github), [Configurando o GitHub Enterprise and Issues no {{site.data.keyword.Bluemix_notm}} Dedicated](#configghe) e [Configurando o GitLab](#gitlab).
{: tip}

1. No painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, em **Visão geral**.
1. Clique em **Incluir uma ferramenta**.
1. Na seção Integrações de ferramentas, clique em **Git Repos and Issue Tracking**.
1. Para criar uma cópia do repositório Git, para o tipo de repositório, clique em **Clonar**. Digite um novo nome de repositório e a URL para o repositório de origem.
1. Se desejar usar o Issues para rastreamento de problemas, marque a caixa de seleção **Ativar Issues**.
1. Se desejar rastrear as mudanças de implementação de código criando tags e comentários sobre confirmações, além de rótulos e comentários sobre problemas referenciados pelas confirmações, marque a caixa de seleção **Rastrear mudanças de implementação de código**. Para obter mais informações, veja [Rastrear onde seu código é implementado com cadeias de ferramentas ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}.
1. Clique em
**Criar integração**.

Após clonar o repositório do Git, será possível removê-lo da sua cadeia de ferramentas.
{: tip}

Se você tiver uma cadeia de ferramentas e estiver incluindo o {{site.data.keyword.gitrepos}} nela, siga estas etapas:    

1. No painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, em **Visão geral**.
1. Clique em **Incluir uma ferramenta**.
1. Na seção Integrações de ferramentas, clique em **Git Repos and Issue Tracking**.
1. Selecione um tipo de repositório:     

  a. Para criar um repositório vazio, para o tipo de repositório, clique em **Novo** e digite um nome de repositório.    
  b. Para bifurcar um repositório Git para que seja possível contribuir com as mudanças por meio de solicitações de mesclagem, para o tipo de repositório, clique em **Bifurcar**. Digite a URL para o repositório de origem.    
  c. Para criar uma cópia de um repositório Git, para o tipo de repositório, clique em **Clonar**. Digite um novo nome de repositório e a URL para o repositório de origem.     
  d. Se você tiver um repositório Git e desejar usá-lo, para o tipo de repositório, clique em **Existente**. Digite a URL.    

1. Se desejar usar o Issues para rastreamento de problemas, marque a caixa de seleção **Ativar Issues**.
1. Se desejar rastrear as mudanças de implementação de código criando tags e comentários sobre confirmações, além de rótulos e comentários sobre problemas referenciados pelas confirmações, marque a caixa de seleção **Rastrear mudanças de implementação de código**. Para obter mais informações, veja [Rastrear onde seu código é implementado com cadeias de ferramentas ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}.
1. Clique em
**Criar integração**.
1. Clique no cartão do repositório Git com o qual deseja trabalhar. Sua página de visão geral do projeto é aberta.    

Se você não tiver privilégios de Principal ou de Proprietário para o repositório ao qual você está vinculando, a sua integração será limitada porque não será possível usar um webhook. Webhooks são necessários para executar automaticamente um pipeline quando uma confirmação é enviada por push para o repositório. Sem um webhook, os pipelines deverão ser iniciados manualmente.
{: tip}

### Saiba mais sobre o Git Repos and Issue Tracking

Para saber mais sobre o {{site.data.keyword.gitrepos}}, consulte o artigo [{{site.data.keyword.gitrepos}}: codificação social hospedada pela IBM ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/code/tool_git_repos_and_issue_tracking/){: new_window} no IBM Cloud Garage Method ou execute este tutorial:

  * [Criar e usar sua primeira cadeia de ferramentas usando a cadeia de ferramentas "Desenvolver um app Cloud Foundry" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}


## Configurando o GitHub
{: #github}

O GitHub é um serviço de hospedagem baseado na web para repos Git. É possível ter ambas as cópias local e remota de
seus repos, o que
facilita a colaboração.

O {{site.data.keyword.ghe_short}} é um serviço de hospedagem no local, baseado na web para repositórios Git.

O GitHub Issues é uma ferramenta de controle que mantém seu trabalho e seus planos todos em um lugar. Ele
é integrado a seu repo de
desenvolvimento para que possa focar em tarefas importantes.

É possível configurar o GitHub como uma integração de ferramenta em sua cadeia de ferramentas para que seja possível gerenciar o código-fonte em um repositório novo ou existente em GitHub.com ou na instância do {{site.data.keyword.ghe_short}} de sua empresa. Envolva-se na codificação social por meio de wikis, rastreamento de problemas e solicitações pull.

Se estiver configurando esta integração de ferramenta conforme estiver criando a cadeia de ferramentas, siga estas etapas:

1. Se você estiver armazenando seu código-fonte em um repositório GitHub, na seção Integrações configuráveis, clique em **GitHub**. Se você está configurando essa integração de ferramenta no {{site.data.keyword.Bluemix_notm}} Public e não autorizou o {{site.data.keyword.Bluemix_notm}} a acessar o GitHub, clique em **Autorizar** para acessar o website do GitHub. Se você não tiver uma sessão do GitHub ativa, será solicitado a efetuar login. Clique em **Autorizar aplicativo** para permitir que o {{site.data.keyword.Bluemix_notm}} acesse sua conta GitHub. Se você tiver uma sessão do GitHub ativa, mas não inseriu sua senha recentemente, poderá ser solicitado a inserir sua senha do GitHub para confirmar.
1. Se você estiver usando um repositório em seu próprio servidor {{site.data.keyword.ghe_short}}, na seção Integrações configuráveis, clique em **Incluir servidor customizado**.

 A rede deve ser capaz de acessar o servidor do Git de destino por meio de um ambiente do {{site.data.keyword.Bluemix_notm}} Dedicated. Se seu servidor GitHub não está disponível na Internet pública ou o nome do host não é resolvido no Servidor de Nomes de Domínio (DNS) público, [abra um chamado de suporte](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd_support#support-ticket){: new_window}. É possível usar o chamado de suporte para enviar uma solicitação para abrir as rotas de rede ou atualizar as configurações de DNS.
 {: important}

 Digite um título para seu servidor GitHub customizado e especifique a URL raiz para o servidor. Insira seu token de acesso pessoal e, em seguida, clique em **Salvar integração customizada**.

  Se você não tiver um token de acesso pessoal, poderá criar um:

     a. Em qualquer página do GitHub, clique em seu ícone do perfil e, em seguida, clique em **Configurações**.

     b. Na barra lateral, clique em **Tokens de acesso pessoal**.

     c. Clique em **Gerar novo token**.

     d. Inclua uma descrição para o token.

     e. Marque as caixas de seleção **repositório** e **usuário** para definir o acesso para o token pessoal.

     f. Clique em **Gerar token**.

     g. Copie o token em um local seguro ou app de gerenciamento de senha. Por razões de segurança, após sair da página, você não pode mais ver o token.

1. Revise os locais de repositório de destino padrão para os repositórios GitHub. Esses repos são clonados a partir dos mesmos
repos de amostra. Se necessário, mude os nomes dos repositórios de destino.
![Locais de repositório de destino padrão](images/toolchain_github_config.png)

Se você tiver uma cadeia de ferramentas e estiver incluindo esta integração de ferramenta nela, siga essas etapas:

1. No painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, em **Visão geral**.
1. Clique em **Incluir uma ferramenta**.
1. Na seção Integrações de ferramenta, clique em **GitHub**.
1. Clique no servidor GitHub que você deseja usar.
1. Se você tiver um repositório GitHub ou {{site.data.keyword.ghe_short}} e desejar usá-lo, para o tipo de repositório, clique em **Existente** e digite a URL.
1. Se você desejar usar um novo repositório GitHub ou {{site.data.keyword.ghe_short}}, digite um nome para o repositório, digite a URL para o repositório que está sendo clonado ou bifurcado e selecione o tipo de repositório:

 a. Para criar um repositório vazio, clique em **Novo**.

 b. Para criar uma cópia de um repositório GitHub ou {{site.data.keyword.ghe_short}}, clique em **Clonar**.

 c. Para bifurcar um repositório GitHub ou {{site.data.keyword.ghe_short}} para que seja possível contribuir com as mudanças por meio de solicitações pull, clique em **Bifurcar**.

1. Se você for um usuário do GitHub.com com uma conta com upgrade ou selecionou um servidor {{site.data.keyword.ghe_short}} e desejar tornar privado um novo repositório no servidor, marque a caixa de seleção **Tornar este repositório privado**.
1. Se desejar usar o GitHub Issues para o controle de emissões, selecione a caixa de seleção **Ativar GitHub Issues**.
1. Se desejar rastrear as mudanças de implementação de código criando tags e comentários sobre confirmações, além de rótulos e comentários sobre problemas referenciados pelas confirmações, marque a caixa de seleção **Rastrear mudanças de implementação de código**. Para obter mais informações, veja [Rastrear onde seu código é implementado com cadeias de ferramentas ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}.
1. Clique em
**Criar integração**.
1. Clique no cartão para o repositório GitHub ou {{site.data.keyword.ghe_short}} que você deseja trabalhar. Dependendo do repositório selecionado, o website GitHub ou o repositório do {{site.data.keyword.ghe_short}} de sua empresa é aberto, no qual é possível visualizar os conteúdos do repositório.

  É possível usar as ferramentas de gerenciamento de código-fonte integrado no Eclipse Orion {{site.data.keyword.webide}} para editar o repositório do GitHub e implementar um app por meio de sua área de trabalho.
  {: tip}

1. Se você tiver ativado o GitHub Issues, clique em **GitHub Issues** para abri-lo. É possível usar essa instância do GitHub Issues para sua cadeia de ferramentas inteira, mesmo se a cadeia de ferramentas contém múltiplos repositórios GitHub ou {{site.data.keyword.ghe_short}}.    

Se você não tiver privilégios de administrador para o repositório ao qual está vinculando, sua integração será limitada porque não será possível usar um webhook. Webhooks são necessários para executar automaticamente um pipeline quando uma confirmação é enviada por push para o repositório. Sem um webhook, os pipelines deverão ser iniciados manualmente.
{: tip}

### Saiba mais sobre o GitHub

Para saber mais sobre o GitHub, consulte os artigos [GitHub ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/code/tool_github/){: new_window} e [GitHub Issues ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/think/tool_github_issues/){: new_window} no IBM Cloud Garage Method ou execute estes tutoriais:

 * [Usar a cadeia de ferramentas "Desenvolver e testar um app Cloud Foundry" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain){:new_window}

 * [Assegurar implementações de qualidade usando a cadeia de ferramentas "Deployment Risk Analytics com o GitHub e Jenkins" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain){:new_window}

 * [Criar uma cadeia de ferramentas customizada ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain){:new_window}


## Configurando o GitHub Enterprise and Issues no {{site.data.keyword.Bluemix_notm}} Dedicated
{: #configghe}

 Estas instruções se aplicam a  {{site.data.keyword.Bluemix_notm}}  Dedicado para  {{site.data.keyword.ghe_short}}. Se você estiver usando sua própria versão gerenciada do {{site.data.keyword.ghe_short}}, algumas etapas poderão ser diferentes, dependendo de seus procedimentos internos.
 {: important}

O {{site.data.keyword.ghe_long}} é um serviço de hospedagem no local, baseado na web para repositórios Git. O Dedicated {{site.data.keyword.ghe_short}} é para clientes {{site.data.keyword.Bluemix_notm}} Dedicated somente. O GitHub Issues é uma ferramenta de rastreamento que mantém o seu trabalho e os seus planos em um local. Ele é integrado a seu repo de desenvolvimento para que possa focar em tarefas importantes. Para obter mais informações sobre o Dedicated {{site.data.keyword.ghe_short}} e o GitHub Issues, veja [Introdução ao {{site.data.keyword.ghe_long}}](/docs/services/ghededicated?topic=ghededicated-gheded_getting_started){: new_window} e o [artigo Problemas do GitHub ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/think/tool_github_issues/){: new_window} no IBM Cloud Garage Method.

É possível configurar o {{site.data.keyword.ghe_short}} como uma integração de ferramenta em sua cadeia de ferramentas para que você possa gerenciar o código-fonte na instância do [{{site.data.keyword.Bluemix_notm}} Dedicated](/docs/dedicated?topic=dedicated-dedicated#dedicated){: new_window} de sua empresa.

1. Se estiver configurando esta integração de ferramenta conforme estiver criando a cadeia de ferramentas, siga estas etapas:

 a. Antes de efetuar login no Dedicated {{site.data.keyword.ghe_short}} pela primeira vez, peça ao administrador de região de sua empresa para incluir o seu ID do usuário em sua instância do {{site.data.keyword.Bluemix_notm}} Dedicated por meio do registro do usuário de sua empresa usando LDAP. Para obter informações sobre como configurar sua conta do {{site.data.keyword.ghe_short}}, consulte [Introdução ao {{site.data.keyword.ghe_long}}](/docs/services/ghededicated?topic=ghededicated-gheded_getting_started){: new_window}.

 b. Na seção Integrações configuráveis, clique em **{{site.data.keyword.ghe_short}}**.    

 c. Revise o nome padrão para o novo repositório {{site.data.keyword.ghe_short}}. Se necessário, mude o nome do novo repositório. A imagem a seguir mostra um exemplo de um repositório que é clonado a partir de um repositório de amostra. É possível usar um repositório existente ou um novo repositório. Para usar um novo repositório, é possível criar um repositório vazio, clonar um repositório ou bifurcar um repositório.
 ![Locais de repositório padrão](images/toolchain_ghe_config.png)

1. Se você tiver uma cadeia de ferramentas e estiver incluindo essa integração de ferramenta nela, no painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, em **Visão geral**.

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramentas, clique em **{{site.data.keyword.ghe_short}}**.

1. Se você tiver um repositório do {{site.data.keyword.ghe_short}} que deseja usar, digite a URL para o repositório. Para o tipo de repositório, clique em **Existente**.
1. Se você deseja usar um novo repositório do {{site.data.keyword.ghe_short}}, digite um nome para o repositório, digite a URL para o repositório que você está clonando ou bifurcando e
selecione o tipo de repositório:

 a. Para criar um repositório vazio, clique em **Novo**.

 b. Para criar uma cópia de um repositório, clique em **Clonar**.

 c. Para bifurcar um repositório para que seja possível contribuir com as mudanças por meio de solicitações pull, clique em **Bifurcar**.

1. Para usar o GitHub Issues para rastreamento de emissão, marque a caixa de seleção **Ativar o GitHub Issues**.
1. Clique em
**Criar integração**.
1. Clique no cartão do repositório {{site.data.keyword.ghe_short}} com o qual deseja trabalhar. O repositório {{site.data.keyword.ghe_short}} de sua empresa é aberto.

  É possível usar as ferramentas de gerenciamento de código-fonte integrado no Eclipse Orion {{site.data.keyword.webide}} para editar o repositório do {{site.data.keyword.ghe_short}} e implementar um app por meio de sua área de trabalho.
  {: tip}

1. Se você tiver ativado o GitHub Issues, clique em **GitHub Issues**. É possível usar essa instância do GitHub Issues para sua cadeia de ferramentas inteira, mesmo se a cadeia de ferramentas contiver múltiplos repositórios GitHub.    

Se você não tiver privilégios de administrador para o repositório ao qual está vinculando, sua integração será limitada porque não será possível usar um webhook. Webhooks são necessários para executar automaticamente um pipeline quando uma confirmação é enviada por push para o repositório. Sem um webhook, os pipelines deverão ser iniciados manualmente.
{: tip}


## Configurando o GitLab
{: #gitlab}

GitLab é um serviço de hospedagem baseado na web para repositórios Git. É possível ter ambas as cópias local e remota de
seus repos, o que
facilita a colaboração.

É possível configurar o GitLab como uma integração de ferramenta em sua cadeia de ferramentas para que seja possível gerenciar o código-fonte em um repositório novo ou existente em GitLab.com ou na instância do GitLab de sua empresa. Envolva-se na codificação social por meio de wikis, rastreamento de problemas e solicitações de mesclagem.

Se estiver configurando esta integração de ferramenta conforme estiver criando a cadeia de ferramentas, siga estas etapas:

1. Se você estiver armazenando seu código-fonte em um repositório GitLab, na seção Integrações configuráveis, clique em **GitLab**. Se você está configurando essa integração de ferramenta no {{site.data.keyword.Bluemix_notm}} Public e não autorizou o {{site.data.keyword.Bluemix_notm}} a acessar o GitLab, clique em **Autorizar** para acessar o website do GitLab. Se você não tiver uma sessão ativa do GitLab, será solicitado que efetue login. Clique em **Autorizar aplicativo** para permitir que o {{site.data.keyword.Bluemix_notm}} acesse sua conta do GitLab. Se você tiver uma sessão do GitLab ativa, mas não inseriu sua senha recentemente, poderá ser solicitado a inserir sua senha do GitLab para confirmar.
1. Se você estiver usando um repositório em seu próprio servidor GitLab, na seção Integrações configuráveis, clique em **Incluir servidor customizado**.

 A rede deve ser capaz de acessar o servidor do GitLab de destino por meio de um ambiente do {{site.data.keyword.Bluemix_notm}} Dedicated.
 {: tip}

 Digite um título para seu servidor GitLab customizado e especifique a URL raiz para o servidor. Insira seu token de acesso pessoal e, em seguida, clique em **Salvar integração customizada**.

  Se você não tiver um token de acesso pessoal, poderá criar um:

     a. Em qualquer página do GitLab, clique em seu ícone do perfil e, em seguida, clique em **Configurações**.

     b. Na página Tokens de acesso, digite o nome do aplicativo para o qual você deseja criar um token de acesso pessoal.

     c. Opcional. Escolha uma data de validade para o token de acesso.

     d. Marque a caixa de seleção **api** para definir o acesso para o token pessoal.

     e. Clique em **Criar token de acesso pessoal**.

     f. Copie o token em um local seguro ou app de gerenciamento de senha. Por razões de segurança, após sair da página, você não pode mais ver o token.

1. Revise os locais de repositório de destino padrão para os repositórios GitLab. Esses repos são clonados a partir dos mesmos
repos de amostra. Se necessário, mude os nomes dos repos de destino.

Se você tiver uma cadeia de ferramentas e estiver incluindo esta integração de ferramenta nela, siga essas etapas:

1. No painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, em **Visão geral**.
1. Clique em **Incluir uma ferramenta**.
1. Na seção Integrações de ferramentas, clique em **GitLab**.
1. Clique no servidor GitLab que você deseja usar.
1. Se você tiver um repositório GitLab e desejar usá-lo, para o tipo de repositório, clique em **Existente** e digite a URL.
1. Se você desejar usar um novo repositório GitLab, digite um nome para o repositório, digite a URL para o repositório que sendo clonado ou bifurcado e selecione o tipo de repositório:

 a. Para criar um repositório vazio, clique em **Novo**.

 b. Para criar uma cópia de um repositório GitLab, clique em **Clonar**.

 c. Para bifurcar um repositório GitLab para que seja possível contribuir com as mudanças por meio de solicitações de mesclagem, clique em **Bifurcar**.

1. Se você desejar criar um repositório público no servidor, limpe a caixa de seleção **Tornar este repositório privado**.
1. Se você desejar usar o Issues do GitLab para rastreamento de problemas, marque a caixa de seleção **Ativar o GitLab Issues**.
1. Se desejar rastrear as mudanças de implementação de código criando tags e comentários sobre confirmações, além de rótulos e comentários sobre problemas referenciados pelas confirmações, marque a caixa de seleção **Rastrear mudanças de implementação de código**. Para obter mais informações, veja [Rastrear onde seu código é implementado com cadeias de ferramentas ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/bluemix/2017/03/track-code-deployed-toolchains/){:new_window}.
1. Clique em
**Criar integração**.
1. Clique no cartão para o repositório GitLab com o qual você deseja trabalhar. Dependendo do repositório selecionado, o website GitLab ou o repositório GitLab de sua empresa é aberto, no qual é possível visualizar os conteúdos do repositório.

  É possível usar as ferramentas de gerenciamento de código-fonte integrado no Eclipse Orion {{site.data.keyword.webide}} para editar o repositório do GitLab e implementar um app por meio de sua área de trabalho.
  {: tip}

1. Se você ativou o GitLab Issues, clique em **GitLab Issues** para abri-lo. É possível usar essa instância do GitLab Issues para toda a sua cadeia de ferramentas, mesmo se a cadeia de ferramentas contém múltiplos repositórios GitLab.    

Se você não tiver privilégios de proprietário ou de mestre para o repositório ao qual está vinculando, sua integração será limitada porque não será possível usar um webhook. Webhooks são necessários para executar automaticamente um pipeline quando uma confirmação é enviada por push para o repositório. Sem um webhook, os pipelines deverão ser iniciados manualmente.
{: tip}

### Saiba mais sobre o GitLab

Para saber mais sobre o GitLab, veja o [artigo do GitLab ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/code/tool_gitlab/){: new_window} no IBM Cloud Garage Method.


## Configurando o Jenkins
{: #jenkins}

Jenkins é uma ferramenta de software livre baseada no servidor que constrói e testa software continuamente, apoiando as práticas de integração contínua e entrega contínua.

Antes de criar uma integração de ferramenta do Jenkins, deve-se ter um servidor do Jenkins.
{: important}

Com a integração de ferramenta Jenkins, é possível enviar notificações de tarefas do Jenkins para outras ferramentas em sua cadeia de ferramentas, como Slack e PagerDuty. Para rastrear o código em implementações, é possível incluir mensagens de implementação nas confirmações do Git e
em seus problemas Git ou JIRA relacionados. É possível também visualizar suas implementações na página Conexões da cadeia de ferramentas. É possível alimentar resultados de teste para o {{site.data.keyword.DRA_short}}, incluir portas de qualidade automatizadas e rastrear seu risco de implementação.

Configure o Jenkins para automatizar a construção, o teste e a implementação contínuos de seus apps:

1. Se você estiver configurando essa integração de ferramenta durante a criação da cadeia de ferramentas, na seção Integrações configuráveis, clique em **Jenkins**.
1. Se você tiver uma cadeia de ferramentas e estiver incluindo essa integração de ferramenta nela, no painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas**. Em seguida, clique em **Visão geral**.  

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramentas, clique em **Jenkins**.

1. Digite o nome que você deseja exibir para essa integração de ferramenta no cartão Jenkins em sua cadeia de ferramentas.
1. Digite a URL do servidor Jenkins que você deseja abrir ao clicar no cartão do Jenkins de sua cadeia de ferramentas.
1. Copie o webhook da cadeia de ferramentas gerada.
1. No servidor Jenkins, conclua estas etapas:

 a. [Instale o plug-in IBM Cloud DevOps ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://wiki.jenkins-ci.org/display/JENKINS/IBM+Cloud+DevOps+Plugin#IBMCloudDevOpsPlugin-Installingtheplugin){: new_window}.

 b. [Configure o Jenkins para notificar as cadeias de ferramentas ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://wiki.jenkins-ci.org/display/JENKINS/IBM+Cloud+DevOps+Plugin#IBMCloudDevOpsPlugin-Notifyingtoolchains){: new_window}.

 c. Retorne para a página Configurar a integração para a integração de ferramenta Jenkins.

1. Clique em
**Criar integração**.
1. Na cadeia de ferramentas, clique em **Jenkins** para visualizar o servidor Jenkins.  

### Saiba mais sobre o Jenkins

Para saber mais sobre o Jenkins, veja o [artigo Jenkins ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/deliver/tool_jenkins/){: new_window} no IBM Cloud Garage Method ou faça este tutorial:

  * [Assegurar implementações de qualidade usando a cadeia de ferramentas "Deployment Risk Analytics com o GitHub e Jenkins" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain){:new_window}

## Configurando o JIRA
{: #jira}

JIRA é uma ferramenta que rastreia problemas e erros relacionados ao software. A integração de ferramenta JIRA atualiza os problemas de seu projeto sempre que o Jenkins ou o {{site.data.keyword.deliverypipeline}} executa uma implementação. Para que a integração de ferramenta JIRA rastreie seus problemas, deve-se usar Confirmações inteligentes JIRA em suas mensagens de confirmação. Para saber mais sobre Confirmações inteligentes JIRA, veja [Usando Confirmações inteligentes ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://confluence.atlassian.com/fisheye/using-smart-commits-298976812.html){: new_window}.

Configure o JIRA para planejar, rastrear e entregar código de qualidade:

1. Se você estiver configurando essa integração de ferramenta durante a criação da cadeia de ferramentas, na seção Integrações configuráveis, clique em **JIRA**.
1. Se você tiver uma cadeia de ferramentas e estiver incluindo essa integração de ferramenta nela, no painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas**. Em seguida, clique em **Visão geral**.  

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramentas, clique em **JIRA**.

1. Se você tiver um projeto JIRA e desejar se conectar a ele, para o tipo JIRA, clique em **Existente**:

 a. Digite a chave do projeto JIRA para o projeto JIRA. É possível localizar a chave do projeto na URL do projeto JIRA.

 b. Digite a URL da API base para sua instância do JIRA. É possível localizar a URL da API do cabeçalho da instância do JIRA. Clique no ícone **Administração** e clique em **Sistema**.

 c. Se você estiver se conectando a uma instância privada do JIRA ou desejar receber informações de rastreabilidade de uma instância pública do JIRA, insira seu nome do usuário e senha do JIRA.

 d. Para controlar a implementação de mudanças de código para o projeto criando rótulos e comentários para problemas referenciados, selecione a caixa de seleção **Controlar implementação de mudanças de código**. Certifique-se de usar a Confirmação inteligente JIRA para referenciar os problemas do JIRA nas confirmações do GitHub. Se você não selecionar essa opção, a integração de ferramenta JIRA ignorará quaisquer confirmações.

1. Se desejar criar um projeto JIRA, para o tipo JIRA, clique em **Novo**:

 a. Digite uma chave de projeto JIRA para ser usada para o novo projeto. Essa chave é usada como um identificador exclusivo na URL do projeto.

 b. Digite um nome para o projeto JIRA.

 c. Digite a URL da API base para sua instância do JIRA. É possível localizar a URL da API do cabeçalho da instância do JIRA. Clique no ícone **Administração** e clique em **Sistema**.

 d. Digite o nome do usuário para o líder do projeto JIRA que você deseja usar para esse projeto. Para especificar alguém como o líder do projeto JIRA, essa pessoa deve ter a permissão de líder de projeto no JIRA.

 e. Digite o nome do usuário do administrador para essa instância do JIRA.

 f. Digite a senha do administrador para essa instância do JIRA.

 g. Para controlar a implementação de mudanças de código para o projeto criando rótulos e comentários para problemas referenciados, selecione a caixa de seleção **Controlar implementação de mudanças de código**. Certifique-se de usar a Confirmação inteligente JIRA para referenciar os problemas do JIRA nas confirmações do GitHub. Se você não selecionar essa opção, a integração de ferramenta JIRA ignorará quaisquer confirmações.

1. Clique em
**Criar integração**.
1. Em sua cadeia de ferramentas, clique em **JIRA** para visualizar o painel do projeto JIRA ao qual você se conectou.

### Saiba mais sobre o JIRA

Para saber mais sobre o JIRA, veja o [artigo JIRA ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/code/tool_jira/){: new_window} no IBM Cloud Garage Method ou faça este tutorial:

  * [Obter insights usando a cadeia de ferramentas "Developer Insights e Team Dynamics com o GitHub e o JIRA" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/gain-insights-developer-insights-and-team-dynamics-with-github-and-jira-toolchain){:new_window}


## Configurando o Nexus
{: #nexus}

Configure o Gerenciador de Repositório do Nexus para armazenar artefatos de construção no repositório (repo) Nexus:

1. Se você estiver configurando essa integração de ferramenta durante a criação da cadeia de ferramentas, na seção Integrações configuráveis, clique em **Nexus**.
1. Se você tiver uma cadeia de ferramentas e estiver incluindo essa integração de ferramenta nela, no painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas**. Em seguida, clique em **Visão geral**.  

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramentas, clique em **Nexus**.

1. Digite um nome para essa instância da integração de ferramenta Nexus.
1. Digite a URL do repositório Nexus que você deseja abrir ao clicar no cartão do Nexus de sua cadeia de ferramentas.
1. Selecione o tipo de repositório ao qual deseja se conectar.
1. Se tiver selecionado **registro npm**, siga estas etapas:

 a. Digite o endereço de e-mail que está associado ao seu registro.

 b. Digite o token de autenticação que está associado ao seu registro.

 c. Digite a URL para seu repositório de liberação Nexus, que é seu registro privado no servidor Nexus.

 d. Digite a URL para o registro de Espelho ou Público que você usa para combinar múltiplos registros npm públicos e privados. Por exemplo, essa URL pode ser a URL do registro virtual no servidor Nexus que pode acessar seu registro privado e um cache do registro global npm.

1. Se você tiver selecionado **repositório Maven**, siga estas etapas:

 a. Digite o ID do usuário que está associado ao seu repositório.

 b. Digite a senha que está associada ao seu repositório.

 c. Digite a URL para seu repositório de liberação do Nexus, que é seu repositório de liberação privada no servidor Nexus.

 d. Digite a URL para seu repositório de captura instantânea do Nexus, que é seu repositório de captura instantânea privada no servidor Nexus.

 e. Digite a URL para o repositório de Espelho ou Público que você usa para combinar múltiplos repositórios Maven públicos e privados. Por exemplo, essa URL pode ser a URL do repositório virtual no servidor Nexus que pode acessar seu repositório privado e um cache do repositório central Maven.

1. Clique em
**Criar integração**.
1. Na cadeia de ferramentas, clique no cartão do repositório Nexus com o qual deseja trabalhar. O website do Nexus é aberto, no qual é possível visualizar os conteúdos do repositório.
1. Opcional: se você estiver usando uma cadeia de ferramentas no {{site.data.keyword.Bluemix_notm}} Public e desejar construir seu app usando o Nexus com npm, configure seu pipeline para incluir uma tarefa de construção npm. Para obter instruções para configurar a tarefa de construção, veja a seção [Configurando uma tarefa de construção npm do Nexus em seu pipeline](#config_nexus_npm).
1. Opcional: se você estiver usando uma cadeia de ferramentas no {{site.data.keyword.Bluemix_notm}} Public e desejar construir seu app usando o Nexus com Maven, configure seu pipeline para incluir uma tarefa de construção Maven. Para obter instruções para configurar a tarefa de construção, veja a seção [Configurando uma tarefa de construção Maven do Nexus em seu pipeline](#config_nexus_maven).

### Configurando uma tarefa de construção npm do Nexus em seu pipeline
{: #config_nexus_npm}

Antes de configurar uma tarefa de construção npm em seu pipeline, será necessário um pipeline funcional que possa usar seu repositório SCM de construção como entrada e o Nexus deverá ser configurado para sua cadeia de ferramentas. Para obter instruções para configurar o Nexus, veja a seção [Nexus](#nexus).

Configure o {{site.data.keyword.deliverypipeline}} para incluir uma tarefa de construção npm:

1. Crie um estágio e configure a entrada para o repositório SCM apropriado.
1. No estágio, inclua uma tarefa de construção.
1. Configure a tarefa de construção:
  ![tarefa de construção npm](images/nexus_npm_job.png)

  a. Para o tipo de construtor, selecione **Construção NPM**.

  b. Se você configurou múltiplas instâncias da integração de ferramenta Nexus, insira o nome da integração de ferramenta Nexus para a qual deseja configurar a tarefa de construção npm.

  c. Para o tipo de integração de ferramenta, selecione **Nexus**.

  d. Para o comando de construção, insira os comandos para construir seu módulo npm ou publicá-lo em seu registro. Este exemplo mostra os comandos para construir o módulo ou publicá-lo.
     ```
     npm install
     # or
     npm publish --registry "${NPM_RELEASE_URL}"
     ```
  **Dica:** É possível localizar a URL e as credenciais do usuário que você usou para se conectar ao registro nas definições de configuração da integração de ferramenta Nexus.

  e. Se a sua tarefa de construção publicar no registro Nexus e o formato da versão do módulo do nó for `x.y.z-SNAPSHOT.w`, marque a caixa de seleção **Incrementar versão do módulo de captura instantânea**. A tarefa de construção atualiza automaticamente a versão do módulo antes da publicação no registro do Nexus. A tarefa de construção seleciona a versão mais alta do módulo do registro npm e o arquivo local `package.json` e incrementa a versão do módulo usando semver. A tarefa de construção não entrega as mudanças para o repositório SCM.

1. Clique em **SALVAR**. Sempre que o pipeline for executado, essa tarefa de construção usará as informações de configuração da integração de ferramenta Nexus para se conectar ao registro npm.

### Configurando uma tarefa de construção Maven do Nexus em seu pipeline
{: #config_nexus_maven}

Antes de configurar uma tarefa de construção Maven em seu pipeline, será necessário um pipeline funcional que possa usar seu repositório SCM de construção como entrada e o Nexus deverá ser configurado para sua cadeia de ferramentas. Para obter instruções para configurar o Nexus, veja a seção [Nexus](#nexus).

Configure o {{site.data.keyword.deliverypipeline}} para incluir uma tarefa de construção Maven:

1. Crie um estágio e configure a entrada para o repositório SCM apropriado.
1. No estágio, inclua uma tarefa de construção.
1. Configure a tarefa de construção:
  ![Tarefa de construção Maven](images/nexus_maven_job.png)

  a. Para o tipo de construtor, selecione **Construção Maven**.

  b. Se você configurou múltiplas instâncias da integração de ferramenta Nexus, insira o nome da integração de ferramenta Nexus para a qual deseja configurar a tarefa de construção Maven.

  c. Para o tipo de integração de ferramenta, selecione **Nexus**.

  d. Para o comando de construção, insira os comandos para construir seu módulo Maven ou publicá-lo em seu registro de captura instantânea. Este exemplo mostra os comandos para construir o módulo ou publicá-lo.
     ```
     mvn -B clean package
     # or
     mvn -DaltDeploymentRepository="snapshots::default::${MAVEN_SNAPSHOT_URL}" deploy
     ```
  É possível localizar a URL e as credenciais do usuário que você usou para se conectar ao seu registro nas definições de configuração para a integração da ferramenta do Nexus.
  {: tip}

1. Clique em **SALVAR**. Sempre que o pipeline for executado, essa tarefa de construção usará as informações de configuração da integração de ferramenta Nexus para se conectar ao repositório Maven.

### Saiba mais sobre o Nexus

Para saber mais sobre o Nexus, veja o [artigo do Nexus ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/deliver/tool_nexus/){: new_window} no IBM Cloud Garage Method.


## Configurando uma ferramenta customizada (Outra Ferramenta)
{: #othertool}

Se a sua equipe usar uma ferramenta que não está incluída na lista de integrações de cadeias de ferramentas, será possível integrar uma ferramenta customizada.

Configure uma ferramenta customizada para que ela trabalhe com outras ferramentas em sua cadeia de ferramentas e esteja disponível para a sua equipe:

1. Se você tiver uma cadeia de ferramentas e estiver incluindo essa integração de ferramenta nela, no painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, em **Visão geral**.

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramenta, clique em **Outra Ferramenta**.

1. Digite o nome da ferramenta.
1. Selecione a fase de ciclo de vida que for mais estreitamente associada à ferramenta. Essa seleção determina em qual categoria sua ferramenta está listada na página Visão geral.
1. Inclua uma URL de ícone. O ícone é mostrado no cartão da sua integração de ferramenta.
1. Inclua uma URL de documentação.
1. Especifique um nome da instância da ferramenta. Por exemplo, Minha ferramenta de equipe.
1. Inclua uma URL da instância da ferramenta. Essa URL é aberta sempre que o cartão da integração de ferramenta é clicado.
1. Inclua uma descrição da sua ferramenta.
1. (Avançado) Inclua propriedades adicionais, se necessário. Por exemplo, liste quaisquer informações ou atributos que forem necessários para integrar sua ferramenta a outras ferramentas na cadeia de ferramentas.  
1. Clique em
**Criar integração**.

### Saiba mais sobre a ferramenta customizada

Para saber mais sobre a ferramenta customizada, veja [Introduzindo a integração de ferramenta customizada para cadeias de ferramentas do {{site.data.keyword.Bluemix_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/bluemix/2016/10/custom-tool-integration-with-bluemix-toolchains/){: new_window} ou faça este tutorial:

  * [Incluir uma integração de ferramenta customizada em uma cadeia de ferramentas ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/add-a-custom-tool-integration-to-a-toolchain){:new_window}


## Configurando o PagerDuty
{: #pagerduty}

O PagerDuty integra dados de diversos sistemas de monitoramento em uma única visualização. Quando um problema ocorre, o PagerDuty
assegura que o membro da equipe que melhor se adapta para corrigi-lo no momento seja notificado. Se o membro da equipe não responder ao problema, as escaladas poderão ser configuradas para roteá-lo para os representantes secundários ou para os gerenciadores de operações.

Configure o PagerDuty para enviar notificações quando as falhas de estágio de pipeline ocorrerem para que você possa corrigir problemas mais rapidamente e reduzir o tempo de inatividade:

1. Se você estiver configurando esta integração de ferramenta conforme estiver criando a cadeia de ferramentas, na seção Integrações configuráveis, clique em **PagerDuty**.
1. Se você tiver uma cadeia de ferramentas e estiver incluindo essa integração de ferramenta nela, no painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, em **Visão geral**.

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramentas, clique em **PagerDuty**.

1. Se você deseja integrar o PagerDuty no nível de conta usando uma chave API, clique em **Conta**:

 a. Digite a chave de acesso API para sua conta PagerDuty. Se você não tiver uma conta do PagerDuty, [registre-se para uma ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://signup.pagerduty.com/accounts/new){: new_window}. Para obter instruções para localizar a chave, veja [Gerando uma chave API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://support.pagerduty.com/hc/en-us/articles/202829310-Generating-an-API-Key){: new_window}.

 b. Digite o nome de seu serviço PagerDuty.

 c. Digite o endereço de e-mail para o contato PagerDuty primário.

 d. Digite o número do telefone para o contato PagerDuty primário.

1. Se você deseja integrar o PagerDuty no nível de serviço usando uma chave de integração, clique em **Serviço**:

 a. Digite a URL para o serviço PagerDuty no qual você deseja postar alertas.

 b. Digite sua chave de integração do PagerDuty. É possível localizar sua chave ou criar uma chave na seção Integrações de sua página de serviço PagerDuty.

1. Clique em
**Criar integração**.
1. Clique em **PagerDuty** para acessar pagerduty.com. É possível visualizar os eventos associados ao serviço PagerDuty
que você especificou quando configurou esta integração de ferramenta para sua cadeia de ferramentas.

### Saiba mais sobre o PagerDuty

Para saber mais sobre o PagerDuty, veja o [artigo do PagerDuty ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/manage/tool_pagerduty/){: new_window} no IBM Cloud Garage Method ou faça este tutorial e o curso de advogado do Garage Method:

  * [Usar a cadeia de ferramentas "Desenvolver e testar microsserviços no Cloud Foundry" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}

  * [Tornar-se um porta-voz do Garage Method ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/course/gm_advocate/){:new_window}


## Configurando o Rational Team Concert
{: #rationalteamconcert}

IBM Rational Team Concert&trade; é uma ferramenta de colaboração em equipe que integra tarefas de desenvolvimento, incluindo planejamento de iteração, gerenciamento de mudanças, rastreamento de defeito, controle de fonte, automação de construção e relatório.

Configure o Rational Team Concert para praticar uma abordagem DevOps e entrega contínua em seu ambiente de desenvolvimento:

1. Se você estiver configurando essa integração de ferramenta enquanto estiver criando a cadeia de ferramentas, na seção Integrações configuráveis, clique em **Rational Team Concert**.
1. Se você tiver uma cadeia de ferramentas e estiver incluindo essa integração de ferramenta nela, no painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas**. Em seguida, clique em **Visão geral**.  

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramentas, clique em **Rational Team Concert**.

1. Digite a URL para o servidor Rational Team Concert que você deseja abrir ao clicar no cartão Rational Team Concert de sua cadeia de ferramentas.
1. Digite o ID do usuário que você usa para acessar o servidor Rational Team Concert.
1. Digite a senha que você usa para acessar o servidor Rational Team Concert.
1. Se você tiver uma área do projeto Rational Team Concert que deseja incluir em sua cadeia de ferramentas, siga estas etapas:

 a. Na lista **Tipo de área do projeto**, selecione **Área do projeto existente**.

 b. Digite o nome da área do projeto para incluir em sua cadeia de ferramentas.

1. Se você desejar criar uma área do projeto do Rational Team Concert para incluir em sua cadeia de ferramentas, siga estas etapas:

 a. Na lista **Tipo de área do projeto**, selecione **Nova área do projeto**.

 b. Digite um nome para a nova área do projeto para incluir em sua cadeia de ferramentas.

 c. Digite o nome do modelo de processo do Rational Team Concert a ser usado para criar o projeto.

1. Para rastrear a implementação de mudanças código para o projeto criando tags e comentários sobre itens de trabalho, selecione a caixa de seleção **Rastrear implementação de mudanças de código**.
1. Clique em
**Criar integração**.
1. Em sua cadeia de ferramentas, clique em **Rational Team Concert** para abrir o painel do Rational Team Concert que você configurou.

### Saiba mais sobre o Rational Team Concert

Para saber mais sobre o Rational Team Concert, veja o [artigo IBM Rational Team Concert ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/think/tool_rtc/){: new_window} no IBM Cloud Garage Method.


## Configurando o Sauce Labs
{: #saucelabs}

O Sauce Labs executa testes de unidade funcional. Quando o suíte de testes do Sauce Labs é configurado como uma tarefa de teste no {{site.data.keyword.deliverypipeline}}, o suíte de testes pode executar testes em relação a seu app da web ou móvel como parte de seu processo de entrega contínua. Esses testes podem fornecer um controle de fluxo valioso para seus projetos, atuando como gates para impedir a implementação de um código ruim.

 Essa integração de ferramenta está disponível somente no {{site.data.keyword.Bluemix_notm}} Public.
 {: tip}

Configure o Sauce Labs para executar testes funcionais automatizados em múltiplos sistemas operacionais e navegadores para que possa emular a
forma que um usuário pode usar um website ou um aplicativo:

1. Se você estiver configurando esta integração de ferramenta conforme estiver criando a cadeia de ferramentas, na seção Integrações configuráveis, clique em **Sauce Labs**.
1. Se você tiver uma cadeia de ferramentas e estiver incluindo essa integração de ferramenta nela, no painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, em **Visão geral**.

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramenta, clique em **Sauce Labs**.

1. Digite o nome de usuário associado à sua conta Sauce Labs. É possível [localizar seu nome do usuário na mensagem de boas-vindas na página de conta do Sauce Labs ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://saucelabs.com/account){: new_window}.
1. Digite a chave de acesso para sua conta Sauce Labs. É possível [localizar a chave na página da sua conta Sauce Labs ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://saucelabs.com/account){: new_window}.
1. Clique em
**Criar integração**.
1. Clique em **Sauce Labs** para acessar saucelabs.com e visualizar a atividade de teste da cadeia de ferramentas.

 Se você incluiu uma tarefa de teste dos Sauce Labs para o {{site.data.keyword.deliverypipeline}}, é possível selecionar a instância de serviço. Para obter instruções para configurar uma tarefa de teste em seu pipeline, veja a seção [Configurando uma tarefa de teste do Sauce Labs em seu pipeline](#config_saucelabs).
 {: tip}

### Saiba mais sobre o Sauce Labs

Para saber mais sobre o Sauce Labs, consulte o artigo [Sauce Labs ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/deliver/tool_sauce_labs/){: new_window} no IBM Cloud Garage Method ou execute este tutorial:

  * [Usar a cadeia de ferramentas "Desenvolver e testar microsserviços no Cloud Foundry" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}



## Configurando o Slack
{: #slack}

As notificações que são postadas em canais públicos do Slack são visíveis para todos na equipe. Você será responsável pelo conteúdo que postar.
{: important}

O Slack é um sistema de mensagens e um sistema de notificação tempo real baseados na nuvem. O Slack fornece o bate-papo persistente, que é uma alternativa interativa ao e-mail para a colaboração da equipe. É
possível se comunicar com sua equipe em um canal dedicado ou em um conjunto de canais diretamente relacionado ao seu trabalho. Também é possível
compartilhar arquivos e imagens por meio dos canais ou em mensagens diretas entre duas ou mais pessoas. As comunicações nas mensagens diretas e nos
canais são retidas para que seja possível procurá-las.

Configure o Slack para recuperar notificações sobre sua cadeia de ferramentas a partir das integrações de ferramenta, como atividades de
teste e de implementação:

1. Se você estiver configurando esta integração de ferramenta conforme estiver criando a cadeia de ferramentas, na seção Integrações configuráveis, clique em **Slack**.
1. Se você tiver uma cadeia de ferramentas e estiver incluindo essa integração de ferramenta nela, no painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, em **Visão geral**.

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramenta, clique em **Slack**.

1. Digite a URL de webhook do Slack, que é gerada pelo Slack como um webhook recebido. É necessária uma URL do webhook do Slack para que um canal Slack receba notificações sobre sua cadeia de ferramentas das integrações de ferramentas. Para obter instruções para criar ou localizar seu webhook, veja [Webhooks recebidos ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://api.slack.com/incoming-webhooks){: new_window}.

 Se você usa uma chave de API para seu canal Slack para receber notificações sobre sua cadeia de ferramentas por meio das integrações de ferramentas, deve-se atualizar sua configuração para usar um webhook em seu lugar.
 {: tip}

1. Digite o nome do canal Slack para o qual deseja que as notificações sejam enviadas. O canal deve existir e estar ativo na equipe do Slack.
1. Digite o nome do host da URL para sua equipe do Slack, que é a palavra ou a frase antes de `.slack.com` na URL de sua equipe. Por exemplo, se a URL de sua equipe for `https://team.slack.com`, o nome do host será `team`.
1. Clique em
**Criar integração**.

 Se a equipe ou o canal do Slack que você especificou não puderem ser acessados, o erro `Setup Failed` será exibido na placa do Slack. Passe o mouse sobre a mensagem `Falha na configuração` e clique em **Reconfigurar**. Certifique-se de que esteja usando parâmetros de configuração válidos para a URL do webhook do Slack, o canal Slack e o nome do host da URL para sua equipe do Slack. Atualize as configurações conforme necessário e clique em **Salvar integração**.
 {: tip}

1. Clique em **Slack**. É possível visualizar todas as atividades para sua cadeia de ferramentas no canal Slack configurado.

### Saiba mais sobre o Slack

Para saber mais sobre o Slack, consulte o artigo [Slack ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/culture/tool_slack/){: new_window} no IBM Cloud Garage Method ou execute este tutorial e o curso de defensor do Garage Method:

  * [Usar a cadeia de ferramentas "Desenvolver e testar microsserviços no Cloud Foundry" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}

  * [Tornar-se um porta-voz do Garage Method ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/course/gm_advocate/){:new_window}


## Configurando o SonarQube
{: #sonarqube}

O SonarQube fornece uma visão geral do funcionamento geral e da qualidade do seu código-fonte e destaca os problemas encontrados no novo código. Os analisadores de código detectam erros difíceis, como desreferência de ponteiro nulo, erros lógicos e fugas de recursos, em mais de 20 linguagens de codificação.

Configure o SonarQube para continuamente analisar e medir a qualidade de seu código-fonte:

1. No painel do DevOps, clique em **Cadeias de ferramentas**. Clique na cadeia de ferramentas na qual deseja incluir o SonarQube. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas**. Em seguida, clique em **Visão geral**.  

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramentas, clique em **SonarQube**.

1. Digite um nome para essa instância da integração de ferramenta SonarQube.
1. Digite a URL para a instância SonarQube que você deseja abrir ao clicar no cartão SonarQube de sua cadeia de ferramentas.
1. Opcional: Digite o nome de usuário que você usa para se conectar ao servidor SonarQube.

 Será necessário especificar um nome do usuário apenas se você usar uma senha para se conectar ao servidor do SonarQube. Se você usar um token de autenticação para se conectar, deixe esse campo vazio.
 {: tip}

1. Digite a senha ou o token de autenticação que deseja usar para se conectar ao servidor SonarQube.
1. Clique em
**Criar integração**.
1. Na cadeia de ferramentas, clique em **SonarQube** para visualizar o painel da instância SonarQube ao qual você se conectou.

### Saiba mais sobre o SonarQube

Para saber mais sobre o SonarQube, veja o [artigo SonarQube ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/content/learn/tool_sonarqube/){: new_window} no IBM Cloud Garage Method.
