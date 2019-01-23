# DescribeZones {#doc_api_918658 .reference}

调用DescribeZones查询指定地域中可用区的列表。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Vpc&api=DescribeZones)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeZones|要执行的操作。 取值：

 **DescribeZones**

 |
|RegionId|String|是|cn-hangzhou|地域ID。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Zones| | |可用区的集合。

 |
|└LocalName|String|华东 1 可用区 B|可用区名称。

 |
|└ZoneId|String|cn-hangzhou-b|可用区ID。

 |
|RequestId|String|6FEA0CF3-D3B9-43E5-A304-D217037876A8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<?xml version="1.0" encoding="UTF-8" ?>
<DescribeZonesResponse>
<RequestId>6FEA0CF3-D3B9-43E5-A304-D217037876A8</RequestId>
	<Zones>
		<Zone>
			<ZoneId>cn-hangzhou-b</ZoneId>
			<LocalName>华东 1 可用区 B</LocalName>
		</Zone>
		<Zone>
			<ZoneId>cn-hangzhou-d</ZoneId>
			<LocalName>华东 1 可用区 D</LocalName>
		</Zone>
		<Zone>
			<ZoneId>cn-hangzhou-e</ZoneId>
			<LocalName>华东 1 可用区 E</LocalName>
		</Zone>
		<Zone>
			<ZoneId>cn-hangzhou-f</ZoneId>
			<LocalName>华东 1 可用区 F</LocalName>
		</Zone>
		<Zone>
			<ZoneId>cn-hangzhou-g</ZoneId>
			<LocalName>华东 1 可用区 G</LocalName>
		</Zone>
		<Zone>
			<ZoneId>cn-hangzhou-h</ZoneId>
			<LocalName>华东 1 可用区 H</LocalName>
		</Zone>
	</Zones>
<DescribeZonesResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"6FEA0CF3-D3B9-43E5-A304-D217037876A8",
	"Zones":{
		"Zone":[
			{
				"ZoneId":"cn-hangzhou-b",
				"LocalName":"华东 1 可用区 B"
			},
			{
				"ZoneId":"cn-hangzhou-d",
				"LocalName":"华东 1 可用区 D"
			},
			{
				"ZoneId":"cn-hangzhou-e",
				"LocalName":"华东 1 可用区 E"
			},
			{
				"ZoneId":"cn-hangzhou-f",
				"LocalName":"华东 1 可用区 F"
			},
			{
				"ZoneId":"cn-hangzhou-g",
				"LocalName":"华东 1 可用区 G"
			},
			{
				"ZoneId":"cn-hangzhou-h",
				"LocalName":"华东 1 可用区 H"
			}
		]
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

