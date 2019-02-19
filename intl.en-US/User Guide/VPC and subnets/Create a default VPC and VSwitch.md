# Create a default VPC and VSwitch {#task_wtv_pwy_rdb .task}

If there is no available VPC and VSwitch to use when creating a cloud resource with the VPC network, you can choose to use the default VPC and VSwitch. A default VPC and VSwitch are created along with the creation of the instance. This document takes ECS as an example to introduce how to create a default VPC and VSwitch.

A region can only have one default VPC but many default VSwitches. Because VPC is a region-based resource while VSwitch is a zone-based resource. Each zone can have a default VSwitch. The properties of default VPC and VSwitch are as follows:

|Default VPC|Default VSwitch|
|:----------|:--------------|
|The default VPC in each region is unique.|The default VSwitch in each zone is unique.|
|The netmask for a default VPC is /16, such as 172.31.0.0/16, providing up to 65536 private IP addresses.|The netmask for a default VSwitch is /20, such as 172.31.0.0/20, providing up to 4096 private IP addresses.|
|The default VPC does not take up the VPC quota.|The default VSwitch does not take up the VSwitch quota.|
|The default VPC is created by the system, and all VPCs created by you are non-default VPCs.|The default VSwitch is created by the system, and all VSwitches created by you are non-default VSwitches.|
|The operations and specifications for the default VPC and non-default VPCs are the same.|The operations and specifications for the default VSwitch and non-default VSwitches are the same.|

1.   Log on to the ECS console. 
2.   In the left-side navigation pane, click **Instances** and then click **Create Instance**. 
3.   Select **Advanced Purchase**. 
4.   On the Basic Configurations page, configure ECS instance and click **Next: Networking**. 
5.   On the Networking page, select **default VPC** and the **default VSwitch**. Click **Next: System Configurations**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2438/1550556199815_en-US.png)

6.   Configure the login credential and instance name, and click **Create Order**. 

    After the instance is created, a default VPC and a default VSwitch will be created in the region.

    ![](images/816_en-US.png "Default VPC")

    ![](images/817_en-US.png "Default VSwitch")


