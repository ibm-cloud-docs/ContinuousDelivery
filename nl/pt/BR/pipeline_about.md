---

copyright:
  years: 2016, 2018
lastupdated: "2018-11-29"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}


# Visão geral do Delivery Pipeline
{: #deliverypipeline_about}

O {{site.data.keyword.contdelivery_full}} inclui o Delivery Pipeline para construir, testar e implementar de forma repetida com mínima intervenção humana. Em um pipeline, as sequências de estágios recuperam a entrada e executam tarefas, como construções, testes e implementações.
{:shortdesc}

As suas permissões para visualizar, modificar ou executar um pipeline são baseadas no controle de acesso para a cadeia de ferramentas que possui o pipeline. Para obter mais informações sobre o controle de acesso para cadeias de ferramentas, consulte [Gerenciando acesso às cadeias de ferramentas em grupos de recursos](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_resource_groups){: new_window} e [Gerenciando acesso a cadeias de ferramentas em organizações do Cloud Foundry](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_orgs){: new_window}.
{: important}

É possível especificar os scripts a serem executados em muitos dos tipos de tarefas que são fornecidos pelo pipeline, fornecendo controle direto sobre o que é executado pela tarefa. Esses scripts são executados em uma imagem do Docker que contém uma série de ferramentas de desenvolvimento padrão, incluindo ferramentas que são necessárias para interagir com os tempos de execução do {{site.data.keyword.Bluemix_notm}}. Para obter mais informações sobre o que a imagem padrão do Docker contém, veja [Recursos pré-instalados](/docs/services/ContinuousDelivery/pipeline_deploy_var.html#deliverypipeline_resources){: new_window}. Se a sua tarefa requer ferramentas de desenvolvimento que não estão disponíveis na imagem padrão ou se você precisa de versões diferentes dessas ferramentas, é possível usar uma imagem customizada. Para obter mais informações sobre imagens customizadas, veja [Trabalhando com imagens customizadas do Docker](/docs/services/ContinuousDelivery/pipeline_custom_docker_images.html#custom_docker_images){: new_window}.

Quando o pipeline executa scripts, as propriedades que descrevem o contexto em que a tarefa está em execução são passadas para o script usando variáveis de ambiente. Por exemplo, a URL do repositório que é a entrada para o estágio, o nome do estágio e a tarefa que está sendo executada, os parâmetros especificados pelo tipo de tarefa e assim por diante. Para visualizar uma lista de variáveis de ambiente disponíveis, veja [Recursos pré-instalados](/docs/services/ContinuousDelivery/pipeline_deploy_var.html#deliverypipeline_envprop){: new_window}. 

É possível definir propriedades no nível de pipeline e no nível de estágio. As propriedades de pipeline são compartilhadas em todos os estágios e tarefas em um pipeline. As propriedades do estágio são exclusivas para um estágio específico e compartilhadas em todas as tarefas nesse estágio. Para obter mais informações sobre as propriedades, veja [Propriedades do ambiente (variáveis de ambiente)](/docs/services/ContinuousDelivery/pipeline_about.html#environment_properties).

## Estágios
{: #deliverypipeline_stages}

Os estágios organizam a entrada e as tarefas conforme o código é construído, implementado e testado. Os estágios aceitam entrada de repositórios de controle de origem (repositórios SCM) ou de tarefas de construção em outros estágios. Para os repositórios SCM, a entrada são os conteúdos de uma ramificação específica no repositório; para as tarefas de construção, a entrada são os artefatos produzidos pela tarefa. Quando você cria seu primeiro estágio, a guia **ENTRADA** contém configurações padrão.

Quando um estágio é executado, a entrada do estágio é passada para cada uma das tarefas no estágio. Cada tarefa recebe um contêiner limpo no qual executar. Como resultado, as tarefas em um estágio não podem passar artefatos umas para as outras. Para passar artefatos entre tarefas, separe as tarefas em dois estágios e use a saída da tarefa no primeiro estágio como entrada para o segundo estágio.
{: tip}

De maneira semelhante a como é possível definir propriedades de pipeline, também é possível definir propriedades de estágio para uso em todas as tarefas em um estágio específico. Por exemplo, é possível definir uma propriedade `TEST_URL` que passa uma URL para as tarefas de implementação e teste em um estágio. A tarefa de implementação implementa nessa URL e a tarefa de teste testa o app em execução na URL. As propriedades do estágio também são passadas para os scripts de tarefa usando variáveis de ambiente. Se a mesma propriedade for definida no nível de pipeline e no nível de estágio, o valor da propriedade do estágio será usado.

Por padrão, em um estágio, as construções e implementações são executadas automaticamente toda vez que
mudanças são entregues no repositório SCM de um projeto. Os estágios e as tarefas são executados em série; eles ativam o controle
de fluxo para seu trabalho. Por exemplo, você poderá colocar um estágio de teste antes de
um estágio de implementação. Se os testes no estágio de teste falharem, o estágio de implementação não será executado.

Você talvez queira restringir o controle de um estágio específico. Se você não
quiser que um estágio seja executado toda vez que uma mudança ocorrer na sua entrada,
será possível desativar o recurso. Na guia **ENTRADA**, na seção
Acionador de estágio, clique em **Executar tarefas somente quando este estágio
for executado manualmente**.

![A guia ENTRADA](images/input_tab_only_execute.png)


### Estágio de Construção
{: #build_stage}

O estágio de Construção especifica um **Tipo Builder** para indicar como construir os
artefatos.  

Muitos dos campos que estão disponíveis em tarefas de Construção são comuns em múltiplos tipos de Construtor.
{: tip}

Os tipos de Builder a seguir estão disponíveis:

* **Simples** - as tarefas que usam o tipo de construtor **Simples** assumem a entrada do estágio atual e, sem a modificar, arquivam a entrada para uso em estágios futuros. Geralmente, o tipo de construtor **Simples** é útil somente quando a entrada do estágio é de um repositório SCM.
* **Ant** - use esse tipo de construtor para usar arquivos Apache Ant para gerenciar a tarefa de construção.
  * **Script de construção** - esse tipo de construtor pode ser qualquer script de construção válido. Por padrão, esse tipo de construtor é configurado como 'ant'.
  * **Diretório ativo** - especifica o diretório no qual o script é executado.
  * **Diretório de archive de construção** - especifica o diretório que contém a saída da tarefa a ser arquivada para uso por um estágio subsequente.
  * **Ativar relatório de teste** - marque essa caixa de seleção para especificar que a tarefa de construção executa testes que produzem arquivos de resultado no formato JUnit XML. Um relatório baseado nos arquivos de resultado é exibido na guia Testes da página Resultados da tarefa. Se algum teste falha, a tarefa é marcada como com falha.
  * **Ativar relatório de cobertura de código** - marque essa caixa de seleção para mostrar mais campos que podem ser usados para o relatório de cobertura de código. É possível especificar o Executor de cobertura (como Istambul, JaCoCo, ore Cobertura), o local do Arquivo de resultado de cobertura e o Diretório de resultados de cobertura relativos ao Diretório ativo.
* **Container Registry**
* **Gradle (Artifactory, Nexus ou SonarQube)**
* **Grunt**
* **IBM Globalization Pipeline**
* **Maven (Artifactory, Nexus ou SonarQube)**
* **npm (Artifactory ou Nexus)**
* **Shell Script**

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

Os scripts de construção e implementação de amostra podem ser localizados em [https://github.com/open-toolchain/commons](https://github.com/open-toolchain/commons).

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

As tarefas podem ser executadas por até 60 minutos. Quando as tarefas excedem esse limite, elas falham. Se uma tarefa estiver excedendo o limite, divida-a em várias tarefas. Por exemplo, se uma tarefa executar três trabalhos, você poderá dividi-la em três tarefas: uma para cada trabalho.
{: tip}

Para saber como incluir uma tarefa em um estágio, veja [Incluindo uma tarefa em um estágio](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_add_job){: new_window}.

### Tarefas de construção

As tarefas de construção compilam seu projeto em preparação para implementação. Elas geram artefatos que podem ser enviados para um diretório de archive de construção, embora por padrão, os artefatos sejam colocados no diretório-raiz do projeto.

As tarefas que tomam a entrada das tarefas de construção devem referenciar os artefatos de construção na mesma estrutura em que eles foram criados. Por exemplo, se uma tarefa de construção arquivar artefatos de construção em um diretório `output`, um script de implementação consultaria o diretório `output` em vez do diretório-raiz do projeto para implementar o projeto compilado. É possível especificar o diretório para archive inserindo o nome do diretório no campo **Construir diretório de archive**. Deixar o campo em branco, arquiva o diretório raiz.

Se você usar o tipo de construtor **Simples**, o seu código não será compilado nem construído; ele será empacotado e disponibilizado para os estágios futuros.
{: tip}

Quando você implementa usando o Cloud Foundry, o Cloud Foundry inclui os artefatos corretos para permitir que seu app seja executado. Para obter mais informações, veja [Implementando aplicativos usando o comando cf](/docs/cloud-foundry/deploy-apps.html#dep_apps). O pipeline para um app Cloud Foundry contém um estágio de Implementação que executa um comando cf.

O Cloud Foundry tenta [detectar o buildpack para uso do ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://docs.cloudfoundry.org/buildpacks/detection.html). Você pode especificar o [Buildpack](/docs/cfapps/byob.html#using-community-buildpacks) para usar no arquivo manifest na pasta raiz de seu app. Os buildpacks geralmente examinam artefatos fornecidos pelo usuário para determinar quais dependências transferir por download e como configurar aplicativos para comunicação com os serviços de limite. Para obter mais informações sobre arquivos manifest, veja [Manifest do aplicativo](/docs/cloud-foundry/deploy-apps.html#appmanifest).

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
[Regiões](/docs/overview/ibm-cloud.html#ov_intro-reg){: new_window}.

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

Um conjunto de propriedades do ambiente predefinidas fornece acesso a informações sobre o ambiente de execução da tarefa. Para obter uma lista completa das propriedades do ambiente predefinidas, veja [Propriedades e recursos do ambiente](/docs/services/ContinuousDelivery/pipeline_deploy_var.html).

Também é possível definir suas próprias propriedades do ambiente. Por exemplo, você pode definir uma propriedade `API_KEY` que passa uma chave de API que é usada para acessar recursos do {{site.data.keyword.Bluemix_notm}} por todos os scripts no pipeline.

É possível incluir os tipos de propriedades a seguir:

* **Texto**: uma chave de propriedade com um valor de linha única.
* **Área de texto**: uma chave de propriedade com um valor multilinhas.
* **Seguro**: uma chave da propriedade com um valor de linha única que é protegida com criptografia AES-128. O valor é exibido como asteriscos.
* **Propriedades**: um arquivo no repositório do projeto. Esse
arquivo pode conter diversas propriedades. Cada propriedade deve estar em sua própria
linha. Para separar os pares de chave/valor, use o sinal de igual (=). Coloque todos os valores de sequência entre aspas. Por exemplo, `MY_STRING="SOME STRING VALUE"`.

É possível examinar as propriedades do ambiente para uma tarefa de pipeline executando o
comando `env` no script da tarefa.
{:tip}

### Propriedades de pipeline
Para definir propriedades de pipeline, no menu overflow na página Pipeline, selecione **Configurar pipeline**.

![Menu overflow de pipeline](images/OverflowMenu.png)

Na guia **PROPRIEDADES DO AMBIENTE** na página de configuração de Pipeline, configure as propriedades do ambiente de nível de pipeline.

![Página de propriedades de pipeline](images/PipelineProperties.png)

### Propriedades do estágio
Para definir as propriedades do estágio, abra a página Configuração de estágio e clique na guia **PROPRIEDADES DO AMBIENTE**.

![Página de propriedades do estágio](images/StageProperties.png)

Também é possível passar propriedades do ambiente entre tarefas no mesmo estágio, exportando as propriedades. Por exemplo, é possível incluir o comando a seguir para usar a propriedade `$API_KEY` em outra tarefa dentro do estágio: `export API_KEY=<insert API key here>`
{:tip}

### Propriedades calculadas
É possível calcular os valores da propriedade do ambiente que são compartilhados entre os estágios criando um arquivo `build.properties` enquanto o estágio está em execução e, então, deixar que o próximo estágio execute o arquivo. Por exemplo, sua tarefa de construção pode incluir o comando a seguir no script de construção:

  `echo "IMAGE_NAME=${FULL_REPOSITORY_NAME}" >> $ARCHIVE_DIR/build.properties`

Todas as tarefas iniciam executando o arquivo `build.properties`, caso ele exista.

## Criando e utilizando artefatos
{: #artifacts}

As tarefas de construção buscam automaticamente o conteúdo na pasta atual na qual o script do usuário é executado. Se você não precisar de todo o conteúdo do repositório git para implementação posterior, será preferível que configure um diretório de saída explícito e, em seguida, copie ou crie os artefatos relevantes nesse local. Os scripts da tarefa são executados no resultado de construção (diretório de saída).

As tarefas que são implementadas no Cloud Foundry precisam especificar a chave de API da Plataforma de um usuário sob cuja autoridade as tarefas são executadas e a região, a organização e o espaço no qual implementar os artefatos. Se mais serviços são necessários para executar seu app, deve-se especificá-los no arquivo `manifest.yml`.

As tarefas de implementação que implementam no {{site.data.keyword.containerlong_notm}} precisam especificar a chave de API da Plataforma de um usuário sob cuja autoridade as tarefas são executadas, um Dockerfile e, opcionalmente, um gráfico do Helm.  

O script da tarefa é executado após a tarefa ter efetuado login no ambiente de destino usando a chave de API da Plataforma designada a ela (para que seja possível executar os comandos `cf push` ou `kubectl` no script).

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
sobre manifests de aplicativos](/docs/cloud-foundry/deploy-apps.html#appmanifest). Para integrar-se com o {{site.data.keyword.Bluemix_notm}}, seu
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
