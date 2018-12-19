# Example of hybrid access and hybrid adding migration {#concept_u32_ycv_sdb .concept}

This document provides an example of using the hybrid access and hybrid adding solution to migrate resources from the classic network to a VPC network.

## Prerequisites {#section_rtn_bdv_sdb .section}

Before the migration, make sure that:

-   You have known the details and limits of the migration. For more information, see [Migration overview](reseller.en-US/Best practices/Migrate from the classic network to VPC/Migration overview.md#).

-   You are familiar with VPC and the related products. VPC and the classic network are very different. Apart from the network isolation, VPC enables you to control your private network by using other related products.

-   The migration example in this document is only for reference. Many systems are more complex than that in the example. Before the migration, you need to make careful evaluation, find out system dependencies and work out a precise migration plan.


## Example systems {#section_gws_mdv_sdb .section}

This document provides two migration examples. One of the systems to be migrated is more complex than the other:

-   **System 1**

    As shown in the following figure, the system to be migrated consists of SLB, ECS, RDS and OSS. The Internet SLB instance uses two ECS instances as the backend servers and the application deployed on the two ECS instances need to access RDS and OSS.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2465/1545207892845_en-US.png)

-   **System 2**

    As shown in the following figure, system 2 has a more complex architecture. As shown in the following figure, the Internet SLB instance uses two ECS instances \(ECS 1 and ECS 2\) as the backend servers. And these two ECS instances have to access an intranet SLB instance. Similarly, the intranet SLB instance also uses two ECS instances \(ECS 3 and ECS 4\) which need to access RDS and OSS.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2465/1545207893846_en-US.png)


## Migrate system 1 to VPC {#section_ozx_pdv_sdb .section}

To migrate *system 1* to a VPC, complete these steps:

1.  Prepare the network environment.

    Firstly, you have to create a VPC and VSwitch to which the system is migrated.

    For more information, see [Create a VPC](../../../../reseller.en-US/Quick Start/Create a VPC.md#).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2465/1545207893847_en-US.png)

2.  Obtain the VPC endpoints of RDS and OSS.
    -   You can migrate the RDS instance to the VPC either through the API or on the console and reserve its classic network endpoint at the same time. For more information, see [Change the network type of ApsaraDB for RDS](reseller.en-US/Best practices/Migrate from the classic network to VPC/Database hybrid access/Change the network type of ApsaraDB for RDS.md#).

        After the migration, the classic network endpoint remains unchanged and a new VPC endpoint is added. Therefore, the ECS instances in the classic network can still access data and the service is not interrupted. When the classic network endpoint expires, the system automatically deletes it and you cannot access the database through the classic network endpoint.

    -   OSS provides two endpoints itself and no switching is required. To obtain the VPC endpoint of OSS, see [Regions and endpoints](../../../../reseller.en-US/Developer Guide/Endpoint/Regions and endpoints.md#).

3.  Create two ECS instances in the VPC and configure the ECS instances.

    As shown in the following figure, create two ECS instances in the VPC, deploy applications on these instances, and change the RDS and OSS endpoints to their VPC endpoints. After the configuration is complete, you need to do test to verify that OSS and RDS are accessible.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2465/1545207893848_en-US.png)

4.  Add the ECS instances in the VPC to the Internet SLB instance.

    As shown in the following figure, add the ECS instances created and configured in the VPC to the Internet SLB instance. Then observe the health check status of the newly added ECS instances. You can set a smaller weight for the ECS instances. This helps reduce the impact on the system when the instances are declared as healthy but other exceptions occur. Also, observe information like system status, traffic monitoring, and health check logs.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2465/1545207893849_en-US.png)

5.  Remove ECS instances of the classic network from the Internet SLB instance.

    As shown in the following figure, when the system is operating normally, remove the ECS instances of the classic network from the Internet SLB instance. You can set the weights of the ECS instances of the classic network to zero and then remove them when no more traffic is distributed to them.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2465/1545207893850_en-US.png)

6.  Release the ECS instances of the classic network.

    As shown in the following figure, release the ECS instances of the classic network after the system has been running normally for a period of time. The Internet SLB instance supports adding ECS instances of the VPC network itself, so no migration is required. Till now, you have finished the migration.

    **Note:** The classic network endpoint of RDS will be automatically deleted once it expires.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2465/1545207893851_en-US.png)


## Migrate system 2 to VPC {#section_vfs_ydv_sdb .section}

When migrating a relative complex system as shown in the following figure, if the procedure for migrating system 1 is used, the ECS instances of the VPC network cannot access the ECS instances of the classic network because the SLB instance does not support hybrid access.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2465/1545207893846_en-US.png)

The basic steps for migrating this system are as follows:

1.  Create two ECS instances in the VPC to migrate the ECS 3 and ECS 4 of the classic network added to the intranet SLB instance.
2.  Configure the newly created ECS instances using the VPC endpoints of RDS and OSS.
3.  Create an intranet SLB instance in the VPC to replace the intranet SLB instance in the classic network.
4.  Configure the intranet SLB instance in the VPC. Add the two ECS instances created in step 1 as the backend servers.
5.  Create two more ECS instances in the VPC to migrate the ECS 1 and ECS 2 of the classic network added to the Internet SLB instance.
6.  Configure these two ECS instances. Change the classic network endpoint of the intranet SLB instance to the VPC endpoint of the instance.
7.  The following steps are similar to the migration of system 1.

