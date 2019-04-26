# AccosicateNetworkAcl {#doc_api_Vpc_AssociateNetworkAcl .reference}

调用AccosicateNetworkAcl接口，绑定网络ACL到交换机。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=AssociateNetworkAcl)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AssociateNetworkAcl|要执行的操作，取值： **AccosicateNetworkAcl**。

 |
|NetworkAclId|String|是|nacl-a2do9e413e0spxxxxxxxx|网络ACL的ID。

 |
|RegionId|String|是|cn-hangzhou|网络ACL所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|Resource.N.ResourceId|String|否|vsw-bp1de348lntdwxxxxxxxx|关联资源的ID。

 |
|Resource.N.ResourceType|String|否|VSwitch|关联资源的类型。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|4CF20CC7-D1FC-425B-A15B-DF7C8E2131A7|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=AssociateNetworkAcl
&NetworkAclId=nacl-a2do9e413e0spxxxxxxxx
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AssociateNetworkAclResponse>
  <RequestId>4CF20CC7-D1FC-425B-A15B-DF7C8E2131A7</RequestId>
</AssociateNetworkAclResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"4CF20CC7-D1FC-425B-A15B-DF7C8E2131A7"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|500|InternalError|The request processing has failed due to some unknown error.|请求处理由于某些未知错误失败。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

