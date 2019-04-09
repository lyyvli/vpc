# Manage VSwitches {#concept_smn_zdx_rdb .concept}

This topic describes how to manage VSwitches, covering how to create and delete a VSwitch and how to create a cloud a cloud resource in a VSwitch.

After creating a VPC, you can further your virtual private network to one or more subnets by creating VSwitches. The VSwitches within a VPC are interconnected by default. You can deploy different applications to the VSwitches that are located in different zones to improve the service availability.

**Note:** A VSwitch does not support multicast or broadcast.

## Create a VSwitch {#section_hd5_g5x_rdb .section}

To create a VSwitch, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  Select the region of the VPC to which the VSwitch will belong.
3.  In the left-side navigation pane, click **VSwitches**.
4.  Click **Create VSwitch** and then click **OK**. Descriptions about the configuration items are provided in the following table.

    **Note:** Currently, only the China \(Hohhot\) region supports enabling IPv6. After IPv6 is enabled, the system creates an IPv6 Gateway.

    |配置|说明|
    |:-|:-|
    |**资源组**|选择交换机的所属资源组。|
    |**专有网络**|选择交换机的所属专有网络。|
    |**IPv4网段**|所选专有网络的IPv4网段。|
    |**IPv6网段**|所选专有网络的IPv6网段。**Note:** 如果选择的专有网络未开启IPv6网段，单击**开通IPv6网段**。开通后，系统将为您创建免费版IPv6网关。

|
    |**描述**|输入VPC的描述信息。描述可包含2-256个中英文字符，不能以http://和https://开头。

|
    |**名称**|交换机的名称。长度为2-128个字符，以英文字母或中文开头，可包含数字，下划线（\_）和短横线（-）。

|
    |**可用区**|交换机的可用区。同一VPC内不同可用区的交换机内网互通。|
    |**IPv4网段**|交换机的IPv4网段。交换机的网段限制如下：    -   交换机的网段可以和其所属的VPC网段相同或者是其VPC网段的子集。

例如，VPC的网段是192.168.0.0/16，那么该VPC内的交换机的网段可以是192.168.0.0/16，也可以是192.168.0.0/17，一直到192.168.0.0/29。

**Note:** 如果交换机的网段和专有网络的网段相同，您只能创建一个交换机。

    -   交换机的网段的大小在16位网络掩码与29位网络掩码之间，可提供8-65536个地址。

    -   每个交换机的第一个和最后三个IP地址为系统保留地址。

以192.168.1.0/24为例，192.168.1.0、 192.168.1.253、 192.168.1.254和192.168.1.255这些地址是系统保留地址。

    -   如果该交换机有和其他专有网络的交换机，或本地数据中心通信的需求，确保交换机的网段和要通信的网段不冲突。

**Note:** 交换机创建后，不能再修改网段。

|
    |**可用IP数量**|显示交换机可用的IPv4地址数量。|
    |**IPv6网段**| 交换机的IPv6网段。

 交换机的IPv6网段的掩码默认为/64，您可以输入十进制数字0-255，来自定义交换机IPv6网段的最后8比特位。

 如VPC的IPv6网段为2001:db8::/64，在交换机的IPv6网段输入十进制数字255（对应十六进制为ff），则交换机的IPv6网段将为2001:db8::ff/64。

 |
    |**描述**|输入交换机的描述信息。描述可包含2-256个中英文字符，不能以http://和https://开头。

|


## Create cloud resources in a VSwitch {#section_drn_dwx_rdb .section}

To create cloud resources in a VSwitch, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  Select the region of the VPC.
3.  In the left-side navigation pane, click **VSwitches**.
4.  Locate the target VSwitch, click **Purchase** and select the cloud resource to create.

    **Note:** Currently, you can create the following cloud resources in a VSwitch: ECS instances, SLB instances, and RDS instances.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2436/15547980769789_en-US.png)


## Delete a VSwitch {#section_ztp_pwx_rdb .section}

Before deleting a VSwitch, make sure the following conditions are met:

-   You have deleted all cloud resources in the VSwitch \(such as ECS, SLB, and RDS instances\).

-   If the VSwitch has been configured with SNAT entries, HAVIP, or any other configuration, make sure that you have deleted these associated resources.


To delete a VSwitch, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  Select the region of the VPC.
3.  In the left-side navigation pane, click **VSwitches**.
4.  Locate the target VSwitch, and click **Delete**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2436/15547980769788_en-US.png)

5.  In the displayed dialog box, click **OK**.

## Related APIs {#section_vhd_xwx_rdb .section}

[CreateVSwitch](../reseller.en-US/API reference/VSwitch/CreateVSwitch.md#)

[DescribeVSwitches](../reseller.en-US/API reference/VSwitch/DescribeVSwitches.md#)

[DeleteVSwitch](../reseller.en-US/API reference/VSwitch/DeleteVSwitch.md#)

[DescribeVSwitchAttributes](../reseller.en-US/API reference/VSwitch/DescribeVSwitchAttributes.md#)

