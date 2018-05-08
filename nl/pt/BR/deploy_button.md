---

copyright:
  years: 2015, 2018
lastupdated: "2018-3-26"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# Criando um botão Implementar no {{site.data.keyword.Bluemix_notm}} {: #deploy-button}

O botão Implementar no {{site.data.keyword.Bluemix_notm}} é uma maneira eficiente de compartilhar seu app público de origem Git para que outras pessoas possam experimentar com o código e implementá-lo no IBM {{site.data.keyword.Bluemix_notm}} usando uma cadeia de ferramentas. O botão requer configuração mínima e é possível inseri-lo em qualquer lugar que suporte marcação. Qualquer pessoa que clica no botão cria uma cópia clonada do código em um novo repositório Git (repositório) para que seu app original não seja afetado.
{: shortdesc}

Quando alguém clica em seu botão, ocorrem estas ações:

1. Se a pessoa não tiver uma conta ativa do {{site.data.keyword.Bluemix_notm}}, ela deverá criar uma conta. Ela pode criar uma conta para teste ou uma conta real.

2. A pessoa pode selecionar uma região, organização, espaço e nome de app clicando no ícone {{site.data.keyword.deliverypipeline}}. O nome do app sugerido é o mesmo que o nome da cadeia de ferramentas, que é construído do nome de seu repositório Git original e a horário. O nome da cadeia de ferramentas também pode ser editado.

3. É criada uma cadeia de ferramentas que inclui um novo clone privado de seu repositório Git, um pipeline para construir e implementar mudanças de código, o Eclipse Orion {{site.data.keyword.webide}} para editar código na Nuvem e um rastreador de problemas.

  **Dica**: se o diretório `.bluemix` contém um arquivo `toolchain.yml`, o arquivo é usado para especificar as integrações de ferramenta para a cadeia de ferramentas. Para obter mais informações sobre o arquivo `toolchain.yml`, veja [Criando cadeias de ferramentas customizadas](/docs/services/ContinuousDelivery/toolchains_custom.html#toolchains_custom){: new_window}.

4. Se o app requer um arquivo de construção, o arquivo de construção é detectado automaticamente e o app é construído.

5. Se um pipeline é configurado para o processo de construção e implementação, um arquivo `pipeline.yml` é usado para implementar o app.

6. Se o app requer um contêiner, um arquivo `pipeline.yml` que define o serviço IBM Containers e um Dockerfile que define uma imagem são usados para implementar o app em um contêiner do {{site.data.keyword.Bluemix_notm}}.

7. O app é implementado na organização do {{site.data.keyword.Bluemix_notm}} que a pessoa selecionou.

## Exemplos do botão {: #button-examples}

Veja um exemplo do botão de app para um repositório {{site.data.keyword.gitrepos}} público:

[![Implementar no Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://git.ng.bluemix.net/idsorg/sample-java-cloudant){:new_window}

Veja um exemplo do botão de app para um repositório GitHub público:

[![Implementar no Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/open-toolchain/starfighter){:new_window}

## Criando um botão {: #create-button}

Para criar um botão Implementar no {{site.data.keyword.Bluemix_notm}}, copie e modifique um dos modelos de fragmento a seguir. Especifique um repositório Git e ramificação na URL.

### Criando um botão em HTML

Para criar um botão em HTML, copie este fragmento e insira uma URL do repositório Git público e ramificação.

```HTML
<a href="https://bluemix.net/deploy?repository=<git_repository_URL>&branch=<git_branch>"><img src="https://bluemix.net/deploy/button.png" alt="Implementar no Bluemix"></a>
```
{: codeblock}

Se você não incluir o parâmetro `branch` na URL do repositório de seu fragmento, o botão Implementar no Bluemix será padronizado com a ramificação principal do repositório.

### Criando um botão em Markdown

Para criar um botão em Markdown, copie este fragmento e insira uma URL do repositório Git público e ramificação.

```Markdown
[![Implementar no Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=<git_repository_URL>&branch=<git_branch>)
```
{: codeblock}

Se você não incluir o parâmetro `branch` na URL do repositório de seu fragmento, o botão Implementar no Bluemix será padronizado com a ramificação principal do repositório.

### Usando os fragmentos do botão {: #button-snippet}

Depois de criar um fragmento do botão Implementar no Bluemix, é possível inseri-lo em blogs, artigos, wikis, arquivos leia-me ou em qualquer outro lugar no qual deseje promover seu app.

Ao customizar o fragmento para o botão Implementar no {{site.data.keyword.Bluemix_notm}}, considere que ambos os modelos usam um caminho padrão para uma imagem de botão externo em formato PNG e em inglês.

* Se você preferir usar uma imagem SVG para o botão em vez de PNG, mude o caminho para a imagem de botão que é usada no fragmento para `https://bluemix.net/deploy/button.svg`.

* Se você preferir usar uma imagem para o botão, mude o caminho da imagem de botão que é usada no fragmento para `https://bluemix.net/deploy/button_x2.png`. Essa imagem é o dobro do tamanho de uma padrão.

* Se você preferir armazenar a imagem localmente, será possível fazer download da imagem e armazená-la no repositório Git. Ajuste o caminho para usar o local relativo da imagem.

* Se desejar usar uma versão traduzida do botão, será possível referenciá-la remotamente ou fazer download dela em [ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button){:new_window}.

## Considerações de repositório {: #button-repo}

Revise estas considerações para o repositório que você usa em seu botão Implementar no {{site.data.keyword.Bluemix_notm}}.


## Requisitos do arquivo de construção
{: build_file}

Se o app deve ser construído antes de poder ser implementado, deve-se incluir um arquivo de construção em seu repositório. Se um arquivo do script de construção é detectado no diretório-raiz do repositório, uma construção automatizada do código é acionada antes da implementação.

Os construtores suportados incluem:

* [Ant ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo"):](http://ant.apache.org/manual/using.html){:new_window} `build.xml`, que constrói a saída para a pasta `./output/`
* [Gradle ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo"):](http://docs.cloudfoundry.org/buildpacks/java/build-tool-int.html#gradle){:new_window} `/build.gradle`, que constrói a saída para a pasta `.` .
* [Grunt ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo"):](http://gruntjs.com/getting-started#the-gruntfile){:new_window} `/Gruntfile.js`, que constrói a saída para a pasta `.` .
* [Maven ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo"):](http://docs.cloudfoundry.org/buildpacks/java/build-tool-int.html#maven){:new_window} `/pom.xml`, que constrói a saída para a pasta `./target/`

### Requisitos do arquivo de pipeline
{: pipeline_file}

Para configurar o pipeline para a cadeia de ferramentas em um diretório `.bluemix`, inclua um arquivo `pipeline.yml`. Para cada arquivo `pipeline.yml` nesse diretório, um pipeline é criado quando a cadeia de ferramentas é instanciada.

Se você não tiver o arquivo `pipeline.yml` no diretório `.bluemix`,
o botão Implementar no {{site.data.keyword.Bluemix_notm}} criará um pipeline padrão com dois
estágios: um estágio de Construção e um estágio de Implementação que implementa no Cloud Foundry.

Para criar um arquivo de pipeline, consulte o arquivo de exemplo nas [instruções de pipeline da cadeia de ferramentas customizada](toolchains_custom.html#toolchains_custom_pipeline_yml). Assim como quando define um pipeline na interface da web, você define um pipeline em texto criando estágios e tarefas, configurando entradas e variáveis de ambiente e incluindo scripts. Também é possível ver vários arquivos de pipeline mais complexo [neste projeto de demonstração](https://github.com/open-toolchain/toolchain-demo/tree/master/.bluemix).

### Requisitos do Container Dockerfile
{: container_dockerfile}

Para implementar um app em um contêiner usando o IBM Containers, deve-se incluir um Dockerfile no diretório-raiz do repositório e, em um diretório `.bluemix`, inclua um arquivo `pipeline.yml`.

O Dockerfile age como uma espécie de script de construção para o app. Se um Dockerfile é detectado no repositório, o app é construído automaticamente em uma imagem antes que seja implementado em um contêiner. Se o próprio app precisar ser construído antes de o app ser construído em uma imagem, inclua um script de construção para o app e um Dockerfile.

Para saber mais sobre a criação de Dockerfiles, veja a [documentação do Docker ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://docs.docker.com/reference/builder/){:new_window}.  Para seguir as instruções passo a passo usando um modelo de cadeia de ferramentas para implementação no Kubernetes, consulte [Tutorial: usar a cadeia de ferramentas "Desenvolver um app do Kubernetes" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-toolchain?task=0){:new_window} ou [Tutorial: usar a cadeia de ferramentas "Desenvolver um app do Kubernetes com o Helm" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-with-helm-toolchain?task=0){:new_window}.  
   Para aprender sobre como transferir seu app Cloud Foundry para um cluster do Kubernetes, consulte [Tutorial: transferir seu app do Cloud Foundry para implementação no Kubernetes ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/port-an-app-from-cf-to-kubernetes-in-a-toolchain?task=0){:new_window}.  

Para criar um `pipeline.yml` manualmente que seja especificamente para contêineres

Para criar um `pipeline.yml` manualmente que seja especificamente para contêineres, veja os [exemplos em GitHub ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/Puquios/){:new_window}.

## Requisitos do arquivo de manifesto (para apps implementados no Cloud Foundry)
{: #manifest_files}

Um arquivo `manifest.yml` não precisa estar em seu repositório. No entanto, se seu app precisar que outros serviços sejam executados, deve fornecer um arquivo manifest que declare esses serviços.

Para saber mais sobre arquivos manifest, consulte [Manifesto do aplicativo](/docs/cfapps/depapps.html#appmanifest).
