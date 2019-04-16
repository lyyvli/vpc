# DeleteIpv6InternetBandwidth {#doc_api_909615 .reference}

调用DeleteIpv6InternetBandwidth接口删除公网带宽。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Vpc&api=DeleteIpv6InternetBandwidth)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteIpv6InternetBandwidth|要执行的操作，取值：**DeleteIpv6InternetBandwidth**。

 |
|RegionId|String|是|cn-huhehaote|IPv6网关的地域ID。

 |
|Ipv6AddressId|String|否|ipv6-123456|IPv6地址的实例ID。

 |
|Ipv6InternetBandwidthId|String|否|2|IPv6地址的公网带宽。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|E07E0FE6-5C21-405F-AF82-7613AA81EF92|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.cn-huhehaote.aliyuncs.com?Action=DeleteIpv6InternetBandwidth
&Ipv6AddressId=ipv6-hp351bytt9inrfp6tgubd
&RegionId=cn-huhehaote
&公共参数

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteIpv6InternetBandwidthResponse>
  <RequestId>6972A26E-99B1-4367-9890-FBDEBB0F5E7D</RequestId>
</DeleteIpv6InternetBandwidthResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"E07E0FE6-5C21-405F-AF82-7613AA81EF92"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

