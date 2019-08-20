# Add a subnet route to a custom route table {#task_1512598 .task}

This topic describes how to add a subnet route to a custom route table. After you add a subnet route to a custom route table, you can associate the custom route table with a VSwitch to control the flow of traffic to and from the VSwitch.

A VPC is created. For more information, see [Create a VPC](reseller.en-US/VPCs and VSwitches/VPC management/Create a VPC.md#).

## Limits {#section_r3m_ki1_1p7 .section}

Before you add a subnet route to a route table, note the following limits:

-   You can only create up to 10 route tables in each VPC, including system route tables.
-   Each VSwitch can be associated with only one route table.
-   Active/standby routes and load balancing routes are not supported by custom route tables.
-   Custom route tables are supported in all regions except China \(Beijing\), China \(Shenzhen\), and China \(Hangzhou\).

## Step 1: Create a custom route table {#section_50v_jf3_myz .section}

To create a custom route table, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **Route Tables**.
3.  Select the region of the route table to be created.
4.  On the Route Tables page, click **Create Route Table**.
5.  On the Create Route Table page, set the parameters, and then click **OK**. The following table describes the parameters. 

    |Configuration|Description|
    |-------------|-----------|
    |**Resource Group**|Select the resource group to which the route table belongs.|
    |**VPC**|Select the VPC to which the route table belongs.|
    |**Name**|Enter a name for the route table. The name must be 2 to 128 characters in length and can contain letters, numbers, underscores \(\_\), and hyphens \(-\). It must start with a letter.

 |
    |**Description**|Enter a description for the route table. The description must be 2 to 256 characters in length and cannot start with `http://` or `https://`.

 |

    After you create a custom route table, you can view it in the list of route tables whose **Route Table Type** is **Custom** on the Route Tables page.

    ![Custom route table](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17037/15663170418671_en-US.png)


## Step 2: Add a subnet route to the custom route table {#section_bnr_cvp_rmd .section}

To add a subnet route to the custom route table, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **Route Tables**.
3.  Select the region to which the target route table belongs.
4.  On the Route Tables page, find the target route table, and then click **Manage** in the **Actions** column.
5.  In the Route Table Details area, click **Route Entry List** tab, and then click **Add Route Entry**.
6.  On the Add Route Entry page, set the parameters, and then click **OK**. The following table describes the parameters. 

    |Configuration|Description|
    |:------------|:----------|
    |**Name**|Enter the name of the route entry. The name must be 2 to 128 characters in length and can contain letters, numbers, hyphens \(-\), and underscores \(\_\). It must start with a letter.

 |
    |**Destination CIDR Block**|Specify the destination CIDR block.     -   **IPv4 CIDR Block**: Traffic is forwarded to an IPv4 address.
    -   **IPv6 CIDR Block**: Traffic is forwarded to an IPv6 address.
 |
    |**Next Hop Type**|Select the type of the next hop. Options:     -   **ECS Instance**: Traffic pointing to the destination CIDR block is routed to the selected ECS instance.

Select this type if you want to route specified traffic to an ECS instance for uniform forwarding and management. For example, configure an ECS instance as an Internet gateway to manage the access of other ECS instances to the Internet.

    -   **VPN Gateway**: Traffic pointing to the destination CIDR block is routed to the selected VPN Gateway.
    -   **NAT Gateway**: Traffic pointing to the destination CIDR block is routed to the selected NAT Gateway.
    -   **Secondary Network Interface**: Traffic pointing to the destination CIDR block is routed to the selected secondary Elastic Network Interface \(ENI\).
    -   **Router Interface \(To VPC\)**: Traffic pointing to the destination CIDR block is routed to the selected VPC.

Select this type if you want to use Express Connect to connect two VPCs.

    -   **Router Interface \(To VBR\)**: Traffic pointing to the destination CIDR block is routed to the router interface associated with the VBR.

Select this type if you want to use Express Connect to connect a VPC to an on-premises data center.

In this mode, you must select one of the following route types:

        -   **General Routing**: Select an associated router interface.
        -   **Active/Standby Routing**: You can use only two instances as the next hops. One is active, the other is standby. The active route is weighted 100 and the standby route is weighted 0. If the active route is detected unhealthy, the standby route replaces the active route.
        -   **Load Balancing Routing**: You need to use two to four router interfaces as the next hops, and the peer routers of the next hops must be VBRs. Valid values of the router interface weight are from 1 to 255, and the default router interface weight is 100. The weights of the selected router interfaces must be the same so that traffic can be evenly distributed to the next-hop router interfaces.
    -   **IPv6 Gateway**: Traffic pointing to the destination CIDR block is routed to the selected IPv6 Gateway.

**Note:** This option is available only when the destination CIDR block is an IPv6 CIDR block.

 |
    |**Resource Group**|Select the resource group to which the next hop belongs.|
    |**ECS Instance/HAVip Address/VPN Gateway/NAT Gateway/Secondary Network Interface/VPC**|Select the next-hop instance.|


## Step 3: Associate the route table with a VSwitch {#section_48i_3db_q50 .section}

You can associate the route table with a VSwitch \(subnet\) to control the flow of traffic to and from the VSwitch. Each VSwitch can be associated with only one custom route table or system route table. To associate the custom route table with a VSwitch, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **Route Tables**.
3.  Select the region to which the target route table belongs.
4.  On the Route Tables page, find the target route table, and then click **Manage** in the **Actions** column.
5.  In the Route Table Details area, click the **Associated VSwitches** tab, and then click **Associate VSwitch**.
6.  On the Associate VSwitch page, select the target VSwitch, and then click **OK**.

