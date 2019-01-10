# CreateIpv6Gateway {#doc_api_910115 .reference}

调用CreateIpv6Gateway接口创建IPv6网关。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Vpc&api=CreateIpv6Gateway)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateIpv6Gateway|要执行的操作，取值：**CreateIpv6Gateway**。

 |
|RegionId|String|是|cn-huhehaote|IPv6网关的地域。

 |
|VpcId|String|是|vpc-123456|要开通IPv6网关的VPC ID。

 |
|ClientToken|String|否|123456|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|Description|String|否|ipv6gatewayforVPC1|IPv6网关的描述信息。

 长度为2-256个字符，必须以字母或中文开头，可包含数字、点号\(.\)、下划线\(\_\)和短橫线\(-\)。但不能以 http:// 或 https:// 开头。

 |
|Name|String|否|ipv6GW|IPv6网关的名称。

 长度为2-128个字符，必须以字母或中文开头，可包含数字、点号\(.\)、下划线\(\_\)和短橫线\(-\)。但不能以 http:// 或 https:// 开头。

 |
|Spec|String|否|Small|IPv6网关的规格。取值：

 -   Small（默认值）：免费版
-   Middle：企业版
-   Large：企业增强版

不同规格的IPv6网关的转发能力都不同，详情参见[IPv6网关规格](~~98926~~)。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Ipv6GatewayId|String|ipv6gw-hp3y0l3ln89j8fv0m5som|IPv6网关的ID。

 |
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateIpv6Gateway
&RegionId=cn-huhehaote
&VpcId=vpc-hp3x04of74a63w0sy3exy
&公共请求参数

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateIpv6GatewayResponse>
  <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
  <Ipv6GatewayId>vipv6gw-hp3y0l3ln89j8fv0m5som</Ipv6GatewayId>
</CreateIpv6GatewayResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0",
	"Ipv6GatewayId":"ipv6gw-hp3y0l3ln89j8fv0m5som"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

