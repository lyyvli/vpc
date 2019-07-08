# ModifyIpv6GatewaySpec {#doc_api_Vpc_ModifyIpv6GatewaySpec .reference}

调用ModifyIpv6GatewaySpec接口修改IPv6网关的规格。

不同的规格的转发能力和带宽都不同，详情参见[IPv6网关规格](~~98926~~)。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=ModifyIpv6GatewaySpec)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyIpv6GatewaySpec|要执行的操作，取值：**ModifyIpv6GatewaySpec**。

 |
|Ipv6GatewayId|String|是|ipv6gw-123456xxxxxxxx|IPv6网关的ID。

 |
|RegionId|String|是|cn-huhehaote|IPv6网关的地域ID。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|Spec|String|是|Middle|IPv6网关的规格，取值：

 -   **Small**（默认值）：免费版。
-   **Middle**：企业版。
-   **Large**：企业增强版。

 |
|ClientToken|String|否|123456|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|9DFEDBEE-E5AB-49E8-A2DC-CC114C67AF75|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyIpv6GatewaySpec
&RegionId=cn-huhehaote
&Ipv6GatewayId=ipv6gw-123456xxxxxxxx
&Spec=Middle
&公共请求参数

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyIpv6GatewaySpecResponse>
  <RequestId>9DFEDBEE-E5AB-49E8-A2DC-CC114C67AF75</RequestId>
</ModifyIpv6GatewaySpecResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"9DFEDBEE-E5AB-49E8-A2DC-CC114C67AF75"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

