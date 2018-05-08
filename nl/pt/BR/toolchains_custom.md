---

copyright:
  years: 2017, 2018
lastupdated: "2018-2-26"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Criando modelos customizados de cadeia de ferramentas
{: #toolchains_custom}

Melhore seu fluxo de trabalho do DevOps criando um modelo customizado de cadeia de ferramentas. É
possível iniciar rapidamente com um modelo de cadeia de ferramentas existente ou criar um modelo de cadeia de
ferramentas que inclua apenas as integrações de que você precisa. É possível incluir ou remover as integrações de sua cadeia de ferramentas a qualquer momento.
{:shortdesc}

É possível
[criar uma
cadeia de ferramentas](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started){: new_window} em várias maneiras. Depois de criar um modelo customizado de cadeia de ferramentas, é possível compartilhá-lo
[criando uma implementação para
o botão {{site.data.keyword.Bluemix_notm}}](/docs/services/ContinuousDelivery/deploy_button.html#deploy-button){: new_window}.   Detalhes sobre o SDK do modelo
de cadeia de ferramentas podem ser localizados no
[SDK de cadeia de ferramentas
aberta](https://github.com/open-toolchain/sdk/wiki/){:new_window}. Um tutorial passo a passo pode ser localizado no site do
[Garage
Method](https://www.ibm.com/cloud/garage/tutorials/create-a-template-for-a-custom-toolchain/){:new_window}.


## Introdução
{: #toolchains_custom_gettingstarted}

Para criar um modelo customizado de cadeia de ferramentas, inicie clonando o modelo de cadeia de ferramentas simples do Cloud Foundry. Clonar um modelo existente fornece a você o ponto de início para sua cadeia de ferramentas customizada.

1. Usando um cliente Git de sua escolha, insira o comando a seguir para clonar o modelo de [Cadeia de ferramentas simples](https://github.com/open-toolchain/simple-toolchain){: new_window} no GitHub.

 ```
 git clone https://github.com/open-toolchain/simple-toolchain.git
 ```
 {: pre}

 Esse modelo implementa um aplicativo Hello World básico a partir de um único
repositório GitHub e inclui uma cadeia de ferramentas simples que está pré-configurada
para entrega contínua, controle de fonte, rastreamento de problemas e edição on-line.

2. Se você preferir iniciar com um modelo de cadeia de ferramentas mais complexa, será possível iniciar pela clonagem da [Cadeia de ferramentas nativa da nuvem para microsserviços](https://github.com/open-toolchain/toolchain-demo){: new_window}.

 ```
 git clone https://github.com/open-toolchain/toolchain-demo.git
 ```
 {: pre}

O modelo de microsserviços implementa um armazenamento on-line que é composto por três microsserviços, cada um contido em seu próprio repositório GitHub. Também é uma cadeia de ferramentas mais complexa que está pré-configurada para:
* Entrega contínua
* Controle de fonte
* Implementações azul/verde
* Teste funcional
* Rastreamento de problema
* Edição on-line
* Sistema de mensagens

Independentemente de qual modelo você escolher, o processo para customizar a cadeia de ferramentas criada geralmente será o mesmo.

Depois de clonar o modelo, você terá um repositório GitHub básico que contém um arquivo leia-me e um diretório `.bluemix`. O diretório contém todos os arquivos de configuração que a cadeia de ferramentas requer para funcionar. No mínimo, o diretório `.bluemix` deve conter os arquivos a seguir:

* `toolchain.yml`
* `deploy.json`
* `pipeline.yml`

![Arquivos mínimos que são necessários para definir uma cadeia de ferramentas](images/min_files_for_a_toolchain.png)


Cada um desses arquivos é explicado nas seções a seguir. Cada seção contém informações de configuração que podem ser consultadas conforme sua cadeia de ferramentas se desenvolve.
O YAML é uma linguagem de serialização de dados que é um superconjunto estrito de JSON, com a adição de
novas linhas e indentação sintaticamente significativas. No entanto, o YAML não permite caracteres de
tabulação literal.

## Entendendo os arquivos de configuração
{: #toolchains_custom_config_files}


Os arquivos de configuração de modelo de cadeia de ferramentas são compostos
principalmente de arquivo de formato YAML. Cada arquivo contém metadados que descrevem
diferentes aspectos da cadeia de ferramentas. Os metadados incluem
* Informações sobre a cadeia de ferramentas e repositórios.
* Detalhes sobre como o código é construído e implementado.
* Propriedades de configuração para as ferramentas que estão na cadeia de ferramentas.

À medida que sua cadeia de ferramentas se torna mais complexa, os arquivos de configuração podem crescer em complexidade também.

Algumas diretrizes para ter em mente ao trabalhar com arquivos YAML:

* Use somente espaços. Não são permitidas tabulações.
* Todas as propriedades e listas devem ser recuadas com um ou mais espaços.
* Todas as chaves e propriedades fazem distinção entre maiúsculas e minúsculas.

Preste atenção à formatação do arquivo YAML para reduzir sua chance de encontrar erros.
Para verificar erros, talvez você queira usar um validador simples, como
[este analisador](http://wiki.ess3.net/yaml/){: new_window}.
{: tip}

## Planejando a seção de serviços
Cada subseção de serviço contém as seguintes informações:

* name - uma sequência gerada pelo usuário que é usada para identificar esse serviço no contexto do
arquivo atual. Esse nome pode ser usado para marcar um serviço como obrigatório.

* service_id - uma cadeia exclusiva que identifica o serviço. Essa sequência vem diretamente do
[catálogo de
serviços](https://github.com/open-toolchain/sdk/wiki/services.md){: new_window}.

* parameters - zero ou mais parâmetros de configuração para o serviço. Esses parâmetros variam entre
os serviços: os usuários precisam consultar o catálogo para compreender quais parâmetros um serviço específico
requer.

### Incluindo texto de outros arquivos

Todas as informações para sua cadeia de ferramentas podem estar no
arquivo `toolchain.yml`. No entanto, talvez você queira criar arquivos separados para cada
UI de integração de ferramenta utilizando `$text`. Isso pode facilitar a manutenção de suas
cadeias de ferramentas, bem como minimizar o tempo gasto editando arquivos de configuração. Este
fragmento de exemplo de um `toolchain.yml` mostra como usar o conteúdo do
arquivo `pipeline.yml` como o valor para `content`.

```
  configuration:
    content:
      $text: pipeline.yml
```

### Localizando seu modelo de cadeia de ferramentas

É possível localizar sua cadeia de ferramentas exteriorizando suas sequências de UI no
diretório `nls` para que as sequências na cadeia de ferramentas sejam exibidas no idioma
preferido do usuário.
Seu arquivo `toolchain.yml` precisa incluir uma referência a `$i18n`.  
O exemplo a seguir mostra uma referência `$i18n` a um arquivo `messages.yml`:

```
messages:
  $i18n: messages.yml
```

  As sequências em inglês estão em `messages.yml` e outros idiomas usam o código de
idiomas, como `messages_de.yml`.  A lista de códigos de idioma pode ser localizada em
[Tags para identificação de idiomas](https://tools.ietf.org/html/rfc5646){: new_window}.

   Para referenciar a sequência de exteriorização, use `$ref` para recuperar a sequência.
Por
exemplo,

```
  template:
    name:
      $ref: "#/messages/template.name"
```

  Se você não usar sequências externalizadas, será possível usar:

```
  template:
    name: my_template
```

Para saber mais, consulte a
[Seção
de mensagens do SDK de cadeia de ferramentas aberta](https://github.com/open-toolchain/sdk/wiki/Template-File-Format#messages-section){: new_window}.

## Configurando o arquivo de cadeia de ferramentas
{: #toolchains_custom_toolchain_yml}

O arquivo `toolchain.yml` é o ponto central da cadeia de
ferramentas. As especificações de sua cadeia de ferramentas, incluindo repositórios para
pull, serviços a serem incluídos e detalhes de construção, estão todos descritos nesse
arquivo. Para entender o conteúdo, ele pode ser dividido em várias seções.

1\. **Informações introdutórias da cadeia de ferramentas:**

 Esta seção do arquivo fornece detalhes simples sobre sua cadeia de ferramentas que o usuário pode ver na página de criação de cadeia de ferramentas. Inclua um nome para sua cadeia de ferramentas, juntamente com uma descrição que explique o propósito da cadeia de ferramentas. Também é possível incluir uma imagem, como um logotipo ou uma representação visual da cadeia de ferramentas.

 Além de fornecer o conteúdo introdutório para sua cadeia de ferramentas, esta seção também inclui uma
chave que é denominada `required` que define as ferramentas que fazem parte da cadeia de
ferramentas. O criador de ferramentas configura essas ferramentas quando ele cria a cadeia de ferramentas de seu modelo. Para cada ferramenta que pode ser configurada na página de criação de cadeia de ferramentas, inclua a chave pai da ferramenta tal como ela está definida no arquivo `toolchain.yml` como uma propriedade da chave `required`.

 Este snippet mostra um exemplo dessa seção:

 ```
 ---
template
  name: "Simple Toolchain"
  description: "This Hello World application uses Node.js and includes a toolchain that is preconfigured for continuous delivery, source control, issue tracking, and online editing.\n\nTo get started, click **Create**."
  header: '![](toolchain.svg)'
  icon: icon.svg
  required:
   - sample-build
   - sample-repo
  info:
    git url: >-
      [https://github.com/my-toolchain/simple-toolchain](https://github.com/open-toolchain/simple-toolchain)
    git branch: >-
      [master](https://github.com/my-toolchain/simple-toolchain/tree/master)
  ```
 {: codeblock}

Nesse exemplo, a URL do Git e a ramificação do Git são para um novo modelo de cadeia de ferramentas.

2\. **Definições de repositório:**

 Uma cadeia de ferramentas pode fornecer entrega contínua para qualquer número de repositórios Git,
incluindo o GitHub, GitHub Enterprise, Git Repos and Issue Tracking e GitLab. Esta seção do arquivo `toolchain.yml` é onde cada repositório está definido.

 Para cada repositório que é incluído na cadeia de ferramentas, inclua uma chave pai que represente o
nome de seu repositório com as propriedades a seguir:

| Item | Chave/Propriedade | Valor | Descrição |
|------|--------------|-------|-------------|
| repo-name | principais |  | O nome do repositório. Essa chave corresponde ao nome (sample-repo) |
| service_id | propriedades | <`githubpublic`, `githubprivate`, `hostedgit`, `gitlab`> | 
Tipo de repositório |
| parâmetros: | principais |  |  |
| repo_name | propriedades |  | Padrão para o nome do repositório. O exemplo a seguir usa o nome da cadeia de ferramentas como o nome do repositório |
| repo_url | propriedades |  | URL do repositório |
| Tipo | propriedades | <`new`, `fork`, `clone`, `link`> | 
Como criar o novo repositório |
| has_issues | propriedades | <`true`, `false`> | Problemas de uso |
| enable_traceability | de metadados |  <`true`, `false`> | Determina se deve rastrear a implementação de mudanças de código criando tags, rótulos e comentários em confirmações, solicitações pull e problemas referenciados.|

 **Nota:** se você definir múltiplos repositórios e configurá-los como
`has_issues: true`, uma instância única do rastreador GitHub Issue será incluída na cadeia de
ferramentas. O rastreador segue problemas para todos os repositórios que são configurados para `true`.

 Este snippet mostra um exemplo dessa seção:

 ```
 # Github repos
 services:
  sample-repo:
    service_id: githubpublic
    parameters:
      repo_name: '{{toolchain.name}}'
      repo_url: 'https://github.com/open-toolchain/node-hello-world'
      type: clone
      has_issues: true
      enable_traceability: true
 ```
 {: codeblock}

3\. **Informações do pipeline:**

 É possível entregar continuamente seu projeto com um pipeline. Esta seção do arquivo define os detalhes de configuração que são usados para construir e implementar o código em cada um de seus repositórios GitHub e Git Repo and Issue Tracking.

 Para iniciar, para cada repositório que está definido em sua cadeia de ferramentas, inclua uma chave pai que representa um nome de seu pipeline. Considere derivar essa chave do nome de seu repositório GitHub ou Git Repo and Issue Tracking. Inclua as seguintes propriedades:

| Item | Chave/Propriedade | Valor | Descrição |
|------|--------------|-------|-------------|
| pipeline-name | principais |  | Nome para o pipeline (sample-build) |
| service_id | propriedades | <`pipeline`> | Nome do serviço a ser usado |
| parâmetros | principais |  |  |
| nome | propriedades | <`repo_name`> | O mesmo nome que está definido na seção repos |
| ui-pipeline | propriedades | <`true`, `false`> |True se os
aplicativos que esse pipeline implementa são mostrados no menu **Visualizar app** na
página de cadeia de ferramentas  |
| configuration | principais |  |  |
| conteúdo | propriedades | <`$ref(pipeline.yml)`> | Arquivo que estabelece a definição de pipeline |
| env | principais |  |  |
| SAMPLE_REPO | principais | <`repo-name-key`> | O mesmo nome que sua chave pai de repositório |
| CF_APP_NAME |  propriedades | <`'{{form.pipeline.parameters.prod-app-name}}'`> | Nome que é usado pelo Cloud Foundry. 
Considere incorporar o nome chave pai do repositório nesta propriedade. |
| PROD_SPACE_NAME | propriedades | <`'{{form.pipeline.parameters.prod-space}}'`> | Nome do espaço do {{site.data.keyword.Bluemix_notm}} no qual implementar |
| PROD_ORG_NAME | propriedades | <`'{{form.pipeline.parameters.prod-organization}}'`> | Nome da organização {{site.data.keyword.Bluemix_notm}} na qual implementar |
| PROD_REGION_ID | propriedades | <`'{{form.pipeline.parameters.prod-region}}'`> | Nome da região {{site.data.keyword.Bluemix_notm}} na qual implementar |
| execute | propriedades | <`true`, `false`> | Iniciar pipeline após criação |

<!--| services | property | <`repo-name-key`> |  GitHub repository parent key |
| hidden | property | <`[form, description]`> |  |
-->

 As informações sobre a criação de um arquivo `pipeline.yml` podem
ser encontradas em uma [seção posterior.](#toolchains_custom_pipeline_yml)

 Este fragmento mostra um exemplo dessa seção do arquivo:

 ```
 # Pipelines
  sample-build:
    service_id: pipeline
    parameters:
      services:
        - sample-repo
      name: '{{services.sample-repo.parameters.repo_name}}'
      ui-pipeline: true
      configuration:
        content:
          $ref: pipeline.yml
        env:
          SAMPLE_REPO: sample-repo
          CF_APP_NAME: '{{form.pipeline.parameters.prod-app-name}}'
          PROD_SPACE_NAME: '{{form.pipeline.parameters.prod-space}}'
          PROD_ORG_NAME: '{{form.pipeline.parameters.prod-organization}}'
          PROD_REGION_ID: '{{form.pipeline.parameters.prod-region}}'
       execute: true
 ```      
 {: codeblock}

4\. **Detalhes da implementação:**

 Como parte do processo de entrega contínua, é possível configurar uma cadeia de ferramentas para implementar um aplicativo para qualquer Região, Organização ou Espaço do {{site.data.keyword.Bluemix_notm}} ao qual um usuário tem acesso. Os detalhes específicos de onde implementar seu
aplicativo podem ser selecionados na página de criação da cadeia de ferramentas.

 ![Definições de configuração do Delivery Pipeline](images/deploy_configuration.png)

 Esta seção do arquivo `toolchain.yml` define os estágios do
pipeline que estão disponíveis para serem configurados na página de criação da cadeia de
ferramentas.

 Para iniciar, a chave-pai `deploy` é usada para identificar as
propriedades de configuração de implementação. As propriedades a seguir compõem o
restante da seção:

| Item | Chave/Propriedade | Valor | Descrição |
|------|--------------|-------|-------------|
| Implementação | principais |  | Nome da seção de implementação |
| Esquema | propriedades | <`deploy.json`> | Arquivo que define o layout da IU para configurar os detalhes da implementação |
| service-category | propriedades | <`pipeline`> | Serviço que usa as configurações de
implementação |
| parâmetros | principais |  |  |
| prod-region | propriedades | <`"{{region}}"`> | Define a região do {{site.data.keyword.Bluemix_notm}} para o estágio de produção |
| prod-organization | propriedades | <`"{{organization}}"`> | Define a organização do {{site.data.keyword.Bluemix_notm}} para o estágio de produção |
| prod-space | propriedades | <`prod`> | Define o espaço do {{site.data.keyword.Bluemix_notm}} para o estágio de produção |
| github-repo-name | propriedades | <`"{{repo-name-key.parameters.repo_name}}"`> | Variável para passar o nome do repositório GitHub para a página de criação da cadeia de ferramentas |

Para obter mais informações sobre como criar um arquivo `deploy.json`, consulte
[esta seção] (#toolchains_custom_deploy_json).

 O exemplo a seguir define um único estágio que é implementado em um ambiente de produção.

 ```
 ## Configuring a deployment stage
 deploy:
   schema: deploy.json
   service-category: pipeline
   parameters:
 	prod-region: "{{region}}"
 	Organização do produto: "{{organization}}"
 	prod-space: prod
 	hello-world-name: "{{hello-world-repo.parameters.repo_name}}"
 ```
 {: codeblock}

 O exemplo de código pode ser usado na maioria das vezes no estado em que se
encontra e requer pouca modificação somente. Para customizar essa seção, configure
`github-repo-name` para que seja consistente com o nome de seu repositório. Os detalhes no
arquivo [`deploy.json`](#toolchains_custom_deploy_json) também
precisam ser atualizados.

 Para criar um pipeline mais complexo que inclua estágios dev, QA e Prod, as propriedades a seguir podem
ser substituídas sob a chave `parameters`.

 ```
   parameters:
 	dev-region: "{{region}}"
 	qa-region: "{{region}}"
 	prod-region: "{{region}}"
 	dev-organization: "{{organization}}"
 	qa-organization: "{{organization}}"
 	Organização do produto: "{{organization}}"
 	dev-space: dev
 	qa-space: qa
 	prod-space: prod
 ```
 {: codeblock}

 ## Configurando um pipeline
 {: #toolchains_custom_pipeline_yml}

 O arquivo `pipeline.yml` contém todos os detalhes de configuração
dos estágios de seu pipeline. É possível iniciar com um pipeline.yml existente e customizá-lo para atender às suas necessidades.

 Se a sua cadeia de ferramentas contiver mais de um pipeline, forneça nomes
exclusivos para cada arquivo `pipeline.yml`.

 Veja a seguir o exemplo de um arquivo `pipeline.yml`:

 ```
 ---
stages:
- name: BUILD
  inputs:
  - type: git
    branch: master
    service: ${SAMPLE_REPO}
  triggers:
  - type: commit
  jobs:
  - name: Build
    type: builder
- name: DEPLOY
  inputs:
  - type: job
    stage: BUILD
    job: Build
  triggers:
  - type: stage
  properties:
  - name: CF_APP_NAME
    value: undefined
    type: text
  - name: APP_URL
    value: undefined
    type: text
  jobs:
  - name: Blue-Green Deploy
    type: deployer
    target:
      region_id: ${PROD_REGION_ID}
      organization: ${PROD_ORG_NAME}
      space: ${PROD_SPACE_NAME}
      application: ${CF_APP_NAME}
    script: |
      #!/bin/bash
      # Push app
      if ! cf app $CF_APP; then  
        cf push $CF_APP
      else
        OLD_CF_APP=${CF_APP}-OLD-$(date +"%s")
        rollback() {
          set +e  
          if cf app $OLD_CF_APP; then
            cf logs $CF_APP --recent
            cf delete $CF_APP -f
            cf rename $OLD_CF_APP $CF_APP
          fi
          exit 1
        }
        set -e
        trap rollback ERR
        cf rename $CF_APP $OLD_CF_APP
        cf push $CF_APP
        cf delete $OLD_CF_APP -f
      fi
      # Export app name and URL for use in later Pipeline jobs
      export CF_APP_NAME="$CF_APP"
      export APP_URL=http://$(cf app $CF_APP_NAME | grep urls: | awk '{print $2}')
      # View logs
      #cf logs "${CF_APP}" --recent
 ```
 {: codeblock}		


 ## Configurando a interface do pipeline
 {: #toolchains_custom_deploy_json}

 Na página de criação da cadeia de ferramentas, quando o Delivery Pipeline é selecionado na seção
Integrações configuráveis, a seção se expande para exibir os itens a seguir:

 	* O nome do aplicativo
 	* A Região, a Organização e o Espaço em que seus estágios do pipeline são implementados.

É possível configurar esses itens para cada ferramenta.

 ![Definições de configuração do Delivery Pipeline](images/deploy_configuration.png)

 O layout desta seção na IU é definido pelo esquema `deploy.json`.

 Dentro do esquema, as propriedades a seguir devem ser atualizadas para que correspondam aos detalhes de
seu aplicativo:

 	* Título
 	* Descrição
 	* LongDescription
 	* Todas as instâncias de `hello-world-name` e os detalhes
associados deverão ser modificados para corresponder aos do seu aplicativo.

 O fragmento a seguir é um exemplo de um arquivo `deploy.json`:

 ```
 {
    "$schema": "http://json-schema.org/draft-04/schema#",
    "messages": {
        "$i18n": "locales.yml"
    },
    "title": {
        "$ref": "#/messages/deploy.title"
    },
    "description": {
        "$ref": "#/messages/deploy.description"
    },
    "longDescription": {
        "$ref": "#/messages/deploy.longDescription"
    },
    "type": "object",
    "properties": {
        "prod-region": {
            "description": "The {{site.data.keyword.Bluemix_notm}} region",
            "type": "string"
        },
        "prod-organization": {
            "description": "The {{site.data.keyword.Bluemix_notm}} org",
            "type": "string"
        },
       "prod-space": {
            "description": "The {{site.data.keyword.Bluemix_notm}} space",
            "type": "string"
        },
        "prod-app-name": {
            "description": {
                "$ref": "#/messages/deploy.appDescription"
            },
            "type": "string",
            "pattern": "\\S"
        }
    },
    "required": [
        "prod-region",
        "prod-organization",
        "prod-space",
        "prod-app-name"
    ],
    "form": [
        {
            "type": "validator",
          "url": "/devops/setup/bm-helper/helper.html"
        },
        {
            "type": "text",
            "readonly": false,
            "title": {
                "$ref": "#/messages/deploy.appName"
            },
            "key": "prod-app-name"
        },
        {
            "type": "table",
            "columnCount": 4,
            "widths": [
                "15%",
                "28%",
                "28%",
                "28%"
            ],
            "items": [
                {
                    "type": "label",
                  "title": ""
                },
                {
                    "type": "label", "title": {
                        "$ref": "#/messages/region"
                    }
                },
                {
                    "type": "label", "title": {
                        "$ref": "#/messages/organization"
                    }
                },
                {
                    "type": "label", "title": {
                        "$ref": "#/messages/space"
                    }
                },
                {
                    "type": "label", "title": {
                        "$ref": "#/messages/prodStage"
                    }
                },
                {
                    "type": "select",
                  "key": "prod-region"
                },
                {
                    "type": "select",
                  "key": "prod-organization"
                },
                {
                    "type": "select",
                  "key": "prod-space",
                  "readonly": false
                }
            ]
        }
    ]
}
 ```
 {: codeblock}


## Outras configurações da ferramenta

 Depois de configurar os componentes principais de sua cadeia de ferramentas, é possível incluir outras
integrações de ferramentas que incluam mais funções na sua cadeia de ferramentas. Todas as ferramentas
adicionais requerem suas próprias entradas no arquivo `toolchain.yml`. Algumas ferramentas
também requerem que você inclua um arquivo de configuração YAML separado no diretório
`.bluemix`.

 ![Arquivos necessários paradefinir uma cadeia de ferramentas](images/files_for_toolchain_with_additional_tools.png)


Para ver a lista de integrações de ferramentas disponíveis, veja <a href="https://github.com/open-toolchain/sdk/wiki/services.md" target="_blank">Serviços disponíveis em um modelo de cadeia de ferramentas</a>. Os exemplos a seguir mostram como formatar adições para um arquivo YAML de cadeia de ferramentas.

### **Slack**

#### toolchain.yml
{: #slack_toolchain_yaml}

```
messaging:
	  service_id: slack
	  $ref: slack.yml
```
{: codeblock}

#### slack.yml
{: #slack_slack_yaml}

```
---YAML
parameters:
  api_token: ""
  channel_name: ""
```
{: codeblock}

### **Sauce Labs**

#### toolchain.yml
{: #sauce_toolchain_yaml}

```YAML
test:
	  service_id: saucelabs
	  $ref: saucelabs.yml
```
{: codeblock}

#### saucelabs.yml
{: #sauce_slack_yaml}

```YAML
---
	parameters:
	  username: ""
  key: ""
```
{: codeblock}

### **Eclipse Orion Web IDE**

####	toolchain.yml
{: #eclipse_toolchain_yaml}

```YAML
webide:
	  service_id: orion
```
{: codeblock}
