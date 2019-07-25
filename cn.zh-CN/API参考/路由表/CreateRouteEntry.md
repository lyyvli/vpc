# CreateRouteEntry {#doc_api_Vpc_CreateRouteEntry .reference}

调用CreateRouteEntry接口在VPC路由器或边界路由器（VBR）上创建自定义路由条目。

使用该接口为专有网络的路由器的路由表添加自定义路由条目时，请注意：

-   同一个路由表中自定义路由条目不能超过48条。
-   自定义路由条目的目标网段（DestinationCidrBlock）不能和VPC内的交换机的网段相同，也不能包含交换机的网段或者被交换机的网段包含。
-   自定义路由条目的目标网段（DestinationCidrBlock）不能指向100.64.0.0/10，也不能被100.64.0.0/10包含。
-   同一路由表下的路由条目的目标网段（DestinationCidrBlock）不允许相同。
-   如果指定的目标网段（DestinationCidrBlock）是一个IP地址，会按照32位掩码来处理。
-   多条自定义路由条目可以指向同一个下一跳（NextHopId）。
-   自定义路由条目的下一跳（NextHopId）必须和路由表在同一个VPC。
-   支持通过NextHopList参数配置ECMP路由：
    -   添加普通（非 ECMP ）自定义路由时，需指定DestinationCidrBlock、NextHopType和NextHopId参数，且不能指定 NextHopList参数。
    -   添加ECMP路由时，需指定DestinationCidrBlock和NextHopList参数，且不能指定NextHopType 和 NextHopId参数。

使用该接口为VBR的路由表添加自定义路由条目时，请注意：

-   同一个路由表中自定义路由条目不能超过48条。
-   不支持NextHopList参数。
-   自定义路由条目的目标网段（DestinationCidrBlock）不能指向100.64.0.0/10，也不能被100.64.0.0/10包含。
-   同一路由表下的路由条目的目标网段（DestinationCidrBlock）不允许相同。
-   如果指定的目标网段（DestinationCidrBlock）是一个IP地址，会按照32位掩码来处理。
-   多条自定义路由条目可以指向同一个下一跳（NextHopId）。
-   自定义路由条目的下一跳（NextHopId）必须是该VBR关联的路由器接口。
-   只允许在VBR状态是Active，而且对应的物理专线状态是Enabled且没有被欠费锁定的情况下在VBR上新建路由条目。
-   仅支持添加普通路由（非ECMP），需指定DestinationCidrBlock、NextHopType和NextHopId参数，且不能指定 NextHopList参数。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=CreateRouteEntry&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateRouteEntry|要执行的操作。

 取值： **CreateRouteEntry**。

 |
|DestinationCidrBlock|String|是|192.168.0.1/24|自定义路由条目的目标网段，支持IPv4和IPv6的目标网段。需满足以下要求：

 -   目标网段不能指向100.64.0.0/10或被100.64.0.0/10包含。
-   同一张路由表内的不同路由条目的目标网段不能相同。
-   如果提供的目标网段是一个IP地址，掩码将按照32位处理。
-   如果提供的目标网段是一个IPv6地址，掩码将按照128位处理。

 |
|RegionId|String|是|cn-hangzhou|路由表所属地域的ID。

 |
|RouteTableId|String|是|vtb-bp145q7glnuzd\*\*\*\*|路由表ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-001\*\*\*\*|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|NextHopId|String|否|ri-2zeo3xzyf38r4\*\*\*\*|下一跳实例的ID。

 |
|NextHopList.N.NextHopId|String|否|ri-2zeo3xzyf38r4\*\*\*\*|下一跳实例的ID。

 |
|NextHopList.N.NextHopType|String|否|RouterInterface|下一跳的类型，取值：

 **RouterInterface：路由器接口**。

 |
|NextHopList.N.Weight|Integer|否|10|下一跳的路由权重。

 |
|NextHopType|String|否|RouterInterface|下一跳的类型，取值：

 -   **Instance**：ECS实例（默认值）
-   **HaVip**：高可用虚拟IP
-   **RouterInterface**：路由器接口
-   **NetworkInterface**：弹性网卡
-   **VpnGateway**：VPN网关
-   **IPv6Gateway**：IPv6网关

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateRouteEntry
&DestinationCidrBlock=192.168.0.1/24
&RouteTableId=vtb-bp145q7glnuzd****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateRouteEntryResponse>
      <RequestId>12D086F6-8F31-4658-84C1-006DED011A85</RequestId>
</CreateRouteEntryResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"12D086F6-8F31-4658-84C1-006DED011A85"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidInstanId.NotFound|Specified instance does not exist.|指定的实例不存在，请您检查该实例是否正确。|
|400|MissingParameter|Miss mandatory parameter.|缺少必要参数,请您检查必填参数是否都已填后再进行操作。|
|400|InvalidCidrBlock.Malformed|Specified CIDR block is not valid.|该 CIDR 格式不正确。|
|404|InvalidNextHopId.NotFound|Specified next hop does not exist.|该下一跳不存在。|
|404|InvalidRouteTableId.NotFound|Specified route table does not exist.|该路由表不存在。|
|400|InvalidCIDRBlock.Duplicate|Specified CIDR block is already exists.|该网段已经在该路由表中存在。|
|400|IncorrectVpcStatus|Current VPC status does not support this operation.|当前 VPC 的状态无法支持这个操作。|
|400|IncorrectInstanceStatus|Current instance status does not support this operation.|当前实例的状态不支持该操作。|
|400|QuotaExceeded|Route entry quota exceeded in this route table.|超过路由条目配额。|
|400|IncorrectRouteEntryStatus|Some route entry status blocked this operation.|无法执行该操作，当前路由表中有路由条目的状态为pending或modifying。|
|400|InvalidCidrBlock|Specified CIDR block is not valid.|可能的报错原因：1.您不在10.0.0.0/8的路由网段的白名单中，不能使用该网段。2.添加的自定义路由目标网段不能从属于同一个VPC下面所有交换机的网段。3.网段不能是100.64.0.0/10。|
|400|InvalidNextHopType|Specified parameter "NextHopType" is not valid|该下一跳类型不合法。|
|400|InvalidNextHop.NotFound|Specified next hop does not exist.|该下一跳地址不存在。|
|400|InvalidVRouter.NotFound|vRouter not exists.|路由器不存在，请您检查输入的路由器是否正确。|
|400|InvalidVPC.NotFound|vpc not exists.|专有网络不存在，请您检查输入的专有网络是否正确。|
|400|InvalidNexthopTypeAndList.BothNull|both nexthopType and nextHopList are null.|下一跳类型和下一跳列表都为空。|
|400|InvalidNexthopTypeAndList.BothNotNull|both nexthopType and nextHopList are not null.|下一跳类型和下一跳列表不能同时为空。|
|400|InvalidRouterInterface|invalid router interface.|该路由器接口不存在。|
|400|InvalidOppositeRouterType|nexthop list cannot only contain router interface whose opposite router interface is on vbr.|下一跳的路由器接口的对端路由器类型必须为边界路由器。|
|400|InvalidNexthopListSize|nexthop size is illegal. Must be between 2 and 4.|必须指定2-4个路由器接口作为下一跳。|
|400|InvalidEntryRuleQuota.NotFound|Route entry quota rule not exists.|路由条目配额规则不存在。|
|400|Forbidden.CheckEntryRuleQuota|Route entry quota rule check error.|检查路由条目配额时发生了错误。|
|400|InvalidVBRStatus|invalid virtual border router status.|边界路由器状态不合法。|
|400|InvalidPhysicalConnectionBusinessStatus|invalid physical connection business status.|物理专线状态不合法。|
|404|InvalidHaVipId.NotFound|The specified HaVip does not exist in the specified VPC.|该HAVIP在VPC中不存在。|
|400|IncorrectHaVipStatus|This operation is denied because satus of the specified HaVip is neither Available nor InUse.|无法执行该操作，因为HAVIP的状态是Available或InUse。|
|400|CountLimitExceed.HaVipRouteEntry|There can be 5 route entry to HaVip at most in one route table.|指向该 HaVip 实例的路由条目数量已达上限。|
|400|InvalidRouteEntry.Duplicate|The route entry already exist.|指定的路由条目已存在。|
|403|IncorrectInstanceStatus|The current status of the resource does not support this operation.|当前资源的状态不支持该操作。|
|400|InvalidCidrBlock|Specified CIDR block is already exists.|该交换机网段与其他交换机的网段重叠或与已有的自定义路由的目标网段重叠，请使用其他未被占用的网段。|
|400|IncorrectRouteEntryStatus|Specified routeEntry status error.|无法执行该操作，当前路由表中有路由条目的状态为pending或modifying。|
|400|IncorrectRouteEntryStatus|The vpc has NotStable routeEntry status.|无法执行该操作，当前路由表中有路由条目的状态为pending或modifying。|
|400|IncorrectRouteEntryStatus|VBR has NotStable route entry.|无法执行该操作，边界路由表中有路由条目的状态为pending或modifying。|
|400|InvalidParam|The Ecmp routerEntry with router interfaces local vgw vip not match.|路由条目与路由器接口本地视频网关VIP不匹配。|
|400|INVALID\_WEIGHT\_PARAM|Specified value of weight invalid|该权重不合法。|
|400|FORBIDDEN\_USE\_VPC\_AS\_INTERNET\_GATEWAY|The Specified CIDR must be in vpc CIDR.|该网段必须是VPC网段的子集。|
|400|INVALID\_VPC\_ID|The Specified VpcId not match.|该 VPC 不存在，请您检查输入的 VPC 是否正确。|
|400|InvalidRouteEntrySize|The Specified routerEntry size not legal.|等价路由需要选择2-4个路由器接口作为路由下一跳。|
|400|InvalidRouteEntry|Specified routeEntry not exist.|该路由条目不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

