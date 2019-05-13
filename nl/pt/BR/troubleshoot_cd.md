---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-11"

keywords: troubleshoot, IBM Cloud Continuous Delivery

subcollection: ContinuousDelivery

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:tip: .tip}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# Resolução de problemas para o  {{site.data.keyword.contdelivery_short}}
{: #troubleshoot-cd}

Os problemas gerais com o uso do {{site.data.keyword.contdelivery_full}} podem incluir a autenticação do GitHub, a criação de pipeline, a configuração de integração de ferramenta ou os problemas do Cloud Foundry. Em muitos casos, é possível recuperar-se desses problemas seguindo algumas etapas simples.
{:shortdesc}

## Eu tentei incluir a integração de ferramenta GitHub em minha cadeia de ferramentas, por que a
integração de ferramenta não estava incluída?
{: troubleshoot-cannot-authorize-github}
{: troubleshoot}

Deve-se obter autorização com o GitHub para que o {{site.data.keyword.Bluemix_notm}} seja autorizado a acessar sua conta do GitHub.

A integração de ferramenta do GitHub não foi incluída em sua cadeia de ferramentas.
{: tsSymptoms}

Se o {{site.data.keyword.Bluemix_notm}} não estiver autorizado a acessar sua conta do GitHub, a
integração de ferramenta não será incluída em sua cadeia de ferramentas.
{: tsCauses}

Se você estiver configurando a integração de ferramenta GitHub enquanto estiver criando sua cadeia de
ferramentas, siga estas etapas para autorizar com o GitHub:
{: tsResolve}

  1. Na seção Integrações configuráveis, clique em **GitHub**.
  1. Se você estiver criando a cadeia de ferramentas no {{site.data.keyword.Bluemix_notm}} Public e o {{site.data.keyword.Bluemix_notm}} não estiver autorizado a acessar o GitHub, clique em **Autorizar** para acessar o website GitHub.
  1. Se você não tiver uma sessão do GitHub ativa, será solicitado a efetuar login. Clique em **Autorizar aplicativo** para permitir que o {{site.data.keyword.Bluemix_notm}} acesse sua conta GitHub.

Se você já tiver uma cadeia de ferramentas, atualize a configuração da integração de ferramenta GitHub:

 1. No painel do DevOps, na página **Cadeias de ferramentas**, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, clique em **Visão geral**.
 1. No cartão GitHub, clique no menu e, em seguida, em **Configurar**.
 1. Atualize as definições de configuração para autorizar o {{site.data.keyword.Bluemix_notm}} a acessar o GitHub. Clique em **Autorizar** para acessar o website do GitHub. Se você não tiver uma sessão do GitHub ativa, será solicitado a efetuar login. Clique em **Autorizar aplicativo** para permitir que o {{site.data.keyword.Bluemix_notm}} acesse sua conta GitHub.
 1. Quando tiver finalizado a atualização das configurações, clique em **Salvar integração**.
 

## Por que não é possível usar a integração de ferramenta do {{site.data.keyword.gitrepos}} em minha cadeia de ferramentas de uma região em uma cadeia de ferramentas dentro de uma região diferente?
{: troubleshoot-cd-grit-integration}
{: troubleshoot}

Não é possível usar uma instância do {{site.data.keyword.gitrepos}} em várias regiões.

Quando tento incluir a integração de ferramenta do {{site.data.keyword.gitrepos}} em minha cadeia de ferramentas, recebo a mensagem de erro a seguir:
{: tsSymptoms}

`Repository URL is not valid. The repository must be on {local GitLab URL}.`

Em que `{local GitLab URL}` é a URL da integração de ferramenta do {{site.data.keyword.gitrepos}} na região em que a cadeia de ferramentas reside.
   
Como o {{site.data.keyword.gitrepos}} está totalmente integrado ao serviço {{site.data.keyword.contdelivery_short}} na região na qual eles estão em execução, não é possível usar uma instância do {{site.data.keyword.gitrepos}} em várias regiões.
{: tsCauses}

Em vez de criar uma integração de ferramenta do {{site.data.keyword.gitrepos}}, crie uma integração de GitLab genérica e use essa integração para apontar para o repositório (repo) do {{site.data.keyword.gitrepos}} em uma região diferente.
{: tsResolve}

1. No painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas na qual você deseja incluir essa integração. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, em **Visão geral**.
1. Clique em **Incluir uma ferramenta**.
1. Na seção Integrações de ferramentas, clique em **GitLab**.
1. Clique no servidor GitLab que você deseja usar. Se o servidor GitLab no qual o repositório que você deseja acessar reside não aparecer nessa lista, inclua um servidor customizado:

 a. Clique em **Incluir servidor customizado**.

 b. Digite um nome para o servidor. Esse nome do servidor aparecerá na lista de servidores GitLab disponíveis.
 
 c. Digite a URL raiz do servidor GitLab customizado.
 
 d. Insira um token de acesso pessoal para seu servidor GitLab customizado. Se você não tiver um token de acesso pessoal, [crie um](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat).
 
 e. Clique em **Salvar integração customizada**.
 
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

Para obter mais informações sobre como configurar uma integração de ferramenta do GitLab, consulte [Configurando o GitLab](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#gitlab).


## Por que não é possível criar uma cadeia de ferramentas por meio de um modelo que usa um repositório privado em uma região diferente?
{: troubleshoot-cd-grit-integration-private}
{: troubleshoot}

O modelo de cadeia de ferramentas que você está usando faz referência a um repositório privado do {{site.data.keyword.gitrepos}}.

O {{site.data.keyword.gitrepos}} é específico da região. Quando você tenta criar uma cadeia de ferramentas usando um modelo e coloca como destino uma região na qual o repositório privado não está localizado, a configuração de integração do Git falha.
{: tsSymptoms}
   
Quando você inclui um repositório do {{site.data.keyword.gitrepos}} em uma cadeia de ferramentas em uma região específica, seu IBMid é mapeado para um nome de usuário do GitLab que fornece acesso ao GitLab nessa região. Mesmo que seu nome de usuário do GitLab pareça igual em todas as regiões, o usuário do GitLab associado é diferente em cada região, porque cada região tem uma instalação separada do GitLab. O acesso aos usuários do GitLab em outras regiões não é concedido automaticamente às cadeias de ferramentas, mesmo quando o nome do usuário do GitLab parece ser o mesmo.
{: tsCauses}

Torne repositório do {{site.data.keyword.gitrepos}} público para que ele possa ser acessado de qualquer lugar, incluindo outras regiões do {{site.data.keyword.Bluemix_notm}}.
{: tsResolve}

Caso o repositório tenha que ser privado, seu proprietário poderá conceder acesso a ele, criando um [token de acesso pessoal](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat) no servidor GitLab no qual o repositório de origem está localizado. É necessário ter acesso apenas ao repositório privado para clonar o conteúdo durante a criação da cadeia de ferramentas. O token de acesso pessoal pode ser criado com uma data de validade para limitar seu tempo de vida para expirar após um dia. 

Depois de ter um token de acesso pessoal, será possível criar uma URL para acessar o repositório de outras regiões. Enquanto você estiver configurando a integração de ferramenta, no campo **URL do repositório de origem**, atualize a URL do repositório para usar seu nome de usuário e token de acesso.

`https://user:XXXXXXX@git.ng.bluemix.net/group/node-hello-world`

Em que `user` é o nome do usuário do GitLab, `XXXXXXX` é o token de acesso, [`group`![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/help/user/group/index.md){:new_window} é o grupo no qual o repositório está armazenado e `node-hello-world` é o nome do repositório.

Se o seu repositório do GitLab não estiver localizado em um grupo do GitLab, o valor de `group` será o mesmo que seu nome do usuário.
{: tip}


## Por que não é possível clonar meu repositório do {{site.data.keyword.gitrepos}} por https?
{: #troubleshoot-grit-clone-repo}
{: troubleshoot}

Deve-se usar um token de acesso pessoal ou uma chave SSH para executar operações do Git.

Você tenta enviar por push ou clonar um repositório por meio da linha de comandos usando https e não consegue autenticar, mesmo que tenha inserido a senha correta.
{: tsSymptoms}
   
O {{site.data.keyword.gitrepos}} usa um mecanismo de conexão única que não suporta a autenticação de Git que usa um nome de usuário e uma senha na linha de comandos.
{: tsCauses}

Para executar operações do Git, como clonar ou enviar por push, deve-se usar um token de acesso pessoal ou uma chave SSH. Para obter mais informações sobre como criar um token de acesso pessoal ou uma chave SSH, consulte o [Tutorial de introdução](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication).
{: tsResolve}

## Por que a autenticação é solicitada quando tento clonar o meu repositório do {{site.data.keyword.gitrepos}} usando SSH?
{: troubleshoot-cd-grit-ssh}
{: troubleshoot}

Pode haver problemas com o local ou as permissões para sua chave SSH privada, ou a linha de comandos do Git pode não estar usando sua chave SSH privada para autenticar com o {{site.data.keyword.gitrepos}}.

Eu incluí a chave pública SSH por meio da interface com o usuário do {{site.data.keyword.gitrepos}}. Quando tento clonar um repositório usando o SSH, uma senha ou um código de segurança é solicitado ou uma mensagem de erro é exibida indicando que a autenticação falhou.
{: tsSymptoms}
   
Qualquer um dos problemas de SSH a seguir pode solicitar que você autentique ou exibir uma mensagem de erro:
{: tsCauses}

* A linha de comandos do Git pode não estar usando a chave SSH privada para autenticar com o {{site.data.keyword.gitrepos}}.

* Sua chave SSH privada pode não estar no local ~/.ssh/id_rsa padrão.

* Sua chave SSH privada pode não ter as permissões corretas (600).


Use qualquer um dos métodos a seguir para resolver esse problema:
{: tsResolve}

* Se você usar o local da chave SSH privada padrão, verifique as permissões para a pasta ~/.ssh/ e o arquivo de chave privado ~/.ssh/id_rsa. Se as permissões forem muito amplas, por padrão, o SSH não usará uma chave privada. Certifique-se de que as permissões para a pasta ~/.ssh/ estejam configuradas como 700 e as permissões para a pasta ~/.ssh/id_rsa sejam configuradas como 600.

* Se a sua chave privada não estiver no local padrão, use o comando a seguir para especificá-la em uma variável de ambiente:

`GIT_SSH_COMMAND='ssh -i/path/to/private_key_file' git clone git@host:owner/repo.git`

* Para depurar esse problema usando informações de conexão, inclua o sinalizador -v ou -vvv na variável de ambiente `GIT_SSH_COMMAND`:

`GIT_SSH_COMMAND='ssh -vvv git clone git@host:owner/repo.git`

`GIT_SSH_COMMAND='ssh -vvv -i/path/to/private_key_file' git clone git@host:owner/repo.git`


## Tentei incluir um usuário no meu projeto do GitLab por meio do e-mail, mas ele não recebeu o convite. Como posso incluí-lo em meu projeto?
{: #troubleshoot-gitlab-add-user}
{: troubleshoot}

O convite pode ser bloqueado pelo e-mail do usuário.

Convidei um usuário para o meu projeto do GitLab usando seu endereço de e-mail que está listado no {{site.data.keyword.gitrepos}}, mas ele não recebeu o e-mail.
{: tsSymptoms}
   
O e-mail pode ser bloqueado na caixa de entrada do usuário por filtros de spam.
{: tsCauses}

É possível usar qualquer um dos métodos a seguir para resolver esse problema:
{: tsResolve}

* Verifique sua pasta de spam de e-mail para determinar se o convite por e-mail foi marcado como spam. Os e-mails são enviados de um endereço noreply@. Atualize seus filtros de spam para permitir e-mails desse endereço.

* Investigue se os filtros de spam corporativos que estão fora do controle do usuário estão bloqueando o e-mail. Solicite ao usuário que efetue login na interface com o usuário do {{site.data.keyword.gitrepos}} e que envie sua identificação de usuário. É possível incluir o usuário no projeto do GitLab usando sua identificação de usuário.


## Por que o pipeline não é criado corretamente quando eu crio uma cadeia de ferramentas por meio do modelo que estou escrevendo? 
{: troubleshoot-cd-pipeline-creation}
{: troubleshoot}

Seu pipeline pode ter recursos ausentes, como tarefas e estágios, devido a um erro em sua definição de pipeline.yaml.

Quando eu tento criar uma cadeia de ferramentas por meio de um modelo que estou escrevendo, recebo a mensagem de erro a seguir na página Pipeline:
{: tsSymptoms}

`This pipeline was created, but might be missing jobs, stages, or other resources. You can use this pipeline, or if you prefer, you can delete it and create another pipeline.`

Normalmente, esse problema é causado por um erro em sua definição de pipeline.yaml.
{: tsCauses}
   
É possível usar qualquer um dos métodos a seguir para depurar esse erro:
{: tsResolve}

* Use a interface com o usuário do pipeline para criar um pipeline de exemplo que replique o pipeline que você está tentando construir com seu modelo. Anexe `/yaml` à URL do pipeline para gerar um arquivo pipeline.yaml semelhante que pode ser usado para procurar diferenças óbvias. Por exemplo, `https://cloud.ibm.com/devops/pipelines/<your pipeline id>/yaml?env_id=<your region>`.

* Use o mecanismo de criação da cadeia de ferramentas sem interface com o usuário. Na página **Criar uma cadeia de ferramentas**, abra o depurador e avalie a expressão `window.Testflags = {nocreate: 1}`. Quando você clica em **Criar uma cadeia de ferramentas** nesse modo, a cadeia de ferramentas não é criada. Em vez disso, as informações que são passadas para a API são retornadas para o console no qual é possível revisá-las.


## Eu configurei uma integração de ferramenta para minha cadeia de ferramentas, por que ela não estava configurada?
{: troubleshoot-tool-integration-error}
{: troubleshoot}

Se ocorrer um erro durante o processo de configuração ou se a comunicação entre a cadeia de ferramentas e a ferramenta não for concluída corretamente, a configuração falhará.

Depois de incluir e configurar uma integração de ferramenta para sua cadeia de ferramentas, uma mensagem de erro será exibida para indicar que a configuração falhou.
{: tsSymptoms}

Quando você inclui uma integração de ferramenta, a cadeia de ferramentas se comunica com a ferramenta que é representada pela integração de ferramenta para provisionar quaisquer recursos necessários e associá-los à cadeia de ferramentas. Se ocorrer um erro durante o processo de configuração ou se a comunicação entre a cadeia de ferramentas e a ferramenta não for concluída corretamente, a integração de ferramenta será colocada em um estado de erro.
{: tsCauses}

 ![Erro de configuração com falha](images/tool_setup_failed.png)

É possível tentar configurar a integração de ferramenta novamente:
{: tsResolve}

1. Em seu cartão de ferramenta, passe o mouse sobre a mensagem `Falha na configuração` e clique em **Reconfigurar**.

 ![Botão Reconfigurar](images/tool_reconfigure.png)

1. Certifique-se de que esteja usando parâmetros de configuração válidos. Se o erro tiver sido causado por uma configuração inválida, uma mensagem de erro será exibida; por exemplo, `A integração não pôde ser configurada. Verifique as configurações e tente novamente. Motivo: api_key:fakeKey inválida`. Atualize as configurações da integração de ferramenta e clique em **Salvar integração**.
1. Se o erro tiver sido causado por um problema de comunicação, clique em **Salvar integração** para tentar novamente.


## Por que não é possível incluir o {{site.data.keyword.contdelivery_short}} em uma organização do Cloud Foundry?
{: troubleshoot-resource_groups}
{: troubleshoot}

Não é mais possível criar instâncias do serviço {{site.data.keyword.contdelivery_short}} nas organizações do Cloud Foundry. 

A mensagem a seguir é exibida na página Cadeias de ferramentas para sua cadeia de ferramentas em uma organização do Cloud Foundry:
{: tsSymptoms}

`Continuous Delivery service required: Add the service to your organization to ensure uninterrupted use of the service capabilities.` 

Quando você clica em **Incluir o serviço**, não há opção para criar o {{site.data.keyword.contdelivery_short}} em uma organização do Cloud Foundry. É possível criar o {{site.data.keyword.contdelivery_short}} apenas em um grupo de recursos.

Os grupos de recursos substituíram as organizações do Cloud Foundry como os contêineres preferenciais para instâncias de serviço. No entanto, ainda é possível criar cadeias de ferramentas em organizações do Cloud Foundry para suportar instâncias pré-existentes do {{site.data.keyword.contdelivery_short}} nas organizações do Cloud Foundry.
{: tsCauses}

Crie sua cadeia de ferramentas novamente em grupos de recursos e, em seguida, remova a cadeia de ferramentas original do organização do Cloud Foundry. Como alternativa, é possível ignorar a mensagem de erro até que um método para migrar cadeias de ferramentas existentes de organizações do Cloud Foundry para grupos de recursos seja fornecido.
{: tsResolve}


## Por que não é possível excluir as cadeias de ferramentas usando a CLI `ibmcloud`?
{: troubleshoot-delete_toolchains_cli}
{: troubleshoot}

Atualmente, não é possível excluir as cadeias de ferramentas usando a CLI ibmcloud resource. 

Tentei excluir uma cadeia de ferramentas por meio da linha de comandos usando o comando `ibmcloud resource service-instance-delete` e o comando falhou com a mensagem de erro a seguir:
{: tsSymptoms}

`Error Code: RC-ServiceBrokerErrorResponse
Message: description : Toolchain delete must be performed from the toolchain dashboard`

As cadeias de ferramentas são um tipo especial de recurso na plataforma de nuvem que não pode ser excluído no momento usando a CLI `ibmcloud resource`.
{: tsCauses}

Para excluir uma cadeia de ferramentas:
{: tsResolve}

1. No painel do DevOps, na página **Cadeias de ferramentas**, clique na cadeia de ferramentas a ser excluída. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas**.
1. Clique no menu **Mais ações**, que está próximo a **Visualizar app**.
1. Clique em **Excluir**. Excluir uma cadeia de ferramentas remove todas as suas integrações de ferramenta, que pode excluir recursos que são gerenciados por essas integrações.
1. Confirme a exclusão digitando o nome da cadeia de ferramentas e clicando em **Excluir**.  


## Por que o Live Edit fica indisponível depois que eu confirmo e envio por push para um repositório?
{: #troubleshoot-liveedit}
{: troubleshoot}

Quando você implementa fora do Eclipse Orion {{site.data.keyword.webide}}, o modo Live Edit é limpo.

Você confirma e envia por push uma mudança por meio da linha de comandos ou {{site.data.keyword.webide}} e o Live Edit fica indisponível.
{: tsSymptoms}
   
Quando você cria uma cadeia de ferramentas que contém um pipeline do {{site.data.keyword.contdelivery_short}} e do {{site.data.keyword.webide}}, ambas as integrações de ferramentas podem implementar seu aplicativo (app). Por padrão, tanto o pipeline quanto o {{site.data.keyword.webide}} são implementados na mesma organização e espaço do Cloud Foundry, usando o mesmo aplicativo e URL do Cloud Foundry. Quando você implementa fora do {{site.data.keyword.webide}}, o modo Live Edit é limpo.
{: tsCauses}

Para desenvolver rapidamente uma versão de teste de seu aplicativo usando o Live Edit, implemente em um aplicativo, espaço e URL diferentes do Cloud Foundry do {{site.data.keyword.webide}}. Quando as mudanças de código forem concluídas, será possível confirmar e enviar por push o código para acionar o pipeline para construir e implementar a versão de produção de seu aplicativo.
{: tsResolve}

1. Na barra de execução, selecione a configuração de ativação que você deseja editar.
2. Edite os valores que são especificados para Espaço e Host.
3. Clique em **Salvar** e em **Sair**.
4. Clique no botão **Executar** na barra de execução. Pode ser necessário implementar várias vezes para ativar o botão Live Edit.

Para obter mais informações sobre o Live Edit, consulte [Live Edit](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-live-syn#live-edit).


## O que "não sincronizado" significa na barra de execução do {{site.data.keyword.webide}}?
{: #troubleshoot-web-ide-sync}
{: troubleshoot}

O sistema de arquivos em sua área de trabalho está fora de sincronização.

No modo Live Edit, o {{site.data.keyword.webide}} sincroniza arquivos de sua área de trabalho com o aplicativo Cloud Foundry em execução e os arquivos estão fora de sincronização.
{: tsSymptoms}
   
O sistema de arquivos em sua área de trabalho poderá ficar fora de sincronização se o aplicativo for modificado fora do {{site.data.keyword.webide}}. Ele também poderá ficar fora de sincronização se o {{site.data.keyword.webide}} não puder recuperar o estado de sincronização do aplicativo.
{: tsCauses}

O estado pode ser limpo após um minuto ou dois, quando as comunicações normais são reestabelecidas e os arquivos são sincronizados. Caso contrário, é possível iniciar e parar o aplicativo com o modo Live Edit ativado.
{: tsResolve}
