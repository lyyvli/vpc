# ClassicLink overview {#concept_q5z_kwb_sdb .concept}

VPC provides the ClassicLink function so that ECS instances of the classic network can communicate cloud resources in a VPC network through the intranet.

## Background {#section_jlf_pwb_sdb .section}

The basic implementation for the connection of classic networks with VPCs is the same as that of two classic networks. Therefore, when connecting a classic network to a VPC, the intranet latency and bandwidth limits remain unchanged. Moreover, operations, such as downtime migration, hot migration, stopping, starting, restarting, and system disk replacement will not change the link of a previously established ClassicLink.

The classic network and VPC network are two different network planes. ClassicLink establishes a private communication channel between these two network planes through routing. Therefore, to use the ClassicLink function, you must plan IP addresses properly to avoid IP address conflicts.

The IP address range used by classic networks in Alibaba Cloud is 10.0.0.0/8 \(excluding 10.111.0.0/16\). As long as the IP address range of a VPC does not conflict with 10.0.0.0/8, you can use ClassicLink to establish a private communication. VPC IP address ranges that can communicate with the classic network are 172.16.0.0/12, 10.111.0.0/16 and 192.168.0.0/16.

## Limits {#section_bbp_dzl_g2b .section}

Note the following before you use the ClassicLink function:

-   Up to 1,000 ECS instances of the classic network can be connected to the same VPC.

-   An ECS instance of the classic network can be connected to only one VPC, and the VPC must be under the same account and belong to the same region.

    For cross-account connection such as ones connecting an ECS instance under account A to a VPC under account B, you can transfer the ECS instance from account A to account B.

-   To enable the ClassicLink function of a VPC, the following conditions must be met:

|VPC CIDR block|Limitations|
|:-------------|:----------|
|172.16.0.0/12|There is no custom route entry destined for 10.0.0.0/8 in the VPC.|
|10.0.0.0/8| -   There is no custom route entry destined for 10.0.0.0/8 in the VPC.

-   Make sure that the CIDR block of the VSwitch to communicate with the ECS instance in the classic network is within 10.111.0.0/16.

 |
|192.168.0.0/16| -   There is no custom route entry destined for 10.0.0.0/8 in the VPC.

-   Add a route entry, of which the destination CIDR block is 192.168.0.0/16 and the next hop is the private NIC, to the ECS instance of the classic network. Download the [Route script](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/65402/jp_ja/1555405679409/route192.zip).

**Note:** Before running the script, read the readme file in the script carefully.

 |


## Connection scenarios {#section_mhc_gnt_g2b .section}

The following table lists the scenarios of connecting an ECS instance of a classic network to a VPC network.

|**Network type of the initiator**|**Region/account**|**Network type of the acceptor/intranet communication**|
|Classic network|VPC network|
|Classic network| Same region

 Same account

 |Add a same-account authorization rule in the security group.|Build a ClassicLink connection.|
| Same region

 Different accounts

 |Add a cross-account authorization rule in the security group.| -   Solution A:
    1.  Migrate the ECS instance of the classic network to the VPC network
    2.  Connect the VPCs
-   Solution B:
    1.  Transfer the ECS instance of the classic network to the account of the VPC
    2.  Build a ClassicLink connection

 |
| Different regions

 Same account

 | 1.  Migrate both ECS instances to the VPC network.
2.  Connect the two VPCs.

 | 1.  Migrate the initiator ECS instance to the VPC network.
2.  Connect the two VPCs.

 |
| Different regions

 Different accounts

 |
|VPC| Same region

 Same account

 |Build a ClassicLink connection|Connect the VPCs|
| Same region

 Different accounts

 | -   Solution A:
    1.  Migrate the ECS instance of the classic network to the VPC
    2.  Connect the VPCs
-   Solution B:
    1.  Migrate the ECS instance of the classic network to the account of the VPC.
    2.  Build a ClassicLink connection

 |
| Different regions

 Same account

 | 1.  Migrate the receiver ECS instance of the classic network to the VPC
2.  Connect the VPCs

 |
| Different regions

 Different accounts

 |

## Example scenario {#section_at5_swb_sdb .section}

After an ECS instance of the classic network is connected to a VPC through ClassicLink:

-   The ECS instance in the classic network can access cloud resources in the VPC.

    After a ClassicLink connection is successfully established, ECS instances in the classic network can access other cloud resources in the connected VPC \(such as other ECS, RDS, or SLB instances\). An real example may be that an ECS instance in the classic network is connected to a VPC of which the IP address range is 10.0.0.0/8, and the VPC has a VSwitch of which the IP address range is 10.111.1.0/24. If you have deployed cloud resources \(such as ECS and RDS instances\) in the VSwitch, then the ECS instance in the classic network can access these resources through ClassicLink.

-   After the ClassicLink connection is successfully established, ECS instances in the VPC can only access ECS instances in the classic network connected to the VPC and cannot access ECS instances or any other cloud resources in classic networks that are not connected to the VPC.


