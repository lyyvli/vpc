# Flow logs {#concept_ubn_5ly_52b .concept}

VPC provides you with the flow log function to capture the IP traffic going to and from Elastic Network Interfaces \(ENI\) in your VPC. With flow logs, you can check access control rules, monitor network traffic, and troubleshoot networking problems.

**Note:** The flow log function is only available in the Indonesia \(Jakarta\) region.

## Introduction to flow logs {#section_cq5_rny_52b .section}

You can capture IP traffic information for an ENI, a VSwitch or a VPC. If you create a flow log for VSwitch or VPC, all the Elastic Network Interfaces, including the newly created Elastic Network Interfaces, are monitored.

Flow log data is stored in Log Service. You can view and analyze IP traffic information in Log Service. Flow log is free of charge in the test phase. But corresponding storage and indexing fees are billed when using Log Service. For more information, see [Billing method](../../../../../reseller.en-US/Pricing/Billing method.md#).

The traffic information captured by the flow log function is recorded as flow log records. Each record captures the network flow for a specific 5-tuple in a specific capture window. The capture window is about 10 minutes. During the capture window, Log Service aggregates data and it takes about 5 minutes, then publishes flow log records.

The following table lists recorded fields of flow log records.

|Field|Description|
|:----|:----------|
|version|The version of the flow log.|
|vswitch-id|The ID of the VSwitch that the ENI belongs to.|
|vm-id|The ID of the ECS instance that the ENI is bound to. |
|vpc-id|The ID of the VPC that the ENI belongs to.|
|account-id|The ID of the account.|
|eni-id|The ID of the ENI.|
|srcaddr|The private IP address of the Elastic Network Interface.|
|srcport|The source port of the traffic.|
|dstaddr|The destination IP address.|
|dstport|The destination port of the traffic.|
|protocol|The IANA protocol number of the traffic.For more information, see [Assigned Internet Protocol Numbers](http://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml).

|
|direction|The direction of the traffic:-   in: traffic goes to the ENI
-   out: traffic goes from the ENI

|
|packets|The number of packets in the capture window.|
|bytes|The number of bytes in the capture window.|
|start|The start time of the capture window.|
|end|The end time of the capture window.|
|log-status|The logging status of the flow log:-   OK: Data is normally recorded.
-   NODATA: There is no traffic to or from the ENI during the capture window.
-   SKIPDATA: Some flow log records were skipped during the capture window.

|
|action|The action associated with the traffic:-   ACCEPT: The traffic that security groups allow to record
-   REJECT: The traffic that security groups do not allow to record

|

## Create a flow log {#section_wyf_vtz_52b .section}

**Note:** Before creating a flow log, make sure that Log Service is activated.

To create a flow log, complete these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **Flow Logs**.
3.  If it is the first using flow logs, click **Confirm Authorization Policy** to authorize VPC to write data to your LogStore.

    **Note:** The authorization is required only when the primary account uses the flow log function for the first time.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21266/154772092211664_en-US.png)

4.  Select a region and then click **Create Flow Log**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21266/15477209229591_en-US.png)

5.  On the Create Flow Log page, configure the flow log according to the following information and then click **OK**.

    |Configuration|Description |
    |:------------|:-----------|
    |**Name**|Enter a name for the flow log.|
    |**Resource type**|Select the resource where a flow log is created:    -   ENI: Capture IP traffic for the selected ENI.
    -   VSwitch: Capture IP traffic for all the ENIs in the selected VSwitch.
    -   VPC: Capture IP traffic for all the ENIs in the selected VPC.
|
    |**Traffic Type**|Select the traffic to capture:    -   All: All traffic is captured.
    -   Allow: Only capture the traffic that is allowed by the security group rules.
    -   Drop: Only capture the traffic that is not allowed by the security group rules.
|
    |**LogStore**|Select the LogStore to store the captured traffic information.|
    |**Turn on FlowLog Analysis Report Function**|After this option is selected, the LogSearch/Analytics \(index\) function will be automatically enabled and a dashboard will be created for the selected LogStore, allowing you to analyze the collected data.You will be billed according to the indexing traffic. For more information, see [Log Service Billing](../../../../../reseller.en-US/Pricing/Billing method.md#).

**Note:** This option is available only when the index function of the selected LogStore is not enabled.

 |
    |**Description**|Enter a description for the flow log.|


## View logs {#section_g5l_3f1_v2b .section}

To view the captured traffic information, complete these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **Flow Log**.
3.  Select a region, and then click the LogStore link of the flow log.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21266/154772092311665_en-US.png)

4.  On the Log Service console, click **Search**.
5.  View the captured traffic information.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21266/154772092311666_en-US.png)


## Disable a flow log {#section_wrx_s23_cfb .section}

You can disable a flow log if you do not want to capture the traffic information.

To disable a flow log, complete these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **Flow Log**.
3.  Select a region, and find the target flow log and then click **Disable**.

## Limits {#section_eq4_pb5_cfb .section}

Note the following when you use the flow log function:

-   The object where a flow log is created: ENI

-   Resource types that support creating flow logs: VPC, VSwitch and ENI

-   The number of flow log instances that can be created per region: 10

    If you need to create more flow log instances, open a ticket.


