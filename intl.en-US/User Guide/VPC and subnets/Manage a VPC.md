# Manage a VPC {#concept_ly1_lpw_rdb .concept}

This topic describes how to manage an Alibaba Cloud Virtual Private Cloud \(VPC\), including how to create a VPC and a VSwitch, enable ClassicLink, attach a VPC to a CEN instance, and how to delete a VPC.

## Create a VPC and a VSwitch {#section_ufw_rhv_rdb .section}

To deploy cloud resources in a VPC, you must create at least one VSwitch. To create a VPC and a VSwitch, follow these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com).
2.  In the top menu bar, select the region to which the VPC will belong.

    The VPC and the cloud resources to deploy must be located in the same region.

3.  Click **Create VPC** and then configure the VPC according to your requirements. The following table describes VPC configuration items. Then, click **OK**.

    **Note:** Currently, only the China \(Hohhot\) region supports enabling IPv6. After IPv6 is enabled, the system creates an IPv6 Gateway.

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


## Enable ClassicLink {#section_jdv_syw_rdb .section}

With ClassicLink enabled, ECS instances of the classic network type can communicate with cloud resources in the connected VPC. For more information, see [ClassicLink overview](intl.en-US/User Guide/Network connection/ClassicLink/ClassicLink overview.md#).

To enable the ClassicLink function, follow these steps:

1.  Log on to the VPC console.
2.  Select the target region and click the ID of the target VPC.
3.  In the upper-right corner of the page, click **Enable the ClassicLink**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2435/15549652259786_en-US.png)

4.  Click **OK**.

    For more information, see [Build a ClassicLink connection](intl.en-US/User Guide/Network connection/ClassicLink/Establish a ClassicLink connection.md#).


## Attach a VPC to a CEN instance {#section_l3q_byw_rdb .section}

You can attach a VPC to a CEN instance so that the VPC can communicate with other VPCs or on-premises data centers attached to the CEN instance. For more information, see [What is Cloud Enterprise Network?](../../intl.en-US/Product Introduction/What is Cloud Enterprise Network?.md#).

To attach a VPC to a CEN instance in the same account, follow these steps:

1.  Log on to the VPC console.
2.  Select the target region and click the ID of the target VPC.
3.  In the upper-right corner of the page, click **Attach to CEN**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2435/15549652259784_en-US.png)

4.  Select the target CEN instance and click **OK**.

## Authorize a CEN instance under another account to attach the VPC {#section_gtw_vbj_w2b .section}

If you want to attach the VPC to a CEN instance under a different account, you need to authorize the CEN instance that is to attach it.

To authorize a CEN instance under a different account to attach your VPC, follow these steps:

1.  Log on to the VPC console.
2.  Select the target region and click the ID of the target VPC.
3.  In the CEN cross account authorization information area, click **CEN Cross Account Authorization**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2435/15549652259785_en-US.png)

4.  In the Attach to CEN dialog box, enter the ID of the account to which the CEN instance belongs and the ID of the CEN Instance, and then click **OK**.

## Delete a VPC {#section_j4l_1xw_rdb .section}

Before you delete a VPC, make sure that you have deleted all VSwitches in the VPC. Otherwise, the deletion operation will not take effect. After a VPC is deleted, its associated VRouters and route tables are also deleted.

To delete a VPC, follow these steps:

1.  Log on to the VPC console and select the target region.
2.  Locate the target VPC and click **Delete**.
3.  In the displayed dialog box, click **OK**.

## Related API actions {#section_es2_lbx_rdb .section}

[CreateVpc](../intl.en-US/API reference/Virtual Private Cloud (VPC)/CreateVpc.md#)

[DeleteVpc](../intl.en-US/API reference/Virtual Private Cloud (VPC)/DeleteVpc.md#)

[DescribeVpcAttribute](../intl.en-US/API reference/Virtual Private Cloud (VPC)/DescribeVpcAttribute.md#)

[DescribeVpcs](../intl.en-US/API reference/Virtual Private Cloud (VPC)/DescribeVpcs.md#)

