---

copyright:
  years: 2015, 2018

lastupdated: "2018-12-6"


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

# Criando cadeias de ferramentas
{: #toolchains_getting_started}

Uma *cadeia de ferramentas* é um conjunto de integrações de ferramentas que suporta tarefas de desenvolvimento, de implementação e de operações. O
poder coletivo de uma cadeia de ferramentas é maior que a soma de suas integrações de ferramentas individuais.
{: shortdesc}

As cadeias de ferramentas abertas estão disponíveis nos ambientes Public e Dedicated no {{site.data.keyword.Bluemix}}. É possível criar uma cadeia de ferramentas de duas formas: usar um modelo para criar uma cadeia de ferramentas ou criar uma cadeia de
ferramentas a partir de um app.

Cada cadeia de ferramentas é associada a um grupo de recursos ou organização (org.) específicos. Se uma cadeia de ferramentas estiver associada a um grupo de recursos, qualquer usuário que tenha permissão de Visualizador do Identity and Access Management (IAM) para o recurso de cadeia de ferramentas ou o grupo de recursos que a contenha poderá acessar a cadeia de ferramentas. Se a cadeia de ferramentas estiver associada a uma organização, qualquer usuário que for um membro dessa organização poderá ser incluído na lista de controle de acesso para qualquer uma de suas cadeias de ferramentas associadas. Para obter mais informações sobre o controle de acesso para cadeias de ferramentas em organizações do Cloud Foundry, consulte [Gerenciando o acesso às cadeias de ferramentas em organizações do Cloud Foundry](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_orgs){: new_window}. Para obter mais informações sobre o controle de acesso para cadeias de ferramentas em grupos de recursos, consulte [Gerenciando o acesso às cadeias de ferramentas em grupos de recursos](/docs/services/ContinuousDelivery/toolchains_using.html#managing_access_resource_groups){: new_window}.

##Criando uma cadeia de ferramentas com base em um modelo   
{: #creating_a_toolchain_from_a_template}

É possível usar um modelo como um ponto de início para [criar uma cadeia de ferramentas ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/devops/create){: new_window} que inclui um conjunto específico de integrações de ferramentas. Saiba mais sobre como usar os modelos no [IBM Cloud Garage Method ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/category/tools){:new_window}.

1. Se você usar o {{site.data.keyword.Bluemix_notm}} Public, efetue login no [{{site.data.keyword.Bluemix_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://cloud.ibm.com){:new_window}.
1. Se você usar o {{site.data.keyword.Bluemix_notm}} Dedicated, efetue login no ambiente Dedicated no {{site.data.keyword.Bluemix_notm}}.
1. No menu na barra de menus do {{site.data.keyword.Bluemix_notm}}, clique em **DevOps**.
1. No painel DevOps, na página **Cadeias de ferramentas**, clique em **Criar uma cadeia de ferramentas**.
1. Na página **Criar uma cadeia de ferramentas**, clique em um
modelo de cadeia de ferramentas.
1. Revise o diagrama da cadeia de ferramentas que você está prestes a criar. O diagrama
mostrará cada integração de ferramenta em sua fase de ciclo de vida na cadeia de ferramentas.

 Alguns dos modelos de cadeia de ferramentas têm múltiplas instâncias de uma integração de ferramenta. Por exemplo, o modelo de cadeia de ferramentas de Microsserviços no {{site.data.keyword.Bluemix_notm}} Public contém três instâncias do GitHub e três instâncias do Delivery Pipeline, uma para cada um dos três microsserviços.
 {: tip}

 O diagrama na imagem a seguir é um exemplo. Ao criar uma cadeia de ferramentas, o diagrama mostra cada integração de ferramenta que faz parte da cadeia de ferramentas.
 ![Diagrama de cadeia de ferramentas](images/toolchain_diagram2.png)

1. Revise as informações padrão para as configurações da cadeia de ferramentas:

 * O nome da cadeia de ferramentas as identifica em
{{site.data.keyword.Bluemix_notm}}. Se você desejar usar um nome diferente, mude o nome da cadeia de ferramentas.
 * A região na qual criar a cadeia de ferramentas. Se você desejar usar uma região diferente, selecione-a na lista de regiões disponíveis.
 * A organização ou o grupo de recursos no qual criar a cadeia de ferramentas. Clique no link para alternar entre a seleção de grupos de recursos e de organizações. Se você desejar usar uma organização ou um grupo de recursos diferente, selecione essa opção diferente na lista de organizações ou de grupos de recursos disponíveis.
 
   Os grupos de recursos estão disponíveis nas regiões Sul dos EUA, Leste dos EUA, Reino Unido, Alemanha e Tóquio. As organizações do Cloud Foundry são suportadas nas regiões Sul dos EUA, Reino Unido e Alemanha.
   {: important}

1. Na seção Integrações de ferramentas, selecione cada integração de ferramenta que deseja configurar para sua cadeia de ferramentas. Algumas integrações de ferramentas não requerem configuração. Para obter informações sobre como configurar as integrações de ferramentas, consulte
[Configurando
integrações de ferramentas](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}.
1. Clique em **Criar**. Várias etapas são executadas automaticamente para configurar sua cadeia de ferramentas. As integrações de ferramentas configuradas são diferentes, dependendo de qual modelo de cadeia de ferramentas você selecionou e se está usando o {{site.data.keyword.Bluemix_notm}} Public ou o {{site.data.keyword.Bluemix_notm}} Dedicated. Por exemplo, quando você cria uma cadeia de ferramentas de Microsserviços no {{site.data.keyword.Bluemix_notm}} Public, estas etapas são executadas:

 * A cadeia de ferramentas é criada.
 * Se você tiver configurado o Delivery Pipeline, os pipelines serão criados e acionados.
 * Se você tiver configurado o Sauce Labs, a cadeia de ferramentas será configurada para incluir tarefas de teste do Sauce Labs nos pipelines.
 * Se tiver configurado o PagerDuty, a cadeia de ferramentas será configurada para enviar notificações de alerta para o serviço PagerDuty especificado.
 * Se tiver configurado o Slack, a cadeia de ferramentas será configurada para enviar notificações sobre o status de implementação para o canal Slack especificado.
 * Se tiver configurado a integração de ferramenta do código-fonte, como o GitHub, o repositório GitHub de amostra será clonado na conta do GitHub.


##Criando uma cadeia de ferramentas com base em um aplicativo
{: #creating_a_toolchain_from_an_app}

É possível criar uma cadeia de ferramentas a partir de seu aplicativo. A cadeia de
ferramentas pode suportar desenvolvimento, implementação e monitoramento contínuos e mais, e é associada ao seu app. Cada app pode ser
associado a uma cadeia de ferramentas. Quando você envia por push as mudanças para o GitHub ou o repositório {{site.data.keyword.ghe_short}} da cadeia de ferramentas, o pipeline constrói e implementa automaticamente o app.

Se você criou seu app usando seu próprio repositório de código, clique em **Conectar à cadeia de ferramentas do DevOps** na página de detalhes de seu app. Em seguida, siga as etapas descritas em [Criando apps por meio de seu próprio repositório de código](/docs/apps/tutorials/tutorial_byoc.html).
{: note}

1. Se você criou seu app usando um kit do iniciador, clique em **Implementar na nuvem** na página de detalhes do seu app. Se você usar o {{site.data.keyword.Bluemix_notm}} Public, seu app será configurado para entrega contínua por meio de um novo repositório GitHub que é preenchido com o código de início do app. Se você usar o {{site.data.keyword.Bluemix_notm}} Dedicated, seu app será configurado para entrega contínua por meio de um novo GitHub ou repositório {{site.data.keyword.ghe_short}} que é preenchido com o código de início do app.
1. Na página de criação da cadeia de ferramentas, revise o diagrama da cadeia de ferramentas que estiver prestes a criar. O diagrama
mostrará cada integração de ferramenta em sua fase de ciclo de vida na cadeia de ferramentas.
1. Revise as informações padrão para as configurações da cadeia de ferramentas. O nome da cadeia de ferramentas as identifica em
{{site.data.keyword.Bluemix_notm}}. Se você desejar usar um nome diferente, mude o nome da cadeia de ferramentas.
1. Na seção Integrações de ferramentas, selecione cada integração de ferramenta que deseja configurar para sua cadeia de ferramentas. Algumas integrações de ferramentas não requerem configuração. Para obter informações sobre como configurar as integrações de ferramentas, consulte
[Configurando
integrações de ferramentas](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}.
1. Clique em **Criar**. Várias etapas são executadas automaticamente para configurar sua cadeia de ferramentas. As integrações de ferramentas configuradas são diferentes, dependendo de se você está usando cadeias de ferramentas no {{site.data.keyword.Bluemix_notm}} Public ou no {{site.data.keyword.Bluemix_notm}} Dedicated. Por exemplo, quando você cria uma cadeia de ferramentas de um app no {{site.data.keyword.Bluemix_notm}} Public, estas etapas são executadas:

 * A cadeia de ferramentas é criada.
 * Se você tiver configurado o Delivery Pipeline, os pipelines serão criados e acionados.
 * Se você tiver configurado o GitHub, o repositório GitHub de amostra será clonado na conta do GitHub.


##Visualizando uma cadeia de ferramentas
{: #viewing_a_toolchain}

Após configurar a cadeia de ferramentas e as suas integrações de ferramenta, é possível visualizar uma representação visual da cadeia de ferramentas.

É possível visualizar uma cadeia de ferramentas por meio de um app clicando em **Visualizar cadeia de ferramentas** na página de detalhes de seu app.
{: tip}

1. No painel DevOps, na página **Cadeias de ferramentas**, selecione um **RESOURCE GROUP** ou **CLOUD FOUNDRY ORG**. Todas as cadeias de ferramentas que estiverem contidas dentro do grupo de recursos selecionado ou na organização do Cloud Foundry serão exibidas. Clique na cadeia de ferramentas que você deseja visualizar para abrir a sua página Visão geral. Como alternativa, na página Visão geral do app, no cartão do Continuous Delivery, clique em **Visualizar cadeia de ferramentas**. Em seguida, clique em **Visão geral**.
2. Para acessar uma integração de ferramenta que esteja em sua cadeia de ferramentas, clique na ferramenta.

 Se você tiver mais de um GitHub, {{site.data.keyword.ghe_short}} ou repositório do Git, poderá ter múltiplas placas para a mesma integração de ferramenta porque cada repositório é representado por sua própria placa. Se você tiver mais de um pipeline, poderá ter múltiplos cartões para a mesma integração de ferramenta porque cada pipeline será representado por seu próprio cartão. Por exemplo, quando você cria uma cadeia de ferramentas de Microsserviços, cada um dos três microsserviços tem seu próprio GitHub, {{site.data.keyword.ghe_short}} ou repositório Git e seu próprio pipeline.
 {: tip}

## Consulte o tutorial: Usando cadeias de ferramentas
{: #toolchain_tutorials}

Consulte um desses tutoriais no [IBM&reg; Cloud Garage Method ![Ícon de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage){:new_window}:

  * [Criar e usar sua primeira cadeia de ferramentas usando a cadeia de ferramentas "Desenvolver um app Cloud Foundry" ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}.

  * [Incluir uma cadeia de ferramentas em um app ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:new_window}.

  * [Usar a cadeia de ferramentas "Desenvolver e testar microsserviços no Cloud Foundry"![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:new_window}.
