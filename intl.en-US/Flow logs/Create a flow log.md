# Create a flow log {#task_1357837 .task}

This topic describes how to create a flow log. After you create a flow log, you can capture the inbound and outbound traffic over the Elastic Network Interface \(ENI\) in your VPC. With flow logs, you can check access control rules, monitor network traffic, and troubleshoot network faults.

Before you create a flow log, make sure that the following conditions are met:

-   Log Service is activated. For more information, see [Log Service page](https://www.aliyun.com/product/sls/).
-   A Project and a Logstore are created to store traffic data. For more information, see [Create a project](../../../../reseller.en-US/Preparation/Manage projects.md#section_ahq_ggx_ndb) and [Create a Logstore.](../../../../reseller.en-US/Preparation/Manage a Logstore.md#section_v52_2jx_ndb).
-   A capture resource is created. For more information, see [../../../../dita-oss-bucket/SP\_2/DNECS19100345/EN-US\_TP\_9734.md\#](../../../../reseller.en-US/Network/Elastic Network Interfaces/Create an ENI.md#), [Create a VPC](reseller.en-US/VPCs and VSwitches/VPC management/Create a VPC.md#), and [Create a VSwitch](reseller.en-US/VPCs and VSwitches/VSwitch management/Create a VSwitch.md#).

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **FlowLog**.
3.  If it is the first time that you use the flow log function, click **Confirm Authorization Policy** to authorize VPC to write data to your Logstore. 

    **Note:** The authorization is required only when the primary account uses the flow log function for the first time.

4.  Select the region in which you want to create a flow log.
5.  On the FlowLog page, click **Create FlowLog**.
6.  On the Create FlowLog page, set the parameters, and then click **OK**. 

    |Configuration|Description|
    |-------------|-----------|
    |**Name**|Enter a name for the flow log. The name must be 2 to 128 characters in length. It can contain letters, numbers, hyphens \(-\), and underscores \(\_\). It must start with an English letter or a Chinese character, but cannot start with `http://` or `https://`.

 |
    |**Resource Type**|Select the type of the resource for which you want to capture traffic, and then select a resource. Options:     -   ENI: Captures traffic for the selected ENI.
    -   VSwitch: Captures traffic for all the ENIs in the selected VSwitch.
    -   VPC: Captures traffic for all the ENIs in the selected VPC.
 |
    |**Traffic Type**|Select the type of the traffic to be captured. Options:     -   All: All traffic of the specified resource is captured.
    -   Allow: Only the traffic allowed by the security group rules is captured.
    -   Drop: Only the traffic not allowed by the security group rules is captured.
 |
    |**LogStore**|Select a Project and a Logstore to store traffic data.|
    |**Turn on FlowLog Analysis Report Function**|If this option is selected, the indexing function is automatically enabled and a dashboard is created for the selected Logstore. You can perform an SQL and visualized analysis of the captured traffic data. The indexing function is charged by traffic. The dashboard is provided free of charge. For more information, see [Log Service pricing](../../../../reseller.en-US/Pricing/Billing method.md#).

 **Note:** This option is displayed only when the report function of the selected Logstore is disabled.

 |
    |**Description**|Enter a description for the flow log. The description must be 2 to 256 characters in length and cannot start with `http://` or `https://`.

 |


