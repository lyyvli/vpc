# DeactiveFlowLog {#doc_api_Vpc_DeactiveFlowLog .reference}

调用DeactiveFlowLog接口停止流日志，停止后不再捕获指定资源的流量。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DeactiveFlowLog&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeactiveFlowLog|要执行的操作，取值：**DeactiveFlowLog**。

 |
|FlowLogId|String|是|fl-m5evbtbptxxxxxxxxxxxx|流日志ID。

 |
|RegionId|String|是|cn-qingdao|流日志的所属地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|F7DDDC17-FA06-4AC2-8F35-59D2470FCFC1|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DeactiveFlowLog
&RegionId=cn-qingdao
&FlowLogId=fl-m5evbtbptxxxxxxxxxxxx
&公共请求参数

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeactiveFlowLog>
       <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
</DeactiveFlowLog>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FExxxxx"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

