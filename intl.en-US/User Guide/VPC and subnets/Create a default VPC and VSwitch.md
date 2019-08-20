# Create a default VPC and VSwitch {#task_wtv_pwy_rdb .task}

This topic describes how to create a default VPC and a default VSwitch when you create an instance. A default VPC and a default VSwitch are created automatically by the system after the instance is created. This topic uses an ECS instance as an example.

You can create only one default VPC in each region and only one default VSwitch in each zone of a VPC. The following table compares a default VPC with a default VSwitch.

|Default VPC|Default VSwitch|
|:----------|:--------------|
|The default VPC is unique in each region.|The default VSwitch is unique in each zone.|
|The mask for the default VPC is /16 \(for example, 172.31.0.0/16\), which provides up to 65,536 private IP addresses.|The mask for the default VSwitch is /20 \(for example, 172.16.0.0/20\), which provides up to 4,096 private IP addresses.|
|The default VPC is not included in the VPC quota.|The default VSwitch is not included in the VSwitch quota.|
|The default VPC is created by the system. All VPCs that you create are non-default VPCs.|The default VSwitch is created by the system. All VSwitches that you create are non-default VSwitches.|
|The operations and specifications for the default VPC and non-default VPCs are the same.|The operations and specifications for the default VSwitch and non-default VSwitches are the same.|

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.
3.  On the Instances page, click **Create Instance**.
4.  Select **Custom Launch**.
5.  On the Basic Configurations page, set the basic parameters, and then click **Next: Networking**.
6.  On the Networking page, select the **Default VPC** and the **Default VSwitch**, and then click **Next: System Configurations**. 

    ![Default VPC and VSwitch](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2438/1566299496815_en-US.png)

7.  Set the logon credential and instance name, and then click **Next: Grouping**. 

    After the ECS instance is created, a default VPC and a default VSwitch is also created in the region.

    ![Default VPC](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2438/1566299496816_en-US.png)

    ![Default VSwitch](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2438/1566299496817_en-US.png)


