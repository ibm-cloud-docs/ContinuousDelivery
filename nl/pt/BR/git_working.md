---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-20"

keywords: Git Repos, Issue Tracking, Collaborate, Git repository

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# {{site.data.keyword.gitrepos}}
{: #git_working}

Colabore com sua equipe e gerencie seu código-fonte com um repositório Git (repo) e o rastreador de problemas que é hospedado pela IBM e desenvolvido com [GitLab Community Edition](https://about.gitlab.com/){: external}.
{: shortdesc}

Convide somente pessoas com as quais você tem um relacionamento pessoal ou de negócio para colaborar em um projeto. Os usuários que usam um convite para um repositório Git para propósitos diferentes de colaborar em um projeto podem ter seu acesso ao serviço suspenso ou revogado.
{: important}

Tanto o GitHub quanto a linha de comandos do Git são alternativas acessíveis para o GitLab.
{: note}

Não armazene dados regulados em arquivos ou problemas dentro de repositórios Git. Os procedimentos para os dados regulados não estão atualmente em vigor.
{: tip}

A integração da ferramenta {{site.data.keyword.gitrepos}} suporta que as equipes gerenciem código e colaborem de várias maneiras:
   * Gerenciar o repositório Git por meio de controles de acesso de baixa granularidade que mantêm o código seguro
   * Revisar o código e aprimorar a colaboração por meio de solicitações de mesclagem
   * Rastrear problemas e compartilhar ideias por meio do rastreador de problemas
   * Documentar projetos no sistema de wikis

Como essa integração de ferramenta é construída no GitLab Community Edition e hospedada pela IBM no {{site.data.keyword.Bluemix_notm}} Platform, algumas opções do GitLab não estão disponíveis. Por exemplo, o Delivery Pipeline fornece integração contínua e entrega contínua para
o {{site.data.keyword.Bluemix_notm}}; portanto, os recursos de integração contínua no GitLab não são
suportados. Além disso, as funções de administração não estão disponíveis porque são gerenciadas pela IBM.
{: tip}


## Usando o {{site.data.keyword.gitrepos}} localmente
{: #git_locally}

É possível acessar localmente os repositórios Git que são armazenados no {{site.data.keyword.gitrepos}}. Para obter instruções para configurar o Git localmente, consulte [Comece a usar o Git usando a linha de comandos](https://us-south.git.cloud.ibm.com/help/gitlab-basics/start-using-git){: external}.

O {{site.data.keyword.gitrepos}} suporta apenas conexões de HTTPS que usem o TLS1.2. Se você usa o Eclipse para se conectar, pode ser necessário especificar esse protocolo para sua versão Java&trade; incluindo `-Dhttps.protocols=TLSv1.2` em seu arquivo eclipse.ini e, em seguida, reiniciando o Eclipse.
{: tip}

## Autenticando com o {{site.data.keyword.gitrepos}}
{: #git_authentication}

Seu login e senha do {{site.data.keyword.Bluemix_notm}} são usados somente para autenticar com o {{site.data.keyword.gitrepos}} em um navegador da web. Não é possível usar as credenciais do usuário do {{site.data.keyword.Bluemix_notm}} para autenticar de clientes Git externos. Para concluir operações do Git remoto, como `clone` ou `push`, de seu repositório Git local, deve-se usar um token de acesso pessoal ou chave SSH para autenticar com o {{site.data.keyword.gitrepos}}.

### Criando um token de acesso pessoal
{: #create_pat}

Para autenticar com o seu repositório Git sobre HTTPS, deve-se criar um token de acesso pessoal.
{: tip}

1. No painel Configurações de usuário do {{site.data.keyword.gitrepos}}, na [página Tokens de acesso](https://us-south.git.cloud.ibm.com/profile/personal_access_tokens){: external}, digite o nome do aplicativo para o qual deseja criar um token de acesso. Por exemplo, `Git CLI`.
1. Opcional: escolha uma data de validade para o token de acesso.
1. Selecione a caixa de seleção **api** para criar um token de acesso pessoal que use api como escopo.
1. Clique em **Criar token de acesso pessoal**. Anote o token de acesso em um local seguro para uso futuro.
1. Na [página Conta](https://us-south.git.cloud.ibm.com/profile/account){: external}, na seção Mudar nome de usuário, localize seu nome de usuário do {{site.data.keyword.gitrepos}}. Seu nome do usuário é exibido como o primeiro segmento da URL para qualquer repositório Git pessoal que você cria.
1. Use seu nome do usuário do {{site.data.keyword.gitrepos}} e o token de acesso pessoal para autenticar com seu repositório Git de um cliente Git externo.

Para saber mais, consulte [Tokens de acesso pessoal](https://us-south.git.cloud.ibm.com/help/api/README.html#personal-access-tokens){: external}.

### Criando uma chave SSH  
{:create_ssh }

Para criar uma chave SSH, consulte [Como criar suas chaves SSH](https://us-south.git.cloud.ibm.com/help/gitlab-basics/create-your-ssh-keys){: external}. O acesso aos repositórios com autenticação SSH pode requerer mais configuração para proxies e firewalls.

Para saber mais, consulte [SSH](https://us-south.git.cloud.ibm.com/help/ssh/README){: external}.

## Arquivo físico e limites de tamanho do repositório
{: #git_limits}

Os arquivos são estritamente limitados a 100 MB. O limite de tamanho sugerido do repositório é 1 GB. Se o seu repositório excede 1 GB, talvez você receba um e-mail com uma solicitação para reduzir o tamanho do repositório.

## Fazer um tutorial: {{site.data.keyword.gitrepos}}
{: #git_tutorials}

Confira um destes tutoriais sobre o [IBM&reg; Cloud Garage Method](https://www.ibm.com/cloud/garage){: external}:

  * [Crie e use sua primeira cadeia de ferramentas usando a cadeia de ferramentas "Desenvolver um app Cloud Foundry"](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){: external}.Saiba como criar uma cadeia de ferramentas aberta por meio de um modelo e usá-la para entregar continuamente um app "Hello World".

  * [Use a cadeia de ferramentas "Desenvolver e testar microsserviços no Cloud Foundry"](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){: external}.Aprenda como criar uma cadeia de ferramentas usando um modelo com três microsserviços e use a cadeia de ferramentas para entregar continuamente uma loja on-line.
