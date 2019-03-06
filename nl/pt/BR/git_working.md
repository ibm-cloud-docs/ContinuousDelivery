---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-5"

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

# {{site.data.keyword.gitrepos}}
{: #git_working}

Colabore com a sua equipe e gerencie seu código-fonte com um repositório (repo) Git e um rastreador de problemas que seja hospedado pela IBM e construído no [GitLab Community Edition ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://about.gitlab.com/){:new_window}.
{: shortdesc}

Convide somente pessoas com as quais você tem um relacionamento pessoal ou de negócio para colaborar em um projeto. Os usuários que usam um convite para um repositório Git para propósitos diferentes de colaborar em um projeto podem ter seu acesso ao serviço suspenso ou revogado.
{: important}

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

É possível acessar localmente os repositórios Git que são armazenados no {{site.data.keyword.gitrepos}}. Para obter instruções de como configurar o Git localmente, consulte [Iniciar o uso do Git na linha de comandos ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/help/gitlab-basics/start-using-git){:new_window}.

O {{site.data.keyword.gitrepos}} suporta apenas conexões de HTTPS que usem o TLS1.2. Se você usa o Eclipse para se conectar, pode ser necessário especificar esse protocolo para sua versão Java&trade; incluindo `-Dhttps.protocols=TLSv1.2` em seu arquivo eclipse.ini e, em seguida, reiniciando o Eclipse.
{: tip}

## Autenticando com o {{site.data.keyword.gitrepos}}
{: #git_authentication}

Seu login e senha do {{site.data.keyword.Bluemix_notm}} são usados somente para autenticar com o {{site.data.keyword.gitrepos}} em um navegador da web. Não é possível usar as credenciais do usuário do {{site.data.keyword.Bluemix_notm}} para autenticar de clientes Git externos. Para concluir operações do Git remoto, como `clone` ou `push`, de seu repositório Git local, deve-se usar um token de acesso pessoal ou chave SSH para autenticar com o {{site.data.keyword.gitrepos}}.

### Criando um token de acesso pessoal
{: #create_pat}

Para autenticar com o seu repositório Git sobre HTTPS, deve-se criar um token de acesso pessoal.
{: tip}

1. No painel Configurações do usuário do {{site.data.keyword.gitrepos}}, na [página Tokens de acesso ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/profile/personal_access_tokens?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window}, digite o nome do aplicativo para o qual você deseja criar um token de acesso. Por exemplo, `Git CLI`.
1. Opcional: escolha uma data de validade para o token de acesso.
1. Selecione a caixa de seleção **api** para criar um token de acesso pessoal que use api como escopo.
1. Clique em **Criar token de acesso pessoal**. Anote o token de acesso em um local seguro para uso futuro.
1. Na [página Conta ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/profile/account?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window}, na seção Mudar nome do usuário, localize o nome do usuário do {{site.data.keyword.gitrepos}}. Seu nome do usuário é exibido como o primeiro segmento da URL para qualquer repositório Git pessoal que você cria.
1. Use seu nome do usuário do {{site.data.keyword.gitrepos}} e o token de acesso pessoal para autenticar com seu repositório Git de um cliente Git externo.

Para saber mais, veja [Tokens de acesso pessoal ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/help/api/README.html#personal-access-tokens){:new_window}.

### Criando uma chave SSH  
{:create_ssh }

Para criar uma chave SSH, veja [Como criar suas chaves SSH ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/help/gitlab-basics/create-your-ssh-keys){:new_window}. O acesso aos repositórios com autenticação SSH pode requerer mais configuração para proxies e firewalls.

Para saber mais, veja [SSH ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/help/ssh/README){:new_window}.

## Arquivo físico e limites de tamanho do repositório
{: #git_limits}

Os arquivos são estritamente limitados a 100 MB. O limite de tamanho sugerido do repositório é 1 GB. Se o seu repositório excede 1 GB, talvez você receba um e-mail com uma solicitação para reduzir o tamanho do repositório.

## Fazer um tutorial: {{site.data.keyword.gitrepos}}
{: #git_tutorials}

Consulte um desses tutoriais no [IBM&reg; Cloud Garage Method ![Ícon de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage){:new_window}:

  * [Criar e usar sua primeira cadeia de ferramentas usando a cadeia de ferramentas "Desenvolver um app Cloud Foundry" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}. Saiba como criar uma cadeia de ferramentas aberta por meio de um modelo e usá-la para entregar continuamente um app "Hello World".

  * [Usar a cadeia de ferramentas "Desenvolver e testar microsserviços no Cloud Foundry"![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}. Aprenda como criar uma cadeia de ferramentas usando um modelo com três microsserviços e use a cadeia de ferramentas para entregar continuamente uma loja on-line.
