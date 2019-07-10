# CreateVpc {#doc_api_Vpc_CreateVpc .reference}

调用CreateVpc接口创建一个专有网络（VPC）。

**调用该接口创建VPC时，请注意：**

-   一个VPC只能指定一个网段，网段的范围包括10.0.0.0/8、172.16.0.0/12和192.168.0.0/16以及它们的子网，网段的掩码为8-24位，默认为172.16.0.0/12。
-   VPC创建后无法修改网段。
-   每个VPC包含的云产品实例数量不超过15,000个。
-   创建VPC后，会自动创建一个虚拟路由器和一个路由表。
-   每个VPC支持三个用户侧网段。如果多个用户侧网段之间存在互相包含，掩码较短的网段实际生效。例如10.0.0.0/8和10.1.0.0/16中，10.0.0.0/8实际生效。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CreateVpc)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateVpc|要执行的操作，取值：**CreateVpc**。

 |
|RegionId|String|是|cn-hangzhou|VPC所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|CidrBlock|String|否|172.16.0.0/12|VPC的网段。您可以使用以下网段或其子集：

 -   10.0.0.0/8。
-   172.16.0.0/12（默认值）。
-   192.168.0.0/16。

 |
|ClientToken|String|否|sha223ndd2333|客户端token，用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。

 |
|Description|String|否|This is my first Vpc.|VPC的描述信息。长度为2-256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|EnableIpv6|Boolean|否|0|是否开启IPv6网段，取值：

 -   **false**（默认值）：不开启。
-   **true**：开启。

 |
|Ipv6CidrBlock|String|否|2408:4004:0:6axx::/56|VPC的IPv6网段。

 |
|ResourceGroupId|String|否|rg-acfmxazb4ph6aiy\*\*\*\*|资源组ID。关于资源组的更多信息，请参见[什么是资源组](~~94475~~)。

 |
|UserCidr|String|否|189.16.0.0/12|用户侧网络的网段，如需定义多个网段请使用半角逗号隔开，最多支持3个网段。

 VPC定义的默认私网转发网段为10.0.0.0/8、172.16.0.0/12、192.168.0.0/16、100.64.0.0/10和VPC CIDR网段。如果ECS实例或弹性网卡已经具备了公网访问能力（ECS实例分配了固定公网IP、ECS实例或弹性网卡绑定了公网IP、ECS实例或弹性网卡设置了DNAT IP映射规则），这类资源访问非上述默认私网转发网段的请求均会通过公网IP直接转发至公网。当希望按照路由表在私网（如VPC内、通过VPN/高速通道/云企业网搭建的混合云网络）转发访问非上述默认私网网段的请求时，需要将网络请求的目的网段设置为ECS或弹性网卡所在VPC的UserCidr。为VPC设置UserCidr后，该VPC中访问UserCidr地址的请求将按照路由表进行转发，而不通过公网IP转发。

 |
|VpcName|String|否|vpc-hp3ld1aq7kl4k7skh\*\*\*\*|VPC的名称。长度为2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-），但不能以`http://`或`https://`开头。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|VpcId|String|vpc-bp15zckdt37pq72zv\*\*\*\*|VPC的ID。

 |
|VRouterId|String|vrt-bp1lhl0taikrteen8\*\*\*\*|路由器的ID。

 |
|RouteTableId|String|vtb-bp145q7glnuzdv\*\*\*\*|路由表的ID。

 |
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。

 |
|ResourceGroupId|String|rg-acfmxazb4ph6aiy\*\*\*\*|资源组ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateVpc
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateVpcResponse>
  <ResourceGroupId>rg-acfmxazb4ph****</ResourceGroupId>
  <RequestId>8B2F5262-6B57-43F2-97C4-971425462DFE</RequestId>
  <RouteTableId>vtb-bp1krxxzp0c2****</RouteTableId>
  <VRouterId>vrt-bp1jcg5cmxjbl9xgc****</VRouterId>
  <VpcId>vpc-bp1qpo0kug3a20qqe****</VpcId>
</CreateVpcResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"8B2F5262-6B57-43F2-97C4-971425462DFE",
	"ResourceGroupId":"rg-acfmxazb4ph****",
	"RouteTableId":"vtb-bp1krxxzp0c29****",
	"VpcId":"vpc-bp1qpo0kug3a20qqe****",
	"VRouterId":"vrt-bp1jcg5cmxjbl9xgc****"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|Specified value of "regionId" is not supported.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|InvalidParameter|Specified CIDR block is not valid|该网段不合法。|
|400|ResourceNotAvailable|Resource you requested is not available in this region or zone.|当前地域或可用区不支持创建交换机。|
|400|InvalidVpcName.Malformed|Specified VPC name is not valid.|专有网络VPC名称格式不正确，请您修复VPC的格式后再重试。|
|400|InvalidVpcDiscription.Malformed|Specified VPC description is not valid.|该 VPC 描述的格式不符合要求。|
|403|Forbbiden|User not authorized to operate on the specified resource.|您没有权限操作该资源，请您申请操作权限后再试。|
|400|QuotaExceeded.Vpc|VPC quota exceeded.|用户名下的 VPC 数量达到配额上限，请提交工单申请提高配额。|
|400|ResourceNotAvailable.Vpc|Resource you requested is not available in this region or zone.|您请求的资源在在该地域或可用区中不可用。|
|400|InvalidParameter|Specified UserCidr invalid format.|该用户侧网段格式不正确。|
|400|InvalidParameter|Specified UserCidr Subnet mask is not valid .|该用户侧网段的子网掩码不合法。|
|400|InvalidUserCidr.Quota|Specified UserCidr number is greater than 3.|UserCird达到配额限制。|
|400|InvalidUserCidr.Malformed|Specified UserCidr overlapping in of 100.64.0.0/10.|该UserCird和100.64.0.0/10重叠。|
|500|InternalError|The request processing has failed due to some unknown error.|请求处理由于某些未知错误失败。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

