---

Copyright:
  years: 2015, 2018
lastupdated: "2018-8-2"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}


# 도구 체인 가용성, 템플리트 및 튜토리얼  
{: #cd_about}  

도구 체인은 {{site.data.keyword.Bluemix_notm}} 퍼블릭 및 데디케이티드에서 사용 가능합니다. 도구 체인을 작성하기 위한 시작점으로 템플리트를 사용할 수 있습니다.
{:shortdesc}

## {{site.data.keyword.Bluemix_notm}} 데디케이티드 및 {{site.data.keyword.Bluemix_notm}} 퍼블릭의 도구 체인 가용성 비교
{: #public_and_dedicated}

{{site.data.keyword.Bluemix_notm}} 퍼블릭은 사용자가 [http://bluemix.net ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://bluemix.net){:new_window}에 의해 액세스되는 애플리케이션을 빌드, 실행 및 관리할 수 있는 오픈 표준의 클라우드 기반 플랫폼입니다. {{site.data.keyword.Bluemix_notm}} 데디케이티드는 {{site.data.keyword.Bluemix_notm}} 퍼블릭 환경과 사용자 네트워크 모두에 안전하게 연결된 데디케이티드 SoftLayer 환경에서 {{site.data.keyword.Bluemix_notm}}의 기능을 제공합니다. 회사의 {{site.data.keyword.Bluemix_notm}} 데디케이티드 환경에 {{site.data.keyword.Bluemix_notm}} 퍼블릭 사이트와 동일한 도구 통합이 포함되지 않을 수 있습니다.

소스 코드 관리 및 문제 추적의 경우 {{site.data.keyword.Bluemix_notm}} 퍼블릭은 일반적으로 {{site.data.keyword.gitrepos}}(IBM에서 호스팅하고 [GitLab Community Edition ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://about.gitlab.com/){:new_window}에서 빌드됨) 또는 GitHub(github.com)를 사용합니다. {{site.data.keyword.Bluemix_notm}} 데디케이티드에서 github.com을 사용할 수도 있지만, 이는 일반적으로 사용자의 회사에서 설치하거나 IBM에서 관리하는 {{site.data.keyword.ghe_short}}를 사용합니다.

{{site.data.keyword.contdelivery_short}}는 {{site.data.keyword.Bluemix_notm}} 퍼블릭의 선택된 지역 및 {{site.data.keyword.Bluemix_notm}} 데디케이티드에서 사용 가능합니다. 도구 체인은 사용자가 {{site.data.keyword.contdelivery_short}}를 {{site.data.keyword.Bluemix_notm}} 퍼블릭에서 또는 {{site.data.keyword.Bluemix_notm}} 데디케이티드에서 사용하는지 여부에 따라 다릅니다.

현재는 도구 체인을 모든 지역에서 사용할 수 없지만, 모든 지역에 앱을 배치하도록 도구 체인을 구성할 수 있습니다. 자세히 알아보려면 <a href="/docs/tutorials/multi-region-webapp.html#deploy-a-secure-web-application-across-multiple-regions" target="_blank">여러 지역에서 보안 웹 애플리케이션 배치</a> 튜토리얼을 활용하십시오.
{: tip}

|도구 체인 |{{site.data.keyword.Bluemix_notm}} 퍼블릭	|{{site.data.keyword.Bluemix_notm}} 데디케이티드 |
|:----------|:------------------------------|:------------------|
|도구 통합 		|지원되는 도구 통합의 목록은 [도구 통합 구성](/docs/services/ContinuousDelivery/toolchains_integrations.html){: new_window}을 참조하십시오. 		|사용 가능한 도구 통합은 {{site.data.keyword.contdelivery_short}}가 사용자 환경에서 설정된 방법에 따라 다릅니다.			|
|템플리트에서 도구 체인 작성		|[{{site.data.keyword.Bluemix_notm}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://console.bluemix.net/devops){:new_window}에 로그인		|{{site.data.keyword.Bluemix_notm}}의 데디케이티드 환경에 로그인합니다.			|
|앱에서 도구 체인 작성		|앱 스타터 코드로 채워진 새 GitHub 저장소에서 지속적 딜리버리를 위해 앱이 구성됩니다.		|앱 스타터 코드로 채워진 새 GitHub 또는 GitHub Enterprise 저장소에서 지속적 딜리버리를 위해 앱이 구성됩니다.		|  
|딜리버리 파이프라인 배치 지역		|모든 {{site.data.keyword.Bluemix_notm}} 퍼블릭 지역이 Cloud Foundry 배치 작업에 사용 가능합니다. 		|{{site.data.keyword.Bluemix_notm}} 데디케이티드 지역이 사용 가능합니다. 또한 동일한 고객 계정 내의 기타 데디케이티드 또는 로컬 지역도 특정 환경에서 {{site.data.keyword.contdelivery_short}}가 설정된 방법에 따라 사용이 가능합니다.		|
|딜리버리 파이프라인 배치 작업		|모든 [작업 유형](/docs/services/ContinuousDelivery/pipeline_about.html#deliverypipeline_jobs)이 사용 가능합니다.		|데디케이티드 환경에 설치되지 않은 {{site.data.keyword.Bluemix_notm}} 서비스에 의존하는 작업 유형은 사용 가능하지 않습니다.	예를 들어, 컨테이너 빌드 및 배치 작업 유형은 {{site.data.keyword.containerlong_notm}}가 없는 환경에서는 사용 가능하지 않습니다.	|
{: caption="표 1: {{site.data.keyword.Bluemix_notm}} 데디케이티드 및 {{site.data.keyword.Bluemix_notm}} 퍼블릭의 도구 체인 간 차이점" caption-side="top"}


## 도구 체인 템플리트
{: #templates}

[도구 체인 작성 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/devops/create){: new_window}에 대한 시작점으로 템플리트를 사용할 수 있습니다. 도구 체인 템플리트에는 개발, 배치 및 운영 태스크를 지원하는 특정 도구 통합 세트가 포함되어 있습니다.

회사의 {{site.data.keyword.Bluemix_notm}} 데디케이티드 환경에 {{site.data.keyword.Bluemix_notm}} 퍼블릭 사이트와 동일한 도구 체인 템플리트가 포함되지 않을 수 있습니다. {{site.data.keyword.Bluemix_notm}} 퍼블릭 및 {{site.data.keyword.Bluemix_notm}} 데디케이티드 모두에서 사용 가능한 도구 체인 템플리트에 {{site.data.keyword.Bluemix_notm}} 데디케이티드의 다른 도구 통합 세트가 포함될 수 있습니다.
{: tip}

일부 도구 체인 템플리트에는 {{site.data.keyword.contdelivery_short}} 서비스의 일부인 도구 통합이 포함되어 있습니다. 해당 서비스의 인스턴스가 아직 리소스 그룹이나 조직에 없는 경우 도구 체인을 작성하기 위해 **작성**을 클릭하면 서비스가 선택된 무료 라이트 플랜으로 자동 추가됩니다. 자세한 정보 및 이용 약관은 [{{site.data.keyword.Bluemix_notm}} 카탈로그 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/catalog/services/continuous-delivery/){:new_window}를 참조하십시오.

"Cloud Foundry에서 마이크로서비스 개발 및 테스트" 도구 체인은 Cloudant 저장소에서 지원하는 주문 API 및 카탈로그로 앱을 배치합니다. 앱 배치의 일부로서 무료 Cloudant 서비스 인스턴스가 작성됩니다. 자세한 정보 및 이용 약관은 [{{site.data.keyword.Bluemix_notm}} 카탈로그 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/catalog/services/cloudant-nosql-db/){:new_window}를 참조하십시오.

사전 정의된 DevOps 도구 체인 템플리트는 실제 시나리오를 해결하는 권장 예제이며 각각 샘플 앱이 포함되어 있습니다.  템플리트에서 도구 체인을 작성하는 경우 Git 저장소를 지정하여 고유 앱을 사용할 수 있습니다.

<table valign="top" padding="2px">
  <caption>표 2. 도구 체인 템플리트</caption>
  <tr>
    <th style="width:25%; text-align:left; vertical-align:top">템플리트 및 사용 가능한 지역</th>
    <th style="width:50%; text-align:left; vertical-align:top">설명 및 사용 가능한 튜토리얼</th>
    <th style="text-align:left; vertical-align:top">포함된 도구</th>
  </tr>
  <tr><td>
  <a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-toolchain" target="_blank">“Cloud Foundry 앱 개발” 도구 체인 <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a> <br><br>

  미국 남부, 독일 및 영국에서 사용 가능합니다.

  </td><td>
이 도구 체인으로 사용자는 Cloud Foundry 앱을 개발하고 배치할 수 있습니다. 기본적으로 이 도구 체인은 샘플 Node.js "Hello world" 앱을 사용하지만, 사용자가 자신의 GitHub 저장소에 대신 링크할 수 있습니다. 이 도구 체인은 지속적 딜리버리, 소스 제어, 문제 추적 및 온라인 편집을 위해 사전 구성되어 있습니다.	<br><br>

  튜토리얼 활용: <a href="https://www.ibm.com/cloud/garage/tutorials/introduce-develop-cloud-foundry-app-toolchain" target="_blank">Introduce Toolchains by using the “Develop a Cloud Foundry app” toolchain <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a> <br><br>
  </td><td><ul><li>
  {{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub 및 Issues
  </li><li>{{site.data.keyword.Bluemix_notm}}
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsecure-kube-toolchain" target="_blank">"Kubernetes 앱 개발" 도구 체인 <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a> <br><br>

  미국 남부, 독일 및 영국에서 사용 가능합니다.

  </td><td>
  이 도구 체인을 사용하여 애플리케이션을 개발하고 {{site.data.keyword.containerlong_notm}}에서 관리하는 Kubernetes 클러스터에 안전하게 배치할 수 있습니다. 기본적으로 도구 체인은 샘플 Node.js "Hello World" 앱을 사용하지만, 대신 고유 GitHub 저장소에 연결할 수 있습니다. 이 도구 체인은 Vulnerability Advisor가 포함된 지속적 딜리버리, 소스 제어, 문제 추적 및 온라인 편집을 위해 사전 구성되었습니다. <br><br>
  튜토리얼 활용: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-toolchain" target="_blank">Use the "Develop a Kubernetes app" toolchain <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a>  
  <br><br>
  </td><td><ul><li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub 및 Issues
  </li><li>{{site.data.keyword.containerlong_notm}}(Kubernetes 클러스터)
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fsimple-helm-toolchain" target="_blank">"Develop a Kubernetes app with Helm" toolchain
   <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a> <br><br>

  미국 남부, 독일 및 영국에서 사용 가능합니다.

  </td><td>
  이 도구 체인을 사용하여 Docker 애플리케이션 및 해당 Helm 차트를 함께 소스 제어로 개발할 수 있으며 빌드하여 자동으로 Kubernetes 클러스터에 배치할 수 있습니다. 도구 체인은 빌드 또는 배치하기 전에 스모크 테스트를 수행하며 컨테이너 레지스트리 및 Kubernetes 클러스터에 대한 개인 컨테이너 레지스트리 및 네임스페이스를 사용하여 개인정보 보호를 보장합니다. 이 도구 체인도 Vulnerability Advisor를 사용하여 안전한 이미지만 배치되도록 합니다. <br><br>
튜토리얼 활용: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-with-helm-toolchain" target="_blank">Use the "Develop a Kubernetes app with Helm" toolchain <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a>	 <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>Git Repos and Issue Tracking
  </li><li>Helm 차트가 포함된 {{site.data.keyword.containerlong_notm}}(Kurbernetes 클러스터)
  </li></ul>
  </td></tr>

  <tr><td>
  <a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdra-toolchain-demo" target="_blank">"Develop and test a Cloud Foundry app" toolchain
   <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a> <br><br>

  미국 남부, 독일 및 영국에서 사용 가능합니다.

  </td><td>
  이 클라우드 네이티브 도구 체인을 사용하면 DevOps Insights를 통해 단순 Cloud Foundry 애플리케이션의 배치를 제공할 수 있습니다. 기본적으로 도구 체인은 샘플 Node.js 날씨 앱을 사용하거나 사용자가 고유 GitHub 저장소에 연결할 수 있습니다. 도구 체인은 Mocha를 사용하여 단위 테스트를 실행하고 Istanbul을 사용하여 코드 적용 범위를 검사합니다.<br><br>
튜토리얼 활용: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-cloud-foundry-app-toolchain" target="_blank">Use the "Develop and test a Cloud Foundry app" toolchain  <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a>  <br><br>
  </td><td><ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>Git Repos and Issue Tracking
  </li><li>{{site.data.keyword.DRA_full}}(미국 남부 전용)
  </li></ul>
  </td></tr>


  <tr><td>
  <a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fmicroservices-toolchain-hosted" target="_blank">
  "Cloud Foundry에서 마이크로서비스 개발 및 테스트" 도구 체인 <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a> <br><br>

  미국 남부, 독일 및 영국에서 사용 가능합니다.

  </td><td>
이 클라우드 네이티브 도구 체인으로 사용자는 3개의 마이크로서비스(카탈로그 API, 주문 API, 그리고 두 API를 모두 호출하는 UI)로 구성된 온라인 저장소를 작성하는 샘플을 사용할 수 있습니다. 이 도구 체인은 지속적 딜리버리, 소스 제어, 기능 테스트, 문제 추적, 온라인 편집 및 경보 알림을 위해 사전 구성되어 있습니다. <br><br>
  튜토리얼 활용: <a href="https://www.ibm.com/cloud/garage/tutorials/use-develop-test-microservices-on-cloud-foundry-toolchain" target="_blank">Use the "Develop and test microservices on Cloud Foundry" toolchain <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a><br><br>
  </td><td>
  <ul>
  <li>{{site.data.keyword.deliverypipeline}}
  </li><li>Eclipse Orion {{site.data.keyword.webide}}
  </li><li>GitHub 및 Issues
  </li><li>{{site.data.keyword.Bluemix_notm}}
  </li><li>{{site.data.keyword.DRA_full}}(미국 남부 전용)
  </li><li>PagerDuty
  </li><li>Sauce Labs
  </li><li>Slack
  </li></ul>
 </td>
</tr>

  <tr>
  <td><a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fcloud-native-toolchain-tutorial" targe="_blank">
"Cloud Foundry를 사용하는 Garage Method 튜토리얼" 도구 체인 <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a> <br><br>

  미국 남부, 독일 및 영국에서 사용 가능합니다.

</td><td>
이 도구 체인은 Garage Method에서 제공하는 DevOps 사례를 보여줍니다. 이 도구 체인은 지속적 딜리버리, 소스 제어, 테스트 자동화, 그리고 자동화된 모니터링 및 운영을 위해 사전 구성되어 있습니다. 이는 추가로 확장이 가능한 Node.js Express 4로 작성된 샘플 앱과 함께 제공됩니다. <br><br>강좌 활용: <a href="https://www.ibm.com/cloud/garage/content/course/gm_advocate" target="_blank">Become a Garage Method advocate <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a>.
</td><td>
<ul>
<li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion {{site.data.keyword.webide}}
</li><li>GitHub 및 Issues
</li><li>Google Analytics
</li><li>{{site.data.keyword.Bluemix_notm}}
</li><li>New Relic
</li><li>PagerDuty
</li><li>Sauce Labs
</li><li>Slack
</li></ul>
</td></tr>

<tr><td>
<a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdevopsinsights-toolchain" target="_blank">"GitHub 및 Jenkins를 사용하는 Deployment Risk Analytics" 도구 체인 <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a> <br><br>

  미국 남부에서 사용 가능합니다.

</td><td>이 도구 체인으로 사용자는 지속적 통합 및 딜리버리를 위한 Jenkins 프로세스에 대한 통찰을 얻을 수 있습니다. Jenkins에서 작업을 실행할 때 {{site.data.keyword.DRA_short}}에 데이터를 전송하도록 Jenkins 서버를 구성할 수 있습니다. 또한 정책에 따라 배치를 차단할 수 있도록 품질 게이트를 구현할 수도 있습니다. 사용자는 {{site.data.keyword.DRA_short}}의 배치 위험성 대시보드에서 결과를 볼 수 있습니다. Jenkins에서 사용하는 소스 저장소를 표시하도록 GitHub 저장소를 구성하는 경우에는 변경 추적성을 사용할 수 있습니다.  
<br><br>
튜토리얼 활용: <a href="https://www.ibm.com/cloud/garage/tutorials/ensure-quality-deployment-risk-analytics-with-github-and-jenkins-toolchain" target="_blank">Ensure quality deployments by using the "Deployment Risk Analytics with GitHub and Jenkins" toolchain  <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a>  <br><br>
</td><td><ul><li>
GitHub 및 Issues
</li><li>Jenkins
</li><li>{{site.data.keyword.DRA_full}}
</li><li>Slack
</li></ul>
</td></tr>

<tr><td>
<a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fdevteaminsights-toolchain" target="_blank">"GitHub 및 JIRA를 사용하는 Developer Insights 및 Team Dynamics" 도구 체인 <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a> <br><br>

  미국 남부에서 사용 가능합니다.

</td><td>
이 도구 체인으로 사용자는 프로젝트의 개발 위험성을 탐색하고 소셜 코딩 분석을 사용하여 개발자 간의 상호작용 패턴을 파악할 수 있습니다. 사용자는 GitHub Issues, JIRA Issues 또는 두 가지 모두로 GitHub 소스 코드를 분석할 수 있습니다. Developer Insights를 사용하면 오류 발생 가능성이 높은 파일을 식별하고 프로젝트가 DevOps 사례를 준수하는 방법을 파악할 수 있습니다. Team Dynamics의 소셜 코딩 분석이 팀 구성원 간의 상호작용 레벨을 식별하므로, 팀은 비생산적인 사례를 수정할 수 있습니다.<br><br>
튜토리얼 활용: <a href="https://www.ibm.com/cloud/garage/tutorials/gain-insights-developer-insights-and-team-dynamics-with-github-and-jira-toolchain" target="_blank">Gain insights by using the "Developer Insights and Team Dynamics with GitHub and JIRA" toolchain <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a> <br><br>
</td><td><ul><li>
GitHub 및 Issues
</li><li>{{site.data.keyword.DRA_full}}
</li><li>JIRA
</li><li>Slack
</li></ul>
</td></tr>

<tr><td>
<a href="https://console.bluemix.net/devops/setup/deploy?repository=https%3A%2F%2Fgithub.com%2Fopen-toolchain%2Fempty-toolchain" target="_blank">사용자 자체 도구 체인 빌드 <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a> <br><br>

  미국 남부, 독일 및 영국에서 사용 가능합니다.

</td><td>
이 도구 체인에는 사전 구성된 도구가 없습니다. 도구 체인에 이미 익숙한 경우 사용자 자체 도구 체인을 설정할 수 있습니다. <br><br>
튜토리얼 활용: <a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">Create a custom toolchain <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a>
</td><td> &nbsp;&nbsp; 없음
</td></tr>

<tr><td>Continuous Delivery 도구 체인 <br><br>

 미국 남부, 독일 및 영국에서 사용 가능합니다.

</td><td>
앱에 대해 지속적 딜리버리를 사용하는 경우 이 도구 체인이 사용됩니다. <br><br>
튜토리얼 활용:

<ul><li><a href="https://www.ibm.com/cloud/garage/tutorials/add-a-toolchain-to-an-app" target="_blank">Add a toolchain to an app <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a></li>
<li><a href="https://www.ibm.com/cloud/garage/tutorials/create-a-custom-toolchain" target="_blank">Create a custom toolchain <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a></li>
<li><a href="/docs/tutorials/multi-region-webapp.html#deploy-a-secure-web-application-across-multiple-regions" target="_blank">여러 지역에서 보안 웹 애플리케이션 배치</a></li>
</ul></td>
<td><ul><li>{{site.data.keyword.deliverypipeline}}
</li><li>Eclipse Orion {{site.data.keyword.webide}}
</li><li>
GitHub 및 Issues
</li>
<li>{{site.data.keyword.Bluemix_notm}}</li></ul>
</td></tr>

<tr><td>사용자 정의 도구 체인 템플리트 <br><br>

 미국 남부, 독일 및 영국에서 사용 가능합니다.

</td><td>
<br><br>
다른 사용자가 사용할 수 있는 사용자 정의 도구 체인 템플리트를 작성할 수 있습니다. <br><br>

다음 문서를 참조하십시오.
<a href="https://github.com/open-toolchain/sdk/wiki" target="_blank">Creating custom toolchain templates <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a>
 <br><br>
튜토리얼 활용:
<a href="https://www.ibm.com/cloud/garage/tutorials/create-a-template-for-a-custom-toolchain" target="_blank">Create a template for a custom toolchain <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘"></a></td>
<td>없음
</td></tr>

</table>
