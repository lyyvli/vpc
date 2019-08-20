# Add a subnet route to a custom route table {#task_1512598 .task}

This topic describes how to add a subnet route to a custom route table. After you add a subnet route to a custom route table, you can associate the custom route table with a VSwitch to control the flow of traffic to and from the VSwitch.

A VPC is created. For more information, see [Create a VPC](intl.en-US/User Guide/VPC and subnets/Create a VPC.md#).

## Limits {#section_r3m_ki1_1p7 .section}

Before you add a subnet route to a route table, note the following limits:

-   You can only create up to 10 route tables in each VPC, including system route tables.
-   Each VSwitch can be associated with only one route table.
-   Active/standby routes and load balancing routes are not supported by custom route tables.
-   Custom route tables are supported in all regions except China \(Beijing\), China \(Shenzhen\), and China \(Hangzhou\).

## Step 1: Create a custom route table {#section_50v_jf3_myz .section}

To create a custom route table, follow these steps:

## Step 2: Add a subnet route to the custom route table {#section_bnr_cvp_rmd .section}

To add a subnet route to the custom route table, follow these steps:

## Step 3: Associate the route table with a VSwitch {#section_48i_3db_q50 .section}

You can associate the route table with a VSwitch \(subnet\) to control the flow of traffic to and from the VSwitch. Each VSwitch can be associated with only one custom route table or system route table. To associate the custom route table with a VSwitch, follow these steps:

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com)。
2.  在左侧导航栏，单击**路由表**。
3.  选择路由表的所属地域。
4.  在路由表页面，找到目标路由表，然后单击**操作**列下的**管理**。
5.  在路由表基本信息区域，单击**已绑定交换机**页签，然后单击**绑定交换机**。
6.  在绑定交换机页面，选择要绑定的交换机，然后单击**确定**。

