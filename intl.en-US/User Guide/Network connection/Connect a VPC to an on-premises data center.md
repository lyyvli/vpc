# Connect a VPC to an on-premises data center {#concept_lgm_hhl_wfb .concept}

You can connect an on-premises data center to a VPC by using VPN Gateway, a physical connection of Express Connect, or Smart Access Gateway to build a hybrid cloud.

## Overview {#section_mw2_mhl_wfb .section}

You can establish intranet communication between a local data center and Alibaba Cloud to build a hybrid cloud. Then you can seamlessly expand your local IT infrastructure to Alibaba Cloud to cope with service fluctuation and improve application stability by right of the mass computing, storage, network, and CDN resources of Alibaba Cloud.

You can use VPN Gateway, a physical connection of Express Connect and Smart Access Gateway to connect a local data center to a VPC. In addition, you can interconnect global networks by using CEN.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/64763/155425483738213_en-US.png)

## Solutions {#section_n25_qq4_4gb .section}

|Solution|Description|
|:-------|:----------|
|VPN Gateway| You can use IPsec-VPN to connect a local data center to a VPC. VPN Gateway contains two different gateway instances which form active/standby hot backup. The traffic is automatically distributed to the standby node when the active node fails.

 The VPN Gateway is based on Internet communication, so its network latency and availability are decided by the Internet. If you do not have a particularly high demand for network latency, we recommend that you use VPN Gateway.

 For more information, see [Create a site-to-site connection through IPsec-VPN](../../../../../reseller.en-US/IPsec-VPN Quick Start/Create a site-to-site connection through IPsec-VPN.md#).

 |
|Physical connection| Physical connection features good network quality and large bandwidth. Therefore, if your priority is good network quality, we recommend that you select physical connection.

 For more information, see [Connect a local data center to a VPC through a physical connection](../../../../../reseller.en-US/Getting Started (New Console)/Connect an on-premises IDC to a VPC through a physical connection.md#).

 |
|Redundant physical connections| You can use redundant physical connections to connect your on-premises data center to a VPC. Redundant physical connections provide high-quality and high-reliability intranet communication between your local data center and Alibaba Cloud. Alibaba Cloud supports up to four physical connections to achieve Equal-CostMultipathRouting \(ECMP\).

 For more information, see [Create redundant physical connections](../../../../../reseller.en-US/User Guide (New Console)/Physical connection/Create redundant physical connections.md#).

 |
|Smart Access Gateway| Smart Access Gateway \(SAG\) is an all-in-one solution for connecting local branches of an enterprise to the Alibaba Cloud. With Smart Access Gateway, enterprises can access Alibaba Cloud through the Internet using a fully encrypted connection, which is more intelligent, more reliable, and more secure.

 Smart Access Gateway is an easy-to-configure and low-cost service. If you want to connect multiple local branches of an enterprise to the cloud, we recommend that you select Smart Access Gateway.

 For more information, see [Connect local branches to Alibaba Cloud through Smart Access Gateway](../../../../../reseller.en-US/Best Practices/Tutorial for configuring Smart Access Gateway as the backup of a physical connection/Configuration overview.md#).

 |
|BGP active/standby links| Function by using both a physical connection and CEN, allowing you to connect an on-premises data center to VPCs in different regions through active/standby links.

 For more information, see [Connect a local data center to Alibaba Cloud by using BGP active/standby links](../../../../../reseller.en-US/Best Practices/Connect a local data center to Alibaba Cloud using BGP active__standby links.md#).

 |
|Physical connection + Smart Access Gateway| A solution using Smart Access Gateway as the backup link of the existing physical connection to build a reliable and high-availability hybrid cloud.

 For more information, see [Tutorial for configuring Smart Access Gateway as the backup of a physical connection](../../../../../reseller.en-US/Best Practices/Tutorial for configuring Smart Access Gateway as the backup of a physical connection/Configuration overview.md#).

 |

