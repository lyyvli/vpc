# CreateIPv6Translator {#doc_api_1132486 .reference}

创建IPv6转换服务实例。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CreateIPv6Translator)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateIPv6Translator|要执行的操作。 取值：**CreateIPv6Translator**。

 |
|RegionId|String|是|cm-hangzhou|IPv6转换服务实例的地域。 您可以通过调用**DescribeRegions**接口获取地域ID。

 |
|AutoPay|Boolean|否|false|是否自动只支付预付费账单。取值：**true|false**。

 |
|Bandwidth|Integer|否|10|IPv6转换服务实例的计费带宽（Mbps）。取值：**1-200**。若不设置转换映射条目的带宽，实例中的IPv6转换服务映射条目共享该带宽。

 **说明：** 若不指定带宽，默认为10Mbps。

 |
|ClientToken|String|否|sha111|客户端token用于保证请求的幂等性。要保证Client Token在不同请求间唯一，最大值不超过64个ASCII字符。

 |
|Duration|Integer|否|1|购买时长，取值：

 -   如果计费时长为**Month**，则取值为1-9。
-   如果计费时长为**Year**，则取值为3。

 |
|Name|String|否|ipv6\_1|IPv6转换服务实例的名称，默认为实例ID。 长度为 2-100个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以http:// 或https://开头。

 |
|PayType|String|否|PREPAY|IPv6转换服务服务实例的付费类型。取值：

 -   **PREPAY**：预付费
-   **POSTPAY**：后付费

 |
|PricingCycle|String|否|Month|预付费的计费周期，取值：

 -   **Month**：按月购买（默认值）
-   **Year**：按年购买

 |
|Spec|String|否|small|IPv6转换服务服务实例的规格。取值： **small**。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Ipv6TranslatorId|String|ipv6trans-bp1i8ahxut1xxxx|IPv6转换服务实例ID。

 |
|Name|String|test\_nat64gw|IPv6转换服务实例名称。

 |
|OrderId|Long|202303300940739|创建IPv6转换服务实例的订单ID。

 |
|RequestId|String|1AE05898-06E5-4782-xxxxx|请求ID。

 |
|Spec|String|small|IPv6转换服务实例规格。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateIPv6Translator
&RegionId=cn-hangzhou
&公共请求参数

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateIPv6TranslatorResponse>
  <Ipv6TranslatorId>ipv6trans-bp1i8ahxut1iexxxx</Ipv6TranslatorId>
  <Name>test_nat64gw</Name>
  <OrderId>202303300940739</OrderId>
  <RequestId>1AE05898-06E5-4782-B4D0-xxxxx</RequestId>
  <Spec>small</Spec>
</CreateIPv6TranslatorResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Name":"test_nat64gw",
	"Spec":"small",
	"RequestId":"1AE05898-06E5-4782-xxxxx",
	"OrderId":202303300940739,
	"Ipv6TranslatorId":"ipv6trans-bp1i8ahxut1xxxx"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

