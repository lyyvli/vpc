# DescribeRouterInterfaces {#doc_api_1116071 .reference}

调用DescribeRouterInterfaces查询指定地域内的路由器接口。

您可以通过以下过滤条件对结果进行过滤。每个过滤条件的多个值之间是“or”关系，即只要与其中一个值吻合则视为符合该过滤条件。各个过滤条件之间为“and”关系，即符合所有指定的过滤条件，才会进入最终的查询结果。

-   **RouterInterfaceId**：路由器接口ID。
-   **RouterId**：路由器ID。
-   **RouterType**：路由器类型，取值：**VRouter| VBR**。
-   **RouterInterfaceOwnerId**：路由器接口的所属账号ID。
-   **OppositeInterfaceId**：对端路由器接口ID。
-   **OppositeRouterType**：对端路由器接口类型，取值：**VRouter | VBR**。
-   **OppositeRouterId**：对端路由器接口ID。
-   **OppositeInterfaceOwnerId**：对端路由器接口所属账号ID。
-   **Status**：路由器接口状态。
-   **Name**：路由器接口名称。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeRouterInterfaces)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRouterInterfaces|要执行的操作。

 取值： **DescribeRouterInterfaces**。

 |
|RegionId|String|是|cn-hangzhou|路由器接口所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|Filter.N.Key|String|否|Filter.1.status|第n个过滤条件的类型。N的取值范围：**1-5**。

 |
|Filter.N.Value.N|RepeatList|否|Filter.1.Active|第n个过滤器的第m个值。

 M的取值范围：**1-5**。

 |
|IncludeReservationData|Boolean|否|false|是否包含续费数据。

 |
|PageNumber|Integer|否|10|列表的页码，默认值为1。

 |
|PageSize|Integer|否|1|分页查询时每页的行数，最大值为50，默认值为10。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|TotalCount|Integer|10|列表条条目数。

 |
|PageNumber|Integer|10|当前页码。

 |
|PageSize|Integer|10|每页包含多少条目。

 |
|RequestId|String|C7F6FCBD-F9CC-4501-8EF3-CDC9577CAE45|请求ID。

 |
|RouterInterfaceSet| | |路由器接口的详细信息。

 |
|└AccessPointId|String|ap-cn-shanghaiSZ-pd-A|接入点ID。

 |
|└Bandwidth|Integer|10|路由器接口的带宽。

 |
|└BusinessStatus|String|Normal|路由器接口的业务状态：

 -   **Normal**：正常
-   **FinancialLocked**：欠费锁定
-   **SecurityLocked**：安全风控锁定

 |
|└ChargeType|String|PayByTraffic|付费方式。

 |
|└ConnectedTime|String|2017-06-08T12:20:55|连接建立的时间。

 |
|└CreationTime|String|2017-06-08T12:20:55|路由表的创建时间。

 |
|└CrossBorder|Boolean|false|是否是跨境连接。

 |
|└Description|String|路由表接口描述。|路由表接口描述。

 |
|└EndTime|String|2017-06-08T12:20:55|获取数据的结束时间点。

 |
|└HasReservationData|String|false|是否有续费数据。

 |
|└HealthCheckSourceIp|String|116.62.222.28|健康检查源IP。

 |
|└HealthCheckTargetIp|String|116.62.222.28|健康检查目标IP。

 |
|└Name|String|test|自定义名称.

 |
|└OppositeAccessPointId|String|ap-cn-shanghaiSZ-pd-A|对端接入点ID。

 |
|└OppositeBandwidth|Integer|12|对端带宽。

 |
|└OppositeInterfaceBusinessStatus|String|Normal|连接对端的路由器接口的业务状态。

 |
|└OppositeInterfaceId|String|ri-bp1itx13bwe6f2wfh3qpj|对端路由器接口ID。

 |
|└OppositeInterfaceOwnerId|String|1231579085529123|对端路由器接口的账号ID。

 |
|└OppositeInterfaceSpec|String|Large|连接对端路由器接口的规格。

 |
|└OppositeInterfaceStatus|String|Normal|连接对端的路由器接口的状态。

 |
|└OppositeRegionId|String|cn-shanghai|连接对端所处的地域。

 |
|└OppositeRouterId|String|vrt-bp1d3bxtdv68tfd7gfjkd|连接对端的路由器接口所属的路由器ID。

 |
|└OppositeRouterType|String|VRouter|连接对端的路由器接口所属的路由器类型。

 |
|└OppositeVpcInstanceId|String|vpc-bp1qpo0kug3a20qqe9h7v|对端的VPC ID。

 |
|└ReservationActiveTime|String|2019-03-11T16:00:00Z|续费生效时间。

 |
|└ReservationBandwidth|String|10|续费带宽。

 |
|└ReservationInternetChargeType|String|PayByBandwidth|续费付费类型。

 |
|└ReservationOrderType|String|RENEWCHANGE|续费订单类型。

 |
|└Role|String|InitiatingSide|对等连接中的角色。

 |
|└RouterId|String|vrt-bp1d3bxtdv68tfd7gfjkd|路由条目所在路由器的ID。

 |
|└RouterInterfaceId|String|ri-2zenfgfpyu3v93koa4sfo|路由器接口的ID。

 |
|└RouterType|String|VRouter|路由表所在路由器的类型，取值：

 -   VRouter：VPC路由器
-   VBR：边界路由器

 |
|└Spec|String|Large|路由器接口的规格。

 |
|└Status|String|active|路由器接口的状态。

 |
|└VpcInstanceId|String|vpc-2ze3tq4uxhysg717x7o4d|对等连接中本端VPC的ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeRouterInterfaces
&RegionId= cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<?xml version="1.0" encoding="UTF-8" ?>
<DescribeRouterInterfacesResponse>
	<PageNumber>1</PageNumber>
	<TotalCount>2</TotalCount>
	<PageSize>10</PageSize>
	<RequestId>01818199-04F6-47F4-9ADF-7CC824CF57A4</RequestId>
	<RouterInterfaceSet>
		<RouterInterfaceType>
			<ChargeType>Prepaid</ChargeType>
			<HasReservationData>false</HasReservationData>
			<OppositeInterfaceBusinessStatus>Normal</OppositeInterfaceBusinessStatus>
			<RouterInterfaceId>ri-2zenfgfpyu3v93koa4sfo</RouterInterfaceId>
			<OppositeInterfaceStatus>Deleted</OppositeInterfaceStatus>
			<Spec>Small.5</Spec>
			<OppositeInterfaceOwnerId>1231579085529123</OppositeInterfaceOwnerId>
			<CrossBorder>false</CrossBorder>
			<OppositeInterfaceSpec>Negative</OppositeInterfaceSpec>
			<CreationTime>2017-12-27T06:34:30Z</CreationTime>
			<RouterType>VRouter</RouterType>
			<Status>Inactive</Status>
			<OppositeRouterType>VRouter</OppositeRouterType>
			<OppositeRouterId>vrt-bp1el837xkkakub7ci0tj</OppositeRouterId>
			<OppositeInterfaceId>ri-bp1itx13bwe6f2wfh3qpj</OppositeInterfaceId>
			<VpcInstanceId>vpc-2ze3tq4uxhysg717x7o4d</VpcInstanceId>
			<RouterId>vrt-2zeazning6tbzkm5c0jj2</RouterId>
			<ConnectedTime>2017-12-27T06:34:37Z</ConnectedTime>
			<OppositeRegionId>cn-hangzhou</OppositeRegionId>
			<BusinessStatus>Normal</BusinessStatus>
			<Role>InitiatingSide</Role>
			<OppositeVpcInstanceId>vpc-bp1iq3579f26c3gpkj92e</OppositeVpcInstanceId>
			<EndTime>2018-01-27T16:00:00Z</EndTime>
		</RouterInterfaceType>
		<RouterInterfaceType>
			<ChargeType>Prepaid</ChargeType>
			<HasReservationData>false</HasReservationData>
			<OppositeInterfaceBusinessStatus>Normal</OppositeInterfaceBusinessStatus>
			<RouterInterfaceId>ri-2zegbp7nhj0mnwm6irnuo</RouterInterfaceId>
			<OppositeInterfaceStatus>Deleted</OppositeInterfaceStatus>
			<Spec>Small.1</Spec>
			<OppositeInterfaceOwnerId>1231579085529123</OppositeInterfaceOwnerId>
			<CrossBorder>false</CrossBorder>
			<OppositeInterfaceSpec>Negative</OppositeInterfaceSpec>
			<CreationTime>2017-12-27T06:31:30Z</CreationTime>
			<RouterType>VRouter</RouterType>
			<Status>Inactive</Status>
			<OppositeRouterType>VRouter</OppositeRouterType>
			<OppositeRouterId>vrt-bp1d3bxtdv68tfd7gfjkd</OppositeRouterId>
			<OppositeInterfaceId>ri-bp12dxgw8gmoma1h506qf</OppositeInterfaceId>
			<VpcInstanceId>vpc-2ze3tq4uxhysg717x7o4d</VpcInstanceId>
			<RouterId>vrt-2zeazning6tbzkm5c0jj2</RouterId>
			<ConnectedTime>2017-12-27T06:31:36Z</ConnectedTime>
			<OppositeRegionId>cn-hangzhou</OppositeRegionId>
			<BusinessStatus>Normal</BusinessStatus>
			<Role>InitiatingSide</Role>
			<OppositeVpcInstanceId>vpc-bp15k6sx6fhdz2jw4daz0</OppositeVpcInstanceId>
			<EndTime>2018-10-27T16:00:00Z</EndTime>
		</RouterInterfaceType>
	</RouterInterfaceSet>
<DescribeRouterInterfacesResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":2,
	"PageSize":10,
	"RequestId":"01818199-04F6-47F4-9ADF-7CC824CF57A4",
	"RouterInterfaceSet":{
		"RouterInterfaceType":[
			{
				"ChargeType":"Prepaid",
				"HasReservationData":false,
				"OppositeInterfaceBusinessStatus":"Normal",
				"RouterInterfaceId":"ri-2zenfgfpyu3v93koa4sfo",
				"OppositeInterfaceStatus":"Deleted",
				"Spec":"Small.5",
				"OppositeInterfaceOwnerId":"1231579085529123",
				"CrossBorder":false,
				"OppositeInterfaceSpec":"Negative",
				"CreationTime":"2017-12-27T06:34:30Z",
				"RouterType":"VRouter",
				"Status":"Inactive",
				"OppositeRouterId":"vrt-bp1el837xkkakub7ci0tj",
				"OppositeRouterType":"VRouter",
				"OppositeInterfaceId":"ri-bp1itx13bwe6f2wfh3qpj",
				"ConnectedTime":"2017-12-27T06:34:37Z",
				"RouterId":"vrt-2zeazning6tbzkm5c0jj2",
				"VpcInstanceId":"vpc-2ze3tq4uxhysg717x7o4d",
				"BusinessStatus":"Normal",
				"OppositeRegionId":"cn-hangzhou",
				"Role":"InitiatingSide",
				"EndTime":"2018-01-27T16:00:00Z",
				"OppositeVpcInstanceId":"vpc-bp1iq3579f26c3gpkj92e"
			},
			{
				"ChargeType":"Prepaid",
				"HasReservationData":false,
				"OppositeInterfaceBusinessStatus":"Normal",
				"RouterInterfaceId":"ri-2zegbp7nhj0mnwm6irnuo",
				"OppositeInterfaceStatus":"Deleted",
				"Spec":"Small.1",
				"OppositeInterfaceOwnerId":"1231579085529123",
				"CrossBorder":false,
				"OppositeInterfaceSpec":"Negative",
				"CreationTime":"2017-12-27T06:31:30Z",
				"RouterType":"VRouter",
				"Status":"Inactive",
				"OppositeRouterId":"vrt-bp1d3bxtdv68tfd7gfjkd",
				"OppositeRouterType":"VRouter",
				"OppositeInterfaceId":"ri-bp12dxgw8gmoma1h506qf",
				"ConnectedTime":"2017-12-27T06:31:36Z",
				"RouterId":"vrt-2zeazning6tbzkm5c0jj2",
				"VpcInstanceId":"vpc-2ze3tq4uxhysg717x7o4d",
				"BusinessStatus":"Normal",
				"OppositeRegionId":"cn-hangzhou",
				"Role":"InitiatingSide",
				"EndTime":"2018-10-27T16:00:00Z",
				"OppositeVpcInstanceId":"vpc-bp15k6sx6fhdz2jw4daz0"
			}
		]
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidFilterKey.ValueNotSupported|Specified filter key is not supported: Filter.X.key|该过滤器的Key不支持：Filter.X.key|
|400|InvalidParam.NotNull|The parameter must not be null.|参数不能为空。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

