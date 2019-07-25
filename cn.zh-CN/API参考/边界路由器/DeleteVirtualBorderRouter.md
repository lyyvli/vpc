# DeleteVirtualBorderRouter {#doc_api_Vpc_DeleteVirtualBorderRouter .reference}

调用DeleteVirtualBorderRouter接口删除边界路由器（VBR）。

在调用本接口删除VBR之前，请注意：

-   删除VBR之前，必须删除VBR上所有的路由器接口。
-   只能删除Unconfirmed，Enabled或Terminated状态的VBR。
-   其他用户的VBR只有处于Unconfirmed状态时，才可以被物理专线的所有者删除。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DeleteVirtualBorderRouter&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteVirtualBorderRouter|要执行的操作。

 取值： **DeleteVirtualBorderRouter**。

 |
|RegionId|String|是|cn-shanghai|VBR所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VbrId|String|是|vbr-bp12mw1f8k3jgygk9\*\*\*\*|VBR的ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过 64 个 ASCII 字符。 

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|F8BF7D24-F3EB-4E23-9208-B77C6EB78E75|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DeleteVirtualBorderRouter
&RegionId=cn-shanghai
&VbrId=vbr-bp12mw1f8k3jgygk9****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteVirtualBorderRouterResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</DeleteVirtualBorderRouterResponse>
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
|404|InvalidVbrId.NotFound|The specified VirutalBorderRouter does not exist in our records.|该边界路由器不存在，请您检查输入的边界路由器是否正确。|
|400|InvalidOperation.RouterInterfaceNotDeleted|The specified VirutalBorderRouter still has routerInterface.|该边界路由器还有关联的路由器接口。|
|400|InvalidOperation.OperationNotAllowedInState|The specified VirutalBorderRouter is in invalid state.|该VirutalBorderRouter状态不合法，请检查VirutalBorderRouter状态。|
|403|Forbidden.OperationNotAllowedByUser|The caller is not allowed to delete the specified VirtualBorderRouter.|不允许删除边界路由器。|
|403|Forbidden.MultiVlanRi|Multiple vlan router interfaces are found.|存在多个VLAN路由器接口。|
|403|Forbidden.NoRiFound|No vlan router interfaces are found.|没有可用的VLAN路由器接口。|
|400|InvalidStatus.NotAllowed|The virtual border has been associated by physicalConnection.|边界路由器已经关联了物理专线。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

