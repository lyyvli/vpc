# DescribeVpnRouteEntries {#doc_api_Vpc_DescribeVpnRouteEntries .reference}

调用DescribeVpnRouteEntries查询VPN目的路由。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeVpnRouteEntries&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeVpnRouteEntries|要执行的操作，取值：**DescribeVpnRouteEntries**。

 |
|RegionId|String|是|cn-hangzhou|VPN目的路由所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VpnGatewayId|String|是|vpn-bp1a3kqjiiq9legfx\*\*\*\*|VPN网关的ID。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为**1**。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为**50**，默认值为**10**。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PageNumber|Integer|10|当前页码。

 |
|PageSize|Integer|10|每页包含的条目数。

 |
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。

 |
|TotalCount|Integer|10|列表条目数。

 |
|VpnRouteEntries| | |VPN目的路由的详细信息。

 |
|CreateTime|Long|1492747187000|VPN目的路由的创建时间。

 |
|NextHop|String|vco-bp15oes1py4i66rmd\*\*\*\*|目的路由的下一跳。

 |
|RouteDest|String|10.0.0.0/24|目的路由的目标网段。

 |
|State|String|published|VPN目的路由的状态。

 |
|VpnInstanceId|String|vpn-bp1cmw7jh1nfe43m9\*\*\*\*|VPN网关的ID。

 |
|Weight|Integer|0|目的路由的权重值，取值：**0**|**100**。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeVpnRouteEntries
&RegionId=cn-hangzhou
&VpnGatewayId=vpn-bp1a3kqjiiq9legfx****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeVpnRouteEntriesResponse>
	  <PageNumber>1</PageNumber>
	  <TotalCount>1</TotalCount>
	  <VpnRouteEntries>
		    <VpnRouteEntry>
			      <RouteDest>10.0.0.0/24</RouteDest>
			      <VpnInstanceId>vpn-bp1cmw7jh1nfe43m9****</VpnInstanceId>
			      <State>normal</State>
			      <Weight>100</Weight>
			      <CreateTime>1563874074000</CreateTime>
			      <NextHop>vco-bp1tui07ob10fmuro****</NextHop>
		    </VpnRouteEntry>
	  </VpnRouteEntries>
	  <PageSize>10</PageSize>
	  <RequestId>BF3995A6-FA4F-4C74-B90F-89ECF4BFF4D5</RequestId>
</DescribeVpnRouteEntriesResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":1,
	"PageSize":10,
	"VpnRouteEntries":{
		"VpnRouteEntry":[
			{
				"RouteDest":"10.0.0.0/24",
				"VpnInstanceId":"vpn-bp1cmw7jh1nfe43m9****",
				"Weight":100,
				"State":"normal",
				"NextHop":"vco-bp1tui07ob10fmuro****",
				"CreateTime":1563874074000
			}
		]
	},
	"RequestId":"BF3995A6-FA4F-4C74-B90F-89ECF4BFF4D5"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

