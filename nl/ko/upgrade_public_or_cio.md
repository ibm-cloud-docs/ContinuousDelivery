---

copyright:
  years: 2015, 2017
lastupdated: "2017-5-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# IBM 기밀 프로젝트를 도구 체인으로 업그레이드 
{: #upgrade_public_or_cio}

{{site.data.keyword.jazzhub}}는 IBM Bluemix {{site.data.keyword.contdelivery_short}}로 진화 중입니다. 해당 변경사항의 일부로서 프로젝트는 도구 체인으로 업그레이드됩니다. 

프로젝트의 업그레이드가 준비되면 메시지가 개요 페이지에 표시됩니다. 그리고 나서 프로젝트를 {{site.data.keyword.Bluemix_notm}} 퍼블릭의 도구 체인으로 업그레이드할 수 있습니다. 도구 체인에는 소스 코드에 대한 Whitewater {{site.data.keyword.ghe_short}} 저장소(repo)가 포함됩니다. Whitewater {{site.data.keyword.ghe_short}}는 IBM 내의 소셜 코딩을 촉진하고 사용 가능하게 하도록 IBM 팀에 제공됩니다.
{: shortdesc}

**{{site.data.keyword.contdelivery_short}} 도구 체인은 Whitewater {{site.data.keyword.ghe_short}}와 함께 사용될 때 IBM 기밀 자료로 승인됩니다.** Whitewater {{site.data.keyword.ghe_short}} 저장소에서 입력을 수신하는 Delivery Pipeline은 스테이징(YS1) 및 퍼블릭(YP) 환경에 배치할 수 있습니다. 

업그레이드 중에 사용자를 대신해서 Whitewater {{site.data.keyword.ghe_short}}에 액세스하도록 {{site.data.keyword.contdelivery_short}}에 권한을 부여하기 위한 프롬프트가 표시됩니다. 

## 업그레이드 후에 Whitewater {{site.data.keyword.ghe_short}} 저장소에 구성원 추가

프로젝트가 JazzHub에 호스팅된 저장소를 사용하는 경우, 업그레이드 중에 새 저장소가 Whitewater {{site.data.keyword.ghe_short}}에서 작성됩니다. 업그레이드 후에는 업그레이드를 시작한 사용자가 Whitewater {{site.data.keyword.ghe_short}} 저장소에 팀 구성원을 추가하고 새 저장소에 액세스할 수 있는 올바른 권한이 있는지 먼저 확인해야 합니다.

## 문제점 해결

파이프라인 배치 단계의 대상을 변경하려고 할 때 간헐적 문제점이 가끔 발생합니다. 이 문제점이 발생하면 오류가 **조직** 및 **영역** 필드에 표시됩니다.

이 문제점은 일반적으로 업그레이드 중에 작성된 파이프라인이 이전과 같은 대상에 올바르게 배치되도록 파이프라인에서 대상을 변경할 때에만 발생합니다. 

대상을 변경하려고 할 때 이 문제점이 발생하는 경우, **조직** 및 **영역** 필드가 채워질 때까지 대상 간에 몇 번 전환하십시오. 

관련된 문제점이 때때로 YS1 대상으로 배치 실패의 원인이 됩니다. 이러한 상황은 드물지만 발생하는 경우에는 파이프라인을 다시 실행하십시오. 

IBM DevOps 서비스팀이 이러한 문제점을 해결하기 위해 적극적으로 작업하고 있습니다.
