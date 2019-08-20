# What is a VPC? {#concept_kbk_cpz_ndb .concept}

A VPC is a private network in Alibaba Cloud. You can specify the IP address range, configure route tables and gateways, and use Alibaba Cloud resources such as ECS, RDS, and SLB in your VPC.

  

Furthermore, you can connect your VPC to other VPCs or local networks to create a custom network environment. In this way, you can smoothly migrate applications to the cloud and extend on-premises data centers.

![VPC](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2427/1566296880805_en-US.png)

## Components {#section_w1b_tvz_ndb .section}

Each VPC consists of a private CIDR block, a VRouter, and one or more VSwitches.

![VPC components](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2427/15662968802749_en-US.png)

-   Private CIDR block

    When you create a VPC or a VSwitch, you must specify the private IP address range in the form of a CIDR block.

    You can use the standard private CIDR blocks listed in the following table and their subnets as CIDR blocks of your VPCs. For more information, see [Plan a VPC network](../../../../reseller.en-US/Quick Start/Plan a VPC network.md#).

    |CIDR block|Number of available private IP addresses \(excluding those reserved by the system\)|
    |:---------|:----------------------------------------------------------------------------------|
    |192.168.0.0/16|65,532|
    |172.16.0.0/12|1,048,572|
    |10.0.0.0/8|16,777,212|

-   VRouter

    A VRouter is a hub that connects all VSwitches in a VPC and serves as a gateway between the VPC and other networks. After a VPC is created, a VRouter is automatically created for the VPC. Each VRouter is associated with a route table.

    For more information, see [Route table overview](../../../../reseller.en-US/User Guide/Routes/Route table overview.md#).

-   VSwitch

    A VSwitch is a basic network device that connects different cloud resources in a VPC. After you create a VPC, you can create one or more subnets in the VPC by creating VSwitches. The VSwitches within a VPC are interconnected. You can deploy your applications on VSwitches that belong to different zones to improve service availability.

    For more information, see [Create a VSwitch](../../../../reseller.en-US/User Guide/VPC and subnets/Create a VSwitch.md#).


