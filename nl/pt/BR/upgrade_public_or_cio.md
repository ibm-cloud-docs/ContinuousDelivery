---

copyright:
  years: 2015, 2018
lastupdated: "2018-3-20"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Fazendo upgrade de projetos IBM Confidencial para cadeias de ferramentas 
{: #upgrade_public_or_cio}

O {{site.data.keyword.jazzhub}} está sendo desenvolvido para o {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.contdelivery_short}}. Como parte dessa mudança, será feito upgrade dos projetos para cadeias de ferramentas.

Quando o projeto está pronto para ser submetido a upgrade, uma mensagem é exibida em sua página Visão geral. É possível então atualizar o projeto para uma cadeia de ferramentas no {{site.data.keyword.Bluemix_notm}} Public. A cadeia de ferramentas incluirá um repositório (repo) do Whitewater {{site.data.keyword.ghe_short}} para seu código-fonte. O Whitewater {{site.data.keyword.ghe_short}} é fornecido às equipes IBM para promover e ativar a codificação social dentro da IBM. 
{: shortdesc}

As cadeias de ferramentas do **{{site.data.keyword.contdelivery_short}} são aprovadas para material IBM Confidential quando elas são usadas com o Whitewater {{site.data.keyword.ghe_short}}.** Os Delivery Pipelines que recebem entrada de repositórios do Whitewater {{site.data.keyword.ghe_short}} podem implementar nos ambientes de preparação (YS1) e públicos (YP).

Durante o upgrade, será solicitado que você autorize o {{site.data.keyword.contdelivery_short}} a acessar o Whitewater {{site.data.keyword.ghe_short}} em seu nome.

## Incluindo membros em seu repositório do Whitewater {{site.data.keyword.ghe_short}} após o upgrade

Se seu projeto usar um repositório hospedado no JazzHub, durante o upgrade, um novo repositório será criado no Whitewater {{site.data.keyword.ghe_short}}. Após o upgrade, a pessoa que iniciou o upgrade deve incluir membros da equipe no repositório do Whitewater {{site.data.keyword.ghe_short}} e assegurar que eles tenham os privilégios corretos para que possam acessar o novo repositório.

## Solucionando problemas

Um problema intermitente às vezes ocorre quando você tenta mudar o destino de um estágio de implementação do pipeline. Quando esse problema ocorre, um erro é mostrado nos campos **Organização** e **Espaço**.

Esse problema geralmente ocorre somente ao mudar o destino do pipeline para que o pipeline criado durante o upgrade seja implementado corretamente nos mesmos destinos como fez antes.

Se você tentar mudar o destino e esse problema ocorrer, alterne entre os destinos algumas vezes até que
os campos **Organização** e **Espaço** sejam concluídos.

Um problema relacionado às vezes causa falha nas implementações nos destinos YS1. Essa situação é rara; se acontecer, execute novamente o pipeline.

A equipe do IBM DevOps Services está trabalhando ativamente para resolver esses problemas.
