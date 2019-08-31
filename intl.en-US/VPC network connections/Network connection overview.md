# Network connection overview {#concept_wyd_112_sdb .concept}

This topic describes the network solutions provided by Alibaba Cloud for connecting your VPC to the Internet, other VPCs, and on-premises data centers.

## Connect a VPC to the Internet {#section_xvk_msk_w2b .section}

The following table lists the products and functions that you can use to connect a VPC to the Internet.

|Product|Function|Benefit|
|:------|:-------|:------|
|ECS public IP address|When you create a VPC ECS instance, you can assign the instance a public IPv4 address that supports access to or from the Internet. An ECS public IP address cannot be dynamically disassociated from the corresponding VPC ECS instance, but can be converted to an EIP. For more information, see [Convert an ECS public IP address to an EIP](../reseller.en-US/User Guide/Create an EIP/Convert an ECS public IP address to an EIP.md#).

 | You can use [Data Transfer Plan](../reseller.en-US/Product Introduction/Product introduction.md#). After changing a public IP address to an EIP, you can also use [Internet Shared Bandwidth](../reseller.en-US/Product Introduction/What is Internet Shared Bandwidth?.md#).

 |
|Elastic IP \(EIP\)|With an EIP, the ECS instance can access the Internet \(SNAT\) and can be accessed from the Internet \(DNAT\).| You can associate an EIP with or disassociate an EIP from an ECS instance at any time.

 You can use [Internet Shared Bandwidth](../reseller.en-US/Product Introduction/What is Internet Shared Bandwidth?.md#) and [Data Transfer Plan](../reseller.en-US/Product Introduction/Product introduction.md#) to reduce Internet cost.

 |
|NAT Gateway|NAT Gateways allow multiple VPC ECS instances to access the Internet \(SNAT\) and be accessed from the Internet \(DNAT\). **Note:** Compared with Server Load Balancer \(SLB\), NAT Gateways does not provide the traffic balancing function.

 |A NAT Gateway can be used for multiple ECS instances to access the Internet, while an EIP can be used for only one VPC ECS instance to access the Internet.|
|SLB| SLB provides layer 4 and layer 7 server load balancing, which allows access to ECS instances from the Internet.

**Note:** VPC ECS instances cannot access the Internet \(SNAT\) through SLB.

 |In DNAT, SLB can forward an Internet request to multiple ECS instances. SLB can distribute traffic to multiple ECS instances to expand service capabilities and improve availability of applications.

 After you associate an EIP with an SLB instance, you can use [Internet Shared Bandwidth](../reseller.en-US/Product Introduction/What is Internet Shared Bandwidth?.md#) and [Data Transfer Plan](../reseller.en-US/Product Introduction/Product introduction.md#) to reduce Internet cost.

 |

## Connect two VPCs {#section_rvx_msk_w2b .section}

The following table lists the products or functions that you can use to connect a VPC to another VPC.

|Product|Function|Benefit|
|:------|:-------|:------|
|Cloud Enterprise Network \(CEN\)| By using a CEN, you can connect VPCs in different regions under different accounts to build an interconnected network.

 For more information, see [Overview](../reseller.en-US/Quick Start/Overview.md#).

 | -   Global access
-   Low latency and fast speed
-   Nearest access and shortest path
-   Link redundancy and disaster recovery
-   Systematic management

 |
|VPN Gateway|By using a VPN Gateway, you can create an IPsec-VPN connection to build an encrypted channel between two VPCs. For more information, see [Establish a connection between two VPCs](../reseller.en-US/User Guide/Configure IPsec-VPN connections/Establish a connection between two VPCs.md#).

 | -   High security
-   High availability
-   Low cost
-   Easy configuration

 |

## Connect a VPC to an on-premises data center {#section_fdz_nsk_w2b .section}

The following table lists the products and functions that you can use to connect a VPC to an on-premises data center.

|Product|Function|Benefit|
|:------|:-------|:------|
|Express Connect|By using Express Connect, you can connect a VPC to an on-premises data center through a physical connection. For more information, see [Connect an on-premises data center to a VPC through a physical connection](../reseller.en-US/Getting Started (New Console)/Connect an on-premises data center to a VPC through a physical connection.md#).

 | -   Based on the backbone network, low latency
-   Secure and reliable physical connection

 |
|VPN Gateway| -   By using a VPN Gateway, you can create an IPsec-VPN connection between a VPC and an on-premises data center.
-   You can connect a local client to a VPC by creating an SSL-VPN connection.

 | -   High security
-   High availability
-   Low cost
-   Easy configuration

 |
|CEN| -   Connect to an on-premises data center

By using a CEN, you can attach the virtual border router \(VBR\) associated with an on-premises data center to a CEN instance to build an interconnected network.

-   Connect multiple VPCs with on-premises data centers

By using a CEN, you can attach multiple networks \(VPC/VBR\) to a CEN instance to build an interconnected network.


 | -   Global access
-   Low latency and fast speed
-   Nearest access and shortest path
-   Link redundancy and disaster recovery
-   Systematic management

 |
|Smart Access Gateway \(SAG\)| -   By using an SAG, you can connect on-premises branches \(such as data centers and outlets\) to Alibaba Cloud to build a hybrid cloud.
-   Interconnect on-premises branches.

 | -   SAGs features automated configuration and out-of-the-box experience, and can quickly adapts to network topology changes.
-   Access is provided from the nearest endpoint over the Internet. Multiple local branches can access Alibaba Cloud by using active and standby SAGs or active and standby links.
-   Local branches and Alibaba Cloud are connected through an encrypted private network. The transmission over the Internet is also encrypted.

 |

