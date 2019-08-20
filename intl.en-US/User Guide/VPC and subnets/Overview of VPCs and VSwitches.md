# Overview of VPCs and VSwitches {#concept_sgp_twv_dgb .concept}

This topic provides an overview of VPCs and VSwitches. You must create a VPC and a VSwitch before you can use the cloud resources in the VPC. You can create more than one VSwitch to divide a VPC into multiple subnets. By default, the subnets in a VPC are interconnected over the intranet.

## VPCs and VSwitches {#section_d3l_ncw_dgb .section}

A VPC is a virtual private network in which you can deploy your cloud resources.

**Note:** Cloud resources cannot be directly deployed in a VPC. They must be deployed in a VSwitch \(subnet\) of the VPC.

A VSwitch is a basic network device that is used to build a VPC and connect cloud resource instances. A VPC is a regional resource. It cannot be deployed across regions, but it contains all zones in the region to which it belongs. You can create one or more VSwitches in a zone to divide the zone into subnets.

![VSwitches](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80559/156629880834448_en-US.png)

## CIDR blocks and IP addresses {#section_xc2_wlw_dgb .section}

VPCs support both IPv4 and IPv6 addressing protocols. By default, VPCs use the IPv4 addressing protocol. However, you can enable the IPv6 addressing protocol as needed.

VPCs can operate in dual-stack mode, whereby VPC resources can communicate with each other through IPv4 or IPv6 addresses. However, when you configure routes and security groups for IP addresses, you need to set the routes and security groups for IPv4 addresses and IPv6 addresses separately in a VPC.

The following table compares an IPv4 address and an IPv6 address.

|IPv4 VPC|IPv6 VPC|
|:-------|:-------|
|32 bits, 4 groups. Each group consists of up to 3 decimal digits.|128 bits, 8 groups. Each group consists of 4 hexadecimal digits.|
|The IPv4 address protocol is enabled by default.|The IPv6 address protocol can be enabled manually.|
|The size of the VPC CIDR block is /56.|The size of the VPC CIDR block is /56.|
|The size of the VSwitch CIDR block range from /16 to /29.|The size of the VSwitch CIDR block must be /64.|
|You can select an IPv4 CIDR block.|You cannot select an IPv6 CIDR block. The system assigns an IPv6 CIDR block from the IPv6 address pool to your VPC.|
|All types of instances support the IPv4 protocol.|Some types of instances do not support the IPv6 protocol. For more information, see [Instance type families](../../../../reseller.en-US/Instances/Instance type families.md#).

 |
|ClassicLink is supported.|ClassicLink is not supported.|
|Elastic IPv4 addresses are supported.|Elastic IPv6 addresses are not supported.|
|VPN Gateways and NAT Gateways are supported.|VPN Gateways and NAT Gateways are not supported.|

By default, IPv4 and IPv6 addresses of VPCs only support intranet communication. Cloud resources under different VSwitches in a VPC can only communicate with each other through the intranet. To connect a VPC to another VPC or an on-premises data center, you need to configure a Smart Access Gateway, Express Connect, or a VPN Gateway. For more information, see [Connect a VPC to an on-premises data center](reseller.en-US/User Guide/Network connection/Connect a VPC to an on-premises data center.md#).

To enable a VPC to communicate with the Internet, you need to configure the VPC as follows:

-   IPv4 Internet communication

    You can associate an EIP or a NAT Gateway with the VPC so that ECS instances in the VPC can communicate through the Internet by using IPv4 addresses.

    For more information, see [Associate an EIP with an ECS instance](../../../../reseller.en-US/User Guide/Associate an EIP with a cloud instance/Associate an EIP with an ECS instance.md#) and [Configure a NAT Gateway](../../../../reseller.en-US/Quick Start/Tutorial overview.md#).

-   IPv6 Internet communication

    You need to purchase an Internet bandwidth for the IPv6 address used for communication with the Internet. Then, you can configure an egress-only rule for the IPv6 address. This allows cloud resource instances in the VPC to access the Internet by only using the IPv6 address, but does not allow the IPv6 client to establish connections with these cloud resource instances.


## Routes {#section_bpg_rgx_dgb .section}

Alibaba Cloud automatically creates a default route table and adds system route entries to it after you create a VPC. Each VPC has only one system route table. The system route table is automatically created when you create a VPC. You cannot create or delete the system route table.

![System route table](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80559/156629881034508_en-US.png)

You can create a custom route table in a VPC and then associate it with a VSwitch to control the subnet routing for more flexible network management. Each VSwitch can only be associated with one route table. For more information, see [Create a custom route table](reseller.en-US/User Guide/Routes/Create a custom route table.md#).

![Custom route table](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80559/156629881134509_en-US.png)

Route tables use the longest prefix match algorithm. Therefore, when multiple IP addresses match the destination IP address, the IP address with the longest mask is selected as the next hop. You can also add a custom route entry to route the traffic to the specified IP address. For more information, see [Add a custom route entry](reseller.en-US/User Guide/Routes/Add a custom route entry.md#).

