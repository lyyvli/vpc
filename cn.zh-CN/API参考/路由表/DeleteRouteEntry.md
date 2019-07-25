# DeleteRouteEntry {#doc_api_Vpc_DeleteRouteEntry .reference}

调用DeleteRouteEntry接口删除VPC路由器或边界路由器的路由表中的路由条目。

调用本接口删除路由条目时，请注意：

-   只有处于Available状态的路由条目可以被删除。
-   路由表所在的VPC正在进行创建/删除交换机或路由条目时，无法删除路由条目。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DeleteRouteEntry&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteRouteEntry|要执行的操作。

 取值： **DeleteRouteEntry**。

 |
|RegionId|String|是|cn-hangzhou|路由表所属地域的ID。

 |
|DestinationCidrBlock|String|否|0.0.0.0/0|路由条目的目标网段，支持IPv4和IPv6网段。

 |
|NextHopId|String|否|ri-2zeo3xzyf38r4urzd\*\*\*\*|下一跳实例的ID。

 |
|NextHopList.N.NextHopId|String|否|ri-2zeo3xzyf38r43cd\*\*\*\*|下一跳实例的ID。

 |
|NextHopList.N.NextHopType|String|否|RouterInterface|下一跳的类型，取值：

 -   **Instance**：ECS实例（默认值）
-   **HaVip**：高可用虚拟IP
-   **RouterInterface**：路由器接口

 |
|RouteEntryId|String|否|rte-bp1mnnr2al0naomnpvxxx|路由条目ID。

 |
|RouteTableId|String|否|trb-2ze3jgygk9bmsj23s\*\*\*\*|路由条目所在的路由表的ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DeleteRouteEntry
&DestinationCidrBlock=0.0.0.0/0
&RouteTableId=trb-2ze3jgygk9bmsj23s****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteRouteEntryResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</DeleteRouteEntryResponse>
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
|400|MissingParameter|Miss mandatory parameter.|缺少必要参数,请您检查必填参数是否都已填后再进行操作。|
|400|IncorrcetRouteEntryStatus|Some route entry status blocked this operation.|无法执行该操作，因为有些路由条目的状态是pending或modifying。|
|400|InvalidCidrBlock.Malformed|Specified CIDR block is not valid.|该 CIDR 格式不正确。|
|404|InvalidRouteTableId.NotFound|Specified route table does not exist.|该路由表不存在。|
|400|OperationDenied|Specified operation is denied as route entry type is system.|无法执行该操作，因为路由条目是系统路由。|
|400|InvalidRouteEntry.NotFound|Route entry not exists.|该路由条目不存在，请您检查路由条目是否正确。|
|400|InvalidVRouter.NotFound|vRouter not exists.|路由器不存在，请您检查输入的路由器是否正确。|
|400|IncorrectRouteEntryStatus|Some route entry status blocked this operation.|无法执行该操作，当前路由表中有路由条目的状态为pending或modifying。|
|400|IncorrectRouteEntryStatus|VBR has NotStable route entry.|无法执行该操作，边界路由表中有路由条目的状态为pending或modifying。|
|404|InvalidVpcId.NotFound|Specified value of VpcId is not found in our record.|该 VPC 不存在，请您检查输入的 VPC 是否正确。|
|400|IncorrectRouteEntryStatus|Specified routeEntry status error.|无法执行该操作，当前路由表中有路由条目的状态为pending或modifying。|
|400|Forbbiden|Specified RouteEntry cannot allowed delete by openApi.|不允许使用API删除该路由条目。|
|400|InvalidNextHop|Specified nexthop and nexthop list cannot both null.|下一跳和下一跳列表不能同时为空。|
|400|InvalidRouteEntry|Specified routeEntry not exist.|该路由条目不存在。|
|400|IncorrectVpcStatus|Current VPC status does not support this operation.|当前 VPC 的状态无法支持这个操作。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

