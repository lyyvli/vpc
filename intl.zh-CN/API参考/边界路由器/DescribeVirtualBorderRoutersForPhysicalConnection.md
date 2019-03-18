# DescribeVirtualBorderRoutersForPhysicalConnection {#doc_api_1088689 .reference}

使用DescribeVirtualBorderRoutersForPhysicalConnection查询指定物理专线下的边界路由器（VBR），包括物理专线所有者的VBR和其他账号的VBR。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVirtualBorderRoutersForPhysicalConnection)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeVirtualBorderRoutersForPhysicalConnection|要执行的操作。

 取值： **DescribeVirtualBorderRoutersForPhysicalConnection**。

 |
|PhysicalConnectionId|String|是|pc-119mfjzm7|物理专线的ID。

 |
|RegionId|String|是|cn-shanghai|物理专线所在的地域。 您可以通过调用[DescribeRegions](~~36063~~) 接口获取地域ID。

 |
|Filter.N.Key|String|否|1|过滤条件的key。N取值：1-5。

 |
|Filter.N.Value.N|RepeatList|否|1|对应过滤条件的取值。N取值：1-5。

 |
|PageNumber|Integer|否|10|列表的页码，默认值为1。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|VirtualBorderRouterForPhysicalConnectionSet| | |查询到的VBR合集 。

 |
|└ActivationTime|String|2017-06-08T12:20:55|VBR第一次激活的时间。

 |
|└CircuitCode|String|longtel001|运营商为物理专线提供的电路编码。

 |
|└CreationTime|String|2017-06-08T12:20:55|VBR的创建时间。

 |
|└LocalGatewayIp|String|10.0.0.4|VBR的阿里云侧互联IP。

 |
|└PeerGatewayIp|String|10.0.0.5|VBR的客户侧互联IP。

 |
|└PeeringSubnetMask|String|255.255.255.0|VBR的阿里云侧和客户侧互联IP的子网掩码。

 |
|└RecoveryTime|String|2017-06-08T12:20:55|VBR最近一次从Terminated状态恢复到Active状态的时间。

 |
|└TerminationTime|String|2017-06-08T12:20:55|VBR最近一次被终止的时间。

 |
|└VbrId|String|12|VBR的ID。

 |
|└VbrOwnerUid|Long|1342435124|VBR所有者的账号ID，VBR和物理专线的所有者相同时该参数为空。

 |
|└VlanId|Integer|10|VBR的VLAN ID。

 |
|TotalCount|Integer|10|列表条条目数。

 |
|PageNumber|Integer|10|当前页码。

 |
|PageSize|Integer|10|每页包含多少条目。

 |
|RequestId|String|7C5AE8B3-A2D8-428D-A2FF-93A225C0821E|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://vpc.aliyuncs.com/?Action=DescribeVirtualBorderRoutersForPhysicalConnection
&PhysicalConnectionId=pc-119mfjzm7
&RegionId=cn-shanghai
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<?xml version="1.0" encoding="UTF-8"?>
<DescribeVirtualBorderRoutersForPhysicalConnectionResponse>
	<RequestId>03E8CB87-5876-4034-BBB2-6E0851281C37</RequestId>
	<PageNumber>1</PageNumber>
	<TotalCount>2</TotalCount>
	<PageSize>10</PageSize>
	<VirtualBorderRouterForPhysicalConnectionSet>
		<VirtualBorderRouterForPhysicalConnectionType>
			<ActivationTime>2018-03-06T11:16:34Z</ActivationTime>
			<CreationTime>2018-03-06T11:16:34Z</CreationTime>
			<CircuitCode></CircuitCode>
			<VlanId>10</VlanId>
			<RecoveryTime></RecoveryTime>
			<VbrOwnerUxxx231579085529123</VbrOwnerUid>
			<TerminationTime></TerminationTime>
			<VbrId>Vbrxxxxx-2zecmmvg5gvu8i4telkhw</VbrId>
		</VirtualBorderRouterForPhysicalConnectionType>
		<VirtualBorderRouterForPhysicalConnectionType>
			<ActivationTime>2018-01-04T13:34:18Z</ActivationTime>
			<CreationTime>2018-01-04T13:34:18Z</CreationTime>
			<CircuitCode></CircuitCode>
			<VlanId>100</VlanId>
			<RecoveryTime></RecoveryTime>
			<VxxxbrOwnerUid>1231579085529123</VbrOwnerUid>
			<TerminationTime></TerminationTime>
			<VbrId>vbr-2zee2e2cwetx4k0tohakw</VbrId>
		</VirtualBorderRouterForPhysicalConnectionType>
</DescribeVirtualBorderRoutersForPhysicalConnectionResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":2,
	"PageSize":10,
	"RequestId":"03E8CB87-5876-4034-BBB2-6E0851281C37",
	"VirtualBorderRouterForPhysicalConnectionSet":{
		"VirtualBorderRouterForPhysicalConnectionType":[
			{
				"CreationTime":"2018-03-06T11:16:34Z",
				"ActivationTime":"2018-03-06T11:16:34Z",
				"CircuitCode":"",
				"VlanId":10,
				"RecoveryTime":"",
				"VbrOwnerUid":"1231579085xxxxxx529123",
				"VbrId":"vbr-2zecmmvg5gvu8xxxxw",
				"TerminationTime":""
			},
			{
				"CreationTime":"2018-01-04T13:34:18Z",
				"ActivationTime":"2018-01-04T13:34:18Z",
				"CircuitCode":"",
				"VlanId":100,
				"RecoveryTime":"",
				"VbrOwnerUid":"1231579085xxx",
				"VbrId":"vbr-2zee2e2cwetx4k0txxxxakw",
				"TerminationTime":""
			}
		]
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidPhysicalConnectionId.NotFound|The specified PhysicalConnectionId does not belong to user.|该物理专线不属于您的账号。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

