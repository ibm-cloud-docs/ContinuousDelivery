---

copyright:
  years: 2019
lastupdated: "2019-06-28"

keywords: IBM Cloud Continuous Delivery, private workers integration

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


# {{site.data.keyword.deliverypipeline}} Private Worker에 대한 작업
{: #private-workers}

{{site.data.keyword.deliverypipeline}}은 공용 및 개인용 작업자를 사용하여 파이프라인 작업을 실행합니다. 기본적으로 파이프라인 작업은 IBM 관리 공용 공유 인프라에서 공용 작업자를 사용하여 실행됩니다.
{: shortdesc}

특정 시나리오에서는 {{site.data.keyword.deliverypipeline}}에 내부 또는 온프레미스 리소스에 대한 액세스 권한이 필요할 수도 있습니다. 이러한 상황에서 {{site.data.keyword.deliverypipeline}} Private Worker를 연결하고 통합하여 고유 Kubernetes 인프라에서 실행할 수 있습니다.

## 전제조건
{: #private_workers_prereqs}

개인용 작업자를 설정하기 전에 다음 리소스가 준비되어 있는지 확인하십시오.

* Kubernetes 클러스터. 개인용 작업자를 설치하려면 클러스터가 있어야 합니다. 고유 클러스터를 제공하거나 {{site.data.keyword.containerlong_notm}}에서 [클러스터를 설정](https://cloud.ibm.com/kubernetes/clusters){:external}할 수 있습니다.

* 하나 이상의 단계가 포함된 파이프라인이 있는 도구 체인. 기존 도구 체인을 사용하거나 [도구 체인을 작성](https://cloud.ibm.com/devops/create){:external}할 수 있습니다.

## {{site.data.keyword.deliverypipeline}} Private Worker 설정
{: #set_up_private_worker}

다음 단계를 완료하여 개인용 작업자를 설정하십시오.

1. 도구 체인에 맞는 {{site.data.keyword.deliverypipeline}} Private Worker 도구 통합을 구성하십시오.
2. 개인용 작업자로 Kubernetes 클러스터를 구성하십시오.
3. 파이프라인에서 개인용 작업자를 사용하십시오.

### {{site.data.keyword.deliverypipeline}} Private Worker 도구 통합 구성
{: #configure_private_worker_integration}

다음 단계를 완료하여 도구 체인에 맞는 {{site.data.keyword.deliverypipeline}} Private Worker 도구 통합을 구성하십시오.

1. 도구 체인을 작성할 때 이 도구 통합을 구성하는 경우, 구성 가능한 통합 섹션에서 **{{site.data.keyword.deliverypipeline}} Private Worker**를 클릭하십시오.
1. 도구 체인이 있고 여기에 이 도구 통합을 추가하는 경우 DevOps 대시보드의 도구 체인 페이지에서 도구 체인을 클릭하여 해당 개요 페이지를 여십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭하고 **개요**를 클릭하십시오.

 a. **도구 추가**를 클릭하십시오.

 b. 도구 통합 섹션에서 **{{site.data.keyword.deliverypipeline}} Private Worker**를 클릭하십시오.

1. 도구 통합의 이름을 입력하십시오. 이 이름은 파이프라인 단계의 **작업자** 탭에서 개인용 작업자의 풀을 식별합니다.
1. 서비스 ID API 키를 입력하여 하나 이상의 개인용 작업자가 작업을 찾을 수 있는 작업 큐에 대한 액세스를 인증하십시오. 서비스 ID API 키가 없는 경우 **작성**을 클릭하여 이 개인용 작업자에 대해 하나를 생성하십시오.
1. **통합 작성**을 클릭하십시오.
1. 도구 체인에서 이 서비스 ID와 연관된 API 키를 사용하여 등록된 모든 작업자 목록을 보려면 **{{site.data.keyword.deliverypipeline}} Private Worker**를 클릭하십시오.

**{{site.data.keyword.deliverypipeline}} Private Worker** 도구 통합에 대한 자세한 정보는 [{{site.data.keyword.deliverypipeline}} Private Worker 구성](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations#privateworker)을 참조하십시오.

### Kubernetes 클러스터 구성
{: #configure_kubernetes_cluster}

개인용 작업자로 Kubernetes 클러스터를 구성하십시오.

1. DevOps 대시보드의 **도구 체인** 페이지에서 도구 체인을 클릭하여 해당 개요 페이지를 여십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭한 후에 **개요**를 클릭하십시오.
1. 구성할 {{site.data.keyword.deliverypipeline}} Private Worker 도구 통합의 카드를 클릭하십시오.
1. **시작하기**를 클릭한 후 단계에 따라 Kubernetes 클러스터에서 개인용 작업자를 설치하고 등록하십시오.

### 파이프라인에서 {{site.data.keyword.deliverypipeline}} Private Worker 사용
{: #use_private_worker_pipeline}

다음 단계를 완료하여 파이프라인에서 개인용 작업자를 사용하십시오.

1. DevOps 대시보드의 **도구 체인** 페이지에서 도구 체인을 클릭하여 해당 개요 페이지를 여십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭한 후에 **개요**를 클릭하십시오.
1. 개인용 작업자를 사용할 파이프라인의 카드를 클릭하십시오.
1. 파이프라인 페이지의 단계에서 **단계 구성** 아이콘을 클릭한 다음 **단계 구성**을 클릭하십시오.
1. **작업자** 탭을 클릭하십시오.
1. 파이프라인에서 사용할 개인용 작업자를 선택하십시오. 

 기본적으로 파이프라인 단계의 작업은 파이프라인이 정의된 지역의 IBM 관리 공유 작업자 풀을 사용하여 실행됩니다.
 {: tip}
 
1. **저장**을 클릭하십시오.
1. 수동으로 단계를 실행하거나 트리거가 연관된 Kubernetes 클러스터에서 지정된 개인용 작업자를 사용하여 단계의 작업을 실행할 때까지 대기할 수 있습니다. 작업에 대한 로그 파일 출력을 보고 사용된 작업자를 판별할 수 있습니다.  


## {{site.data.keyword.deliverypipeline}} Private Worker 도구 통합 인증 정보 수정
{: #modify_private_worker}

개인용 작업자를 설정한 후 도구 통합에 사용되는 인증 정보를 업데이트할 수 있습니다. 이러한 인증 정보가 삭제되거나 만료되거나 손상된 경우 해당 인증 정보를 변경할 수 있습니다. 새 서비스 ID를 작성하거나 API 키를 업데이트하여 인증 정보를 업데이트할 수 있습니다.

### 서비스 ID 작성
{: #create_service_id}

다음 단계를 완료하여 서비스 ID를 작성하십시오.

1. DevOps 대시보드의 **도구 체인** 페이지에서 도구 체인을 클릭하여 해당 개요 페이지를 여십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭한 후에 **개요**를 클릭하십시오.
1. 수정할 개인용 작업자 도구 통합의 카드에서 메뉴를 클릭하여 구성 옵션에 액세스하십시오.
1. **작성**을 클릭하십시오.
1. 서비스 ID에 대한 이름과 설명을 입력하십시오.
1. **통합 저장**을 클릭하십시오.
1. DevOps 대시보드의 **도구 체인** 페이지에서 도구 체인을 클릭하여 해당 개요 페이지를 여십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭한 후에 **개요**를 클릭하십시오.
1. 사용자 인증 정보를 새로 지정할 {{site.data.keyword.deliverypipeline}} Private Worker 도구 통합의 카드를 클릭하십시오.
1. **시작하기**를 클릭하고 2와 3단계를 완료하여 클러스터에서 개인용 작업자를 등록하고 확인하십시오.

### API 키 업데이트
{: #update_api_key}

다음 단계를 완료하여 {{site.data.keyword.deliverypipeline}} Private Worker 도구 통합에 사용할 API 키를 업데이트하십시오.

1. DevOps 대시보드의 **도구 체인** 페이지에서 도구 체인을 클릭하여 해당 개요 페이지를 여십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭한 후에 **개요**를 클릭하십시오.
1. 수정할 {{site.data.keyword.deliverypipeline}} Private Worker 도구 통합의 카드에서 메뉴를 클릭하여 구성 옵션에 액세스하십시오.
1. 새 API 키를 지정하십시오. 
1. **통합 저장**을 클릭하십시오.

## {{site.data.keyword.deliverypipeline}} Private Worker 삭제
{: #delete_private_worker}

다음 단계를 완료하여 개인용 작업자를 삭제하십시오.

1. 작업자 풀에서 개인용 작업자를 삭제하십시오.
1. Kubernetes 클러스터에서 개인용 작업자를 삭제하십시오.

### 작업자 풀에서 {{site.data.keyword.deliverypipeline}} Private Worker 삭제

다음 단계를 완료하여 작업자 풀에서 개인용 작업자를 삭제하십시오.

1. DevOps 대시보드의 **도구 체인** 페이지에서 도구 체인을 클릭하여 해당 개요 페이지를 여십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭한 후에 **개요**를 클릭하십시오.
1. 구성할 {{site.data.keyword.deliverypipeline}} Private Worker 도구 통합의 카드를 클릭하십시오.
1. **개요**를 클릭하십시오.
1. 삭제할 개인용 작업자의 메뉴를 클릭하여 구성 옵션에 액세스하십시오.
1. **제거**를 클릭한 후 **확인**을 클릭하십시오.

### Kubernetes 클러스터에서 {{site.data.keyword.deliverypipeline}} Private Worker 삭제

다음 단계를 완료하여 클러스터에서 개인용 작업자를 삭제하십시오.

1. 구성할 {{site.data.keyword.deliverypipeline}} Private Worker 도구 통합의 카드를 클릭하십시오.
1. **시작하기**를 클릭하고 단계에 따라 클러스터에서 개인용 작업자를 삭제하십시오.

## {{site.data.keyword.deliverypipeline}} Private Worker 도구 통합 삭제
{: #delete_private_workers_tool_integration}

도구 체인에서 {{site.data.keyword.deliverypipeline}} Private Worker 도구 통합을 삭제하는 경우 삭제를 실행 취소할 수 없습니다.
{: important}

다음 단계를 완료하여 {{site.data.keyword.deliverypipeline}} Private Worker 도구 통합을 삭제하십시오.

1. DevOps 대시보드의 **도구 체인** 페이지에서 도구 체인을 클릭하여 해당 개요 페이지를 여십시오. 또는 앱 개요 페이지의 Continuous Delivery 카드에서 **도구 체인 보기**를 클릭한 후에 **개요**를 클릭하십시오.
1. 삭제할 {{site.data.keyword.deliverypipeline}} Private Worker 도구 통합의 카드에서 메뉴를 클릭하여 구성 옵션에 액세스하십시오.
1. 도구 체인에서 도구 통합을 삭제하려면 **삭제**를 클릭하십시오.
1. **삭제**를 클릭하여 확인하십시오. {{site.data.keyword.deliverypipeline}} Private Worker 도구 통합은 도구 체인에서 제거되며 Delivery Pipeline 단계 구성 페이지의 **작업자** 탭에서 더 이상 사용할 수 없습니다.

도구 체인에서 {{site.data.keyword.deliverypipeline}} Private Worker 도구 통합을 삭제하고 개인용 작업자가 파이프라인 단계에 대해 구성된 경우 단계 구성 페이지의 **작업자** 탭에 나열됩니다. 하지만 개인용 작업자는 사용 불가능하며 REMOVED로 레이블이 지정되어 있습니다. 다른 개인용 작업자(있는 경우)를 선택하거나 대신 공용 작업자를 사용해야 합니다.
{: tip}
