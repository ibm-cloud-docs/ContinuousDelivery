---

copyright:
  years: 2023, 2024
lastupdated: "2024-7-11"

keywords: IBM Cloud Public, firewall configuration, network zones

subcollection: ContinuousDelivery

---

{{site.data.keyword.attribute-definition-list}}


# Subnet ranges for {{site.data.keyword.deliverypipeline}} 
{: #pipeline-subnet-ranges}
{: support}

If your firewall configuration prevents the {{site.data.keyword.deliverypipeline}} from communicating with environments that are behind a firewall, you must update the configuration, including subnet ranges, to access resources that are behind the firewall.
{: shortdesc}

Use the following subnet ranges for your specific region.

```text
jp-tok
10.129.50.128/27
10.192.14.0/27
10.192.72.0/26
10.193.16.192/27
10.193.40.128/26
10.223.197.15/32
10.223.210.248/32
10.223.221.179/32
128.168.108.0/26
128.168.130.29
128.168.68.192/27
161.202.235.192/27
162.133.142.43
165.192.107.64/26
165.192.130.197
165.192.70.32/27
169.56.10.128/26
====
jp-osa
10.10.15.128/26
10.12.18.41/32
10.12.35.119/32
10.12.41.23/32
10.8.29.128/26
10.9.10.128/26
163.68.73.192/27
163.68.73.80/28
163.68.85.144
163.69.65.16/28
163.69.67.224/27
163.69.88.234
163.73.67.240/28
163.73.68.0/27
163.73.84.30
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
10.177.11.128/26
10.185.130.0/26
10.22.213.99/32
10.22.26.156/32
10.37.91.0/26
150.240.160.67
150.240.163.132
150.240.70.54
169.47.72.160/27
169.47.92.174
169.48.221.240/28
169.61.249.80/28
52.118.100.155
52.118.103.76
52.118.135.32/27
52.118.208.80
52.118.249.97
52.118.79.48
67.228.108.96/27
67.228.197.224/28
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
10.196.17.128/26
10.249.101.24/32
10.249.106.155/32
10.45.57.192/26
10.72.31.64/26
141.125.108.183
141.125.70.224/28
141.125.74.192/27
158.175.104.64/26
158.175.180.112
158.176.189.117
158.176.72.192/26
161.156.200.18
====
eu-de
10.123.37.224/27
10.123.89.192/26
10.135.250.0/26
10.22.106.66/32
10.22.111.14/32
10.223.59.132/32
10.75.196.192/26
10.75.51.0/27
10.85.201.160/27
149.81.122.0/26
149.81.15.59
149.81.216.45
149.81.236.141
149.81.73.160/27
158.176.15.220
158.176.6.60
158.177.14.29
159.122.96.192/27
161.156.157.192/26
161.156.77.128/27
169.50.53.0/26
====
eu-es
10.118.139.0/26
10.118.4.0/26
10.118.67.128/26
10.22.177.66/32
10.22.193.134/32
10.22.210.159/32
13.120.68.112/28
13.120.69.96/27
13.120.91.162
13.121.64.64/27
13.121.68.176/28
13.121.91.15
13.122.67.208/28
13.122.70.96/27
13.122.88.31
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
10.14.14.0/26
10.15.17.0/26
10.150.99.64/26
13.116.90.7
163.107.70.96/27
163.107.90.148
163.109.70.160/28
163.109.70.192/27
163.109.81.154
169.57.162.64/27
169.57.175.144/28
```



{: screen}

## Using the Toolchain service reference
{: #toolchain-service-reference}

If you are using context-based restrictions to control access to {{site.data.keyword.cloud_notm}} services, you can use the Toolchain service reference to allow {{site.data.keyword.deliverypipeline}} tasks to access those {{site.data.keyword.cloud_notm}} services without having to specify the IP address ranges listed in the previous section. The Toolchain service network zone IP ranges are internally maintained and updated, allowing you to define context-based restrictions network zones and rules without having to know the origin IP addresses of the Toolchain service. See [What are context-based restrictions?](/docs/account?topic=account-context-restrictions-whatis) for more information about using network zones.
