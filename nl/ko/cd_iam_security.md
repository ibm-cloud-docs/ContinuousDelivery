---

copyright:
  years:  2018, 2019
lastupdated: "2019-02-25"

keywords: Administrator Create, Administrator Update, Editor Update, Update

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


# Identity and Access Management를 사용하여 Continuous Delivery에 대한 사용자 액세스 관리
{: #cd-iam-security}

계정에 있는 사용자의 리소스 그룹에서 {{site.data.keyword.contdelivery_full}} 서비스 인스턴스에 대한 액세스는 {{site.data.keyword.Bluemix_notm}} Identity and Access Management(IAM)를 사용하여 제어됩니다. 

**참고**: 

* {{site.data.keyword.contdelivery_short}} 서비스 인스턴스 및 도구 체인 인스턴스의 사용자 액세스는 별도로 관리됩니다. 리소스 그룹의 도구 체인에 대한 사용자 액세스 관리의 자세한 정보는 [Identity and Access Management를 사용하여 도구 체인에 대한 사용자 액세스 관리](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security){: new_window}를 참조하십시오.

* Cloud Foundry 조직의 도구 체인에 대한 사용자 액세스는 리소스 그룹의 도구 체인에 대한 사용자 액세스와는 다르게 관리됩니다. Cloud Foundry 조직의 도구 체인에 대한 사용자 액세스 관리의 자세한 정보는 [Cloud Foundry 조직의 도구 체인에 대한 액세스 관리](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#managing_access_orgs){: new_window}를 참조하십시오.

계정의 {{site.data.keyword.contdelivery_short}} 서비스에 액세스하는 모든 사용자에게 IAM 사용자 역할이 정의된 액세스 정책을 지정해야 합니다. 이 정책은 선택한 서비스 또는 인스턴스의 컨텍스트 내에서 사용자가 수행할 수 있는 조치를 판별합니다. 허용 가능한 조치는 서비스에서 수행할 수 있는 오퍼레이션으로서 {{site.data.keyword.Bluemix_notm}} 서비스에서 정의되고 사용자 정의됩니다. 그런 다음 조치는 IAM 사용자 역할에 맵핑됩니다.

정책을 사용하면 여러 레벨에서 액세스 권한을 부여할 수 있습니다. 일부 옵션은 다음과 같습니다. 

* 계정에 있는 서비스의 모든 인스턴스에 액세스
* 계정에 있는 개별 서비스 인스턴스에 액세스
* 인스턴스 내 특정 리소스에 액세스
* 계정의 모든 IAM 사용 서비스에 액세스

액세스 정책 범위를 정의한 후 역할을 지정하십시오. {{site.data.keyword.contdelivery_short}} 서비스 내에서 각 역할이 허용하는 조치를 설명하는 다음 표를 검토하십시오.

다음 표에는 플랫폼 관리 역할에 맵핑된 조치에 대한 자세한 설명이 있습니다. 플랫폼 관리 역할을 사용하면 사용자가 플랫폼 레벨에서 서비스 리소스에 대한 태스크를 수행할 수 있습니다(예: 서비스에 대한 사용자 액세스 지정, 서비스 ID 작성 또는 삭제, 인스턴스 작성 및 애플리케이션에 인스턴스 바인드).

| 플랫폼 관리 역할 | 조치 설명 | 조치 예|
|:-----------------|:-----------------|:-----------------|
| 뷰어, 운영자 | {{site.data.keyword.contdelivery_short}} 서비스의 인스턴스를 봅니다. | <ul><li>{{site.data.keyword.contdelivery_short}} 서비스 인스턴스를 클릭하여 해당 대시보드를 엽니다.</li></ul>|
| 편집자, 관리자 | {{site.data.keyword.contdelivery_short}} 서비스에 대한 플랜을 작성하고, 보고, 업데이트하고, 수정하며, 이 서비스의 인스턴스를 삭제합니다. |<ul><li>리소스 그룹에서 {{site.data.keyword.contdelivery_short}}의 인스턴스를 프로비저닝합니다.</li><li>리소스 그룹에서 {{site.data.keyword.contdelivery_short}}의 인스턴스를 삭제합니다.</li><li>{{site.data.keyword.contdelivery_short}} 인스턴스 플랜을 Lite에서 프로페셔널로 변경합니다.</li></ul> |
| 관리자 | 권한 부여된 사용자 목록을 업데이트합니다.| <ul><li>권한 부여된 사용자 목록에 사용자를 추가합니다.</li><li>권한 부여된 사용자 목록에서 사용자를 제거합니다.</li></ul> |
{: caption="표 1. IAM 사용자 역할 및 조치" caption-side="top"}

 {{site.data.keyword.contdelivery_short}}의 경우 다음 조치가 있습니다.

| 조치 | 서비스에 대한 오퍼레이션 | 역할
|:-----------------|:-----------------|:--------------|
| create | 리소스 그룹에서 {{site.data.keyword.contdelivery_short}} 서비스 인스턴스를 프로비저닝합니다. | 관리자, 편집자 |
| update | 리소스 그룹에서 {{site.data.keyword.contdelivery_short}} 서비스 인스턴스를 업데이트합니다. 예를 들어, 서비스 인스턴스의 이름을 바꿉니다. | 관리자, 편집자 |
| update_plan | 리소스 그룹에서 {{site.data.keyword.contdelivery_short}} 서비스 인스턴스의 플랜을 변경합니다. | 관리자, 편집자 |
| delete | 리소스 그룹에서 {{site.data.keyword.contdelivery_short}} 서비스 인스턴스를 삭제합니다. | 관리자, 편집자 |
| retrieve | 리소스 그룹에서 {{site.data.keyword.contdelivery_short}} 서비스 인스턴스를 봅니다. | 관리자, 편집자, 운영자, 뷰어 |
| add-auth-users | {{site.data.keyword.contdelivery_short}} 서비스 인스턴스 내에서 관리 탭의 권한 부여된 사용자 목록에 항목을 추가합니다. | 관리자(Administrator), 작성자, 관리자(Manager) |
| remove-auth-users | {{site.data.keyword.contdelivery_short}} 서비스 인스턴스 내에서 관리 탭의 권한 부여된 사용자 목록에서 항목을 제거합니다. | 관리자(Administrator), 작성자, 관리자(Manager) |
{: caption="표 2. 서비스 조치 및 오퍼레이션" caption-side="top"}

다음 표에는 서비스 액세스 역할에 맵핑된 조치에 대한 자세한 설명이 있습니다. 서비스 액세스 역할을 사용하면 사용자가 {{site.data.keyword.contdelivery_short}} API 호출 기능뿐만 아니라 {{site.data.keyword.contdelivery_short}}에 액세스할 수 있습니다.

| 서비스 액세스 역할 | 조치 설명 | 조치 예|
|:-----------------|:-----------------|:-----------------|
| 작성자, 관리자 | {{site.data.keyword.contdelivery_short}} 서비스 인스턴스 내에서 관리 탭의 권한 부여된 사용자 목록에서 사용자를 추가하고 제거합니다. | <ul><li>권한 부여된 사용자를 추가합니다.</li><li>권한 부여된 사용자를 제거합니다.</li></ul>|
{: caption="표 3. IAM 서비스 액세스 역할 및 조치" caption-side="top"}

UI에서 사용자 역할 지정에 대한 정보는 [IAM 액세스 관리](/docs/iam?topic=iam-iammanidaccser)를 참조하십시오.

<!--This link is not live in production yet. Use https://console.bluemix.net/docs/iam/iamusermanage.html#iamusermanage until the link above is available in production.-->
