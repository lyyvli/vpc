# DescribeFlowLogs {#doc_api_Vpc_DescribeFlowLogs .reference}

调用DescribeFlowLogs接口查询流日志。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeFlowLogs&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeFlowLogs|要执行的操作，取值：**DescribeFlowLogs**。

 |
|RegionId|String|是|cn-qingdao|流日志的所属地域ID。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|FlowLogId|String|否|flowlog-m5evbtbptxxxxxxxxxxxx|流日志ID。

 |
|FlowLogName|String|否|myFlowlog|流日志名称。长度为2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://`或`https://`开头。

 |
|LogStoreName|String|否|FlowLogStore|存储捕获到的流量的LogStore。

 |
|ProjectName|String|否|FlowLogProject|存储捕获到的流量的Project。

 |
|ResourceId|String|否|eni-askldfasxxxxxxxx|要捕获的流量的资源ID。

 |
|ResourceType|String|否|NetworkInterface|要捕获的流量的资源类型：

 -   NetworkInterface：弹性网卡
-   VSwitch：交换机内的所有弹性网卡
-   VPC：专有网络内的所有弹性网卡

 |
|TrafficType|String|否|All|采集的流量类型：

 -   All：全部流量
-   Allow：访问控制允许的流量
-   Drop：访问控制拒绝的流量

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|FlowLogs| | |流日志。

 |
|CreationTime|String|2018-07-24T13:00:52Z|创建时间。

 |
|Description|String|abc|描述信息。

 |
|FlowLogId|String|flowlog-m5evbtbptxxxxxxxxxxxx|流日志ID。

 |
|FlowLogName|String|myFlowlog|流日志名称。

 |
|LogStoreName|String|FlowLogStore|存储捕获到的流量的LogStore。

 |
|ProjectName|String|FlowLogProject|存储捕获到的流量的Project。

 |
|RegionId|String|cn-qingdao|流日志所属地域。

 |
|RequestId|String|F7DDDC17-FA06-4AC2-8F35-59D2470FCFC1|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeFlowLogs
&RegionId=cn-qingdao
&FlowLogId=fl-m5evbtbptxxxxxxxxxxxx
&公共请求参数

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeFlowLogsResponse>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
</DescribeFlowLogsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FExxxxx"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

