# 云数据库RDS版网络切换 {#concept_xnk_1w5_sdb .concept}

您可以通过控制台和API将云数据库RDS版的网络类型切换至专有网络，同时保留经典网络的访问地址。

关于RDS平滑迁移网络的原理介绍，请参见[经典网络平滑迁移到VPC的混访方案](../../../../intl.zh-CN/用户指南/数据库连接/经典网络平滑迁移到VPC的混访方案.md#)。

**说明：** 

-   经典网络的访问地址有保留时间限制，您可以根据需要指定保留期限。到期后，经典网络地址会自动被系统删除。在正式删除前，您会收到短信提醒。

-   如果要切换的RDS实例是DRDS实例的一个分库，当RDS切换了网络类型后，DRDS与RDS之间的网络连通性会被破坏，需要手动修复。


## 前提条件 {#section_vcx_2w5_sdb .section}

-   实例的网络类型是经典网络。

-   实例所在可用区已有可用的VPC和交换机。详情参见[管理专有网络](../../../../intl.zh-CN/专有网络和交换机/管理专有网络/创建专有网络.md#)。


## 通过控制台切换网络类型 {#section_p5v_fw5_sdb .section}

1.  登录RDS管理控制台。
2.  选择目标实例所在地域。
3.  单击目标实例的ID。
4.  在左侧导航栏中选择**数据库连接**。
5.  在实例连接标签页中，单击**切换为专有网络**。
6.  在切换为专有网络页面，选择要切换到的VPC及交换机。
7.  勾选**保留原经典网络**，并选择原经典网络内网地址的**过期时间**。

    -   从要删除原经典网络地址前的第7天开始，系统会每天给您账号绑定的手机发送提示短信。

    -   原经典网络内网地址的保留时间到期后，内网地址会被自动释放，您将无法通过经典网络的内网地址访问数据库。为避免业务中断，请根据实际需求设置保留时间。混访设置成功后，您可以修改过期时间。

8.  单击**确定**，控制台会增加**保留的经典网络地址**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2461/1568769588842_zh-CN.png)


## 通过控制台修改经典网络内网地址使用期限 {#section_pnk_cx5_sdb .section}

设置经典网络访问地址的保留时间后，您可以在过期前通过控制台延长其保留时间。

在混访期间，您可以根据需求随时调整保留原经典网络的时间，过期时间会从变更日期重新开始计时。例如，原经典网络的内网地址会在2017年8月18日过期，但您在2017年8月15日将过期时间变更为“14天后”，则原经典网络的内网地址将会在2017年8月29日被释放。

1.  登录RDS管理控制台。
2.  选择目标实例所在地域。
3.  单击目标实例的ID。
4.  在左侧导航栏中选择**数据库连接**。
5.  在实例连接标签页中，单击**修改过期时间**。
6.  选择过期时间，然后单击**确定**。

## 通过API切换网络类型 {#section_gyr_xw5_sdb .section}

1.  单击SDK链接下载相关SDK。
    -   [aliyun-java-sdk-rds-new.zip](http://sdk-release.oss-cn-hangzhou.aliyuncs.com/jarfiles/aliyun-java-sdk-rds-2.1.0.jar?spm=5176.143622.693811.15.tKN4aq&file=aliyun-java-sdk-rds-2.1.0.jar)

    -   [aliyun-python-sdk-rds-new.zip](https://pypi.python.org/pypi/aliyun-python-sdk-rds?spm=5176.143622.695759.10.vdzt6P)

    -   [aliyun-php-sdk-rds-new.zip](https://github.com/aliyun/aliyun-openapi-php-sdk)

2.  调用ModifyDBInstanceNetworkType接口进行网络切换。

    **请求参数说明** 

    |名称|类型|是否必须|说明|
    |:-|:-|:---|:-|
    |Action|String|是|系统规定参数，取值： ModifyDBInstanceNetworkType

 |
    |DBInstanceId|String|是|实例ID。|
    |InstanceNetworkType|String|是|实例的网络类型：     -   VPC：VPC类型的实例。

    -   Classic：经典网络类型的实例。

 |
    |VPCId|String|否|专有网络的ID|
    |VSwitchId|String|否|交换机的ID，如果指定了VPC ID，则该参数也必须指定。|
    |PrivateIpAddress|String|否|输入交换机网段内的一个IP地址。如果不输入，系统根据VPC ID和交换机ID自动分配一个私网IP地址。|
    |RetainClassic|String|否| 是否保留经典网络地址，默认False：

    -   True：保留
    -   False：不保留
 |
    |ClassicExpiredDays|String|否| 经典网络地址保留的天数，最短1天，最长180天，默认7天。

 若选择保留经典网络地址，则该参数必传。

 |

    **返回参数说明** 

    |参数|类型|说明|
    |:-|:-|:-|
    |RequestId|String|请求ID。|
    |TaskId|String|任务ID。|

    **参考代码**

    当要选择保留经典网络地址时:

    -   配置RetainClassic参数，设置为True，保留经典网络地址。

    -   配置ClassicExpiredDays参数，设置保留时间。到期后将删除经典网络地址。

    ``` {#codeblock_2if_yid_oil}
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
             request.setInstanceId("<您的实例ID>");
             request.setInstanceNetworkType ("VPC");
             request. setVPCId("<VpcId:当TargetNetworkType为VPC时必填>");
             request.setVSwitchId("<VSwitchId:当TargetNetworkType时VPC时必填>");
             request.setRetainClassic("<是否保留CLASSIC的网络链接：True保留，False不保留>");
             request.setClassicExpiredDays("保留CLASSIC的网络链接的天数");
             IClientProfile profile = DefaultProfile.getProfile("cn-hangzhou", "<您的AK>",
                 "<您的Security>");
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

3.  调用DescribeDBInstanceNetInfo接口查看经典网络和专有网络的访问地址。

    **请求参数**

    |名称|类型|是否必须|说明|
    |:-|:-|:---|:-|
    |Action|String|是|系统规定参数，取值： DescribeDBInstanceNetInfo

 |
    |DBInstanceId|String|是|实例ID。|

    **返回参数** 

    |参数|类型|说明|
    |:-|:-|:-|
    |DBInstanceNetInfos|List|实例的连接信息。|
    |InstanceNetworkType|String|实例的网络类型：     -   VPC：VPC类型的实例。

    -   Classic：经典网络类型的实例。

 |

    **DBInstanceNetInfo数据结构** 

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

    ``` {#codeblock_t7f_52r_gql}
    import com.aliyuncs.IAcsClient;
     import com.aliyuncs.exceptions.ClientException;
     import com.aliyuncs.exceptions.ServerException;
     import com.aliyuncs.profile.DefaultProfile;
     import com.aliyuncs.profile.IClientProfile;
     import com.aliyuncs.rds.model.v20140815.DescribeDBInstanceNetInfoRequest;
     import import com.aliyuncs.rds.model.v20140815.DescribeDBInstanceNetInfoResponse;
     import org.junit.Test;
     public class DescribeDBInstanceNetInfoTest {
         @Test
         public  void describeDBInstanceNetInfo_success() {
             DescribeDBInstanceNetInfoRequest request=new DescribeDBInstanceNetInfoRequest();
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

1.  单击SDK链接下载相关SDK。
    -   [aliyun-java-sdk-rds-new.zip](http://sdk-release.oss-cn-hangzhou.aliyuncs.com/jarfiles/aliyun-java-sdk-rds-2.1.0.jar?spm=5176.143622.693811.15.tKN4aq&file=aliyun-java-sdk-rds-2.1.0.jar)

    -   [aliyun-python-sdk-rds-new.zip](https://pypi.python.org/pypi/aliyun-python-sdk-rds?spm=5176.143622.695759.10.vdzt6P)

    -   [aliyun-php-sdk-rds-new.zip](https://github.com/aliyun/aliyun-openapi-php-sdk)

2.  调用ModifyDBInstanceNetworkExpireTime接口修改经典网络使用期限。

    **请求参数说明** 

    |名称|类型|是否必须|说明|
    |:-|:-|:---|:-|
    |Action|String|是|系统规定参数，取值： ModifyDBInstanceNetworkExpireTime

 。|
    |DBInstanceId|String|是|实例ID。|
    |ConnectionString|String|是|要延期的经典网络连接串，经典网络字符串有两种：当前实例的经典网络字符串，读写分离的经典网络字符串。|
    |ClassicExpiredDays|Integer|是|经典网络字符串保留天数\[1-120\]。|

    **返回参数** 

    |参数|类型|说明|
    |:-|:-|:-|
    |RequestId|String|请求ID。|

    **参考代码**

    ``` {#codeblock_epy_6oa_jil}
    public static void main(String[] args) {
         ModifyDBInstanceNetExpireTimeRequest request = new ModifyDBInstanceNetExpireTimeRequest();
         request.setClassicExpiredDays(3);
         request.setConnectionString("<链接字符串>");
         request.setDBInstanceId("<实例Id>");
         IClientProfile profile
                 = DefaultProfile.getProfile("cn-qingdao", "<你的ak>",
                 "<你的sk>");
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


