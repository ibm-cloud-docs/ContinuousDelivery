---

copyright:
  years: 2023, 2026
lastupdated: "2026-05-07"

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
10.51.174.190/32
10.51.176.15/32
10.51.181.1/32
159.23.93.132/32
130.198.13.123/32
135.90.139.171/32
====
br-sao
10.51.184.90/32
10.12.70.244/32
10.12.86.46/32
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
10.223.158.228/32
10.223.165.19/32
10.223.179.208/32
163.66.87.95/32
163.74.84.73/32
163.75.89.124/32
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
10.249.139.153/32
10.22.48.211/32
10.12.114.13/32
150.239.108.99/32
169.59.164.22/32
150.239.214.217/32
====
us-south
10.249.193.90/32
10.16.247.19/32
10.119.52.219/32
150.240.160.94/32
52.118.206.20/32
67.18.92.94/32
```
{: screen}
