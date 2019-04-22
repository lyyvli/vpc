# How to choose a product to gain access to an intranet? {#concept_yxq_zs5_sdb .concept}

Virtual Private Cloud \(VPC\) is a private network dedicated to you on Alibaba Cloud. Alibaba Cloud provides various products and services to access VPC, such as Express Connect, VPN Gateway, CEN, and Smart Access Gateway.

The following table describes various scenarios where different Alibaba Cloud products are used to establish an intranet environment connected to VPC.

|[Connect VPCs](reseller.en-US/Best practices/How to choose a product to gain access to an intranet?.md#section_wbw_gt5_sdb)|
|**Product**|**Scenario**|**Benefits**|**Limits**|
|[Cloud Enterprise Network \(CEN\)](../../../../reseller.en-US/Product Introduction/What is Cloud Enterprise Network?.md#)|Connect one or more VPC networks located in different regions and under different accounts.| Easy configurations, and automatic route learning and distribution functions.

 Low latency and high speed.

 The networks \(VPC/VBR\) attached to a CEN instance are all connected with each other.

 The connection between networks in the same region is free of charge.

 |None|
|[Express Connect](../../../../reseller.en-US/Product Introduction/What is Express Connect?.md#)|Establish a peering connection between two VPCs.|The connection between two VPCs in the same region is free of charge.|None|
|[Connect to an on-premises data center](reseller.en-US/Best practices/How to choose a product to gain access to an intranet?.md#section_klv_ft5_sdb)|
|**Product**|**Scenario**|**Benefits**|**Limits**|
|[VPN Gateway](../../../../reseller.en-US/Product Overview/What is VPN Gateway?.md#)|Connect an on-premises data center and a VPC through an Internet-based and encrypted IPsec-VPN tunnel.| Low cost.

 Secure.

 Configurations take effect immediately.

 |The network latency and availability is dependent on the quality of the Internet connection.|
|[Cloud Enterprise Network \(CEN\)](../../../../reseller.en-US/Product Introduction/What is Cloud Enterprise Network?.md#)|Through automatic route learning and distribution, CEN can connect resources in the whole network. You only need to attach the VBR associated with the local data center to the CEN instance.| Easy configurations, and automatic route learning and distribution functions.

 Low latency and high speed.

 The networks \(VPC/VBR\) attached to a CEN instance are all connected with one other.

 Connecting networks in the same region is free of charge.

 |None|
|[Smart Access Gateway](../../../../reseller.en-US/Product Introduction/What is Smart Access Gateway.md#)|Connect a local data center to Alibaba Cloud.| Automatic features with out-of-the-box functionality.

 The connection between local branches and Alibaba Cloud is through an encrypted private network and encryption authentication is implemented during the Internet transmission.

 Nearby access within the city through the Internet is supported. Additionally, multiple local branches can access Alibaba Cloud using the Smart Access Gateway devices with active/standby links.

 |None|
|[Express Connect](../../../../reseller.en-US/Product Introduction/What is Express Connect?.md#)|Connect an on-premises data center and a VPC through the physical connection of Express Connect.| High network quality.

 Large bandwidth.

 | Initial setup costs are high.

 The service activation takes a long time.

 |
|VPN software in the Alibaba Cloud Marketplace|You can buy a VPN Gateway in the Alibaba Cloud Marketplace and deploy it in the VPC so that you can connect a local data center to the VPC through an Internet-based and encrypted IPsec-VPN tunnel.| Secure.

 Multiple types of VPN software available to meet different network architectures.

 Configurations take effect immediately.

 | You need to manually deploy and maintain the VPN Gateway.

 The network latency and availability is dependent on the quality of the Internet connection.

 |
|[Connect multiple sites](reseller.en-US/Best practices/How to choose a product to gain access to an intranet?.md#section_ub1_r55_sdb)|
|**Product**|**Scenario**|**Benefits**|**Limits**|
|[VPN Gateway](../../../../reseller.en-US/Product Overview/What is VPN Gateway?.md#)|Establish secure communication between multiple sites through the VPN Gateway. The VPN-Hub function provides communication between sites, and between the sites and the VPC.| Low cost.

 Zero touch provisioning \(ZTP\), and configurations take effect immediately.

 |None|
|[Smart Access Gateway](../../../../reseller.en-US/Product Introduction/What is Smart Access Gateway.md#) + [Express Connect](../../../../reseller.en-US/Product Introduction/What is Express Connect?.md#)|After you purchase and configure Smart Access Gateway for the local branches, you can add the Smart Access Gateways to a Cloud Connect Network \(CCN\). Then, you can attach the CCN to a Cloud Enterprise Network \(CEN\) instance to enable intranet communication between the local branches.| Zero touch provisioning \(ZTP\).

 The local branches and the Alibaba Cloud are connected through an encrypted private network and encryption authentication is implemented during the Internet transmission.

 Nearby access within the city through the Internet is supported. Additionally, multiple local branches can access Alibaba Cloud using the Smart Access Gateway devices with active/standby links.

 |None|
|[VPN Gateway](../../../../reseller.en-US/Product Overview/What is VPN Gateway?.md#)|You can use VPN Gateway and Express Connect to connect application systems and office sites around the world.| High network quality.

 |The network latency and availability depends on the quality of the Internet connection.|
|[Remote access to a VPC](reseller.en-US/Best practices/How to choose a product to gain access to an intranet?.md#section_hdl_555_sdb)|
|**Product**|**Scenario**|**Benefits**|**Limits**|
|[VPN Gateway](../../../../reseller.en-US/Product Overview/What is VPN Gateway?.md#) \(SSL-VPN function\)|Use the SSL-VPN function to securely and quickly access a VPC from a remote client.| Low cost.

 Reliable.

 Easy to configure and deploy.

 |None|
|SSL-VPN software in Alibaba Cloud Marketplace|After you purchase SSL-VPN software from the Alibaba Cloud Marketplace, you can deploy it in a VPC so that you can access the VPN server from a remote client.|Multiple types of SSL-VPN software are available.| High cost.

 Low reliability.

 You need to deploy and maintain the SSL-VPN software by yourself.

 |

## Connect VPCs {#section_wbw_gt5_sdb .section}

You can deploy different applications in different VPC networks to build a service network across regions. This architecture helps provide services from nearby locations, reduce network latency, achieve mutual backup and improve the reliability of the whole system.

Both Express Connect and VPN Gateway can connect VPCs in the same region or in different regions.

-   CEN

    Cloud Enterprise Network \(CEN\) allows you to build an intranet-based communication channel between one or more VPCs. By using automatic route distribution and learning functions, CEN accelerates network convergence, improves the quality and security of cross-network communication, and interconnects resources within the whole network, helping you achieve an interconnected network with enterprise-level scale and communication capabilities.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2448/1555934760834_en-US.png)

-   VPN Gateway

    VPN Gateway can connect a local data center, a local office network, or an Internet terminal to a VPC through an Internet-based, encrypted channel. You can connect VPCs located in different regions and under different accounts through VPN Gateway. By default, a VPN Gateway contains two gateway instances that form active/standby backup, so that if the active instance fails, the traffic is immediately directed to the standby instance. You can also use VPN Gateway to implement an IPsec-VPN connection between an on-premises data center and a VPC..

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2448/1555934760835_en-US.png)


## Connect to an on-premises data center {#section_klv_ft5_sdb .section}

You can connect a VPC to an on-premises data center to build a hybrid cloud. By using the secure and reliable connection between the VPC and the on-premises data center, and by integrating the computing, storage, network, CDN and BGP resources of Alibaba Cloud, you can easily expand your local IT infrastructure to Alibaba Cloud to cope with changing service demands.

You can connect an on-premises data center to a VPC through Express Connect, VPN Gateway, or CEN.

-   Express Connect

    Express Connect helps establish physical access. After a leased line is connected to an Alibaba Cloud access point, you can create a peer connection between a VBR and a VPC to build a hybrid cloud.

    With Express Connect, the intranet connection of the leased line does not use the Internet. Therefore, compared with a traditional Internet connection, the physical connection features higher security, reliability, and speed while also providing lower network latency.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2448/1555934760836_en-US.png)

-   VPN Gateway

    VPN Gateway can connect a local data center, a local site, an Internet terminal to a VPC in a secure and reliable way through an Internet-based and encrypted channel. VPN Gateway contains two different gateway instances which provide active/standby hot backup. The traffic is automatically distributed to the standby node when the active node fails. You can use IPsec-VPN to connect a local data center to a VPC.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2448/1555934761837_en-US.png)

-   CEN

    Through automatic route distribution and learning, CEN enables you to build a secure, private, and enterprise-class interconnected network between VPCs in different regions and your local data centers. You only need to attach the VBR associated with the on-premises data center to a CEN instance, then the on-premises data center can communicate with all networks \(VPCs or VBRs\) attached to the CEN instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2448/15559347619794_en-US.png)

-   Smart Access Gateway

    Smart Access Gateway Smart Access Gateway is a device-based solution that enables the connection of on-premises data centers to Alibaba Cloud. With Smart Access Gateway, enterprises can access Alibaba Cloud through the Internet in an encrypted manner, and experience a more intelligent, more reliable, and more secure mechanism in which to access the Alibaba Cloud ecosystem.

    You can buy a Smart Access Gateway device for the local data center, and attach the CCN instance associated with the device to the CEN instance so as to connect the on-premises data center to Alibaba Cloud.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2448/15559347619796_en-US.png)

-   VPN software in the Alibaba Cloud Marketplace

    The Alibaba Cloud Marketplace provides various types of VPN software and images. You can purchase the required VPN software from the Alibaba Cloud Marketplace and deploy it on your ECS instance. Then you can use an EIP to connect the VPC to the customer gateway of your on-premises data center through the Internet.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2448/1555934762838_en-US.png)


## Connect multiple sites {#section_ub1_r55_sdb .section}

You can connect multiple sites through Smart Access Gateway or the VPN-Hub function of VPN Gateway.

-   Smart Access Gateway

    Smart Access Gateway is a device-based solution that enables the connection of on-premises data centers to Alibaba Cloud. With Smart Access Gateway, enterprises can access Alibaba Cloud through the Internet in an encrypted manner, and experience a more intelligent, more reliable, and more secure mechanism in accessing the Alibaba Cloud ecosystem.

    You can purchase Smart Access Gateway devices for local branches and connect the devices through CEN so that the local branches can communicate with one another.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2448/15559347629795_en-US.png)

-   VPN Gateway

    The IPSec-VPN function of VPN Gateway provides site-to-site VPN connection. Each VPN Gateway supports 10 IPsec-VPN connections. Therefore, you can buy a VPN Gateway to connect 10 on-premises data centers or local sites in different areas.

    You can establish secure communication between multiple sites through the VPN-Hub function. The sites cannot communicate with the connected VPC, but can communicate with each another. VPN-Hub allows large enterprises to establish intranet communication across different sites.

    The VPN-Hub function is enabled by default. You only need to configure the IPsec-VPN connection between each office site and Alibaba Cloud. No additional configurations or payments required. A VPN Gateway supports up to 10 IPsec connections. The following figure shows an example of how to connect three office sites \(Shanghai, Hangzhou, and Ningbo\). In this example, you only need to create a VPN Gateway and three customer gateways, and establish three IPsec connections.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2448/1555934762839_en-US.png)

-   Build a high-speed global network

    You can connect application systems and office sites located around the world through VPN Gateway and Express Connect. This method features high security, high network quality and low cost.

    As shown in the following figure, to connect office sites in US \(Virginia\) and office sites in Shanghai, you can deploy application systems in the VPC in US \(Virginia\) and the VPC in Shanghai, connect the VPCs through Express Connect and then connect the office sites in the two regions to the two VPCs through IPsec-VPN.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2448/1555934762840_en-US.png)


## Remote access to a VPC {#section_hdl_555_sdb .section}

The SSL-VPN function of VPN Gateway provides site-to-site VPN connection. Terminals can directly access a VPC without the need to configure customer gateways. You can deploy local internal applications in a VPC, and staff based in office can access the internal system through SSL-VPN. For example, local IT staff can access the VPC through the intranet, while staff that are based out of the office can access local applications in the VPC from remote sites.

Both VPN Gateway or VPN software/images from the Alibaba Cloud Marketplace can be used to achieve remote access to the VPC.

-   VPN Gateway \(SSL-VPN\)

    You can create an SSL-VPN connection to connect a remote client to applications deployed in a VPC. When the deployment is complete, you only need to load the certificate in the client to initiate the connection. VPN Gateway contains two different gateway instances which provide active-standby hot backup. The traffic is automatically distributed to the standby node when the active node fails.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2448/1555934762841_en-US.png)

-   SSL-VPN software from the Alibaba Cloud Marketplace

    After you purchase SSL-VPN software from the Alibaba Cloud Marketplace, you can deploy it in a VPC so that you can access the VPN server from a remote client. Multiple types of SSL-VPN software are available.


