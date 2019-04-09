# Flow logs {#concept_ubn_5ly_52b .concept}

This topic describes the flow logs function in Alibaba Cloud Virtual Private Cloud \(VPC\). The flow logs function allows you to monitor the IP traffic going to and coming from Elastic Network Interfaces \(ENI\) in your VPC. By using the flow logs, you can check the access control list \(ACL\) rules, monitor network traffic, and troubleshoot networking problems.

**Note:** The flow log function is available only in the China \(Hohhot\), Malaysia, Indonesia \(Jakarta\), UK \(London\), and Indonesia \(Jakarta\) regions.

## Introduction to flow logs {#section_cq5_rny_52b .section}

You can use the flow log function to monitor the IP traffic information for an ENI, a VSwitch or a VPC. If you create a flow log for a VSwitch or a VPC, all the Elastic Network Interfaces, including the newly created Elastic Network Interfaces, are monitored.

Flow log data is stored in Log Service, where you can view and analyze IP traffic information. Currently, the flow log function is available free of charge. However, corresponding storage and indexing fees associated with the use of Log Service are billed. For more information, see [Billing method](../../../../../reseller.en-US/Pricing/Billing method.md#).

The traffic information monitored by the flow log function is recorded as flow log records. Each record captures the network flow for a specific 5-tuple in a specific monitoring time period \(approximately 10 minutes\). During the monitoring time period, Log Service aggregates data, which takes about 5 minutes, and then publishes the generated flow log records.

The following table describes the fields recorded in flow log records.

|Field|Description|
|:----|:----------|
|version|The version of the flow log.|
|vswitch-id|The ID of the VSwitch to which the ENI belongs.|
|vm-id|The ID of the ECS instance to which the ENI is attached. |
|vpc-id|The ID of the VPC to which the ENI belongs.|
|account-id|The ID of the account.|
|eni-id|The ID of the ENI.|
|srcaddr|The source address.|
|srcport|The source port.|
|dstaddr|The destination IP address.|
|dstport|The destination port of traffic.|
|protocol|The IANA protocol number of traffic.For more information, see [Assigned Internet Protocol Numbers](http://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml).

|
|direction|The direction of traffic. Supported values include:-   in: traffic goes to the ENI
-   out: traffic goes from the ENI

|
|packets|The number of packets monitored in the specified time period.|
|bytes|The number of bytes monitored in the specified time period.|
|start|The start time of the monitoring time period.|
|end|The end time of the monitoring time period.|
|log-status|The logging status of the flow log: Supported values include:-   OK: Data is normally recorded.
-   NODATA: There is no traffic recorded going to or coming from the ENI during the monitoring time period.
-   SKIPDATA: Some flow log records were skipped during the monitoring time period.

|
|action|Actions associated with the traffic. Supported values include:-   ACCEPT: Traffic that security groups allow to be recorded
-   REJECT: Traffic that security groups do not allow to be recorded

|

## Create a flow log {#section_wyf_vtz_52b .section}

**Note:** Before creating a flow log, make sure that Log Service is activated.

After you have activated Log Service, you can create flow logs. To do so, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **FlowLog**.
3.  If it is the first time that you activate the flow logs function, click **Confirm Authorization Policy** to authorize VPC to write data to your specified LogStore.

    **Note:** Authorization is required only when the primary account uses the flow log function for the first time.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21266/155477693211664_en-US.png)

4.  Select the region in which to monitor flow logs and then click **Create Flow Log**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21266/15547769329591_en-US.png)

5.  On the Create Flow Log page, configure the flow log according to the following information and then click **OK**.

    |Configuration|Description |
    |:------------|:-----------|
    |**Name**|Enter a name for the flow log.|
    |**Resource Type**|Select the resource where a flow log is created:    -   ENI: Monitor IP traffic for the selected ENI.
    -   VSwitch: Monitor IP traffic for all ENIs in the selected VSwitch.
    -   VPC: Monitor IP traffic for all ENIs in the selected VPC.
|
    |**Traffic Type**|Select the type of traffic to be monitored:    -   All: All traffic is monitored.
    -   Allow: Only monitor traffic that is allowed by the security group rules.
    -   Drop: Only monitor traffic that is not allowed by the security group rules.
|
    |**LogStore**|Select the LogStore in which to store the monitored traffic information.|
    |**Turn on FlowLog Analysis Report Function**|If this option is selected, the LogSearch/Analytics \(index\) function is automatically enabled and a dashboard is created for the selected LogStore, so that you can perform SQL and visualized analysis of the collected data.The indexing function of Log Service incurs fees. However, the dashboard is provided free of charge. For more information, see [Log Service Billing](../../../../../reseller.en-US/Pricing/Billing method.md#).

**Note:** This option is available only when the report function of the selected LogStore is not enabled.

 |
    |**Description**|Enter a description for the flow log.|


## View logs {#section_g5l_3f1_v2b .section}

To view the monitored traffic information, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **Flow Log**.
3.  Select the target region, and then click the LogStore link of the flow log.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21266/155477693211665_en-US.png)

4.  On the Log Service console, click **Search**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21266/155477693211666_en-US.png)


## Disable a flow log {#section_wrx_s23_cfb .section}

You can disable a flow log when you no longer need to monitor the corresponding traffic information.

To disable a flow log, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **Flow Log**.
3.  Select the target region, find the target flow log, and then click **Disable**.

## Limits {#section_eq4_pb5_cfb .section}

Before you activate the flow log function, note the following:

-   The object where a flow log is created can only be ENI.

-   Only the following resource types support the creation of flow logs: VPC, VSwitch, and ENI.

-   The maximum number of flow log instances that can be created in each region is 10. If you need to create more flow log instances, open a ticket.


