---

copyright:
  years: 2023, 2026
lastupdated: "2026-03-30"

keywords: IBM Cloud Public, firewall configuration

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}


# Subnet ranges for Git 
{: #git-subnet-ranges}
{: support}

{{site.data.keyword.contdelivery_short}} will be discontinued in the following regions on 10 April 2026: **eu-es** and **jp-osa**.
This discontinuation also applies to any features provided within the service, including Code Risk Analyzer and {{site.data.keyword.DRA_short}}.
[Learn more](/docs/ContinuousDelivery?topic=ContinuousDelivery-faq_region_feature_consolidation)
{: important}

{{site.data.keyword.contdelivery_short}} will be discontinued in the following regions on 12 February 2027: **au-syd**, **ca-mon**, **ca-tor**, **us-east**. Code Risk Analyzer and {{site.data.keyword.DRA_short}} will also be deprecated in all regions on that date. However, if a region has no active usage of these features, the features in that region may be discontinued earlier and stop accepting new instances. [Learn more](/docs/ContinuousDelivery?topic=ContinuousDelivery-faq_region_feature_consolidation)
{: important}

You can update your firewall configuration to allow webhook messages from {{site.data.keyword.gitrepos}} to reach endpoints that are behind the firewall.
{: shortdesc}

To allow Git webhook messages, open traffic to the following subnet ranges for your specific region.

Montreal (ca-mon) is a limited-availability region and not generally available.
{: important}

```text
au-syd
10.139.55.128/26
10.195.7.128/26
10.63.14.64/26
130.198.80.128/28
130.198.85.32/27
135.90.66.176/28
135.90.66.96/27
168.1.36.32/27
168.1.59.208/28
====
br-sao
10.14.14.0/26
10.15.17.0/26
10.150.99.64/26
10.51.184.90/32
10.12.70.244/32
10.12.86.46/32
163.107.68.48/28
163.107.70.96/27
163.109.70.160/28
163.109.70.192/27
169.57.162.64/27
169.57.175.144/28
13.116.88.218/32
163.107.80.212/32
163.109.87.137/32
====
ca-mon
10.46.73.151/32
10.46.77.151/32
10.46.81.151/32
64.5.42.134/32
64.5.44.189/32
64.5.50.234/32
====
ca-tor
10.11.30.0/26
10.114.28.192/26
10.243.29.0/26
158.85.67.192/27
163.74.68.224/28
163.74.69.64/27
163.75.66.144/28
163.75.68.0/27
169.53.183.48/28
====
eu-de
10.16.205.83/32
10.22.113.244/32
10.22.116.37/32
149.81.6.137/32
161.156.167.49/32
149.81.243.202/32
====
eu-gb
10.196.17.128/26
10.45.57.192/26
10.72.31.64/26
141.125.70.224/28
141.125.74.192/27
158.175.104.64/26
158.176.72.192/26
10.16.49.234/32
10.16.58.12/32
10.223.23.122/32
158.175.190.216/32
141.125.158.101/32
158.176.171.70/32
====
jp-osa
10.10.15.128/26
10.8.29.128/26
10.9.10.128/26
163.68.73.192/27
163.68.73.80/28
163.69.65.16/28
163.69.67.224/27
163.73.67.240/28
163.73.68.0/27
====
jp-tok
10.223.198.234/32
10.223.203.247/32
10.223.217.62/32
128.168.134.141/32
162.133.129.192/32
165.192.138.80/32
====
us-east
10.183.12.0/26
10.188.28.192/26
10.190.252.64/26
169.47.140.64/26
169.47.160.64/26
169.60.92.192/26
169.62.30.64/26
====
us-south
10.177.103.0/26
10.184.211.0/25
10.184.63.64/26
10.185.27.0/26
10.186.76.128/25
10.187.66.0/26
10.221.70.0/25
169.48.211.176/28
169.60.247.192/26
169.61.132.64/26
169.61.41.64/26
10.249.193.90/32
10.16.247.19/32
10.119.52.219/32
150.240.160.94/32
52.118.206.20/32
67.18.92.94/32
```
{: screen}
