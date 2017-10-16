---

copyright:
  years: 2016, 2017
lastupdated: "2017-7-24"
---
<!-- Copyright info at top of file: REQUIRED
    The copyright info is YAML content that must occur at the top of the MD file, before attributes are listed.
    It must be surrounded by 3 dashes.
    The value "years" can contain just one year or a two years separated by a comma. (years: 2014, 2016)
    Indentation as per the previous template must be preserved.
-->

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Limitações e uso do plano
{: #deliverypipeline_plans}
{: #free_deprecation}

O uso do {{site.data.keyword.contdelivery_full}} está limitado a operações de construção, implementação, teste e em andamento de aplicativos na plataforma do {{site.data.keyword.Bluemix_notm}} ou em outras ofertas de plataforma como serviço ou infraestrutura como serviço compatíveis.

Os comportamentos de uso aceitáveis incluem, mas não estão limitados a estes comportamentos:

* A compilação e o conjunto de artefatos para linguagens de programação suportadas
* A implementação automatizada de artefatos de aplicativo, configurações e recursos ou serviços de suporte
* Teste, validação e outro comportamento gerado pelo evento de desenvolvimento que é acionado como resultado de um processo de desenvolvimento

Os comportamentos de uso que não são permitidos incluem, mas não estão limitados a estes comportamentos:

* O uso de tarefas ou trabalhadores de pipeline para comportamentos de cálculo geral, como mineração de Bitcoin, ataques de negação de serviço distribuídos e comportamento malicioso ou ofensivo para outros clientes ou usuários dentro da plataforma IBM Cloud ou usuários gerais da Internet
* O uso no processo de desenvolvimento normal para sites ou serviços que promovem discurso de ódio ou outras atividades que violam as IBM Business Conduct Guidelines
* O uso de comportamento gerado pelo evento para intrusão maliciosa ou ataques contra o {{site.data.keyword.Bluemix_notm}} ou outros sites

A critério da IBM, os usuários que violam os comportamentos de uso aceitáveis dos serviços {{site.data.keyword.contdelivery_short}} ou as [IBM Business Conduct Guidelines ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){: new_window} podem ser desativados sem aviso. A critério da IBM, alguns serviços poderão ser restaurados se os usuários corrigirem seus comportamentos de uso depois de serem notificados da ação ofensiva. Caso contrário, as contas poderão ser suspensas ou finalizadas.

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
  2. Os projetos privados são visíveis somente para usuários selecionados. Para obter detalhes sobre como conceder acesso de usuário a um projeto, veja [Usuários do projeto ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/help/workflow/add-user/add-user.md){: new_window}.
  3. Os projetos internos são visíveis para todos os usuários com login efetuado. Qualquer usuário que tenha uma conta do {{site.data.keyword.Bluemix_notm}} pode visualizar esses projetos.

É possível modificar o tipo de projeto nas configurações do projeto. Para obter mais informações, veja [Como mudar a visibilidade do projeto ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/help/public_access/public_access#how-to-change-project-visibility){: new_window}.

Quando você usa o {{site.data.keyword.gitrepos}}, o conteúdo contribuído para um projeto é licenciado sob os termos que são especificados nesse projeto. Ao criar um projeto, inclua um arquivo que descreva a licença que se aplica ao conteúdo. Quando você contribui para um projeto, seu nome e o endereço de e-mail que está associado às suas confirmações podem ser visíveis para o público. O endereço de e-mail que está associado à sua conta do {{site.data.keyword.Bluemix_notm}} é usado quando você cria confirmações por meio da interface da web do {{site.data.keyword.gitrepos}}.

<!-- ###Privacy with Git Repos and Issue Tracking profiles -->

<!-- A few features of {{site.data.keyword.gitrepos}} require the use of a profile page that publicly displays information that you provide. You give IBM the following permissions: -->

  <!-- a. Make the information in your profile&mdash;such as your name, email, picture, bio, social media links, and user activity&mdash;visible to other users of the service. -->

  <!-- b. Publicly disclose your name and other public information and activities that are associated with your use of the service, or otherwise publicize the fact that you are a user of the service, without any further notice to you. -->

<!-- The email address that is associated with your profile page is derived from your {{site.data.keyword.Bluemix_notm}} account details. To modify the email address that is displayed on your profile page, modify your {{site.data.keyword.Bluemix_notm}} account. -->

<!-- ## Deprecated services
{: #deprecated_services} -->

<!--{{site.data.keyword.trackplan}} and {{site.data.keyword.deliverypipeline}} Classic, which are part of IBM Bluemix {{site.data.keyword.jazzhub_short}} (JazzHub), are being retired. For more information, see [Track & Plan Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/track-plan-retirement/){: new_window} and [Delivery Pipeline Retirement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/04/delivery-pipeline-retirement/){: new_window}. -->

<!-- Starting on May 25, no new JazzHub projects can be created. Through automatic rolling upgrades, JazzHub projects will be upgraded to {{site.data.keyword.contdelivery_short}} toolchains. The JazzHub site will be removed from service in early July. For more information about the upgrade, see [Upgrading JazzHub project to Bluemix Continuous Delivery toolchains ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/devops-services/2017/4/18/upgrading-jazzhub-projects-bluemix-continuous-delivery-toolchains/){: new_window} -->
