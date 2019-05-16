# Add a custom route entry {#task_nks_lwn_4gb .task}

After a VPC is created, the system automatically creates a default route table and adds system routes to the route table to manage traffic. You cannot create or delete system routes, but you can create custom routes to direct traffic to specified destination CIDR blocks.

Each item in a route table is a route entry. A route entry specifies the destination of the traffic and consists of the destination CIDR block, next hop type, and next hop. Route entries include system routes and custom routes.

You can add custom routes to a system route table or a custom route table.

1.  Log on to the [专有网络控制台](https://vpcnext.console.aliyun.com)。
2.  Select the region to which the target VPC belongs.
3.  In the left-side navigation pane, select **Route Tables**.
4.  Click the ID of the target route table, and then click the **Route Entry List** tab page. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17037/15580107968671_en-US.png)

5.  Click **Add Route Entry**.
6.  In the displayed dialog box, configure the route entry according to the following information and click **OK**. 

    |Configuration|Description|
    |:------------|:----------|
    |**Destination CIDR Block**|The destination CIDR block.     -   **IPv4 CIDR Block**: Traffic is forwarded to an IPv4 address.
    -   **IPv6 CIDR Block**: Traffic is forwarded to an IPv6 address.
 |
    |**Next Hop Type and Next Hop**|Select the next hop type:     -   **ECS Instance**: Direct the traffic pointing to the destination CIDR block to the selected ECS instance.

Select this type when you want to direct the specifed traffic to an ECS instance to uniformly forward and manage the traffic. For example, configure an ECS instance as an Internet gateway to manage the access of other ECS instances to the Internet.

    -   **VPN Gateway**: Direct the traffic pointing to the destination CIDR block to the selected VPN Gateway.

    -   **NAT Gateway**: Direct the traffic pointing to the destination CIDR block to the selected NAT Gateway.

    -   **Secondary NetworkInterface**: Direct the traffic pointing to the destination CIDR block to the selected secondary ENI.

    -   **Router Interface \(To VPC\)**: Direct the traffic pointing to the destination CIDR block to the selected VPC.

Select this type when you want to use Express Connect to connect VPCs.

    -   **Router Interface \(To VBR\)**: Direct the traffic pointing to the destination CIDR block to the router interface associated with the VBR.

Select this type when you want to use Express Connect to connect a VPC to an on-premises data center.

In this mode, you also need to select the route type:

        -   **General Routing**: Select any associated router interface.

        -   **Active/Standby Routing**: You can use only two instances as the next hops, one that is designated as active, the other as standby. The active route is weighted at 100, and the standby route at 0. When the active route is declared as unhealthy, the standby route replaces the active route.

        -   **Load Balancing Routing**: You need to use two to four router interfaces as the next hops and the peer routers of the next hops must be VBRs. Valid values of the router interface weight are from 1 to 255, and the default router interface weight is 100. The weight of each router interface must be the same. The system evenly allocates traffic to next-hop router interfaces.

    -   **IPv6 Gateway**: Direct traffic pointing to the destination IDR block to the selected IPv6 Gateway instance.

**Note:** This option is available only when the destination CIDR block is an IPv6 CIDR block.

 |


