---

copyright:
  years: 2015, 2018
lastupdated: "2018-1-15"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Continuous Delivery 시작하기
{: #cd_getting_started}

애플리케이션의 빌드와 배치를 자동화하는 오픈 도구 체인이 포함된 {{site.data.keyword.contdelivery_full}}를 사용하여 DevOps 접근 방법을 채택합니다. 개발, 배치, 운영 태스크를 지원하는 단순 배치 도구 체인을 작성하여 시작할 수 있습니다.
{: shortdesc}

{{site.data.keyword.Bluemix_notm}} 카탈로그에서 선택하여 {{site.data.keyword.contdelivery_short}}의 인스턴스를 작성하고 나면 템플리트에서 Continuous Delivery 도구 체인을 작성하거나 기존 도구 체인과 작업할 수 있습니다.
 ![Continuous Delivery 시작 페이지](images/cd_landing_page2.png)

* 템플리트에서 Continuous Delivery 도구 체인을 작성 및 구성하려면 **[여기에서 시작하십시오](#starting_from_a_toolchain_template)**. 도구 체인은 파이프라인의 계획, 개발, 배치와 애플리케이션의 관리에 사용할 도구를 통합합니다. 언제나 도구 체인에서 도구를 추가하거나 제거할 수 있습니다.
* 도구 체인이 이미 있는 경우 "도구 체인 템플리트에서 시작" 섹션에서 **도구 체인 보기**를 클릭하십시오. 도구 체인 관련 작업에 대한 자세한 정보는 [도구 체인 사용](/docs/services/ContinuousDelivery/toolchains_using.html){: new_window}을 참조하십시오.

##{{site.data.keyword.contdelivery_short}} 개요
{: #cd_overview}

{{site.data.keyword.contdelivery_short}}를 통해 DevOps 사례와 업계 최고의 도구를 사용하여 애플리케이션을 빌드하고 테스트하며 전달할 수 있습니다.
{:shortdesc}

{{site.data.keyword.contdelivery_short}} 서비스에서는 다음과 같이 DevOps 워크플로우를 지원합니다.

 * 개발, 배치 및 운영 태스크를 지원하는 도구 통합을 사용할 수 있도록 통합된 DevOps 오픈 [도구 체인](/docs/services/ContinuousDelivery/toolchains_about.html){: new_window}을 작성할 수 있습니다.

  도구 체인은 애플리케이션 개발, 빌드, 배치, 테스트 및 관리에 함께 사용할 수 있는 통합 도구 세트이며 오퍼레이션을 반복 가능하고 관리하기 더 쉽게 만듭니다. 도구 체인에는 오프 소스 도구, {{site.data.keyword.Bluemix_notm}} 서비스(예: [{{site.data.keyword.DRA_full}}](/docs/services/ContinuousDelivery/di_working.html){: new_window}) 및 써드파티 도구(예:GitHub, PagerDuty, Slack)가 포함될 수 있습니다. 
  
  **참고**: {{site.data.keyword.DRA_short}}는 미국 남부 지역에서만 사용 가능합니다. 

 * 자동화된 [파이프라인](/docs/services/ContinuousDelivery/pipeline_about.html){: new_window}을 사용하여 지속적 딜리버리를 제공합니다.

  빌드, 단위 테스트, 배치 등을 자동화하십시오. 사용자 개입을 최소화하여 반복할 수 있는 방식으로 빌드, 테스트, 배치를 수행하십시오. 언제든 프로덕션으로 릴리스할 수 있게 준비하십시오.

 * [웹 기반 IDE](/docs/services/ContinuousDelivery/web_ide.html){: new_window}를 사용하여 어디서든 코드를 편집하고 푸시합니다.

  GitHub에서 소스 제어 태스크의 작성, 편집, 실행, 디버그, 완료를 수행하십시오. 코드 편집에서 프로덕션으로 배치하는 작업으로 원활하게 이동하십시오. 
  
 * IBM에서 호스팅하고 GitLab Community Edition에서 빌드된 [Git 저장소(repos) 및 문제 트래커](/docs/services/ContinuousDelivery/git_working.html#git_working){: new_window}로 사용자의 팀과 협업하고 소스 코드를 관리합니다.

  코드의 보안을 유지하는 미세 조정된 액세스 제어를 통해 Git 저장소를 관리합니다. 코드를 검토하고 병합 요청을 통해 협업을 개선합니다. 문제 트래커를 통해 문제를 추적하고 아이디어를 공유합니다. 위키 시스템에서 프로젝트를 문서화합니다.


##도구 체인 템플리트에서 시작
{: #starting_from_a_toolchain_template}

[템플리트 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/devops/create){: new_window}에서 Continuous Delivery 도구 체인을 작성하고 구성하려면 다음을 수행하십시오.

1. **도구 체인 작성** 페이지에서 도구 체인 템플리트를 클릭하십시오.
1. 작성하려는 도구 체인의 다이어그램을 검토하십시오. 다이어그램은 도구 체인에서 해당 라이프사이클 단계(Phase)에 있는 각 도구 통합을 보여줍니다.

 **팁**: 일부 도구 체인 템플리트에는 도구 통합의 여러 인스턴스가 있습니다. 예를 들어, {{site.data.keyword.Bluemix_notm}} 퍼블릭의 마이크로서비스 도구 체인 템플리트에는 3개 마이크로서비스 각각에 대해 하나씩 GitHub의 3개 인스턴스와 Delivery Pipeline의 3개 인스턴스가 포함되어 있습니다.

 다음 이미지의 다이어그램을 예로 들 수 있습니다. 도구 체인을 작성할 때 다이어그램은 도구 체인의 일부인 각 도구 통합을 표시합니다.
![Toolchain_diagram](images/toolchain_diagram2.png)
1. 도구 체인 설정에 대한 기본 정보를 검토하십시오.

 * 도구 체인의 이름은 {{site.data.keyword.Bluemix_notm}}에서 해당 도구 체인을 식별합니다. 다른 이름을 사용하려면 도구 체인의 이름을 변경하십시오.
 * 도구 체인을 작성할 지역입니다. 다른 지역을 사용하려는 경우 사용 가능한 지역의 목록에서 선택하십시오.
 * 도구 체인을 작성할 조직입니다. 다른 조직을 사용하려는 경우 사용 가능한 조직의 목록에서 선택하십시오.
 
1. 도구 통합 섹션에서 도구 체인에 대해 구성할 각 도구 통합을 선택하십시오. 몇몇 도구 통합에서는 구성이 필요 없습니다. 도구 통합 구성에 대한 정보는 [도구 통합 구성](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}의 내용을 참조하십시오.
1. **작성**을 클릭하십시오. 여러 단계가 자동으로 실행되어 도구 체인을 설정합니다. 설정된 도구 통합은 선택된 도구 체인 템플리트 및 사용자가 {{site.data.keyword.Bluemix_notm}} 퍼블릭 또는 {{site.data.keyword.Bluemix_notm}} 데디케이티드를 사용 중인지 여부에 따라 다릅니다. 예를 들어, {{site.data.keyword.Bluemix_notm}} 퍼블릭에서 마이크로서비스 도구 체인을 작성하면 다음 단계가 실행됩니다.

 * 도구 체인이 작성됩니다.
 * Delivery Pipeline을 구성한 경우에는 파이프라인이 작성되고 실행됩니다.
 * Sauce Labs를 구성한 경우에는 Sauce Labs 테스트 작업을 파이프라인에 추가하도록 도구 체인이 설정됩니다.
 * PagerDuty를 구성한 경우에는 경보 알림을 지정된 PagerDuty 서비스에 전송하도록 도구 체인이 설정됩니다.
 * Slack을 구성한 경우에는 배치 상태에 대한 알림을 지정된 Slack 채널에 전송하도록 도구 체인이 설정됩니다.
 * GitHub 등의 소스 코드 도구 통합을 구성한 경우에는 샘플 GitHub 저장소가 GitHub 계정으로 복제됩니다.
