# ModifyFlowLogAttribute {#doc_api_Vpc_ModifyFlowLogAttribute .reference}

 调用ModifyFlowLogAttribute接口编辑流日志的名称和描述。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyFlowLogAttribute&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyFlowLogAttribute|要执行的操作，取值：**ModifyFlowLogAttribute**。

 |
|FlowLogId|String|是|flowlog-m5evbtbptxxxxxxxxxxxx|流日志ID。

 |
|RegionId|String|是|cn-qingdao|流日志的所属地域ID。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|Description|String|否|This is my Flowlog.|流日志描述。长度为2-256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|FlowLogName|String|否|myFlowlog|流日志名称。长度为2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://`或`https://`开头。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|F7DDDC17-FA06-4AC2-8F35-59D2470FCFC1|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyFlowLogAttribute
&RegionId=cn-qingdao
&FlowLogId=flowlog-m5evbtbptxxxxxxxxxxxx
&FlowLogName=myFlowlog
&公共请求参数

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyFlowLogAttributeResponse>
	  <RequestId>62172DD5-6BAC-45DF-8D44-xxxxxxxx</RequestId>
	  <FlowLogId>flowlog-m5evbtbptxxxxxxxxxxxx</FlowLogId>
</ModifyFlowLogAttributeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"62172DD5-6BAC-45DF-8D44-xxxxxxxx",
	"FlowLogId":"flowlog-m5evbtbptxxxxxxxxxxxx"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

