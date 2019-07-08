# RecoverVirtualBorderRouter {#doc_api_Vpc_RecoverVirtualBorderRouter .reference}

调用RecoverVirtualBorderRouter恢复被终止的边界路由器（VBR）。

调用该接口后VBR从**Terminated**状态变为**Recovering**状态，恢复成功后进入**Enabled**状态。

在调用本接口恢复VBR之前，请注意：

-   只有物理专线的所有者可以调用该接口。
-   VBR所属的物理专线必须处于**Enabled**状态。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=RecoverVirtualBorderRouter)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RecoverVirtualBorderRouter|要执行的操作。

 取值： **RecoverVirtualBorderRouter**。

 |
|RegionId|String|是|cn-shanghai|VBR所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VbrId|String|是|vbr-bp1lhl0taikrteen80|VBR的ID。

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

http(s)://[Endpoint]/?Action=RecoverVirtualBorderRouter
&RegionId=cn-shanghai
&VbrId=vbr-bp1lhl0taikrteen80
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<RecoverVirtualBorderRouterResponse>
  <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</RecoverVirtualBorderRouterResponse>

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
|400|InvalidOperation.OperationNotAllowedInState|The specified VirutalBorderRouter is in invalid state|该边界路由器接口状态不支持该操作。|
|400|OperationFailed.VlanIdAlreadyInUse|The specifed vlanId has been used.|该VLAN已经被占用。|
|403|Forbidden.OperationNotAllowedByUser|The caller is not allowed to recover the specified VirtualBorderRouter.|不允许恢复边界路由器。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

