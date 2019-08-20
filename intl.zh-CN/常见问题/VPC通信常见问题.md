# VPC通信常见问题 {#concept_bxf_qf4_tdb .concept}

本章节介绍并解答VPC通信的常见问题。

-   [同一VPC内不同交换机可以通信么？](#section_ppc_2l5_vdb)
-   [不同VPC之间能否内网互通？](#section_qpc_2l5_vdb)
-   [VPC是否支持专线接入？](#section_rpc_2l5_vdb)
-   [VPC是否提供VPN功能？](#section_spc_2l5_vdb)
-   [VPC可以访问公网服务么？](#section_tpc_2l5_vdb)
-   [公网可以访问VPC中的云服务么？](#section_vpc_2l5_vdb)
-   [VPC是否可以直接与经典网络通信？](#section_xpc_2l5_vdb)

## 同一VPC内不同交换机可以通信么？ {#section_ppc_2l5_vdb .section}

只要安全组规则允许，同一VPC内的ECS实例均可以互相通信，无论交换机是否相同。

## 不同VPC之间能否内网互通？ {#section_qpc_2l5_vdb .section}

不同VPC之间逻辑上完全隔离，您可以使用高速通道、VPN网关、云企业网实现VPC内网互通。详细信息，请参见[VPC私网接入](../../../../intl.zh-CN/最佳实践/如何选择私网类产品？.md#)。

## VPC是否支持专线接入？ {#section_rpc_2l5_vdb .section}

VPC支持本地数据中心通过物理专线接入，详细信息，请参见[自主申请物理专线接入](../../../../intl.zh-CN/快速入门/自主申请物理专线接入.md#)。

## VPC是否提供VPN功能？ {#section_spc_2l5_vdb .section}

VPC提供VPN功能，详细信息，请参见[VPN网关介绍](../../../../intl.zh-CN/用户指南/VPN网关介绍.md#)。

## VPC可以访问公网服务么？ {#section_tpc_2l5_vdb .section}

您可以使用以下方法从VPC访问公网服务：

-   分配公网IP
-   绑定弹性公网IP
-   配置NAT网关

详细信息，请参见[如何选择公网类产品](../../../../intl.zh-CN/最佳实践/如何选择公网类产品？.md#)。

## 公网可以访问VPC中的云服务么？ {#section_vpc_2l5_vdb .section}

您可以使用以下方法从公网访问VPC中的云服务：

-   分配公网IP
-   绑定弹性公网IP
-   配置NAT网关
-   配置公网负载均衡

详细信息，请参见[如何选择公网类产品](../../../../intl.zh-CN/最佳实践/如何选择公网类产品？.md#)。

## VPC是否可以直接与经典网络通信？ {#section_xpc_2l5_vdb .section}

VPC不能直接与经典网络通信。您可以通过以下方法为VPC中的ECS实例配置公网IP，通过Internet与经典网络中的云产品实例通信。详细信息，请参见[如何选择公网类产品](../../../../intl.zh-CN/最佳实践/如何选择公网类产品？.md#)。

或者，通过ClassicLink实现经典网络ECS和专有网络ECS内网低延时高速互通。详细信息，请参见[ClassicLink概述](../../../../intl.zh-CN/VPC与外部网络连接/ClassicLink/ClassicLink概述.md#)。

