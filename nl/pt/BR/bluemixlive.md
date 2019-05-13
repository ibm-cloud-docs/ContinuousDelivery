---



copyright:
  years: 2015，2019
lastupdated: "2019-02-25"

keywords: IBM Cloud Live Synch, Use IBM Cloud Live Sync

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# {{site.data.keyword.Bluemix_notm}} Live Sync
{: #live-sync}


Se você estiver construindo um aplicativo Node.js, será possível usar o {{site.data.keyword.Bluemix}} Live Sync para atualizar rapidamente a instância do aplicativo no {{site.data.keyword.Bluemix_notm}} e desenvolver sem reimplementar manualmente.   
{: shortdesc}

Quando você fizer uma mudança, será possível ver essa mudança no aplicativo {{site.data.keyword.Bluemix_notm}} em execução imediatamente. O {{site.data.keyword.Bluemix_notm}} Live Sync funciona
<!--from both the command line and -->
no Eclipse Orion Web IDE (Web IDE). É possível depurar aplicativos que são gravados no Node.js usando o {{site.data.keyword.Bluemix_notm}} Live Sync.  

O {{site.data.keyword.Bluemix_notm}} Live Sync consiste em dois recursos.
<!--three -->

<!--
**Desktop Sync**  

You can synchronize any desktop directory tree with a cloud-based project workspace similar to the way Dropbox works. The Web IDE directly edits the same cloud-based workspace, so both stay in sync. Desktop Sync works for any kind of application. To use Desktop Sync, you need to download and install the BL command line interface.  
-->

**Live Edit**

É possível editar um aplicativo Node.js que é executado no {{site.data.keyword.Bluemix_notm}} e testá-lo em seu navegador imediatamente. As mudanças feitas no Web IDE são propagadas para o sistema de arquivos do aplicativo imediatamente.  

**Debug**  

Enquanto um aplicativo Node.js estiver no modo Live Edit, é possível executar shell nele e depurá-lo. É possível editar o código dinamicamente, inserir pontos de interrupção, percorrer o código, reiniciar o tempo de execução e muito mais usando o depurador Node Inspector.  


##Live Edit
{: #live-edit}

Se você está construindo um aplicativo Node.js que é executado no {{site.data.keyword.Bluemix_notm}}, o recurso Live Edit do {{site.data.keyword.Bluemix_notm}} Live Sync pode atualizar rapidamente a instância do aplicativo. O Live Edit está disponível somente no Web IDE. É possível usar o Live Edit para desenvolver tal como você faria na área de trabalho sem reimplementar.

O Live Edit é suportado para aplicativos Node.js apenas

No Eclipse Orion Web IDE (Web IDE), na barra de execução, clique em **Live Edit**.

![Imagem da barra de execução com edição em tempo real](images/bluemix-live-sync-light.png)

Use o Live Edit para visualizar rapidamente as mudanças nos aplicativos Node.js que são executados no {{site.data.keyword.Bluemix_notm}}. Ao atualizar seu código com o Live Edit ligado, é possível atualizar sua janela do navegador de aplicativo da Web para ver essas mudanças refletidas segundos após criá-los.

Para ver um tutorial sobre o uso do recurso Live Edit do {{site.data.keyword.Bluemix_notm}} Live Sync, consulte [Usar o {{site.data.keyword.Bluemix_notm}} Live Sync para desenvolver, depurar e implementar seu app ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/use-live-sync-to-develop-debug-and-deploy-your-app){:new_window}.

Quando você muda os arquivos em seu Web IDE, eles são reimplementados automaticamente em sua instância do aplicativo no {{site.data.keyword.Bluemix_notm}}. Se você precisar reiniciar o aplicativo Node, clique no botão **Reiniciar** na barra de execução.

Para obter uma experiência mais consistente, ao usar o recurso Live Edit do {{site.data.keyword.Bluemix_notm}} Live Sync, 256 MB de memória extra serão necessários e incluídos.
{: tip}

## {{site.data.keyword.Bluemix_notm}} Live Debug
{: #live-debug}

O {{site.data.keyword.Bluemix_notm}} Live Sync Debug usa
o [Node Inspector ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/node-inspector/node-inspector){:new_window}
para fornecer recursos de depuração. Você precisa usar a versão 4 do Nó para que o depurador fique disponível, pois as versões mais recentes do Node.js não incluem o Node Inspector.

É possível acessar o {{site.data.keyword.Bluemix_notm}} Live Debug quando o {{site.data.keyword.Bluemix_notm}} Live Edit está ativado para o app Node.js.  

Com o Debug, é possível editar código dinamicamente, inserir pontos de interrupção, percorrer o código, reiniciar o tempo de execução e muito mais, tudo enquanto seu app está sendo entregue pelo {{site.data.keyword.Bluemix_notm}}. É possível desenvolver incrementalmente seu app com agilidade enquanto você escolhe na grande lista de serviços do {{site.data.keyword.Bluemix_notm}}.

O {{site.data.keyword.Bluemix_notm}} Live Debug inclui os recursos a seguir:

* Controle de tempo de execução do aplicativo
* Depuração usando o [Node Inspector ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/node-inspector/node-inspector){:new_window}
* Acesso ao shell

### Controle de tempo de execução do aplicativo {: #app-runtime}

Com o controle de tempo de execução do aplicativo, é possível usar o Debug para inspecionar o estado do app no horário de início. Esse recurso é útil quando você está solucionando problemas de um app que falha ao ser iniciado.

Enquanto você está desenvolvendo seu app, é possível selecionar a partir das ações a seguir:

* Executar uma reinicialização rápida do app
* Suspender o app antes da execução de qualquer código de app

Depois de efetuar login, a página {{site.data.keyword.Bluemix_notm}} Live Debug é aberta.

### Depurar {: #debug}

**Restrição:** o Google Chrome e o Node 4 são necessários.

O Debug inclui os recursos a seguir:  
* Veja os pontos de interrupção no código do app para pausar a execução em uma linha específica.
  Os pontos de interrupção não são suportados no programa principal, mas são suportados em pontos de entrada.
  {: tip}
* Edite as condições do ponto de interrupção para pausar a execução somente quando determinados critérios forem atendidos.
* Inspecione o estado das variáveis e dos campos locais.
* Visualize a saída de depuração das chamadas `console.log()` imediatamente. Essa ação é mais rápida do que monitorar logs cf.
* Use o editor de código-fonte integrado para fazer mudanças imediatas, ou mesmo temporárias, no código do app em execução.

### Shell {: #shell}

Essa ferramenta lhe concede acesso ao shell para o contêiner no qual seu app está em execução. Usando esse terminal, é possível executar remotamente os comandos shell de diagnóstico para administrar seu app. Todas as versões do Node.js suportam o recurso Shell.

Monitore o uso de memória e CPU na instância que usa comandos Linux padrão, como **top**, **ps** e **kill**.

### Configurando um app para ativar o {{site.data.keyword.Bluemix_notm}} Live Debug {: #configure_app_debug}

1. O {{site.data.keyword.Bluemix_notm}} Live Debugger usa o Node Inspector. Você precisa usar o Nó versão 4. Também precisa permitir que o buildpack detecte o comando inicial do app. O comando inicial deve ser detectado automaticamente pelo buildpack, não configurado no arquivo manifest.yml.

   Um arquivo `package.json` que suporta o {{site.data.keyword.Bluemix_notm}} Live Debug é:

  ```
  {
      "scripts": {
         "start": "node app.js"
      },
      "engines": {
         "node": "4"
      }
  }
  ```

2. Aumente a memória.  

    a. No arquivo `manifest.yml` do app, inclua 128 MB ou mais no valor que é especificado para o atributo de memória.

Após a instalação do {{site.data.keyword.Bluemix_notm}} Live Debug, é possível usar as ferramentas de depuração.

Envie por push o app e, em seguida, navegue para `https://_app-host.mybluemix.net_/bluemix-debug/manage` para acessar a interface com o usuário do {{site.data.keyword.Bluemix_notm}} Debug. Quando for solicitado a autenticar, insira seu nome do usuário do IBMid e a senha ou uma senha descartável.    

O Depurador pode levar um minuto ou mais para ser inicializado.
{: tip}

### Restaurando configurações do app e desativando o {{site.data.keyword.Bluemix_notm}} Live Debug {: #restore_live_debug}

1. Restaure a versão original do Node.js do app, o comando inicial e o valor de memória.

2. Envie por push o app.
