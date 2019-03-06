---

copyright:
  years: 2015, 2019
lastupdated: "2019-2-1"

---


{:screen: .screen}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:shortdesc: .shortdesc}

# 파이프라인에 대한 작업 
{: #pipeline-working}

빌드와 {{site.data.keyword.Bluemix}}에 대한 배치를 자동화하려면 {{site.data.keyword.contdelivery_full}} 파이프라인을 사용하십시오.
{: shortdesc}

파이프라인을 사용하면 여러 빌드 유형 중에서 선택할 수 있습니다. 사용자가 빌드 스크립트를 제공하면 {{site.data.keyword.contdelivery_short}}에서 이 스크립트를 실행합니다. 사용자가 빌드 시스템을 설정할 필요는 없습니다. 그러면 한 번의 클릭으로 하나 또는 다수의 {{site.data.keyword.Bluemix_notm}} 영역, 공용 Cloud Foundry 서비스 또는 {{site.data.keyword.containerlong}}의 Docker 컨테이너에 앱을 자동적으로 배치할 수 있습니다.

빌드 작업은 Git 저장소에서 앱 소스 코드를 컴파일하고 패키지합니다. 빌드 작업을 통해 WAR 파일 또는 {{site.data.keyword.containerlong_notm}}의 Docker 컨테이너와 같은 배치 가능한 아티팩트가 생성됩니다. 또한, 빌드 내에서 단위 테스트를 자동으로 실행할 수 있습니다. 커미트가 푸시될 때마다 빌드가 트리거되도록 빌드 작업을 설정할 수 있습니다.

배치 작업은 빌드 작업의 결과물을 가져와 {{site.data.keyword.Bluemix_notm}}와 같은 Cloud Foundry 서버 또는 {{site.data.keyword.containerlong_notm}}에 배치합니다.

하나 또는 다수의 지역과 서비스에 배치할 수 있습니다. 예를 들면, {{site.data.keyword.deliverypipeline}}이 하나 이상의 서비스를 사용하고 한 지역에서 테스트되며 여러 지역의 프로덕션에 배치되도록 설정할 수 있습니다.

##파이프라인 작성

다음 방법 중 하나를 사용하여 파이프라인을 작성할 수 있습니다.

   * [기존 Cloud Foundry 애플리케이션에서 도구 체인 작성](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_an_app){: new_window}. 결과 도구 체인에는 파이프라인이 포함됩니다.

   * 하나 이상의 파이프라인이 포함된 [도구 체인을 템플리트에서 작성](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_a_template){: new_window}.

   * 기존 도구 체인에 [{{site.data.keyword.deliverypipeline}} 도구 통합 추가](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#deliverypipeline){: new_window}. 
   
{{site.data.keyword.deliverypipeline}}에서 구성을 변경하십시오. 빌드 상태, 배치된 앱 및 최근 배치를 확인하십시오. 최신 로그와 배치 세부사항을 확인하거나 파이프라인을 삭제하십시오.
