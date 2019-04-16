# Change the network type of ApsaraDB for Redis {#reference_c51_jz5_sdb .concept}

This document describes how to switch the network type of an ApsaraDB for Redis instance to a VPC network through the console and API while preserving the classic network endpoint. The classic network endpoint has a retention time limit. You can specify a retention period as needed. When the retention time is reached, the classic network endpoint is automatically deleted by the system. Before the endpoint is deleted, you will receive a message.

## Prerequisites {#section_vcx_2w5_sdb .section}

Before changing the network type, make sure that the following conditions are met:

-   Make sure the network type of the instance is the classic network.

-   There are available VPC and VSwitches in the zone where the Redis instance is located. For more information, see [Create a VPC and a VSwitch](../../../../reseller.en-US/User Guide/VPC and subnets/Manage a VPC.md#section_ufw_rhv_rdb).


## Change the network type on the console {#section_p5v_fw5_sdb .section}

1.  Log on to the Redis Console.
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance.
4.  On the Instance Information page, click **Switch to VPC**.
5.  In the displayed dialog box, complete these steps:
    1.  Select the target VPC and VSwitch.
    2.  Select to retain the classic network endpoint and select the retention time.

        **Note:** After you select to retain the classic network endpoint, the classic network endpoint and the VPC endpoint remain as two independent endpoints. As a result, ECS instances of the classic network can still access the database and the service is not affected. When the classic network endpoint expires, the system automatically deletes the classic network endpoint and you cannot access the database through the classic network endpoint.

    3.  Click **OK**.
6.  On the Instance Information page, click **Refresh** to view the VPC endpoint and classic network endpoint.

## Modify the retention time {#section_pnk_cx5_sdb .section}

After setting the retention time for the classic network endpoint, you can extend its retention time through the console before it expires.

During the hybrid access period, you can change the retention time of the classic network endpoint at any time as needed. For example, if the classic network endpoint is set to expire on August 18, 2017 and you change the expiration date to 14 days later on August 15, 2017, the endpoint will be released on August 29, 2017.

1.  Log on to the Redis Console.
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance.
4.  In the **Retained Connection Address of the Classic Network** area, click **Modify Retention Period**.
5.  In the displayed dialog box, select a new expiration date and click **OK**.

## Change the network type through API {#section_gyr_xw5_sdb .section}

1.  Download the SDK. \(The SDK of ApsaraDB for Memcache is the same as that of ApsaraDB for Redis\).
    -   [aliyun-java-sdk- r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897538196/aliyun-java-sdk-r-kvstore.zip)

    -   [aliyun-python-sdk- r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897520896/aliyun-python-sdk-r-kvstore.zip)

    -   [aliyun-php-sdk-r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897558248/aliyun-php-sdk-r-kvstore.zip)

2.  Call the SwitchNetwork API to change the network type.

    **Request parameters** 

    |Name|Type|Required|Description|
    |:---|:---|:-------|:----------|
    |Action|String|Yes|The action to perform. Valid value: SwitchNetwork

 |
    |InstanceId|String|Yes|The ID of the instance.|
    |TargetNetworkType|String|Yes|The network type of the instance.     -   VPC: VPC
    -   Classic: Classic network
 |
    |VPCId|String|No|The ID of the VPC.|
    |VSwitchId|String|No| The ID of the VSwitch.

 This parameter must be specified if VPC ID is specified.

 |
    |RetainClassic|String|No| Whether to retain the classic network endpoint. The default value is False:

    -   True: Retain
    -   False: Do not retain
 |
    |ClassicExpiredDays|String|No| The retention time of the classic network endpoint. The shortest time is 1 day, the longest time is 120 days, and the default value is 7 days.

 This parameter must be specified if RetainClassic is set to True.

 |

    **Response parameters** 

    |Name|Type|Description|
    |:---|:---|:----------|
    |RequestId|String|The ID of the request.|
    |TaskId|String|The ID of the task.|

    **Example code**

    ```
    import com.aliyuncs.DefaultAcsClient;
     import com.aliyuncs.IAcsClient;
     import com.aliyuncs.exceptions.ClientException;
     import com.aliyuncs.exceptions.ServerException;
     import com.aliyuncs.profile.DefaultProfile;
     import com.aliyuncs.profile.IClientProfile;
     import com.aliyuncs.r_kvstore.model.v20150101. SwitchNetworkRequest;
     import com.aliyuncs.r_kvstore.model.v20150101. SwitchNetworkResponse;
     Import org. JUnit. test;
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
             request.setClassicExpiredDays("The retention time of the classic network endpoint");
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

3.  Call the DescribeDBInstanceNetInfo API to view the classic network endpoint and the VPC endpoint.

    **Request parameters**

    |Name|Type|Required|Description|
    |:---|:---|:-------|:----------|
    |Action|String|Yes|The action to perform. Valid value: DescribeDBInstanceNetInfo

 |
    |InstanceId|String|Yes|The ID of the instance.|

    **Response parameters** 

    |Name|Type|Description|
    |:---|:---|:----------|
    |NetInfoItems|List|The connection information of the instance.|
    |InstanceNetworkType|String|The network type of the instance.     -   VPC: An instance of the VPC network.

    -   Classic: An instance of the classic network.

 |

    **InstanceNetInfo** 

    |Name|Type|Description|
    |:---|:---|:----------|
    |ConnectionString|String|The connection string of DNS.|
    |IPAddress|String|The IP address.|
    |IPType|String| The IP type of an instance of the classic network: Inner | Public.

 The IP type of an instance of the VPC network: Private | Public.

 |
    |Port|String|The port information.|
    |VPCId|String|The ID of the VPC.|
    |VSwitchId|String|The ID of the VSwitch.|
    |ExpiredTime|String|The time of expiration.|

    **Example code** 

    ```
    import com.aliyuncs.DefaultAcsClient;
     import com.aliyuncs.IAcsClient;
     import com.aliyuncs.exceptions.ClientException;
     import com.aliyuncs.exceptions.ServerException;
     import com.aliyuncs.profile.DefaultProfile;
     import com.aliyuncs.profile.IClientProfile;
     import com.aliyuncs.r_kvstore.model.v20150101. DescribeDBInstanceNetInfoRequest;
     import com.aliyuncs.r_kvstore.model.v20150101. DescribeDBInstanceNetInfoResponse;
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


## Modify the retention time of the classic network endpoint through API {#section_a3s_sy5_sdb .section}

1.  Click the SDK link to download the SDK. \( The SDK of ApsaraDB for Memcache is the same as that of ApsaraDB for Redis.\)
    -   [aliyun-java-sdk- r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897538196/aliyun-java-sdk-r-kvstore.zip)

    -   [aliyun-python-sdk- r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897520896/aliyun-python-sdk-r-kvstore.zip)

    -   [aliyun-php-sdk-r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897558248/aliyun-php-sdk-r-kvstore.zip)

2.  Call the ModifyInstanceNetExpireTime API to change the network type.

    **Request parameters** 

    |Name|Type|Required|Description|
    |:---|:---|:-------|:----------|
    |Action|String|Yes|The action to perform. Valid value: ModifyInstanceNetExpireTime

 .|
    |InstanceId|String|Yes|The ID of the instance.|
    |ConnectionString|String|Yes|The classic network endpoint.|
    |ClassicExpiredDays|Interger|Yes| Select the retention time.

 Valid values: 14, 30, 60, or 120.

 |

    **Response parameters** 

    |Name|Type|Description|
    |:---|:---|:----------|
    |RequestId|String|The ID of the request.|

    **Example code**

    ```
    public static void main(String[] args) {
         ModifyInstanceNetExpireTimeRequest request = new ModifyInstanceNetExpireTimeRequest();
         request.setClassicExpiredDays(3);
         request.setConnectionString("<link string>");
         request.setInstanceId("<instance Id>");
         IClientProfile profile
                 = DefaultProfile.getProfile("cn-hangzhou", "<Your ak>",
                 "<Your sk>");
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
         } catch (ServerException e) {
             e.printStackTrace();
         }
         } catch (ClientException e) {
             e.printStackTrace();
         }
     }
    ```


