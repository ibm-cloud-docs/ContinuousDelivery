---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-19"

keywords: Eclipse Orion {{site.data.keyword.webide}}, file types, Local Editor Settings icon

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:important: .important}
{:note: .note}
{:tip: .tip}
{:download: .download}

# Desenvolvendo com o Eclipse Orion Web IDE
{: #web_ide}

O Eclipse Orion {{site.data.keyword.webide}} é um ambiente de desenvolvimento baseado em
navegador no qual é possível desenvolver para a web em JavaScript, HTML e CSS com a ajuda de assistência de
conteúdo, conclusão de código e verificação de erro. O {{site.data.keyword.webide}} trabalha com quase qualquer idioma e é possível destacar a sintaxe para a maioria dos tipos de arquivo. O controle de versão é construído e é possível implementar código localmente para testar e depurar os apps.
{:shortdesc}

O melhor de tudo, o {{site.data.keyword.webide}} é desenvolvido com a web. Você não tem nada para instalar, nada para manter e nada para escalar. É possível desenvolver em qualquer lugar no qual haja uma conexão de Internet.

Não armazene dados regulados em arquivos dentro do {{site.data.keyword.webide}}. Os procedimentos para os dados regulados não estão atualmente em vigor.
{: tip}

O {{site.data.keyword.webide}} é acessível pelo teclado e funciona bem com um leitor de tela. É possível usar o {{site.data.keyword.webide}} para editar o código, se preferir, será possível editar o código usando o editor de código ou editor de texto favorito. Também é possível usar os recursos do Git que são fornecidos com o {{site.data.keyword.webide}}; como alternativa, é possível usar a linha de comandos do Git ou o github.com para acessar os recursos do Git do {{site.data.keyword.webide}}.
{: note}

## Configurando o IDE
{: #editorsetup}

O {{site.data.keyword.webide}} é customizável de maneira que é possível escolher os esquemas de cores, as ferramentas técnicas e configurações que atendam às necessidades de desenvolvimento. Para visualizar e modificar as configurações, na barra lateral de navegação à esquerda, clique no ícone **Configurações**<img class="inline" src="images/webide_settings_icon_light_small.png"  alt="O ícone configurações">.

Se for necessário mudar com frequência certas configurações ao editar, será possível acessar essas configurações rapidamente por meio do ícone **Configurações do editor local** <img class="inline" src="images/webide_local_settings_icon_light_small.png"  alt="Ícone Configurações do editor local">.

![Configurações do editor local](images/webide_local_editor_settings_light.png)

Por padrão, as configurações para o estilo de editor e o tamanho da fonte são sempre mostradas. Para incluir outras configurações do editor no menu, siga estas etapas:

1. Clique no ícone **Configurações do editor local** <img class="inline" src="images/webide_local_settings_icon_light_small.png"  alt="Ícone Configurações do editor local">.

2. Clique em **Configurações do editor**.

3. Para incluir ou excluir uma configuração do menu **Configurações do editor local**, clique na estrela a cada configuração.

![Alternância de Configurações do editor](images/webide_editor_settings_toggle_light.png)


## Editando código
{: #editcode}

O {{site.data.keyword.webide}} tem duas seções. A primeira seção é o navegador de arquivo, que mostra os arquivos de projeto em uma estrutura em árvore. A partir do navegador de arquivo, é possível criar, renomear, excluir e gerenciar os seus arquivos e pastas.

Para fazer upload de arquivos para o navegador de arquivo, arraste-os de seu computador para o navegador de arquivo.
{: tip}

A segunda seção é a área de janela do editor. O editor fornece vários recursos de codificação, incluindo assistência de conteúdo e validação de sintaxe.

![Web IDE](images/webide_light.png)

### Trabalhando com múltiplos arquivos
1. Para trabalhar com dois arquivos ao mesmo tempo, clique no ícone **Mudar modo do editor de divisão** <img class="inline" src="images/webide_split_editor_icon_light_small.png"  alt="Ícone Editor de divisão">.
2. A partir do menu que é aberto, selecione uma visualização.

 Após você selecionar uma visualização, se um arquivo já foi aberto no editor, ele será mostrado em ambas as visualizações do editor.

 Para abrir ou mudar um arquivo que é mostrado em uma das visualizações do editor:
 1. Mova o cursor para a visualização do editor que você deseja mudar.
 2. No navegador de arquivo, clique em um arquivo.

### Atalhos pelo Teclado
Muitos dos comandos no {{site.data.keyword.webide}} são acessíveis por meio de atalhos de teclado.

Para ver uma lista dos atalhos de teclado no editor, clique em **Ferramentas** > **Mostrar chaves**. Como alternativa, é possível ver a lista pressionando Alt+Shift+? ou, em MacOS, Ctrl+Shift+?. É possível customizar um atalho passando o mouse sobre a chave, clicando no lápis e digitando a nova ligação de teclas.

## Gerenciamento de código fonte
{: #sourcecontrol}

O {{site.data.keyword.webide}} é integrado com ferramentas de gerenciamento de código-fonte. Para trabalhar com o repositório Git, clique no ícone **Repositório Git** <img class="inline" src="images/webide_git_icon_light_small.png"  alt="O ícone Repositório Git">.  Para obter mais informações, consulte
[Trabalhando com o Git no Eclipse
Orion Web IDE](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_web_ide#git_web_ide).

## Implementando um aplicativo a partir de sua área de trabalho
{: #deploy}

1. Para implementar seu app, na barra de execução, selecione ou crie uma configuração de ativação.
 ![Barra de execução](images/webide_runbar_light.png)   
1. Clique no ícone de implementação <img class="inline" src="images/webide_deploy_button_light_small.png"  alt="O ícone de implementação">. Uma instância de seu aplicativo é implementada usando os conteúdos atuais de sua área de trabalho e o ambiente que está definido em sua configuração de ativação.
2. Após o seu aplicativo ser implementado, é possível usar a barra de execução para parar, reiniciar ou depurar o seu aplicativo, visualizar logs e mais.

<table role="presentation">
<tr><td><img src="./images/stop_button.png"  alt="O ícone de parada"></td><td>Pare o app.</td></tr>
<tr><td> <img src="./images/open_app_url.png"  alt="O ícone URL de abertura do app"></td><td> Abra o app implementado.</td></tr>
<tr><td><img src="./images/view_logs.png"  alt="O ícone visualizar logs"></td><td>Visualize os logs do app implementado.</td></tr>
<tr><td><img src="./images/open_dashboard.png"  alt="O ícone abrir painel"></td><td>Abra o Painel do app.</td></tr>
</table>

Se você estiver desenvolvendo um app Node.js, ative o modo Live Edit: <img  src="./images/enable_live_edit.png"  alt="A régua de controle de ativação do Live Edit">

<table role="presentation"><tr><td><img src="./images/live_edit_restart.png"  alt="O ícone de reinicialização do Live Edit"></td><td>Com o modo Live Edit ativado, reinicie o app rapidamente, sem reimplementação.</td></tr>
<tr><td> <img src="./images/debug_icon.png"  alt="O ícone de depuração"></td>
<td>Com o modo Live Edit ativado, acesse o depurador.
</td></tr>
</table>

## Idiomas suportados
{: #supported_languages}

O Eclipse Orion {{site.data.keyword.webide}} fornece assistente de conteúdo, dicas de ferramentas, visualizações, validação e destaca a sintaxe para os arquivos JavaScript, HTML, CSS e Markdown. Também é possível destacar a sintaxe para estes tipos de arquivo:

<table role="presentation">
<tr>
<td>
<ul><li>Arduino
</li><li>C</li>
<li>C#
</li><li>C++
</li><li>CoffeeScript
</li><li>CSHTML
</li><li>Embedded JavaScript (ejs)
</li><li>Erlang
</li><li>Ir
</li><li>HTML abstraction markup language (Haml)
</li><li>Jade
</li><li>Compilador Java
</li><li>JSON
</li><li>Menor que  
</li><li>Lua  
</li><li>Objective-C
</li><li>PHP
</li><li>Python</li></ul>
</td>
<td>
<ul><li>Rubi
</li><li>Sass/SCSS
</li><li>SQL
</li><li>Swift
</li><li>TypeScript
</li><li>Visual Basic (vb)
</li><li>VMHTML
</li><li>XHTML
</li><li>XML
</li><li>XQuery
</li><li>YAML
</li><li>Arquivo de ativação 	
</li><li>Dockerfile
</li><li>gitignore
</li><li>git config
</li><li>cfignore
</li><li>de metadados
</li></ul>
</td>
</tr>
</table>

## Fazer um tutorial: Eclipse Orion Web IDE
{: #toolchain_web_ide_tutorials}

Confira um destes tutoriais sobre o [IBM&reg; Cloud Garage Method](https://www.ibm.com/cloud/garage){: external}:

  * [Crie e use sua primeira cadeia de ferramentas usando a cadeia de ferramentas "Desenvolver um app Cloud Foundry"](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){: external}.

  * [Use a cadeia de ferramentas "Desenvolver e testar microsserviços no Cloud Foundry"](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){: external}. 
