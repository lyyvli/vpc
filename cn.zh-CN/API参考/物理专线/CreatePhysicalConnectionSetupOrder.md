# CreatePhysicalConnectionSetupOrder {#doc_api_Vpc_CreatePhysicalConnectionSetupOrder .reference}

调用CreatePhysicalConnectionSetupOrder创建初装费订单。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=CreatePhysicalConnectionSetupOrder&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|AccessPointId|String|是|ap-cn-beijing-ft-A|接入点ID。

 |
|Action|String|是|CreatePhysicalConnectionSetupOrder|要执行的操作。

 取值：**CreatePhysicalConnectionSetupOrder**。

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

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|OrderId|String|202844382740728|订单ID。

 |
|PhysicalConnectionId|String|pc-1111111|物理专线ID。

 |
|RequestId|String|F7A6301A-64BA-41EC-8284-8F4838C15D1F|请求ID。

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
<CreatePhysicalConnectionSetupOrderResponse>
      <code>200</code>
	  <data>
		    <orderId>203255400960138</orderId>
	  </data>
	  <httpStatusCode>200</httpStatusCode>
	  <message>successful</message>
	  <requestId>AA874147-4A58-41D4-95E2-F2FFDAF417A6</requestId>
	  <success>true</success>
    </CreatePhysicalConnectionSetupOrderResponse>
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

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

