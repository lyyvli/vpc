# AllocateIpv6InternetBandwidth {#doc_api_909769 .reference}

调用AllocateIpv6InternetBandwidth接口为IPv6地址购买公网带宽。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Vpc&api=AllocateIpv6InternetBandwidth)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AllocateIpv6InternetBandwidth|要执行的操作，取值：**AllocateIpv6InternetBandwidth**。

 |
|Bandwidth|Integer|是|2|IPv6地址的公网带宽，单位：Mbps，取值范围：**1-5000**。

 -   当**InternetChargeType**为**PayByBandwidth**，IPv6地址的公网带宽为1-5000
-   当**InternetChargeType**为**PayByTraffic**，IPv6地址的公网带宽范围同时受到IPv6网关规格的制约：
-   Small（默认免费版），公网带宽范围为1-500
-   Middle（企业版），公网带宽范围为1-1000
-   Large（企业增强版），公网带宽范围为1-2000

 |
|Ipv6AddressId|String|是|ipv6-123456|IPv6地址的实例ID。

 |
|Ipv6GatewayId|String|是|ipv5gw-123456|IPv6网关的ID。

 |
|RegionId|String|是|cn-huhehaote|IPv6网关的地域ID。

 |
|ClientToken|String|否|123456|请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|InternetChargeType|String|否|PayByTraffic|IPv6公网带宽的计费方式。取值：

 -   **PayByTraffic**：按使用流量计费
-   **PayByBandwidth**（默认值）：按带宽计费

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|InternetBandwidthId|String|2|购买的公网带宽。

 |
|Ipv6AddressId|String|2408:4004:c0:200:35b:cd32:c460:6aa4|IPv6的地址。

 |
|RequestId|String|6972A26E-99B1-4367-9890-FBDEBB0F5E7D|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.cn-huhehaote.aliyuncs.com?Action=AllocateIpv6InternetBandwidth
&Bandwidth=2
&Ipv6AddressId=ipv6-hp351bytt9inrfp6tgubd
&Ipv6GatewayId=ipv6gw-hp38x2x0fz785tlc65pfv
&RegionId=cn-huhehaote
&公共请求参数

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AllocateIpv6InternetBandwidthResponse>
  <RequestId>6972A26E-99B1-4367-9890-FBDEBB0F5E7D</RequestId>
  <InternetBandwidthId>2</InternetBandwidthId>
  <Ipv6AddressId>ipv6-hp352ungkzcknmeicfvss</Ipv6AddressId>
</AllocateIpv6InternetBandwidthResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Ipv6AddressId":"ipv6-hp352ungkzcknmeicfvss",
	"RequestId":"6972A26E-99B1-4367-9890-FBDEBB0F5E7D",
	"InternetBandwidthId":2
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

