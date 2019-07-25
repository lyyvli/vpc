# CreateFlowLog {#doc_api_Vpc_CreateFlowLog .reference}

 调用CreateFlowLog接口创建流日志。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=CreateFlowLog&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateFlowLog|要执行的操作，取值： **CreateFlowLog**。

 |
|LogStoreName|String|是|FlowLogStore|存储捕获到的流量的LogStore。

 |
|ProjectName|String|是|FlowLogProject|存储捕获到的流量的Project。

 |
|RegionId|String|是|cn-qingdao|流日志的所属地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|ResourceId|String|是|eni-askldfasxxxxxxxx|要捕获流量的资源ID。

 |
|ResourceType|String|是|NetworkInterface|要捕获流量的资源类型：

 -   NetworkInterface：弹性网卡
-   VSwitch：交换机内的所有弹性网卡
-   VPC：专有网络内的所有弹性网卡

 |
|TrafficType|String|是|all|采集的流量类型：

 -   All：全部流量
-   Allow：访问控制允许的流量
-   Drop：访问控制拒绝的流量

 |
|Description|String|否|This is my Flowlog.|流日志描述。 长度为 2-256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|FlowLogName|String|否|myFlowlog|流日志名称。 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://`或`https://`开头。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|FlowLogId|String|flowlog-m5evbtbptxxxxxxxxxxxx|流日志ID。

 |
|RequestId|String|54B48E3D-DF70-471B-AA93-08E683A1B457|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateFlowLog
&LogStoreName=FlowLogStore
&ProjectName=FlowLogProject
&RegionId=cn-qingdao
&ResourceId=eni-askldfasxxxxxxxx
&ResourceType=NetworkInterface
&TrafficType=all
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateFlowLogResponse>
      <RequestId>62172DD5-6BAC-45DF-8D44-xxxxxxxx</RequestId>
      <FlowLogId>flowlog-m5evbtbptxxxxxxxxxxxx</FlowLogId>
</CreateFlowLogResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"62172DD5-6BAC-45DF-8D44-xxxxxxxx",
	"FlowLogId":"flowlog-m5evbtbptxxxxxxxxxxxx"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|INVALID\_PARAMETER|The parameter invalid.|参数不合法。|
|400|MissingParameter|Missing mandatory parameter|缺少必要参数,请您检查必填参数是否都已填后再进行操作。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

