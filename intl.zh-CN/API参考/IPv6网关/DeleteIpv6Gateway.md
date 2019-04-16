# DeleteIpv6Gateway {#doc_api_910116 .reference}

调用DeleteIpv6Gateway接口删除IPv6网关。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Vpc&api=DeleteIpv6Gateway)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteIpv6Gateway|要执行的操作，取值：**DeleteIpv6Gateway**。

 |
|Ipv6GatewayId|String|是|ipv6gw-hp3y0l3ln89j8fv0m5som|要删除的IPv6网关。

 |
|RegionId|String|是|cn-huhehaote|IPv6网关的所属地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|E9A8AABE-A84B-4AF2-A68A-8E2EA190E7AE|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DeleteIpv6Gateway
&RegionId=cn-hangzhou
&CidrBlock=10.10.0.0/24
&公共请求参数

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteIpv6GatewayResponse>
  <RequestId>E9A8AABE-A84B-4AF2-A68A-8E2EA190E7AE</RequestId>
</DeleteIpv6GatewayResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"E9A8AABE-A84B-4AF2-A68A-8E2EA190E7AE"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

