---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: IBM Cloud Continuous Delivery, private workers integration

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}


# Trabalhando com {{site.data.keyword.deliverypipeline}} Private Workers
{: #private-workers}

O {{site.data.keyword.deliverypipeline}} usa trabalhadores públicos e privados para executar tarefas de pipeline. Por padrão, as tarefas de pipeline são executadas usando trabalhadores públicos na infraestrutura compartilhada pública gerenciada pela IBM.
{: shortdesc}

Em certos cenários, seu {{site.data.keyword.deliverypipeline}} pode requerer acesso a recursos internos ou no local. Nessas situações, é possível conectar e integrar um {{site.data.keyword.deliverypipeline}} Private Worker para executar em sua própria infraestrutura do Kubernetes.

## Pré-requisitos
{: #private_workers_prereqs}

Antes de configurar um trabalhador privado, assegure-se de ter os recursos a seguir disponíveis:

* Um cluster Kubernetes. Deve-se ter um cluster para instalar um trabalhador privado. É possível fornecer seu próprio cluster ou é possível [configurar um cluster](https://cloud.ibm.com/kubernetes/clusters){:external} por meio do {{site.data.keyword.containerlong_notm}}.

* Uma cadeia de ferramentas com um pipeline que contenha pelo menos um estágio. É possível usar uma cadeia de ferramentas existente ou [criar uma cadeia de ferramentas](https://cloud.ibm.com/devops/create){:external}.

## Configurando um {{site.data.keyword.deliverypipeline}} Private Worker
{: #set_up_private_worker}

Conclua as etapas a seguir para configurar um trabalhador privado:

1. Configure a integração de ferramenta do {{site.data.keyword.deliverypipeline}} Private Worker para sua cadeia de ferramentas.
2. Configure seu cluster Kubernetes com um trabalhador privado.
3. Use o trabalhador privado em seu pipeline.

### Configurando a integração de ferramenta do {{site.data.keyword.deliverypipeline}} Private Worker
{: #configure_private_worker_integration}

Conclua as etapas a seguir para configurar a integração de ferramenta do {{site.data.keyword.deliverypipeline}} Private Worker para sua cadeia de ferramentas:

1. Se você estiver configurando essa integração de ferramenta enquanto estiver criando a cadeia de ferramentas, na seção Integrações configuráveis, clique em **{{site.data.keyword.deliverypipeline}} Private Worker**.
1. Se você tiver uma cadeia de ferramentas e estiver incluindo essa integração de ferramenta nela, no painel do DevOps, na página Cadeias de ferramentas, clique na cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, em **Visão geral**.

 a. Clique em **Incluir uma ferramenta**.

 b. Na seção Integrações de ferramenta, clique em **{{site.data.keyword.deliverypipeline}} Private Worker**.

1. Digite um nome para a integração de ferramenta. Esse nome identifica um conjunto de trabalhadores privados na guia **Trabalhadores** do estágio de pipeline.
1. Digite sua chave de API do ID de Serviço para autenticar o acesso à fila de trabalho em que um ou mais trabalhadores privados podem procurar trabalho. Se você não tiver uma chave de API de ID de Serviço, clique em **Criar** para gerar uma para esse trabalhador privado.
1. Clique em
**Criar integração**.
1. Em sua cadeia de ferramentas, clique em **{{site.data.keyword.deliverypipeline}} Private Worker** para visualizar uma lista de todos os trabalhadores registrados usando uma chave de API que é associada a esse ID de Serviço.

Para obter mais informações sobre a integração de ferramenta **{{site.data.keyword.deliverypipeline}} Private Worker**, consulte [Configurando o {{site.data.keyword.deliverypipeline}} Private Worker](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations#privateworker).

### Configurando seu cluster Kubernetes
{: #configure_kubernetes_cluster}

Configure seu cluster Kubernetes com um trabalhador privado:

1. No painel do DevOps, na página **Cadeias de ferramentas**, clique em uma cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, clique em **Visão geral**.
1. Clique no cartão para a integração de ferramenta do {{site.data.keyword.deliverypipeline}} Private Worker que deseja configurar.
1. Clique em **Introdução** e, em seguida, siga as etapas para instalar e registrar um trabalhador privado em seu cluster Kubernetes.

### Usando o {{site.data.keyword.deliverypipeline}} Private Worker em seu pipeline
{: #use_private_worker_pipeline}

Conclua as etapas a seguir para usar o trabalhador privado em seu pipeline:

1. No painel do DevOps, na página **Cadeias de ferramentas**, clique em uma cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, clique em **Visão geral**.
1. Clique no cartão para o pipeline com o qual você deseja usar o trabalhador privado.
1. Na página Pipeline, no estágio, clique no ícone **Configuração de estágio** e, em seguida, clique em **Configurar estágio**.
1. Clique na guia **Trabalhadores**.
1. Selecione o trabalhador privado que você deseja usar em seu pipeline. 

 Por padrão, as tarefas em um estágio de pipeline são executadas usando um conjunto de trabalhadores compartilhados gerenciados pela IBM na região em que o pipeline está definido.
 {: tip}
 
1. Clique em **Salvar**.
1. É possível executar manualmente seu estágio ou esperar que um acionador execute as tarefas no estágio usando o trabalhador privado especificado no cluster Kubernetes associado. É possível visualizar a saída do arquivo de log para as tarefas a fim de determinar qual trabalhador foi usado.  


## Modificando as credenciais de integração de ferramenta do {{site.data.keyword.deliverypipeline}} Private Worker
{: #modify_private_worker}

Após configurar seu trabalhador privado, será possível atualizar as credenciais que são usadas para a integração de ferramenta. Você pode desejar mudar essas credenciais se elas forem excluídas, estiverem expiradas ou comprometidas. É possível atualizar as credenciais criando um novo ID de Serviço ou atualizando a chave de API.

### Criando um ID de Serviço
{: #create_service_id}

Conclua as etapas a seguir para criar um ID de Serviço:

1. No painel do DevOps, na página **Cadeias de ferramentas**, clique em uma cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, clique em **Visão geral**.
1. No cartão para a integração de ferramenta de trabalhadores privados que você deseja modificar, clique no menu para acessar as opções de configuração.
1. Clique em **Criar**.
1. Insira um nome e uma descrição para o ID de Serviço.
1. Clique em **Salvar integração**.
1. No painel do DevOps, na página **Cadeias de ferramentas**, clique em uma cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, clique em **Visão geral**.
1. Clique no cartão para a integração de ferramenta do {{site.data.keyword.deliverypipeline}} Private Worker para o qual você deseja especificar as novas credenciais de usuário.
1. Clique em **Introdução** e conclua as etapas 2 e 3 para registrar e verificar o trabalhador privado em seu cluster.

### Atualizando a chave de API
{: #update_api_key}

Conclua as etapas a seguir para atualizar a chave de API para uso com a integração de ferramenta do {{site.data.keyword.deliverypipeline}} Private Worker:

1. No painel do DevOps, na página **Cadeias de ferramentas**, clique em uma cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, clique em **Visão geral**.
1. No cartão para a integração de ferramenta do {{site.data.keyword.deliverypipeline}} Private Worker que você deseja modificar, clique no menu para acessar as opções de configuração.
1. Especifique sua nova chave de API. 
1. Clique em **Salvar integração**.

## Excluindo um {{site.data.keyword.deliverypipeline}} Private Worker
{: #delete_private_worker}

Conclua as etapas a seguir para excluir um trabalhador privado:

1. Exclua o trabalhador privado do conjunto de trabalhadores.
1. Exclua o trabalhador privado do seu cluster Kubernetes.

### Excluindo um {{site.data.keyword.deliverypipeline}} Private Worker do conjunto de trabalhadores

Conclua as etapas a seguir para excluir o trabalhador privado do conjunto de trabalhadores:

1. No painel do DevOps, na página **Cadeias de ferramentas**, clique em uma cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, clique em **Visão geral**.
1. Clique no cartão para a integração de ferramenta do {{site.data.keyword.deliverypipeline}} Private Worker que deseja configurar.
1. Clique em **Visão geral**.
1. Clique no menu para o trabalhador privado que deseja excluir a fim de acessar as opções de configuração.
1. Clique em **Remover** e, em seguida, clique em **Confirmar**.

### Excluindo um {{site.data.keyword.deliverypipeline}} Private Worker do seu cluster Kubernetes

Conclua as etapas a seguir para excluir o trabalhador privado do seu cluster:

1. Clique no cartão para a integração de ferramenta do {{site.data.keyword.deliverypipeline}} Private Worker que deseja configurar.
1. Clique em **Introdução** e siga as etapas para excluir o trabalhador privado do seu cluster.

## Excluindo a integração de ferramenta do {{site.data.keyword.deliverypipeline}} Private Worker
{: #delete_private_workers_tool_integration}

Se você excluir a integração de ferramenta do {{site.data.keyword.deliverypipeline}} Private Worker da sua cadeia de ferramentas, a exclusão não poderá ser desfeita.
{: important}

Conclua as etapas a seguir para excluir uma integração de ferramenta do {{site.data.keyword.deliverypipeline}} Private Worker:

1. No painel do DevOps, na página **Cadeias de ferramentas**, clique em uma cadeia de ferramentas para abrir sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas** e, em seguida, clique em **Visão geral**.
1. No cartão para a integração de ferramenta do {{site.data.keyword.deliverypipeline}} Private Worker que você deseja excluir, clique no menu para acessar as opções de configuração.
1. Para excluir a integração de ferramenta de sua cadeia de ferramentas, clique em **Excluir**.
1. Confirme clicando em **Excluir**. A integração de ferramenta do {{site.data.keyword.deliverypipeline}} Private Worker é removida da cadeia de ferramentas e não está mais disponível na guia **Trabalhadores** na página Configuração de estágio de pipeline de entrega.

Se você excluir a integração de ferramenta do {{site.data.keyword.deliverypipeline}} Private Worker de uma cadeia de ferramentas e o trabalhador privado estiver configurado para um estágio de pipeline, ela ainda será listada na guia **Trabalhadores** da página Configuração de estágio. Entretanto, o trabalhador privado é desativado e rotulado REMOVED. Deve-se selecionar um trabalhador privado diferente (se existir um) ou usar um trabalhador público no lugar.
{: tip}
