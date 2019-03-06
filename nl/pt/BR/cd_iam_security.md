---

copyright:
  years:  2018, 2019
lastupdated: "2019-2-1"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Gerenciando o acesso de usuário à Entrega Contínua com o Identity and Access Management
{: #cd-iam-security}

O acesso às instâncias do serviço {{site.data.keyword.contdelivery_full}} em grupos de recursos para usuários em sua conta é controlado pelo Identity and Access Management (IAM) do {{site.data.keyword.Bluemix_notm}}. 

** Notas **: 

* O acesso de usuário às instâncias de serviço e às instâncias de cadeia de ferramentas do {{site.data.keyword.contdelivery_short}} é gerenciado separadamente. Para obter mais informações sobre como gerenciar o acesso de usuário a cadeias de ferramentas em grupos de recursos, consulte [Gerenciando o acesso de usuário às cadeias de ferramentas com o Identity and Access Management](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security){: new_window}.

* O acesso de usuário às cadeias de ferramentas em organizações do Cloud Foundry é gerenciado de forma diferente do acesso do usuário às cadeias de ferramentas em grupos de recursos. Para obter mais informações sobre como gerenciar o acesso de usuário às cadeias de ferramentas em organizações do Cloud Foundry, consulte [Gerenciando o acesso às cadeias de ferramentas em organizações do Cloud Foundry](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs){: new_window}.

A todo usuário que acessa o serviço {{site.data.keyword.contdelivery_short}} em sua conta deve ser designada uma política de acesso com uma função de usuário do IAM definida. Essa política determina quais ações o usuário pode executar dentro do contexto do serviço ou instância que você seleciona. As ações permitidas são customizadas e definidas pelo serviço {{site.data.keyword.Bluemix_notm}} como operações que têm permissão para serem executadas no serviço. As ações são, então, mapeadas para funções de usuário do IAM.

As políticas permitem que o acesso seja concedido em diferentes níveis. Algumas das opções incluem o seguinte: 

* Acesso em todas as instâncias do serviço em sua conta
* Acesso a uma instância de serviço individual em sua conta
* Acesso a um recurso específico dentro de uma instância
* Acesso a todos os serviços ativados para o IAM em sua conta

Depois de definir o escopo da política de acesso, você designa uma função. Revise as tabelas a seguir que descrevem quais ações cada função permite dentro do serviço {{site.data.keyword.contdelivery_short}}.

A tabela a seguir detalha as ações que são mapeadas para funções de gerenciamento de plataforma. As funções de gerenciamento de plataforma permitem que os usuários executem tarefas em recursos de serviço no nível de plataforma, por exemplo, designar acesso de usuário para o serviço, criar ou excluir IDs de serviço, criar instâncias e ligar instâncias aos aplicativos.

| Função de gerenciamento da plataforma | Descrição das acções | Ações de exemplo|
|:-----------------|:-----------------|:-----------------|
| Visualizador, Operador | Visualize instâncias do serviço do  {{site.data.keyword.contdelivery_short}} . | <ul><li>Clique em uma instância do serviço {{site.data.keyword.contdelivery_short}} para abrir o seu painel.</li></ul>|
| Editor, Administrador | Crie, visualize, atualize, modifique o plano e exclua instâncias do serviço {{site.data.keyword.contdelivery_short}}. |<ul><li>Provisione uma instância do {{site.data.keyword.contdelivery_short}} em um grupo de recursos.</li><li>Exclua uma instância do {{site.data.keyword.contdelivery_short}} de um grupo de recursos.</li><li>Mude um plano de instância do {{site.data.keyword.contdelivery_short}} de Lite para Professional.</li></ul> |
| Administrador | Atualize a lista de Usuários autorizados.| <ul><li>Inclua um usuário na lista de Usuários autorizados.</li><li>Remova um usuário da lista de Usuários autorizados.</li></ul> |
{: caption="Tabela 1. Funções e ações do usuário do IAM" caption-side="top"}

 Para  {{site.data.keyword.contdelivery_short}}, existem as seguintes ações:

| Ação | Operação em serviço | Papel
|:-----------------|:-----------------|:--------------|
| criar | Provisione uma instância do serviço {{site.data.keyword.contdelivery_short}} em um grupo de recursos. | Administrador, Editor |
| atualizar | Atualize uma instância do serviço {{site.data.keyword.contdelivery_short}} em um grupo de recursos. Por exemplo, renomeie a instância de serviço. | Administrador, Editor |
| update_plan | Mude o plano para a instância do serviço {{site.data.keyword.contdelivery_short}} em um grupo de recursos. | Administrador, Editor |
| excluir | Exclua uma instância do serviço {{site.data.keyword.contdelivery_short}} de um grupo de recursos. | Administrador, Editor |
| recuperar | Visualize uma instância do serviço {{site.data.keyword.contdelivery_short}} em um grupo de recursos. | Administrador, Editor, Operador, Visualizador |
| add-auth-users | Inclua entradas na lista de Usuários autorizados na guia Gerenciar dentro da instância do serviço {{site.data.keyword.contdelivery_short}}. | Administrador, Transcritor, Gerente |
| remove-auth-users | Remova as entradas da lista de Usuários autorizados na guia Gerenciar dentro da instância do serviço {{site.data.keyword.contdelivery_short}}. | Administrador, Transcritor, Gerente |
{: caption="Tabela 2. Operações e Operações de Serviço" caption-side="top"}

A tabela a seguir detalha as ações que são mapeadas para as funções de acesso de serviço. As funções de acesso de serviço permitem que os usuários acessem o {{site.data.keyword.contdelivery_short}}, bem como a capacidade de chamar a API do {{site.data.keyword.contdelivery_short}}.

| Função de Acesso de Serviço | Descrição das acções | Ações de exemplo|
|:-----------------|:-----------------|:-----------------|
| Gravador, Gerente | Inclua e remova usuários da lista de Usuários autorizados na guia Gerenciar dentro de uma instância do serviço {{site.data.keyword.contdelivery_short}}. | <ul><li>Incluir usuário autorizado.</li><li>Remova o usuário autorizado.</li></ul>|
{: caption="Tabela 3. Funções e ações de acesso do serviço IAM" caption-side="top"}

Para obter informações sobre como designar funções de usuário na IU, consulte [Gerenciando o acesso ao IAM](/docs/iam?topic=iam-iammanidaccser).

<!--This link is not live in production yet. Use https://console.bluemix.net/docs/iam/iamusermanage.html#iamusermanage until the link above is available in production.-->
