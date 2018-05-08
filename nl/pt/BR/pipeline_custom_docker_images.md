---

Copyright:
  years: 2018
lastupdated: "2018-4-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Trabalhando com imagens customizadas do Docker
{: #custom_docker_images}

A imagem base do pipeline pode não suportar todos os requisitos de sua construção. Por exemplo, pode ser
necessário um controle de granularidade mais baixa sobre versões do Node, do Java ou de outras ferramentas. É possível
resolver esse problema incluindo uma primeira etapa em suas tarefas de pipeline que instala uma série de
novos pacotes e configura cuidadosamente variáveis de ambiente, como `PATH`, para configurar seu
ambiente. No entanto, uma abordagem melhor é usar o suporte do pipeline para executar uma "Imagem customizada do
Docker" como a base para sua tarefa.

Se você está usando um tipo de tarefa de Construção, Teste ou Implementação, é possível selecionar um
subtipo de Imagem Customizada do Docker para fornecer o nome da imagem do Docker para usar e especificar o
script a ser executado. Por exemplo, use as opções a seguir para executar uma tarefa de construção com o Maven
3.5.3 e IBM Java:

 ![Construção do Maven com imagem customizada](images/custom-image-maven-build.png)


## Especificando o nome da imagem do Docker
{: #docker_image_name}

O nome da imagem do Docker em tarefas de imagem customizada do Docker é projetado para funcionar na mesma maneira que os nomes de imagem funcionam com a CLI do Docker. O formato de um nome de imagem do Docker é: `[repository][:][tag]`. Por exemplo, para `docker run maven:3.5.3-ibmjava`, o nome da imagem do Docker é `maven:3.5.3-ibmjava`, em que `maven` é o repositório e `3.5.3-ibmjava` é a tag. Não há restrições sobre o nome da imagem do Docker que pode ser usado; qualquer imagem do docker válida funciona.

**Dica**: se o campo **Nome da imagem do Docker** não for concluído, a imagem base do pipeline padrão será usada. 

Por padrão, seu repositório no [Docker Hub ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://hub.docker.com/){: new_window} é procurado. Se você usa outro registro do Docker, como o IBM Cloud Registry, é possível usar o nome DNS completo. Também é possível usar o nome completo para imagens no Docker Hub. Por exemplo, `registry.hub.docker.com/library/maven:3.5.3-ibmjava`.

A `tag` para uma imagem do Docker é opcional. Se você não especificar uma tag, ela será configurada como `latest`, por padrão. Um valor padrão de `latest` é apenas um nome de tag que o proprietário do repositório deve gerenciar. Isso não significa que, cronologicamente, essa imagem do Docker é a imagem mais recente.

É possível localizar uma comunidade grande de repositórios no Docker Hub. A IBM hospeda uma série de repositórios públicos que a equipe do IBM Cloud usa em [https://hub.docker.com/u/ibmcom/ ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://hub.docker.com/u/ibmcom/){: new_window}. Os repositórios `ibmcom/ibmjava` e `ibmcom/ibmnode` são úteis para construção. 

## Usando um registro de imagem privada
{: #private_image_registry}

Se você está usando um registro privado que requer autenticação, deve-se configurar duas propriedades do ambiente de estágio adicionais: `DOCKER_USERNAME` e `DOCKER_PASSWORD`. É possível usar uma propriedade segura para mascarar seu `DOCKER_PASSWORD`. Antes que sua imagem seja puxada, a tarefa de imagem customizada do Docker usa suas credenciais de nome de usuário e senha para concluir um `docker login`.

Para a maioria dos registros, é possível usar o nome de usuário e a senha que foram fornecidos a você. Se você usa o IBM Cloud Registry para armazenar suas imagens privadas, deve-se usar uma chave API de plataforma para a autenticação. 

1. [Solicite uma chave API de plataforma ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/iam/#/apikeys){: new_window} e certifique-se de salvar a chave. 
1. Crie as duas propriedades do ambiente do estágio usando `iamapikey` para seu `DOCKER_USERNAME` e a Chave API da plataforma que você salvou para `DOCKER_PASSWORD`.

 ![Credenciais do IBM Cloud Registry](images/custom-image-private-repository.png)


## Especificando o script
{: #specify_script}

É possível usar o bloco **script** em tarefas de imagem customizada do Docker para criar um arquivo de script que seja executado em uma pasta de tarefa, semelhante ao modo como as tarefas de pipeline normais funcionam. 

**Importante**: o `ENTRYPOINT` e o `CMD` no Dockerfile de sua imagem do Docker são substituídos e não são chamados. Em alguns casos, isso pode significar a necessidade de incluir etapas de inicialização em seu script.

Tarefas de imagem customizada do Docker fornecem maior flexibilidade o modo de execução de seu script; especificamente, é possível controlar o interpretador de comandos. Normalmente, se a primeira linha do script começa com `#!` e com o nome de um interpretador de comandos, essa entrada é usada para executar os comandos na tarefa. Se você não especificar um interpretador de comandos, o shell padrão para a imagem do Docker será usado. Geralmente, `#!/bin/bash` ou `#!/bin/sh` são usados; interpretadores de comando de imagem para `awk`, `node` e `ruby` também funcionam, se você especifica uma imagem do Docker apropriada.
