---

Copyright:
 years: 2015, 2019
lastupdated: "2019-06-18"

keywords: IBM Cloud DevOps, enterprise application Developer, IBM Cloud Garage Method

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


# {{site.data.keyword.Bluemix_notm}} DevOps
{: #devops_intro}

빠르게 반복하고 실험할 수 있도록 시장 수요가 팀에 요구하는 속도로 소프트웨어와 서비스를 제공합니다. 피드백과 데이터에 따라 새 버전을 자주 배치해야 합니다. 가장 성공적인 클라우드 개발 팀에서는 현대적 DevOps 문화 및 사례를 사용하고, 클라우드 네이티브 아키텍처를 수용하며, 생산성을 높이기 위해 최고 수준의 도구에서 도구를 어셈블링합니다. 이러한 작업을 빠르게 수행하는 것이 경쟁 우위를 차지하는 핵심입니다.

[IBM Cloud Garage Method](https://www.ibm.com/cloud/garage){:external}는 아키텍처, 사례 및 DevOps 도구 체인을 설명하여 기업이 규모에 맞게 혁신할 수 있습니다. {{site.data.keyword.Bluemix_notm}} Garage Method를 사용하여 사용자 문화를 변화시키고 도구를 효과적이고 빠르게 사용할 수 있습니다.

엔터프라이즈 애플리케이션 개발자는 몇 분 안에 클라우드 네이티브 애플리케이션의 빌드 및 배치를 시작할 수 있습니다. 전체 서비스 세트를 사용하여 코그너티브, IoT, 블록체인, 모바일 및 데이터 집약적 애플리케이션을 빌드할 수 있습니다. IBM Cloud 앱 서비스를 사용하면 개별 개발자가 프로젝트를 작성하고, 애플리케이션 스타터 킷을 선택하고, 프로덕션 준비가 되어 있는 애플리케이션을 {{site.data.keyword.Bluemix_notm}}에 배치할 수 있습니다. 플랫폼의 코드 생성 기술은 스타터 애플리케이션을 개발자가 선호하는 언어 및 프레임워크에 작성하며 해당 요구 및 유스 케이스에 알맞게 조정합니다. Watson Conversation과 같은 유스 케이스를 지원하는 데 필요한 모든 서비스는 자동으로 프로비저닝됩니다. 개발자는 로컬 워크스테이션 또는 클라우드에서 디버그하고 테스트할 수 있으며 DevOps 도구 체인을 사용하여 다른 사용자와 협업하고 딜리버리 프로세스를 자동화할 수 있습니다.

팀 구성원이 프로젝트에 합류하는 경우 구성원은 개발, 배치 및 프로덕션 오퍼레이션을 포함하는 통합 도구 세트가 필요합니다. IBM의 오픈 도구 체인 아키텍처를 통해 팀은 최고의 DevOps 도구를 IBM, 오픈 소스 등에서 빠르게 프로비저닝할 수 있습니다. 이러한 도구 간의 통합은 자동으로 구성됩니다. 도구 체인이 플랫폼에서의 최고 개념이므로 개발자는 필요한 모든 것을 한 위치에서 빠르게 구성할 수 있으며 시간이 지남에 따라 도구 체인을 발달시킬 수 있습니다. IBM에서는 Garage Method 우수 사례를 지원하는 도구 체인 템플리트를 제공하며 이를 통해 입증된 도구 체인 패턴을 기업 전체에 촉진하도록 사용자 정의할 수 있습니다.

{{site.data.keyword.contdelivery_full}}는 DevOps 도구 체인: {{site.data.keyword.gitrepos}}, Delivery Pipeline 및 Eclipse Orion {{site.data.keyword.webide}}의 핵심 도구 세트를 제공합니다. {{site.data.keyword.gitrepos}}는 GitLab Community Edition을 기반으로 하며 병합 요청을 통해 소스 코드 협업 및 플랜 보드를 제공합니다. Delivery Pipeline은 개발자에서 프로덕션으로 진행상태가 변경되면 여러 환경에서 빌드, 테스트 및 배치 작업을 구성합니다. 몇 분 안에 애플리케이션을 Cloud Foundry 환경 또는 {{site.data.keyword.Bluemix_notm}}의 Kubernetes 클러스터에 퍼블릭 또는 프라이빗 클라우드로 배치할 수 있습니다. Eclipse Orion {{site.data.keyword.webide}}는 개발자에게 어느 브라우저에서나 코드에 빠르게 액세스할 수 있는 권한을 제공합니다.

오픈 도구 체인은 Slack, Atlassian JIRA, Sonatype Nexus, JFrog Artifactory, Sauce Labs, PagerDuty, IBM Cloud Availability Monitoring, IBM Cloud Alert Notification, IBM Vulnerability Advisor 및 IBM Globalization Pipeline과 같은 {{site.data.keyword.contdelivery_short}} 주위의 추가 도구를 통합합니다. 또한 GitHub, GitHub 엔터프라이즈 및 Jenkins를 포함하여 {{site.data.keyword.contdelivery_short}} 기능에 대한 다른 도구를 대체할 수도 있습니다. 개발자는 개발자가 좋아하는 IDE 및 편집기를 사용할 수도 있습니다(예: Visual Studio Code, Eclipse 등).

코드 저장소, 문제 추적 시스템, 빌드 시스템 및 배치 시스템은 앱을 보다 효율적이고 효과적으로 제공하도록 지원하는 데 사용할 수 있는 풍부한 데이터를 나타냅니다. {{site.data.keyword.DRA_full}}는 빅데이터 분석을 사용하여 경영진, 관리자 및 개발자에게 유용한 통찰을 제공합니다. {{site.data.keyword.DRA_short}}는 DevOps 도구 체인의 데이터를 집계하고 분석하여 특정 변경사항을 배치하는 데 따른 위험성 및 코드 베이스와 팀 생산성을 향상시키기 위한 영역에 대해 알려줍니다. Delivery Pipeline은 변경의 위험성을 기반으로 배치를 환경에 자동으로 게이트 처리할 수 있습니다.

리소스 그룹은 미국 남부, 미국 동부, 영국, 독일 및 도쿄 지역에서 사용할 수 있습니다. Cloud Foundry 조직은 미국 남부, 영국 및 독일 지역에서 지원됩니다.
{: note}

{{site.data.keyword.Bluemix_notm}} DevOps는 클라우드 개발에 대한 구체적인 사례와 아키텍처를 제공합니다. 이를 통해 개발자가 {{site.data.keyword.Bluemix_notm}}에서 다양한 서비스 카탈로그를 사용하는 새 프로젝트를 빠르게 시작할 수 있습니다. 또한 {{site.data.keyword.Bluemix_notm}} DevOps는 빠른 속도와 제어을 바탕으로 전달을 자동화하기 위한 통합된 오픈 도구 세트도 개발자에게 제공합니다.
