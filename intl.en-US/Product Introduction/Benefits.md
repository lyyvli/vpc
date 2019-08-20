# Benefits {#concept_ckn_y3z_ndb .concept}

This topic describes the benefits of using VPCs.

## High security {#section_as5_cxz_vdb .section}

Each VPC has a unique tunnel ID, and each tunnel ID corresponds to a virtual network. Different VPCs are isolated by tunnel IDs:

-   Similar to traditional networks, VPCs can also be divided into subnets. ECS instances in the same subnet use the same VSwitch to communicate with each other, while ECS instances in different subnets use VRouters to communicate with each other.
-   VPCs are completely isolated from each other and can only be interconnected by mapping an EIP or a NAT IP address.
-   ECS IP packets are encapsulated by using the tunneling technique. Therefore, information about the data link layer \(layer-2 MAC address\) of ECS does not go to the physical network. As a result, the layer-2 network between different ECS instances or between different VPCs is isolated.
-   ECS instances in a VPC use security groups as firewalls to control traffic going to and from ECS instances. This is layer-3 isolation.

## High flexibility {#section_elt_dxz_vdb .section}

You can use security groups or whitelists to flexibly control traffic going to and from the cloud resources in a VPC.

## Ease of use {#section_nls_2xz_vdb .section}

You can quickly create and manage VPCs in the VPC console. After a VPC is created, the system automatically creates a VRouter and a route table for the VPC.

## High scalability {#section_d4p_fxz_vdb .section}

You can create multiple subnets in a VPC to deploy different services. Additionally, you can connect a VPC to other VPCs or on-premises data centers to expand your network.

