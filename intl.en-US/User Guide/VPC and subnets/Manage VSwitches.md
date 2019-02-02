# Manage VSwitches {#concept_smn_zdx_rdb .concept}

A VSwitch is a basic network module in a VPC network, used to connect different cloud product instances in the VPC.

After creating a VPC, you can further segment your virtual private network to one or more subnets by creating VSwitches. The VSwitches within a VPC are interconnected by default. You can deploy different applications to the VSwitches that are located in different zones to improve the service availability.

**Note:** A VSwitch does not support multicast or broadcast. You can achieve multicast proxy by using the multicast agent tool provided by Alibaba Cloud. For more information, see [Configure multicast for Linux kernel](intl.en-US/User Guide/VPC and subnets/Configure multicast for Linux kernel.md#).

## Create VSwitch {#section_hd5_g5x_rdb .section}

To create a VSwitch, complete these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com).
2.  Select the region of the VPC to which the VSwitch belongs.
3.  In the left-side navigation pane, click **VSwitches**.
4.  Click **Create VSwitch**, configure the VSwitch according to the following information and click **OK**.

    |Configuration|Description|
    |:------------|:----------|
    |**VPC**|Select the VPC to which the VSwitch belongs.|
    |**CIDR Block**|Display the CIDR block of the VPC.|
    |**Name**| Enter the name of the VSwitch.

 The name can contain 2 to 128 characters. It must begin with English letters or Chinese characters and can contain numbers, hyphens, and underlines.

 |
    |**Zones**|Select the zone of the VSwitch. In a VPC, VSwitches in different zones can communicate with each other through the intranet.|
    |**Zone Resource**|Display the cloud resources that can be used in the selected zone.|
    |**CIDR**| Enter the CIDR block of the VSwitch.

 Note the following when specifying the VSwitch CIDR block:

    -   The CIDR block of the VSwitch can be the same as that of the VPC to which it belongs, or a subset of the VPC CIDR block.

For example, if the CIDR block of the VPC is 192.168.0.0/16, the CIDR block of the VSwitch in the VPC can be 192.168.0.0/16, 192.168.0.0/17, …, till 192.168.0.0/29.

**Note:** If the CIDR block of the VSwitch is the same as that of the VPC to which it belongs, you can only create one VSwitch in the VPC.

    -   The size of the subnet mask for the VSwitch can be /16 to /29, which can provide 8 to 65536 IP addresses.

    -   The first and last three IP addresses are reserved by the system.

Take the IP address range 192.168.1.0/24 as an example, IP addresses 192.168.1.0, 192.168.1.253, 192.168.1.254, and 192.168.1.255 are reserved by the system.

    -   Make sure the CIDR block does not conflict with that of the VSwitch in another VPC or the local data center that the VSwitch connects to.

 |
    |**Number of Available Private IPs**|Display the number of available private IPs of the VSwitch.|
    |**Description**| Enter a description of the VSwitch.

 The name can contain 2 to 256 characters, but cannot begin with`http://` and `https://`.

 |


## Create cloud resources in a VSwitch {#section_drn_dwx_rdb .section}

To create cloud resources in a VSwitch, complete these steps:

1.  Log on to the VPC console.
2.  Select the region of the VPC.
3.  In the left-side navigation pane, click **VSwitches**.
4.  Locate the target VSwitch, click **Purchase** and select the cloud resources to create.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2436/15490940179789_en-US.png)

5.  Complete the configuration.

## Delete a VSwitch {#section_ztp_pwx_rdb .section}

**Note:** Before deleting a VSwitch, make sure that:

-   You have deleted all cloud resources in the VSwitch, such as ECS, SLB, and RDS.

-   If the VSwitch has configured an SNAT entry, VPN Gateway, or HAVIP, delete these associated resources.


To delete a VSwitch, complete these steps:

1.  Log on to the VPC console.
2.  Select the region of the VPC.
3.  In the left-side navigation pane, click **VSwitches**.
4.  Locate the target VSwitch, and click **Delete**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2436/15490940179788_en-US.png)

5.  In the displayed dialog, click **OK**.

## Related APIs {#section_vhd_xwx_rdb .section}

[CreateVSwitch](../../../../../intl.en-US/API reference/VSwitch/CreateVSwitch.md#)

[DeleteVSwitch](../../../../../intl.en-US/API reference/VSwitch/DeleteVSwitch.md#)

[DescribeVSwitches](../../../../../intl.en-US/API reference/VSwitch/DescribeVSwitches.md#)

[ModifyVSwitchAttribute](../../../../../intl.en-US/API reference/VSwitch/ModifyVSwitchAttribute.md#)

