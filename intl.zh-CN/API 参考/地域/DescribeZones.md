# DescribeZones {#reference_i4w_xmt_ndb .reference}

查询指定地域中可用区的列表。

## 请求参数 {#section_cch_pjg_mdb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是| 要执行的操作。 取值：

 DescribeZones

 |
|RegionId|String|是| 地域的ID。

 您可以通过调用 DescribeRegions接口获取地域ID。

 |

## 返回参数 {#section_ugs_f1g_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|Zones|List|可用区的集合。|

## 示例 {#section_ix5_h1g_cz .section}

**请求示例**

``` {#createVPCpub}
https://vpc.aliyuncs.com/?Action=DescribeZones
&RegionId=cn-hangzhou
&公共请求参数
```

**返回示例**

XML格式

```
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

JSON格式

```
{
    "RequestId": "6FEA0CF3-D3B9-43E5-A304-D217037876A8", 
    "Zones": {
        "Zone": [
            {
                "ZoneId": "cn-hangzhou-b", 
                "LocalName": "华东 1 可用区 B"
            }, 
            {
                "ZoneId": "cn-hangzhou-d", 
                "LocalName": "华东 1 可用区 D"
            }, 
            {
                "ZoneId": "cn-hangzhou-e", 
                "LocalName": "华东 1 可用区 E"
            }, 
            {
                "ZoneId": "cn-hangzhou-f", 
                "LocalName": "华东 1 可用区 F"
            }, 
            {
                "ZoneId": "cn-hangzhou-g", 
                "LocalName": "华东 1 可用区 G"
            }, 
            {
                "ZoneId": "cn-hangzhou-h", 
                "LocalName": "华东 1 可用区 H"
            }
        ]
    }
}
```

