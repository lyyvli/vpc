# Add a subnet route to a route table {#concept_187313 .concept}

You can create a custom route table in a VPC and add subnet routes to the created custom route table. Then, you can associate the route table with a VSwitch to control the traffic to and from the VSwitch.

## Prerequisites {#section_bwg_vwq_gcm .section}

A VPC and a VSwitch are created. For more information, see [Manage a VPC](reseller.en-US/User Guide/VPC and subnets/Manage a VPC.md#).

## Limits {#section_pp4_w5m_1as .section}

Note the following limits before you add subnet routes to a route table:

-   You can create up to 10 route tables in a VPC, including system route tables.
-   Each VSwitch can be associated with only one route table.
-   Active/standby routes and load balancing routes are not supported by custom route tables.
-   Currently, custom route tables are available in all regions except for China \(Beijing\), China \(Hangzhou\), and China \(Shenzhen\).

## Step 1: Create a custom route table {#section_ate_8wr_8xn .section}

To create a custom route table, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, click **Route Tables**.
3.  Select a region.
4.  On the Route Tables page, click **Create Route Table**.
5.  On the Create Route Table page, configure the route table according to the following information, and click **OK**.

    |Configuration|Description|
    |:------------|:----------|
    |**Name**|Enter a name for the route table. The name must be 2 to 128 characters in length and can contain letters, numbers, underscores \(\_\), and hyphens \(-\). The name must start with a letter.

 |
    |**VPC**|Select a VPC to which the route table belongs.|
    |**Description**|Enter a description for the route table. The description must be 2 to 256 characters in length and cannot start with `http://` or `https://`.

 |


## Step 2: Add a subnet route to the custom route table {#section_qjn_6no_zrf .section}

To add a subnet route entry to the created custom route table, follow these steps:

1.  In the left-side navigation pane, click **Route Tables**.
2.  On the Route Tables page, find the target route table and click **Manage** in the **Actions** column.
3.  On the Route Entry List tab, click **Add Route Entry**.
4.  On the Add Route Entry page, configure the subnet route entry according to the following information, and click **OK**.

    |Configuration|Description|
    |:------------|:----------|
    |**Destination CIDR Block**|Specify the destination CIDR block of the traffic.     -   **IPv4 CIDR Block**: Directs the traffic to an IPv4 address.
    -   **IPv6 CIDR Block**: Directs the traffic to an IPv6 address.
 |
    |**Next Hop Type and Next Hop**|Select the type of the next hop.     -   **ECS Instance**: Directs the traffic to a specified ECS instance.

This type of next hop is suitable for when you need to direct specific traffic to an ECS instance for centralized traffic forwarding and management \(for example, set an ECS instance as an Internet gateway to manage access of other ECS instances to the Internet\).

    -   **VPN Gateway**: Directs the traffic to a specified VPN Gateway.
    -   **VPN Gateway**: Directs the traffic to a specified NAT Gateway.
    -   **Secondary NetworkInterface**: Directs the traffic to a specified secondary Elastic Network Interface \(ENI\).
    -   **Router Interface \(To VPC\)**: Directs the traffic to a specified VPC.

This type of next hop is suitable for when you connect two VPCs by using Express Connect.

    -   **Router Interface \(To VBR\)**: Directs the traffic to a router interface that is associated with the Virtual Border Router \(VBR\).

This type of next hop is suitable for when you connect your on-premises data center to a VPC by using Express Connect.

You need to further select a routing method when this type is selected:

        -   **General Routing**: Select a router interface that is associated with the VBR.
        -   **Active/Standby Routing**: Active/standby routing only supports up to two router interfaces for the next hop. The active router interface has a weight of 100, and the standby router interface has a weight of 0. If the active router interface fails health checks, the system switches to the standby router interface.
        -   **Load Balancing Routing**: You can select two to four router interfaces as the next hop. The peer ends of the selected router interfaces must be VBRs. Value range of the weights of the router interfaces: 1 to 255. Default value: 100. The weights of the selected router interfaces must be the same so that traffic can be evenly distributed to the router interfaces.
    -   **IPv6 Gateway**: Directs the traffic to a specified IPv6 Gateway.

**Note:** This option is available only when the destination CIDR block is an IPv6 CIDR block.

 |

    For more information, see [Routing examples](reseller.en-US/User Guide/Routes/Route overview.md#section_eh3_vny_rdb).


## Step 3: Associate the route table with a VSwitch {#section_x47_qsf_673 .section}

You can associate the created route table with a VSwitch \(subnet\) to control the traffic to and from this VSwitch. A VSwitch can be associated with only one route table, including system route tables. To associate the created custom route table with a VSwitch, follow these steps:

1.  In the left-side navigation pane, click **Route Tables**.
2.  On the Route Tables page, find the target route table and click **Manage** in the **Actions** column.
3.  Click the **Associated VSwitches** tab, and then click **Associate VSwitch**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17037/15619452958675_en-US.png)

4.  On the Associate VSwitch page, select the VSwitch to associate and click **OK**.

