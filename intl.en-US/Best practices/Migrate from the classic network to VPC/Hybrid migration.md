# Hybrid migration {#concept_u32_ycv_sdb .concept}

This topic describes how to use the hybrid migration solution to migrate cloud resources from a classic network to a VPC.

## Prerequisites {#section_rtn_bdv_sdb .section}

Before the hybrid migration, make sure that:

-   You are aware of the limits of the hybrid migration solution. For more information, see [Migration overview](reseller.en-US/Best practices/Migrate from the classic network to VPC/Migration overview.md#).

-   You are familiar with VPCs and the related products. VPCs are isolated private networks that allow you to manage your cloud resources by using relevant cloud products.

-   You conduct an assessment of network architecture and system dependencies before you create a migration plan.


## Example systems {#section_gws_mdv_sdb .section}

The following two systems are used as examples to describe the hybrid migration procedure.

-   **System 1**

    System 1 is a classic network system that consists of SLB, ECS, RDS, and OSS instances. The Internet SLB instance uses two ECS instances as backend servers. The applications deployed on the two ECS instances need to access the RDS instance and the OSS instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2465/1567942907845_en-US.png)

-   **System 2**

    System 2 is a classic network system that has a more complex architecture than system 1. The Internet SLB instance uses two ECS instances \(ECS 1 and ECS 2\) as backend servers. Both ECS instances need to access an intranet SLB instance. The intranet SLB instance also uses two ECS instances \(ECS 3 and ECS 4\) as backend servers. Both ECS instances need to access the RDS instance and the OSS instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2465/1567942907846_en-US.png)


## Migrate system 1 to a VPC {#section_ozx_pdv_sdb .section}

To migrate *system 1* to a VPC, follow these steps:

1.  Prepare the network environment.

    Create a VPC and a VSwitch to which the system is migrated.

    For more information, see [../../../../dita-oss-bucket/SP\_22/DNVPC11885991/EN-US\_TP\_2434.md\#](../../../../reseller.en-US/Quick Start/Create an IPv4 VPC.md#).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2465/1567942907847_en-US.png)

2.  Obtain the VPC endpoints of the RDS instance and the OSS instance.
    -   You can use the console or call the relevant API action to switch the network type of the RDS instance to VPC and reserve its classic network endpoint. For more information, see [Change the network type of ApsaraDB for RDS](reseller.en-US/Best practices/Migrate from the classic network to VPC/Database hybrid access/Change the network type of ApsaraDB for RDS.md#).

        After the migration, the classic network endpoint remains unchanged and a new VPC endpoint is added. As a result, the ECS instances in the classic network can still access the database without service disruptions. When the classic network endpoint expires, it is automatically deleted and you cannot access the database through the classic network endpoint.

    -   The OSS instance provides a classic network endpoint and a VPC endpoint. You do not need to switch its network type. To obtain the VPC endpoint of the OSS instance, see [Regions and endpoints](../../../../reseller.en-US/Developer Guide/Endpoint/Regions and endpoints.md#).

3.  Create and configure two ECS instances in the VPC.

    Create two ECS instances in the VPC, deploy applications on the ECS instances, and change the RDS and OSS endpoints to their VPC endpoints. After that, conduct a test to verify that the ECS instances can access the OSS instance and the RDS instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2465/1567942908848_en-US.png)

4.  Add the ECS instances in the VPC to the Internet SLB instance.

    Add the two ECS instances in the VPC to the Internet SLB instance. Check the health status of the ECS instances. We recommend that you set a lower weight for the ECS instances. This can reduce the impact of unexpected faults on the system. Check the system status, traffic monitoring, and health check logs.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2465/1567942908849_en-US.png)

5.  Remove the classic-network ECS instances from the Internet SLB instance.

    Remove the classic-network ECS instances from the Internet SLB instance. We recommend that you set the weight of the classic-network ECS instances to 0 and then remove them when they no longer receive requests.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2465/1567942908850_en-US.png)

6.  Release the classic-network ECS instances.

    Release the classic-network ECS instances after the system runs normally for a period of time. You do not need to migrate the Internet SLB instance because VPC ECS instances can be added to it directly.

    **Note:** The classic network endpoint of the RDS instance will be automatically deleted after it expires.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2465/1567942908851_en-US.png)


## Migrate system 2 to a VPC {#section_vfs_ydv_sdb .section}

When you migrate system 2 to a VPC, the preceding procedure does not apply. If you use the preceding procedure, the ECS instances in the VPC cannot access the ECS instances in the classic network because the SLB instance does not support hybrid access.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2465/1567942907846_en-US.png)

To migrate system 2 to a VPC, follow these steps:

1.  Create two ECS instances in the VPC to migrate ECS 3 and ECS 4 added to the intranet SLB instance.
2.  Configure the two ECS instances, and change the endpoint of the RDS instance and the OSS instance to the endpoint of the VPC endpoint.
3.  Create an intranet SLB instance in the VPC to replace the intranet SLB instance in the classic network.
4.  Configure the intranet SLB instance in the VPC. Add the two ECS instances created in step 1 as backend servers.
5.  Create two more ECS instances in the VPC to migrate the ECS 1 and ECS 2 added to the Internet SLB instance.
6.  Configure the two new ECS instances. Change the classic network endpoint of the intranet SLB instance to the VPC endpoint of this instance.
7.  Refer to steps 4 to 6 described in the migration of system 1 to complete the migration of system 2.

