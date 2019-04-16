# DescribeVSwitches {#doc_api_907500 .reference}

使用DescribeVSwitches查询已创建的交换机。

查询用户的 VSwitch 列表。此接口支持分页查询，每页的数量默认为 10 条。

该接口只会校验参数的合法性，不会校验参数之间的依赖关系，返回结果是所有条件的交集。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Vpc&api=DescribeVSwitches)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeVSwitches|要执行的操作。 取值： **DescribeVSwitches**

 |
|RegionId|String|是|cn-hangzhou|交换机所属VPC所在的地域。 您可以通过调用 DescribeRegions接口获取地域ID。

 |
|IsDefault|Boolean|否|true|是否查询指定地域下的默认交换机，取值：

 -   true（默认值）：查询指定地域下的所有交换机。
-   false：不查询默认交换机。

 |
|OwnerAccount|String|否| |用户账号。

 |
|PageNumber|Integer|否|10|列表的页码，默认值为1。

 |
|PageSize|Integer|否|1|分页查询时每页的行数，最大值为50，默认值为10。

 |
|ResourceGroupId|String|否|1234567|资源组ID。

 |
|RouteTableId|String|否|vtb-bp145q7glnuzdvzu21pom|路由表的ID。

 |
|VSwitchId|String|否|vsw-23dsf3xxxxxxxxx|交换机的ID。

 |
|VSwitchName|String|否|VSwitch-1|交换机名字

 |
|VpcId|String|否|vpc-25eq58plxxxxxxxxxx|VPC的ID。

 |
|ZoneId|String|否|cn-hangzhou-d|交换机所属区的ID。 您可以通过调用 DescribeZones接口获取地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|VSwitches| | |交换机的详细信息。

 |
|└AvailableIpAddressCount|Long|1|交换机中可用的IP地址数量。

 |
|└CidrBlock|String|172.16.0.0/24|交换机的网段。

 |
|└CreationTime|String|2018-01-18T12:43:57Z|交换机的创建时间。

 |
|└Description|String|This is my vswitch.|交换机的描述信息。

 |
|└Ipv6CidrBlock|String|2408:4004:0:2900::/64|交换机的IPv6网段。

 |
|└IsDefault|Boolean|true|是否是该可用区的默认交换机。

 |
|└ResourceGroupId|String|123456|交换机所属的资源组ID。

 |
|└RouteTable| | |路由表信息。

 |
|└RouteTableId|String|vrt-123456|交换机关联的路由表ID。

 |
|└RouteTableType|String|System|路由表类型：

 -   System：系统路由表
-   Custom：自定义路由表

 |
|└Status|String|Available|交换机的状态，取值：

 -   Pending：配置中
-   Available：可用

 |
|└VSwitchId|String|vsw-xxxxxxxxxxxxxxxx|交换机的ID。

 |
|└VSwitchName|String|VSwitch-1|交换机的名称。

 |
|└VpcId|String|vpc-234asxxxxxxxxxxxxx|交换机所属VPC的ID。

 |
|└ZoneId|String|cn-hangzhou-d|交换机所在的可用区。

 |
|TotalCount|Integer|10|列表条条目数。

 |
|PageNumber|Integer|10|当前页码。

 |
|PageSize|Integer|10|每页包含多少条目。

 |
|RequestId|String|9A572171-4E27-40D1-BD36-D26XXXXXXXXX|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeVSwitchesResponse>
  <RequestId>9A572171-4E27-40D1-BD36-D26C9E71E29E</RequestId>
  <VSwitches>
    <VSwitch>
      <VSwitchId> vsw-25b7pv15t </VSwitchId>
      <Status>Available</Status>
      <CidrBlock>172.16.1.0/24</CidrBlock>
      <ZoneId>cn-beijing-a</ZoneId>
      <AvailableIpAddressCount>246</AvailableIpAddressCount>
      <VpcId>vpc-257gq642n</VpcId>
      <Description/>
      <VSwitchName/>
      <CreationTime> 2014-10-29T15:21:02Z </CreationTime>
    </VSwitch>
  </VSwitches>
</DescribeVSwitchesResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"VSwitches":{
		"VSwitch":[
			{
				"CreationTime":"2014-10-29T15:21:02Z",
				"Status":"Available",
				"CidrBlock":"172.16.1.0/24",
				"Description":"",
				"AvailableIpAddressCount":246,
				"VSwitchName":"",
				"ZoneId":"cn-beijing-a",
				"VSwitchId":"vsw-25b7pv15t",
				"VpcId":"vpc-257gq642n"
			}
		]
	},
	"TotalCount":1,
	"PageSize":10,
	"RequestId":"9A572171-4E27-40D1-BD36-D26C9E71E29E"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidVSwitchId.NotFound|VSwitch not exist.|该交换机不存在，请您检查输入的交换机是否正确。|
|400|Forbidden.VpcNotFound|Specified VPC can not found.|指定的 VPC 不存在，请您检查 VPC 是否正确。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

