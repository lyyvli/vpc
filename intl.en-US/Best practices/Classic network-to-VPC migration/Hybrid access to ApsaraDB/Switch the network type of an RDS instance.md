# Switch the network type of an RDS instance {#concept_xnk_1w5_sdb .concept}

This topic describes how to switch the network type of an RDS instance from a classic network to a VPC by using the console or by calling the relevant API action.

For more information, see [Hybrid access solution for smooth migration from classic networks to VPCs](../../../../reseller.en-US/User Guide/Connection management/Hybrid access solution for smooth migration from classic networks to VPCs.md#).

**Note:** 

-   When you switch the network type, you can specify a retention period for the classic network endpoint. After the retention period expires, the classic network endpoint is automatically deleted. Before the endpoint is deleted, you will receive a message.

-   If the RDS instance is a subdatabase of a DRDS instance, the connection between the DRDS and the RDS instance will be broken after the network type is changed and must be manually reconnected.


## Prerequisites {#section_vcx_2w5_sdb .section}

-   The network type of the RDS instance is the classic network.

-   VPCs and VSwitches are available in the zone to which the RDS instance belongs. For more information, see [../../../../dita-oss-bucket/SP\_22/DNVPC11839992/EN-US\_TP\_2435.md\#](../../../../reseller.en-US/VPCs and VSwitches/VPC management/Create a VPC.md#).


## Method 1 - Switch the network type by using the console {#section_p5v_fw5_sdb .section}

1.  Log on to the ApsaraDB for RDS console.
2.  Select the region to which the target instance belongs.
3.  Click the ID of the target instance.
4.  In the left-side navigation pane, select **Database Connection**.
5.  On the Instance Connection tab page, click **Switch to VPC Network**.
6.  On the Switch to VPC Network page, select the target VPC and VSwitch.
7.  Select **Reserve original classic endpoint**, and then select the **Expiration time**.

    -   From the seventh day before the classic network endpoint is deleted, the system will send a message to the mobile phone associated with your account every day.

    -   When the classic network endpoint expires, it is automatically deleted and you cannot access the database through the classic network endpoint. To avoid service disruptions, set the retention period according to your specific needs. After you configure the hybrid access mode, you can change the expiration time.

8.  Click **OK**. An **Original classic endpoint** is added in the console.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2461/1568251430842_en-US.png)


## Modify the retention period of the classic network endpoint through the console {#section_pnk_cx5_sdb .section}

After you set the retention period for the classic network endpoint, you can extend the retention period by using the console before it expires.

During the hybrid access period, you can modify the retention period of the classic network endpoint at any time. For example, if the classic network endpoint is set to expire on August 18, 2017 and you modify the expiration date to 14 days later on August 15, 2017, the endpoint will be deleted on August 29, 2017.

1.  Log on to the ApsaraDB for RDS console.
2.  Select the region to which the target instance belongs.
3.  Click the ID of the target instance.
4.  In the left-side navigation pane, select **Database Connection**.
5.  On the Instance Connection tab page, click **Change Expiration Time**.
6.  Select the expiration time and click **OK**.

## Method 2 - Switch the network type by calling the relevant API action {#section_gyr_xw5_sdb .section}

1.  Download the SDK.
    -   [aliyun-java-sdk-rds-new.zip](http://sdk-release.oss-cn-hangzhou.aliyuncs.com/jarfiles/aliyun-java-sdk-rds-2.1.0.jar?spm=5176.143622.693811.15.tKN4aq&file=aliyun-java-sdk-rds-2.1.0.jar)

    -   [aliyun-python-sdk-rds-new.zip](https://pypi.python.org/pypi/aliyun-python-sdk-rds?spm=5176.143622.695759.10.vdzt6P)

    -   [aliyun-php-sdk-rds-new.zip](https://github.com/aliyun/aliyun-openapi-php-sdk)

2.  Call the ModifyDBInstanceNetworkType API action to switch the network type.

    **Request parameters**

    |Parameter|Type|Required?|Description|
    |:--------|:---|:--------|:----------|
    |Action|String|Yes|The name of this action. Valid value:ModifyDBInstanceNetworkType

|
    |DBInstanceId|String|Yes|The ID of the Instance.|
    |InstanceNetworkType|String|Yes|The network type of the instance. Valid values:    -   VPC: VPC instance.

    -   Classic: classic-network instance

|
    |VPCId|String|否|The ID of the VPC.|
    |VSwitchId|String|No|The ID of the VSwitch. This parameter must be specified if the VPC ID is specified.|
    |PrivateIpAddress|String|No|An IP address in the VSwitch CIDR block. If no IP address is entered, the system assigns a private IP address according to the VPC ID and the VSwitch ID.|
    |RetainClassic|String|No| Indicates whether to retain the classic network endpoint. Default: False.

    -   True: The classic network endpoint will be retained.
    -   False: The classic network endpoint will not be retained.
 |
    |ClassicExpiredDays|String|No| The retention period of the classic network endpoint in days. The shortest period is 1 day, the longest period is 180 days, and the default period is 7 days.

 This parameter must be specified if RetainClassic is set to True.

 |

    **Response parameters**

    |Parameter|Type|Description|
    |:--------|:---|:----------|
    |RequestId|String|The ID of the request.|
    |TaskId|String|The ID of the task.|

    **Example code**

    If you want to retain the classic network endpoint:

    -   Set the RetainClassic parameter to True.

    -   Set the ClassicExpiredDays parameter. After the classic network endpoint expires, it will be deleted.

    ```
    import com.aliyuncs.DefaultAcsClient;
     import com.aliyuncs.IAcsClient;
     import com.aliyuncs.exceptions.ClientException;
     import com.aliyuncs.exceptions.ServerException;
     import com.aliyuncs.profile.DefaultProfile;
     import com.aliyuncs.profile.IClientProfile;
     import com.aliyuncs.rds.model.v20140815.ModifyDBInstanceNetworkTypeRequest;
     import com.aliyuncs.rds.model.v20140815.ModifyDBInstanceNetworkTypeResponse;
     import org.junit.Test;
     public class ModifyDBInstanceNetworkTypeTest {
         @Test
         public  void switchNetwork_success() {
         ModifyDBInstanceNetworkTypeRequest request=new ModifyDBInstanceNetworkTypeRequest ();
             request.setInstanceId ("<Your instance ID>");
             request.setInstanceNetworkType ("VPC");
             request. setVPCId("<VpcId: This parameter is required when the TargetNetworkType is VPC>");
             request.setVSwitchId("<VSwitchId: This parameter is required when the TargetNetworkType is VPC>");
             request.setRetainClassic("<Whether to retain the classic network endpoint>");
             request.setClassicExpiredDays("The retention period of the classic network endpoint");
             IClientProfile profile = DefaultProfile.getProfile("cn-hangzhou", "<Your AK>",
                 "<Your Security>");
             IAcsClient client = new DefaultAcsClient(profile);
         try {
                 ModifyDBInstanceNetworkTypeResponse response
                     = client.getAcsResponse(request);
                 System.out.println(response.getRequestId());
         }catch (ServerException e) {
                 e.printStackTrace();
         }
             catch (ClientException e) {
                 e.printStackTrace();
             }
         }
     }
    ```

3.  Call the DescribeDBInstanceNetInfo API action to view the classic network endpoint and the VPC endpoint.

    **Request parameters**

    |Parameter|Type|Required?|Description|
    |:--------|:---|:--------|:----------|
    |Action|String|Yes|The name of this action. Valid value:DescribeDBInstanceNetInfo

|
    |DBInstanceId|String|Yes|The ID of the Instance.|

    **Response parameters**

    |Parameter|Type|Description|
    |:--------|:---|:----------|
    |DBInstanceNetInfos|List|The connection information of the instance.|
    |InstanceNetworkType|String|The network type of the instance. Valid values:    -   VPC: VPC instance.

    -   Classic: classic-network instance.

|

    **DBInstanceNetInfo**

    |Parameter|Type|Description|
    |:--------|:---|:----------|
    |ConnectionString|String|The connection string of DNS.|
    |IPAddress|String|The IP address.|
    |IPType|String| The IP address type of the classic-network instance: Inner | Public.

 The IP address type of the VPC instance: Private | Public.

 |
    |Port|String|The port information.|
    |VPCId|String|The ID of the VPC.|
    |VSwitchId|String|The ID of the VSwitch.|
    |ExpiredTime|String|The expiration time.|

    **Example code**

    ```
    import com.aliyuncs.IAcsClient;
     import com.aliyuncs.exceptions.ClientException;
     import com.aliyuncs.exceptions.ServerException;
     import com.aliyuncs.profile.DefaultProfile;
     import com.aliyuncs.profile.IClientProfile;
     import com.aliyuncs.rds.model.v20140815.DescribeDBInstanceNetInfoRequest;
     import com.aliyuncs.rds.model.v20140815.DescribeDBInstanceNetInfoResponse;
     import org.junit.Test;
     public class DescribeDBInstanceNetInfoTest {
         @Test
         public  void describeDBInstanceNetInfo_success() {
             DescribeDBInstanceNetInfoRequest request=new DescribeDBInstanceNetInfoRequest();
             request.setInstanceId("<Your instance ID>");
             IClientProfile profile = DefaultProfile.getProfile("cn-hangzhou", "<Your AK>",
                 "<Your Security>");
             IAcsClient client = new DefaultAcsClient(profile);
             try {
                 DescribeDBInstanceNetInfoResponse response
                     = client.getAcsResponse(request);
                 System.out.println(response.getRequestId());
         }catch (ServerException e) {
                 e.printStackTrace();
         }
             catch (ClientException e) {
                 e.printStackTrace();
             }
         }
     }
    ```


## Modify the retention period of the classic network endpoint through the relevant API {#section_a3s_sy5_sdb .section}

1.  Download the SDK.
    -   [aliyun-java-sdk-rds-new.zip](http://sdk-release.oss-cn-hangzhou.aliyuncs.com/jarfiles/aliyun-java-sdk-rds-2.1.0.jar?spm=5176.143622.693811.15.tKN4aq&file=aliyun-java-sdk-rds-2.1.0.jar)

    -   [aliyun-python-sdk-rds-new.zip](https://pypi.python.org/pypi/aliyun-python-sdk-rds?spm=5176.143622.695759.10.vdzt6P)

    -   [aliyun-php-sdk-rds-new.zip](https://github.com/aliyun/aliyun-openapi-php-sdk)

2.  Call the ModifyDBInstanceNetworkExpireTime API action to modify the retention period of the classic network endpoint.

    **Request parameters**

    |Parameter|Type|Required?|Description|
    |:--------|:---|:--------|:----------|
    |Action|String|Yes|The name of this action. Valid value:ModifyDBInstanceNetworkExpireTime

.|
    |DBInstanceId|String|Yes|The ID of the instance.|
    |ConnectionString|String|Yes|The classic network endpoint whose retention period you want to extend. Classic network endpoints are divided into the classic network endpoint of the current instance and the classic network endpoint with separate read and write.|
    |ClassicExpiredDays|Integer|Yes|The retention period of the classic network endpoint. Value range: 1 to 120 days.|

    **Response parameters**

    |Parameter|Type|Description|
    |:--------|:---|:----------|
    |RequestId|String|The ID of the request.|

    **Example code**

    ```
    public static void main(String[] args) {
         ModifyDBInstanceNetExpireTimeRequest request = new ModifyDBInstanceNetExpireTimeRequest();
         request.setClassicExpiredDays(3);
         request.setConnectionString("<The link string>");
         request.setDBInstanceId("<The instance ID>");
         IClientProfile profile
                 = DefaultProfile.getProfile("cn-qingdao", "<Your AK>",
                 "<Your SK>");
         IAcsClient client = new DefaultAcsClient(profile);
         try {
             ModifyDBInstanceNetExpireTimeResponse response
                     = client.getAcsResponse(request);
             System.out.println(response.getRequestId());
         }catch (ServerException e) {
             e.printStackTrace();
         }
         catch (ClientException e) {
             e.printStackTrace();
         }
     }
    ```


