---

copyright:
  years: 2015, 2017
lastupdated: "2017-5-25"

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}

# Resolução de problemas do {{site.data.keyword.contdelivery_short}}
{: #ts_cd}

Obtenha respostas para perguntas comuns de resolução de problemas sobre como usar {{site.data.keyword.contdelivery_full}}.
{:shortdesc}


## Não é possível autorizar com o GitHub
{: #cannot_authorize_github}

Você não tem autorização com o GitHub.
{:shortdesc}

Se o {{site.data.keyword.Bluemix_notm}} não estiver autorizado a acessar sua conta do GitHub, qualquer um destes problemas poderá ocorrer:
{: tsSymptoms}

 * Quando você tentar incluir a integração de ferramenta GitHub em sua cadeia de ferramentas, a integração de ferramenta não será incluída.
 * O pipeline não é executado automaticamente quando você envia mudanças por push para seu repositório GitHub ou GitHub Enterprise.

O {{site.data.keyword.Bluemix_notm}} não está autorizado a acessar o GitHub.  
{: tsCauses}

Se você estiver configurando a integração de ferramenta GitHub enquanto estiver criando sua cadeia de ferramentas, siga estas etapas:
{: tsResolve}

  1. Na seção Integrações configuráveis, clique em **GitHub**.
  1. Se você estiver criando a cadeia de ferramentas no {{site.data.keyword.Bluemix_notm}} Public e o {{site.data.keyword.Bluemix_notm}} não estiver autorizado a acessar o GitHub, clique em **Autorizar** para acessar o website GitHub.
  1. Se você não
tiver uma sessão GitHub ativa, será solicitado que efetue login. Clique em **Autorizar aplicativo** para permitir que o {{site.data.keyword.Bluemix_notm}} acesse sua conta GitHub.

Se você já tiver uma cadeia de ferramentas, atualize a configuração da integração de ferramenta GitHub:

 1. No painel do DevOps, na página **Cadeias de ferramentas**, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, clique em **Visão geral**.
 1. No cartão GitHub, clique no menu e, em seguida, em **Configurar**.
 1. Atualize as definições de configuração para autorizar o {{site.data.keyword.Bluemix_notm}} a acessar o GitHub. Clique em **Autorizar** para acessar o website GitHub. Se você não
tiver uma sessão GitHub ativa, será solicitado que efetue login. Clique em **Autorizar aplicativo** para permitir que o {{site.data.keyword.Bluemix_notm}} acesse sua conta GitHub.
 1. Quando tiver finalizado a atualização das configurações, clique em **Salvar integração**.


## Não é possível criar uma cadeia de ferramentas
{: #cannot_create_toolchain}

Um erro é exibido quando você cria uma cadeia de ferramentas.
{:shortdesc}

Ao criar uma cadeia de ferramentas, você vê a mensagem de erro a seguir:
{: tsSymptoms}

`Esta organização contém 200 cadeias de ferramentas, que é o limite máximo. Para poder incluir outra cadeia de ferramentas, remova uma ou mais cadeias de ferramentas da organização.`

Não é possível ter mais de 200 cadeias de ferramentas em uma organização (org).  
{: tsCauses}

Remova uma ou mais cadeias de ferramentas de sua organização e, em seguida, crie sua cadeia de ferramentas novamente.
{: tsResolve}


## O limite de memória da organização foi excedido
{: #org_outofmemory}

Você pode não conseguir implementar um app no {{site.data.keyword.Bluemix_notm}} se o limite de memória da sua organização é excedido. É possível reduzir a memória que seus apps usam ou aumentar a cota de memória de sua conta. A cota máxima
de memória para uma conta de avaliação é 2 GB. A cota pode ser aumentada quando você faz upgrade para uma conta paga.

Ao implementar um app no {{site.data.keyword.Bluemix_notm}}, você vê a mensagem de erro a seguir:
{: tsSymptoms}

`Erro de Servidor COM FALHA, código de status: 400, código de erro: 100005, mensagem: Você excedeu seu limite de memória da organização.`

Esse erro ocorre quando a quantia de memória restante para a sua organização é menor que a quantia de memória requerida pelo aplicativo que você deseja implementar. A cota máxima
de memória para uma conta de avaliação é 2 GB.
{: tsCauses}

É possível aumentar a cota de memória de sua conta ou reduzir a memória que seus apps usam.
{: tsResolve}

  * Para aumentar a cota de memória de sua conta,
converta sua conta de avaliação em uma conta paga. Para obter informações sobre como converter sua conta para teste para uma conta paga, veja [Contas pagas](/docs/pricing/index.html#pay-accounts).
  * Para reduzir a memória que seus apps usam, use o console do {{site.data.keyword.Bluemix_notm}} ou a interface da linha de comandos cf.

    Se você usar o console do {{site.data.keyword.Bluemix_notm}}, conclua as etapas a seguir:

    1. No Painel Apps, selecione seu app. A página de detalhes do app é aberta.
    2. Na área de janela de tempo de execução, é possível reduzir o limite máximo de memória ou os números de instâncias do app, ou ambos, para seu app.

    Se você usar a interface de linha de comandos cf, conclua as seguintes etapas:

    1. Verifique quanta memória está sendo usada para seus apps:

	  ```
	  cf apps
	  ```

	  O comando cf apps lista todos os aplicativos que você implementou no espaço atual. O status de cada app também é exibido.

    2. Para reduzir a quantia de memória que é usada por seu app, reduza o número de instâncias do app ou o limite máximo de memória, ou ambos:

	  ```
	  cf push appname -p app_path -i instance_number -m memory_limit
      ```

    3. Reinicie seu app para que as mudanças entrem em vigor.

Para obter mais informações sobre problemas gerais com o gerenciamento de seus apps, veja [Resolução de problemas para gerenciar apps](https://console.bluemix.net/docs/troubleshoot/ts_apps.html#managingapps).


## A barra de execução não mostra os ícones do Bluemix Live Sync no Eclipse Orion Web IDE
{: #ts_llz_lkb_3r}

Você criou um app, mas os ícones do IBM Bluemix Live Sync não são mostrados na barra de execução do Eclipse Orion Web IDE. Você não vê a barra de execução integral com os ícones do Live Edit:

![Barra de execução](images/webide_runbar_light.png)   

Ao editar um app Node.js no Web IDE, os ícones de edição em tempo real, de reinicialização rápida e de depuração do {{site.data.keyword.Bluemix_notm}} não são mostrados na barra de execução.
{: tsSymptoms}

Os ícones não ficarão disponíveis nestas circunstâncias:
{: tsCauses}

* O arquivo `manifest.yml` não está armazenado no nível superior de seu projeto.
* Seu app é armazenado em um subdiretório em vez de raiz, mas o caminho para o subdiretório não está especificado no arquivo `manifest.yml`.
* O app não contém um arquivo `package.json`.

Use um dos métodos a seguir:
{: tsResolve}

* Se o arquivo `manifest.yml` não estiver armazenado na raiz, armazene-o lá.
* Se seu app estiver armazenado em um subdiretório, especifique o caminho para o
subdiretório no arquivo `manifest.yml`.
   ```
    path: path_to_application
    ```
* Crie um arquivo `package.json` que esteja no
mesmo diretório que seu app.


## A cadeia de ferramentas não é carregada
{: #toolchains_load}

Quando você clica em uma cadeia de ferramentas para visualizar sua página Visão geral, a cadeia de ferramentas não é carregada.
{:shortdesc}

No painel do DevOps, na página **Cadeias de ferramentas**, clique na cadeia de ferramentas para abrir a página Visão geral. Como alternativa, na página de visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas**. Em seguida, clique em **Visão geral**. A página Visão geral para a cadeia de ferramentas não se abre.
{: tsSymptoms}

Verifique o status do {{site.data.keyword.Bluemix_notm}} para ver se o problema é causado por uma indisponibilidade.
{: tsCauses}

Visualize a página Status do {{site.data.keyword.Bluemix_notm}} para determinar se problemas conhecidos estão afetando a plataforma {{site.data.keyword.Bluemix_notm}} e os serviços principais no {{site.data.keyword.Bluemix_notm}}.
{: tsResolve}

É possível localizar a página Status, escolhendo uma das opções a seguir:

  * Efetue login no console do
{{site.data.keyword.Bluemix_notm}}. Na barra de menus, clique em **Suporte** e selecione **Status**. Verifique os recursos listados para o ícone ![alguns problemas](../../support/images/some_issues.svg). Esse ícone pode indicar uma indisponibilidade.
  * Acesse-o indiretamente em [IBM {{site.data.keyword.Bluemix_notm}} - Status do sistema ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://ibm.biz/bluemixstatus){: new_window}.

Para obter mais informações sobre a página Status do {{site.data.keyword.Bluemix_notm}}, veja [Visualizando o status do {{site.data.keyword.Bluemix_notm}}](https://console.bluemix.net/docs/support/index.html#viewing-bluemix-status).


## A integração de ferramenta não está configurada
{: #tool_integration_error}

Depois de configurar uma integração de ferramenta para sua cadeia de ferramentas, o erro `Falha na configuração` é exibido em seu cartão de ferramenta.
{:shortdesc}

Depois de configurar uma integração de ferramenta, você visualiza seu cartão de ferramenta na página Visão geral da cadeia de ferramentas e observa que a configuração falhou.
{: tsSymptoms}

 ![Erro de configuração com falha](images/tool_setup_failed.png)

Quando você inclui uma integração de ferramenta, a cadeia de ferramentas se comunica com a ferramenta que é representada pela integração de ferramenta para provisionar quaisquer recursos necessários e associá-los à cadeia de ferramentas. Se ocorrer um erro durante o processo de configuração ou se a comunicação entre a cadeia de ferramentas e a ferramenta não for concluída corretamente, a integração de ferramenta será colocada em um estado de erro.
{: tsCauses}

Configure a integração de ferramenta novamente:
{: tsResolve}

1. Em seu cartão de ferramenta, passe o mouse sobre a mensagem `Falha na configuração` e clique em **Reconfigurar**.

 ![Botão Reconfigurar](images/tool_reconfigure.png)

1. Certifique-se de que esteja usando parâmetros de configuração válidos. Se o erro tiver sido causado por uma configuração inválida, uma mensagem de erro será exibida; por exemplo, `A integração não pôde ser configurada. Verifique as configurações e tente novamente. Motivo: api_key:fakeKey inválida`. Atualize as configurações da integração de ferramenta e clique em **Salvar integração**.
1. Se o erro tiver sido causado por um problema de comunicação, clique em **Salvar integração** para tentar novamente.



<!-- ## Pipeline job failures
{: #cannot_authorize_github}

A pipeline job failed.
{:shortdesc}

Your pipeline job failed.
{: tsSymptoms}

 * Some reasons

Many reasons  
{: tsCauses}

If you are configuring the GitHub tool integration while you are creating your toolchain, follow these steps:
{: tsResolve}

  1. In the Configurable Integrations section, click **GitHub**.
  1. If you are creating the toolchain on {{site.data.keyword.Bluemix_notm}} Public and you have not authorized {{site.data.keyword.Bluemix_notm}} to access GitHub, click **Authorize** to go to the GitHub website.
  1. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account. If you have an active GitHub session but you haven't entered your password recently, you might be prompted to enter your GitHub password to confirm.

If you already have a toolchain, update the GitHub tool integration's configuration:

 1. On the DevOps dashboard, on the **Toolchains** page, click the toolchain to open its Overview page. Alternatively, on the app's Overview page, on the Continuous delivery card, click **View Toolchain**, and then click **Overview**.
 1. On the GitHub card, click the menu and click **Configure**.
 1. Update the configuration settings to authorize {{site.data.keyword.Bluemix_notm}} to access GitHub. Click **Authorize** to go to the GitHub website. If you don't have an active GitHub session, you are prompted to log in. Click **Authorize Application** to allow {{site.data.keyword.Bluemix_notm}} to access your GitHub account. If you have an active GitHub session but you haven't entered your password recently, you might be prompted to enter your GitHub password to confirm.
 1. When you are finished updating the settings, click **Save Integration**.  -->




<!-- This is the template for a problem topic.  -->

<!-- The short description section contains a brief description of problem. For example:  

After you create an app on the Dashboard, you click *ADD GIT* to create a Git repository, but you cannot proceed.
{:shortdesc} -->

<!-- The symptoms section contains a description of problem symptoms. For example:  
When you click ADD GIT, a window opens and one of these issues occur:
- The window hangs with a blank screen.
- A message states that a problem exists with 3rd party cookies.
{: tsSymptoms} -->

<!-- The causes section contains a brief explanation of what causes the problem. For example:  
Your browser might be configured to prevent a cookie from being set. That cookie must be set from the IBM Bluemix DevOps Services site in the hub.jazz.net internet domain from within the context of the Bluemix console.
{: tsCauses} -->

<!-- The resolve section contains steps to resolve the problem. For example:  
You can fix this problem in one of three ways:
- Follow the instructions that are in the window that opens from the Bluemix console. Click the button. Another browser window opens temporarily. In that window, DevOps Services sets the authentication cookie.
- In another browser tab, go to https://hub.jazz.net and log in. Return to the Bluemix console and refresh the page. Click ADD GIT again.
- Change your browser settings to enable 3rd party cookies and click ADD GIT again.
{: tsResolve} -->
