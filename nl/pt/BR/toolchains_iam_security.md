---

copyright:
  years:  2018
lastupdated: "2018-11-14"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Gerenciando o acesso de usuário às cadeias de ferramentas com o Identity and Access Management

O acesso às cadeias de ferramentas em grupos de recursos para usuários em sua conta é controlado pelo Identity and Access Management (IAM) do {{site.data.keyword.Bluemix_notm}}. 

** Notas **: 

* O acesso de usuário às instâncias da cadeia de ferramentas e às instâncias do serviço {{site.data.keyword.contdelivery_short}} é gerenciado separadamente. Para obter mais informações sobre como gerenciar o acesso de usuário a instâncias do serviço {{site.data.keyword.contdelivery_short}} em grupos de recursos, consulte [Gerenciando o acesso de usuário ao {{site.data.keyword.contdelivery_short}} com o Identity and Access Management](/docs/services/ContinuousDelivery/cd_iam_security.html){: new_window}.

* O acesso de usuário às cadeias de ferramentas em organizações do Cloud Foundry é gerenciado de forma diferente do acesso do usuário às instâncias do serviço {{site.data.keyword.contdelivery_short}} em grupos de recursos. Para obter mais informações sobre como gerenciar o acesso de usuário às cadeias de ferramentas em organizações do Cloud Foundry, consulte [Gerenciando o acesso às cadeias de ferramentas em organizações do Cloud Foundry](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_orgs.html){: new_window}.

Cada usuário que acessa cadeias de ferramentas em sua conta deve ter uma política de acesso designada com uma função de usuário do IAM definida. Essa política determina quais ações o usuário pode executar dentro do contexto do serviço ou instância que você seleciona. As ações permitidas são customizadas e definidas pelo serviço {{site.data.keyword.Bluemix_notm}} como operações que têm permissão para serem executadas no serviço. As ações são, então, mapeadas para funções de usuário do IAM.

As políticas permitem que o acesso seja concedido em diferentes níveis, incluindo: 

* Acesso em todas as instâncias do serviço em sua conta
* Acesso a uma instância de serviço individual em sua conta
* Acesso a um recurso específico dentro de uma instância
* Acesso a todos os serviços ativados para o IAM em sua conta

Depois de definir o escopo da política de acesso, você designa uma função. Revise as tabelas a seguir que descrevem quais ações cada função permite dentro de cadeias de ferramentas.

A tabela a seguir detalha as ações que são mapeadas para funções de gerenciamento de plataforma. As funções de gerenciamento de plataforma permitem que os usuários executem tarefas em recursos de serviço no nível de plataforma, por exemplo, designar acesso de usuário para o serviço, criar ou excluir IDs de serviço, criar instâncias e ligar instâncias aos aplicativos.

| Função de gerenciamento da plataforma | Descrição das acções | Ações de exemplo|
|:-----------------|:-----------------|:-----------------|
| Visualizador, Operador | Visualizar cadeias de ferramentas e pipelines de entrega. Execute pipelines de entrega. | <ul><li>Clique em uma cadeia de ferramentas para abrir a sua página de Visão geral.</li><li>Clique no ícone **Executar estágio** do estágio em que a tarefa de pipeline está.</li></ul> |
| Editor, Administrador | Crie, visualize, atualize e exclua cadeias de ferramentas e pipelines de entrega. |<ul><li>No painel DevOps, na página **Cadeias de ferramentas**, clique em **Criar uma cadeia de ferramentas**.</li><li>No painel do DevOps, na página **Cadeias de ferramentas**, clique na cadeia de ferramentas para abrir sua página Visão geral.</li><li>No painel do DevOps, na página **Cadeias de ferramentas**, clique na cadeia de ferramentas a ser excluída. Clique no menu **Mais ações**, que está próximo a **Visualizar app**. Clique em **Excluir**.</li></ul> |
{: caption="Tabela 1. Funções e ações do usuário do IAM" caption-side="top"}

 Para cadeias de ferramentas, existem as seguintes ações:

| Ação | Operação em serviço | Papel
|:-----------------|:-----------------|:--------------|
| criar | Crie uma cadeia de ferramentas em um grupo de recursos. | Administrador, Editor |
| atualizar | Atualize uma cadeia de ferramentas em um grupo de recursos. Por exemplo, renomeie a cadeia de ferramentas. Mude os pipelines de entrega que são ligados a cadeias de ferramentas em um grupo de recursos. | Administrador, Editor |
| update_plan | Não se aplica. | Administrador, Editor |
| excluir | Exclua uma cadeia de ferramentas de um grupo de recursos. | Administrador, Editor |
| recuperar | Visualize os detalhes para uma cadeia de ferramentas em um grupo de recursos. Visualize e execute pipelines de entrega que são ligados a cadeias de ferramentas em um grupo de recursos. | Administrador, Editor, Operador, Visualizador |
| ligações de lista | Visualize as integrações de ferramentas que são ligadas a uma cadeia de ferramentas em um grupo de recursos. | Administrador, Editor, Visualizador |
| criar-ligações | Inclua uma integração de ferramenta em uma cadeia de ferramentas em um grupo de recursos. | Administrador, Editor |
| delete-bindings | Remova uma integração de ferramenta de uma cadeia de ferramentas em um grupo de recursos. | Administrador, Editor |
{: caption="Tabela 2. Operações e Operações de Serviço" caption-side="top"}

Para obter informações sobre como designar funções de usuário na IU, consulte [Gerenciando o acesso ao IAM](/docs/iam/mngiam.html#iammanidaccser).

<!--This link is not live in production yet. Use https://console.bluemix.net/docs/iam/iamusermanage.html#iamusermanage until the link above is available in production.-->
