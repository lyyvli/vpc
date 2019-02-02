# Routing {#concept_zkv_dxx_rdb .concept}

Alibaba Cloud automatically creates a default route table and adds system route entries to it after you create a VPC. You cannot create system route entries, nor delete system route entries, but you can create custom route entries to override system route entries, routing the traffic from specific IP address to the specified destination.

You can add custom route entries to both system route tables and custom route tables. For more information about route tables, see [Route table](reseller.en-US/User Guide/Routes/Route table.md#).

Each entry in the route table is a route entry. A route entry defines the next hop of the network traffic destined for a specific IP address. Route entries include system route entries and custom route entries.

## System route entries {#section_hcs_tly_rdb .section}

The following system route entries are added to the route table after you create a VPC.

-   A route entry destined for 100.64.0.0/10. It is used for cloud resource communication in the VPC.
-   A route entry destined for the IP address range of a VSwitch. It is used for cloud resource communication in the VSwitch.

For example, you have created a VPC with the IP address range of 192.168.0.0/16, and two VSwitches with the IP address ranges of 192.168.1.0/24 and 192.168.0.0/24. The following system route entries are automatically added to the route table of the VPC:

|CIDR Block|Next Hop Type|Type|
|:---------|:------------|:---|
|100.64.0.0/10|-|System|
|192.168.1.0/24|-|System|
|192.168.0.0/24|-|System|

## Custom route entries {#section_d44_4my_rdb .section}

You can add custom route entries to override system route entries or route traffic destined for specific IP address range to a target destination. You can specify the following next hop types when creating a custom route entry:

-   ECS instance: route traffic destined for a specific IP address range to an ECS instance in the VPC.

    Select this type when you want to access the Internet through the application deployed on the ECS instance.

-   VPN Gateway: Route traffic destined for a specific IP address range to a VPN Gateway.

    Select this type when you want to connect to a VPC or a local IDC through the VPN Gateway.

-   Router Interface \(To VPC\): Route traffic destined for a specific IP address range to a VPC.

    Select this type when you want to connect two VPCs through router interfaces of Express Connect.

-   Router Interface \(To VBR\): Route traffic destined for a specific IP address range to a VBR.

    Select this type when you want to connect to a local IDC through a dedicated connection of Express Connect.

-   Secondary ENI: Route traffic destined for a specific IP address range to a secondary ENI.


## Routing rules {#section_dq3_3ny_rdb .section}

The longest prefix match algorithm is used to route traffic when more than one route entries match the destination IP address range. The route entry with the longest subnet mask \(the most specific route\) is used.

Here is an example of a route table of a VPC.

|Destination CIDR block|Next hop type|Next hop|Type|
|:---------------------|:------------|:-------|:---|
|100.64.0.0/10|-|-|System|
|192.168.0.0/24|-|-|System|
|0.0.0.0/0|ECS instance|i-12345678|Custom|
|10.0.0.0/24|ECS instance|i-87654321|Custom|

The route entries with the destination of `100.64.0.0/10` and `192.168.0.0/24` are system route entries. The route entries with the destination of`0.0.0.0/0` and `10.0.0.0/24` are custom route entries. Traffic destined for `0.0.0.0/0` will be routed to the ECS instance `i-12345678`, and traffic destined for `10.0.0.0/24` will be routed to the ECS instance `i-87654321`. According to the longest prefix match algorithm, traffic destined for `10.0.0.1` will be routed to the ECS instance `i-87654321`, while traffic destined for `10.0.1.1` will be routed to the ECS instance `i-12345678`.

## Routing examples {#section_eh3_vny_rdb .section}

-   Routing within a VPC

    As shown in the following figure, a self-built NAT gateway is deployed on an ECS instance \(ECS01\), add the following route entry to the route table if you want other ECS instances to access the Internet through this ECS instance:

    |Destination CIDR block|Next hop type|Next hop type|
    |:---------------------|:------------|:------------|
    |0.0.0.0/0|ECS instance|ECS01|

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2437/1549094806810_en-US.png)

-   VPC interconnection \(Express Connect\)

    As shown in the following figure, when using Express Connect to connect VPC 1 \(172.16.0.0/12\) and VPC 2 \(192.168.0.0/16\), you must add the following route entries in the VPC after creating route interfaces:

    -   Custom route entry added in VPC1

        |Destination CIDR block|Next hop type|Next hop|
        |:---------------------|:------------|:-------|
        |192.168.0.0/16|Router interface \(To VPC\)|VPC 2|

    -   Custom route entry added in VPC2

        |Destination CIDR block|Next hop type|Next hop|
        |:---------------------|:------------|:-------|
        |172.16.0.0/12|Router interface \(To VPC\)|VPC 1|

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2437/1549094806811_en-US.png)


-   VPC interconnection \(VPN Gateway\)

    As shown in the following figure, when using Express Connect to connect VPC 1 \(172.16.0.0/12\) and VPC 2 \(10.0.0.0/8\), you must add the following route entries in the VPC after configuring VPN Gateway:

    -   Custom route entry added in VPC 1

        |Destination CIDR block|Next hop type|Next hop|
        |:---------------------|:------------|:-------|
        |10.0.0.0/8|VPN metric reference|VPN Gateway 1|

    -   Custom route entry added in VPC 2

        |Destination CIDR block|Next hop type|Next hop|
        |:---------------------|:------------|:-------|
        |172.16.0.0/12|VPN metric reference|VPN Gateway 2|

-   Local IDC connection \(Express Connect\)

    As shown in the following figure, when using Express Connect to connect a VPC to a local network, you must add the following route entries after configuring the leased line and the VBR:

    -   Custom route entry added in VPC

        |Destination CIDR block|Next hop type|Next hop|
        |:---------------------|:------------|:-------|
        |192.168.0.0/16|Router interface \(To VBR/General Routing\)|Router interface \(RI 1\)|

    -   Custom route entry added in VBR

        |Destination CIDR block|Next hop type|Next hop|
        |:---------------------|:------------|:-------|
        |192.168.0.0/16|To leased line|Router interface \(RI 3\)|
        |172.16.0.0/12|To VPC|Router interface \(RI 2\)|

    -   Custom route entry added in the local network

        |Destination CIDR block|Next hop type|Next hop|
        |:---------------------|:------------|:-------|
        |172.16.0.0/12|—|Local gateway|

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2437/15490948066425_en-US.png)

-   Local connection \(VPN Gateway\)

    As shown in the following figure, when using a VPN Gateway to connect a VPC \(172.16.0.0/12\) to a local network \(92.168.0.0/16\), you must add the following custom route entries:

    |Destination CIDR block|Next hop type|Next hop|
    |:---------------------|:------------|:-------|
    |192.168.0.0/16|VPN metric reference|VPN Gateway|

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2437/1549094806814_en-US.png)


## Add custom route entry {#section_k5r_n5y_rdb .section}

To add a custom route entry, complete these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  Select the region of the VPC.
3.  In the left-side navigation pane, click **Route Tables**.
4.  Click the ID of the target route table, and then click the **Route Entry List** tab.
5.  Click **Add Route Entry**.
6.  In the displayed dialog box, configure the route entry according to the following information and click **OK**.

    |Configuration|Description|
    |:------------|:----------|
    |**Destination CIDR Block**|The traffic from which IP address range to route.|
    |**Next hop type and next hop**|Select the next hop type and the corresponding next hop:    -   **ECS Instance**: Route the traffic destined for the specified IP address range to the selected ECS instance.

Applicable to the scenario where traffic destined for the specified network is routed to an ECS instance for unified traffic forwarding and management. For example, configure an ECS instance as an Internet gateway to control the Internet access for other ECS instances.

    -   **VPN Gateway**: Route the traffic destined for the specified IP address range to the selected VPN Gateway.

    -   **Secondary ENI**: Route the traffic destined for the specified IP address range to the selected secondary ENI.

    -   **Router Interface \(To VPC\)**: Route the traffic destined for the specified IP address range to the selected VPC.

Applicable to the scenario where Express Connect is used to connect VPCs.

    -   **Router Interface \(To VBR\)**: Route the traffic destined for the specified IP address range to the selected router interface of which the peer router interface is a VBR.

Applicable to the scenario where Express Connect is used to connect a VPC to a local IDC.

You need to further select a routing method when this type is selected:

        -   **General Routing**: Route the traffic to the specified route interface.

        -   **Active/Standby Routing**: Choose two router interfaces as the next hop. The weight for the active route entry is 100 and for the standby route entry is 0. The standby route entry takes over traffic routing when the health check for the active route entry fails.

        -   **Load Balancing Routing**: Choose at least two router interfaces or four router interfaces at most as the next hop. Set a weight value between 1 and 255 for each added route interface. The default value is 100. The weights must be identical. Therefore, the system will distribute the traffic evenly among these router interfaces.

|


