---



copyright:
  years: 2015，2019
lastupdated: "2019-06-19"

keywords: IBM Cloud Live Synch, Use IBM Cloud Live Sync

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

# {{site.data.keyword.Bluemix_notm}} Live Sync
{: #live-sync}

Node.js 애플리케이션을 빌드 중인 경우 {{site.data.keyword.Bluemix}} Live Sync를 사용하여 수동 재배치 없이 {{site.data.keyword.Bluemix_notm}}에서 애플리케이션 인스턴스를 신속하게 업데이트하고 개발할 수 있습니다.   
{: shortdesc}

변경할 경우 실행 중인 {{site.data.keyword.Bluemix_notm}} 애플리케이션에서 변경사항을 즉시 확인할 수 있습니다. {{site.data.keyword.Bluemix_notm}} Live Sync는
<!--from both the command line and -->
Eclipse Orion{{site.data.keyword.webide}}({{site.data.keyword.webide}})에서 작동합니다. 

##Live Edit
{: #live-edit}

{{site.data.keyword.Bluemix_notm}}에서 실행되는 Node.js 애플리케이션을 편집하여 브라우저에서 바로 테스트할 수 있습니다. {{site.data.keyword.webide}}의 변경사항은 애플리케이션의 파일 시스템으로 즉시 전파됩니다.

{{site.data.keyword.Bluemix_notm}}에서 실행되는 Node.js 애플리케이션을 빌드 중인 경우 {{site.data.keyword.Bluemix_notm}} Live Sync의 Live Edit 기능으로 애플리케이션 인스턴스를 신속하게 업데이트할 수 있습니다. Live Edit는 {{site.data.keyword.webide}}에서만 사용할 수 있습니다. Live Edit를 사용하여 재배치하지 않고 데스크탑에서와 같이 개발할 수 있습니다.

Live Edit는 Node.js 애플리케이션에서만 지원됩니다.
{: important}

{{site.data.keyword.webide}}의 실행 표시줄에서 **Live Edit**를 클릭하십시오.

![Live Edit가 포함된 실행 표시줄의 이미지](images/cloud-live-sync-light.png)

Live Edit를 사용하여 {{site.data.keyword.Bluemix_notm}}에서 실행되는 Node.js 애플리케이션에 대한 변경사항을 신속하게 미리보십시오. Live Edit를 켠 상태에서 코드를 업데이트하는 경우 웹 애플리케이션의 브라우저 창을 새로 고치면 변경 후 몇 초 이내에 변경사항이 적용되어 표시됩니다.

{{site.data.keyword.Bluemix_notm}} Live Sync의 Live Edit 기능 사용에 대한 튜토리얼은 [{{site.data.keyword.Bluemix_notm}} Live Sync를 사용하여 앱 개발, 디버그 및 배치](https://www.ibm.com/cloud/garage/tutorials/use-live-sync-to-develop-debug-and-deploy-your-app){: external}를 참조하십시오.

{{site.data.keyword.webide}}에서 파일을 변경하면 이 파일이 {{site.data.keyword.Bluemix_notm}}의 애플리케이션 인스턴스에 자동으로 재배치됩니다. 노드 애플리케이션을 다시 시작해야 하는 경우 실행 표시줄에 있는 **다시 시작** 단추를 클릭하십시오.

{{site.data.keyword.Bluemix_notm}} Live Sync의 Live Edit 기능을 사용할 때, 보다 일관된 경험을 위해서 256MB의 추가 메모리가 필요함에 따라 추가됩니다.
{: tip}
