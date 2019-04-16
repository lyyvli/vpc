# CreatePhysicalConnectionSetupOrder {#doc_api_1032091 .reference}

调用CreatePhysicalConnectionSetupOrder创建资源占用费订单。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CreatePhysicalConnectionSetupOrder)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|AccessPointId|String|是|ap-cn-beijing-ft-A|接入点ID。

 |
|Action|String|是|CreatePhysicalConnectionSetupOrder|要执行的操作。

 取值：**CreatePhysicalConnectionSetupOrder**

 |
|LineOperator|String|是|CT|提供接入物理线路的运营商，取值：

 -   CT：中国电信
-   CU：中国联通
-   CM：中国移动
-   CO：中国其他
-   Equinix：Equinix
-   Other：境外其他

 |
|RegionId|String|是|cn-shanghai|物理专线所在的地域。 您可以通过调用DescribeRegions接口获取地域ID。

 |
|AutoPay|Boolean|否|true|是否自动支付。

 取值：**true|false**

 |
|ClientToken|String|否|318BB676-0A2B-43A0-9AD8-F1D34E93750F|客户端Token鉴权。

 |
|PortType|String|否|100Base-T|物理专线接入端口类型：

 -   **100Base-T**：百兆电口
-   **1000Base-T**（默认值）：千兆电口
-   **1000Base-LX**：千兆单模光口（10千米）
-   **10GBase-T**：万兆电口
-   **10GBase-LR**：万兆单模光口（10千米）

 |
|RedundantPhysicalConnectionId|String|否|pc-bp10zsv5ntpxxxxxxxxxx|冗余物理专线的ID，该专线的状态必须为**Allocated**、**Confirmed**或**Enabled**。

 |
|Type|String|否|VPC|物理专线类型。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|OrderId|String|202844382740728|订单ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?AccessPointId=ap-cn-beijing-ft-A
&LineOperator=CT
&RegionId=cn-shanghai
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreatePhysicalConnectionSetupOrder>
  <code>200</code>
  <data>
    <orderId>203255400960138</orderId>
  </data>
  <httpStatusCode>200</httpStatusCode>
  <message>successful</message>
  <requestId>AA874147-4A58-41D4-95E2-F2FFDAF417A6</requestId>
  <success>true</success>
</CreatePhysicalConnectionSetupOrder>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"message":"successful",
	"httpStatusCode":200,
	"requestId":"AA874147-4A58-41D4-95E2-F2FFDAF417A6",
	"data":{
		"orderId":203255400960138
	},
	"code":"200",
	"success":true
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

