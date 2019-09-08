# Overview of migration solutions {#concept_wjl_hv5_sdb .concept}

This topic provides an overview of the solutions that are used to migrate cloud resources from a classic network to a Virtual Private Cloud \(VPC\). Compared with a classic network, a VPC is an isolated network environment with higher security.

## Benefits {#section_mmn_mv5_sdb .section}

A VPC is a private network in Alibaba Cloud. You can use Alibaba Cloud resources in your VPC. The benefits of VPCs are as follows:

-   Secure network environment

    Based on the tunneling technique, VPCs isolate the data link layer and provide an independent, isolated, and secure network for each tenant. VPCs are completely isolated from each other.

-   Flexible network configurations

    You can specify the IP address range and configure route tables and gateways in your VPC. Furthermore, you can connect your VPC to other VPCs or on-premises data centers to create a custom network environment through a physical connection or VPN. In this way, you can smoothly migrate applications to the cloud and extend on-premises data centers.


## Migration solutions {#section_omn_mv5_sdb .section}

You can use two solutions \(hybrid migration and single ECS migration\) to migrate your cloud resources from a classic network to a VPC. The two solutions can be used independently or together to meet your requirements in different scenarios.

-   Hybrid migration

    We recommend that you use the hybrid migration solution if your system is deployed on RDS, SLB, or other cloud products. By using this solution, you can migrate your system to a VPC without service disruptions.

    Furthermore, this solution can be used along with the ClassicLink function to allow ECS instances in the classic network to access cloud resources in the VPC. For more information, see [ClassicLink overview](../../../../reseller.en-US/VPC network connections/ClassicLink/ClassicLink overview.md#).

-   Single ECS migration

    We recommend that you use the single ECS migration solution if your applications are deployed on an ECS instance and also if restarting the ECS instance does not affect your system.


## Hybrid migration {#section_qmn_mv5_sdb .section}

The hybrid migration is a seamless migration solution that consists of hybrid access and hybrid attachment. This solution allows you to create a cloud instance \(such as ECS instance\) in a VPC and then migrate your system to the VPC. After all your systems are migrated to the VPC, you can release the cloud resources in the classic network. For more information, see [Hybrid migration](reseller.en-US/Best practices/Migrate from the classic network to VPC/Hybrid migration.md#).

-   **Hybrid attachment**

    Hybrid attachment refers to attaching a classic-network ECS instance and a VPC ECS instance to a Server Load Balancer \(SLB\) instance as backend servers to process forwarded requests. Hybrid attachment also allows you to attach a classic-network ECS instance and a VPC ECS instance to a VServer group.

    Hybrid attachment is supported by Internet and intranet SLB instances.

    **Note:** If you attach a classic-network ECS instance and a VPC ECS instance to an intranet SLB instance and configure a layer-4 \(TCP and UDP\) listener, you can obtain the real client IP address from the VPC ECS instance, but cannot obtain this address from the classic-network ECS instance. If you configure a layer-7 \(HTTP and HTTPs\) listener, you can obtain the real client IP address from the VPC ECS instance and the classic-network ECS instance.

-   **Hybrid access**

    Hybrid access refers to a process during which classic-network ECS instances and VPC ECS instances access RDS, OSS, or other cloud products at the same time. These products have two endpoints. One is used to access the classic network and the other is used to access the VPC.


When you use the hybrid migration solution, note the following:

-   If the classic-network ECS instances and VPC ECS instances in your system need to communicate with each other, you can use the ClassicLink function.

-   This solution applies only to the migration of your system from a classic network to a VPC.


