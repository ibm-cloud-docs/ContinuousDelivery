---

copyright:
  years: 2016, 2018
lastupdated: "2018-3-22"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Visão geral do Delivery Pipeline
{: #deliverypipeline_about}

O {{site.data.keyword.contdelivery_full}} inclui o Delivery Pipeline para construir, testar e implementar de forma repetida com mínima intervenção humana. Em um pipeline, as sequências de estágios recuperam a entrada e executam tarefas, como construções, testes e implementações.
{:shortdesc}

As seções a seguir descrevem os detalhes conceituais por trás dos pipelines.

## Estágios
{: #deliverypipeline_stages}

Os estágios organizam a entrada e as tarefas conforme o código é construído, implementado e testado. Os estágios aceitam entrada de repositórios de controle de fonte (repositórios SCM) ou tarefas de construção (artefatos de construção) em outros estágios. Ao criar seu primeiro estágio, as configurações padrão são definidas para você na guia **ENTRADA**.

A entrada de um estágio é passada para as tarefas que ele contém e cada tarefa recebe um contêiner limpo no qual é executada.

**Importante**: as tarefas em um estágio não podem transmitir artefatos entre si. 
Como não é possível transmitir artefatos entre estágios, é necessário que você tenha um estágio de Construção
separado de um estágio de Implementação, caso seu estágio de implementação use os artefatos do estágio de construção.

É possível definir as propriedades do ambiente do estágio que podem ser usadas em todas as tarefas. Por
exemplo, é possível definir uma propriedade `TEST_URL` que transmita uma única URL para
implementar e testar as tarefas em um único estágio. A tarefa de implementação seria implementada nessa URL e a tarefa de teste testaria o app de execução na URL.

Por padrão, em um estágio, as construções e implementações são executadas automaticamente toda vez que
mudanças são entregues no repositório SCM de um projeto. Os estágios e as tarefas são executados em série; eles ativam o controle
de fluxo para seu trabalho. Por exemplo, você poderá colocar um estágio de teste antes de
um estágio de implementação. Se os testes no estágio de teste falharem, o estágio de
implementação não será executado.

Você talvez queira restringir o controle de um estágio específico. Se você não
quiser que um estágio seja executado toda vez que uma mudança ocorrer na sua entrada,
será possível desativar o recurso. Na guia **ENTRADA**, na seção
Acionador de estágio, clique em **Executar tarefas somente quando este estágio
for executado manualmente**.

![A guia ENTRADA](images/input_tab_only_execute.png)


### Estágio de Construção
{: #build_stage}

<!-- Need the Pipeline team to fill out what each builder does and possible add an example -->
O estágio de Construção especifica um **Tipo Builder** para indicar como construir os
artefatos.  Os tipos de Builder a seguir estão disponíveis:

1. **Simple** - se você usa o tipo de construtor **Simples**,
seu código não é compilado nem construído; ele é empacotado e disponibilizado para estágios futuros.
2. **Ant**
3. **Container Registry**
4. **Gradle**
5. **Gradle (Artifactory, Nexus ou SonarQube)**
6. **Grunt**
7. **IBM Globalization Pipeline**
8. **Maven**
9. **Maven (Artifactory, Nexus ou SonarQube)**
10. **npm**
11. **npm (Artifactory ou Nexus)**
12. **Shell Script**

### Estágio de Implementação
O estágio de Implementação especifica a entrada de um estágio de Construção.  As tarefas no estágio de implementação
especificam um **Tipo Deployer**.  Os tipos de Deployer a seguir estão disponíveis:

1. **Cloud Foundry**
2. **Kubernetes**

## Tarefas
{: #deliverypipeline_jobs}

Uma tarefa é uma unidade de execução dentro de um estágio. Um estágio contém
diversas tarefas e as tarefas de um estágio são executadas sequencialmente. Por padrão,
se uma tarefa falhar, as tarefas subsequentes do estágio não serão executadas.

![Tarefas de construção e teste dentro de um estágio](images/jobs.png)

Tarefas executadas em diretórios ativos discretos dentro dos contêineres do Docker
que são criados para cada pipeline executado. Antes da execução de uma tarefa, seu
diretório ativo é preenchido com a entrada que é definida no nível do estágio. Por
exemplo, talvez você tenha um estágio que contém uma tarefa de teste e uma tarefa de
implementação. Se você instalar dependências de uma tarefa, elas não estarão disponíveis
à outra tarefa. Entretanto, se você tornar as dependências disponíveis na entrada do
estágio, elas estarão disponíveis a ambas as tarefas.

Exceto tarefas de construção do tipo simples, ao configurar uma tarefa, é possível
incluir shell scripts do UNIX que incluam comandos de construção, teste ou implementação. Como
as tarefas são executadas em contêineres ad hoc, as ações de uma não podem afetar os
ambientes de execução das outras, mesmo que essas tarefas façam parte do mesmo estágio.

Corpo de amostra e scripts de implementação podem ser localizadas em
[https://github.com/open-toolchain/commons](https://github.com/open-toolchain/commons).

Além disso, as tarefas de pipeline podem executar apenas os comandos a seguir como `sudo`:
  * `/usr/sbin/service`
  * `/usr/bin/apt-get`
  * `/usr/bin/apt-key`
  * `/usr/bin/dpkg`
  * `/usr/bin/add-apt-repository`
  * `/opt/IBM/node-v0.10.40-linux-x64/npm`
  * `/opt/IBM/node-v0.12.7-linux-x64/npm`
  * `/opt/IBM/node-v4.2.2-linux-x64/npm`
  * `/usr/bin/Xvfb`
  * `/usr/bin/pip`


Após a execução de uma tarefa, o contêiner que foi criado para ela é descartado. Os resultados da execução de uma tarefa podem persistir, mas o ambiente no qual ela foi executada não.

**Nota:** as tarefas podem ser executadas por até 60 minutos. Quando as tarefas excedem esse limite, elas falham. Se uma tarefa estiver excedendo o limite, divida-a em várias tarefas. Por exemplo, se uma tarefa executar três trabalhos, você poderá dividi-la em três tarefas: uma para cada trabalho.

Para saber como incluir uma tarefa em um estágio, veja [Incluindo uma tarefa em um estágio](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_add_job){: new_window}.

### Tarefas de construção

As tarefas de construção compilam seu projeto em preparação para implementação. Elas geram artefatos que podem ser enviados para um diretório de archive de construção, embora por padrão, os artefatos sejam colocados no diretório-raiz do projeto.

As tarefas que tomam a entrada das tarefas de construção devem referenciar os artefatos de construção na mesma estrutura em que eles foram criados. Por exemplo, se uma tarefa de construção arquivar artefatos de construção em um diretório `output`, um script de implementação consultaria o diretório `output` em vez do diretório-raiz do projeto para implementar o projeto compilado. É possível especificar o diretório para archive inserindo o nome do diretório no campo **Construir diretório de archive**. Deixar o campo em branco, arquiva o diretório raiz.

**Nota:** se você usa o tipo de construtor **Simples**, seu código não é compilado ou construído; ele é empacotado e disponibilizado para estágios futuros.

Quando você implementa usando o Cloud Foundry, o Cloud Foundry inclui os artefatos corretos para permitir que seu app seja executado. Para obter mais informações, veja [Implementando aplicativos usando o comando cf](https://console.ng.bluemix.net/docs/manageapps/depapps.html#dep_apps). O pipeline para um app Cloud Foundry contém um estágio de Implementação que executa um comando cf.

O Cloud Foundry tenta [detectar o buildpack para uso do ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://docs.cloudfoundry.org/buildpacks/detection.html). Você pode especificar o [Buildpack](/docs/cfapps/byob.html#using-community-buildpacks) para usar no arquivo manifest na pasta raiz de seu app. Os buildpacks geralmente examinam artefatos fornecidos pelo usuário para determinar quais dependências transferir por download e como configurar aplicativos para comunicação com os serviços de limite. Para obter mais informações sobre arquivos manifest, veja [Manifest do aplicativo](/docs/manageapps/depapps.html#appmanifest).

### Tarefas de implementação

As tarefas de implementação fazem upload do seu projeto para o {{site.data.keyword.Bluemix_notm}} como um app e são acessíveis por meio de uma URL. Depois que um projeto é implementado, é possível localizar o app implementado no seu painel do {{site.data.keyword.Bluemix_notm}}.

As tarefas de implementação podem implementar novos apps ou atualizar os existentes. Mesmo
que você tenha primeiro implementado um app usando outro método, como a interface da
linha de comandos do Cloud Foundry ou a barra de execução no IDE da web, é possível
atualizar o app usando uma tarefa de implementação. Para atualizar um app, na tarefa de
implementação, use o nome desse app.

É possível implementar para uma ou várias regiões e serviços. Por exemplo, é
possível configurar seu {{site.data.keyword.deliverypipeline}} para usar um ou
mais serviços, testar em uma região e implementar para produção em múltiplas regiões. Para obter informações adicionais, consulte
[Regiões](/docs/overview/whatisbluemix.html#ov_intro_reg){: new_window}.

### Tarefas de teste
Para requerer que as condições sejam atendidas, inclua tarefas de teste antes ou
após suas tarefas de construção e implementação. É possível customizar as tarefas de
teste para serem simples ou complexas, conforme necessário. Por exemplo, você poderá
emitir um comando cURL e esperar uma resposta específica. Também será possível executar um conjunto de testes de unidade ou executar testes funcionais com serviços de teste de terceiros, como o Sauce Labs.

Se os seus testes produzirem arquivos de resultado no formato XML JUnit, um
relatório baseado nos arquivos de resultado será mostrado na guia
**Testes** de cada página de resultado do teste. Se um teste falhar, a
tarefa também falhará.

## Propriedades do ambiente (variáveis de ambiente)
{: #environment_properties}

É possível incluir propriedades do ambiente dentro dos comandos shell de uma tarefa. As propriedades fornecem acesso a informações sobre o ambiente de execução da tarefa. Para obter mais informações, veja [Propriedades e recursos do ambiente para o serviço {{site.data.keyword.deliverypipeline}}](/docs/services/ContinuousDelivery/pipeline_deploy_var.html).  
As propriedades do ambiente podem ser transmitidas entre tarefas no mesmo estágio exportando as propriedades.  
Para transmitir as propriedades do ambiente entre estágios, crie um arquivo `build.properties`
no repositório no estágio e, em seguida, faça com que o próximo estágio execute o `build.properties`.
Por exemplo, sua tarefa de construção pode incluir este comando no script de construção:

    `echo "IMAGE_NAME=${FULL_REPOSITORY_NAME}" >> $ARCHIVE_DIR/build.properties`

    Todas as tarefas começarão a executar o arquivo `build.properties`, se ele
existir.

## Criando e utilizando artefatos
{: #artifacts}

As tarefas de construção buscam automaticamente o conteúdo na pasta atual na qual o script de
usuário é executado.  Caso você não precise do conteúdo do repositório Git inteiro para implementação
posterior, é preferível que configurar um diretório de saída explícito e, em seguida, copiar ou criar
os artefatos relevantes lá.  Os scripts de tarefa são executados no resultado de construção (diretório de
saída).

As tarefas de implementação que são implementadas no Cloud Foundry precisam especificar a organização e o
espaço do local para a implementação dos artefatos. Se serviços adicionais forem necessários para executar
seu app, será necessário especificá-los no arquivo `manifest.yml`.

As tarefas de implementação que são implementadas no IBM Cloud Container Service em um cluster do
Kubernetes precisam de um Dockerfile e, opcionalmente, de um gráfico do Helm.  

O script da tarefa é executado depois que a tarefa efetua login no ambiente de destino (para que seja
possível executar os comandos `cf push` ou `kubectl` no script).

## Um pipeline de exemplo
{: #deliverypipeline_example}

Um pipeline simples pode conter três estágios:

1. Um estágio de construção que compila e executa processos de construção em um app.
2. Um estágio de teste que implementa uma instância do app e, em seguida, executa testes nele.
3. Um estágio de produção que implementa uma instância de produção do app testado.

Esse pipeline é mostrado no diagrama conceitual a seguir:

![Um diagrama conceitual de estágios e tarefas em um pipeline](images/diagram.jpg)

*Um modelo conceitual de um pipeline de três estágios*

Os estágios tomam suas entradas dos repositórios e das tarefas de construção e as
tarefas dentro de um estágio são executadas de maneira sequencial e independente umas das
outras. No pipeline de exemplo, os estágios são executados sequencialmente, mesmo que os
estágios de Teste e Produção assumam a saída do estágio de Construção como sua entrada.

## Arquivos manifest do Cloud Foundry
{: #deliverypipeline_manifest}

Os arquivos manifest, que são denominados `manifest.yml` e armazenados no
diretório-raiz do projeto, controlam como seu projeto é implementado no
{{site.data.keyword.Bluemix_notm}}. Para obter informações sobre a criação de arquivos manifest para
um projeto, consulte a documentação do
[{{site.data.keyword.Bluemix_notm}}
sobre manifests de aplicativos](/docs/manageapps/depapps.html#appmanifest). Para integrar-se com o {{site.data.keyword.Bluemix_notm}}, seu
projeto deve ter um arquivo manifest em seu diretório-raiz. No entanto, não é necessário implementar com base nas informações no arquivo.

No pipeline, é possível especificar tudo que um arquivo manifest pode fazer usando os argumentos
do comando `cf push`. Os argumentos do comando `cf
push` são úteis em projetos com diversos destinos de implementação. Se diversas
tarefas de implementação tentarem todas usar a rota especificada no arquivo manifest do
projeto, um conflito ocorrerá.

Para evitar conflitos, é possível especificar uma rota usando `cf
push` seguido pelo argumento de nome do host, `-n`, e o nome de
uma rota. A modificação do script de implementação para estágios individuais possibilita
evitar conflitos de rota ao implementar em vários destinos.

Para usar os argumentos do comando `cf push`, abra as definições
de configuração para uma tarefa de implementação e modifique o campo **Script
de implementação**. Para obter mais informações, veja a [documentação Push do Cloud Foundry ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://docs.cloudfoundry.org/devguide/installcf/whats-new-v6.html#push){: new_window}.
