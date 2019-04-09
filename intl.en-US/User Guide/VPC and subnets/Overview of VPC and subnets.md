# Overview of VPC and subnets {#concept_sgp_twv_dgb .concept}

This topic describes Alibaba Cloud Virtual Private Clouds \(VPCs\) and VSwitches \(indicated as subnets in this topic\). You can create multiple VSwitches to divide a VPC into multiple subnets. By default, VSwitches in a VPC are connected through the intranet.

## VPC and subnets {#section_d3l_ncw_dgb .section}

VPC is a virtual cloud network dedicated to you. You can deploy cloud products in your VPC.

**Note:** You cannot deploy a cloud product in a VPC directly. You must deploy each cloud product in a VSwitch \(subnet\) of a VPC.

VSwitches are basic network devices that are used to form a VPC and connect different cloud product instances. VPCs are region-level resources. A VPC cannot be used across multiple regions, but it can contain all zones in a region. You can create one or more VSwitches in a zone to divide the zone into multiple subnets.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80559/155479659034448_en-US.png)

## CIDR blocks and IP addresses {#section_xc2_wlw_dgb .section}

VPCs support both IPv4 and IPv6 addressing protocols. By default, each VPC uses the IPv4 addressing protocol. However, you can enable the IPv6 addressing protocol as needed.

VPCs can operate in dual-stack mode, whereby resources in a VPC can communicate through IPv4 or IPv6 addresses. However, when you configure routes and security groups for IP addresses, you need to set the routes and security groups for IPv4 addresses and IPv6 addresses separately in a VPC.

The following table lists the differences between an IPv4 address and an IPv6 address.

|IPv4 VPC|IPv6 VPC|
|:-------|:-------|
|32 bits, 4 groups. Each group consists of up to 3 numbers.|128 bits, 8 groups, each group consists of 4 hexadecimal numbers.|
|The IPv4 address protocol is enabled by default.|You can select to enable the IPv6 address protocol.|
|The size of the VPC CIDR block can range from /8 to /24.|The size of the VPC CIDR block is /56.|
|The size of the VSwitch CIDR block can range from /16 to /29.|The size of the VSwitch CIDR block is /64.|
|You can select the IPv4 CIDR block to use.|You cannot select the IPv6 CIDR block to use. The system allocates an IPv6 CIDR block from the IPv6 address pool to your VPC.|
|All types of instances support the IPv4 protocol.|Some types of instances do not support the IPv6 protocol.For more information, see [Instance type families](../../../../../reseller.en-US/Instances/Instance type families/Instance type families.md#).

|
|Configuring ClassicLink is supported.|Configuring ClassicLink is not supported.|
|Configuring elastic IPv4 addresses is supported.|Configuring elastic IPv6 addresses is not supported.|
|Configuring VPN Gateway and NAT Gateway is supported.|Configuring VPN Gateway or NAT Gateway is not supported.|

By default, both IPv4 and IPv6 addresses of VPC only support intranet communication, which means products under different VSwitches in a VPC can only communicate with each other through the intranet. To connect a VPC to another VPC or an on-premises data center, you need to configure a Smart Access Gateway, Express Connect, a VPN Gateway or another related product to achieve communication. For more information, see [Connect an on-premises data center](../../../../../reseller.en-US/User Guide/Network connection/Connect a VPC to an on-premises data center.md#).

To enable the VPC to communicate with the Internet, configure the VPC as follows:

-   IPv4 Internet communication

    You can associate an EIP or NAT Gateway so that ECS instances in a VPC can communicate through the Internet by using IPv4 addresses.

    For more information, see [Attach cloud resources](../../../../../reseller.en-US/User Guide/Bind EIP to cloud resources.md#) and [Configure NAT Gateway](../../../../../reseller.en-US/Quick Start/Tutorial overview.md#).

-   IPv6 Internet communication

    You need to purchase an Internet bandwidth for the IPv6 address used for communication with the Internet. Then, you can configure an egress-only rule for the IPv6 address, so that cloud products in the VPC can only access the Internet by using the IPv6 address, and IPv6 clients can actively establish connections with other cloud products in the VPC.


## Routes {#section_bpg_rgx_dgb .section}

After a VPC is created, the system automatically creates one default route table \(the system route table\) and adds system routes to it to manage traffic. You cannot manually create or delete a default system route entry, or delete the system route table.

![](images/34508_en-US_source.png)

![](images/34508_en-US_source.png)

If you need to add custom subnet routes, you can create a custom route table in a target VPC and attach it to the corresponding VSwitch. Each VSwitch can only be associated with one route table. For more information, see [Manage route tables](reseller.en-US/User Guide/Routes/Manage custom route tables.md#).

![](images/34509_en-US_source.png)

Route tables implements the longest prefix match algorithm. Therefore, when multiple IP addresses match the destination IP address, the IP address with the longest mask is selected as the next hop. You can also add a custom route entry to route the traffic to the specified IP address. For more information, see [Add a custom route entry](http://icms.alibaba-inc.com/document/content/265?version=79&topic=2437).

