---

copyright:
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

# Introdução às cadeias de ferramentas após o upgrade de seu projeto {{site.data.keyword.jazzhub_short}}
{: #toolchains_post_upgrade}

Os projetos do {{site.data.keyword.jazzhub}} no hub.jazz.net foram submetidos a upgrade nas
cadeias de ferramentas no serviço do
{{site.data.keyword.contdelivery_short}} {{site.data.keyword.Bluemix_notm}}. 

O {{site.data.keyword.jazzhub_short}} no hub.jazz.net está obsoleto. 

Para os projetos do DevOps, use o serviço [{{site.data.keyword.contdelivery_short}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/devops){:new_window}. Se você for novo no {{site.data.keyword.Bluemix_notm}}, certifique-se de verificar a visão geral do [{{site.data.keyword.Bluemix_notm}}](/docs/overview/ibm-cloud.html#overview).

{: shortdesc}

## Localizar a cadeia de ferramentas que foi criada de seu projeto
{: #find_toolchain}

Confirme se o upgrade está completo acessando a [página Cadeias de ferramentas ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/devops/toolchains){: new_window} e verificando se você vê as cadeias de ferramentas com nomes que correspondam aos nomes de seus projetos hub.jazz.net. Se foi feito upgrade de seus projetos automaticamente, lembre-se destas advertências:
   - Se outra cadeia de ferramentas já usava o nome do seu projeto antes do upgrade do projeto, a nova cadeia de ferramentas que foi criada para seu projeto pode não ter o nome exato de seu projeto. 
   - Se você não vir cadeias de ferramentas para seus projetos, alterne para quaisquer outras organizações às quais você pertença e verifique as cadeias de ferramentas lá.
   
## Visão geral de cadeias de ferramentas
{: #compare_toolchains}

Se você tinha um ou mais projetos no hub.jazz.net, eles foram submetidos a upgrade automaticamente nas cadeias de ferramentas de serviço do {{site.data.keyword.contdelivery_short}}, a menos que o upgrade tenha falhado. Os upgrades podem falhar devido a contas ou organizações inválidas do IBM Cloud. Esses proprietários de conta e de organização foram notificados por e-mail sobre as falhas e sobre as ações específicas necessárias de sua parte para resolvê-las. Se você precisar de ajuda para localizar a cadeia de ferramentas para o seu projeto que passou por upgrade, entre em contato com [suporte ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. 

As cadeias de ferramentas são como projetos, com algumas diferenças importantes:

- Os projetos podem ter apenas um repositório (repo) e pipeline. As cadeias de ferramentas podem ter tantos repositórios e pipelines quantos forem necessários.
- As cadeias de ferramentas podem incluir ferramentas que não estão disponíveis em projetos, como Slack, Sauce Labs, PagerDuty e {{site.data.keyword.DRA_full}}.

 O {{site.data.keyword.DRA_short}} está disponível somente na região Sul dos EUA.
 {: tip}
 
- Em projetos, a associação era mantida no nível do projeto. O acesso a cadeias de ferramentas é gerenciado pela organização (org) do {{site.data.keyword.Bluemix_notm}} e por cadeia de ferramentas. Para trabalhar com uma cadeia de ferramentas, deve-se ser um membro da organização que contém a cadeia de ferramentas. O proprietário da cadeia de ferramentas tem mais controle sobre quem pode acessar a cadeia de ferramentas e o que eles podem fazer. Para obter detalhes, veja a etapa 2 em [Introdução à sua cadeia de ferramentas](#upgrade_next_steps).
- Dependendo do tipo de repositório que você usou em seu projeto no hub.jazz.net, sua cadeia de ferramentas pode conter um repositório GitHub.com ou um repositório {{site.data.keyword.gitrepos}}.

É possível aprender mais sobre cadeias de ferramentas no [YouTube ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://youtu.be/2SIPE1e7NJ4){: new_window} ou em [Introdução ao {{site.data.keyword.contdelivery_short}}](/docs/services/ContinuousDelivery/index.html).

## Introdução à sua cadeia de ferramentas
{: #upgrade_next_steps}

1. Dê aos membros da equipe acesso à cadeia de ferramentas.
    - Cada membro da equipe deve ter uma conta do {{site.data.keyword.Bluemix_notm}} válida. Os membros da equipe que não tiverem contas deverão [inscrever-se ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/registration){:new_window}.
    - Conceda aos membros da organização acesso à cadeia de ferramentas na página Gerenciar da cadeia de ferramentas. Os membros existentes do projeto são incluídos como membros da cadeia de ferramentas como parte do processo de upgrade. Para obter mais informações sobre o controle de acesso de cadeias de ferramentas, consulte [Gerenciando o acesso ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access){:new_window}.
    - Se um usuário não for membro da organização à qual a cadeia de ferramentas pertence, inclua-o na organização na página Gerenciar organizações.
    - Se sua cadeia de ferramentas usar {{site.data.keyword.gitrepos}}, todos os membros do projeto JazzHub que tenham um ID válido do {{site.data.keyword.Bluemix_notm}} serão incluídos no repositório {{site.data.keyword.gitrepos}} com os mesmos privilégios que eles tinham no projeto JazzHub. Se o seu projeto JazzHub inclui membros que não têm um ID válido do {{site.data.keyword.Bluemix_notm}}, eles podem se registrar para um. Após eles se registrarem, será possível incluí-los no repositório.
      Para obter mais informações sobre como gerenciar organizações, consulte [Gerenciando organizações e espaços ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/account/orgs_spaces.html#orgsspacesusers){:new_window}.

2. Se você estiver usando o {{site.data.keyword.gitrepos}}, autentique usando um token de acesso pessoal ou uma chave SSH. Para obter mais informações sobre chaves SSH, consulte [Criando um token de acesso pessoal ou uma chave SSH para autenticação](/docs/services/ContinuousDelivery/git_working.html#git_authentication). Para autenticar de um cliente Git externo através de https, siga estas etapas:
    1. Acesse a [página Tokens de acesso ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/profile/personal_access_tokens){:new_window} das configurações de usuário do {{site.data.keyword.gitrepos}}.
    2. Crie um token de acesso pessoal que use **api** como escopo.
    3. Acesse a [página Conta ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/profile/account){:new_window} e localize seu nome de usuário para o {{site.data.keyword.gitrepos}}. Seu nome de usuário é listado na seção "Mudar nome do usuário" e mostrado como a primeira parte da URL de qualquer repositório pessoal que você criar.
    4. Para autenticar-se no {{site.data.keyword.gitrepos}} de um cliente Git externo por meio de HTTPS, use seu nome do usuário e seu token de acesso pessoal.
    5. Se você desejar reutilizar o repositório local de seu repositório Git JazzHub, aponte o repositório para o novo repositório no {{site.data.keyword.gitrepos}}. Em um shell de terminal, mude para o diretório no qual o repositório Git JazzHub é clonado. Insira o comando `git remote set-url`: `git remote set-url origin https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`

        Para verificar quais URLs remotas estão configuradas para quais nomes remotos, use o comando `git remote -v`. O nome remoto padrão é `origin`. Se você tiver uma configuração mais avançada, o formulário do comando será o seguinte: `git remote set-url <remote-name-that-uses-jazzhub-repo> https://git.ng.bluemix.net/<userid>/<name-of-new-repo>`
        {: tip}

3. Opcional: para explorar a maturidade de desenvolvimento do projeto, as práticas da equipe e a qualidade do código base, inclua o IBM Cloud {{site.data.keyword.DRA_short}} na sua cadeia de ferramentas. O {{site.data.keyword.DRA_short}} aplica a análise de desenvolvedor, equipe e implementação aos projetos do DevOps. Para obter mais informações, consulte [Introdução ao {{site.data.keyword.DRA_short}}](/docs/services/DevOpsInsights/index.html).

  O {{site.data.keyword.DRA_short}} está disponível somente na região Sul dos EUA.
  {: tip}


## Solucionando problemas
{: #upgrade_troubleshoot}

Se você encontrar problemas que estão relacionados ao upgrade de seu projeto, poste uma pergunta no [fórum de suporte ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/answers/questions/ask/?smartspace=devops-services){:new_window}. No post do fórum, inclua as URLs em seu projeto {{site.data.keyword.jazzhub_short}} e na cadeia de ferramentas do {{site.data.keyword.contdelivery_short}} e identifique seu post com a tag `devops-services`.


## Perguntas Mais Freqüentes
{: #upgrade_faq}

### Meu projeto JazzHub está associado à região do Reino Unido, mas minha cadeia de ferramentas está na região sul dos EUA. Como isso funciona?
{: #faq_region}

Os projetos no hub.jazz.net e as cadeias de ferramentas são ambos hospedados na região sul dos EUA. Se seu projeto foi configurado para implementar apps em uma região diferente, como a região do Reino Unido, a cadeia de ferramentas ainda implementará apps nessa região, também. Portanto, nada está realmente mudando sobre onde os dados são hospedados. As cadeias de ferramentas estarão disponíveis em mais regiões no futuro.

### O que aconteceu com meus itens de trabalho e painéis em Track &amp; Plan após o upgrade?
{: #faq_tp}

O serviço {{site.data.keyword.contdelivery_short}} fornece recursos de rastreamento de problemas por meio do {{site.data.keyword.gitrepos}}, que é hospedado pela IBM e baseado no GitLab Community Edition. O {{site.data.keyword.contdelivery_short}} também suporta integrações com outras ferramentas de planejamento e rastreamento de problemas, como GitHub Issues e JIRA.

Durante o processo de upgrade automático, seus itens de trabalho Track & Plan foram migrados para o Git Issues. O GitHub Issues e o {{site.data.keyword.gitrepos}} fornecem placas kanban e rastreamento de problemas para planejamento. Para saber mais sobre Placas de problemas, que é o recurso kanban no Git Repos and Issue Tracking, veja [Placa de problema ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/help/user/project/issue_board.md){: new_window}.

Se você requer a mesma função que o JazzHub Track &amp; Plan descontinuado, um novo serviço IBM Track and Plan on Cloud está disponível para compra em países selecionados em uma base por usuário por mês. Com esse serviço de nuvem, você obtém a função integral, equivalente a licenças do contribuidor do Rational Team Concert&trade;, em uma assinatura de nuvem de locatário único.

Esse novo serviço IBM Track and Plan on Cloud fornece muito mais capacidade do que o JazzHub Track &amp; Plan descontinuado, suportando customização do processo, hierarquias do projeto, SAFe&reg; e muitos outros métodos ágeis e híbridos, além de escalabilidade para crescer além um único projeto. Ele é baseado na versão mais recente do Rational Team Concert 6.0.3 e estará na versão 6.0.4 nos próximos 60 dias, enquanto o JazzHub Track &amp; Plan era baseado no Rational Team Concert 5.x. Uma migração de dados é possível para o IBM Track and Plan on Cloud por meio de serviços adicionais. É possível entrar em contato com [Tom Hollowell ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](mailto:trhollow@us.ibm.com){:new_window}, Connected Products SaaS Sales Leader, para obter mais informações.

Para obter informações sobre o IBM Track and Plan on Cloud ou para comprar on-line, visite [IBM Marketplace ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/us-en/marketplace/cloud-change-management){: new_window}.

Para comprar o Build Automation and Source Code Management, o [Rational Team Concert on Cloud ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/us-en/marketplace/change-and-configuration-management/purchase#product-header-top){: new_window} é uma opção.

### O que aconteceu com meu repositório de código após o upgrade?
{: #faq_repo}

Após o upgrade, seu novo serviço Git é comparável ao que você tinha antes. Se você usava o github.com com seu projeto JazzHub, sua cadeia de ferramentas será conectada ao mesmo repositório GitHub. Se o seu projeto JazzHub usava o IBM Hosted Git, o conteúdo desse repositório será clonado em um novo repositório no {{site.data.keyword.gitrepos}}, que faz parte do {{site.data.keyword.contdelivery_short}} e hospedado pela IBM.

Para obter mais informações sobre como cada tipo de repositório é tratado no processo de upgrade, veja a tabela a seguir.

|Repositório de projetos |Tipo de projeto	|Repositório de cadeias de ferramentas |
|:----------|:------------------------------|:------------------|
|github.com 		|Privado ou público 		|O mesmo repositório github.com com o {{site.data.keyword.Bluemix_notm}} Public.	|
|hub.jazz.net/git		|Privado ou público 		|Um novo repositório privado ou público no {{site.data.keyword.gitrepos}} com o {{site.data.keyword.Bluemix_notm}} Public.	|
|Jazz SCM		|Privado ou público 		|Um novo repositório privado ou público no {{site.data.keyword.gitrepos}} com o {{site.data.keyword.Bluemix_notm}} Public.	|
{: caption="Tabela 1. Repositórios de projeto mapeados para repositórios de cadeia de ferramentas" caption-side="top"}


### O que aconteceu com minhas definições de construção no meu projeto após o upgrade?
{: #faq_build}

Se você estava construindo seu código-fonte usando o Jazz em vez do Delivery Pipeline, deve-se migrar manualmente suas definições de construção para o Delivery Pipeline em sua cadeia de ferramentas.

Se você estava usando o Jazz SCM como um repositório de origem e usando o Delivery Pipeline para construir seu código, a origem no Jazz SCM foi movida automaticamente para um repositório Git. Sua configuração do Delivery Pipeline permanece igual, com a exceção de que consome a origem do repositório Git em vez da origem do Jazz SCM.

### Eu tive que criar uma organização para meu projeto do qual foi feito upgrade para uma cadeia de ferramentas, então incluí um cartão de crédito em minha conta. Meu cartão de crédito será debitado?
{: #faq_charges}

Como um [cliente Pré-pago ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud-computing/bluemix/pricing){: new_window}, se usar qualquer tempo de execução, serviço ou componente além das alocações grátis que estão listadas para ele no catálogo do {{site.data.keyword.Bluemix_notm}}, você será cobrado. Para uma estimativa de uso, veja a [folha de precificação ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/?direct=classic/&cm_mc_uid=49681106114614956310454&cm_mc_sid_50200000=1495641296&cm_mc_sid_52640000=1494981898#/pricing/cloudOEPaneId=pricing&paneId=pricingSheet){: new_window}. Para ver a precificação atual do Continuous Delivery, consulte o catálogo do [{{site.data.keyword.Bluemix_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/catalog/services/continuous-delivery){: new_window}.

Se você for um funcionário IBM, projetos IBM internos poderão ser faturados nos departamentos em vez de por meio de um cartão de crédito pessoal. Se você precisar usar recursos além das dotações grátis para funcionários IBM, crie um chamado de suporte.

### Eu não consigo localizar ou acessar minha cadeia de ferramentas. O que devo fazer?
{: #faq_find}

As cadeias de ferramentas estão hospedadas nas organizações {{site.data.keyword.Bluemix_notm}}. O processo de upgrade inclui todos os membros do projeto JazzHub na cadeia de ferramentas. Entretanto, a menos que o proprietário da organização {{site.data.keyword.Bluemix_notm}} inclua tais usuários na organização, eles não poderão ver a cadeia de ferramentas.

Para acessar sua cadeia de ferramentas, acesse {{site.data.keyword.Bluemix_notm}}, clique no ícone de menu e clique em **Serviços &gt; DevOps**. A página Cadeia de Ferramentas é aberta. Certifique-se de que você está na região Sul dos EUA e que você está na organização que contém a cadeia de ferramentas. Se sua cadeia de ferramentas não for listada na página Cadeia de Ferramentas, consulte [esta entrada da FAQ](#faq_uk).

### Meu projeto está associado à região Reino Unido. Após o upgrade, vejo mensagens de erro, meus colegas não conseguem acessar a cadeia de ferramentas e não vejo minha cadeia de ferramentas na página Cadeias de ferramentas no {{site.data.keyword.Bluemix_notm}}. O que está errado?
{: #faq_uk}

**Pergunta completa:**

Meu projeto do JazzHub está associado à região Reino Unido do {{site.data.keyword.Bluemix_notm}}, de acordo com as configurações do projeto. Verifiquei minhas configurações do projeto acessando a página de visão geral no JazzHub, clicando no ícone **Configurações**, que parece uma engrenagem, e clicando em **Opções &gt; Tornar este um Projeto {{site.data.keyword.Bluemix_notm}}: Região**. Após fazer upgrade do projeto para a cadeia de ferramentas nos EUA, ocorrem esses problemas:

   1. Quando eu seleciono a organização nos EUA, vejo uma mensagem dizendo que a organização não tem um espaço na região Sul dos EUA e é solicitado que eu crie um espaço. Não desejo executar nada nos EUA.
   
   2. Alguns de meus colegas não conseguem acessar a cadeia de ferramentas, embora estejam listados como membros no projeto do JazzHub original. Se eles tentarem abrir a cadeia de ferramentas na página de visão geral do aplicativo na região Reino Unido clicando em **Visualizar cadeia de ferramentas**, verão uma mensagem de "acesso negado".
   
   3. Eu não vejo a cadeia de ferramentas listada em minha página Cadeia de Ferramentas em [https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/devops/toolchains?env_id=ibm:yp:us-south){: new_window}, embora possa acessar a cadeia de ferramentas diretamente na página de visão geral do aplicativo na região Reino Unido clicando em **Visualizar cadeia de ferramentas**. Eu recebo um erro de que não posso modificar a cadeia de ferramentas ou recebo um erro de que não possuo nenhuma cadeia de ferramentas e preciso criar uma. 

**Resposta:**

Esses problemas podem ocorrer se você veio de uma organização do {{site.data.keyword.Bluemix_notm}} que não é dos EUA e não expandiu sua organização explicitamente para a região Sul dos EUA antes de fazer upgrade. É possível confirmar isso abrindo a página Cadeias de ferramentas. Você verá a região e a organização no início da página. 

O que aconteceu foi que, no momento do upgrade, sua organização que não é dos EUA não existia nos EUA, portanto, o upgrade selecionou outra organização para você procurando uma à qual você tem acesso.

Se você alternar para essa organização do {{site.data.keyword.Bluemix_notm}} nos EUA, poderá localizar a cadeia de ferramentas. Se você incluir seus colegas nessa organização, eles terão o acesso concedido. Esta cadeia de ferramentas pode continuar implementando sua organização que não é dos EUA. O único problema é que essas duas organizações são distintas; você não consegue executar o gerenciamento do usuário em ambas automaticamente.

Se você deseja que sua cadeia de ferramentas esteja em uma organização dos EUA que corresponda à sua organização que não é dos EUA, siga essas etapas:

   1. Efetue login em [https://console.bluemix.net ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net){: new_window} e selecione a região que não é dos EUA e a organização da qual você está vindo.
   
   2. No cabeçalho do {{site.data.keyword.Bluemix_notm}}, alterne para a região Sul dos EUA. Será solicitado que você crie um espaço nessa região.
   
   3. Crie um espaço na região Sul dos EUA para expandir sua organização para essa região. 
   
   4. Exclua a cadeia de ferramentas que foi criada por meio do processo de upgrade. 
   
      O repositório Git não é excluído automaticamente. Você pode desejar excluí-lo manualmente ou renomeá-lo agora. Se você já tiver feito mudanças nele, poderá atualizar a cadeia de ferramentas futura para usá-la posteriormente.
      {: tip}

   5. Retorne ao projeto do JazzHub. Ele deve se reconfigurar para outra tentativa de upgrade. Se ele não for reconfigurado, entre em contato com hub@jazz.net e forneça a URL do projeto.
   
   6. Reinicie o processo de upgrade e certifique-se de selecionar a organização adequada nos EUA, correspondendo o nome de sua organização na região que não é dos EUA.
   
   7. Se você manteve ou renomeou o repositório Git da tentativa de upgrade da cadeia de ferramentas anterior (consulte a etapa 4), poderá reconfigurar a placa Git em sua cadeia de ferramentas para apontar para esta URL do repositório Git. A mudança é refletida automaticamente no pipeline. Para confirmar, marque a guia Entrada no estágio Construção.
