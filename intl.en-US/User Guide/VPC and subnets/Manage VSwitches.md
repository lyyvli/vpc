# Manage VSwitches {#concept_smn_zdx_rdb .concept}

This topic describes how to manage VSwitches, covering how to create and delete a VSwitch and how to create a cloud a cloud resource in a VSwitch.

After creating a VPC, you can further your virtual private network to one or more subnets by creating VSwitches. The VSwitches within a VPC are interconnected by default. You can deploy different applications to the VSwitches that are located in different zones to improve the service availability.

**Note:** A VSwitch does not support multicast or broadcast.

## Create a VSwitch {#section_hd5_g5x_rdb .section}

To create a VSwitch, follow these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com).
2.  Select the region of the VPC to which the VSwitch will belong.
3.  In the left-side navigation pane, click **VSwitches**.
4.  Click **Create VSwitch** and then click **OK**. Descriptions about the configuration items are provided in the following table.

    **Note:** Currently, only the China \(Hohhot\) region supports enabling IPv6. After IPv6 is enabled, the system creates an IPv6 Gateway.

    |Configuration|Description|
    |:------------|:----------|
    |**Resource Group**|Optional. Select a resource group to which the VSwitch to be created belongs.|
    |**VPC**|Select a VPC to which the VSwitch to be created belongs.|
    |**IPv4 CIDR Block**|The IPv4 CIDR block of the selected VPC.|
    |**IPv6 CIDR Block**|The IPv6 CIDR block of the selected VPC.**Note:** If an IPv6 CIDR block is not enabled for the VPC you selected, click **Enable IPv6 CIDR Block**. After the IPv6 CIDR block is enabled, the system automatically creates an IPv6 Gateway of the Free Version specification for the VPC.

|
    |**Name**|Enter a name for the VSwitch to be created.The name must be 2 to 128 characters in length and can contain letters, numbers, underscores \(\_\), and hyphens \(-\). The name must start with a letter.

|
    |**Zone**|The zone of the VSwitch to be created. VSwitches that belong to the same VPC, but different zones, can communicate with each other through the intranet.|
    |**IPv4 CIDR Block**|The IPv4 CIDR block of the VSwitch.    -   The IPv4 CIDR block of the VSwitch can be the same as the CIDR block of the VPC that the VSwitch belongs. It can also be a subnet of the VPC CIDR block.

For example, if the CIDR block of the VPC is 192.168.0.0/16, the CIDR block of the VSwitch can be 192.168.0.0/16, or any CIDR block between 192.168.0.0/17 and 192.168.0.0/29.

**Note:** If the CIDR block of the VSwitch is the same as the CIDR block of the VPC, you can only create one VSwitch.

    -   The subnet mask of the VSwitch CIDR block can be 16 to 29 bits, which means the VSwitch can provide 8 to 65536 IP addresses.

    -   The first IP address and the last three IP addresses in the VSwitch CIDR block are reserved.

For example, if the VSwitch CIDR block is 192.168.1.0/24, the IP addresses 192.168.1.0, 192.168.1.253, 192.168.1.254, and 192.168.1.255 are reserved.

    -   If the VSwitch needs to communicate with other VSwitches of other VPCs or on-premises data centers, you need to make sure that the CIDR blocks involved do not conflict with each other.

**Note:** You cannot modify the CIDR block of the VSwitch after the VSwitch is created.

|
    |**Number of Available Private IPs**|The number of available IPv4 addresses provided by the VSwitch.|
    |**IPv6 CIDR Block**| The IPv6 CIDR block of the VSwitch.

 The mask of the IPv6 CIDR block of the VSwitch is set to /64 by default. You can enter 0 to 255 to customize the last eight bits of the IPv6 CIDR block.

 For example, if the IPv6 CIDR block of the selected VPC is 2001:db8::/64, you can enter 255 \(ff in hexadeciaml notation\). Then, the IPv6 CIDR block of the VSwitch is 2001:db8:ff::/64.

 |
    |**Description**|Optional. Enter a description for the VSwitch.The description must be 2 to 256 characters in length and can contain letters, numbers, and special characters. The description cannot start with http:// or https://.

|


## Create cloud resources in a VSwitch {#section_drn_dwx_rdb .section}

To create cloud resources in a VSwitch, follow these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com).
2.  Select the region of the VPC.
3.  In the left-side navigation pane, click **VSwitches**.
4.  Locate the target VSwitch, click **Purchase** and select the cloud resource to create.

    **Note:** Currently, you can create the following cloud resources in a VSwitch: ECS instances, SLB instances, and RDS instances.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2436/15579974799789_en-US.png)


## Delete a VSwitch {#section_ztp_pwx_rdb .section}

Before deleting a VSwitch, make sure the following conditions are met:

-   You have deleted all cloud resources in the VSwitch \(such as ECS, SLB, and RDS instances\).

-   If the VSwitch has been configured with SNAT entries, HAVIP, or any other configuration, make sure that you have deleted these associated resources.


To delete a VSwitch, follow these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com).
2.  Select the region of the VPC.
3.  In the left-side navigation pane, click **VSwitches**.
4.  Locate the target VSwitch, and click **Delete**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2436/15579974799788_en-US.png)

5.  In the displayed dialog box, click **OK**.

## Related APIs {#section_vhd_xwx_rdb .section}

[CreateVSwitch](../intl.en-US/API reference/VSwitch/CreateVSwitch.md#)

[DescribeVSwitches](../intl.en-US/API reference/VSwitch/DescribeVSwitches.md#)

[DeleteVSwitch](../intl.en-US/API reference/VSwitch/DeleteVSwitch.md#)

[DescribeVSwitchAttributes](../intl.en-US/API reference/VSwitch/DescribeVSwitchAttributes.md#)

