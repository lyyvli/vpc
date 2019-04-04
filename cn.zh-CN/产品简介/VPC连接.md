# VPC连接 {#concept_wyd_112_sdb .concept}

阿里云提供了丰富的解决方案以满足VPC内的云产品实例与公网（Internet）、其他VPC、或本地数据中心（IDC）互连的需求。

## 连接公网 {#section_jyt_lhj_w2b .section}

您可以使用下表中的产品或功能，将专有网络和公网（Internet）打通。

|产品|功能|优势|
|:-|:-|:-|
|VPC ECS固定公网IP| 在专有网络内创建ECS时自动分配的公网IP，支持VPC ECS访问公网（SNAT）和用户从公网访问VPC ECS（DNAT）。

 目前默认不能动态和VPC ECS解绑，但可以将公网IP转换为EIP。详细说明，请参见[ECS固定公网IP转换为EIP](../cn.zh-CN/用户指南/ECS固定公网IP转换为EIP.md#)。

 | 支持使用[共享流量包](https://www.aliyun.com/product/flowbag)，将公网IP转换为EIP后也可以使用[共享带宽](https://www.aliyun.com/product/cbwp)。

 |
|弹性公网IP（EIP）|能够动态和VPC ECS绑定和解绑，支持VPC ECS访问公网（SNAT）和用户从公网访问VPC ECS（DNAT）。| EIP可以随时和ECS实例绑定和解绑。

 可以使用[共享带宽](https://www.aliyun.com/product/cbwp)和[共享流量包](https://www.aliyun.com/product/flowbag)，降低公网成本。

 |
|NAT网关|支持多台VPC ECS访问公网（SNAT）和用户从公网访问VPC ECS（DNAT）。**说明：** 和负载均衡相比，NAT网关本身没有均衡流量的功能。

| NAT网关和EIP的核心区别是NAT网关可用于多台VPC ECS和公网通信，而EIP只能用于一台VPC ECS和公网通信。

 |
|负载均衡| 基于端口提供四层和七层负载均衡功能，支持用户从公网通过负载均衡（SLB）访问ECS。

**说明：** 负载均衡不支持VPC网络的ECS通过负载均衡主动访问公网（SNAT）。

 | 在DNAT方面，负载均衡是基于端口的负载均衡，即一个负载均衡的一个端口可以对应多台ECS。

 负载均衡通过对多台ECS进行流量分发，可以扩展应用系统对外的服务能力，并通过消除单点故障提升应用系统的可用性。

 绑定EIP后，支持使用[共享带宽](https://www.aliyun.com/product/cbwp)和[共享流量包](https://www.aliyun.com/product/flowbag)，降低公网成本。

 |

## 连接VPC {#section_lq3_mhj_w2b .section}

您可以使用下表中的产品或功能，连接两个VPC。

|产品|功能|优势|
|:-|:-|:-|
|VPN网关| 您可以通过在两个VPC之间创建IPsec连接，建立加密通信通道。

 详细说明，请参见[../DNvpc1887258/../../../../../../dita-oss-bucket/SP\_74/DNVPN11815583/ZH-CN\_TP\_13352.md\#](../cn.zh-CN/用户指南/配置IPsec-VPN/配置VPC到VPC连接.md#)。

 | -   成本低，安全，配置简单、即开即用，但网络质量依赖公网（Internet）。

-   IPsec-VPN支持IKEv1和IKEv2协议。只要支持这两种协议的设备都可以和阿里云VPN网关互连，比如华为、华三、山石、深信服、Cisco ASA、Juniper、SonicWall、Nokia、IBM 和 Ixia等。


 |
|云企业网| 支持将多个不同地域、不同账号的VPC连接起来，构建互联网络。

 详细说明，请参见[教程概览](../cn.zh-CN/快速入门/教程概览.md#)。

 | -   配置简单，自动学习分发路由。

-   低时延高速率。

-   加载到同一个云企业网实例的网络实例（VPC/VBR）全互通。

-   同地域网络实例互通免费。


 |

## 连接本地IDC {#section_s1d_4hj_w2b .section}

您可以使用下表中的产品或功能，将本地网络和云上专有网络打通。

|产品|功能|优势|
|:-|:-|:-|
|高速通道| 通过物理专线接入使VPC与本地数据中心网络互通。

 详细说明，请参见[物理专线接入](../cn.zh-CN/快速入门/物理专线接入.md#)。

 | -   基于骨干网络，延迟低。

-   专线连接更加安全、可靠、速度更快、延迟更低。


 |
|VPN网关| -   您可以通过IPsec连接，可以将本地数据中心网络和云上VPC连接起来。

-   多本地IDC连接

VPN网关默认开始VPN-Hub功能，支持多站点连接。各连接的站点不仅可以和VPC互通，并且各站点之间也可以通过VPN-Hub通信。

-   客户端远程接入

通过建立SSL-VPN连接，客户端可以远程接入VPC。


 | -   成本低、安全、配置简单，即开即用，但网络质量依赖公网（Internet）。

-   IPsec-VPN支持IKEv1和IKEv2协议。只要支持这两种协议的设备都可以和阿里云VPN网关互连，比如华为、华三、山石、深信服、Cisco ASA、Juniper、SonicWall、Nokia、IBM 和 Ixia等。

-   SSL-VPN连接支持Windows、Linux、Mac、IOS和Android等操作系统多终端接入。


 |
|云企业网| -   与本地IDC互通

支持将要互通的本地IDC关联的边界路由器（VBR）加载到已创建的云企业网实例，构建互联网络。

-   多VPC与IDC互通

支持将要互通的多个网络实例（VPC和VBR）加载到已创建的云企业网实例，构建企业级互联网络。


 | -   配置简单，自动学习分发路由。

-   低时延高速率。

-   加载到同一个云企业网实例的网络实例（VPC/VBR）全互通。

-   同地域网络实例互通免费。


 |
|智能接入网关| -   可实现线下机构（IDC/分支机构/门店等）接入阿里云数据中心，轻松构建混合云。

-   支持线下机构互通。


 | -   配置高度自动化，即插即用，网络拓扑变化自适应快速收敛。

-   城域内Internet就近接入，可通过设备及链路级主备方式实现线下多机构可靠上云。

-   混合云私网加密互连，Internet传输过程中加密认证。


 |

