# Switch the network type of a MongoDB instance {#concept_okq_mbv_sdb .concept}

This topic describes how to switch the network type of a MongoDB instance from classic network to VPC by using the console or by calling the relevant API action. When you switch the network type, you can specify a retention period for the classic network endpoint. After the retention period expires, the classic network endpoint is automatically deleted.

## Prerequisites {#section_vcx_2w5_sdb .section}

Before you can switch the network type, the following conditions must be met:

-   The network type is the classic network.

-   The instance type must be MongoDB replica set.

-   VPCs and VSwitches are available in the zone to which the MongoDB instance belongs. For more information, see [../../../../dita-oss-bucket/SP\_22/DNVPC11839992/EN-US\_TP\_2435.md\#section\_ufw\_rhv\_rdb](../../../../reseller.en-US/VPCs and VSwitches/VPC management/Create a VPC.md#section_ufw_rhv_rdb).


## Switch the network type by using the console {#section_p5v_fw5_sdb .section}

1.  Log on to the ApsaraDB for MongoDB console.
2.  Find the target instance, and then click the instance ID or click **Manage** in the **Actions** column.
3.  In the left-side navigation pane, click Database Connection, and then click **Switch to VPC**.
4.  In the displayed dialog box, complete these settings:
    1.  Select the target VPC and VSwitch.
    2.  Select to retain the classic network endpoint and select a retention period.

        **Note:** After you select to retain the classic network endpoint, classic-network ECS instances can access the database normally. When the classic network endpoint expires, it is automatically deleted and you cannot access the database through the classic network endpoint.

    3.  Click **OK**.
5.  On the Database Connection page, click **Refresh** to view the VPC endpoint and the classic network endpoint.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2463/1568792790844_en-US.png)


## Switch the network type by calling the relevant API action {#section_gyr_xw5_sdb .section}

1.  Download the SDK.
    -   [aliyun-python-sdk-dds.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57966/cn_zh/1502775994876/aliyun-python-sdk-dds.zip)
    -   [aliyun-java-sdk-dds.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57966/cn_zh/1502776029662/aliyun-java-sdk-dds.zip)
    -   [aliyun-php-sdk-dds.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57966/cn_zh/1502776047750/aliyun-php-sdk-dds.zip)
2.  Call the ModifyDBInstanceNetworkType to switch the network type.

    **Request parameters** 

    |Parameter|Type|Required?|Description|
    |:--------|:---|:--------|:----------|
    |Action|String|Yes|The name of this action. Valid value: ModifyDBInstanceNetworkType

 |
    |DBInstanceId|String|Yes|The ID of the Instance.|
    |NetworkType|String|Yes|The network type of the instance.     -   VPC: a VPC instance.
    -   Classic: a classic-network instance.
 |
    |VPCId|String|No|The ID of the VPC.|
    |VSwitchId|String|No| The ID of the VSwitch.

 This parameter must be specified if the VPC ID is specified.

 |
    |RetainClassic|String|No| Indicates whether to retain the classic network endpoint. Default: False.

    -   True: The classic network endpoint will be retained.
    -   False: The classic network endpoint will not be retained.
 |
    |ClassicExpiredDays|String|No| The retention period of the classic network endpoint in days. The shortest period is 1 day, the longest period is 120 days, and the default period is 7 days.

 This parameter must be specified if RetainClassic is set to True.

 |

    **Response parameters** 

    |Parameter|Type|Description|
    |:--------|:---|:----------|
    |RequestId|String|The ID of the request.|
    |TaskId|String|The ID of the task.|

3.  Call the DescribeReplicaSetRole API action to view the classic network endpoint and the VPC endpoint.

    **Request parameters**

    |Parameter|Type|Required?|Description|
    |:--------|:---|:--------|:----------|
    |Action|String|Yes|The name of this action. Valid value: DescribeReplicaSetRole

 |
    |DBInstanceId|String|Yes|The ID of the instance.|

    **Response parameters**

    |Parameter|Type|Description|
    |:--------|:---|:----------|
    |ReplicaSets|List|The list of replica set roles.|
    |DBInstanceId|String|The ID of the instance.|

    **ReplicaSetRole** 

    |Parameter|Type|Description|
    |:--------|:---|:----------|
    |ReplicaSetRole|String|The replica set role. Valid values: Primary | Secondary.|
    |ConnectionDomain|String|The connection domain of the instance.|
    |ConnectionPort|String|The connection port of the instance.|
    |ExpiredTime|String|The remaining retention period of the classic network endpoint in seconds.|
    |NetworkType|String|The network type of the instance.     -   VPC: a VPC instance.
    -   Classic: a classic-network instance.
 |


