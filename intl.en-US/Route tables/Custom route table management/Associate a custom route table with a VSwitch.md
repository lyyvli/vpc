# Associate a custom route table with a VSwitch {#task_1443302 .task}

This topic describes how to associate a custom route table with a VSwitch. After you associate a custom route table with a VSwitch, you can control the routes of the VSwitch \(subnet\). Each custom route table can be associated with more than one VSwitches, but each VSwitch can only be associated with one custom route table or system route table. However, after a VSwitch is associated with a custom route table, the system route table is automatically disassociated.

A VSwitch is created. For more information, see [Create a VSwitch](reseller.en-US/VPCs and VSwitches/VSwitch management/Create a VSwitch.md#).

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **Route Tables**.
3.  Select the region to which the target route table belongs.
4.  On the Route Tables page, find the target route table, and then click **Manage** in the **Actions** column.
5.  In the Route Table Details area, click the **Associated VSwitches** tab, and then click **Associate VSwitch**.
6.  On the Associate VSwitch page, select the target VSwitch, and then click **OK**.

