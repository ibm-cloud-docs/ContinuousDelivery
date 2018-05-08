---

copyright:
  years: 2015, 2018
lastupdated: "2018-3-26"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}


# {{site.data.keyword.Bluemix_notm}}에 배치 단추 작성 {: #deploy-button}

{{site.data.keyword.Bluemix_notm}}에 배치 단추는 도구 체인을 사용하여 다른 사람들이 코드를 실험하고 IBM {{site.data.keyword.Bluemix_notm}}에 배치할 수 있도록 공용 Git 소스 앱을 공유하는 효율적인 방법입니다. 이 단추를 사용하려면 최소한의 구성이 필요하며 마크업을 지원하는 모든 위치에 이 단추를 삽입할 수 있습니다. 단추를 클릭하는 모든 사용자는 원래의 앱이 영향을 받지 않도록 새 Git 저장소에 코드의 복제된 사본을 작성합니다.
{: shortdesc}

사용자가 단추를 클릭하면 다음과 같은 조치가 수행됩니다.

1. 사용자가 활성 {{site.data.keyword.Bluemix_notm}} 계정을 갖고 있지 않은 경우 계정을 작성해야 합니다. 평가판 계정 또는 실제 계정을 작성할 수 있습니다.

2. 사용자는 {{site.data.keyword.deliverypipeline}} 아이콘을 클릭하여 지역, 조직, 영역 및 앱 이름을 선택할 수 있습니다. 제안된 앱 이름은 원래의 Git 저장소의 이름 및 시간으로 생성된 도구 체인 이름과 동일합니다. 도구 체인 이름도 편집할 수 있습니다.

3. Git 저장소의 새 개인용 복제본, 코드 변경사항 빌드 및 배치를 위한 파이프라인, Cloud에서 코드 편집을 위한 Eclipse Orion {{site.data.keyword.webide}} 및 문제 트래커를 포함한 도구 체인이 작성됩니다.

  **팁**: `.bluemix` 디렉토리에 `toolchain.yml` 파일이 포함된 경우 파일은 도구 체인에 대한 도구 통합을 지정하도록 사용됩니다. `toolchain.yml` 파일에 대한 자세한 정보는 [사용자 정의 도구 체인 작성](/docs/services/ContinuousDelivery/toolchains_custom.html#toolchains_custom){: new_window}을 참조하십시오.

4. 앱에 빌드 파일이 필요한 경우 빌드 파일이 자동으로 발견되어 앱을 빌드합니다.

5. 파이프라인이 빌드 및 배치 프로세스에 대해 구성된 경우 앱을 배치하는 데 `pipeline.yml` 파일이 사용됩니다.

6. 앱에 컨테이너가 필요한 경우 IBM Containers 서비스를 정의하는 `pipeline.yml` 파일 및 이미지를 정의하는 Dockerfile은 {{site.data.keyword.Bluemix_notm}} 컨테이너의 앱을 배치하는 데 사용됩니다.

7. 앱은 사용자가 선택한 {{site.data.keyword.Bluemix_notm}} 조직에 배치됩니다.

## 단추 예 {: #button-examples}

공용 {{site.data.keyword.gitrepos}} 저장소에 대한 앱 단추 예를 참조하십시오.

[![Bluemix에 배치](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://git.ng.bluemix.net/idsorg/sample-java-cloudant){:new_window}

공용 GitHub 저장소에 대한 앱 단추 예를 참조하십시오.

[![Bluemix에 배치](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/open-toolchain/starfighter){:new_window}

## 단추 작성 {: #create-button}

{{site.data.keyword.Bluemix_notm}}에 배치 단추를 작성하려면 다음 스니펫 템플리트 중 하나를 복사하고 수정하십시오. URL에 Git 저장소 및 분기를 지정하십시오.

### HTML에서 단추 작성

HTML에서 단추를 작성하려면 이 스니펫을 복사하여 공용 Git 저장소 URL 및 분기를 삽입하십시오.

```HTML
<a href="https://bluemix.net/deploy?repository=<git_repository_URL>&branch=<git_branch>"><img src="https://bluemix.net/deploy/button.png" alt="Deploy to Bluemix"></a>
```
{: codeblock}

스니펫의 저장소 URL에 `branch` 매개변수를 포함시키지 않은 경우 Bluemix에 배치 단추가 기본적으로 저장소의 마스터 분기로 설정됩니다.

### 마크다운에서 단추 작성

마크다운에서 단추를 작성하려면 이 스니펫을 복사하여 공용 Git 저장소 URL 및 분기를 삽입하십시오.

```Markdown
[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=<git_repository_URL>&branch=<git_branch>)
```
{: codeblock}

스니펫의 저장소 URL에 `branch` 매개변수를 포함시키지 않은 경우 Bluemix에 배치 단추가 기본적으로 저장소의 마스터 분기로 설정됩니다.

### 단추 스니펫 사용 {: #button-snippet}

Bluemix에 배치 단추 스니펫을 작성한 후 블로그, 기사, 위키, readme 파일 또는 앱을 홍보할 모든 위치에 삽입할 수 있습니다.

{{site.data.keyword.Bluemix_notm}}에 배치 단추에 대한 스니펫을 사용자 정의하는 경우 두 템플리트 모두에서 외부 단추 이미지의 기본 경로를 PNG 형식 및 영어로 사용할 것을 고려하십시오.

* 단추의 이미지를 PNG 대신 SVG로 사용하려는 경우 스니펫에 사용되는 단추 이미지의 경로를 `https://bluemix.net/deploy/button.svg`로 변경하십시오.

* 단추의 이미지를 사용하려는 경우 스니펫에 사용되는 단추 이미지의 경로를 `https://bluemix.net/deploy/button_x2.png`로 변경하십시오. 이 이미지는 기본 이미지 크기의 두 배입니다.

* 이미지를 로컬로 저장하려는 경우 이미지를 다운로드하여 Git 저장소에 저장할 수 있습니다. 이미지의 상대 위치를 사용하도록 경로를 조정하십시오.

* 단추의 변환된 버전을 사용하려는 경우 원격으로 참조하거나 [ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](ftp://public.dhe.ibm.com/cloud/bluemix/deploy_button){:new_window}에서 다운로드할 수 있습니다.

## 저장소 고려사항 {: #button-repo}

{{site.data.keyword.Bluemix_notm}}에 배치 단추에 사용하는 저장소에 대한 다음 고려사항을 검토하십시오.


## 빌드 파일 요구사항
{: build_file}

앱을 배치하기 전에 빌드해야 하는 경우 저장소에 빌드 파일을 포함해야 합니다. 빌드 스크립트 파일이 저장소의 루트 디렉토리에서 발견되면 코드의 자동화된 빌드가 배치 전에 트리거됩니다.

지원되는 빌더는 다음과 같습니다.

* [Ant ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘"):](http://ant.apache.org/manual/using.html){:new_window} `build.xml`. `./output/` 폴더에 출력을 빌드합니다.
* [Gradle ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘"):](http://docs.cloudfoundry.org/buildpacks/java/build-tool-int.html#gradle){:new_window} `/build.gradle`. `.` 폴더에 출력을 빌드합니다.
* [Grunt ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘"):](http://gruntjs.com/getting-started#the-gruntfile){:new_window} `/Gruntfile.js`. `.` 폴더에 출력을 빌드합니다.
* [Maven ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘"):](http://docs.cloudfoundry.org/buildpacks/java/build-tool-int.html#maven){:new_window} `/pom.xml`. `./target/` 폴더에 출력을 빌드합니다.

### 파이프라인 파일 요구사항
{: pipeline_file}

`.bluemix` 디렉토리에 도구 체인의 파이프라인을 구성하려면 `pipeline.yml` 파일을 포함하십시오. 해당 디렉토리에 있는 각 `pipeline.yml` 파일의 경우 도구 체인이 인스턴스화될 때 파이프라인이 작성됩니다.

`pipeline.yml` 파일이 `.bluemix` 디렉토리에 없는 경우 {{site.data.keyword.Bluemix_notm}}에 배치 단추를 누르면 빌드 단계와 Cloud Foundry에 배치하는 배치 단계의 두 가지 단계로 기본 파이프라인을 작성합니다. 

파이프라인 파일을 작성하려면 [사용자 정의 도구 체인 파이프라인 지시사항](toolchains_custom.html#toolchains_custom_pipeline_yml)에 있는 예제 파일을 참조하십시오. 웹 인터페이스의 파이프라인을 정의할 때 단계 및 작업을 작성하고 입력 및 환경 변수를 설정하며 스크립트를 추가하여 텍스트의 파이프라인을 정의합니다. 또한 [이 데모 프로젝트](https://github.com/open-toolchain/toolchain-demo/tree/master/.bluemix)에서 좀 더 복잡한 다수의 파이프라인을 볼 수 있습니다.

### 컨테이너 Dockerfile 요구사항
{: container_dockerfile}

IBM Containers를 사용하여 컨테이너에 앱을 배치하려면 저장소의 루트 디렉토리에 Dockerfile을 포함하고 `.bluemix` 디렉토리에 `pipeline.yml` 파일을 포함해야 합니다.

Dockerfile은 앱에 대한 빌드 스크립트 종류로 작동합니다. Dockerfile이 저장소에서 발견되면 앱이 컨테이너에 배치되기 전에 이미지에 자동으로 빌드됩니다. 앱이 이미지로 빌드되기 전에 앱이 자체적으로 빌드되어야 하는 경우 앱 및 Dockerfile에 대한 빌드 스크립트를 포함해야 합니다.

Dockerfile 작성에 대해 자세히 알아보려면 [Docker 문서![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://docs.docker.com/reference/builder/){:new_window}를 참조하십시오.  Kubernetes에 배치하기 위해 도구 체인 템플리트를 사용하여 단계별 지시사항을 따르려면 [튜토리얼: "Kubernetes 앱 개발" 도구 체인 사용 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-toolchain?task=0){:new_window} 또는 [튜토리얼: "Helm으로 Kubernetes 앱 개발" 도구 체인 사용 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/garage/tutorials/use-develop-kubernetes-app-with-helm-toolchain?task=0){:new_window}을 참조하십시오.  
   Kubernetes 클러스터에 Cloud Foundry 앱 포팅에 대해 자세히 살펴보려면 [튜토리얼: Cloud Foundry 앱을 Kubernetes에 포팅 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/cloud/garage/tutorials/port-an-app-from-cf-to-kubernetes-in-a-toolchain?task=0){:new_window}을 참조하십시오.  

수동으로 컨테이너 전용 `pipeline.yml` 작성

특히 컨테이너용인 `pipeline.yml`을 수동으로 작성하려면 [GitHub의 예![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/Puquios/){:new_window}를 참조하십시오.

## Manifest 파일 요구사항(Cloud Foundry에 배치된 앱의 경우)
{: #manifest_files}

`manifest.yml` 파일이 사용자의 저장소에 있지 않아도 됩니다. 그러나 앱에서 다른 서비스를 실행해야 하는 경우 해당 서비스를 선언하는 Manifest 파일을 제공해야 합니다.

Manifest 파일에 대해 자세히 알아보려면 [애플리케이션 Manifest](/docs/cfapps/depapps.html#appmanifest)를 참조하십시오.
