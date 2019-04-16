# DescribeHaVips {#doc_api_1063462 .reference}

查询指定地域内的高可用虚拟IP实例。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeHaVips)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeHaVips|要执行的操作。 取值：**DescribeHaVips**。

 |
|RegionId|String|是|cn-hangzhou|HaVip实例所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|Filter.N.Key|String|否|HaVipId.havip-bp149uyvut73dplduoq8s|过滤条件，最多可提供5个过滤条件。`n`的取值范围为1~5。

 每个过滤条件（filter key）可以提供多个值，多个值之间是“or”关系，即只要与其中一个值符合则视为符合参数的过滤条件。

 各个过滤条件（filter key）之间为“and”逻辑关系，即符合所有参数的过滤条件，才会被查询出来。

 支持的过滤条件如下：

 -   **VpcId**：专有网络ID。
-   **VSwitchId**：交换机ID。
-   **Status**：HaVip实例状态。
-   **HaVipId**：HaVip实例ID。
-   **HaVipAddress**：HaVip实例的IP地址。

 |
|Filter.N.Value.N|RepeatList|否|1|指定的过滤条件对应的值。`m`的取值范围为1~5。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为`1`。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为`50`，默认值为`10`。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|HaVips| | |HaVip的详细信息。

 |
|└AssociatedEipAddresses| |121.23.36.XX|绑定在该HaVip上的EIP列表。

 |
|└AssociatedInstances| |i-bp145q7glnuzdvzu21xxxx|HaVip的绑定的ECS实例。

 |
|└CreateTime|String|2018-07-03T14:25:26Z|创建时间。

 |
|└Description|String|My HaVip|HaVip实例的描述。

 |
|└HaVipId|String|havip-bp149uyvut73dplduoq8|HaVip实例ID。

 |
|└IpAddress|String|192.168.35.27|HaVip的私网IP地址。

 |
|└MasterInstanceId|String|i-bp145q7glnuzdvzxxxx|当前获得HaVip私网IP的实例ID。

 |
|└RegionId|String|cn-hangzhou|HaVip实例的地域。

 |
|└Status|String|Available|HaVip实例的状态。

 |
|└VSwitchId|String|vsw-bp1pkt1fba8e824ezs80a|HaVip实例所属的交换机ID。

 |
|└VpcId|String|vpc-bp1kcm36tevkpms97o2pm|HaVip实例所属的VPC ID。

 |
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|10|每页包含的条目数。

 |
|RequestId|String|33E480C5-B46F-4CA5-B6FD-D77C746E86AB|请求ID。

 |
|TotalCount|Integer|1|列表条目数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ecs.aliyuncs.com/?Action=DescribeHaVips 
&RegionId=cn-hangzhou 
&Filter=HaVipId.havip-bp149uyvut73dplduoq8s 
&公共请求参数

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeHaVipsResponse>
  <PageNumber>1</PageNumber>
  <TotalCount>1</TotalCount>
  <HaVips>
    <HaVip>
      <Status>Available</Status>
      <Description/>
      <MasterInstanceId/>
      <AssociatedInstances/>
      <AssociatedEipAddresses/>
      <CreateTime>2018-07-03T14:25:26Z</CreateTime>
      <RegionId>cn-hangzhou</RegionId>
      <IpAddress>192.168.35.27</IpAddress>
      <HaVipId>havip-bp149uyvut73dplduoq8s</HaVipId>
      <VSwitchId>vsw-bp1pkt1fba8e824ezs80a</VSwitchId>
      <VpcId>vpc-bp1kcm36tevkpms97o2pm</VpcId>
    </HaVip>
  </HaVips>
  <PageSize>10</PageSize>
  <RequestId>33E480C5-B46F-4CA5-B6FD-D77C746E86AB</RequestId>
</DescribeHaVipsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":1,
	"PageSize":10,
	"HaVips":{
		"HaVip":[
			{
				"Status":"Available",
				"Description":"",
				"MasterInstanceId":"",
				"AssociatedInstances":{
					"associatedInstance":[]
				},
				"AssociatedEipAddresses":{
					"associatedEipAddresse":[]
				},
				"RegionId":"cn-hangzhou",
				"CreateTime":"2018-07-03T14:25:26Z",
				"IpAddress":"192.168.35.27",
				"HaVipId":"havip-bp149uyvut73dplduoq8s",
				"VSwitchId":"vsw-bp1pkt1fba8e824ezs80a",
				"VpcId":"vpc-bp1kcm36tevkpms97o2pm"
			}
		]
	},
	"RequestId":"33E480C5-B46F-4CA5-B6FD-D77C746E86AB"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidFilterKey.ValueNotSupported|Specified filter key is not supported: Filter.X.key|该过滤器的Key不支持：Filter.X.key|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

