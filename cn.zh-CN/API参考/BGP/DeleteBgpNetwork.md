# DeleteBgpNetwork {#doc_api_Vpc_DeleteBgpNetwork .reference}

使用DeleteBgpNetwork删除已宣告的BGP网络。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DeleteBgpNetwork&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteBgpNetwork|要执行的操作。

 取值： **DeleteBgpNetwork**。

 |
|DstCidrBlock|String|是|10.110.192.12/32|需要和IDC互联的VPC或交换机的网段。

 |
|RegionId|String|是|cn-hangzhou|BGP组所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|RouterId|String|是|vrt-bp1lhl0taikrteen80oxx|边界路由器ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过 64 个 ASCII 字符。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|22F4C006-D3BB-4F96-9FF9-4C8335276D70|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DeleteBgpNetwork
&DstCidrBlock=10.110.192.12/32
&RegionId=cn-hangzhou
&RouterId=vrt-bp1lhl0taikrteen80oxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteBgpNetworkResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</DeleteBgpNetworkResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
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

