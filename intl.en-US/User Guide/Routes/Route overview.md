# Route overview {#concept_qbk_bvn_4gb .concept}

After a VPC is created, the system automatically creates a default route table and adds system routes to it to manage traffic. You cannot create or delete system routes. However, you can create custom routes to route traffic to the destination CIDR block.

## Route tables {#section_rmh_4nb_r2b .section}

After a VPC is created, the system creates a default route table to control routes of the VPC and all VSwitches in the VPC use the route table by default. You cannot create or delete the default route table. However, you can create a custom route table and attach it to the VSwitch to control the routes of the subnet.

A route entry specifies the destination of the traffic and consists of the destination CIDR block, the next hop type, and the next hop. Route entries include system route entries and custom route entries.

Note the following when managing route tables:

-   Each VPC can contain up to ten route tables. This number includes the system route table.
-   Each VSwitch can be attached to only one route table. The routes of a VSwitch \(subnet\) are managed by the associated route table.
-   After a VSwitch is created, it is automatically attached to the system route table.
-   To change a custom route table attached to a VSwitch to a system route table, detach the custom route table from the VSwitch. To attach the VSwitch to another route table, detach the current route table from the VSwitch and then attach the VSwitch to the target custom route table.
-   Currently, all regions except China \(Beijing\), China \(Shenzhen\), and China \(Hangzhou\) support custom route tables.
-   Cutom route tables do not support active/standby routes and load balancing routes.

## System routes {#section_hcs_tly_rdb .section}

After a VPC is created, the system automatically adds the following system routes to the route table:

-   The route entry whose destination CIDR block is 100.64.0.0/10. It is used for cloud product communication within the VPC.
-   The route entry whose destination CIDR block is the CIDR block of the VSwitch. It is used for cloud product communication within the VSwitch.

## Custom routes {#section_d44_4my_rdb .section}

You can add custom route entries to replace system route entries or route traffic to a specified destination. You can specify the following next hop types when creating a custom route entry:

-   ECS instance: Route the traffic pointing to the destination CIDR block to an ECS instance in the VPC.

    Select this type when you want to access the Internet or other applications through the application deployed on the ECS instance.

-   VPN Gateway: Route the traffic pointing to the destination CIDR block to a VPN Gateway.

    Select this type when you want to connect to another VPC or an on-premises data center through VPN Gateway.

-   Router Interface \(To VPC\): Route the traffic pointing to the destination CIDR block to a VPC.

    Select this type when you want to connect two VPCs through router interfaces of Express Connect.

-   Router Interface \(To VBR\): Route the traffic pointing to the destination CIDR block to a VBR.

    Select this type when you want to connect a VPC to a local data center through Express Connect \(physical access\).

-   Secondary ENI: Route the traffic pointing to the destination CIDR block to a secondary ENI.


## IPv6 routes {#section_efr_nys_dgb .section}

If your VPC has enabled IPv6, the following route entries will be automatically added to the system route table of the VPC:

-   The custom route entry \(whose destination CIDR block is ::/0 and whose next hop is the IPv6 Gateway\) is used for communicating with the Internet within a VPC through IPv6 addresses.

-   The system route entry \(whose destination CIDR block is the IPv6 CIDR block of the VSwitch\) is used for communication within aVSwitch.

    **说明：** If you have created a custom route table and attached it to a VSwitch with IPv6 CIDR block enabled, you must maunally add a custom route entry whose the destination CIDR block is ::/0 and the next hop is the IPv6 Gateway instance.


## Routing rules {#section_dq3_3ny_rdb .section}

The longest prefix match is used to route traffic when more than one route entries match the destination CIDR block. The route entry with the longest subnet mask \(the most specific route\) is used.

The route table of a VPC is as follows:

|Destination CIDR block|Next hop type|Next hop|Route entry type|
|:---------------------|:------------|:-------|:---------------|
|100.64.0.0/10|-|-|System|
|192.168.0.0/24|-|-|System|
|0.0.0.0/0|Instance|i-12345678|Custom|
|10.0.0.0/24|Instance|i-87654321|Custom|

The route entries destined for `100.64.0.0/10` and `192.168.0.0/24` CIDR blocks are system route entries. The route entries destined for the `0.0.0.0/0` and `10.0.0.0/24` CIDR blocks are custom route entries. Traffic destined for `0.0.0.0/0` will be routed to the ECS instance `i-12345678`, and traffic destined for `10.0.0.0/24` will be routed to the ECS instance `i-87654321`. According to the longest prefix match algorithm, traffic destined for `10.0.0.1` will be routed to the ECS instance `i-87654321`, and traffic destined for `10.0.1.1` will be routed to the ECS instance `i-12345678`.

## Routing examples {#section_eh3_vny_rdb .section}

You can add custom route entries to the route table to control traffic.

-   Routing within a VPC

    As shown in the following figure, a self-built NAT Gateway is deployed on an ECS instance \(ECS01\) in a VPC. To enable cloud resources in the VPC to access the Internet through this ECS instance, add the following route entry to the route table:

    |Destination CIDR block|Next hop type|Next hop|
    |:---------------------|:------------|:-------|
    |0.0.0.0/0|ECS instance|ECS01|

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/120612/155479986638745_en-US.png)

-   Connect VPCs \(Express Connect\)

    As shown in the following figure, when using Express Connect to connect VPC 1 \(172.16.0.0/12\) and VPC 2 \(192.168.0.0/16\), you must add the following route entries in the VPCs after creating route interfaces:

    -   Route entry added to VPC1

        |Destination CIDR block|Next hop type|Next hop|
        |:---------------------|:------------|:-------|
        |192.168.0.0/16|Router interface \(To VPC\)|VPC2|

    -   Route entry added to VPC2

        |Destination CIDR block|Next hop type|Next hop|
        |:---------------------|:------------|:-------|
        |172.16.0.0/12|Router interface \(To VPC\)|VPC1|

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/120612/155479986638746_en-US.png)


-   Connect VPCs

    As shown in the following figure, when using VPN Gateway to connect VPC 1 \(172.16.0.0/12\) and VPC 2 \(10.0.0.0/8\), you must add the following route entries in the VPCs after configuring VPN Gateway:

    -   Route entry added to VPC 1

        |Destination CIDR block|Next hop type|Next hop|
        |:---------------------|:------------|:-------|
        |10.0.0.0/8|VPN Gateway|VPN Gateway 1|

    -   Route entry added to VPC 2

        |Destination CIDR block|Next hop type|Next hop|
        |:---------------------|:------------|:-------|
        |172.16.0.0/12|VPN Gateway|VPN Gateway 2|

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/120612/155479986638748_en-US.png)

-   Connect a VPC to a local data center \(Express Connect\)

    As shown in the following figure, when using Express Connect to connect a VPC to a local data center, you must add the following route entries after configuring the leased line and the VBR:

    -   Route entry added to VPC

        |Destination CIDR block|Next hop type|Next hop|
        |:---------------------|:------------|:-------|
        |192.168.0.0/16|Router interface \(To VBR/General Routing\)|Router interface \(RI 1\)|

    -   Route entry added to VBR

        |Destination CIDR block|Next hop type|Next hop|
        |:---------------------|:------------|:-------|
        |192.168.0.0/16|To leased line|Router interface \(RI 3\)|
        |172.16.0.0/12|To VPC|Router interface \(RI 2\)|

    -   Route entry added to the local network

        |Destination CIDR block|Next hop type|Next hop|
        |:---------------------|:------------|:-------|
        |172.16.0.0/12|—|Local gateway device|

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/120612/155479986638749_en-US.png)

-   Connect a VPC to a local data center \(VPN Gateway\)

    As shown in the following figure, when using a VPN Gateway to connect a VPC \(172.16.0.0/12\) to a local network \(92.168.0.0/16\), you must add the following route entry to the VPC:

    |Destination CIDR block|Next hop type|Next hop|
    |:---------------------|:------------|:-------|
    |192.168.0.0/16|VPN Gateway|The created VPN Gateway|

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/120612/155479986638750_en-US.png)


