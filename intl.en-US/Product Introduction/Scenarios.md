# Scenarios {#concept_fhg_jlz_ndb .concept}

This topic describes several scenarios where Alibaba Cloud Virtual Private Cloud \(VPC\) can be applied to deliver better service availability and enhanced communication security.

## Host applications {#section_fmj_tlz_ndb .section}

You can use VPC to host one or some applications that have different Internet access requirements, and manage the requirements by creating security group rules and applying access control lists \(ACLs\) by means of a whitelist. You can also control the access by isolating the application server from the database. For example, you can deploy a web server in a VSwitch \(subnet\) that is allowed to access the Internet and deploy the database of the application in another subnet that is denied access to the Internet, all within the same VPC.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13390/15550626512768_en-US.png)

## Host applications that require access to the Internet {#section_dtj_vlz_ndb .section}

You can host one or more applications that require access to the Internet in a subnet of a VPC and route the traffic through NAT Gateway. Specifically, after you configure SNAT rules, an instance in the subnet can access the Internet without exposing its private IP address and the private IP address can be changed to a public IP address any time.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13390/15550626512769_en-US.png)

## Cross-zone disaster tolerance {#section_nlp_4vh_w2b .section}

In a VPC, you can create one or multiple subnets by creating VSwitches \(subnets\), and the VSwitches can communicate with one another through the intranet. You can deploy resources in VSwitches of different zones to achieve cross-zone disaster tolerance.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13390/15550626519780_en-US.png)

## Isolate different systems {#section_bsg_pvh_w2b .section}

VPCs are logically isolated from one another. Therefore, if you need to isolate multiple systems \(such as isolate the production environment from the test environment\), you can create multiple VPCs. If the VPCs need to communicate with each other, you can create a peer connection between them.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13390/15550626519781_en-US.png)

## Build a hybrid cloud {#section_nsl_llz_ndb .section}

You can create a dedicated connection to connect your VPC to an on-premises data center, allowing you to expand your local network. Then, through the dedicated connection, you can seamlessly migrate your local applications to the cloud without changing the way of accessing applications.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13390/15550626512767_en-US.png)

## Share bandwidth across multiple applications {#section_i4s_wlz_ndb .section}

If you applications experience great bandwidth fluctuation, you can configure DNAT rules through NAT Gateway and add EIPs to an Internet Shared Bandwidth so that the EIPs can share the bandwidth. In this way, bandwidth fluctuation can be reduced, thereby lowering overall costs.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13390/15550626512770_en-US.png)

