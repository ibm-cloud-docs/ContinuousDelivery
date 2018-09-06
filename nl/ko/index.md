---

copyright:
  years: 2015, 2018
lastupdated: "2018-8-15"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# 시작하기 튜토리얼
{: #cd_getting_started}

애플리케이션의 빌드와 배치를 자동화하는 오픈 도구 체인이 포함된 {{site.data.keyword.contdelivery_full}}를 사용하여 DevOps 접근 방법을 채택합니다. 개발, 배치, 운영 태스크를 지원하는 단순 배치 도구 체인을 작성하여 시작할 수 있습니다. 
{: shortdesc}

##전제조건
{: #cd_prereqs}

템플리트에서 Continuous Delivery 도구 체인을 작성하려면 {{site.data.keyword.Bluemix_notm}} 카탈로그에서 선택하여 {{site.data.keyword.contdelivery_short}}의 인스턴스를 작성해야 합니다. 도구 체인은 파이프라인의 계획, 개발, 배치와 애플리케이션의 관리에 사용할 도구를 통합합니다. 언제나 도구 체인에서 도구를 추가하거나 제거할 수 있습니다. 도구 체인이 이미 있는 경우 [기존 도구 체인 보기](/docs/services/ContinuousDelivery/toolchains_working.html#viewing_a_toolchain){: new_window}를 수행할 수 있습니다. 도구 체인 관련 작업에 대한 자세한 정보는 [도구 체인 사용](/docs/services/ContinuousDelivery/toolchains_using.html){: new_window}을 참조하십시오.

{{site.data.keyword.contdelivery_short}}의 인스턴스가 이미 있는 경우 [도구 체인 작성 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/devops/create){: new_window} 또는 [기존 도구 체인 보기](/docs/services/ContinuousDelivery/toolchains_working.html#viewing_a_toolchain){: new_window}를 수행할 수 있습니다.
{: tip}

##1단계: 도구 체인 템플리트 선택
{: #select_a_toolchain_template}

1. **도구 체인 작성** 페이지에서 [도구 체인 템플리트 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/devops/create){: new_window}를 클릭하십시오.
1. 작성하려는 도구 체인의 다이어그램을 검토하십시오. 다이어그램은 도구 체인에서 해당 라이프사이클 단계(Phase)에 있는 각 도구 통합을 보여줍니다.

 일부 도구 체인 템플리트에는 도구 통합의 여러 인스턴스가 있습니다. 예를 들어, {{site.data.keyword.Bluemix_notm}} 퍼블릭의 마이크로서비스 도구 체인 템플리트에는 3개 마이크로서비스 각각에 대해 하나씩 GitHub의 3개 인스턴스와 Delivery Pipeline의 3개 인스턴스가 포함되어 있습니다.
 {: tip}

 다음 이미지의 다이어그램을 예로 들 수 있습니다. 도구 체인을 작성할 때 다이어그램은 도구 체인의 일부인 각 도구 통합을 표시합니다.
![Toolchain_diagram](images/toolchain_diagram2.png)
 
##2단계: 도구 체인 작성 
{: #create_a_toolchain}
 
1. 도구 체인 설정에 대한 기본 정보를 검토하십시오.

 * 도구 체인의 이름은 {{site.data.keyword.Bluemix_notm}}에서 해당 도구 체인을 식별합니다. 다른 이름을 사용하려면 도구 체인의 이름을 변경하십시오.
 * 도구 체인을 작성할 지역입니다. 다른 지역을 사용하려는 경우 사용 가능한 지역의 목록에서 선택하십시오.
 * 도구 체인을 작성할 리소스 그룹 또는 조직입니다. 리소스 그룹 선택과 조직 선택 간에 전환하려면 링크를 클릭하십시오. 다른 리소스 그룹이나 조직을 사용하려는 경우 사용 가능한 리소스 그룹 또는 조직의 목록에서 선택하십시오.
 
   리소스 그룹은 미국 남부 지역에서만 사용 가능합니다.
   {: tip}
 
1. 도구 통합 섹션에서 도구 체인에 대해 구성할 각 도구 통합을 선택하십시오. 몇몇 도구 통합에서는 구성이 필요 없습니다. 도구 통합 구성에 대한 정보는 [도구 통합 구성](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}의 내용을 참조하십시오.
1. **작성**을 클릭하십시오. 여러 단계가 자동으로 실행되어 도구 체인을 설정합니다. 설정된 도구 통합은 선택된 도구 체인 템플리트 및 사용자가 {{site.data.keyword.Bluemix_notm}} 퍼블릭 또는 {{site.data.keyword.Bluemix_notm}} 데디케이티드를 사용 중인지 여부에 따라 다릅니다. 예를 들어, {{site.data.keyword.Bluemix_notm}} 퍼블릭에서 마이크로서비스 도구 체인을 작성하면 다음 단계가 실행됩니다.

 * 도구 체인이 작성됩니다.
 * Delivery Pipeline을 구성한 경우에는 파이프라인이 작성되고 실행됩니다.
 * Sauce Labs를 구성한 경우에는 Sauce Labs 테스트 작업을 파이프라인에 추가하도록 도구 체인이 설정됩니다.
 * PagerDuty를 구성한 경우에는 경보 알림을 지정된 PagerDuty 서비스에 전송하도록 도구 체인이 설정됩니다.
 * Slack을 구성한 경우에는 배치 상태에 대한 알림을 지정된 Slack 채널에 전송하도록 도구 체인이 설정됩니다.
 * GitHub 등의 소스 코드 도구 통합을 구성한 경우에는 샘플 GitHub 저장소가 GitHub 계정으로 복제됩니다.

##다음 단계
{: #next_steps}

[IBM&reg; Cloud Garage Method![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/garage){:new_window}에 있는 다음 튜토리얼 중 하나를 확인하십시오.

  * [Create and use your first toolchain by using the "Develop a Cloud Foundry app" toolchain ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:new_window}.

  * [Add a toolchain to an app![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:new_window}.
