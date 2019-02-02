# Manage a VPC {#concept_ly1_lpw_rdb .concept}

Virtual Private Cloud \(VPC\) is a private network dedicated to you in Alibaba Cloud. You have full control over your VPC, such as specifying its IP address range, and configuring route tables and network gateways. You can also use Alibaba Cloud resources such as ECS, RDS, and SLB in your own VPC.

## VPC components {#section_q1l_qpw_rdb .section}

VRouter and VSwitch are two basic components of VPC:

-   VRouter connects VSwitches in a VPC and serves as the gateway connecting the VPC with other networks. A VRouter is automatically created after a VPC is created. Each VRouter associates with a route table. For more information, see [Routing](intl.en-US//Routing.md#).

-   VSwitch is a basic network module in a VPC, used to connect different cloud product instances. After creating a VPC, you can further segment your virtual private network to one or more subnets by creating VSwitches. You can deploy different applications to different VSwitches that are located in different zones to improve the service availability. VSwitches in different zones of a VPC can communicate with each other through the intranet by default. For more information, see [Manage VSwitches](intl.en-US/User Guide/VPC and subnets/Manage VSwitches.md#).


![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2435/1549093925809_en-US.png)

## IP address range \(CIDR block\) {#section_uy3_vqw_rdb .section}

When creating a VPC, you must specify the IP address range for the VPC in the form of a Classless Inter-Domain Routing \(CIDR\) block. Use the following standard private CIDR blocks or their subsets as the IP address range. The IP address range is related to your network design. For more information, see [Plan and design VPC](../../../../../intl.en-US/Best practices/Plan and design VPC.md#).

If you want to use a subset of a standard CIDR block as the IP address range, you must use the [CreateVpc](../../../../../intl.en-US/API reference/Virtual Private Cloud (VPC)/CreateVpc.md#) API to create a VPC.

|CIDR block|Number of available private IPs|
|:---------|:------------------------------|
|192.168.0.0/16|65,532|
|172.16.0.0/12|1,048,572|
|10.0.0.0/8|16,777,212|

## Create a VPC and a VSwitch {#section_ufw_rhv_rdb .section}

To deploy cloud resources in a VPC, you must create at least a VSwitch. To create a VPC and a VSwitch, complete these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com).
2.  Select the region of the VPC.

    The VPC and the cloud resources to deploy must locate in the same region.

3.  Click **Create VPC**, configure the VPC according to the following information and click **OK**.

    |Configuration|Description|
    |:------------|:----------|
    |**VPC configurations**|
    |**Name**|Enter a name for the VPC.The name can contain 2 to 128 characters. It must begin with English or Chinese characters and can contain numbers, hyphens \(-\) and underlines \(\_\).

|
    |**Destination CIDR Block**|Select a CIDR block for the VPC. Limitations on the VPC CIDR blocks are as follows:    -   You can use the standard CIDR blocks: 192.168.0.0/16, 172.16.0.0/12, and 10.0.0.0/8, or their subsets as the IP address range of the VPC. If you want to use a subnet of a standard CIDR block as the IP address range, you must use the CreateVpc API to create a VPC.

    -   If you want to connect a VPC to another VPC, or to a local network to build a hybrid cloud, it is recommended that you use the subset of the standard CIDR blocks, and make sure that the network mask is no longer than /16.

    -   If you only have one VPC and it does not need to communicate with your local network, you can use any of the standard CIDR blocks or their subsets.

**Note:** After the VPC is created, you cannot change its CIDR block.

|
    |**VSwitch configurations**|
    |**Name**|Enter a name for the VSwitch.The name can contain 2 to 128 characters. It must begin with English letters or Chinese characters and can contain numbers, hyphens \(-\) and underlines \(\_\).

|
    |**Zones**|Select the zone of the VSwitch. In a VPC, VSwitches in different zones can communicate with each other through the intranet.|
    |**CIDR Block**|Enter the CIDR block of the VSwitch. Note the following when specifying the VSwitch CIDR block:    -   The CIDR block of the VSwitch can be the same as that of the VPC to which it belongs, or a subset of the VPC CIDR block.

For example, if the CIDR block of the VPC is 192.168.0.0/16, the CIDR block of the VSwitch in the VPC can be 192.168.0.0/16, 192.168.0.0/17, …, till 192.168.0.0/29.

**Note:** If the CIDR block of the VSwitch is the same as that of the VPC to which it belongs, you can only create one VSwitch in the VPC.

    -   The size of the subnet mask for the VSwitch can be /16 to /29, which can provide 8 to 65536 IP addresses.

    -   The first and last three IP addresses are reserved by the system.

Take the IP address range 192.168.1.0/24 as an example, IP addresses 192.168.1.0, 192.168.1.253, 192.168.1.254, and 192.168.1.255 are reserved by the system.

    -   Make sure the CIDR block does not conflict with that of the VSwitch in another VPC or the local data center that the VSwitch connects to.

**Note:** After the VSwitch is created, you cannot change its CIDR block.

|


## Delete a VPC {#section_j4l_1xw_rdb .section}

Make sure that you have deleted all switches in the VPC. After the VPC is deleted, the associated VRouters and route tables are also deleted.

To delete a VPC, complete these steps:

1.  On the VPC console, select the region of the VPC.
2.  Locate the target VPC and click **Delete**.
3.  In the displayed dialog box, click **OK**.

## Enable ClassicLink {#section_jdv_syw_rdb .section}

With ClassicLink, ECS instances in the classic network can communicate with the cloud resource in the connected VPC. For more information, see [ClassicLink overview](intl.en-US//ClassicLink/ClassicLink overview.md#).

To enable the ClassicLink function, complete these steps:

1.  On the VPC console, select the region of the VPC.
2.  Click the ID of the target VPC.
3.  On theVPC Detailspage, click**Enable the ClassicLink**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2435/15490939259786_en-US.png)

4.  Click **OK**.
5.  Create a ClassicLink connection.

    For more information, see [Build a ClassicLink connection](intl.en-US//ClassicLink/Build a ClassicLink connection.md#).


## Attach to a CEN instance {#section_l3q_byw_rdb .section}

You can attach a VPC to a CEN instance, so that the VPC can communicate with other VPCs in the CEN instance or local data centers. For more information, see [What is Cloud Enterprise Network?](../../../../../intl.en-US/Product Introduction/What is Cloud Enterprise Network?.md#).

To quickly attach a VPC to a CEN instance in the same account, complete these steps:

1.  On the VPC console, select the region of the VPC.
2.  Click the ID of the target VPC.
3.  On the VPC Details page, click **Attach to CEN**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2435/15490939259784_en-US.png)

4.  Select a CEN instance and click **OK**.

## Authorize CEN {#section_gtw_vbj_w2b .section}

If you want the VPC to be attached to a CEN instance in a different account, authorize the CEN instance to attach it.

To authorize a CEN instance in a different account to attach your VPC, complete these steps:

1.  On the VPC console, select the region of the VPC.
2.  Click the ID of the target VPC to attach.
3.  On the VPC Details page, click **CEN Cross Account Authorization**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2435/15490939259785_en-US.png)

4.  In the Attach to CEN dialog box, enter the ID of the account that the CEN instance belongs to and the ID of the CEN Instance, and then click **OK**.

## Related APIs {#section_es2_lbx_rdb .section}

[CreateVpc](../../../../../intl.en-US/API reference/Virtual Private Cloud (VPC)/CreateVpc.md#)

[DeleteVpc](../../../../../intl.en-US/API reference/Virtual Private Cloud (VPC)/DeleteVpc.md#)

[DescribeVpcs](../../../../../intl.en-US/API reference/Virtual Private Cloud (VPC)/DescribeVpcs.md#)

[ModifyVpcAttribute](../../../../../intl.en-US/API reference/Virtual Private Cloud (VPC)/ModifyVpcAttribute.md#)

