---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-19"

keywords: IBM Cloud Continuous Delivery, GitHub tool integration, error message

subcollection: ContinuousDelivery

---
<!-- Common attributes used in the template are defined as follows: -->
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
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

## Por que a página Cadeias de ferramentas mostra que o plano Lite do serviço {{site.data.keyword.contdelivery_short}} foi excedido?
{: #plan_exceeded}
{: faq}

{{site.data.keyword.contdelivery_short}}  oferece dois planos: Lite e Professional. Se você tiver o plano Lite do {{site.data.keyword.contdelivery_short}}, será possível usar cadeias de ferramentas gratuitamente, até os limites do plano. A mensagem de erro indica que você excedeu um ou mais limites do plano Lite. Por exemplo, você poderá exceder o plano se você tiver muitos usuários autorizados que estiverem associados à instância do serviço {{site.data.keyword.contdelivery_short}} ou se você executou o número máximo de tarefas do {{site.data.keyword.deliverypipeline}}. Para obter mais informações sobre os termos de seu plano, veja [Limitações e uso do plano](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).


## Meu serviço {{site.data.keyword.contdelivery_short}} afirma que os serviços do plano Lite são excluídos após 30 dias de inatividade. O que inatividade significa?
{: #plan_inactivity}
{: faq}

Uma instância do serviço {{site.data.keyword.contdelivery_short}} é considerada ativa quando uma ou mais das cadeias de ferramentas dentro do mesmo grupo de recursos ou organização (org) do Cloud Foundry estão ativas. Uma cadeia de ferramentas é considerada ativa quando os usuários interagem com ela por meio da interface com o usuário, as tarefas do pipeline de entrega são acionadas, os repositórios que são gerenciados pelo {{site.data.keyword.gitrepos}} são acessados ou as áreas de trabalho do {{site.data.keyword.webide}} Eclipse Orion estão em uso. Para ser considerada inativa, todas essas condições devem estar ausentes para todas as cadeias de ferramentas associadas ao serviço {{site.data.keyword.contdelivery_short}} por 30 dias.


## Eu criei uma cadeia de ferramentas; por que a página Cadeias de ferramentas mostra que um serviço de Continuous Delivery é necessário?
{: #service_required_resource_group}
{: faq}

Os termos do plano para a instância do serviço {{site.data.keyword.contdelivery_short}} que está no mesmo grupo de recursos ou organização, uma vez que a cadeia de ferramentas gerencia o uso de algumas das integrações de ferramenta ({{site.data.keyword.deliverypipeline}}, Eclipse Orion {{site.data.keyword.webide}} e {{site.data.keyword.gitrepos}}) que estão contidas no serviço. A mensagem de erro indica que o grupo de recursos ou a organização não contém a instância necessária do serviço {{site.data.keyword.contdelivery_short}}. Para obter mais informações sobre os termos de seu plano, veja [Limitações e uso do plano](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-limitations_usage).


## Atualizei as informações para uma cadeia de ferramentas por meio de uma organização do Cloud Foundry, por que não vejo minhas mudanças na cadeia de ferramentas?
{: #updates_in_cloud_foundry}
{: faq}

Quando você atualiza as informações da cadeia de ferramentas diretamente no Cloud Foundry, pode levar alguns minutos para que o serviço {{site.data.keyword.contdelivery_short}} atualize e mostre suas mudanças. Por exemplo, se você incluir ou remover um usuário de uma organização do Cloud Foundry, poderá levar alguns minutos para o {{site.data.keyword.contdelivery_short}} descobrir que há um novo usuário e permitir que esse usuário acesse a cadeia de ferramentas.


## Eu criei uma cadeia de ferramentas em uma organização do Cloud Foundry; por que a página Cadeias de ferramentas mostra que um serviço de Continuous Delivery é necessário?
{: #service_required_cloud_foundry}
{: faq}

Quando você criar uma cadeia de ferramentas em um grupo de recursos ou em uma organização que não tem uma instância do serviço {{site.data.keyword.contdelivery_short}}, a plataforma da cadeia de ferramentas tentará criar automaticamente uma instância do serviço usando o plano Lite. A mensagem de erro indica que a plataforma da cadeia de ferramentas não pôde criar a instância de serviço.

Esse erro poderá ocorrer quando você criar uma cadeia de ferramentas na região Sul dos EUA e em uma organização do Cloud Foundry que ainda não tiver uma instância do {{site.data.keyword.contdelivery_short}}. Na região sul dos EUA, deve-se criar todas as novas instâncias do serviço {{site.data.keyword.contdelivery_short}} em grupos de recursos. 

Será possível criar a cadeia de ferramentas em um grupo de recursos ou criar a cadeia de ferramentas em uma organização que já tiver uma instância do {{site.data.keyword.contdelivery_short}}.
  

## Como mover minha cadeia de ferramentas de uma organização do Cloud Foundry para um grupo de recursos?
{: #toolchain_move_to_resource_group}
{: faq}

Ainda não está disponível um recurso para migrar automaticamente cadeias de ferramentas de uma organização do Cloud Foundry para um grupo de recursos. Em vez disso, é possível criar manualmente a cadeia de ferramentas novamente em um grupo de recursos e, em seguida, remover a cadeia de ferramentas original da organização do Cloud Foundry.


## Eu tentei implementar um app no {{site.data.keyword.Bluemix_notm}}, por que estou recebendo
um erro?
{: #org_outofmemory}
{: faq}

Ao tentar implementar um app no {{site.data.keyword.Bluemix_notm}}, se você receber a mensagem de erro a seguir, a quantia de memória restante em sua organização será menor do que a quantia de memória requerida pelo app que você deseja implementar.

`Erro de Servidor COM FALHA, código de status: 400, código de erro: 100005, mensagem: Você excedeu seu limite de memória da organização.`

É possível aumentar a cota de memória de sua conta ou reduzir a memória que seus apps usam. A cota máxima
de memória para uma conta de avaliação é 2 GB. Para aumentar a cota de memória de sua conta, converta sua conta de avaliação em uma conta paga. Para obter informações sobre como converter sua conta de avaliação em uma conta paga, consulte [Como faço upgrade ou mudo minha conta?](/docs/account?topic=account-accountfaqs#changeacct). Para reduzir a memória que seus apps usam, use o console do {{site.data.keyword.Bluemix_notm}} ou a interface da linha de comandos cf.

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


## Criei um aplicativo, por que a barra de execução não mostra os ícones do Live Sync do {{site.data.keyword.Bluemix_notm}} no {{site.data.keyword.webide}}?
{: #ts_llz_lkb_3r}
{: faq}

![Barra de execução](images/webide_runbar_light.png)   

Ao editar um aplicativo Node.js no {{site.data.keyword.webide}}, os ícones de edição em tempo real, reinicialização rápida e depuração do {{site.data.keyword.Bluemix_notm}} não estão disponíveis na barra de execução nestas circunstâncias:


* O arquivo `manifest.yml` não está armazenado no nível superior de seu projeto.
* Seu app é armazenado em um subdiretório em vez de raiz, mas o caminho para o subdiretório não está especificado no arquivo `manifest.yml`.
* O app não contém um arquivo `package.json`.


Se o arquivo `manifest.yml` não estiver armazenado na raiz, armazene-o lá. Se seu app estiver armazenado em um subdiretório, especifique o caminho para o subdiretório no arquivo `manifest.yml`. Se o app não contiver um arquivo `package.json`, crie um que esteja no mesmo diretório que seu app.


## Cliquei no botão de execução do {{site.data.keyword.webide}}, onde estão os arquivos de log? 
{: #web_ide_log_files}
{: faq}  

Quando você clica no botão Executar, o conteúdo de sua área de trabalho é enviado por push para o Cloud Foundry da mesma maneira que são implementados quando você digita `cf push` na sua área de trabalho. É possível localizar os arquivos de log no painel do Cloud Foundry.

Para obter mais informações sobre como implementar o conteúdo de sua área de trabalho, consulte [Implementando um aplicativo de sua área de trabalho](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#deploy).


## Como evitar que o {{site.data.keyword.webide}} selecione automaticamente todas as mudanças na visualização do Git? 
{: #web_ide_git_view}
{: faq} 

O {{site.data.keyword.webide}} assume, por padrão, que você deseja enviar por push as mudanças de saída para o repositório de código toda vez que você acessa a página do Git. Se desejar selecionar manualmente quais recursos consolidar, sincronizar, reconfigurar e substituir, na página de preferências do GIT, limpe a caixa de seleção **Sempre selecionar arquivos mudados**.


## Por que o {{site.data.keyword.webide}} não suporta o idioma que eu uso? 
{: #web_ide_language_support}
{: faq}  

O {{site.data.keyword.webide}} fornece ferramentas extensivas e suporte para JavaScript, HTML e CSS. Fornece também o destaque da sintaxe para os idiomas mais populares. Não é possível estender o {{site.data.keyword.webide}} para suportar um idioma específico. Para visualizar uma lista completa dos idiomas que o {{site.data.keyword.webide}} suporta, consulte [Idiomas suportados](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-web_ide#supported_languages).


## Como localizar o status do {{site.data.keyword.Bluemix_notm}} e do serviço {{site.data.keyword.contdelivery_short}}?
{: #toolchains_load}
{: faq}

Verifique a página Status do {{site.data.keyword.Bluemix_notm}} para determinar se problemas conhecidos estão afetando a plataforma do {{site.data.keyword.Bluemix_notm}} e os serviços principais no {{site.data.keyword.Bluemix_notm}}.

É possível localizar a página Status, escolhendo uma das opções a seguir:

  * Efetue login no console do {{site.data.keyword.Bluemix_notm}}. Na barra de menus, clique em **Suporte** e selecione **Status**. Verifique os recursos listados para o ícone ![alguns problemas](../../get-support/images/some_issues.svg). Esse ícone pode indicar uma indisponibilidade.
  * Acesse-o diretamente em [{{site.data.keyword.Bluemix_notm}} - Status do sistema](https://cloud.ibm.com/status){: external}.

Para obter mais informações sobre a página Status do {{site.data.keyword.Bluemix_notm}}, consulte [Visualizando status do {{site.data.keyword.Bluemix_notm}}](/docs/get-support?topic=get-support-viewing-cloud-status#viewing-cloud-status).


## Como passar os artefatos entre as tarefas de pipeline?
{: #artifacts_pipeline_jobs}
{: faq}

Como todas as tarefas de pipeline em um estágio recebem a mesma entrada de estágio, não é possível passar artefatos entre tarefas que estão no mesmo estágio. No entanto, as tarefas de construção geram artefatos que as tarefas em outros estágios podem usar. Para passar os artefatos entre duas tarefas, mova cada tarefa para um estágio separado. Para obter mais informações sobre tarefas de pipeline, consulte [Tarefas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about#deliverypipeline_jobs).


## Há um limite de tempo máximo no qual minhas tarefas de pipeline podem ser executadas?
{: #pipeline_jobs_time_limit}
{: faq}

Cada tarefa de pipeline pode ser executada por um máximo de 60 minutos. Se uma tarefa exceder esse limite de tempo, ela falhará. Analise se o trabalho que a tarefa de pipeline faz pode ser dividido em etapas menores. É possível dividir a tarefa de pipeline em várias tarefas de pipeline mais curtas, que são executadas por menos de 60 minutos.


## Quão seguras são as propriedades seguras de pipeline?
{: #pipeline_secure_properties}
{: faq}

As propriedades seguras de pipeline são criptografadas usando AES-128 e decriptografadas imediatamente antes de serem passadas para o script de pipeline. Essas propriedades também são mascaradas usando asteriscos na interface com o usuário de propriedades e em seus arquivos de log de pipeline. Antes que os dados sejam gravados no arquivo de log para a tarefa de pipeline, eles são varridos para correspondências exatas em todos os valores nas propriedades seguras de pipeline. Se uma correspondência for encontrada, ela será mascarada usando asteriscos. Tenha cuidado quando estiver trabalhando com propriedades seguras e arquivos de log, já que somente correspondências exatas são mascaradas. 
