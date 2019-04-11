# Create a VPC {#concept_isl_ghv_rdb .concept}

This tutorial shows how to create an ECS instance in a VPC. This tutorial also shows how to attach an EIP to the ECS instance to enable the instance to access the Internet.

## Step 1: Create a VPC and a VSwitch {#section_ufw_rhv_rdb .section}

To deploy cloud resources in a VPC, you must first plan the network, create a VPC and create at least one VSwitch. To plan the network, see [Network planning](../reseller.en-US/Best practices/Plan and design VPC.md#).

To create a VPC and a VSwitch, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc) .
2.  Select a region.

    The VPC and the cloud resources to deploy must be in the same region. In this tutorial, select the **China \(Qingdao\)** region.

3.  Configure the VPC and VSwitch. Descriptions about the configuration items are provided in the following table.

    **Note:** In this tutorial, do not select **Assign IPv6 Address Free of Charge**.

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


## Step 2: Create an ECS instance {#section_b1n_rhw_rdb .section}

To create an ECS instance in the VPC, follow these steps:

1.  In the left-side navigation pane, click **VSwitches**.
2.  Select the target region. In this tutorial, select **China \(Qingdao\)**.
3.  Find the created VSwitch, and then click **Purchase** \> **ECS Instance**.
4.  Configure the ECS instance and click **Buy Now**.

    For network configurations, the following are used in this tutorial:

    -   **Network**: Select the created VPC and VSwitch.
    -   **Assign Public IP**: Do not select.
    -   **Select Security Group**: Select to use the default security group. For more information, see [Default security group rules](../../reseller.en-US//Default security group rules.md#).
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2434/155494605534441_en-US.png)

5.  Go back to the ECS console to view the created ECS instance.

    ![](images/808_en-US_source.png)


## Step 3: Create and attach an EIP {#section_xw3_lkw_rdb .section}

An Elastic IP address \(EIP\) is a public IP address resource that you can purchase and use independently.

To create an EIP, follow these steps:

1.  In the left-side navigation pane, click **Elastic IP addresses**.
2.  Select the region of the EIP and click **Create EIP**. In this tutorial, select **China \(Qingdao\)**.
3.  Configure the EIP, and click Buy Now.

    For more information, see [Pay-As-You-Go](../../reseller.en-US/Pricing/Pay-As-You-Go.md#).

4.  Find the created EIP and click **Bind**.
5.  In the displayed dialog box, select **ECS Instance** as the **Instance Type**, select the created ECS instance and then click **OK**

\\

## Step 4: Test the Internet access {#section_q5d_smw_rdb .section}

After the ECS instance is associated with an EIP, it can communicate with the Internet. You can use the associated EIP address to initiate a remote access to the ECS instance.

**Note:** Make sure the security group rules of the ECS instance allow remote access. For more information, see [Typical applications of commonly used ports](../../reseller.en-US/Security/Security groups/Typical applications of commonly used ports.md#).

