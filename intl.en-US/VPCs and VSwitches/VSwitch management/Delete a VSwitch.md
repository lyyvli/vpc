# Delete a VSwitch {#task_1375158 .task}

This topic describes how to delete a VSwitch. After a VSwitch is deleted, cloud resources can no longer be deployed in the VSwitch.

Before you can delete a VSwitch, the following conditions must be met:

-   All cloud resources in the VSwitch, such as ECS, SLB, and RDS instances, are deleted.
-   The resources associated with the VSwitch, such as SNAT entries and HAVIP, are deleted.

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **VSwitches**.
3.  Select the region of the VPC to which the target VSwitch belongs.
4.  On the VSwitches page, find the target VSwitch, and then click **Delete** in the **Actions** column.
5.  In the Delete VSwitch dialog box, click **OK**.

