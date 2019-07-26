# ModifyBgpGroupAttribute {#doc_api_Vpc_ModifyBgpGroupAttribute .reference}

调用ModifyBgpGroupAttribute接口修改BGP组的配置。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyBgpGroupAttribute&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyBgpGroupAttribute|要执行的操作，取值： **ModifyBgpGroupAttribute**。

 |
|BgpGroupId|String|是|bgpg-wz9f62v4fbg2gxxxxxxxx|指定BGP组的ID。

 |
|RegionId|String|是|cn-shanghai|BGP组所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|AuthKey|String|否|!PWZ2wsq|BGP组的认证密钥。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-001xxxxxxxx|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。 

 |
|Description|String|否|BGP|BGP组的描述信息。

 长度为2-256个字符，必须以字母或中文开头，但不能以`http://` 或`https://`开头。

 |
|IsFakeAsn|Boolean|否|true|运行BGP的路由器一般情况下只能属于一个AS，某些情况下，比如AS需要迁移或者和其他AS进行合并，要用新的AS替代原有的AS号。

 |
|Name|String|否|test|BGP组的名称。

 长度为2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-），但不能以`http://` 或`https://`开头。

 |
|PeerAsn|Long|否|1111|侧设备的AS号。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|8C3C6D7C-A1CE-4FD8-BC57-DC493A55F76F|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyBgpGroupAttribute
&BgpGroupId=bgpg-wz9f62v4fbg2gxxxxxxxx
&RegionId=cn-shanghai
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyBgpGroupAttributeResponse>
      <RequestId>C1221A1F-2ACD-4592-8F27-474E02883159</RequestId>
</ModifyBgpGroupAttributeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"C1221A1F-2ACD-4592-8F27-474E02883159"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|Specified value of "regionId" is not supported.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|QuotaExceeded.Bgp|bgp peer count per vbr quota exceed.|边界路由器的BGP组的数量已达到配额。|
|400|QuotaExceeded.Nqa|nqa count per vbr quota exceed.|NQA数超过VBR配额。|
|400|QuotaExceeded.BgpNetwork|bgp network count per vbr quota exceed.|边界路由器的BGP网络数量已达到配额。|
|400|InvalidPeerIpAddress|multi pconn peer ip can not be null.|多物理专线的IP地址不能为空。|
|400|InvalidVbrNetwork|vbr netowrk not exists|该边界路由器不存在，请您检查输入的边界路由器是否正确。|
|400|InvalidBgpGroup|bgp group not exists|该BGP组不存在。|
|400|InvalidBgpName.Malformed|Specified Bgp Group name is not valid.|该BGP组的名称不合法。|
|400|InvalidBgpDiscription.Malformed|Specified Bgp Group description is not valid.|该BGP组的描述不合法。|
|400|InvalidBgpAuthkey.Malformed|Specified Bgp Group authkey is not valid.|该BGP组的验证密钥不合法。|
|400|InvalidIP.Malformed|Ip malformed.|IP格式不合法。|
|400|InvalidPeerAsn.Malformed|invalid peer asn cannot equals aliyun asn:45104|ASN号码不能和阿里云ASN号码一致。|
|400|InvalidParams.NotNull|invalid peer asn cannot equals aliyun asn:45104|ASN号码不能和阿里云ASN号码一致。|
|400|InvalidParams.NotFound|instance not found|实例不存在。|
|400|InvalidParams.NotFound|vpc instance not found|该 VPC 不存在，请您检查输入的 VPC 是否正确。|
|400|InvalidParams.AlreadyExists|bgp network already exists|BGP 网络已经存在。|
|400|InvalidStatus.CannotOperate|invalid status cannot operate|状态不合法，无法执行该操作。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

