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

# Fazer upgrade do projeto {{site.data.keyword.jazzhub_short}} para uma cadeia de ferramentas
{: #upgrade_projects}

O {{site.data.keyword.jazzhub}} está sendo desenvolvido para o {{site.data.keyword.contdelivery_full}}. Como parte dessa mudança, os projetos são submetidos a upgrade para cadeias de ferramentas.

É possível fazer upgrade de seu projeto ou esperar que seja submetido a upgrade automaticamente. Para obter a melhor experiência, certifique-se de atender aos [pré-requisitos](#upgrade_prereqs) e fazer upgrade de seu projeto assim que possível para que possa controlar o nome da sua cadeia de ferramentas e a organização na qual ela foi criada.
{: shortdesc}

**Perguntas Mais Frequentes**

- [Meu projeto JazzHub está associado à região Reino Unido, mas a minha cadeia de ferramentas está na região Sul dos EUA. Como isso funcionará?](#faq_region)
- [O que acontece com meus itens de trabalho e painéis no Track &amp; Plan quando faço upgrade?](#faq_tp)
- [O que acontece com o meu repositório de código quando faço upgrade?](#faq_repo)
- [O que acontece com minhas definições de construção em meu projeto quando faço upgrade para uma cadeia de ferramentas?](#faq_build)
- [Eu preciso criar uma organização para meu projeto que é submetido a upgrade para uma cadeia de ferramentas. Eu entendo que preciso incluir um cartão de crédito em minha conta antes que eu possa criar uma organização. Meu cartão de crédito será debitado?](#faq_charges)
- [Não consigo localizar ou acessar minha cadeia de ferramentas. O que eu posso fazer? ](#faq_find)
- [Meu projeto está associado à região do Reino Unido. Após o upgrade, eu vejo mensagens de erro, meus colegas não conseguem acessar a cadeia de ferramentas e eu não vejo minha cadeia de ferramentas na página Cadeias de ferramentas no {{site.data.keyword.Bluemix_notm}} Platform. O que há de errado?](#faq_uk)

## Cadeias de ferramentas
{: #compare_toolchains}

As cadeias de ferramentas são como projetos, com algumas diferenças importantes:

- Os projetos podem ter apenas um repositório (repo) e pipeline. As cadeias de ferramentas podem ter tantos repositórios e pipelines quantos forem necessários.
- As cadeias de ferramentas podem incluir ferramentas que não estão disponíveis em projetos, como Slack, Sauce Labs, PagerDuty e {{site.data.keyword.DRA_full}}.
- O acesso às cadeias de ferramentas é gerenciado pelas organizações {{site.data.keyword.Bluemix_notm}} padrão. A associação é mantida no nível de organização, ao contrário dos projetos, nos quais a associação era mantida no nível do projeto.

É possível saber mais sobre cadeias de ferramentas no [YouTube ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://youtu.be/2SIPE1e7NJ4){: new_window} ou em [Introdução ao {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery/index.html).
[![Link externo para o YouTube](images/CD_video.png)](https://youtu.be/2SIPE1e7NJ4){: new_window}

## Pré-requisitos
{: #upgrade_prereqs}

- Para acessar a cadeia de ferramentas de seu projeto atualizado, você precisa de um ID do {{site.data.keyword.Bluemix_notm}}. Antes de fazer upgrade, deve-se verificar se você tem um ID do {{site.data.keyword.Bluemix_notm}} ativo. Se você não tiver um, [inscreva-se](https://console.ng.bluemix.net/registration/).
- Certifique-se de que o proprietário do projeto {{site.data.keyword.jazzhub_short}} esteja correto. A cadeia de ferramentas que é criada por meio de seu projeto faz parte da organização do {{site.data.keyword.Bluemix_notm}} do proprietário.
- Certifique-se de que a organização e o espaço nos quais você deseja criar sua cadeia de ferramentas estejam no {{site.data.keyword.Bluemix_notm}} Public na região sul dos EUA. Para confirmar que há uma organização e um espaço válidos no sul dos EUA, efetue login em [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window} e crie um espaço se você for solicitado a criar um.
- Se estiver planejando iniciar o upgrade, certifique-se de que você seja um membro de cada organização e espaço em que o pipeline for implementado. Qualquer administrador de projeto pode iniciar o upgrade. No entanto, se o administrador que iniciar o upgrade não for um membro de cada organização e espaço em que o pipeline for implementado, o pipeline não poderá ser criado. A pessoa que inicia o upgrade se torna o proprietário do repositório na cadeia de ferramentas.
- O Eclipse Orion {{site.data.keyword.webide}} na cadeia de ferramentas é separado do {{site.data.keyword.webide}} que está associado ao projeto. Se você usar o {{site.data.keyword.webide}} e houver mudanças não confirmadas, confirme-as antes de fazer upgrade.


## Fazendo upgrade de um projeto para uma cadeia de ferramentas
{: #project_to_toolchain}

Os projetos no hub.jazz.net e as cadeias de ferramentas são ambos hospedados na região sul dos EUA. Se seu projeto foi configurado para implementar apps em uma região diferente, ele ainda implementará apps nessa região após ser submetido a upgrade para uma cadeia de ferramentas.
{: tip}

Quando seu projeto estiver pronto para ser submetido a upgrade, uma mensagem será exibida no cartão do projeto e na página Visão geral.

![Imagem do cartão com o rótulo Pronto para upgrade](images/card-project-to-upgrade.png)

![Mensagem de horário para upgrade](images/banner-ready-to-upgrade.png)

Será possível localizar projetos que estiverem prontos para upgrade por meio do menu na página Meus Projetos:

![Imagem do item de menu Projetos dos quais fazer upgrade](images/menu-projects-to-upgrade.png)
{: tip}

Ao iniciar o upgrade, os estágios do pipeline em seu projeto serão bloqueados. Não é possível os executar nem os modificar. Se você reverter o upgrade excluindo a cadeia de ferramentas, o pipeline será desbloqueado.

Se seu projeto usar um repositório Git hospedado no JazzHub, depois de iniciar o upgrade, o repositório será bloqueado para garantir a integridade dos dados que são movidos para a cadeia de ferramentas. Se você reverter o upgrade excluindo a cadeia de ferramentas, o repo no JazzHub será desbloqueado.

Para obter detalhes integrais sobre como cada tipo de repositório é tratado no processo de upgrade, veja a tabela a seguir.

|Repositório de projetos |Tipo de projeto	|Repositório de cadeias de ferramentas |
|:----------|:------------------------------|:------------------|
|github.com 		|Privado ou público 		|O mesmo repositório github.com com o {{site.data.keyword.Bluemix_notm}} Public.	|
|hub.jazz.net/git		|Privado ou público 		|Um novo repositório no {{site.data.keyword.gitrepos}} com o {{site.data.keyword.Bluemix_notm}} Public.	|
{: caption="Tabela 1. Repositórios de projeto mapeados para repositórios de cadeia de ferramentas" caption-side="top"}

## Iniciando o Processo de Upgrade
{: #start_upgrade}

Antes de iniciar o processo de upgrade, é possível observá-lo em ação no [YouTube ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://youtu.be/LSr2e3uvyLs){: new_window}.
[![Link externo para o YouTube](images/migration-video2.png)](https://youtu.be/LSr2e3uvyLs){: new_window}

Para fazer upgrade de seu projeto para uma cadeia de ferramentas, siga estas etapas:

1. Para iniciar o processo de upgrade, na mensagem do banner, clique em **fazer upgrade agora**. A página "Cadeia de ferramentas de upgrade do projeto" é aberta.

   ![Exemplo de uma página de upgrade](images/project-upgrade-toolchain.png)

   Para obter uma visão geral do processo de upgrade, leia a descrição nessa página. A cadeia de ferramentas inclui um novo pipeline que contém os mesmos estágios e tarefas que o pipeline do projeto. Além disso, a cadeia de ferramentas contém um ponteiro para o Eclipse Orion {{site.data.keyword.webide}} que é executado no {{site.data.keyword.contdelivery_short}}.

   Nesse exemplo, como o projeto usa um repositório público em github.com, a cadeia de ferramentas é conectada ao mesmo repositório GitHub. Se o seu projeto usar um repositório Git que está hospedado no JazzHub, os conteúdos desse repositório serão clonados para um novo repositório no {{site.data.keyword.gitrepos}}, que faz parte do {{site.data.keyword.contdelivery_short}}.

2. Para customizar a cadeia de ferramentas, é possível configurar algumas definições:

   - Para mudar o nome da cadeia de ferramentas, edite o campo **Nome**.

      ![Campo Nome](images/name-change.png)

   - Para mudar em qual organização do {{site.data.keyword.Bluemix_notm}} criar a cadeia de ferramentas, selecione a organização no menu de sua conta:

      ![{{site.data.keyword.Bluemix_notm}}Seletor de organização](images/bluemix-organization-chooser.png)

   Como as cadeias de ferramentas são gerenciadas no nível de organização, certifique-se de selecionar uma organização na qual os membros do projeto que precisam acessar a cadeia de ferramentas existem ou podem ser incluídos.

3. Se você usou Track & Plan em seu projeto, é possível transferir os dados do Track & Plan para o GitHub Issues.

   ![Opções de Track and Plan](images/upgrade-tutorial-track-and-plan.png)

   - Indique se você deseja migrar seus dados do Track & Plan.
   - Por padrão, todos os dados do Track & Plan são migrados. Se você preferir migrar apenas os itens de trabalho que fazem parte de uma consulta específica, especifique essa consulta.
   - Selecione qualquer atributo de item de trabalho que você deseja mapear para rótulos no GitHub Issues.

4. Clique em **Criar**. A nova cadeia de ferramentas é criada e sua página Visão geral é exibida.

   ![Visão geral da cadeia de ferramentas com upgrade](images/new-toolchain-page.png)

   - Para acessar seu repositório GitHub ou o rastreador de problemas associado, clique em **GitHub** ou **Problemas**.
   - Para acessar seu pipeline, clique em **Delivery Pipeline**.
   - Para acessar o {{site.data.keyword.webide}}, que contém o conteúdo de seu repositório que foi retirado para a área de trabalho, clique em **Eclipse Orion {{site.data.keyword.webide}}**.

   Se você retornar para seu projeto durante o upgrade, a mensagem do banner poderá declarar que o upgrade está em andamento, especialmente se o processo de upgrade envolve a importação de código-fonte para um novo repositório ou a importação de itens de trabalho do Track &amp; Plan como problemas.

   ![Mensagem sobre o projeto em upgrade para uma cadeia de ferramentas](images/project-being-upgraded-banner.png)

## Revisitando seu projeto
{: #revisit_projects}

Você está pronto para usar sua nova cadeia de ferramentas. Seu projeto agora está identificado como "Submetido a upgrade" e, na página Visão geral, é exibida uma mensagem de confirmação.

![Imagem do cartão do projeto com o rótulo Upgrade feito](images/card-upgraded-project.png)

![Projeto com upgrade](images/banner-upgraded.png)

É possível ver quais projetos foram submetidos a upgrade selecionando **Projetos submetidos a upgrade** no menu na página Meus projetos:

![Imagem do item de menu Projetos com upgrade](images/menu-upgraded-projects.png)

Se for necessário reverter o upgrade, exclua sua cadeia de ferramentas. É possível excluir sua cadeia de ferramentas do menu **Mais ações** na página Visão geral da cadeia de ferramentas:

![imagem da ação Excluir no menu Mais ações](images/upgrade-tutorial-delete-toolchain.png)

Quando você retornar ao seu projeto, a mensagem de upgrade será exibida novamente e um novo upgrade poderá ser feito quando você estiver pronto.

## Próximas Etapas
{: #upgrade_next_steps}

1. Confirme se o upgrade está completo atualizando seu navegador e verificando a mensagem de que seu projeto foi "atualizado para essa cadeia de ferramentas" na página Visão geral do projeto:

   ![Mensagem no banner indicando que foi feito upgrade do projeto](images/banner-upgraded.png)

   Se a mensagem disser "Fazer upgrade agora", o seu upgrade falhou. Clique no link **upgrade agora** para tentar novamente.
   {: tip}

   ![Mensagem no banner indicando que o projeto está pronto para upgrade](images/banner-ready-to-upgrade.png)

2. Dê aos membros da equipe acesso à cadeia de ferramentas.
    - Cada membro da equipe deve ter uma conta do {{site.data.keyword.Bluemix_notm}} válida. Os membros da equipe que não tiverem contas deverão [inscrever-se ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/registration){:new_window}.
    - Conceda aos membros da organização acesso à cadeia de ferramentas na página Gerenciar da cadeia de ferramentas. Os membros existentes do projeto são incluídos como membros da cadeia de ferramentas como parte do processo de upgrade. Para obter mais informações sobre o controle de acesso de cadeias de ferramentas, consulte [Gerenciando o acesso ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access){:new_window}.
    - Se um usuário não for um membro da organização à qual a cadeia de ferramentas pertence, inclua-o na organização na página Gerenciar organizações.
    - Se sua cadeia de ferramentas usar {{site.data.keyword.gitrepos}}, todos os membros do projeto JazzHub que tenham um ID válido do {{site.data.keyword.Bluemix_notm}} serão incluídos no repositório {{site.data.keyword.gitrepos}} com os mesmos privilégios que eles tinham no projeto JazzHub. Se o seu projeto JazzHub incluir membros que não têm um ID do {{site.data.keyword.Bluemix_notm}} válido, eles deverão registrar-se para um e ser incluídos no repositório.
      Para obter mais informações sobre como gerenciar organizações, consulte [Gerenciando organizações e espaços ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/admin/orgs_spaces.html#orgsspacesusers){:new_window}.

3. Use as ferramentas de sua cadeia de ferramentas no lugar das ferramentas de seu projeto {{site.data.keyword.jazzhub_short}}. Por exemplo, para editar código usando um navegador, use o Web IDE de sua cadeia de ferramentas.

4. Se você estiver usando o {{site.data.keyword.gitrepos}}, autentique usando um token de acesso pessoal ou uma chave SSH. Para obter mais informações sobre chaves SSH, consulte [Criando um token de acesso pessoal ou uma chave SSH para autenticação](/docs/services/ContinuousDelivery/git_working.html#git_authentication). Para autenticar de um cliente Git externo através de https, siga estas etapas:
    1. Acesse a [página Tokens de acesso ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window} das configurações de usuário do {{site.data.keyword.gitrepos}}.
    2. Crie um token de acesso pessoal que use **api** como escopo.
    3. Acesse a [página Conta ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/profile/account){:new_window} e localize seu nome de usuário para o {{site.data.keyword.gitrepos}}. Seu nome do usuário é listado na seção "Mudar o nome do usuário" e é mostrado como a primeira parte da URL para qualquer repositório pessoal criado.
    4. Para autenticar com o {{site.data.keyword.gitrepos}} por meio de um cliente Git externo usando https, use seu nome do usuário e seu token de acesso pessoal.
    5. Se você desejar reutilizar o repositório local de seu repositório Git JazzHub, aponte o repositório para o novo repositório no {{site.data.keyword.gitrepos}}. Em um shell em um terminal, mude para o diretório no qual o repositório Git JazzHub é clonado. Insira o comando `git remote set-url`: `git remote set-url origin https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

        Para verificar quais URLs remotas estão configuradas para quais nomes remotos, use o comando `git remote -v`. O nome remoto padrão é `origin`. Se você tiver uma configuração mais avançada, o formulário do comando será o seguinte: `git remote set-url <remote-name-that-uses-jazzhub-repo> https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`
        {: tip}

5. Quando a sua cadeia de ferramentas for configurada e você começar a usá-la, considere executar todas ou qualquer uma destas etapas para assegurar que ninguém use seu projeto:
    - Inclua um sufixo no nome do projeto para indicar que ele não deve ser usado. Você poderá incluir `_DO_NOT_USE` no final do nome do projeto.
    - Atualize a descrição do projeto para mencionar que ele não é mais usado e inclua um ponteiro na cadeia de ferramentas.
    - Remova os membros do projeto.
    - Quando você não precisar mais do projeto, exclua-o.

6. Opcional: para explorar a maturidade de desenvolvimento do projeto, as práticas da equipe e a qualidade do código base, inclua o IBM Cloud {{site.data.keyword.DRA_short}} na sua cadeia de ferramentas. O {{site.data.keyword.DRA_short}} aplica a análise de desenvolvedor, equipe e implementação aos projetos do DevOps. Para obter mais informações, consulte [Introdução ao {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights/index.html).


## Solucionando problemas
{: #upgrade_troubleshoot}

Se você encontrar um problema durante o processo de upgrade, tente uma ou mais destas etapas de resolução de problemas:

- Verifique os [pré-requisitos](#upgrade_prereqs) para assegurar que os atenda. Em particular, certifique-se de que você seja um membro de cada organização e espaço em que o pipeline for implementado.
- Se o problema ocorreu durante sua primeira tentativa de upgrade e você atende a todos os pré-requisitos, tente o upgrade novamente.
- Se seu projeto usar o Jazz SCM ou IBM Hosted Git para controle de fonte, verifique o tamanho do repositório. Se ele for maior que 500 MB, [entre em contato com a equipe de serviços do DevOps ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}.
- Se não for possível localizar ou acessar sua cadeia de ferramentas, veja [esta entrada de FAQ](#faq_find).
- Se você continuar a encontrar problemas, poste uma pergunta no [fórum de suporte ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. No post do fórum, inclua as URLs em seu projeto {{site.data.keyword.jazzhub_short}} e na cadeia de ferramentas do {{site.data.keyword.contdelivery_short}} e identifique seu post com a tag `devops-services`.


## Perguntas Mais Freqüentes
{: #upgrade_faq}

### Meu projeto JazzHub está associado à região Reino Unido, mas a minha cadeia de ferramentas está na região Sul dos EUA. Como isso funciona?
{: #faq_region}

Os projetos no hub.jazz.net e as cadeias de ferramentas são ambos hospedados na região sul dos EUA. Se seu projeto estiver configurado para implementar apps em uma região diferente, como a região Reino Unido, ele ainda implementará apps nessa região após ser submetido a upgrade para uma cadeia de ferramentas. Portanto, nada está realmente mudando em relação ao local onde os dados estão hospedados. As cadeias de ferramentas estarão disponíveis em mais regiões no futuro.

### O que acontece com meus itens de trabalho e painéis no Track &amp; Plan quando faço upgrade?
{: #faq_tp}

O serviço {{site.data.keyword.contdelivery_short}} fornece recursos de rastreamento de problemas por meio do {{site.data.keyword.gitrepos}}, que é hospedado pela IBM e baseado no GitLab Community Edition. O {{site.data.keyword.contdelivery_short}} também suporta integrações com outras ferramentas de planejamento e rastreamento de problemas, como GitHub Issues e JIRA.

Durante o processo de upgrade, é possível escolher migrar seus itens de trabalho do Track &amp; Plan para o Git Issues. O GitHub Issues e o {{site.data.keyword.gitrepos}} fornecem placas kanban e rastreamento de problemas para planejamento. Para saber mais sobre Placas de problemas, que são o recurso kanban no Git Repos and Issue Tracking, veja [Placa de problema ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/help/user/project/issue_board.md){: new_window}.

Para clientes que requerem a mesma função que o JazzHub Track &amp; Plan descontinuado, um novo serviço IBM Track and Plan on Cloud está disponível para compra separadamente em países selecionados em uma base por usuário por mês. Com esse serviço de nuvem, você obtém a função integral, equivalente a licenças do contribuidor do Rational Team Concert&trade;, em uma assinatura de nuvem de locatário único.

Esse novo serviço IBM Track and Plan on Cloud fornece muito mais capacidade do que o JazzHub Track &amp; Plan descontinuado, suportando customização do processo, hierarquias do projeto, SAFe&reg; e muitos outros métodos ágeis e híbridos, além de escalabilidade para crescer além um único projeto. Ele é baseado na versão mais recente do Rational Team Concert 6.0.3 e estará na versão 6.0.4 nos próximos 60 dias, enquanto o JazzHub Track &amp; Plan era baseado no Rational Team Concert 5.x. Uma migração de dados é possível para o IBM Track and Plan on Cloud por meio de serviços extras. É possível entrar em contato com [Tom Hollowell ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](mailto:trhollow@us.ibm.com){:new_window}, Connected Products SaaS Sales Leader, para obter mais informações.

Para obter informações sobre o IBM Track and Plan on Cloud ou para comprar on-line, acesse [IBM Marketplace ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window}.

Além disso, para comprar o Build Automation e o Source Code Management, o [Rational Team Concert on Cloud ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/us-en/marketplace/change-and-configuration-management/purchase#product-header-top){: new_window} é uma opção.

### O que acontece com o meu repositório de código quando faço upgrade?
{: #faq_repo}

Após o upgrade, seu novo serviço Git é comparável ao que você tinha antes. Se você usava o github.com com seu projeto JazzHub, sua cadeia de ferramentas será conectada ao mesmo repositório GitHub. Se o seu projeto JazzHub usava o IBM Hosted Git, o conteúdo desse repositório será clonado em um novo repositório no {{site.data.keyword.gitrepos}}, que faz parte do {{site.data.keyword.contdelivery_short}} e hospedado pela IBM.

Para obter detalhes integrais sobre como cada tipo de repositório é tratado no processo de upgrade, veja a tabela a seguir.

|Repositório de projetos |Tipo de projeto	|Repositório de cadeias de ferramentas |
|:----------|:------------------------------|:------------------|
|github.com 		|Privado ou público 		|O mesmo repositório github.com com o {{site.data.keyword.Bluemix_notm}} Public.	|
|hub.jazz.net/git		|Privado ou público 		|Um novo repositório privado ou público no {{site.data.keyword.gitrepos}} com o {{site.data.keyword.Bluemix_notm}} Public.	|
{: caption="Tabela 1. Repositórios do projeto que são mapeados para repositórios da cadeia de ferramentas" caption-side="top"}


### O que acontece com minhas definições de construção em meu projeto quando faço upgrade para uma cadeia de ferramentas?
{: #faq_build}

Se você está construindo seu código-fonte usando o Jazz em vez do Delivery Pipeline, deve-se migrar manualmente suas definições de construção para o Delivery Pipeline em sua cadeia de ferramentas.

Se você estiver usando o Jazz SCM como um repositório de origem e usando o Delivery Pipeline para construir seu código, a origem no Jazz SCM será movida automaticamente para um repositório Git. Sua configuração do Delivery Pipeline permanece a mesma, exceto que consome a origem do repositório Git em vez da origem do Jazz SCM.

### Preciso criar uma organização para meu projeto que será submetido a upgrade para uma cadeia de ferramentas. Eu entendo que preciso incluir um cartão de crédito em minha conta antes que eu possa criar uma organização. Meu cartão de crédito será debitado?
{: #faq_charges}

Como um [cliente Pré-pago ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window}, se usar qualquer tempo de execução, serviço ou componente além das alocações grátis que estão listadas para ele no catálogo do {{site.data.keyword.Bluemix_notm}}, você será cobrado. Para uma estimativa de uso, veja a [folha de precificação ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window}. Para ver a precificação atual do Continuous Delivery, consulte o catálogo do [{{site.data.keyword.Bluemix_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/catalog/services/continuous-delivery){: new_window}.

Se você for um funcionário IBM, projetos IBM internos poderão ser faturados para departamentos em vez de um cartão de crédito pessoal. Se você precisar usar recursos além das dotações grátis para funcionários IBM, crie um chamado de suporte.

### Eu não consigo localizar ou acessar minha cadeia de ferramentas. O que eu posso fazer?
{: #faq_find}

As cadeias de ferramentas estão hospedadas nas organizações {{site.data.keyword.Bluemix_notm}}. O processo de upgrade inclui todos os membros do projeto JazzHub na cadeia de ferramentas. Entretanto, a menos que o proprietário da organização {{site.data.keyword.Bluemix_notm}} inclua tais usuários na organização, eles não poderão ver a cadeia de ferramentas.

Para acessar sua cadeia de ferramentas, acesse o {{site.data.keyword.Bluemix_notm}} Platform, clique no ícone de menu e clique em **Serviços &gt; DevOps**. A página Cadeia de Ferramentas é aberta. Certifique-se de que você está na região Sul dos EUA e que você está na organização que contém a cadeia de ferramentas. Se sua cadeia de ferramentas não for listada na página Cadeia de Ferramentas, consulte [esta entrada da FAQ](#faq_uk).

Como alternativa, enquanto o site JazzHub ainda está disponível, é possível acessar sua cadeia de ferramentas clicando no link no banner na página Visão geral do seu projeto.

### Meu projeto está associado à região Reino Unido. Após o upgrade, vejo mensagens de erro, meus colegas não conseguem acessar a cadeia de ferramentas e não vejo minha cadeia de ferramentas na página Cadeias de ferramentas no {{site.data.keyword.Bluemix_notm}}. O que está errado?
{: #faq_uk}

**Pergunta completa:**

Meu projeto do JazzHub está associado à região Reino Unido do {{site.data.keyword.Bluemix_notm}}, de acordo com as configurações do projeto. Verifiquei minhas configurações do projeto acessando a página de visão geral no JazzHub, clicando no ícone **Configurações**, que parece uma engrenagem, e clicando em **Opções &gt; Tornar este um Projeto {{site.data.keyword.Bluemix_notm}}: Região**. Após fazer upgrade do projeto para a cadeia de ferramentas nos EUA, ocorrem esses problemas:

   1. Quando eu seleciono a organização nos EUA, vejo uma mensagem dizendo que a organização não tem um espaço na região Sul dos EUA e é solicitado que eu crie um espaço. Não desejo executar nada nos EUA.
   
   2. Alguns de meus colegas não conseguem acessar a cadeia de ferramentas, embora estejam listados como membros no projeto do JazzHub original. Se eles tentarem abrir a cadeia de ferramentas na página de visão geral do aplicativo na região Reino Unido clicando em **Visualizar cadeia de ferramentas**, verão uma mensagem de "acesso negado".
   
   3. Eu não vejo a cadeia de ferramentas listada em minha página Cadeia de Ferramentas em [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window}, embora possa acessar a cadeia de ferramentas diretamente na página de visão geral do aplicativo na região Reino Unido clicando em **Visualizar cadeia de ferramentas**. Eu recebo um erro de que não posso modificar a cadeia de ferramentas ou recebo um erro de que não possuo nenhuma cadeia de ferramentas e preciso criar uma. 

**Resposta:**

Esses problemas podem ocorrer se você veio de uma organização do {{site.data.keyword.Bluemix_notm}} que não é dos EUA e não expandiu sua organização explicitamente para a região Sul dos EUA antes de fazer upgrade. É possível confirmar esse cenário de duas maneiras:

   * Quando você abrir a URL da cadeia de ferramentas, verifique o cabeçalho do {{site.data.keyword.Bluemix_notm}}. Muito provavelmente, você verá o nome da sua organização e nenhum espaço será indicado.
   
   * Na página Visão Geral de sua cadeia de ferramentas, clique em **Gerenciar**. Na página Controle de Acesso, clique no link **Gerenciadores da organização**. A organização que contém a cadeia de ferramentas é listada na página principal.

O que aconteceu é que, no momento do upgrade, como sua organização que não é dos EUA não existia nos EUA, o upgrade selecionou outra organização para você procurando por uma à qual coincidentemente você tem acesso.

Se você alternar para essa organização do {{site.data.keyword.Bluemix_notm}} nos EUA, poderá localizar a cadeia de ferramentas. Se você incluir seus colegas nessa organização, eles terão acesso concedido. Esta cadeia de ferramentas pode continuar implementando sua organização que não é dos EUA. O único problema é que essas duas organizações são distintas; você não consegue executar o gerenciamento do usuário em ambas automaticamente.

Se você deseja que sua cadeia de ferramentas esteja em uma organização dos EUA que corresponda à sua organização que não é dos EUA, siga estas etapas:

   1. Efetue login no [https://console.bluemix.net ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net){: new_window} e selecione a região e a organização que não seja dos EUA da qual você está vindo.
   
   2. No cabeçalho do {{site.data.keyword.Bluemix_notm}}, alterne para a região Sul dos EUA. Você é solicitado a criar um espaço nessa região.
   
   3. Crie um espaço na região Sul dos EUA para expandir sua organização para essa região. 
   
   4. Exclua a cadeia de ferramentas que foi criada por meio do processo de upgrade. 
   
      O repositório Git não é excluído automaticamente. Você pode desejar excluí-lo manualmente ou renomeá-lo agora. Se você já mudou o repositório, é possível atualizar a cadeia de ferramentas futura para usá-la posteriormente.
      {: tip}

   5. Retorne ao projeto do JazzHub. Ele deve se reconfigurar para outra tentativa de upgrade. Se ele não for reconfigurado, entre em contato com hub@jazz.net e forneça a URL do projeto.
   
   6. Reinicie o processo de upgrade e certifique-se de selecionar a organização adequada nos EUA, correspondendo o nome de sua organização na região que não é dos EUA.
   
   7. Se você manteve ou renomeou o repositório Git da tentativa de upgrade da cadeia de ferramentas anterior (consulte a etapa 4), poderá reconfigurar a placa Git em sua cadeia de ferramentas para apontar para esta URL do repositório Git. A mudança é refletida automaticamente no pipeline. Para confirmar, marque a guia Entrada no estágio Construção.
