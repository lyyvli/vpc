# Plan a VPC network {#concept_dvk_lj5_sdb .concept}

Before you create VPCs and VSwitches, you must plan the quantity and CIDR block of VPCs and VSwitches according to your specific business needs.

A VPC is a private network in Alibaba Cloud. VPCs are logically isolated from each other. VPCs have the following characteristics:

-   Isolated network environment

    Based on the tunneling technique, VPC isolates the data link layer and provides an independent, isolated, and safe network. VPCs cannot communicate with each other unless they are interconnected through an EIP or a NAT IP address.

-   Controllable network configurations

    You can specify its IP address range or configure route tables and gateways for secure and easy access to resources. Furthermore, you can connect your VPC to a traditional data center through a leased line or VPN to create a custom network environment. This allows you to smoothly migrate your applications to Alibaba Cloud and expand your data center.

    For more information, see [Virtual Private Cloud](https://www.aliyun.com/product/vpc?spm=5176.8142029.388261.75.NcXndU).


To use a VPC, you must first plan a VPC network. We recommend that you consider the following questions:

-   [Question 1: How many VPCs are required?](reseller.en-US/Quick Start/Plan a VPC network.md#section_ocz_5j5_sdb)

-   [Question 2: How many VSwitches are required?](reseller.en-US/Quick Start/Plan a VPC network.md#section_ak2_sm5_sdb)

-   [Question 3: How do I specify the private IP address range?](reseller.en-US/Quick Start/Plan a VPC network.md#section_yzq_tm5_sdb)

-   [Question 4: How do I specify the private IP address range if I need to connect a VPC to other VPCs or on-premises data centers?](reseller.en-US/Quick Start/Plan a VPC network.md#section_wn4_tm5_sdb)


## Question 1: How many VPCs are required? {#section_ocz_5j5_sdb .section}

-   One VPC

    We recommend that you create one VPC if you do not need to deploy your business systems in multiple regions or isolate these systems by using VPCs. Currently, a VPC can accommodate up to 15,000 cloud product instances.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2447/1566265661821_en-US.jpg)

-   Multiple VPCs

    We recommend that you create multiple VPCs if you need to:

    -   Deploy your business systems in multiple regions.

        VPCs are resources that cannot be deployed across regions. If you want to deploy your business systems in different regions, you must create multiple VPCs. You can use Express Connect, VPN Gateway, and CEN to connect VPCs.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2447/1566265661822_en-US.jpg)

    -   Isolate multiple business systems.

        To isolate multiple business systems, for example, isolate the production environment from the test environment, you must create multiple VPCs, as shown in the following figure.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2447/1566265661824_en-US.jpg)


## Question 2: How many VSwitches are required? {#section_ak2_sm5_sdb .section}

We recommend that you create at least two VSwitches for each VPC and deploy them in two different zones for cross-region disaster tolerance.

We also recommend that you check the network latency between different zones in the same region after you deploy your business systems. This is because the network latency may be higher than expected due to complicated system calls or cross-zone calls. We recommend that you optimize and adjust your systems accordingly to keep a balance between high availability and low latency.

The number of VSwitches used also relates to the system size and system planning. If your front-end systems can be accessed by the Internet and you want them to access the Internet, you can deploy these systems under different VSwitches. At the same time, you can deploy the backend system in other VSwitches. This helps provide better disaster tolerance.

## Question 3: How do I specify the private IP address range? {#section_yzq_tm5_sdb .section}

When you create VPCs and VSwitches, you must specify the private IP address range for these VPCs in the form of a Classless Inter-Domain Routing \(CIDR\) block.

-   Private IP address range of VPCs

    You can use 192.168.0.0/16, 172.16.0.0/12, 10.0.0.0/8, or their subsets as the private IP address range for your VPC. When you plan the private IP address range of your VPC, note the following:

    -   If you have only one VPC and it does not need to communicate with on-premises data centers, you can use any of the preceding IP address ranges or their subnets.
    -   If you have multiple VPCs, or you want to build a hybrid cloud consisting of VPCs and on-premises data centers, you can use a subset of the preceding IP address ranges as the IP address range for your VPC. In this case, the netmask cannot be longer than 16 bits.
    -   You also need to consider whether a classic network is used when you select a CIDR block for your VPC. If you plan to connect ECS instances in a classic network with your VPC, we recommend that you do not use the IP address range 10.0.0.0/8. This is because the IP address range is also used by the classic network.
-   Private IP address range of VSwitches

    A VSwitch can share the same IP address range with the VPC that the VSwitch belongs to. The VSwitch can also use a subnet of the IP address range of the VPC. For example, if the IP address range of the VPC is 192.168.0.0/16, the IP address range of the VSwitch can be 192.168.0.0/16, or any IP address range between 192.168.0.0/17 and 192.168.0.0/29.

    When you plan the IP address range of a VSwitch, note the following:

    -   The block size for a VSwitch is between a 16-bit netmask and a 29-bit netmask. It means that 8 to 65,536 IP addresses can be provided. This range is set because the 16-bit netmask can provide IP addresses to support 65,532 ECS instances, while a netmask smaller than 29 bits cannot provide sufficient IP addresses.
    -   The first IP address and the last three IP addresses of each VSwitch are reserved by the system. For example, if the CIDR block of a VSwitch is 192.168.1.0/24, the IP addresses 192.168.1.0, 192.168.1.253, 192.168.1.254, and 192.168.1.255 are reserved.
    -   The ClassicLink function allows ECS instances in a classic network to communicate with ECS instances in a VPC whose CIDR blocks are 192.168.0.0/16, 10.0.0.0/8, and 172.16.0.0/12. For example, if you want to connect an ECS instance of a VSwitch in a VPC to an ECS instance in the classic network, and the IP address range of the VPC is 10.0.0.0/8, then the IP address range of the VSwitch must be 10.111.0.0/16. For more information, see [ClassicLink overview](../../../../reseller.en-US/User Guide/Network connection/ClassicLink/ClassicLink overview.md#).
    -   When you plan the IP address range of a VSwitch, you need to consider the number of ECS instances in the VSwitch.

## Question 4: How do I specify the private IP address range if I need to connect a VPC to other VPCs or on-premises data centers? {#section_wn4_tm5_sdb .section}

To connect a VPC to other VPCs or on-premises data centers, make sure that the CIDR block of the VPC does not conflict with that of the target network.

For example, you have three VPCs: VPC1 in China \(Hangzhou\), VPC2 in China \(Shanghai\), and VPC3 in China \(Beijing\), as shown in the following figure. VPC1 and VPC2 can communicate with each other through Express Connect. VPC3 does not need to communicate with VPC1 or VPC2 currently, but may need to communicate with VPC2 later. Additionally, you have an on-premises data center in Shanghai, and you need to connect it to VPC1 by using the physical connection of Express Connect.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2447/1566265662825_en-US.jpg)

In this example, the CIDR blocks of VPC1 and VPC2 are different, but the CIDR blocks of VPC2 and VPC3 are the same. This is because VPC3 does not need to communicate with VPC1 or VPC2 currently. However, the VSwitches in VPC2 and VPC3 use different CIDR blocks so that these two VPCs can communicate with each other in future. VPCs that need to communicate with each other can have the same CIDR block, but their VSwitches cannot have the same CIDR block.

When you specify the IP address range for multiple VPCs to allow them to communicate with other VPCs or on-premises data centers, follow these rules:

-   Try to specify different IP address ranges for different VPCs. You can use the subsets of the standard IP address ranges to increase the number of available VPC CIDR blocks.
-   If you cannot specify different IP address ranges for different VPCs, try to use different CIDR blocks for VSwitches of different VPCs.
-   If you cannot use different CIDR blocks for VSwitches of different VPCs, make sure that the VSwitches that need to communicate with each other use different CIDR blocks.

