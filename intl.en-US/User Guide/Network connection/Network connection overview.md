# Network connection overview {#concept_wyd_112_sdb .concept}

Alibaba Cloud provides rich solutions for connecting a VPC to the Internet, other VPCs, or on-premises data centers.

## Connect to the Internet {#section_xvk_msk_w2b .section}

The following table lists the products and functions that you can use to connect a VPC to the Internet.

|Product|Features|Benefits|
|:------|:-------|:-------|
|The public IP of an ECS instance of the VPC network| The public IP allocated by Alibaba Cloud when creating an ECS instance of the VPC network. With this public IP, the ECS instance can access the Internet \(SNAT\) and also can be accessed from the Internet \(DNAT\).

 | You can use [Data Transfer Plan](../reseller.en-US/Product Introduction/Product introduction.md#)

 After changing a public IP to an EIP, you can also use [Internet Shared Bandwidth](Internet Shared Bandwidth../../SP_136/DNcbwp1847875/EN-US_TP_14714_V3.dita#concept_mks_snx_b2b).

 |
|Elastic IP Address \(EIP\)|With an EIP, the ECS instance can access the Internet \(SNAT\) and also can be accessed from the Internet \(DNAT\).| You can bind and unbind an EIP from an ECS instance at any time.

 You can use [Internet Shared Bandwidth](Internet Shared Bandwidth../../SP_136/DNcbwp1847875/EN-US_TP_14714_V3.dita#concept_mks_snx_b2b) and [Data Transfer Plan](Data Transfer Plan../../SP_123/DNflowbag1859607/EN-US_TP_14709_V4.dita#concept_usr_lsx_b2b) to reduce Internet cost.

 |
|NAT Gateway|NAT Gateway is an enterprise-class Internet gateway, supporting multiple ECS instances accessing the Internet with one EIP \(SNAT\) and being accessed from the Internet \(DNAT\). **Note:** Compared to Server Load Balancer, NAT Gateway itself does not provide traffic balancing.

 | Internet access for multiple ECS instances is supported. \(Note that EIP does not provide this support.\)

 |
|Server Load Balancer| Port-based load balancing, Server Load Balancer provides Layer-4 \(TCP and UDP protocols\) and Layer-7 \(HTTP and HTTPS protocols\) load balancing. Server Load Balancer can forward the client requests from the Internet to the backend ECS instances.

 **Note:** ECS instances without a public IP address cannot access the Internet \(SNAT\) through Server Load Balancer.

 | In DNAT, Server Load Balancer supports forwarding an Internet request to multiple ECS instances.

 Server Load Balancer can increase your service capability and enhance overall availability.

 After binding with an EIP, you can use [Internet Shared Bandwidth](Internet Shared Bandwidth../../SP_136/DNcbwp1847875/EN-US_TP_14714_V3.dita#concept_mks_snx_b2b) and [Data Transfer Plan](Data Transfer Plan../../SP_123/DNflowbag1859607/EN-US_TP_14709_V4.dita#concept_usr_lsx_b2b) to reduce the Internet cost.

 |

## Connect to a VPC {#section_rvx_msk_w2b .section}

The following table lists the products and functions that you can use to connect a VPC to another VPC.

|Product|Features|Benefits|
|:------|:-------|:-------|
|VPN Gateway| VPN Gateway allows you to create an IPsec-VPN connection to build an encrypted communication between two VPCs.

 | -   Low cost, secure, and simple configuration. \(The quality of the network depends on your Internet connection.\)

-   IPsec-VPN supports IKEv1 and IKEv2 protocols. Devices that support these two protocols can connect to Alibaba Cloud VPN Gateway. Supported devices: Huawei, H3C, SANGFOR, Cisco ASA, Juniper, SonicWall, Nokia, IBM, and Ixia.


 |
|Cloud Enterprise Network \(CEN\)| CEN allows you to connect VPCs in different regions and under different accounts to build an interconnected network.

 For more information, see [Tutorial overview](../reseller.en-US/Quick Start/Tutorial overview.md#).

 | -   Simple configuration, and automatic route learning and distribution.

-   Low latency and fast speed.

-   The networks \(VPCs/VBRs\) attached to a CEN instance are connected to each other.

-   The network connection in the same region is free of charge.


 |

## Connect a VPC to an on-premises data center {#section_fdz_nsk_w2b .section}

The following table lists the products and functions that you can use to connect a VPC to an on-premises data center.

|Product|Features|Benefits|
|:------|:-------|:-------|
|Express Connect| Express Connect allows you to connect a VPC to an on-premises data center.

 For more information, see [Connect an on-premises IDC to a VPC through a physical connection](../reseller.en-US/Getting Started (New Console)/Connect an on-premises IDC to a VPC through a physical connection.md#).

 | -   Based on the backbone network, low latency.

-   Leased line access features higher security and reliability, faster speed, and lower latency.


 |
|VPN Gateway| -   VPN Gateway allows you to create an IPsec-VPN connection between a VPC to an on-premises data center.

-   Connect multiple on-premises data centers

The VPN-Hub function of VPN Gateway allows you to connect multiple on-premises data centers to the VPC. The connected data centers can communicate with the VPC, but also can communicate with each other.

-   Remote access

VPN Gateway allows you to create an SSL-VPN connection to let clients access the VPC from a remote computer.


 | -   Low cost, secure, and simple configuration. However, the quality of the network depends on the Internet.

-   IPsec-VPN supports IKEv1 and IKEv2 protocols. Devices that support these two protocols can connect to Alibaba Cloud VPN Gateway. Supported devices: Huawei, H3C, SANGFOR, Cisco ASA, Juniper, SonicWall, Nokia, IBM, and Ixia.

-   SSL-VPN connections support connecting a VPC from a remote computer using the Linux, Windows, and MacOS.


 |
|CEN| -   Connect to an on-premises data center

CEN allows you to attach the VBR associated with an on-premises data center to a CEN instance to build an interconnected network.

-   Connect multiple VPCs with on-premises data centers

CEN allows you to attach multiple networks \(VPC/VBR\) to a CEN instance. All the attached networks are connected with each other.


 | -   Simple configuration, and automatic route learning and distribution.

-   Low latency and fast speed.

-   The networks \(VPCs/VBRs\) attached to a CEN instance are connected with each other.

-   The network connection in the same region is free of charge.


 |
|Smart Access Gateway\(SAG\)| -   Smart Access Gateway allows you to connect on-premises branches to the Alibaba Cloud to build a hybrid cloud for large organizations.

-   Connect local branches.


 | -   SAG features highly automated configuration and automatically and quickly adapts to network topology changes.

-   Access is provided from a nearby point within the city over the Internet. Additionally, multiple local branches can access Alibaba Cloud using the Smart Access Gateway devices with master-slave links.

-   The local branches and the Alibaba Cloud are connected through an encrypted private network and encryption authentication is implemented during the Internet transmission.


 |

