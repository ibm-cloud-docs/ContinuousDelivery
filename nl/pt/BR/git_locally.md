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

# Configurando clientes locais para trabalhar com controle de fonte Git
{: #git_local}


É possível gerenciar e trabalhar com seu código-fonte em um repositório (repo) GitHub, GitHub Enterprise ou Git Repos and Issue Tracking, localmente ou no Eclipse Orion Web IDE. Para trabalhar localmente, clone seu repositório com um cliente Git, como a interface da linha de comandos do Git, e edite o código com seu editor favorito. Se você trabalha no Eclipse, é possível instalar o plug-in EGit para controle de versão.

## Clonando o projeto Git por meio da linha de comandos


## Antes de Começar
{: #git_before_clone}

1. Para acessar o servidor Git fora do navegador, pode ser necessário criar um token de acesso pessoal ou chave SSH para autenticação. A tabela a seguir mostra o que você precisa fazer para configurar a autenticação.

| Tipo de Git  | Configuração de HTTPS | Uso de HTTPS |  Configuração de SSH |
|:-----------|:-------------|:------------|:-------------|
| Git Repos and Issue Tracking (git.ng.bluemix.com) | [Token de acesso pessoal](/docs/services/ContinuousDelivery/git_working.html#git_authentication) | O nome do usuário (não seu IBMid) do Git Repos and Issue tracking e o token de acesso pessoal | [Configurar a chave
SSH](/docs/services/ContinuousDelivery/git_working.html#git_authentication) |
| GitHub público (github.com) | O token de acesso pessoal não é necessário, mas é possível configurar um e usá-lo | O nome do usuário e senha do GitHub ou o nome do usuário do GitHub e token de acesso pessoal ou apenas o token de acesso pessoal como o nome do usuário | [Configurar uma chave SSH do GitHub](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/) |
| GitHub corporativo | [Token de acesso pessoal](/docs/services/ghededicated/index.html#gheded_getting_started#ghe_auth) | O nome do usuário (não seu IBMid) do GitHub Enterprise e o token de acesso pessoal | [Configurar a chave SSH do GitHub Enterprise](/docs/services/ghededicated/index.html#gheded_getting_started#ghe_auth) |

Se você preferir usar SSH, será possível reutilizar uma única chave ao longo de todos os servidores do Git. Crie ou localize sua chave e configure-a em cada servidor, conforme descrito nos links anteriores. Se criar sua chave com uma passphrase, essa passphrase será solicitada quando você usar a chave.
{: tip}

2. Se você for usar a linha de comandos do Git, faça o seguinte:

    a. Verifique se o Git está instalado. Em uma linha de comandos, digite `git version`. Se o Git estiver instalado, o número da versão será mostrado e será possível iniciar.

    b. Se o Git não estiver instalado, [acesse o website Git ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://git-scm.com/downloads){: new_window}.

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


Depois que o download é concluído, você tem uma versão local dos arquivos em seu repositório. Para obter mais informações sobre o uso do Git, [veja a documentação do Git ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")]](http://git-scm.com/doc){: new_window}.


## Acessando seu repositório usando o Eclipse e o plug-in EGit
{: #git_egit}

Se você usa o Eclipse e tem um projeto que usa o Git para controle de fonte, é possível usar o plug-in EGit para gerenciar seu repositório do Eclipse. Para obter instruções para instalar e configurar o EGit, veja [Tutorial do EGit ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")]](http://eclipsesource.com/blogs/tutorials/egit-tutorial/){: new_window}.
Se você usa o Git Repos and Issue Tracking e tem algum problema, veja [Git Repos and Issue Tracking](git_working.html#git_local).

## Desenvolvendo com o IBM Eclipse Tools
{: #git_eclipse_tools}

O IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} fornece plug-ins que podem ser
instalados em um ambiente do Eclipse para integrar seu IDE com o {{site.data.keyword.Bluemix_notm}}.

Com as ferramentas, é possível implementar os tipos de arquivos e servidores a seguir no
{{site.data.keyword.Bluemix_notm}} diretamente de seu Eclipse IDE ou do IBM WebSphere&reg;
Application Server Developer Tools (WDT):

* Arquivos JavaScript
* Arquivos WAR (archive web)
* Arquivos EAR (archive corporativo)
* Servidores empacotados do perfil Liberty

Também é possível criar serviços e vinculá-los ao seu app e definir variáveis de ambiente como parte da implementação. Para obter mais informações sobre o IBM Eclipse Tools, consulte
[Implementando apps com o IBM Eclipse
Tools for {{site.data.keyword.Bluemix_notm}}](/docs/manageapps/eclipsetools/eclipsetools.html).
