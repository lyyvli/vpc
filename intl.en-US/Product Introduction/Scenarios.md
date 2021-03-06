# Scenarios {#concept_fhg_jlz_ndb .concept}

This topic describes the scenarios in which VPCs are used to guarantee a high level of data security and service availability.

## Host applications that provide external services {#section_fmj_tlz_ndb .section}

You can host applications that provide external services in a VPC and control access to these applications from the Internet by creating security group rules and access control whitelists. You can also isolate Internet-based mutual access between the application server and the database. For example, you can deploy the web server in a subnet that can access the Internet and deploy the application database in a subnet that cannot access the Internet.

![Host applications that provide external services](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13390/15679426332768_en-US.png)

## Host applications that require access to the Internet {#section_dtj_vlz_ndb .section}

You can host applications that require access to the Internet in a subnet of a VPC and route traffic through network address translation \(NAT\). After you configure SNAT rules, instances in the subnet can access the Internet without exposing their private IP addresses, which can be changed to public IP addresses any time to avoid external attacks.

![Host applications that require access to the Internet](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13390/15679426332769_en-US.png)

## Implement disaster tolerance across zones {#section_nlp_4vh_w2b .section}

You can create one or multiple subnets in a VPC by creating VSwitches. VSwitches in a VPC can communicate with each other. You can deploy resources on VSwitches in different zones for disaster tolerance.

![Implement disaster tolerance across zones](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13390/15679426339780_en-US.png)

## Isolate business systems {#section_bsg_pvh_w2b .section}

VPCs are logically isolated from each other. Therefore, you can create multiple VPCs to isolate multiple business systems, for example, isolate the production environment from the test environment. You can also create a peering connection between two VPCs if they need to communicate with each other.

![Isolate business systems](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13390/15679426339781_en-US.png)

## Build a hybrid cloud {#section_nsl_llz_ndb .section}

You can create a dedicated connection to connect your VPC to an on-premises data center to expand your local network. By doing so, you can seamlessly migrate your local applications to the cloud without changing the method of access to these applications.

![Build a hybrid cloud](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13390/15679426332767_en-US.png)

## Control big bandwidth fluctuations caused by multiple applications {#section_i4s_wlz_ndb .section}

If your applications generate big bandwidth fluctuations, you can configure DNAT forwarding rules through the NAT Gateway. Then, you can add EIPs to Internet Shared Bandwidth so that these EIPs can share the bandwidth. This can reduce bandwidth fluctuations and save your cost.

![Control big bandwidth fluctuations caused by multiple applications](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13390/15679426332770_en-US.png)

