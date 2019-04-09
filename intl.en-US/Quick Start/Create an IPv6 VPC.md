# Create an IPv6 VPC {#concept_qnx_55q_dgb .concept}

This tutorial guides you to build a VPC with an IPv6 CIDR block, create an ECS instance with an IPv6 address in the VPC, and enable the IPv6 service to be accessed.

## Step 1: Create a VPC {#section_a5p_lvq_dgb .section}

To use a cloud product in a VPC, you must plan the network, create a VPC, and create a subnet \(VSwitch\) to which the cloud product belongs. For more information, see [Network planning](../reseller.en-US/Best practices/Plan and design VPC.md#).

To create a VPC and a VSwitch with an IPv6 CIDR block, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc) .
2.  In the top menu bar, select a region.

    The VPC and the cloud resources to deploy must be in the same region. In this tutorial, **China \(Hohhot\)** is selected.

    **Note:** Currently, only the China \(Hohhot\) region supports enabling IPv6 CIDR block.

3.  Configure the VPC and VSwitch according to the following information.

    **Note:** In this tutorial, select **Allocate IPv6 CIDR Block**. After a VPC is created, the system automatically allocates an IPv6 CIDR block whose mask is /56 to the VPC and creates a IPv6 gateway for free. You can control the traffic of the IPv6 address through the IPv6 gateway.

    |Configuration|Description|
    |:------------|:----------|
    |**VPC**|
    |**Name**|Enter a name for the VPC.The name must be 2 to 128 characters in length. It can contain letters, numbers, hyphens \(-\) and underscores \(\_\) and must begin with a letter.

|
    |**IPv4 CIDR Block**|We recommend that you use an RFC private IP address range as the CIDR block of the VPC.    -   You can use the standard CIDR blocks: 192.168.0.0/16, 172.16.0.0/12, and 10.0.0.0/8, or their subnets as the IP address range of the VPC. If you want to use a subnet of a standard CIDR block as the IP address range of the VPC, you must call CreateVpc to create a VPC.

    -   If you want to connect a VPC to another VPC, or to an on-premises data center to build a hybrid cloud, we recommend that you use a subnet of the standard CIDR blocks as the CIDR block of the VPC, and make sure that the mask is no longer than /16.

    -   If you only have one VPC and it does not need to communicate with an on-premises data center, you can use any of the standard CIDR blocks or their subnets.

**Note:** After a VPC is created, you cannot change its IPv4 CIDR block.

|
    |**IPv6 CIDR block**| Select whether to allocate an IPv6 CIDR block to the VPC. By default, no IPv6 CIDR block is allocated.

 If you enable IPv6 CIDR blocks, the sysem allocates an IPv6 CIDR block with the mask /56 for your VPC, such as 2001:db8::/56.

 **Note:** After the VPC is created, you cannot change its CIDR block.

 |
    |**Description**|Enter a description for the VSwitch.The description must be 2 to 256 characters in length and cannot begin with http:// or https://.

|
    |**Resource Group**|Select the resource group to which the VPC belongs.|
    |**VSwitch**|
    |**Name**|Enter a name for the VSwitch.The name must be 2 to 128 characters in length and can contain letters, numbers, hyphens \(-\) and underscores \(\_\). The name must start with a letter.

|
    |**Zone**|Select the zone of the VSwitch. In a VPC, VSwitches in different zones can communicate with each other through the intranet.|
    |**IPv4 CIDR Block**|Enter the IPv4 CIDR block of the VSwitch. Note the following when specifying the VSwitch CIDR block:    -   The CIDR block of the VSwitch can be the same as that of the VPC to which it belongs, or a subnet of the VPC CIDR block.

For example, if the CIDR block of the VPC is 192.168.0.0/16, the CIDR block of the VSwitch in the VPC can be in the range of 192.168.0.0/16 to 192.168.0.0/29.

**Note:** If the CIDR block of the VSwitch is the same as that of the VPC to which it belongs, you can only create one VSwitch in the VPC.

    -   The size of the mask for the VSwitch can be /16 to /29, which can provide 8 to 65536 IP addresses.

    -   The first and last three IP addresses are reserved by the system.

For example, for the IP address range 192.168.1.0/24, IP addresses 192.168.1.0, 192.168.1.253, 192.168.1.254, and 192.168.1.255 are reserved by the system.

    -   Make sure the CIDR block does not conflict with that of the VSwitch in another VPC or the on-premises data center to which the VSwitch connects.

**Note:** After the VSwitch is created, you cannot change its CIDR block.

|
    |**IPv6 CIDR Block**| The IPv6 CIDR block of the VSwitch.

 The mask for the IPv6 CIDR block of the VSwitch is /64. You can enter a value from 0 to 255 to define the last 8 bits of the IPv6 CIDR block.

 If the IPv6 CIDR block of the VPC is 2001:db8::/64 and you enter 255 in the IPv6 CIDR block of the VSwitch \(the corresponding hexadecimal representation is ff\), the IPv6 CIDR block of the VSwitch is 2001:db8::ff/64.

 **Note:** After the VSwitch is created, you cannot change its CIDR block.

 |
    |**Description**|Enter a description for the VSwitch.The description must be 2 to 256 characters in length and cannot start with http:// or https://.

|

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80011/155479642634424_en-US.png)


## Step 2: Create and configure an ECS instance {#section_d2s_s1r_dgb .section}

After creating the IPv6 VPC and VSwitch, you can create an ECS instance with an IPv6 address. After you create the ECS instance, you need to attach the allocated IPv6 address to the ENI on it.

To create and configure an ECS instance, follow these steps:

1.  In the left-side navigation pane of the VPC console, click **VSwitches**.
2.  On the VSwitches page, find the target VSwitch and click **Purchase** \> **ECS Instance**.
3.  Configure the ECS instance according to your needs.

    **Note:** In this tutorial, the network configurations of the ECS instance are as follows:

    -   To log on to the ECS instance, configure the network card. Select **Assign public IP** and set the bandwidth to 1 Mpbs. You can also select to use an EIP instead.
    -   Select **Allocate an Ipv6 address for free**.
4.  After the ECS instance is purchased, go back to the ECS instances page. Click the ID of the target instance and view the allocated IPv6 address.
5.  Configure a static IPv6 address.

## （Optional）Step 3: Enable the IPv6 address to access or be accessed from the Internet {#section_qqb_wkr_dgb .section}

By default, IPv6 addresses are only capable of intranet communication. To enable the allocated IPv6 address to access the Internet or be accessed by Internet Ipv6 clients, you need to enable the IPv6 Internet bandwidth.

To buy an Internet bandwidth, follow these steps:

1.  In the left-side navigation pane of the VPC console, click **IPv6 Gateway**.
2.  Find the target IPv6 Gateway and click **Manage**.
3.  In the left-side navigation pane, click **IPv6 Internet Bandwidth**.
4.  Find the IPv6 address used by the ECS instance and click **Enable Internet Bandwidth**.
5.  Select a billing method and an Internet bandwidth, and complete the payment.

## Step 4: Configure security group rules {#section_ugx_1jr_dgb .section}

For more information, see [Add security group rules](../../reseller.en-US/Security/Security groups/Add security group rules.md#).

## Step 5: Test the connection {#section_qtm_wqr_dgb .section}

Log on to the ECS instance and ping an IPv6 service to test if the service can be accessed.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80011/155479642634440_en-US.png)

