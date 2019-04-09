# Manage custom route tables {#concept_ym5_jhv_q2b .concept}

This topic describes how to manage custom route tables. Specifically, this topic explains how you can create and edit custom route tables and how you can associate them with or detach them from a VSwitch.

## Create a custom route table {#section_kyq_v41_r2b .section}

To create a custom route table, follow these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com).
2.  In the left-side navigation pane, click **Route Tables**.
3.  On the Route Tables page, click **Create Route Table**.
4.  Configure the route table according to the following information, and then click **OK**.

    |Configuration|Description|
    |:------------|:----------|
    |**Name**| Enter a name for the route table.

 The name must be 2 to 128 characters in length and can contain letters, numbers, Chinese characters, hyphens \(-\) and underscores \(\_\). It must begin with a letter.

 |
    |**VPC**|Select the VPC to which the route table belongs.|
    |**Description**| Enter a description for the route table.

 The description must be 2 to 256 characters in length but cannot begin with `http://` and `https://`.

 |

    You can view and manage custom route tables on the Route Tables page.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17037/15547999318671_en-US.png)


## Associate a custom route table with a VSwitch {#section_yry_52b_r2b .section}

You can associate a custom route table with a VSwitch to control routing of the VSwitch subnet. A VSwitch can only be associated with one route table, including the system route table.

To associate a custom route table with a VSwitch, follow these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com).
2.  In the left-side navigation pane, click **Route Tables**.
3.  On the Route Tables page, locate the target custom route table.
4.  Click the **Associated VSwitches** tab, and then click **Associate VSwitch**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17037/15547999318675_en-US.png)

5.  In the displayed dialog box, select the VSwitch to attach, and then click **OK**.
6.  Click the **Route Entry List** tab and add custom route entries.

    For more information, see [EN-US\_TP\_2437.md\#section\_k5r\_n5y\_rdb](reseller.en-US/User Guide/Routes/Add a custom route entry.md#section_k5r_n5y_rdb).


## Detach a custom route table from a VSwitch {#section_p1c_jjb_r2b .section}

You can detach a custom route table from a VSwitch. After a customer route table is detached, the VSwitch automatically uses the default route table if you do not associate it with another custom route table.

To detach a custom route table from a VSwitch, follow these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com).
2.  In the left-side navigation pane, click **Route Tables**.
3.  On the Route Tables page, click the ID of the target custom route table.
4.  On the **Associated VSwitches** page, locate the target VSwitch.
5.  Click **Unbind**. In the displayed dialog box, click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17037/15547999329790_en-US.png)


## Edit the custom route table {#section_svh_r4b_r2b .section}

To modify the name and description of a custom route table, follow these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com).
2.  In the left-side navigation pane, click **Route Tables**.
3.  On the Route Tables page, click the ID of the target custom route table.
4.  In the **Route Table Details** area, modify the name and description accordingly.

## Related operations {#section_f54_dlj_w2b .section}

[EN-US\_TP\_2437.md\#section\_k5r\_n5y\_rdb](reseller.en-US/User Guide/Routes/Add a custom route entry.md#section_k5r_n5y_rdb)

