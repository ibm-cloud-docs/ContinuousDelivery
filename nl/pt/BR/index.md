---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-18"

keywords: IBM Cloud Continuous Delivery, tool integration, toolchain template

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


# Tutorial de Introdução
{: #getting-started}

Adote uma abordagem DevOps usando o {{site.data.keyword.contdelivery_full}}, que inclui cadeias de ferramentas abertas que automatizam a construção e a implementação de aplicativos. É possível começar criando uma cadeia de ferramentas de implementação simples que suporte as tarefas de desenvolvimento, implementação e operações. 
{: shortdesc}


Se você já tiver uma instância do {{site.data.keyword.contdelivery_short}}, será possível [criar uma cadeia de ferramentas](https://cloud.ibm.com/devops/create){:external} ou [visualizar cadeias de ferramentas existentes](https://cloud.ibm.com/devops/toolchains){:external}.
{: tip}


##Pré-requisitos
{: #cd_prereqs}

Antes de poder criar uma cadeia de ferramentas de entrega contínua por meio de um modelo, deve-se criar uma instância do {{site.data.keyword.contdelivery_short}} selecionando-a no catálogo do {{site.data.keyword.Bluemix_notm}}. A
cadeia de ferramentas integra ferramentas para planejar, desenvolver, implementar
pipelines e gerenciar aplicativos. Sempre é possível incluir ou remover ferramentas de
suas cadeias de ferramentas. Se você já tiver cadeias de ferramentas, será possível [visualizar as cadeias de ferramentas existentes](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#viewing_a_toolchain). Para obter mais informações sobre como trabalhar com cadeias de ferramentas, veja [Usando cadeias de ferramentas](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using).


##Etapa 1: Selecione um modelo de cadeia de ferramentas
{: #select_a_toolchain_template}

Para localizar rapidamente o modelo de cadeia de ferramentas que trata de seus requisitos específicos, selecione as caixas de seleção apropriadas para filtrar por ferramentas e destino de implementação.
{: tip}

1. Na página **Criar uma cadeia de ferramentas**, clique em um [modelo de cadeia de ferramentas](https://cloud.ibm.com/devops/create){:external}.
1. Revise o diagrama da cadeia de ferramentas que você está prestes a criar. O diagrama
mostrará cada integração de ferramenta em sua fase de ciclo de vida na cadeia de ferramentas.

 Alguns dos modelos de cadeia de ferramentas têm múltiplas instâncias de uma integração de ferramenta. Por exemplo, o modelo de cadeia de ferramentas de Microsserviços no {{site.data.keyword.Bluemix_notm}} Public contém três instâncias do GitHub e três instâncias do Delivery Pipeline, uma para cada um dos três microsserviços.
 {: tip}

 O diagrama na imagem a seguir é um exemplo. Ao criar uma cadeia de ferramentas, o diagrama mostra cada integração de ferramenta que faz parte da cadeia de ferramentas.
 ![Toolchain_diagram](images/toolchain_diagram2.png)
 
##Etapa 2: Criar uma Cadeia de Ferramentas 
{: #create_a_toolchain}
 
1. Revise as informações padrão para as configurações da cadeia de ferramentas:

 * O nome da cadeia de ferramentas as identifica em
{{site.data.keyword.Bluemix_notm}}. Se você desejar usar um nome diferente, mude
o nome da cadeia de ferramentas.
 * A região na qual criar a cadeia de ferramentas. Se você desejar usar uma região diferente, selecione-a na lista de regiões disponíveis.
 * A organização ou o grupo de recursos no qual criar a cadeia de ferramentas. Clique no link para alternar entre a seleção de grupos de recursos e de organizações. Se você desejar usar uma organização ou um grupo de recursos diferente, selecione essa opção diferente na lista de organizações ou de grupos de recursos disponíveis.
 
   Os grupos de recursos estão disponíveis nas regiões Sul dos EUA, Leste dos EUA, Reino Unido, Alemanha e Tóquio. As organizações do Cloud Foundry são suportadas nas regiões Sul dos EUA, Reino Unido e Alemanha.
   {: important}
 
1. Na seção Integrações de ferramentas, selecione cada integração de ferramenta que deseja configurar para sua cadeia de ferramentas. Algumas integrações de ferramentas não requerem configuração. Para obter informações sobre como configurar as integrações de ferramentas, consulte
[Configurando
integrações de ferramentas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations).
1. Clique em **Criar**. Várias etapas são executadas automaticamente para configurar sua cadeia de ferramentas. As integrações de ferramentas configuradas são diferentes, dependendo de qual modelo de cadeia de ferramentas você selecionou e se está usando o {{site.data.keyword.Bluemix_notm}} Public ou o {{site.data.keyword.Bluemix_notm}} Dedicated. Por exemplo, quando você cria uma cadeia de ferramentas de Microsserviços no {{site.data.keyword.Bluemix_notm}} Public, estas etapas são executadas:

 * A cadeia de ferramentas é criada.
 * Se você tiver configurado o Delivery Pipeline, os pipelines serão criados e executados.
 * Se você tiver configurado o Sauce Labs, a cadeia de ferramentas será configurada para incluir tarefas de teste do Sauce Labs nos pipelines.
 * Se tiver configurado o PagerDuty, a cadeia de ferramentas será configurada para enviar notificações de alerta para o serviço PagerDuty especificado.
 * Se tiver configurado o Slack, a cadeia de ferramentas será configurada para enviar notificações sobre o status de implementação para o canal Slack especificado.
 * Se tiver configurado a integração de ferramenta do código-fonte, como o GitHub, o repositório GitHub de amostra será clonado na conta do GitHub.

##Próximas Etapas
{: #next_steps}

Confira um destes tutoriais sobre o [IBM&reg; Cloud Garage Method](https://www.ibm.com/cloud/garage){:external}:

  * [Crie e use sua primeira cadeia de ferramentas usando a cadeia de ferramentas "Desenvolver um app Cloud Foundry"](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:external}.

  * [Inclua uma cadeia de ferramentas em um app](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:external}.
