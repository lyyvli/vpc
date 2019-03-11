# Create a default VPC and VSwitch {#task_wtv_pwy_rdb .task}

If no VPC or VSwitch is available when you create an instance, you can use a default VPC or VSwitch. A default VPC and VSwitch can be created alongside a new instance. This topic describes how to create a default VPC or VSwitch when you create an instance by using an ECS instance as an example..

You can create only one default VPC in each region and only one default VSwitch in each zone of a VPC. The following table compares a default VPC with a default VSwitch:

|Default VPC|Default VSwitch|
|:----------|:--------------|
|The default VPC is unique in each region.|The default VSwitch is unique in each zone.|
|The mask for the default VPC is /16 \(for example, 172.31.0.0/16\), which provides up to 65,536 private IP addresses.|The mask for the default VSwitch is /20 \(for example, 172.31.0.0/20\), which provides up to 4,096 private IP addresses.|
|The default VPC is not included in the VPC quota.|The default VSwitch is not included in the VSwitch quota.|
|The default VPC is created by the system, and all VPCs created by you are non-default VPCs.|The default VSwitch is created by the system, and all VSwitches created by you are non-default VSwitches.|
|The operations and specifications for the default VPC and non-default VPCs are the same.|The operations and specifications for the default VSwitch and non-default VSwitches are the same.|

1.   Log on to the ECS console. 
2.   In the left-side navigation pane, click **Instances** and then click **Create Instance**. 
3.   Select **Advanced Purchase**. 
4.  On the Basic Configurations page, configure the ECS instance and click **Next: Networking**. 
5.  On the Networking page, select the **default VPC** and **default VSwitch**. Then click **Next: System Configurations**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2438/1552294066815_en-US.png)

6.  Configure the logon credential and instance name, and click **Create Order**. 

    After the instance is created, a default VPC and a default VSwitch will be created in the region.

    ![](images/816_en-US.png "Default VPC")

    ![](images/817_en-US.png "Default VSwitch")


