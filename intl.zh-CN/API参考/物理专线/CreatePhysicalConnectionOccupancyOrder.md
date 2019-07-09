# CreatePhysicalConnectionOccupancyOrder {#doc_api_Vpc_CreatePhysicalConnectionOccupancyOrder .reference}

调用CreatePhysicalConnectionOccupancyOrder创建资源占用费订单。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CreatePhysicalConnectionOccupancyOrder)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreatePhysicalConnectionOccupancyOrder|要执行的操作。

 取值：**CreatePhysicalConnectionOccupancyOrder**。

 |
|PhysicalConnectionId|String|是|pc-bp1hp0wr072f6ambni141|物理专线的实例ID。

 |
|RegionId|String|是|cn-hangzhou|物理专线所在的地域。

 |
|AutoPay|Boolean|否|true|是否自动支付。取值范围：

 -   true（默认）：自动支付。您需要确保账户余额充足，如果账户余额不足会生成异常订单，只能作废订单。
-   false：只生成订单不扣费。

 |
|ClientToken|String|否|CBCE910E-D396-4944-8764-B4047838B2D1|客户端Token鉴权。

 |
|InstanceChargeType|String|否|PostPaid|实例的付费方式。取值范围：

 -   PrePaid：预付费，包年包月。选择该类付费方式时，您必须确认自己的账号支持余额支付/信用支付。
-   PostPaid（默认）：按量付费。

 |
|Period|Integer|否|1|购买时长。

 |
|PricingCycle|String|否|Month|订购的周期单位。

 -   年：Year。
-   月：Month。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CBCE910E-D396-4944-8764-B4047838B2D1|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=CreatePhysicalConnectionOccupancyOrder
&PhysicalConnectionId=pc-bp1hp0wr072f6ambni141
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreatePhysicalConnectionOccupancyOrderResponse>
  <code>200</code>
  <data>
    <orderId>203167309740138</orderId>
  </data>
  <httpStatusCode>200</httpStatusCode>
  <message>successful</message>
  <requestId>CBCE910E-D396-4944-8764-B4047838B2D1</requestId>
  <success>true</success>
</CreatePhysicalConnectionOccupancyOrderResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"message":"successful",
	"httpStatusCode":200,
	"requestId":"CBCE910E-D396-4944-8764-B4047838B2D1",
	"data":{
		"orderId":203167309740138
	},
	"code":"200",
	"success":true
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidPhysicalConnectionId.NotFound|The PhysicalConnectionId provided does not exist in our records.|该物理专线不存在。|
|400|Forbidden.NotAllowedInState|The request does not allow in this state.|该状态无法执行请求。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

