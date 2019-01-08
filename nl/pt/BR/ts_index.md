---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-6"

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:faq: data-hd-content-type='faq'}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# Perguntas mais frequentes
{: #ts_cd}

Obtenha respostas para as perguntas mais frequentes sobre o uso
do {{site.data.keyword.contdelivery_full}}.
{:shortdesc}


## Eu tentei incluir a integração de ferramenta GitHub em minha cadeia de ferramentas, por que a
integração de ferramenta não estava incluída?
{: #cannot_authorize_github}
{: faq}

Se o {{site.data.keyword.Bluemix_notm}} não estiver autorizado a acessar sua conta do GitHub, a
integração de ferramenta não será incluída em sua cadeia de ferramentas.

Se você estiver configurando a integração de ferramenta GitHub enquanto estiver criando sua cadeia de
ferramentas, siga estas etapas para autorizar com o GitHub:

  1. Na seção Integrações configuráveis, clique em **GitHub**.
  1. Se você estiver criando a cadeia de ferramentas no {{site.data.keyword.Bluemix_notm}} Public e o {{site.data.keyword.Bluemix_notm}} não estiver autorizado a acessar o GitHub, clique em **Autorizar** para acessar o website GitHub.
  1. Se você não
tiver uma sessão do GitHub ativa, será solicitado a efetuar login. Clique em **Autorizar aplicativo** para permitir que o {{site.data.keyword.Bluemix_notm}} acesse sua conta GitHub.

Se você já tiver uma cadeia de ferramentas, atualize a configuração da integração de ferramenta GitHub:

 1. No painel do DevOps, na página **Cadeias de ferramentas**, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, clique em **Visão geral**.
 1. No cartão GitHub, clique no menu e, em seguida, em **Configurar**.
 1. Atualize as definições de configuração para autorizar o {{site.data.keyword.Bluemix_notm}} a acessar o GitHub. Clique em **Autorizar** para acessar o website do GitHub. Se você não
tiver uma sessão do GitHub ativa, será solicitado a efetuar login. Clique em **Autorizar aplicativo** para permitir que o {{site.data.keyword.Bluemix_notm}} acesse sua conta GitHub.
 1. Quando tiver finalizado a atualização das configurações, clique em **Salvar integração**.


## Eu tentei criar uma cadeia de ferramentas, por que estou recebendo um erro?
{: #cannot_create_toolchain}
{: faq}

Ao tentar criar uma cadeia de ferramentas em uma organização, se você receber a mensagem de erro a seguir, remova uma ou mais cadeias de ferramentas de sua organização e, em seguida, crie a sua cadeia de ferramentas novamente.

`Esta organização contém 200 cadeias de ferramentas, que é o limite máximo. Para poder incluir outra cadeia de ferramentas, remova uma ou mais cadeias de ferramentas da organização.`


## Por que a página Cadeias de ferramentas mostra que o plano Lite do serviço {{site.data.keyword.contdelivery_short}} foi excedido?
{: #plan_exceeded}
{: faq}

{{site.data.keyword.contdelivery_short}}  oferece dois planos: Lite e Professional. Se você tiver o plano Lite do {{site.data.keyword.contdelivery_short}}, será possível usar cadeias de ferramentas gratuitamente, até os limites do plano. A mensagem de erro indica que você excedeu um ou mais limites do plano Lite. Por exemplo, você poderá exceder o plano se você tiver muitos usuários autorizados que estiverem associados à instância do serviço {{site.data.keyword.contdelivery_short}} ou se você executou o número máximo de tarefas do {{site.data.keyword.deliverypipeline}}. Para obter mais informações sobre os termos de seu plano, veja [Limitações e uso do plano](/docs/services/ContinuousDelivery/limitations_plans.html){: new_window}.


## Eu criei uma cadeia de ferramentas; por que a página Cadeias de ferramentas mostra que um serviço de Entrega Contínua é necessário?
{: #service_required_resource_group}
{: faq}

Os termos do plano para a instância do serviço {{site.data.keyword.contdelivery_short}} que está no mesmo grupo de recursos ou organização, uma vez que a cadeia de ferramentas gerencia o uso de algumas das integrações de ferramenta ({{site.data.keyword.deliverypipeline}}, Eclipse Orion {{site.data.keyword.webide}} e {{site.data.keyword.gitrepos}}) que estão contidas no serviço. A mensagem de erro indica que o grupo de recursos ou a organização não contém a instância necessária do serviço {{site.data.keyword.contdelivery_short}}. Para obter mais informações sobre os termos de seu plano, veja [Limitações e uso do plano](/docs/services/ContinuousDelivery/limitations_plans.html){: new_window}.


## Eu criei uma cadeia de ferramentas em uma organização do Cloud Foundry; por que a página Cadeias de ferramentas mostra que um serviço de Entrega Contínua é necessário?
{: #service_required_cloud_foundry}
{: faq}

Quando você criar uma cadeia de ferramentas em um grupo de recursos ou em uma organização que não tem uma instância do serviço {{site.data.keyword.contdelivery_short}}, a plataforma da cadeia de ferramentas tentará criar automaticamente uma instância do serviço usando o plano Lite. A mensagem de erro indica que a plataforma da cadeia de ferramentas não pôde criar a instância de serviço.

Esse erro poderá ocorrer quando você criar uma cadeia de ferramentas na região Sul dos EUA e em uma organização do Cloud Foundry que ainda não tiver uma instância do {{site.data.keyword.contdelivery_short}}. Na região sul dos EUA, deve-se criar todas as novas instâncias do serviço {{site.data.keyword.contdelivery_short}} em grupos de recursos. 

Será possível criar a cadeia de ferramentas em um grupo de recursos ou criar a cadeia de ferramentas em uma organização que já tiver uma instância do {{site.data.keyword.contdelivery_short}}.
  

## Eu tentei implementar um app no {{site.data.keyword.Bluemix_notm}}, por que estou recebendo
um erro?
{: #org_outofmemory}
{: faq}

Ao tentar implementar um app no {{site.data.keyword.Bluemix_notm}}, se você receber a mensagem de erro a seguir, a quantia de memória restante em sua organização será menor do que a quantia de memória requerida pelo app que você deseja implementar.

`Erro de Servidor COM FALHA, código de status: 400, código de erro: 100005, mensagem: Você excedeu seu limite de memória da organização.`

É possível aumentar a cota de memória de sua conta ou reduzir a memória que seus apps usam. A cota máxima
de memória para uma conta de avaliação é 2 GB. Para aumentar a cota de memória de sua conta, converta sua conta de avaliação em uma conta paga. Para obter informações sobre como converter sua conta para teste para uma conta paga, veja [Contas pagas](/docs/pricing/index.html#pay-accounts). Para reduzir a memória que seus apps usam, use o console do {{site.data.keyword.Bluemix_notm}} ou a interface da linha de comandos cf.

Se você usar o console do {{site.data.keyword.Bluemix_notm}}, conclua as etapas a seguir:

1. No Painel Apps, selecione seu app. A página de detalhes do app é aberta.
1. Na área de janela de tempo de execução, é possível reduzir o limite máximo de memória ou os números de instâncias do app, ou ambos, para seu app.

Se você usar a interface de linha de comandos cf, conclua as seguintes etapas:

1. Verifique quantia de memória que está sendo usada para seus apps. O comando cf apps lista todos os aplicativos que você implementou no espaço atual. O status de cada app também é exibido.

	  ```
	  cf apps
	  ```

1. Para reduzir a quantia de memória que é usada por seu app, reduza o número de instâncias do app ou o limite máximo de memória, ou ambos:

	  ```
	  cf push appname -p app_path -i instance_number -m memory_limit
      ```
    
1. Reinicie seu app para que as mudanças entrem em vigor.


## Eu criei um app, por que a barra de execução não mostra ícones do {{site.data.keyword.Bluemix_notm}} Live Sync no Eclipse Orion Web IDE?
{: #ts_llz_lkb_3r}
{: faq}

![Barra de execução](images/webide_runbar_light.png)   

Ao editar um app Node.js no Web IDE, os ícones de edição em tempo real, reinicialização rápida e depuração do {{site.data.keyword.Bluemix_notm}} não estão disponíveis na barra de execução nestas circunstâncias:


* O arquivo `manifest.yml` não está armazenado no nível superior de seu projeto.
* Seu app é armazenado em um subdiretório em vez de raiz, mas o caminho para o subdiretório não está especificado no arquivo `manifest.yml`.
* O app não contém um arquivo `package.json`.


Se o arquivo `manifest.yml` não estiver armazenado na raiz, armazene-o lá. Se seu app estiver armazenado em um subdiretório, especifique o caminho para o subdiretório no arquivo `manifest.yml`. Se o app não contiver um arquivo `package.json`, crie um que esteja no mesmo diretório que seu app.


## Eu cliquei em uma cadeia de ferramentas para visualizar sua página Visão geral, por que a cadeia de ferramentas não está carregada?
{: #toolchains_load}
{: faq}

Verifique a página Status do {{site.data.keyword.Bluemix_notm}} para determinar se problemas conhecidos estão afetando a plataforma do {{site.data.keyword.Bluemix_notm}} e os serviços principais no {{site.data.keyword.Bluemix_notm}}.

É possível localizar a página Status, escolhendo uma das opções a seguir:

  * Efetue login no console do {{site.data.keyword.Bluemix_notm}}. Na barra de menus, clique em **Suporte** e selecione **Status**. Verifique os recursos listados para o ícone ![alguns problemas](../../get-support/images/some_issues.svg). Esse ícone pode indicar uma indisponibilidade.
  * Acesse-a diretamente em [{{site.data.keyword.Bluemix_notm}} - Status do sistema ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/status){: new_window}.

Para obter mais informações sobre a página Status do {{site.data.keyword.Bluemix_notm}}, veja [Visualizando o status do {{site.data.keyword.Bluemix_notm}}](https://cloud.ibm.com/docs/get-support/ViewStatus.html#viewing-bluemix-status).


## Eu configurei uma integração de ferramenta para minha cadeia de ferramentas, por que ela não estava configurada?
{: #tool_integration_error}
{: faq}

Quando você inclui uma integração de ferramenta, a cadeia de ferramentas se comunica com a ferramenta que é representada pela integração de ferramenta para provisionar quaisquer recursos necessários e associá-los à cadeia de ferramentas. Se ocorrer um erro durante o processo de configuração ou se a comunicação entre a cadeia de ferramentas e a ferramenta não for concluída corretamente, a integração de ferramenta será colocada em um estado de erro.

 ![Erro de configuração com falha](images/tool_setup_failed.png)

É possível tentar configurar a integração de ferramenta novamente:

1. Em seu cartão de ferramenta, passe o mouse sobre a mensagem `Falha na configuração` e clique em **Reconfigurar**.

 ![Botão Reconfigurar](images/tool_reconfigure.png)

1. Certifique-se de que esteja usando parâmetros de configuração válidos. Se o erro tiver sido causado por uma configuração inválida, uma mensagem de erro será exibida; por exemplo, `A integração não pôde ser configurada. Verifique as configurações e tente novamente. Motivo: api_key:fakeKey inválida`. Atualize as configurações da integração de ferramenta e clique em **Salvar integração**.
1. Se o erro tiver sido causado por um problema de comunicação, clique em **Salvar integração** para tentar novamente.
