# CreateBgpPeer {#doc_api_Vpc_CreateBgpPeer .reference}

调用CreateBgpPeer接口向指定的BGP组中添加BGP邻居。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=CreateBgpPeer&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateBgpPeer|要执行的操作，取值： **CreateBgpPeer**。

 |
|BgpGroupId|String|是|bgpg-wz9f62v4fbgxxxxxxxx|BGP组的ID。

 |
|RegionId|String|是|cn-shanghai|BGP组所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-001xxxxxxxx|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。 

 |
|EnableBfd|Boolean|否|true|是否开启BFD功能，取值：

 -   **true**：开启BFD功能。
-   **false**：不开启BFD功能。

 |
|PeerIpAddress|String|否|116.62.xx.xx|BGP邻居的IP地址。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|BgpPeerId|String|Bgp-awjhxxxxxxxx|BGP邻居的ID。

 |
|RequestId|String|D4B7649A-61BB-4C64-A586-1DFF1EDA6A42|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateBgpPeer
&BgpGroupId=bgpg-wz9f62v4fbgxxxxxxxx
&RegionId=cn-shanghai
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateBgpPeerResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</CreateBgpPeerResponse>
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
|400|QuotaExceeded.Bgp|bgp group count per vbr quota exceed.|边界路由器的BGP组的数量已达到配额。|
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

