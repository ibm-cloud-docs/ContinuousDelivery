---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-27"

keywords: users of a service instance, a-service, Git Repos

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}


# Limitações e uso do plano
{: #limitations_usage}

O uso do {{site.data.keyword.contdelivery_full}} está limitado a operações de construção, implementação, teste e em andamento de aplicativos na plataforma do {{site.data.keyword.Bluemix_notm}} ou em outras ofertas de plataforma como serviço ou infraestrutura como serviço compatíveis.

## Escopo de uma instância de serviço
{: #service_scope}

Deve-se ter uma [instância de serviço](https://cloud.ibm.com/catalog/services/continuous-delivery){:external} {{site.data.keyword.contdelivery_short}} para criar e usar cadeias de ferramentas do DevOps. Uma instância de serviço pode pertencer a um [grupo de recursos](/docs/services/resources?topic=resources-rgs) {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) ou a uma organização {{site.data.keyword.Bluemix_notm}} (org).

É possível criar *novas* instâncias do serviço {{site.data.keyword.contdelivery_short}} somente em grupos de recursos. A migração de cadeias de ferramentas das organizações para grupos de recursos não é suportada atualmente. Se você estiver sem um serviço {{site.data.keyword.contdelivery_short}} para uma organização que contenha cadeias de ferramentas, será possível criar as cadeias de ferramentas novamente em um grupo de recursos ou entrar em contato com o [Suporte IBM](https://cloud.ibm.com/unifiedsupport){:external} para obter ajuda.

É possível ter um serviço Lite somente por conta. É recomendado que você use o plano Profissional se desejar trabalhar com cadeias de ferramentas em múltiplas organizações ou grupos de recursos ou dentro de múltiplas regiões.
{: tip}


## Usuários autorizados
{: #authorized_users}

Os [planos de serviço](https://cloud.ibm.com/catalog/services/continuous-delivery){:external} {{site.data.keyword.contdelivery_short}} são definidos e precificados com base no número de usuários autorizados para uma instância de serviço. Quem contribui para um
esforço deve ser contado como um usuário autorizado, incluindo:

 * Os usuários que interagem com problemas, conselhos de problemas, código-fonte ou outros artefatos em
um repositório do {{site.data.keyword.gitrepos}}.
 * Os usuários que manipulam, acionam (diretamente na interface com o usuário ou indiretamente confirmando em um repositório) ou visualizam o status de um Delivery Pipeline.
 * Os usuários que interagem com o Eclipse Orion {{site.data.keyword.webide}}.
 
O plano Lite está sujeito a limites. Para obter mais informações sobre o plano Lite e o plano Profissional, consulte o [catálogo de serviços](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}.
{: tip}
 
### Como os usuários são contados para instâncias do {{site.data.keyword.contdelivery_short}} em grupos de recursos?

Os usuários autorizados são contados e gerenciados para cada instância de serviço, examinando a lista de usuários autorizados para limites de faturamento e plano Lite. Os usuários do serviço {{site.data.keyword.contdelivery_short}} são automaticamente incluídos nessa lista. É possível impedir que os usuários acessem cadeias de ferramentas e sejam incluídos automaticamente em uma instância de serviço {{site.data.keyword.contdelivery_short}}. Para obter mais informações sobre como usar o IAM para remover o acesso de usuário do Grupo de recursos que contém a cadeia de ferramentas (ou da própria cadeia de ferramentas), consulte [Gerenciando o acesso de usuário ao {{site.data.keyword.contdelivery_short}} com Identity and Access Management](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security). 

O método que você usa para organizar cadeias de ferramentas dentro de grupos de recursos impacta diretamente o acesso do usuário e o faturamento. Quando um usuário usa cadeias de ferramentas em múltiplos grupos de recursos, eles são contados e faturados para cada serviço nesses grupos de recursos.
{: tip}

É possível gerenciar a lista de usuários autorizados na guia **Gerenciar** dentro da instância de serviço {{site.data.keyword.contdelivery_short}}.

1. Acesse a [Lista de recursos](https://cloud.ibm.com/resources){:external} para sua conta do {{site.data.keyword.Bluemix_notm}}.
2. Na coluna **Nome**, na caixa de texto de filtro, digite **Entrega Contínua** para mostrar seus serviços existentes.
3. Para cada serviço, clique no hyperlink na coluna **Nome**.
4. Na guia **Gerenciar**, é possível visualizar, incluir ou remover usuários da lista de Usuários autorizados, conforme necessário.

Os usuários são incluídos automaticamente ou incluídos novamente quando usam o serviço {{site.data.keyword.contdelivery_short}}.
{: tip}

### Como os usuários são contados para instâncias do {{site.data.keyword.contdelivery_short}} em organizações?

Os usuários autorizados são contados examinando todos os usuários na organização {{site.data.keyword.Bluemix_notm}} que contém o serviço {{site.data.keyword.contdelivery_short}}. Para obter mais informações sobre organizações e espaços, consulte [Criando organizações e espaços](/docs/cloud-foundry?topic=cloud-foundry-create_orgs).

Para visualizar a lista de usuários em sua organização em um ambiente público do {{site.data.keyword.Bluemix_notm}}, na barra de menus, clique em **Gerenciar > Conta**. Em seguida, clique em **Organizações do Cloud Foundry**.

### Como é possível visualizar informações de faturamento e uso?

É possível visualizar todas as instâncias do serviço do {{site.data.keyword.contdelivery_short}} em sua conta e o número de usuários e execuções de pipeline relatados com relação a cada instância em um ambiente do {{site.data.keyword.Bluemix_notm}} Public.

1. Na barra de menus, clique em **Gerenciar > Faturamento e uso**.
2. Clique em **Uso**.
3. Na seção **Serviços**, clique em **Visualizar planos** para o serviço {{site.data.keyword.contdelivery_short}}.
4. Clique em **Visualizar detalhes** para o plano sobre o qual você deseja visualizar informações.
5. Clique em **Visualizar detalhes da instância** para a instância do {{site.data.keyword.contdelivery_short}} para a qual você deseja visualizar informações de uso.

A métrica `AUTHORIZED_USERS_PER_MONTH` é calculada com base em uma média mensal de usuários que é contada diariamente.
{: tip}

### O que acontece quando você excede os limites de seu plano de serviço?

O plano de serviço Lite tem outras limitações, como o número de tarefas de Delivery Pipeline que podem ser executadas ou o consumo de armazenamento. Para obter mais informações sobre a descrição do plano, consulte o [catálogo de serviços](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}. Se qualquer uma das limitações de plano for excedida em um período de faturamento, o serviço será suspenso. Por exemplo, as tarefas do Delivery Pipeline não são executadas para o restante do período de faturamento.

## Uso do Delivery Pipeline
{: #pipeline_usage}

Os comportamentos de uso aceitáveis incluem, mas não estão limitados a estes comportamentos:

* A compilação e o conjunto de artefatos para linguagens de programação suportadas.
* A implementação automatizada dos artefatos de aplicativos, configurações e recursos de suporte ou serviços.
* Teste, validação e outro comportamento gerado pelo evento de desenvolvimento que é acionado como o resultado de um processo de desenvolvimento.

Os comportamentos de uso que não são permitidos incluem, mas não estão limitados a estes comportamentos:

* O uso de tarefas de pipeline ou trabalhadores para comportamentos de cálculo gerais, como mineração de Bitcoin, ataques de Negação de Serviço distribuídos e comportamento malicioso ou ofensivo para outros clientes ou usuários na plataforma {{site.data.keyword.Bluemix_notm}} ou usuários gerais da Internet.
* O uso no processo de desenvolvimento normal para sites ou serviços que promovem discurso de ódio ou outras atividades que violam as Business Conduct Guidelines da IBM.
* O uso de comportamento gerado por evento para intrusão maliciosa ou ataques contra o {{site.data.keyword.Bluemix_notm}} ou outros sites.

A critério da IBM, os usuários que violarem os comportamentos de uso aceitáveis dos serviços do {{site.data.keyword.contdelivery_short}} ou de [IBM Business Conduct Guidelines](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){:external} podem ser desativados sem aviso. A critério da IBM, alguns serviços poderão ser restaurados se os usuários corrigirem seus comportamentos de uso depois de serem notificados da ação ofensiva. Caso contrário, as contas poderão ser suspensas ou finalizadas.

## Limitações do Git Repos and Issue Tracking
{: #git_limitations}

O {{site.data.keyword.gitrepos}} é construído no GitLab Community Edition e hospedado pela IBM no {{site.data.keyword.Bluemix_notm}}, no entanto, algumas opções do GitLab não estão disponíveis:

 * Como o {{site.data.keyword.deliverypipeline}} fornece a integração contínua e entrega contínua para o {{site.data.keyword.Bluemix_notm}}, os recursos de integração contínua no GitLab não são suportados.
 * As funções de administração do GitLab não estão disponíveis porque elas são gerenciadas pela IBM.
 * O {{site.data.keyword.gitrepos}} pode não ser totalmente acessível.

## Informações sobre o usuário e conteúdo do Git Repos and Issue Tracking
{: #git_projects}

Três tipos de projetos do {{site.data.keyword.gitrepos}} estão disponíveis:

  1. Os projetos públicos são visíveis para todos os visitantes do site. O conteúdo em um projeto público está visível para todos que acessam o {{site.data.keyword.contdelivery_short}}, mesmo se eles não forem convidados para o projeto.
  2. Os objetos privados são visíveis para usuários selecionados somente. Para obter mais informações sobre como conceder acesso de usuários a um projeto, consulte [Usuários do projeto](https://us-south.git.cloud.ibm.com/help/user/project/members/index.md){:external}.
  3. Os projetos internos são visíveis para todos os usuários com login efetuado. Qualquer usuário que tenha uma conta do {{site.data.keyword.Bluemix_notm}} pode visualizar esses projetos.

É possível modificar o tipo de projeto nas configurações do projeto. Para obter mais informações sobre as configurações do projeto, consulte [Como mudar a visibilidade do projeto](https://us-south.git.cloud.ibm.com/help/public_access/public_access#how-to-change-project-visibility){:external}.

Quando você usa o {{site.data.keyword.gitrepos}}, o conteúdo contribuído para um projeto é licenciado sob os termos que são especificados nesse projeto. Ao criar um projeto, inclua um arquivo que descreva a licença que se aplica ao conteúdo. Quando você contribui para um projeto, seu nome e o endereço de e-mail que está associado às suas confirmações podem ser visíveis para o público. O endereço de e-mail que está associado à sua conta do {{site.data.keyword.Bluemix_notm}} é usado quando você cria confirmações por meio da interface da web do {{site.data.keyword.gitrepos}}.
