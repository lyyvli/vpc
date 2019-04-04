# DescribeRouteTableList {#doc_api_1107885 .reference}

使用DescribeRouteTableList查询路由表。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeRouteTableList)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRouteTableList|要执行的操作。

 取值： **DescribeRouteTableList**。

 |
|RegionId|String|是|cn-hangzhou|路由表所属的VPC的地域ID。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为1。

 |
|PageSize|Integer|否|12|分页查询时每页的行数，最大值为50，默认值为10。

 |
|ResourceGroupId|String|否|rg-acfmxazb4ph6aiy|资源组ID。

 |
|RouteTableId|String|否|vtb-bp145q7glnuzdvzu21pom|路由表的ID。

 |
|RouteTableName|String|否|doctest|路由表的名称。

 |
|RouterId|String|否|vrt-bp1lhl0taikrteen80oxx|路由表所属路由器的ID。

 |
|RouterType|String|否|VBR|路由表所属的路由器类型。取值：

 -   VRouter（默认值）：VPC路由器
-   VBR：边界路由器

 |
|VpcId|String|否|vpc-bp15zckdt37pq72zvw3|路由表所属的VPC路由器的ID。

 指定该参数后，参数**RouterType**的值自动设置为**VRouter**。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PageNumber|Integer|12|当前页码。

 |
|PageSize|Integer|1|每页包含多少条目。

 |
|RequestId|String|DC668356-BCB4-42FD-9BC3-FA2B2E04B634|请求ID。

 |
|RouterTableList| | |路由表。

 |
|└CreationTime|String|2017-08-22T10:40:25Z|路由表的创建时间。按照ISO8601标准表示，使用UTC时间，格式为**YYYY-MM-DDThh:mmZ**。

 |
|└Description|String|This is Route Table.|路由表的描述。

 |
|└ResourceGroupId|String|rg-acfmxazb4ph6aiy|资源组ID。

 |
|└RouteTableId|String|vtb-bp145q7glnuzdvzu21pom|路由表的ID。

 |
|└RouteTableName|String|doctest|路由表的名称。

 |
|└RouteTableType|String|System| 

 路由表的类型。取值：

 -   Custom：自定义路由表
-   System：系统路由表

 |
|└RouterId|String|vrt-bp1lhl0taikrteen80oxx|路由表所属的路由器ID。

 |
|└RouterType|String|VBR| 

 路由表所属的路由器类型。取值：

 -   VRouter：VPC路由器
-   VBR：边界路由器

 |
|└Tags| | |路由表的标签。

 |
|└VSwitchIds| |vsw-bp12mw1f8k3jgygk9bmlj|VPC下的交换机列表。

 |
|└VpcId|String|vpc-bp15zckdt37pq72zvw3|路由表所属的VPC路由器的ID。

 指定该参数后，参数**RouterType**的值自动设置为**VRouter**。

 |
|TotalCount|Integer|12|列表条目数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeRouteTableList
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeRouteTableListResponse>
  <Code>200</Code>
  <Message>successful</Message>
  <PageNumber>1</PageNumber>
  <PageSize>10</PageSize>
  <RequestId>87261511-FEB9-4BEC-85BF-70XXXXXXXXX</RequestId>
  <RouterTableList>
    <RouterTableListType>
      <CreationTime>2018-08-03T08:14:54Z</CreationTime>
      <Description>ddd</Description>
      <RouteTableId>vtb-m5evbtbptnx2bXXXXXXXXX</RouteTableId>
      <RouteTableName>aaa1111</RouteTableName>
      <RouteTableType>Custom</RouteTableType>
      <RouterId>vrt-m5egeuhgj52xgXXXXXXXXX</RouterId>
      <RouterType>VRouter</RouterType>
      <VSwitchIds>
        <VSwitchId>vsw-m5e3r57pxkgijXXXXXXXXX</VSwitchId>
      </VSwitchIds>
      <VpcId>vpc-m5epe3ag3qXXXXXXXXX</VpcId>
    </RouterTableListType>
  </RouterTableList>
</DescribeRouteTableListResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":1,
	"RouterTableList":{
		"RouterTableListType":[
			{
				"CreationTime":"2018-08-03T08:14:54Z",
				"RouterType":"VRouter",
				"Description":"ddd",
				"VSwitchIds":{
					"VSwitchId":[
						"vsw-m5e3r57pxkgijXXXXXXXXX"
					]
				},
				"RouterId":"vrt-m5egeuhgj52xgXXXXXXXXX",
				"RouteTableId":"vtb-m5evbtbptnx2bXXXXXXXXX",
				"RouteTableName":"aaa1111",
				"VpcId":"vpc-m5epe3ag3qXXXXXXXXX",
				"RouteTableType":"Custom"
			}
		]
	},
	"Message":"successful",
	"PageSize":10,
	"RequestId":"87261511-FEB9-4BEC-85BF-70XXXXXXXXX",
	"Success":true,
	"Code":"200"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden|User not authorized to operate on the specified resource.|您没有权限操作该资源，请您申请操作权限后再试。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

