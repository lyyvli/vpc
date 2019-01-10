# ModifyIpv6InternetBandwidth {#doc_api_910127 .reference}

调用ModifyIpv6InternetBandwidth接口修改IPv6地址的公网带宽。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Vpc&api=ModifyIpv6InternetBandwidth)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyIpv6InternetBandwidth|要执行的操作，取值：**ModifyIpv6InternetBandwidth**。

 |
|Bandwidth|Long|是|4|IPv6地址的公网带宽，单位：Mbps，取值范围：**1-5000**。

 -   当**InternetChargeType**为**PayByBandwidth**，IPv6地址的公网带宽为1-5000
-   当**InternetChargeType**为**PayByTraffic**，IPv6地址的公网带宽范围同时受到IPv6网关规格的制约：
-   Small（默认免费版），公网带宽范围为1-500
-   Middle（企业版），公网带宽范围为1-1000
-   Large（企业增强版），公网带宽范围为1-2000

 |
|RegionId|String|是|cn-huhehaote|IPv6网关的地域ID。

 |
|ClientToken|String|否|123456|请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|Ipv6AddressId|String|否|ipv5-1233456|IPv6地址的实例ID。

 |
|Ipv6InternetBandwidthId|String|否|123456|公网带宽ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|D560AF68-4CE8-4A5C-B3FE-469F558094D0|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.cn-huhehaote.aliyuncs.com/?Action=ModifyIpv6InternetBandwidth
&Bandwidth=3
&Ipv6AddressId=ipv6-hp351bytt9inrfp6tgubd
&RegionId=cn-huhehaote
&公共参数

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyIpv6InternetBandwidthResponse>
  <RequestId>D560AF68-4CE8-4A5C-B3FE-469F558094D0</RequestId>
</ModifyIpv6InternetBandwidthResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"D560AF68-4CE8-4A5C-B3FE-469F558094D0"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

