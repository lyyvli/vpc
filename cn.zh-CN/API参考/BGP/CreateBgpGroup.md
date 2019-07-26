# CreateBgpGroup {#doc_api_Vpc_CreateBgpGroup .reference}

使用CreateBgpGroup为指定的边界路由器（VBR）创建一个BGP组。

您可以通过BGP实现边界路由器与本地IDC的互通。每个BGP组关联一个VBR，您仅需将与VBR通信的BGP邻居添加到对应的BGP组中，然后在VBR中宣告BGP网络即可。

BGP组主要是用于简化BGP配置，可以将需要不断重复的配置合并到一个组中，减少配置复杂度。您需根据AS号码建立一个BGP组。

调用本接口创建BGP组时，请注意：

-   BGP组支持的BGP版本为BGP4。
-   BGP组支持IPv4 BGP，不支持IPv6 BGP。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=CreateBgpGroup&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateBgpGroup|要执行的操作。

 取值： **CreateBgpGroup**。

 |
|PeerAsn|Long|是|1111|侧设备的ASN。

 |
|RegionId|String|是|cn-shanghai|BGP组所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|RouterId|String|是|vrt-bp1lhl0taikrteen80oxx|VBR的ID。

 |
|AuthKey|String|否|!PWZ2wsq|BGP组的认证密钥。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|客户端token，用于保证请求的幂等性。 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|Description|String|否|BGP|BGP组的描述信息。 长度为 2-256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|IsFakeAsn|Boolean|否|true|运行BGP的路由器一般情况下只能属于一个AS，某些情况下，比如AS需要迁移或者和其他AS进行合并，要用新的AS替代原有的AS号码。

 |
|Name|String|否|test|BGP组的名称。 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://`或`https://`开头。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|BgpGroupId|String|bgpg-2zendnzngq9lkjkhvlrsr|新建BGP组的ID。

 |
|RequestId|String|C1221A1F-2ACD-4592-8F27-474E02883159|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateBgpGroup
&PeerAsn=1111
&RegionId=cn-shanghai
&RouterId=vrt-bp1lhl0taikrteen80oxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateBgpGroupResponse>
      <BgpGroupId>bgpg-2zendnzngq9lkjkhvlrsr</BgpGroupId>
      <RequestId>C1221A1F-2ACD-4592-8F27-474E02883159</RequestId>
</CreateBgpGroupResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"BgpGroupId":"bgpg-2zendnzngq9lkjkhvlrsr",
	"RequestId":"C1221A1F-2ACD-4592-8F27-474E02883159"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|QuotaExceeded.Bgp|bgp peer count per vbr quota exceed.|边界路由器的BGP组的数量已达到配额。|
|400|QuotaExceeded.Nqa|nqa count per vbr quota exceed.|NQA数超过VBR配额。|
|400|QuotaExceeded.BgpNetwork|bgp network count per vbr quota exceed.|边界路由器的BGP网络数量已达到配额。|
|400|InvalidPeerIpAddress|multi pconn peer ip can not be null.|多物理专线的IP地址不能为空。|
|400|InvalidVbrNetwork|vbr netowrk not exists|该边界路由器不存在，请您检查输入的边界路由器是否正确。|
|400|InvalidBgpName.Malformed|Specified Bgp Group name is not valid.|该BGP组的名称不合法。|
|400|InvalidBgpDescription.Malformed|Specified Bgp Group description is not valid.|该BGP组的描述不合法。|
|400|InvalidBgpAuthkey.Malformed|Specified Bgp Group authkey is not valid.|该BGP组的验证密钥不合法。|
|404|InvalidRegionId.NotFound|The specified RegionId is not found.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|InvalidIP.Malformed|Ip malformed.|IP格式不合法。|
|400|InvalidPeerAsn.Malformed|invalid peer asn cannot equals aliyun asn:45104|ASN号码不能和阿里云ASN号码一致。|
|400|InvalidParams.NotNull|invalid peer asn cannot equals aliyun asn:45104|ASN号码不能和阿里云ASN号码一致。|
|400|InvalidParams.NotFound|instance not found|实例不存在。|
|400|InvalidParams.NotFound|vpc instance not found|该 VPC 不存在，请您检查输入的 VPC 是否正确。|
|400|InvalidParams.AlreadyExists|bgp network already exists|BGP 网络已经存在。|
|400|InvalidStatus.CannotOperate|invalid status cannot operate|状态不合法，无法执行该操作。|
|400|QuotaExceeded.Bgp|bgp group count per vbr quota exceed.|边界路由器的BGP组的数量已达到配额。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

