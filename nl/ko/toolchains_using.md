---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-18"

keywords: user management function, tool integrations, Cloud Foundry org

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
{:tip: .tip}
{:important: .important}

# 도구 체인 사용
{: #toolchains-using}

오픈 도구 체인은 {{site.data.keyword.Bluemix}} Public 및 Dedicated 환경에서 사용 가능합니다. 도구 체인을 사용하여 일상적인 개발, 배치 및 및 운영 작업의 생산성을 향상시킬 수 있습니다. 도구 체인을 설정한 후에는 도구 통합을 추가, 삭제 또는 구성하거나 도구 체인에 대한 액세스를 관리할 수 있습니다.
{: shortdesc}

리소스 그룹을 사용하여 미국 남부, 미국 동부, 영국, 독일 및 도쿄 퍼블릭 지역에서 도구 체인을 관리할 수 있습니다. Cloud Foundry 조직을 사용하여 미국 남부, 영국 및 독일 퍼블릭 지역에서 도구 체인을 관리할 수 있습니다. 액세스 제어 및 권한 부여된 사용자 관리는 도구 체인이 리소스 그룹에 포함되었는지 아니면 Cloud Foundry 조직에 포함되었는지에 따라 도구 체인에 대해 다르게 작동합니다.
{: important}

## 도구 통합 구성
{: #configuring_a_tool_integration}

도구 체인을 작성할 때 도구 통합 구성을 연기한 경우에는 **구성** 단추가 해당 카드에 표시됩니다. 도구 체인을 작성할 때 도구 통합을 구성한 경우에는 구성 설정을 업데이트할 수 있습니다.

1. DevOps 대시보드의 **도구 체인** 페이지에서 도구 체인을 클릭하여 해당 개요 페이지를 여십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭한 후에 **개요**를 클릭하십시오.
1. 처음으로 도구 통합을 구성해야 하는 경우에는 해당 카드에서 **구성**을 클릭하십시오.

  ![구성 단추](images/toolchain_tile_configure.png)

 도구 통합 구성을 완료하면 **통합 저장**을 클릭하십시오.

1. 도구 통합의 구성을 업데이트해야 하는 경우에는 해당 카드에서 메뉴를 클릭하여 구성 옵션에 액세스하십시오.

  ![구성 메뉴](images/toolchain_tile_menu.png)

 일부 도구 통합은 사전 구성되어 있으며 구성 매개변수를 필요로 하지 않습니다. 자신이 구성한 도구 통합에 대해서만 구성 설정을 업데이트할 수 있습니다.
 {: tip}

 설정 업데이트를 완료하면 **통합 저장**을 클릭하십시오. 특정 도구 통합 구성에 대한 자세한 정보는 [도구 통합 구성](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations)을 참조하십시오.

## 도구 통합 추가
{: #adding_a_tool_integration}

도구 체인의 도구 통합을 추가하고 구성할 수 있습니다. 사용 가능한 도구 통합은 {{site.data.keyword.Bluemix_notm}} Public 또는 {{site.data.keyword.Bluemix_notm}} Dedicated를 사용하는지 여부에 따라 다릅니다.

1. DevOps 대시보드의 **도구 체인** 페이지에서 도구 체인을 클릭하여 해당 개요 페이지를 여십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭한 후에 **개요**를 클릭하십시오.
1. 추가할 도구 통합의 목록을 보려면 **도구 추가**를 클릭하십시오.
1. 추가할 도구 통합을 클릭하십시오.
1. 도구 통합을 구성하는 데 필요한 정보를 입력하십시오.
1. **통합 작성**을 클릭하여 도구 체인에 도구 통합을 추가하십시오.

## 도구 통합 삭제
{: #deleting_a_tool_integration}

도구 체인에서 도구 통합을 삭제하는 경우 삭제를 실행 취소할 수 없습니다.

1. DevOps 대시보드의 **도구 체인** 페이지에서 도구 체인을 클릭하여 해당 개요 페이지를 여십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭한 후에 **개요**를 클릭하십시오.
1. 삭제할 도구 통합의 카드에서 메뉴를 클릭하여 구성 옵션에 액세스하십시오.
1. 도구 체인에서 도구 통합을 삭제하려면 **삭제**를 클릭하십시오.
1. **삭제**를 클릭하여 확인하십시오.  

## 리소스 그룹의 도구 체인에 대한 액세스 관리
{: #managing_access_resource_groups}

Identity and Access Management(IAM) 서비스를 사용하여 도구 체인에 대한 사용자 액세스를 관리할 수 있습니다. IAM을 사용한 액세스 제어 관리에 대한 자세한 정보는 [Identity and Access Management를 사용하여 도구 체인에 대한 사용자 액세스 관리](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security)를 참조하십시오. 

{{site.data.keyword.contdelivery_short}}의 선택된 인스턴스에 대한 권한 부여된 사용자 목록에 있는 사용자만 Delivery Pipeline, Eclipse Orion {{site.data.keyword.webide}} 및 {{site.data.keyword.contdelivery_short}} 도구 체인의 {{site.data.keyword.gitrepos}} 기능을 사용할 수 있습니다. 지정된 리소스 그룹 내에서 {{site.data.keyword.contdelivery_short}}의 선택된 인스턴스의 관리 탭을 사용하여 권한 부여된 사용자 자격을 관리할 수 있습니다.

Delivery Pipeline과 같은 도구 체인에 있는 {{site.data.keyword.contdelivery_short}}의 주요 기능에 액세스하려면 사용자에게 IAM의 도구 체인에 대한 액세스 권한이 있어야 하고 사용자는 {{site.data.keyword.contdelivery_short}} 인스턴스의 권한 부여된 사용자 목록에 있어야 합니다.
{: important}

권한 부여된 사용자 자격은 {{site.data.keyword.contdelivery_short}}의 인스턴스와 동일한 리소스 그룹에 포함된 모든 도구 체인에 적용됩니다.
{: tip}


## Cloud Foundry 조직의 도구 체인에 대한 액세스 관리
{: #managing_access_orgs}

도구 체인이 연관된 조직 및 도구 체인의 액세스 제어 목록 모두에 사용자를 추가하여 도구 체인에 대한 액세스 권한을 해당 사용자에게 부여할 수 있습니다. 각 도구 체인은 특정 조직과 연관되어 있으며 해당 조직의 구성원인 사용자는 이와 연관된 도구 체인의 액세스 제어 목록에 추가될 수 있습니다. 현재 작업 중인 조직은 메뉴 표시줄에 표시됩니다. 다른 도구 체인 세트에 액세스하려면 다른 조직으로 전환하십시오.

도구 체인이 호스팅되는 지역에 있는 도구 체인의 조직에 사용자를 추가해야 합니다. 앱을 다른 지역에 배치하도록 도구 체인이 구성된 경우 여전히 해당 지역에 앱을 배치합니다.
{: important}

{{site.data.keyword.ghe_short}}용 {{site.data.keyword.Bluemix_notm}} Dedicated를 사용 중인 경우, {{site.data.keyword.Bluemix_notm}} 조직 및 영역에 사용자를 추가하면 해당 사용자가 자체 {{site.data.keyword.Bluemix_notm}} ID 및 비밀번호를 사용하여 {{site.data.keyword.ghe_short}}에 로그인할 수 있습니다. 사용자가 로그인할 때 사용자의 계정이 작성됩니다. {{site.data.keyword.Bluemix_notm}} 조직 및 영역에 사용자를 추가하는 경우, {{site.data.keyword.ghe_short}} 저장소에는 자동으로 추가되지 않습니다. 저장소에 대해 관리자 권한이 있는 사용자가 추가해야 합니다. 자세한 정보는 [Dedicated GitHub Enterprise 사용](/docs/services/ghededicated?topic=ghededicated-getting-started)을 참조하십시오. {{site.data.keyword.ghe_short}}의 자체 관리 버전을 사용 중이면 내부 프로시저를 따르십시오.

###도구 체인에 대한 액세스 관리를 위한 팁

* 도구 체인 액세스를 관리하려면 DevOps 대시보드의 **도구 체인** 페이지에서 관리할 도구 체인을 클릭한 후에 **관리**를 클릭하십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭한 후에 **관리**를 클릭하십시오.

* 도구 체인의 조직의 모든 구성원에게 액세스 권한을 부여하려면 **조직 추가**를 클릭하십시오. 해당 조직의 모든 구성원이 도구 체인을 볼 수 있습니다.

* 조직 또는 사용자에게 관리자 권한을 부여할 수 있습니다. 관리자는 도구 체인을 수정하고 삭제할 수 있습니다. 관리자 권한을 부여하려면 조직 또는 사용자에 대해 **관리자** 선택란을 선택하십시오.

* 조직에 대해 **관리자** 선택란을 선택하면 해당 조직의 모든 구성원이 관리자가 됩니다. 조직에 관리자 권한을 부여한 후에 조직에 구성원을 추가하는 경우, 해당 구성원에는 조직의 나머지 구성원과 동일한 액세스 권한이 부여됩니다.

* 도구 체인의 조직의 구성원인 사용자에게 액세스 권한을 부여하려면 사용자 ID를 입력하고 **사용자 추가**를 클릭하십시오. 사용자는 도구 체인을 볼 수 있습니다.

* 도구 체인의 조직의 구성원이 아닌 사용자에게 액세스 권한을 부여하려면 다음 단계를 따르십시오.

   a. 메뉴 표시줄에서 **관리 > 액세스(IAM)**를 클릭하십시오.

   b. **사용자로 액세스 시작**을 클릭하십시오.
   
   c. 액세스 권한을 지정하려는 사용자에 대한 행에서 **조치** 메뉴를 선택한 후 **액세스 권한 지정**을 클릭하십시오.
   
   d. **Cloud Foundry를 사용한 액세스 권한 지정**을 선택하십시오.

   e. **조직 지정**을 선택하십시오.

   f. 사용자 액세스 권한을 지정하십시오.

     * 사용자를 추가할 조직을 선택하십시오.

     * 조직 역할을 지정하십시오.

     * 지역을 선택하십시오.

     * 영역을 선택하십시오.

     * 조직의 선택된 영역에 대한 역할을 지정하십시오.

     기본적으로 조직 관리자에게는 조직과 연관된 모든 도구 체인에 대한 전체 관리자 권한이 있습니다. 사용자에게 전체 관리자 권한을 부여하려면 **관리자** 역할을 선택하십시오. 청구 관리자 및 감사자 역할은 도구 체인 액세스에 영향을 주지 않습니다. 나중에 팀 디렉토리 페이지에서 역할을 변경할 수 있습니다. 자세한 정보는 [Cloud Foundry 역할](/docs/iam?topic=iam-cfaccess#cfaccess)을 참조하십시오.
     {: tip}

   사용자가 조직의 구성원이 된 후에는 도구 체인의 관리 페이지로 돌아가서 사용자를 도구 체인에 추가하십시오.  


## 도구 체인 구성
{: #organizing_toolchains}

도구 체인을 구성하고 나중에 쉽게 찾을 수 있도록 이 도구 체인에 태그를 추가할 수 있습니다. 태그는 도구 체인 목록에서 도구 체인을 쉽게 필터링하기 위해 도구 체인에 지정하는 레이블입니다.

1. DevOps 대시보드의 **도구 체인** 페이지에서 태그를 추가할 도구 체인을 찾아 **태그 추가**를 클릭하십시오.
1. 도구 체인에 추가할 태그의 이름을 입력하십시오. 쉼표로 구분된 여러 태그를 추가할 수 있습니다.
1. **저장**을 클릭하십시오.

태그에 대한 자세한 정보는 [태그 관련 작업](/docs/resources?topic=resources-tag#)을 참조하십시오.


## 도구 체인 삭제
{: #deleting_a_toolchain}

도구 체인을 삭제할 수 있으며 삭제할 연관된 도구 통합을 지정할 수 있습니다. 도구 체인을 삭제하는 경우 삭제를 실행 취소할 수 없습니다.

1. DevOps 대시보드의 **도구 체인** 페이지에서 삭제할 도구 체인을 클릭하십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭하십시오.
1. **앱 보기** 옆에 있는 **추가 조치** 메뉴를 클릭하십시오.
1. **삭제**를 클릭하십시오. 도구 체인을 삭제하면 도구 통합이 모두 제거되므로 해당 통합에서 관리하는 리소스를 삭제할 수 있습니다.
1. 도구 체인의 이름을 입력하고 **삭제**를 클릭하여 삭제를 확인하십시오.  

 GitHub, {{site.data.keyword.ghe_short}} 또는 {{site.data.keyword.gitrepos}} 도구 통합을 삭제할 때 연관된 저장소는 GitHub, {{site.data.keyword.ghe_short}} 또는 {{site.data.keyword.gitrepos}}에서 삭제되지 않습니다. 해당 저장소를 수동으로 제거해야 합니다.
 {: tip}

##튜토리얼 보기: 도구 체인 사용
{: #toolchain-tutorial}

[IBM&reg; Cloud Garage Method](https://www.ibm.com/cloud/garage){:external}에서 다음 튜토리얼을 확인하십시오.

  * ["Cloud Foundry 앱 개발" 도구 체인을 사용하여 첫 번째 도구 체인 작성 및 사용](https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain){:external}.

  * [앱에 도구 체인 추가](https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app?task=2){:external}.

  * ["Cloud Foundry에서 마이크로서비스 개발 및 테스트" 사용](https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain){:external}.
