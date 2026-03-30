---

copyright:
  years: 2023, 2026
lastupdated: "2026-03-30"

keywords: IBM Cloud Public, firewall configuration, network zones

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}


# Subnet ranges for {{site.data.keyword.deliverypipeline}} 
{: #pipeline-subnet-ranges}
{: support}

{{site.data.keyword.contdelivery_short}} will be discontinued in the following regions on 10 April 2026: **eu-es** and **jp-osa**.
This discontinuation also applies to any features provided within the service, including Code Risk Analyzer and {{site.data.keyword.DRA_short}}.
[Learn more](/docs/ContinuousDelivery?topic=ContinuousDelivery-faq_region_feature_consolidation)
{: important}

{{site.data.keyword.contdelivery_short}} will be discontinued in the following regions on 12 February 2027: **au-syd**, **ca-mon**, **ca-tor**, **us-east**. Code Risk Analyzer and {{site.data.keyword.DRA_short}} will also be deprecated in all regions on that date. However, if a region has no active usage of these features, the features in that region may be discontinued earlier and stop accepting new instances. [Learn more](/docs/ContinuousDelivery?topic=ContinuousDelivery-faq_region_feature_consolidation)
{: important}

If your firewall configuration prevents the {{site.data.keyword.deliverypipeline}} from communicating with environments that are behind a firewall, you must update the configuration, including subnet ranges, to access resources that are behind the firewall.
{: shortdesc}

Use the following subnet ranges for your specific region.

Montreal (ca-mon) is a limited-availability region and not generally available.
{: important}

```text
jp-tok
10.223.197.15/32
10.223.210.248/32
10.223.221.179/32
128.168.130.29
162.133.142.43
165.192.130.197
====
au-syd
10.12.7.197/32
10.139.55.128/26
10.195.7.128/26
10.223.239.74/32
10.223.247.163/32
10.63.14.64/26
130.198.22.227
130.198.80.128/28
130.198.85.32/27
135.90.132.97
135.90.66.176/28
135.90.66.96/27
159.23.98.163
168.1.36.32/27
168.1.59.208/28
====
us-south
10.16.253.160/32
10.22.213.99/32
10.22.26.156/32
150.240.160.67
150.240.163.132
150.240.70.54
169.47.92.174
52.118.100.155
52.118.103.76
52.118.208.80
52.118.249.97
52.118.79.48
====
us-east
10.12.102.198/32
10.12.112.28/32
10.148.53.128/26
10.188.56.192/26
10.190.205.192/26
10.22.50.70/32
150.239.84.167
150.239.85.11
169.55.102.192/28
169.55.108.32/27
169.59.191.231
169.62.28.32/28
169.62.37.128/27
169.63.139.64/27
169.63.187.212
52.117.123.180
52.117.124.168
====
eu-gb
10.16.70.223/32
10.249.101.24/32
10.249.106.155/32
141.125.108.183
158.175.180.112
158.176.189.117
161.156.200.18
====
eu-de
10.22.106.66/32
10.22.111.14/32
10.223.59.132/32
149.81.15.59
149.81.216.45
149.81.236.141
158.176.15.220
158.176.6.60
158.177.14.29
====
ca-tor
10.11.30.0/26
10.114.28.192/26
10.223.149.98/32
10.223.170.38/32
10.223.173.146/32
10.243.29.0/26
158.85.67.192/27
163.66.92.164
163.74.68.224/28
163.74.69.64/27
163.74.89.63
163.75.66.144/28
163.75.68.0/27
163.75.89.141
169.53.183.48/28
====
br-sao
10.12.183.32/32
10.12.69.195/32
10.12.90.104/32
13.116.90.7
163.107.90.148
163.109.81.154
====
ca-mon
10.46.75.50/32
10.46.79.50/32
10.46.83.50/32
64.5.41.106
64.5.44.244
64.5.51.59
10.12.102.198/32
10.12.112.28/32
10.148.53.128/26
10.188.56.192/26
10.190.205.192/26
10.22.50.70/32
150.239.84.167
150.239.85.11
169.55.102.192/28
169.55.108.32/27
169.59.191.231
169.62.28.32/28
169.62.37.128/27
169.63.139.64/27
169.63.187.212
52.117.123.180
52.117.124.168
```



{: screen}

## Using the Toolchain service reference
{: #toolchain-service-reference}

If you are using context-based restrictions to control access to {{site.data.keyword.cloud_notm}} services, you can use the Toolchain service reference to allow {{site.data.keyword.deliverypipeline}} tasks to access those {{site.data.keyword.cloud_notm}} services without having to specify the IP address ranges listed in the previous section. The Toolchain service network zone IP ranges are internally maintained and updated, allowing you to define context-based restrictions network zones and rules without having to know the origin IP addresses of the Toolchain service. See [What are context-based restrictions?](/docs/account?topic=account-context-restrictions-whatis) for more information about using network zones.
