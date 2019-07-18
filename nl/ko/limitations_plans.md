---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-27"

keywords: users of a service instance, a-service, Git Repos

subcollection: ContinuousDelivery

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}


# 플랜 제한사항 및 이용
{: #limitations_usage}

{{site.data.keyword.contdelivery_full}}를 사용하는 것은 {{site.data.keyword.Bluemix_notm}} 플랫폼 또는 기타 호환 가능 PaaS(Platform as a Service) 또는 IaaS(Infrastructure as a Service)에서 애플리케이션의 빌드, 배치, 테스트 및 진행 조작으로 한정됩니다.

## 서비스 인스턴스의 범위
{: #service_scope}

DevOps 도구 체인을 작성하고 사용하려면 {{site.data.keyword.contdelivery_short}} [서비스 인스턴스](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}가 있어야 합니다. 서비스 인스턴스는 {{site.data.keyword.Bluemix_notm}} Identity and Access Management(IAM) [리소스 그룹](/docs/services/resources?topic=resources-rgs) 또는 {{site.data.keyword.Bluemix_notm}} 조직(org)에 속할 수 있습니다.

리소스 그룹에서 {{site.data.keyword.contdelivery_short}} 서비스의 *새* 인스턴스만 작성할 수 있습니다. 조직에서 리소스 그룹으로의 도구 체인 마이그레이션은 현재 지원되지 않습니다. 도구 체인이 포함된 조직의 {{site.data.keyword.contdelivery_short}} 서비스가 누락된 경우 리소스 그룹에서 도구 체인을 다시 작성하거나 [IBM 지원 센터](https://cloud.ibm.com/unifiedsupport){:external}에 문의하여 도움을 받을 수 있습니다.

계정당 하나의 Lite 서비스만 가질 수 있습니다. 여러 조직 또는 리소스 그룹에서 또는 여러 지역 내에서 도구 체인에 대한 작업을 수행하려는 경우 프로페셔널 플랜을 사용하는 것이 좋습니다.
{: tip}


## 권한이 부여된 사용자
{: #authorized_users}

{{site.data.keyword.contdelivery_short}} [서비스 플랜](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}은 서비스 인스턴스의 권한 부여된 사용자의 수에 따라 정의되고 가격이 책정됩니다. 다음을 포함하여 노력에 기여한 사용자는 권한이 있는 사용자로 계산되어야 합니다.

 * {{site.data.keyword.gitrepos}} 저장소의 문제, 문제 보드, 소스 코드 또는 다른 아티팩트와 상호작용하는 사용자
 * (저장소에 커미트하여 간접적으로 또는 사용자 인터페이스에서 직접) Delivery Pipeline의 상태를 조작하고 트리거하고 보는 사용자
 * Eclipse Orion {{site.data.keyword.webide}}와 상호작용하는 사용자
 
Lite 플랜은 제한을 받습니다. Lite 플랜 및 프로페셔널 플랜에 대한 자세한 정보는 [서비스 카탈로그](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}를 참조하십시오.
{: tip}
 
### 리소스 그룹의 {{site.data.keyword.contdelivery_short}} 인스턴스에 대한 사용자를 어떻게 계산합니까?

권한 부여된 사용자는 비용 청구 및 Lite 플랜 한계에 대해 권한 부여된 사용자 목록을 확인하여 각 서비스 인스턴스에서 계수되고 관리됩니다. {{site.data.keyword.contdelivery_short}} 서비스 사용자는 이 목록에 자동으로 추가됩니다. 사용자가 도구 체인에 액세스하여 자동으로 {{site.data.keyword.contdelivery_short}} 서비스 인스턴스에 추가되지 않도록 할 수 있습니다. IAM을 사용하여 도구 체인이 포함된 리소스 그룹에서(또는 도구 체인 자체에서) 사용자 액세스를 제거하는 데 대한 자세한 정보는 [Identity and Access Management를 사용하여 {{site.data.keyword.contdelivery_short}}에 대한 사용자 액세스 관리](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security)를 참조하십시오. 

리소스 그룹 내에서 도구 체인을 구성하는 데 사용하는 방법은 사용자 액세스 및 비용 청구에 직접 영향을 줍니다. 사용자가 여러 리소스 그룹에서 도구 체인을 사용하는 경우 해당 리소스 그룹의 각 서비스에 대해 계수되고 청구됩니다.
{: tip}

{{site.data.keyword.contdelivery_short}} 서비스 인스턴스 내 **관리** 탭에서 권한 부여된 사용자 목록을 관리할 수 있습니다.

1. {{site.data.keyword.Bluemix_notm}} 계정의 [리소스 목록](https://cloud.ibm.com/resources){:external}으로 이동하십시오.
2. **이름** 열의 필터 텍스트 상자에 **Continuous Delivery**를 입력하여 기존 서비스를 표시하십시오.
3. 각 서비스에 대해 **이름** 열의 하이퍼링크를 클릭하십시오.
4. **관리** 탭에서 필요에 따라 권한 부여된 사용자 목록의 사용자를 보거나 추가하거나 제거할 수 있습니다.

사용자가 {{site.data.keyword.contdelivery_short}} 서비스를 사용할 때 자동으로 추가되거나 다시 추가됩니다.
{: tip}

### 조직의 {{site.data.keyword.contdelivery_short}} 인스턴스에 대한 사용자를 어떻게 계산합니까?

권한 부여된 사용자는 {{site.data.keyword.contdelivery_short}} 서비스가 포함된 {{site.data.keyword.Bluemix_notm}} 조직의 모든 사용자를 확인하여 계수됩니다. 조직 및 영역에 대한 자세한 정보는 [조직 및 영역 작성](/docs/cloud-foundry?topic=cloud-foundry-create_orgs)을 참조하십시오.

{{site.data.keyword.Bluemix_notm}} Public 환경에서 조직의 사용자 목록을 보려면 메뉴 표시줄에서 **관리 > 계정**을 클릭하십시오. 그 후 **Cloud Foundry 조직**을 클릭하십시오.

### 비용 청구 및 사용 정보를 보는 방법은 무엇입니까?

계정에 있는 {{site.data.keyword.contdelivery_short}} 서비스의 모든 인스턴스 및 {{site.data.keyword.Bluemix_notm}} Public 환경에서 각 인스턴스에 대해 보고되는 사용자 및 파이프라인 실행의 수를 볼 수 있습니다.

1. 메뉴 표시줄에서 **관리 > 청구 및 사용**을 클릭하십시오.
2. **사용**을 클릭하십시오.
3. **서비스** 섹션에서 {{site.data.keyword.contdelivery_short}} 서비스에 대해 **플랜 보기**를 클릭하십시오.
4. 정보를 볼 플랜에 대해 **세부사항 보기**를 클릭하십시오.
5. 사용 정보를 볼 {{site.data.keyword.contdelivery_short}}의 인스턴스에 대해 **인스턴스 세부사항 보기**를 클릭하십시오.

`AUTHORIZED_USERS_PER_MONTH` 메트릭은 매일 계수되는 월간 평균 사용자 수에 따라 계산됩니다.
{: tip}

### 서비스 플랜의 한계를 초과하면 어떤 일이 발생합니까?

Lite 서비스 플랜에는 스토리지 이용량 또는 실행할 수 있는 Delivery Pipeline 작업의 수와 같은 다른 제한사항이 있습니다. 플랜 설명에 대한 자세한 정보는 [서비스 카탈로그](https://cloud.ibm.com/catalog/services/continuous-delivery){:external}를 참조하십시오. 비용 청구 기간에 플랜 한계가 초과되는 경우 서비스가 일시중단됩니다. 예를 들어, Delivery Pipeline 작업이 나머지 비용 청구 기간 동안 실행되지 않습니다.

## Delivery Pipeline 사용
{: #pipeline_usage}

다음 행위가 허용되지만 이에 국한되지는 않습니다.

* 지원되는 프로그래밍 언어에 대한 아티팩트의 컴파일 및 어셈블리.
* 애플리케이션 아티팩트, 구성 및 지원 리소스나 서비스의 자동화된 배치.
* 테스트, 유효성 검증, 그리고 개발 프로세스의 결과로서 트리거되는 기타 개발 이벤트 생성 행위.

허용되지 않는 이용 행위에는 다음 행위가 포함되지만 이에 국한되지는 않습니다.

* 일반 컴퓨팅 행위에 대한 작업자 또는 파이프라인 작업의 이용(예: 비트코인 마이닝, 분산 서비스 거부(DoS) 공격, 그리고 일반 인터넷 사용자 또는 {{site.data.keyword.Bluemix_notm}} 플랫폼 내의 기타 클라이언트 또는 사용자에 대한 악의적이거나 공격적인 동작).
* 혐오 발언 또는 IBM Business Conduct Guidelines를 위반하는 기타 활동을 조장하는 서비스 또는 사이트에 대한 일반 개발 프로세스의 이용.
* {{site.data.keyword.Bluemix_notm}} 또는 기타 사이트에 대한 악의적 침해나 공격에 이벤트 생성 행위의 이용.

IBM의 재량에 따라, {{site.data.keyword.contdelivery_short}} 서비스의 허용되는 이용 행위나 [IBM Business Conduct Guidelines](https://www.ibm.com/investor/governance/business-conduct-guidelines.html){:external}를 위반하는 사용자는 통지 없이 사용이 거부될 수 있습니다. IBM의 재량에 따라, 공격적 행위에 대해 통지를 받은 후에 사용자가 해당 이용 행위를 바로잡은 경우에는 일부 서비스가 복원될 수 있습니다. 그렇지 않으면, 계정이 일시중단되거나 중지될 수 있습니다.

## Git Repos and Issue Tracking 제한사항
{: #git_limitations}

{{site.data.keyword.gitrepos}}은 GitLab Community Edition에 빌드되어 IBM이 {{site.data.keyword.Bluemix_notm}}에서 호스팅하고 있습니다. 그러나 몇 가지 GitLab 옵션은 사용할 수 없습니다.

 * {{site.data.keyword.deliverypipeline}}이 {{site.data.keyword.Bluemix_notm}}에 대해 지속적 통합 및 지속적 딜리버리를 제공하기 때문에 GitLab에서 지속적 통합 기능은 지원되지 않습니다.
 * IBM에서 관리하기 때문에 GitLab 관리자 기능은 사용할 수 없습니다.
 * {{site.data.keyword.gitrepos}}에 완전하게 액세스할 수 없을 수 있습니다.

## Git Repos and Issue Tracking 사용자 정보 및 컨텐츠
{: #git_projects}

다음 세 가지 유형의 {{site.data.keyword.gitrepos}} 프로젝트가 사용 가능합니다.

  1. 공용 프로젝트는 모든 사이트 방문자에게 표시됩니다. 공용 프로젝트의 컨텐츠는 프로젝트에 초대되지 않은 경우라도 {{site.data.keyword.contdelivery_short}}에 액세스하는 모든 사용자에게 표시됩니다.
  2. 개인용 프로젝트는 선택한 사용자에게만 표시됩니다. 프로젝트에 대한 사용자 액세스 권한 부여의 자세한 정보는 [Project users](https://us-south.git.cloud.ibm.com/help/user/project/members/index.md){:external}를 참조하십시오.
  3. 내부 프로젝트는 로그인한 모든 사용자들에게 표시됩니다. {{site.data.keyword.Bluemix_notm}} 계정이 있는 사용자는 이러한 프로젝트를 볼 수 있습니다.

프로젝트의 설정에서 프로젝트 유형을 수정할 수 있습니다. 프로젝트 설정에 대한 자세한 정보는 [프로젝트 가시성 변경 방법](https://us-south.git.cloud.ibm.com/help/public_access/public_access#how-to-change-project-visibility){:external}을 참조하십시오.

{{site.data.keyword.gitrepos}}을 사용할 때 사용자가 프로젝트에 제공하는 컨텐츠는 그 프로젝트에 지정된 조항 아래에서 라이센스가 부여됩니다. 프로젝트를 작성할 때는 컨텐츠에 적용되는 라이센스를 설명하는 파일을 포함하십시오. 프로젝트에 제공할 때 커미트와 연관된 사용자의 이름 및 이메일 주소가 공개적으로 표시될 수 있습니다. {{site.data.keyword.Bluemix_notm}} 계정과 연관된 이메일 주소가 {{site.data.keyword.gitrepos}} 웹 인터페이스를 통해 커미트를 작성할 때 사용됩니다.
