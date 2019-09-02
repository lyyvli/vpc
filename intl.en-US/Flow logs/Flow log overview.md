# Flow log overview {#concept_1357832 .concept}

This topic provides an overview of the flow log function of VPCs. By using this function, you can capture the inbound and outbound traffic over the Elastic Network Interface \(ENI\) in your VPC. With flow logs, you can check access control rules, monitor network traffic, and troubleshoot network faults.

**Note:** The flow log function is only supported in China \(Hohhot\), Malaysia \(Kuala Lumpur\), Indonesia \(Jakarta\), UK \(London\), and India \(Mumbai\).

## Features {#section_rr5_iph_ms8 .section}

You can capture the traffic of an ENI, a VPC, or a VSwitch. If you create a flow log for a VPC or VSwitch, you can capture the traffic of all ENIs in the VPC or VSwitch, including the ENIs created after the flow log function is enabled.

The captured traffic data is stored in Log Service. You can view and analyze traffic data in Log Service. During the beta testing phase of hte flow log function, you are only charged for the storage and retrieval of traffic data in Log Service.

The traffic data captured by flow logs is written to Log Service as flow log records. Each flow log record includes specified quintuple network streams in a capture window. A capture window is about 10 minutes. During this period, traffic data is aggregated and then released to the flow log record.

The following table describes the fields of a flow log record.

|Field|Description|
|:----|:----------|
|version|The version of the flow log.|
|vswitch-id|The ID of the VSwitch to which the ENI belongs.|
|vm-id|The ID of the ECS instance with which the ENI is associated.|
|vpc-id|The ID of the VPC instance to which the ENI belongs.|
|account-id|The ID of the account.|
|eni-id|The ID of the ENI.|
|srcaddr|The source IP address.|
|srcport|The source port.|
|dstaddr|The destination IP address.|
|dstport|The destination port.|
|protocol|The IANA protocol number of the traffic. For more information, see [Internet Protocol Numbers](http://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml).

 |
|direction|The direction of the traffic. -   in: indicates inbound traffic.
-   out: indicates outbound traffic.

 |
|packets|The number of data packets.|
|bytes|The data packet size.|
|start|The start time of the capture window.|
|end|The end time of the capture window.|
|log-status|The status of the recorded flow log. -   OK: The data is recorded.
-   NODATA: No inbound or outbound traffic is transmitted over the ENI during the capture window.
-   SKIPDATA: Some flow log records are skipped during the capture window.

 |
|action|The action associated with the traffic. -   ACCEPT: the traffic that security groups allow to record.
-   REJECT: the traffic that security groups do not allow to record.

 |

## Procedure {#section_3et_c62_ry9 .section}

The following figure shows the procedure for configuring a flow log.

![Flow log configuration process](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1082282/156739277053062_en-US.png)

1.  Activate Log Service.

    The traffic data captured by the flow log function is stored in Alibaba Cloud Log Service. Therefore, you must activate Log Service before you create a flow log.

2.  Optional. Create an Access Key.

    If you want to write data through APIs or SDKs, you must create an Access Key \(AK\). If you want to collect logs by using Logtail, you do not need to create an AK.

3.  Create a Project.

    You must create a Project in Log Service. For more information, see [Create a project](../../../../reseller.en-US/Preparation/Manage projects.md#section_ahq_ggx_ndb).

4.  Create a Logstore.

    A Logstore is a collection of resources created in a Project. All data in a Logstore is from the same data source. After you create a Project, you must create a Logstore. For more information, see [Create a Logstore.](../../../../reseller.en-US/Preparation/Manage a Logstore.md#section_v52_2jx_ndb).

5.  Create a capture resource.

    Before you create a flow log, you must create a resource whose logs you want to capture. You can capture logs of a specified ENI, VPC, or VSwitch. For more information, see [Create an ENI](../../../../reseller.en-US/Network/Elastic Network Interfaces/Create an ENI.md#) ,[Create a VPC](reseller.en-US/VPCs and VSwitches/VPC management/Create a VPC.md#) and [Create a VSwitch](reseller.en-US/VPCs and VSwitches/VSwitch management/Create a VSwitch.md#).

6.  Create a flow log.

    After you create a flow log, you can capture the traffic data among instances in different regions of the specified CEN. For more information, see [Create a flow log](reseller.en-US/Flow logs/Create a flow log.md#).

7.  View the flow log.

    After you create a flow log, you can view the flow log. You can use the captured traffic data to analyze cross-region traffic, optimize traffic costs, and troubleshoot network faults. For more information, see [View a flow log](reseller.en-US/Flow logs/View a flow log.md#).


## Limits {#section_06z_qjd_dq6 .section}

You can create up to 10 flow log instances in each region. To increase the quota, open a ticket.

