---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-19"

keywords: Git source control, personal access token, Git repos

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Configurando clientes locais para trabalhar com controle de fonte Git
{: #git_local}


É possível gerenciar e trabalhar com o código-fonte em um GitHub, um GitHub Enterprise ou um repositório (repo) do {{site.data.keyword.gitrepos}}, localmente ou no Eclipse Orion {{site.data.keyword.webide}}. Para trabalhar localmente, clone seu repositório com um cliente Git, como a interface da linha de comandos do Git, e edite o código com seu editor favorito. Se você trabalha no Eclipse, é possível instalar o plug-in EGit para controle de versão.

## Clonando o projeto Git por meio da linha de comandos


## Antes de Começar
{: #git_before_clone}

1. Para acessar o servidor Git fora do navegador, deve-se criar um token de acesso pessoal ou uma chave SSH para autenticação. A tabela a seguir mostra o que você precisa fazer para configurar a autenticação.

| Tipo de Git  | Configuração de HTTPS | Uso de HTTPS |  Configuração de SSH |
|:-----------|:-------------|:------------|:-------------|
| Git Repos and Issue Tracking  | [Token de acesso pessoal](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#create_pat) | O nome do usuário (não seu IBMid) do Git Repos and Issue tracking e o token de acesso pessoal | [Configurar a chave
SSH](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#creating-an-ssh-key) |
| GitHub público (github.com) | O token de acesso pessoal não é necessário, mas é possível configurar um e usá-lo | O nome do usuário e senha do GitHub ou o nome do usuário do GitHub e token de acesso pessoal ou apenas o token de acesso pessoal como o nome do usuário | [Configurar uma chave SSH do GitHub](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/){: external} |
| GitHub corporativo | [Token de acesso pessoal](/docs/services/ghededicated?topic=ghededicated-getting-started#ghe_auth) | O nome do usuário (não seu IBMid) do GitHub Enterprise e o token de acesso pessoal | [Configurar a chave SSH do GitHub Enterprise](/docs/services/ghededicated?topic=ghededicated-getting-started#ghe_auth) |
{: caption="Tabela 1. Instalação de autenticação do Git" caption-side="top"}

Se você preferir usar SSH, será possível reutilizar uma única chave ao longo de todos os servidores do Git. Crie ou localize sua chave e configure-a em cada servidor, conforme descrito nos links anteriores. Se você criar sua chave com uma passphrase, essa passphrase será solicitada ao usar a chave.
{: tip}

2. Se você for usar a linha de comandos do Git, conclua as etapas a seguir:

    a. Verifique se o Git está instalado. Em uma linha de comandos, digite `git version`. Se o Git estiver instalado, o número da versão será mostrado e será possível iniciar.

    b. Se o Git não estiver instalado, [acesse o website do Git](http://git-scm.com/downloads){: external}.

    c. Faça download e instale a versão para seu sistema operacional. É possível aceitar os valores de instalação padrão.


### Clonando seu projeto
{: #git_clone}

Crie uma cópia local dos arquivos de projeto clonando o repositório Git para que seja possível acessar o conteúdo de seu repositório fora do IDE da Web usando qualquer ferramenta da área de trabalho.

1. Na página Visão geral da sua cadeia de ferramentas, clique no cartão para o repositório que você deseja clonar.

2. Reúna sua URL do repositório:

   a. No GitHub, clique em **Clonar ou fazer download**. Para usar HTTPS, selecione **Usar HTTPS**.  Para usar SSH, clique em **Usar SSH**. Clique no ícone de área de transferência para copiar a URL.

   b. No Git Repos and Issue Tracking, selecione **HTTPS** ou **SSH** e copie a URL no campo.

3. Abra uma linha de comandos

4. Mude o diretório para onde você deseja que a cópia local do repositório Git esteja.

5. Digite `git clone`, cole a URL e pressione Enter.

6. Se for solicitada autenticação, insira as informações apropriadas, conforme definido na tabela anterior.


Depois que o download é concluído, você tem uma versão local dos arquivos em seu repositório. Para obter mais informações sobre o uso do Git, consulte a [documentação do Git](http://git-scm.com/doc){: external}.


## Acessando seu repositório usando o Eclipse e o plug-in EGit
{: #git_egit}

Se você usa o Eclipse e tem um projeto que usa o Git para controle de fonte, é possível usar o plug-in EGit para gerenciar seu repositório do Eclipse. Para obter mais informações sobre como instalar e configurar o EGit, consulte o [tutorial do EGit](http://eclipsesource.com/blogs/tutorials/egit-tutorial/){: external}.

Se você usar o {{site.data.keyword.gitrepos}} e tiver algum problema, consulte a documentação do [{{site.data.keyword.gitrepos}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_local).
