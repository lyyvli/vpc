# 云数据库 Redis 版网络切换 {#reference_c51_jz5_sdb .concept}

本文档介绍了如何通过控制台和API将云数据库Redis版的网络类型切换至专有网络，同时保留经典网络的访问地址。经典网络的访问地址有保留时间限制，您可以根据需要指定保留期限。到期后，经典网络地址会自动被系统删除。

## 前提条件 {#section_vcx_2w5_sdb .section}

在开始切换前，确认当前实例是否具备以下切换条件：

-   确认当前网络类型是否为经典网络。

-   确认在当前数据库实例可用区下是否有可用的VPC和交换机。详情参见[创建专有网络和交换机](../../../../../cn.zh-CN/用户指南/专有网络和子网/管理专有网络.md#section_ufw_rhv_rdb)。


## 通过控制台切换网络类型 {#section_p5v_fw5_sdb .section}

1.  登录云数据库Redis版管理控制台。
2.  选择目标实例所在地域。
3.  单击目标实例的ID。
4.  在实例信息页面，单击**切换为专有网络**。
5.  在弹出的对话框中，执行以下操作：
    1.  选择切换的目标专有网络和交换机。
    2.  选择保留经典网络地址并选择保留时长。

        **说明：** 选择保留经典网络地址后，专有网络地址和经典网络地址是两个不同的地址。经典网络下的ECS仍可访问数据，对业务无影响。 当经典网络地址到期后，系统会自动删除经典网络地址，您将无法通过经典网络地址访问数据库。

    3.  单击**确定**。
6.  在实例信息页面，单击**刷新**查看专有网络和经典网的访问地址。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2462/1555309471843_zh-CN.png)


## 通过控制台修改经典网络内网地址使用期限 {#section_pnk_cx5_sdb .section}

设置经典网络访问地址的保留时间后，您可以在过期前通过控制台延长其保留时间。

在混访期间，您可以根据需求随时调整保留原经典网络的时间，过期时间会从变更日期重新开始计时。例如，原经典网络的内网地址会在2017年8月18日过期，但您在2017年8月15日将过期时间变更为14天后，则原经典网络的内网地址将会在2017年8月29日被释放。

1.  登录云数据库Redis版管理控制台。
2.  选择目标实例所在地域。
3.  单击目标实例的ID。
4.  在**预留的经典IP地址**区域，单击**修改过期时间**。
5.  在弹出的对话框中，选择新的过期时间，然后单击**确定**。

## 通过API切换网络类型 {#section_gyr_xw5_sdb .section}

1.  单击SDK链接下载相关SDK。（云数据库Memcache版和Redis版的SDK相同。）
    -   [aliyun-java-sdk- r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897538196/aliyun-java-sdk-r-kvstore.zip)

    -   [aliyun-python-sdk- r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897520896/aliyun-python-sdk-r-kvstore.zip)

    -   [aliyun-php-sdk-r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897558248/aliyun-php-sdk-r-kvstore.zip)

2.  调用SwitchNetwork接口进行网络切换。

    **请求参数说明** 

    |名称|类型|是否必须|说明|
    |:-|:-|:---|:-|
    |Action|String|是|系统规定参数，取值： SwitchNetwork

 |
    |InstanceId|String|是|实例 ID。|
    |TargetNetworkType|String|是|实例的网络类型：     -   VPC：专有网络
    -   Classic：经典网络
 |
    |VPCId|String|否|专有网络的ID。|
    |VSwitchId|String|否| 交换机的ID。

 如果指定了VPC ID，则该参数也必须指定。

 |
    |RetainClassic|String|否| 是否保留经典网络地址，默认False：

    -   True：保留
    -   False：不保留
 |
    |ClassicExpiredDays|String|否| 经典网络地址保留的天数，最短1天，最长120天，默认7天。

 若选择保留经典网络地址，则该参数必传。

 |

    **返回参数说明** 

    |参数|类型|说明|
    |:-|:-|:-|
    |RequestId|String|请求ID。|
    |TaskId|String|任务ID。|

    **参考代码**

    ```
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
             request.setInstanceId("<您的实例ID>");
             request.setTargetNetworkType("VPC");
             request.setVpcId("<VpcId:当TargetNetworkType时VPC时必填>");
             request.setVSwitchId("<VSwitchId:当TargetNetworkType为VPC时必填>");
             request.setRetainClassic("<是否保留CLASSIC的网络链接，True保留，False不保留>");
             request.setClassicExpiredDays("保留CLASSIC的网络链接的天数");
             IClientProfile profile = DefaultProfile.getProfile("cn-hangzhou", "<您的AK>",
                 "<您的Security>");
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

3.  调用DescribeDBInstanceNetInfo接口查看经典网络和专有网络的访问地址。

    **请求参数**

    |名称|类型|是否必须|说明|
    |:-|:-|:---|:-|
    |Action|String|是|系统规定参数，取值： DescribeDBInstanceNetInfo

 |
    |InstanceId|String|是|实例ID。|

    **返回参数** 

    |参数|类型|说明|
    |:-|:-|:-|
    |NetInfoItems|List|实例的连接信息。|
    |InstanceNetworkType|String|实例的网络类型：     -   VPC：VPC类型的实例。

    -   Classic：经典网络类型的实例。

 |

    **InstanceNetInfo数据结构** 

    |参数|类型|说明|
    |:-|:-|:-|
    |ConnectionString|String|DNS连接串。|
    |IPAddress|String|IP地址。|
    |IPType|String| 经典网络类型的实例的IP类型有：Inner | Public。

 VPC类型的实例的IP类型有：Private | Public。

 |
    |Port|String|端口信息。|
    |VPCId|String|VPC ID。|
    |VSwitchId|String|交换机ID。|
    |ExpiredTime|String|过期时间。|

    **参考代码** 

    ```
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
             request.setInstanceId("<您的实例ID>");
             IClientProfile profile = DefaultProfile.getProfile("cn-hangzhou", "<您的AK>",
                 "<您的Security>");
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


## 通过API修改经典网络内网地址使用期限 {#section_a3s_sy5_sdb .section}

1.  单击SDK链接下载相关SDK。（云数据库Memcache版和Redis版的SDK相同。）
    -   [aliyun-java-sdk- r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897538196/aliyun-java-sdk-r-kvstore.zip)

    -   [aliyun-python-sdk- r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897520896/aliyun-python-sdk-r-kvstore.zip)

    -   [aliyun-php-sdk-r-kvstore.zip](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/57965/cn_zh/1505897558248/aliyun-php-sdk-r-kvstore.zip)

2.  调用ModifyInstanceNetExpireTime接口进行网络切换。

    **请求参数说明** 

    |名称|类型|是否必须|说明|
    |:-|:-|:---|:-|
    |Action|String|是|系统规定参数，取值： ModifyInstanceNetExpireTime

 。|
    |InstanceId|String|是|实例ID。|
    |ConnectionString|String|是|经典网络的访问域名。|
    |ClassicExpiredDays|Integer|是| 选择保留时长。

 取值：14、30、60或120

 |

    **返回参数** 

    |参数|类型|说明|
    |:-|:-|:-|
    |RequestId|String|请求ID。|

    **参考代码**

    ```
    public static void main(String[] args) {
         ModifyInstanceNetExpireTimeRequest request = new ModifyInstanceNetExpireTimeRequest();
         request.setClassicExpiredDays(3);
         request.setConnectionString("<链接字符串>");
         request.setInstanceId("<实例Id>");
         IClientProfile profile
                 = DefaultProfile.getProfile("cn-hangzhou", "<你的ak>",
                 "<你的sk>");
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


