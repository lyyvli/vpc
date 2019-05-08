# Add a subnet route to a route table {#concept_187313 .concept}

You can create a custom route table in a VPC and add subnet routes to the created custom route table. Then, you can associate the route table with a VSwitch to control the traffic to and from the VSwitch, enabling flexible network management.

## Prerequisites {#section_bwg_vwq_gcm .section}

A VPC and a VSwitch are created. For more information, see [Manage a VPC](reseller.en-US/User Guide/VPC and subnets/Manage a VPC.md#).

## Limits {#section_pp4_w5m_1as .section}

Note the following limits before you add subnet routes to a route table:

-   You can create up to ten route tables in a VPC, including system route tables.
-   Each VSwitch can be associated with only one route table.
-   Active/standby routes and load balancing routes are not supported by custom route tables.

## Step 1: Create a custom route table {#section_ate_8wr_8xn .section}

To create a custom route table, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **Route Tables**.
3.  Click **Create Route Table**.
4.  Configure the route table according to the following information, and then click **OK**.

    |Configuration|Description|
    |:------------|:----------|
    |**Name**| Enter a name for the route table to be created.

 The name must be 2 to 128 characters in length and can contain letters, numbers, Chinese characters, underscores \(\_\), and hyphens \(-\). The name must start with a letter or a Chinese character.

 |
    |**VPC**|Select a VPC to which the route table to be created belongs.|
    |**Description**| Enter a description for the route table to be created.

 The description must be 2 to 256 characters in length and cannot start with `http://` or `https://`.

 |


## Step 2: Add a subnet route to the custom route table {#section_qjn_6no_zrf .section}

To add a subnet route entry to the created custom route table, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  Select the region of the VPC to which the created route table belongs.
3.  In the left-side navigation pane, click **Route Tables**.
4.  Find the target route table, click the route table ID, and then click the **Route Entry List** tab.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/161231/155731652845150_en-US.png)

5.  Click **Add Route Entry**.
6.  In the displayed dialog box, configure the subnet route entry according to the following information, and then click **OK**.

    |Configuration|Description|
    |:------------|:----------|
    |**Destination CIDR Block**|Specify the destination CIDR block of the traffic.     -   **IPv4 CIDR Block**: Forwards IPv4 traffic.
    -   **IPv6 CIDR Block**: Forwards IPv6 traffic.
 |
    |**Next Hop Type and Next Hop**|Select the type of the next hop.     -   **ECS Instance**: Directs the traffic from the destination CIDR block to a specified ECS instance.

This type of next hop is suitable for when you need to direct specific traffic to an ECS instance for centralized traffic forwarding and management \(for example, set an ECS instance as an Internet gateway to manage access of other ECS instances to the Internet\).

    -   **VPN Gateway**: Directs the traffic from the destination CIDR block to a specified VPN Gateway.

    -   **NAT Gateway**: Directs the traffic from the destination CIDR block to a specified NAT Gateway.

    -   **Secondary NetworkInterface**: Directs the traffic from the destination CIDR block to a specified secondary Elastic Network Interface \(ENI\).

    -   **Router Interface \(To VPC\)**: Directs the traffic from the destination CIDR block to a specified VPC.

This type of next hop is suitable for when you connect two VPCs by using Express Connect.

    -   **Router Interface \(To VBR\)**: Directs the traffic from the destination CIDR block to a router interface that is associated with the Virtual Border Router \(VBR\).

This type of next hop is suitable for when you connect your on-premises data center to a VPC by using Express Connect.

If you select **Router Interface \(To VBR\)**, you need to select a routing method.

        -   **General Routing**: Select a router interface that is associated with the VBR.

        -   **Active/Standby Routing**: Active/standby routing only supports up to two router interfaces for the next hop. The active router interface has a weight of 100, and the standby router interface has a weight of 0. If the active router interface fails health checks, the system switches to the standby router interface.

        -   **Load Balancing Routing**: You can select two to four router interfaces as the next hop. The peer ends of the selected router interfaces must be VBRs. Value range of the weights of the router interfaces: 1 to 255. Default value: 100. The weights of the selected router interfaces must be the same so that traffic can be evenly distributed to the router interfaces.

    -   **IPv6 Gateway**: Directs the traffic from the destination CIDR block to a specified IPv6 Gateway.

**Note:** This option is available only when the destination CIDR block is an IPv6 CIDR block.

 |


## Step 3: Associate the route table with a VSwitch {#section_x47_qsf_673 .section}

You can associate the created route table with a VSwitch \(subnet\) to control the traffic to and from this VSwitch. A VSwitch can be associated with only one route table, including system route tables. To associate the created custom route table with a VSwitch, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **Route Tables**.
3.  Select the region of the target custom route table.
4.  Find the route table and click the route table ID.
5.  Click the **Associated VSwitches** tab. Then, click **Associate VSwitch**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/161231/155731652845151_en-US.png)

6.  In the displayed dialog box, select the target VSwitch. Then, click **OK**.

