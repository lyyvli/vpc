# DescribeRouteEntryList {#doc_api_Vpc_DescribeRouteEntryList .reference}

调用DescribeRouteEntryList查询路由条目列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeRouteEntryList&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRouteEntryList|要执行的操作，取值：**DescribeRouteEntryList**。

 |
|RegionId|String|是|cn-hangzhou|路由条目所在路由表的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|RouteTableId|String|是|vtb-bp1r9pvl4xen8s9ju\*\*\*\*|路由表ID。

 |
|DestinationCidrBlock|String|否|192.168.2.0/24|路由条目的目标网段，支持IPv4和IPv6网段。

 **说明：** 仅中国站支持IPv6网段。

 |
|IpVersion|String|否|IPv4|IP协议的版本，取值：

 -   **IPv4**：IPv4协议。
-   **IPv6**：IPv6协议。

 **说明：** 仅中国站支持IPv6协议。

 |
|MaxResult|Integer|否|50|分页大小，取值范围：**20**~**100**，默认为**50**。

 |
|NextHopId|String|否|vpn-bp10zyaph5cc8b7c7\*\*\*\*|下一跳实例ID。

 |
|NextHopType|String|否|Instance|下一跳类型，取值：

 -   **Instance**：ECS实例。
-   **HaVip**：高可用虚拟IP。
-   **VpnGateway**：VPN网关。
-   **NatGateway**：NAT网关。
-   **NetworkInterface**：辅助弹性网卡。
-   **RouterInterface**：路由器接口。
-   **IPv6Gateway**：IPv6网关。

 **说明：** 仅中国站支持IPv6网关作为下一跳。

 |
|NextToken|String|否|caeba0bbb2be03f84eb48b699f0a4883|下一个查询开始Token。

 |
|RouteEntryId|String|否|rte-bp1mnnr2al0naomnp\*\*\*\*|路由条目ID。

 |
|RouteEntryName|String|否|abc|路由条目的名称。

 |
|RouteEntryType|String|否|System|路由条目的类型，取值：

 -   **Custom**：自定义路由。
-   **System**：系统路由。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|NextToken|String|caeba0bbb2be03f84eb48b699f0a4883|下一个查询开始Token。

 |
|RequestId|String|14A07460-EBE7-47CA-9757-12CC4761D47A|请求ID。

 |
|RouteEntrys| | |路由条目信息。

 |
|RouteEntry| | |路由条目信息。

 |
|DestinationCidrBlock|String|10.0.0.0/24|路由条目的目标网段。

 |
|IpVersion|String|IPv4|IP协议的版本。

 -   **IPv4**：IPv4协议。
-   **IPv6**：IPv6协议。

 |
|NextHops| | |下一跳信息。

 |
|NextHop| | |下一跳信息。

 |
|Enabled|Integer|0|路由是否可用。

 -   **0**：不可用。
-   **1**：可用。

 |
|NextHopId|String|vpn-bp10zyaph5cc8b7c7\*\*\*\*|下一跳实例ID。

 |
|NextHopRegionId|String|cn-hangzhou|下一跳实例所在的地域。

 |
|NextHopRelatedInfo| | |下一跳相关信息。

 |
|InstanceId|String|vpc-bp1t36rn9l53iwbsf\*\*\*\*|下一跳相关联实例的实例ID。

 |
|InstanceType|String|VPC|下一跳相关联实例的实例类型。

 -   **VPC**：专有网络。
-   **VBR**：边界路由器。

 |
|RegionId|String|ch-hangzhou|下一跳相关联实例所在的地域。

 |
|NextHopType|String|Instance|下一跳类型。

 -   **Instance**：ECS实例。
-   **HaVip**：高可用虚拟IP。
-   **VpnGateway**：VPN网关。
-   **NatGateway**：NAT网关。
-   **NetworkInterface**：辅助弹性网卡。
-   **RouterInterface**：路由器接口。
-   **IPv6Gateway**：IPv6网关。

 **说明：** 仅中国站支持IPv6网关作为下一跳。

 |
|Weight|Integer|100|路由条目的权重。

 |
|RouteEntryId|String|rte-bp1mnnr2al0naomnp\*\*\*\*|路由条目的ID。

 |
|RouteEntryName|String|aaa|路由条目的名称。

 |
|RouteTableId|String|vtb-bp15w5q90d2rk3bww\*\*\*\*|路由表ID。

 |
|Status|String|Available|路由条目的状态。

 |
|Type|String|Custom|路由条目的类型。

 -   **Custom**：自定义路由。
-   **System**：系统路由。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeRouteEntryList
&RegionId=cn-hangzhou
&RouteTableId=vtb-bp1r9pvl4xen8s9ju****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeRouteEntryListResponse>
	  <NextToken></NextToken>
	  <RouteEntrys>
		    <RouteEntry>
			      <NextHops>
				        <NextHop>
					          <NextHopId>eni-bp16v0fuhulfl5e1****</NextHopId>
					          <NextHopRelatedInfo></NextHopRelatedInfo>
					          <NextHopType>NetworkInterface</NextHopType>
				        </NextHop>
			      </NextHops>
			      <Status>Available</Status>
			      <RouteEntryName>ENI</RouteEntryName>
			      <RouteEntryId>rte-bp1aejenqyg5zcmv4****</RouteEntryId>
			      <Type>Custom</Type>
			      <IpVersion>ipv4</IpVersion>
			      <RouteTableId>vtb-bp15w5q90d2rk3bww****</RouteTableId>
			      <DestinationCidrBlock>103.0.0.0/32</DestinationCidrBlock>
		    </RouteEntry>
	  </RouteEntrys>
	  <RequestId>57828ADD-F0C4-4125-AF79-6556D44C5277</RequestId>
</DescribeRouteEntryListResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"NextToken":"",
	"RouteEntrys":{
		"RouteEntry":[
			{
				"Status":"Available",
				"NextHops":{
					"NextHop":[
						{
							"NextHopId":"eni-bp16v0fuhulfl5e1****",
							"NextHopRelatedInfo":{},
							"NextHopType":"NetworkInterface"
						}
					]
				},
				"RouteEntryName":"ENI",
				"Type":"Custom",
				"RouteEntryId":"rte-bp1aejenqyg5zcmv4****",
				"IpVersion":"ipv4",
				"RouteTableId":"vtb-bp15w5q90d2rk3bww****",
				"DestinationCidrBlock":"103.0.0.0/32"
			}
		]
	},
	"RequestId":"57828ADD-F0C4-4125-AF79-6556D44C5277"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

