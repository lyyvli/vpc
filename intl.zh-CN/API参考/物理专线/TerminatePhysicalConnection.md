# TerminatePhysicalConnection {#doc_api_Vpc_TerminatePhysicalConnection .reference}

在物理专线开通后调用TerminatePhysicalConnection接口终止物理专线接入。

调用TerminatePhysicalConnection接口后，物理专线进入Terminating状态，处理完成后进入Terminated状态。

调用本接口终止物理专线时，请注意：

-   只能终止处于**Enabled**状态的物理专线。
-   终止物理专线之前，必须删除与其关联的VBR。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=TerminatePhysicalConnection)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|TerminatePhysicalConnection|要执行的操作。

 取值： **TerminatePhysicalConnection**。

 |
|PhysicalConnectionId|String|是|pc-119mfjzm7|物理专线的ID。

 |
|RegionId|String|是|cn-hangzhou|物理专线所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个ASCII字符。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=TerminatePhysicalConnection
&PhysicalConnectionId=pc-119mfjzm7
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<TerminatePhysicalConnectionResponse>
  <RequestId>513E0A50-4F2D-4CBE-BF35-40559DF65D79"
</RequestId>
</TerminatePhysicalConnectionResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"513E0A50-4F2D-4CBE-BF35-40559DF65D79"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidPhysicalConnectionId.NotFound|The PhysicalConnectionId provided does not exist in our records.|该物理专线不存在。|
|400|Forbidden.NotAllowedInState|The request does not allow in this state.|该状态无法执行请求。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

