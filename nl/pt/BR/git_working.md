---

copyright:
  years: 2015, 2017
lastupdated: "2017-6-6"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:screen:.screen}
{:codeblock:.codeblock}

# Git Repos and Issue Tracking
{: #git_working}

Colabore com a sua equipe e gerencie seu código-fonte com um repositório (repo) Git e um rastreador de problemas que seja hospedado pela IBM e construído no [GitLab Community Edition ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://about.gitlab.com/){:new_window}.
{: shortdesc}

A integração de ferramenta {{site.data.keyword.gitrepos}} suporta que as equipes gerenciem código e colaborem de várias maneiras:
   * Gerenciar repositórios Git por meio de controles de acesso de baixa granularidade que mantém o código seguro
   * Revisar o código e aprimorar a colaboração por meio de solicitações de mesclagem
   * Rastrear problemas e compartilhar ideias por meio do rastreador de problemas
   * Documentar projetos no sistema de wikis

**Nota:** como essa integração de ferramenta é construída no GitLab Community Edition e hospedada pela IBM no Bluemix, algumas opções do GitLab não estão disponíveis. Por exemplo, o Delivery Pipeline fornece integração contínua e entrega contínua para o Bluemix, portanto, os recursos de integração contínua no GitLab não são suportados. Além disso, as funções de administração não estão disponíveis porque são gerenciadas pela IBM.

## Limites de tamanho do arquivo e do repositório
{: #git_limits}

Os arquivos são estritamente limitados a 100 MB. O limite de tamanho sugerido do repositório é 1 GB. Se o seu repositório excede 1 GB, talvez você receba um e-mail com uma solicitação para reduzir o tamanho do repositório.

## Usando o Repos and Issue Tracking localmente
{: #git_local}

É possível acessar localmente os repositórios Git que são armazenados no {{site.data.keyword.gitrepos}}. Para obter instruções de como configurar o Git localmente, consulte [Iniciar o uso do Git na linha de comandos ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/help/gitlab-basics/start-using-git){:new_window}.

**Dica**: O {{site.data.keyword.gitrepos}} suporta somente conexões HTTPS que usam TLS1.2. Se você usa o Eclipse para se conectar, pode ser necessário especificar esse protocolo para sua versão Java&trade; incluindo `-Dhttps.protocols=TLSv1.2` em seu arquivo eclipse.ini e, em seguida, reiniciando o Eclipse.

## Autenticando com GitLab  
{: #git_authentication}

Para concluir operações Git remotas, como `clonar` ou `enviar por push` no repositório Git local, deve-se usar um token de acesso pessoal ou uma chave SSH para se autenticar no GitLab.

### Criando um token de acesso pessoal  
Para autenticar com o seu repositório Git sobre HTTPS, deve-se criar um token de acesso pessoal. Seu login e senha do {{site.data.keyword.Bluemix_notm}} funcionam com o {{site.data.keyword.gitrepos}} somente em um navegador. Não é possível usar as credenciais do usuário do {{site.data.keyword.Bluemix_notm}} para autenticar de clientes Git externos.

1. No painel Configurações do usuário do {{site.data.keyword.gitrepos}}, na [página Tokens de acesso ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/profile/personal_access_tokens?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window}, digite o nome do aplicativo para o qual você deseja criar um token de acesso. Por exemplo, `Git CLI`.
1. Opcional: escolha uma data de validade para o token de acesso.
1. Selecione a caixa de seleção **api** para criar um token de acesso pessoal que use api como escopo.
1. Clique em **Criar token de acesso pessoal**. Anote o token de acesso em um local seguro para uso futuro.
1. Na [página Conta ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/profile/account?cm_sp=dw-bluemix-_-nospace-_-answers){:new_window}, na seção Mudar nome do usuário, localize o nome do usuário do {{site.data.keyword.gitrepos}}. Seu nome do usuário é exibido como o primeiro segmento da URL para qualquer repositório Git pessoal que você cria.
1. Use seu nome do usuário do {{site.data.keyword.gitrepos}} e o token de acesso pessoal para autenticar com seu repositório Git de um cliente Git externo.

Para saber mais, veja [Tokens de acesso pessoal ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/help/api/README.html#personal-access-tokens){:new_window}.

### Criando uma chave SSH  
Para criar uma chave SSH, veja [Como criar suas chaves SSH ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/help/gitlab-basics/create-your-ssh-keys){:new_window}. O acesso aos repositórios com autenticação SSH pode requerer mais configuração para proxies e firewalls.

Para saber mais, veja [SSH ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://git.ng.bluemix.net/help/ssh/README){:new_window}.
