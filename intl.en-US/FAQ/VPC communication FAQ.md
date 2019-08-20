# VPC communication FAQ {#concept_bxf_qf4_tdb .concept}

This topic describes FAQ about VPC communication.

-   [Can different VSwitches in a VPC communicate with each other?](#section_ppc_2l5_vdb)
-   [Can different VPCs communicate with each other through the intranet?](#section_qpc_2l5_vdb)
-   [Does VPCs support physical connection access?](#section_rpc_2l5_vdb)
-   [Does a VPC provide the VPN function?](#section_spc_2l5_vdb)
-   [Can a VPC access Internet services?](#section_tpc_2l5_vdb)
-   [Can cloud services in a VPC be accessed from the Internet?](#section_vpc_2l5_vdb)
-   [Can a VPC directly communicate with the classic network?](#section_xpc_2l5_vdb)

## Can different VSwitches in a VPC communicate with each other? {#section_ppc_2l5_vdb .section}

Yes, different VSwitches in a VPC can communicate with each other as long as the security group rules allow the VSwitches to communicate.

## Can different VPCs communicate with each other through the intranet? {#section_qpc_2l5_vdb .section}

Yes, different VPCs can communicate with each other through Express Connect, VPN Gateway, and CEN instances although these VPCs are logically isolated from each other. For more information, see [How to choose a product to gain access to an intranet?](../../../../reseller.en-US/Best practices/How to choose a product to gain access to an intranet?.md#).

## Does VPCs support physical connection access? {#section_rpc_2l5_vdb .section}

Yes, VPCs allow access from on-premises data centers through a physical connection. For more information, see [../../../../dita-oss-bucket/SP\_72/DNexpressconnect1847151/EN-US\_TP\_13831.md\#](../../../../reseller.en-US/Getting Started (New Console)/Connect an on-premises data center to a VPC through a physical connection.md#).

## Does a VPC provide the VPN function? {#section_spc_2l5_vdb .section}

Yes, a VPC provides the VPN function. For more information, see [What is VPN Gateway?](../../../../reseller.en-US/User Guide/What is VPN Gateway?.md#).

## Can a VPC access Internet services? {#section_tpc_2l5_vdb .section}

Yes, a VPC can access Internet services by using the following methods:

-   Assign a public IP address to the VPC.
-   Associate an EIP with the VPC.
-   Configure a NAT Gateway for the VPC.

For more information, see [How to choose an Internet-facing product?](../../../../reseller.en-US/Best practices/How to choose an Internet-facing product?.md#)

## Can cloud services in a VPC be accessed from the Internet? {#section_vpc_2l5_vdb .section}

Yes, you can access cloud services in a VPC from the Internet by using the following methods:

-   Assign a public IP address to the VPC.
-   Associate an EIP with the VPC.
-   Configure a NAT Gateway for the VPC.
-   Configure an Internet SLB instance for the VPC.

For more information, see [How to choose an Internet-facing product?](../../../../reseller.en-US/Best practices/How to choose an Internet-facing product?.md#)

## Can a VPC directly communicate with the classic network? {#section_xpc_2l5_vdb .section}

No, a VPC cannot directly communicate with the classic network. However, you can configure a public IP address for the ECS instances in the VPC to enable the ECS instances to communicate with cloud resource instances in the classic network through the Internet. For more information, see [How to choose an Internet-facing product?](../../../../reseller.en-US/Best practices/How to choose an Internet-facing product?.md#)

Alternatively, you can use ClassicLink to establish low-latency and high-speed connections between classic-network ECS instances and VPC ECS instances. For more information, see [ClassicLink overview](../../../../reseller.en-US/VPC network connections/ClassicLink/ClassicLink overview.md#).

