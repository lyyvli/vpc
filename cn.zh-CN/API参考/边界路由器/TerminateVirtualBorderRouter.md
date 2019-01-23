# TerminateVirtualBorderRouter {#doc_api_951284 .reference}

使用TerminateVirtualBorderRouter终止边界路由器（VBR）。

调用该接口后VBR从**Enabled**状态进入**Terminated**状态，终止成功后进入**Terminated**状态。

**说明：** 只有物理专线的所有者可以调用该接口。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=TerminateVirtualBorderRouter)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|TerminateVirtualBorderRouter|要执行的操作。

 取值： **TerminateVirtualBorderRouter**。

 |
|RegionId|String|是|cn-shanghai|VBR所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VbrId|String|是|vbr-bp15zckdt37pq72zvw3|VBR的ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|客户端token，用于保证请求的幂等性。 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://vpc.aliyuncs.com/?Action=TerminateVirtualBorderRouter
&RegionId=cn-shanghai
&VbrId=vbr-bp15zckdt37pq72zvw3
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<TerminateVirtualBorderRouterResponse>
  <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</TerminateVirtualBorderRouterResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidVbrId.NotFound|The specified VirutalBorderRouter is not found.|该边界路由器不存在，请您检查输入的边界路由器是否正确。|
|400|InvalidOperation.OperationNotAllowedInState|The specified VirutalBorderRouter is in invalid state.|该VirutalBorderRouter状态不合法，请检查VirutalBorderRouter状态。|
|403|Forbidden.OperationNotAllowedByUser|The caller is not allowed to terminate the specified VirtualBorderRouter.|不允许终止边界路由器。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

