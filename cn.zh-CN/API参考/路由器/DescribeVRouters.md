# DescribeVRouters {#doc_api_1052026 .reference}

调用DescribeVRouters查询指定地域的路由器列表。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVRouters)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeVRouters|要执行的操作。

 取值：**DescribeVRouters**。

 |
|RegionId|String|是|cn-hangzhou|VPC所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VRouterId|String|否|vrt-bp1lhl0taikrteen80oxx|路由器的ID。

 |
|PageNumber|Integer|否|10|列表的页码，默认值为1。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|VRouters| | |路由器的详细信息。

 |
|└CreationTime|String|2018-03-22T07:46:20Z|VPC路由器的创建时间。

 |
|└Description|String|路由器描述。|VPC路由器的描述信息。

 |
|└RegionId|String|us-west-1|VPC所在的地域。

 |
|└RouteTableIds| |\{ "RouteTableId": \[ "vtb-rj9ybe3y0u41mmjspmop0" \] \}|VPC路由器的路由表的ID。

 |
|└VRouterId|String|vrt-rj98khsezfqpjrxmvl7cy|VPC路由器的ID。

 |
|└VRouterName|String|doctest|VPC路由器的名称。

 |
|└VpcId|String|vpc-rj905wotv6y030t1zz5vl|路由器所属VPC的ID。

 |
|TotalCount|Integer|1|列表条目数。

 |
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|2|每页包含的条目数。

 |
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeVRouters
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeVRoutersResponse>
  <PageNumber>1</PageNumber>
  <TotalCount>2</TotalCount>
  <VRouters>
    <VRouter>
      <VRouterName/>
      <RouteTableIds>
        <RouteTableId>vtb-bp1krxxzp0c29fmontbal</RouteTableId>
      </RouteTableIds>
      <CreationTime>2018-12-06T06:11:55Z</CreationTime>
      <Description/>
      <RegionId>cn-hangzhou</RegionId>
      <VRouterId>vrt-bp1jcg5cmxjbl9xgc58bw</VRouterId>
      <VpcId>vpc-bp1qpo0kug3a20qqe9h7v</VpcId>
    </VRouter>
    <VRouter>
      <VRouterName/>
      <RouteTableIds>
        <RouteTableId>vtb-bp1blq1oh0ybfnpm1bh20</RouteTableId>
      </RouteTableIds>
      <CreationTime>2018-11-08T08:54:03Z</CreationTime>
      <Description/>
      <RegionId>cn-hangzhou</RegionId>
      <VRouterId>vrt-bp149ve7yeyvio4ncklxz</VRouterId>
      <VpcId>vpc-bp1aevy8sofi8mh1qc5cm</VpcId>
    </VRouter>
  </VRouters>
  <PageSize>10</PageSize>
  <RequestId>EE4C2417-9437-4333-BDEB-8493F7AA7258</RequestId>
</DescribeVRoutersResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":1,
	"VRouters":{
		"VRouter":[
			{
				"CreationTime":"2018-03-22T07:46:20Z",
				"RouteTableIds":{
					"RouteTableId":[
						"vtb-rj9ybe3y0u41mmjspmop0"
					]
				},
				"VRouterName":"",
				"Description":"",
				"RegionId":"us-west-1",
				"VpcId":"vpc-rj905wotv6y030t1zz5vl",
				"VRouterId":"vrt-rj98khsezfqpjrxmvl7cy"
			}
		]
	},
	"PageSize":10,
	"RequestId":"CB2793A8-845F-444C-8E93-76F1BBDF9C78"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

