---

copyright:
  years: 2018
lastupdated: "2018-8-2"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Gerenciando dados pessoais no Continuous Delivery
{: #cd_personal_data}

É possível modificar, exportar ou excluir dados pessoais por meio do {{site.data.keyword.contdelivery_full}}.
{: shortdesc}

Dados pessoais são quaisquer informações relacionadas a uma pessoa física ou que a identificam. Por exemplo, os dados pessoais podem ser um nome, um endereço de e-mail, um avatar, um token ou qualquer número de identificadores que são usados com o {{site.data.keyword.contdelivery_short}}. Os componentes do {{site.data.keyword.contdelivery_short}} a seguir contêm dados pessoais:

 * O Eclipse Orion {{site.data.keyword.webide}}
 * {{site.data.keyword.gitrepos}}
 * Pipelines do {{site.data.keyword.contdelivery_short}}
 * Cadeias de ferramentas e integrações de ferramentas
 * [GitHub Enterprise on IBM Cloud ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/services/ghededicated/ghe_personal_data.html){: new_window}
 * [{{site.data.keyword.DRA_full}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/services/DevOpsInsights/insights_personal_data.html){: new_window}
 
A IBM não gerencia dados no serviço {{site.data.keyword.contdelivery_short}}. Antes de deixar o serviço {{site.data.keyword.contdelivery_short}} que está hospedado no {{site.data.keyword.Bluemix_notm}} Public, deve-se excluir os seus próprios dados.
{: tip}

O {{site.data.keyword.contdelivery_short}} fornece as permissões apropriadas para gerenciar dados dentro de um grupo de recursos ou de uma organização do Cloud Foundry. Sua empresa pode ter políticas que limitam essas permissões. Se você não tiver as permissões apropriadas, entre em contato com o administrador para a sua conta do {{site.data.keyword.Bluemix_notm}}.

Para gerenciar seus dados pessoais, deve-se entender as contas do IBM Cloud, como essas contas são usadas e seus direitos de acesso associados.
 
## Contas e direitos de acesso
{: #accounts_access_rights}

Para trabalhar no IBM Cloud, deve-se efetuar login com um nome de usuário e uma senha. Ao efetuar login, o IBM Cloud associa pelo menos uma conta do IBM Cloud às suas credenciais do usuário. Quando você criar recursos como organizações do Cloud Foundry, grupos de recursos, cadeias de ferramentas e objetos do {{site.data.keyword.contdelivery_short}}, eles serão associados a uma conta do IBM Cloud.

A estrutura de login do IBM Cloud fornece a opção de trabalhar em diferentes contas. Usando a interface com o usuário do IBM Cloud, é possível alternar de uma conta para outra. Ao efetuar login, qualquer um dos tipos de contas a seguir pode ser associado às suas credenciais do usuário: 

 * Conta pessoal
 * Conta corporativa
 * Conta individual corporativa

###Contas pessoais

Geralmente, cada usuário tem sua própria conta que é a sua conta pessoal. É possível identificar facilmente sua conta pessoal, pois geralmente contém seu nome, por exemplo, *Conta do John Smith*. 

Você tem direitos totais sobre todos os objetos que são criados em sua conta pessoal. É possível convidar outros usuários a se associarem à sua conta e designar a eles direitos sobre objetos que você cria e também direitos para criar objetos em sua conta. Isso significa que os dados pessoais de outros usuários podem estar em sua conta e seus dados pessoais podem estar em contas de outros usuários. 

Se você tiver permissão para criar um objeto em uma conta, também terá o direito de modificá-lo e de excluí-lo, independentemente da conta na qual o objeto está armazenado. Quando dois usuários colaboram, eles geralmente compartilham uma conta pessoal.

###Contas corporativas

Uma conta corporativa é configurada por sua empresa. Geralmente, você é incluído automaticamente na conta, em vez de ser convidado. Contas corporativas fornecem aos usuários um local para trabalho, comunicação e compartilhamento de recursos e cobrança; no entanto, isso é apenas uma convenção. Na realidade, uma conta corporativa não é diferente de uma conta pessoal. Os objetos que são criados em uma conta corporativa estão associados à conta e os usuários podem ser convidados para a conta.

Equipes de pessoas que trabalham para uma empresa frequentemente colaboram usando uma conta corporativa.

###Contas corporativas individuais

Ao trabalhar para uma empresa, o trabalho em sua conta pode pertencer legalmente à empresa. Muitos usuários que trabalham para uma empresa têm uma conta individual corporativa. Se você efetua login em sua conta usando as credenciais que contêm o nome de sua empresa e também têm o que parece ser uma conta pessoal, o trabalho dentro de sua conta pessoal pode pertencer à empresa.

Uma conta individual corporativa não é diferente de qualquer outra conta. É possível convidar usuários para uma conta individual corporativa e os objetos que são criados em uma conta individual corporativa são de propriedade da conta.

Se você trabalha para uma empresa que possui seu trabalho, uma conta pessoal que normalmente contém seu nome é considerada uma conta individual corporativa. 

## Modificando, exportando e excluindo dados pessoais
{: #managing_personal_data}

Independentemente do tipo de conta do IBM Cloud que é usado, se você tiver direitos para os objetos na conta, será possível modificá-los, exportá-los e excluí-los. Antes de fazer mudanças, coordene com outros usuários para garantir que você não modifique nem exclua dados desnecessariamente.

Antes de excluir dados de uma conta, determine se é uma conta pessoal ou uma conta individual corporativa.

###Conta pessoal

Se você possui uma conta pessoal, é possível fazer mudanças e excluir seus dados. Se você compartilha sua conta com outro usuário, você possui os dados, mas talvez você queira entrar em contato com esse usuário sobre o trabalho compartilhado. 

Se você não pode efetuar login na sua conta do IBM Cloud, [entre em contato com o Suporte IBM ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/support){:new_window}
 
###Conta individual corporativa

Se você possui uma conta individual corporativa, deve-se coordenar quaisquer mudanças com sua empresa e com outros membros de sua equipe. Exclua seus dados pessoais, independentemente se eles estão armazenados em uma conta corporativa ou em uma conta corporativa individual. Certifique-se de que você não exclua o trabalho que você compartilhou com outros usuários.

Antes de começar a gerenciar seus dados pessoais para os componentes do {{site.data.keyword.contdelivery_short}}, certifique-se de que você está trabalhando em sua conta do IBM Cloud. Para visualizar a conta do IBM Cloud na qual você está trabalhando atualmente, na barra de menus, clique no avatar do seu perfil. 

Se não for possível efetuar login na sua conta do IBM Cloud, entre em contato com a empresa e trabalhe com eles para excluir seus dados pessoais.

Se você desejar excluir todos os seus dados pessoais do {{site.data.keyword.contdelivery_short}}, a ordem na qual você excluir esses dados será importante. Primeiramente, exclua todas as áreas de trabalho do {{site.data.keyword.webide}}. Em seguida, exclua seus dados do {{site.data.keyword.gitrepos}} e, então, exclua sua conta do {{site.data.keyword.gitrepos}}. Finalmente, exclua seus pipelines de entrega, suas integrações de ferramentas e suas cadeias de ferramentas.
{: tip}

## Exportando e excluindo dados do Web IDE
{: #managing_web_ide_data}

O {{site.data.keyword.webide}} fornece uma área de trabalho pessoal na nuvem. É possível usar o {{site.data.keyword.webide}} para clonar repositórios Git e arquivos de edição. Você possui a área de trabalho do {{site.data.keyword.webide}}; ela não é compartilhada por nenhuma outra conta.

Antes de excluir os seus dados do {{site.data.keyword.webide}}, talvez você queira exportar o seu trabalho. Depois de excluir suas áreas de trabalho, elas são removidas do {{site.data.keyword.contdelivery_short}} e todos os arquivos são excluídos.
{: tip}

###Exportando uma área de trabalho do Web IDE

Para exportar uma área de trabalho do {{site.data.keyword.webide}}:

1. Selecione **Arquivo > Exportar > Zip**.
1. Repita para cada área de trabalho que você deseja exportar.

###Excluindo suas áreas de trabalho do Web IDE

Para excluir suas áreas de trabalho do {{site.data.keyword.webide}}, incluindo todos seus dados pessoais:

1. De qualquer cadeia de ferramentas, navegue para o {{site.data.keyword.webide}}.
1. Clique no ícone **Configurações** <img class="inline" src="images/webide_settings_icon_light_small.png" alt="O ícone de configurações"> na barra lateral de navegação à esquerda.
1. Clique em **PERFIL DO USUÁRIO**.
1. Clique em **Excluir** para remover todos os seus dados do {{site.data.keyword.webide}}.

O {{site.data.keyword.webide}} usa um mecanismo de conexão única. Na primeira vez em que você acessa essa integração de ferramenta, uma conta do {{site.data.keyword.webide}} correspondente, porém oculta é criada para sua conta do IBM Cloud. Depois de excluir todas as suas áreas de trabalho, não acesse o {{site.data.keyword.webide}}. Se você acessar o {{site.data.keyword.webide}} novamente, uma nova conta será criada automaticamente, que deverá ser excluída.
{: tip}

## Modificando, exportando e excluindo dados do Git Repos and Issue Tracking
{: #managing_grit_data}

O {{site.data.keyword.gitrepos}} fornece um serviço Git hospedado na nuvem. Um mecanismo de conexão única é usado para associar sua conta do IBM Cloud a uma conta do Git. Um nome completo e um nome abreviado são criados para você na sua conta do Git. Outros usuários poderão usar seu nome abreviado para referir-se a você em um comentário dentro de um problema do Git. É possível customizar sua conta do Git e incluir dados pessoais, como uma descrição de si mesmo ou uma imagem. 

O {{site.data.keyword.gitrepos}} fornece um ambiente de codificação social poderoso, porém complexo no qual os usuários contribuem com diferentes projetos e os objetos são compartilhados. Esse ambiente pode dificultar a localização e a exclusão de seus dados pessoais.

Seus perfis e configurações da conta, projetos pessoais, grupos e fragmentos estão associados à sua conta do Git. Se você excluir sua conta do Git, esses objetos serão excluídos. Para excluir dados pessoais em outro projeto, navegue até o projeto e, em seguida, modifique-o para remover seus dados pessoais ou excluir o projeto inteiramente. Certifique-se de que você coordene com outros membros da sua equipe antes de excluir projetos compartilhados.

Antes de excluir a sua conta do Git, exclua os seus dados pessoais de outros projetos. Depois de excluir sua conta do Git, pode ser difícil ou impossível localizar todos os projetos para os quais você contribuiu.
{: tip}

###Projetos pessoais e compartilhados

É possível convidar outros usuários para colaborar em projetos. Os projetos Git que você cria dentro de sua conta são chamados de projetos pessoais. Também é possível criar grupos do Git nos quais os projetos podem ser de propriedade de múltiplos proprietários do Git. É possível criar novos projetos para o grupo ou transferir a propriedade de projetos pessoais para o grupo. Um grupo Git é frequentemente usado para representar uma conta corporativa do IBM Cloud para indicar a propriedade de projetos pela corporação.

###Exportando um projeto do Git Repos and Issue Tracking

Antes de excluir um projeto do {{site.data.keyword.gitrepos}}, é possível exportar o projeto para arquivá-lo. 

1. Clique no ícone **Configurações** <img class="inline" src="images/webide_settings_icon_light_small.png" alt="O ícone de configurações"> na barra lateral de navegação à esquerda.
1. Clique em **Geral**.
1. Clique em **Expandir** para expandir a seção Exportar projeto.
1. Clique em **Exportar projeto**.

Depois que o projeto é arquivado, ele pode ser importado para outra instância do GitLab. 

###Excluindo sua conta do Git Repos and Issue Tracking

É possível excluir sua conta do {{site.data.keyword.gitrepos}} e tudo o que pertence a essa conta.

1. No painel Configurações do usuário do {{site.data.keyword.gitrepos}}, na página [Conta ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/profile/account?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window}, na seção Excluir conta, clique em **Excluir conta**.
1. Todos os projetos do Git, incluindo repositórios e problemas são excluídos. Você também é removido de quaisquer grupos do {{site.data.keyword.gitrepos}} aos quais você pertence.

Após a sua conta ser excluída, algum conteúdo permanecerá. Esse conteúdo será designado para um Usuário fantasma em todo o sistema Para obter mais informações sobre como excluir uma conta do {{site.data.keyword.gitrepos}}, consulte [Excluindo uma conta do usuário ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/profile/account/delete_account#associated-records){:new_window}.
{: tip}

O {{site.data.keyword.gitrepos}} usa um mecanismo de conexão única que cria automaticamente uma conta do Git correspondente para a sua conta do IBM Cloud na primeira vez que você acessar a integração da ferramenta. Depois de excluir sua conta, não acesse o {{site.data.keyword.gitrepos}}. Se você acessar o {{site.data.keyword.gitrepos}} novamente, uma nova conta será criada automaticamente, que deverá ser excluída.
{: tip}

## Modificando, exportando e excluindo dados do pipeline de Entrega contínua
{: #managing_pipeline_data}

Os pipelines do {{site.data.keyword.contdelivery_short}} executam scripts para construir, testar e implementar seu aplicativo no IBM Cloud. Para fazer isso, os pipelines fornecem estágios, tarefas, variáveis de ambiente e outros objetos que podem conter dados pessoais. É possível excluir esses objetos individualmente ou excluir um pipeline inteiro.

Certifique-se de que você coordene com outros membros da sua equipe antes de excluir objetos ou pipelines compartilhados. A exclusão de um estágio pode fazer com que um pipeline falhe.

Um pipeline não pode existir fora de uma cadeia de ferramentas. Se você excluir uma cadeia de ferramentas, todos os pipelines que estiverem associados à cadeia de ferramentas também serão excluídos. Se você planeja excluir uma cadeia de ferramentas inteira, não é necessário excluir cada pipeline individualmente. Em vez disso, acesse a seção "Modificando e excluindo as cadeias de ferramentas e integrações de ferramentas" e siga as etapas para excluir uma cadeia de ferramentas.
{: tip}

Os estágios de pipeline podem incluir dados pessoais, como credenciais na forma de propriedades de ambiente e uma definição de pipeline que mostra o estado atual do pipeline. Estágios também podem incluir scripts dentro de tarefas que você deseja modificar ou excluir, bem como artefatos e logs para as execuções de pipeline mais recentes que você deseja exportar. Use as ações Configurar Estágio ou Excluir Estágio para modificar ou excluir um estágio. Use a ação Download para exportar artefatos ou logs de um estágio.

  ![Menu de estágios](images/pipeline_stages.png)

###Modificando um Estágio de Pi

Para modificar um estágio de pipeline:

1. Na página Pipeline, clique no ícone **Configurações**.
1. Clique em **Configurar estágio**.
1. Na guia **PROPRIEDADES DO AMBIENTE**, edite ou exclua propriedades.
1. Modifique um script de tarefa no estágio de pipeline. Selecione a tarefa e mude os valores que façam parte da Configuração de Construção, Implementação ou Teste.
   
   ![Modificar script da tarefa](images/job_script.png)
  
1. Excluir uma tarefa do estágio de pipeline. Na guia **TAREFAS**, selecione a tarefa que deseja excluir e clique em **Remover**.
 
###Exportando um Estágio de Pipel

Para exportar a definição para um estágio de pipeline, anexe `/yaml` à URL do pipeline:

` http (s): //<DevOps Services domain>/pipeline/user/project/yaml `


Para exportar artefatos e logs para um estágio de pipeline:

1. Na página Pipeline, clique em **Visualizar logs e histórico**.
1. Clique no número da construção para o qual você deseja exportar artefatos e logs.
1. Clique em **DOWNLOAD** > **Artefatos** para exportar os artefatos para a compilação selecionada.
1. Clique em **DOWNLOAD** > **Logs** para exportar os logs para a compilação selecionada.  

###Excluindo um Estágio de Pipel

Para excluir um estágio de pipeline:

1. Na página Pipeline, clique no ícone **Configurações**.
1. Clique em **Excluir estágio**.

## Modificando e excluindo cadeias de ferramentas e integrações de ferramentas
{: #managing_toolchains}

Usando cadeias de ferramentas, as equipes podem colaborar com e compartilhar integrações de ferramenta diferentes. 

É recomendado que você configure todas as integrações do {{site.data.keyword.contdelivery_short}} usando dados que estejam associados à sua equipe ou empresa, em vez de dados que estejam associados a você. No entanto, em algumas instâncias, seus dados pessoais podem ser usados inadvertidamente. Nesses casos, deve-se identificar todos os dados que você possui e excluí-los.

Quando uma integração de ferramenta é criada, o {{site.data.keyword.contdelivery_short}} não pode registrar a origem de todos os dados. Por exemplo, outro membro da equipe pode criar uma integração de ferramenta para você usando dados pessoais que você fornece em um e-mail. Deve-se entender quais dados você possui e certificar-se de que eles são excluídos.

Coordene com outros membros de sua equipe antes de excluir integrações de ferramentas ou cadeias de ferramentas compartilhadas.

###Modificando e excluindo integrações de ferramentas

Ao criar uma integração de ferramenta, você é obrigado a fornecer credenciais do usuário e outras informações de conta que pertençam à integração. Se você usou suas próprias credenciais pessoais e informações de conta, substitua essas informações por valores diferentes ou exclua a integração de ferramenta.

Para modificar uma integração de ferramenta:

1. No cartão da ferramenta, clique no menu para acessar as opções de configuração.

  ![Menu de configuração da ferramenta](images/toolchain_tile_menu.png)

1. Quando tiver finalizado a atualização das configurações, clique em **Salvar integração**.

Para excluir uma integração de ferramenta:

1. Para excluir uma integração de ferramenta por meio de sua cadeia de ferramentas, clique em **Excluir**.
1. Confirme clicando em **Excluir**.

###Excluindo cadeias de ferramentas

Quando você excluir uma cadeia de ferramentas, a exclusão não poderá ser desfeita.

1. No painel do DevOps, na página **Cadeias de ferramentas**, clique na cadeia de ferramentas a ser excluída. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas**.
1. Clique no menu **Mais ações**, que está próximo a **Visualizar app**.
1. Clique em **Excluir**. A exclusão de uma cadeia de ferramentas remove todas as suas integrações de ferramenta, incluindo pipelines, podendo excluir recursos que sejam gerenciados por essas integrações.
1. Confirme a exclusão digitando o nome da cadeia de ferramentas e clicando em **Excluir**. 

Quando você excluir uma cadeia de ferramentas, os repositórios do {{site.data.keyword.gitrepos}} não serão excluídos. Os usuários que tiverem acesso àqueles repositórios poderão ter cópias dos dados se eles executaram um `git clone` ou criaram uma área de trabalho {{site.data.keyword.webide}}. Para certificar-se de que todos os dados sejam excluídos, deve-se solicitar que esses usuários excluam as suas cópias dos dados.
{: tip}

###Excluindo todas as cadeias de ferramentas

Não é possível excluir todas as cadeias de ferramentas dentro de um grupo de recursos ou uma organização ao mesmo tempo. Deve-se excluir cada cadeia de ferramentas por vez.

As cadeias de ferramentas têm escopo definido por região do IBM Cloud e grupo de recursos ou organização do Cloud Foundry. Certifique-se de selecionar cada região e grupo de recursos ou organização dentro da região para excluir cada cadeia de ferramentas que você criou.
{: tip}
