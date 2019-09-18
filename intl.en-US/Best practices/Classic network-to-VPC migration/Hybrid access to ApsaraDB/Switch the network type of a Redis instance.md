# Switch the network type of a Redis instance {#reference_c51_jz5_sdb .concept}

This topic describes how to switch the network type of a Redis instance from classic network to VPC by using the console or by calling the relevant API action. When you switch the network type, you can specify a retention period for the classic network endpoint. After the retention period expires, the classic network endpoint is automatically deleted.

## Prerequisites {#section_vcx_2w5_sdb .section}

Before you can switch the network type, the following conditions must be met:

-   The network type of the Redis instance is the classic network.

-   VPCs and VSwitches are available in the zone to which the Redis instance belongs. For more information, see [../../../../dita-oss-bucket/SP\_22/DNVPC11839992/EN-US\_TP\_2435.md\#section\_ufw\_rhv\_rdb](../../../../reseller.en-US/VPCs and VSwitches/VPC management/Create a VPC.md#section_ufw_rhv_rdb).


## Switch the network type by using the console {#section_p5v_fw5_sdb .section}

1.  Log on to the ApsaraDB for Redis console.
2.  Select the region to which the target instance belongs.
3.  Click the ID of the target instance.
4.  On the Instance Information page, click **Switch to VPC Network**.
5.  In the displayed dialog box, complete these settings:
    1.  Select the target VPC and VSwitch.
    2.  Select to retain the classic network endpoint and select a retention period.

        **Note:** After you select to retain the classic network endpoint, the classic network endpoint and the VPC endpoint remain two different endpoints. As a result, ECS instances in the classic network can still access the database and services are not affected. When the classic network endpoint expires, it is automatically deleted and you cannot access the database through the classic network endpoint.

    3.  Click **OK**.
6.  On the Instance Information page, click **Refresh** to view the VPC endpoint and classic network endpoint.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2462/1568792735843_en-US.png)


## Modify the retention period of the classic network endpoint through the console {#section_pnk_cx5_sdb .section}

After you set the retention period for the classic network endpoint, you can extend the retention period by using the console before it expires.

During the hybrid access period, you can modify the retention period of the classic network endpoint at any time. For example, if the classic network endpoint is set to expire on August 18, 2017 and you modify the expiration date to 14 days later on August 15, 2017, the endpoint will be released on August 29, 2017.

1.  Log on to the ApsaraDB for Redis console.
2.  Select the region to which the target instance belongs.
3.  Click the ID of the target instance.
4.  In the **Retained Classic Network IP Address** area, click **Change Expiration Date**.
5.  In the displayed dialog box, select a new expiration date, and then click **OK**.

## Switch the network type by calling the relevant API action {#section_gyr_xw5_sdb .section}

1.  Download the SDK. The SDK of ApsaraDB for Memcache is the same as that of ApsaraDB for Redis.
    -   [aliyun-java-sdk- r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897538196/aliyun-java-sdk-r-kvstore.zip)

    -   [aliyun-python-sdk- r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897520896/aliyun-python-sdk-r-kvstore.zip)

    -   [aliyun-php-sdk-r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897558248/aliyun-php-sdk-r-kvstore.zip)

2.  Call the SwitchNetwork API action to switch the network type.

    **Request parameters** 

    |Parameter|Type|Required?|Description|
    |:--------|:---|:--------|:----------|
    |Action|String|Yes|The name of this action. Valid value: SwitchNetwork

 |
    |InstanceId|String|Yes|The ID of the instance.|
    |TargetNetworkType|String|Yes|The network type of the instance. Valid values:     -   VPC: a VPC instance
    -   Classic: a classic-network instance
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

    **Example code**

    ``` {#codeblock_1xe_tnq_dcq}
    import com.aliyuncs.DefaultAcsClient;
     import com.aliyuncs.IAcsClient;
     import com.aliyuncs.exceptions.ClientException;
     import com.aliyuncs.exceptions.ServerException;
     import com.aliyuncs.profile.DefaultProfile;
     import com.aliyuncs.profile.IClientProfile;
     import com.aliyuncs.r_kvstore.model.v20150101.SwitchNetworkRequest;
     import com.aliyuncs.r_kvstore.model.v20150101.SwitchNetworkResponse;
     import org.junit.Test;
     /**
      * Created by wb259286 on 2017/6/9.
      */
     public class SwitchNetworkTest {
         @Test
         public  void switchNetwork_success() {
             SwitchNetworkRequest request=new SwitchNetworkRequest();
             request.setInstanceId("<your instance ID>");
             request.setTargetNetworkType("VPC");
             request.setVpcId("<VpcId: This parameter is required when the TargetNetworkType is VPC>");
             request.setVSwitchId("<VSwitchId: This parameter is required when the TargetNetworkType is VPC>");
             request.setRetainClassic("<Whether to retain the classic network endpoint.>");
             request.setClassicExpiredDays("The retention period of the classic network endpoint");
             IClientProfile profile = DefaultProfile.getProfile("cn-hangzhou", "<Your AK>",
                 "<Your Security>");
             IAcsClient client = new DefaultAcsClient(profile);
             try {
                 SwitchNetworkResponse response
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
    |Action|String|Yes|The name of this action. Valid value: DescribeDBInstanceNetInfo

 |
    |InstanceId|String|Yes|The ID of the instance.|

    **Response parameters** 

    |Parameter|Type|Description|
    |:--------|:---|:----------|
    |NetInfoItems|List|The connection information of the instance.|
    |InstanceNetworkType|String|The network type of the instance. Valid values:     -   VPC: a VPC instance.

    -   Classic: a classic-network instance.

 |

    **InstanceNetInfo** 

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

    ``` {#codeblock_jab_e1z_5um}
    import com.aliyuncs.DefaultAcsClient;
     import com.aliyuncs.IAcsClient;
     import com.aliyuncs.exceptions.ClientException;
     import com.aliyuncs.exceptions.ServerException;
     import com.aliyuncs.profile.DefaultProfile;
     import com.aliyuncs.profile.IClientProfile;
     import com.aliyuncs.r_kvstore.model.v20150101.DescribeDBInstanceNetInfoRequest;
     import com.aliyuncs.r_kvstore.model.v20150101.DescribeDBInstanceNetInfoResponse;
     import org.junit.Test;
     /**
      *
      */
     public class DescribeDBInstanceNetInfoTest {
     @Test
         public  void describeDBInstanceNetInfo_success() {
             DescribeDBInstanceNetInfoRequest request=new     DescribeDBInstanceNetInfoRequest();
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

1.  Download the SDK. The SDK of ApsaraDB for Memcache is the same as that of ApsaraDB for Redis.
    -   [aliyun-java-sdk- r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897538196/aliyun-java-sdk-r-kvstore.zip)

    -   [aliyun-python-sdk- r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897520896/aliyun-python-sdk-r-kvstore.zip)

    -   [aliyun-php-sdk-r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897558248/aliyun-php-sdk-r-kvstore.zip)

2.  Call the ModifyInstanceNetExpireTime API action to switch the network type.

    **Request parameters** 

    |Parameter|Type|Required?|Description|
    |:--------|:---|:--------|:----------|
    |Action|String|Yes|The name of this action. Valid value: ModifyInstanceNetExpireTime

 .|
    |InstanceId|String|Yes|The ID of the instance.|
    |ConnectionString|String|Yes|The classic network endpoint.|
    |ClassicExpiredDays|Integer|Yes| The retention period.

 Valid values: 14, 30, 60, or 120.

 |

    **Response parameters** 

    |Parameter|Type|Description|
    |:--------|:---|:----------|
    |RequestId|String|The ID of the request.|

    **Example code**

    ``` {#codeblock_rri_kzj_mc8}
    public static void main(String[] args) {
         ModifyInstanceNetExpireTimeRequest request = new ModifyInstanceNetExpireTimeRequest();
         request.setClassicExpiredDays(3);
         request.setConnectionString("<link string>");
         request.setInstanceId("<instance Id>");
         IClientProfile profile
                 = DefaultProfile.getProfile("cn-hangzhou", "<Your AK>",
                 "<Your SK>");
         IAcsClient client = new DefaultAcsClient(profile);
         try {
             ModifyInstanceNetExpireTimeResponse response
                     = client.getAcsResponse(request);
             for (NetInfoItem item:response.getNetInfoItems()) {
                 System.out.println(item.getConnectionString());
                 System.out.println(item.getPort());
                 System.out.println(item.getDBInstanceNetType());
                 System.out.println(item.getIPAddress());
                 System.out.println(item.getExpiredTime());
             }
         }catch (ServerException e) {
             e.printStackTrace();
         }
         catch (ClientException e) {
             e.printStackTrace();
         }
     }
    ```


