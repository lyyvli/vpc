# DescribeVirtualBorderRouters {#doc_api_Vpc_DescribeVirtualBorderRouters .reference}

调用DescribeVirtualBorderRouters接口查询已创建的边界路由器（VBR）。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeVirtualBorderRouters&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeVirtualBorderRouters|要执行的操作。

 取值：**DescribeVirtualBorderRouters**。

 |
|RegionId|String|是|cn-shanghai|VBR所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|Filter.N.Key|String|否|1|第n个过滤器的类型，N取值：**1-5**。

 |
|Filter.N.Value.N|RepeatList|否|1|第n个过滤器的第m个值，M取值：**1-5**。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为**1**。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为**50**，默认值为**10**。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|VirtualBorderRouterSet| | |查询到的VBR合集。

 |
|AccessPointId|String|ap-cn-kojok1xxxxxxxx|物理专线接入点的ID。

 |
|ActivationTime|String|2017-06-08T12:20:55|VBR第一次激活的时间。

 |
|AssociatedCens| | |云企业网。

 |
|CenId|String|cen-kojok19xxxxxxxx|云企业网实例的ID。

 |
|CenOwnerId|Long|1086496381294461|云企业网实例所属账号的UID。

 |
|CenStatus|String|Attached|云企业网状态。

 |
|AssociatedPhysicalConnections| | |绑定的物理连接。

 |
|CircuitCode|String|12|VBR专线侧接口对应运营商的电路编码。

 |
|LocalGatewayIp|String|116.62.xx.xx|VBR专线侧接口本端的IP地址。

 |
|PeerGatewayIp|String|116.62.xx.xx|VBR专线侧接口对端的IP地址。

 |
|PeeringSubnetMask|String|255.255.255.252|实VBR专线侧接口本端与对端互联的子网掩码。

 |
|PhysicalConnectionBusinessStatus|String|Normal|物理专线业务状态。

 |
|PhysicalConnectionId|String|pc-119mfjzm7xxxxxxxx|物理专线ID。

 |
|PhysicalConnectionOwnerUid|String|qfrgrgs|物理专线owner的UID。

 |
|PhysicalConnectionStatus|String|Normal|物理专线状态。

 |
|VlanId|String|0|VBR的VLAN ID。

 |
|VlanInterfaceId|String|ri-kojok19x3j0q6kxxxxxxxxx|虚拟边界路由器（VBR）专线侧接口（RouterInterface）的ID。可以用来做VBR上路由的下一跳。

 |
|CircuitCode|String|longtel001|运营商为物理专线提供的电路编码。

 |
|CreationTime|String|2017-06-08T12:20:55|VBR的创建时间。

 |
|Description|String|VBR|VBR的描述信息。

 |
|DetectMultiplier|Long|3|检测时间倍数。即接收方允许发送方发送报文的最大连接丢包数，用来检测链路是否正常，取值：3-10。

 |
|LocalGatewayIp|String|116.62.xx.xx|阿里云侧互联IP。

 |
|MinRxInterval|Long|100|配置BFD报文的接收间隔，取值：200-1000，单位为ms。

 |
|MinTxInterval|Long|100|配置BFD报文的发送间隔，取值：200-1000，单位为ms。

 |
|Name|String|test|VBR的名称。

 |
|PeerGatewayIp|String|116.62.xx.xx|客户侧互联IP。

 |
|PeeringSubnetMask|String|255.255.255.252|阿里云侧互联IP和客户侧互联IP的子网掩码。

 |
|PhysicalConnectionBusinessStatus|String|Normal|物理专线业务状态。

 |
|PhysicalConnectionId|String|pc-119mfjzm7xxxxxxxx|VBR所属的物理专线的ID。

 |
|PhysicalConnectionOwnerUid|String|usdgbh123fvgf|物理专线owner的UID。

 |
|PhysicalConnectionStatus|String|Normal|物理专线状态。

 |
|RecoveryTime|String|2017-06-08T12:20:55|VBR最近一次从Terminated状态恢复到Active状态的时间。

 |
|RouteTableId|String|rtb-bp1nxxxxxxxxxxxxxxxx|VBR的路由表的ID。

 |
|Status|String|active|物理专线状态：

 -   Initial：申请中
-   Approved：审批通过
-   Allocating：正在分配资源
-   Allocated：接入施工中。
-   Confirmed：等待用户确认
-   Enabled：已开通
-   Rejected：申请被拒绝
-   Canceled：已取消
-   Allocation Failed：资源分配失败
-   Terminated：已终止

 |
|TerminationTime|String|2017-06-08T12:20:55|VBR最近一次被终止的时间。

 |
|VbrId|String|vbr-kojok19xxxxxxxxx|VBR的ID。

 |
|VlanId|Integer|10|VBR的VLAN ID。

 |
|VlanInterfaceId|String|ri-2zeo3xzyf38r4xxxxxxxx|VBR的路由器接口的ID。

 |
|TotalCount|Integer|1|列表条条目数。

 |
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|10|每页包含多少条目。

 |
|RequestId|String|DE77A7F3-3B74-41C0-A5BC-CAFD188C28B6|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeVirtualBorderRouters
&RegionId=cn-shanghai
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeVirtualBorderRoutersResponse>
		  <RequestId>AE65530E-8436-4FB1-8217-DCD35712AC89</RequestId>
		  <PageNumber>1</PageNumber>
		  <VirtualBorderRouterSet>
			    <VirtualBorderRouterType>
				      <LocalGatewayIp>10.1.xx.xx</LocalGatewayIp>
				      <PeerGatewayIp>10.2.xx.xx</PeerGatewayIp>
				      <PhysicalConnectionOwnerUid>123157908XXXXXXXX</PhysicalConnectionOwnerUid>
				      <VlanId>10</VlanId>
				      <PhysicalConnectionStatus>Enabled</PhysicalConnectionStatus>
				      <PhysicalConnectionId>pc-2zeoaxkq3jotxxxxxxxx</PhysicalConnectionId>
				      <RouteTableId>vtb-2ze9hmd6yofwvxxxxxxxx</RouteTableId>
				      <PeeringSubnetMask>255.0.0.0</PeeringSubnetMask>
				      <CreationTime>2018-03-06T11:16:34Z</CreationTime>
				      <ActivationTime>2018-03-06T11:16:34Z</ActivationTime>
				      <Status>active</Status>
				      <PhysicalConnectionBusinessStatus>Normal</PhysicalConnectionBusinessStatus>
				      <VlanInterfaceId>ri-2zeum6rgu0586xxxxxxxx</VlanInterfaceId>
				      <AccessPointId>ap-cn-beijing-dx-A</AccessPointId>
				      <VbrId>vbr-2zecmmvg5gxxxxxxxx</VbrId>
			    </VirtualBorderRouterType>
		  </VirtualBorderRouterSet>
		  <TotalCount>1</TotalCount>
		  <PageSize>10</PageSize>
</DescribeVirtualBorderRoutersResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"DescribeVirtualBorderRoutersResponse":{
		"PageNumber":"1",
		"VirtualBorderRouterSet":{
			"VirtualBorderRouterType":{
				"LocalGatewayIp":"10.1.xx.xx",
				"PeerGatewayIp":"10.2.xx.xx",
				"PhysicalConnectionOwnerUid":"123157908XXXXXXXX",
				"VlanId":"10",
				"PhysicalConnectionStatus":"Enabled",
				"PhysicalConnectionId":"pc-2zeoaxkq3jotxxxxxxxx",
				"RouteTableId":"vtb-2ze9hmd6yofwvxxxxxxxx",
				"PeeringSubnetMask":"255.0.0.0",
				"CreationTime":"2018-03-06T11:16:34Z",
				"ActivationTime":"2018-03-06T11:16:34Z",
				"Status":"active",
				"PhysicalConnectionBusinessStatus":"Normal",
				"VlanInterfaceId":"ri-2zeum6rgu0586xxxxxxxx",
				"VbrId":"vbr-2zecmmvg5gxxxxxxxx",
				"AccessPointId":"ap-cn-beijing-dx-A"
			}
		},
		"TotalCount":"1",
		"PageSize":"10",
		"RequestId":"AE65530E-8436-4FB1-8217-DCD35712AC89"
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidFilterKey.ValueNotSupported|Specified filter key is not supported: Filter.X.key|该过滤器的Key不支持：Filter.X.key|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

