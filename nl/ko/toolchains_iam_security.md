---

copyright:
  years:  2018, 2019
lastupdated: "2019-02-27"

keywords: Administrator Create, Editor Update, Update, user access

subcollection: ContinuousDelivery

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Identity and Access Management를 사용하여 도구 체인에 대한 사용자 액세스 관리
{: #toolchains-iam-security}

계정에 있는 사용자의 리소스 그룹에서 도구 체인에 대한 액세스는 {{site.data.keyword.Bluemix_notm}} Identity and Access Management(IAM)를 사용하여 제어됩니다. 

**참고**: 

* {{site.data.keyword.contdelivery_short}} 서비스 인스턴스 및 도구 체인 인스턴스의 사용자 액세스는 별도로 관리됩니다. 리소스 그룹의 {{site.data.keyword.contdelivery_short}} 서비스 인스턴스에 대한 사용자 액세스 관리의 자세한 정보는 [Identity and Access Management를 사용하여 {{site.data.keyword.contdelivery_short}}에 대한 사용자 액세스 관리](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-cd-iam-security){: new_window}를 참조하십시오.

* Cloud Foundry 조직의 도구 체인에 대한 사용자 액세스는 리소스 그룹의 {{site.data.keyword.contdelivery_short}} 서비스 인스턴스에 대한 사용자 액세스와는 다르게 관리됩니다. Cloud Foundry 조직의 도구 체인에 대한 사용자 액세스 관리의 자세한 정보는 [Cloud Foundry 조직의 도구 체인에 대한 액세스 관리](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs){: new_window}를 참조하십시오.

계정의 도구 체인에 액세스하는 모든 사용자에게 IAM 사용자 역할이 정의된 액세스 정책을 지정해야 합니다. 이 정책은 선택한 서비스 또는 인스턴스의 컨텍스트 내에서 사용자가 수행할 수 있는 조치를 판별합니다. 허용 가능한 조치는 서비스에서 수행할 수 있는 오퍼레이션으로서 {{site.data.keyword.Bluemix_notm}} 서비스에서 정의되고 사용자 정의됩니다. 그런 다음 조치는 IAM 사용자 역할에 맵핑됩니다.

정책을 사용하면 다음을 포함하여 여러 레벨에서 액세스 권한을 부여할 수 있습니다. 

* 계정에 있는 서비스의 모든 인스턴스에 액세스
* 계정에 있는 개별 서비스 인스턴스에 액세스
* 인스턴스 내 특정 리소스에 액세스
* 계정의 모든 IAM 사용 서비스에 액세스

액세스 정책 범위를 정의한 후 역할을 지정하십시오. 도구 체인 내에서 각 역할이 허용하는 조치를 설명하는 다음 표를 검토하십시오.

다음 표에는 플랫폼 관리 역할에 맵핑된 조치에 대한 자세한 설명이 있습니다. 플랫폼 관리 역할을 사용하면 사용자가 플랫폼 레벨에서 서비스 리소스에 대한 태스크를 수행할 수 있습니다(예: 서비스에 대한 사용자 액세스 지정, 서비스 ID 작성 또는 삭제, 인스턴스 작성 및 애플리케이션에 인스턴스 바인드).

| 플랫폼 관리 역할 | 조치 설명 | 조치 예|
|:-----------------|:-----------------|:-----------------|
| 뷰어, 운영자 | 도구 체인 및 Delivery Pipeline을 봅니다. Delivery Pipeline을 실행합니다. | <ul><li>도구 체인을 클릭하여 개요 페이지를 엽니다.</li><li>파이프라인 작업이 있는 단계의 **단계 실행** 아이콘을 클릭합니다.</li></ul> |
| 편집자, 관리자 | 도구 체인 및 Delivery Pipeline을 작성하고 보고 업데이트하고 삭제합니다. |<ul><li>DevOps 대시보드의 **도구 체인** 페이지에서 **도구 체인 작성**을 클릭하십시오.</li><li>DevOps 대시보드의 **도구 체인** 페이지에서 도구 체인을 클릭하여 해당 개요 페이지를 여십시오.</li><li>DevOps 대시보드의 **도구 체인** 페이지에서 삭제할 도구 체인을 클릭하십시오. **앱 보기** 옆에 있는 **추가 조치** 메뉴를 클릭하십시오. **삭제**를 클릭하십시오.</li></ul> |
{: caption="표 1. IAM 사용자 역할 및 조치" caption-side="top"}

 도구 체인의 경우 다음 조치가 있습니다.

| 조치 | 서비스에 대한 오퍼레이션 | 역할
|:-----------------|:-----------------|:--------------|
| create | 리소스 그룹에서 도구 체인을 작성합니다. | 관리자, 편집자 |
| update | 리소스 그룹에서 도구 체인을 업데이트합니다. 예를 들어, 도구 체인의 이름을 바꿉니다. 리소스 그룹의 도구 체인에 바인드되는 Delivery Pipeline을 변경합니다. | 관리자, 편집자 |
| update_plan | 해당되지 않습니다. | 관리자, 편집자 |
| delete | 리소스 그룹에서 도구 체인을 삭제합니다. | 관리자, 편집자 |
| retrieve | 리소스 그룹에서 도구 체인의 세부사항을 업데이트합니다. 리소스 그룹의 도구 체인에 바인드되는 Delivery Pipeline을 보고 실행합니다. | 관리자, 편집자, 운영자, 뷰어 |
| list-bindings | 리소스 그룹에서 도구 체인에 바인드된 도구 통합을 봅니다. | 관리자, 편집자, 뷰어 |
| create-bindings | 리소스 그룹에서 도구 체인에 도구 통합을 추가합니다. | 관리자, 편집자 |
| delete-bindings | 리소스 그룹의 도구 체인에서 도구 통합을 제거합니다. | 관리자, 편집자 |
{: caption="표 2. 서비스 조치 및 오퍼레이션" caption-side="top"}

UI에서 사용자 역할 지정에 대한 정보는 [IAM 액세스 관리](/docs/iam?topic=iam-iammanidaccser)를 참조하십시오.

<!--This link is not live in production yet. Use https://console.bluemix.net/docs/iam/iamusermanage.html#iamusermanage until the link above is available in production.-->
