# DescribeEipMonitorData {#doc_api_Vpc_DescribeEipMonitorData .reference}

调用DescribeEipMonitorData查看EIP的监控信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeEipMonitorData)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeEipMonitorData|要执行的操作。 取值：

 **DescribeEipMonitorData**

 |
|AllocationId|String|是|eip-2zeerraiwb7uj6ixxxxxxxx|EIP的实例ID。

 |
|EndTime|String|是|2017-01-05T01:05:10Z|获取数据的结束时间。 使用UTC时间。按照ISO8601标准，格式为YYYY-MM-DDThh:mm:ssZ。 例如，北京时间2013年1月10日20点0分0秒，表示为2013-01-10T12:00:00Z。

 如果秒不是00，则自动取下一分钟为起始时间点。

 |
|RegionId|String|是|cn-hangzhou|EIP所属地域ID。

 |
|StartTime|String|是|2017-01-05T02:05:05Z|获取数据的起始时间。 使用UTC时间。按照ISO8601标准，格式为YYYY-MM-DDThh:mm:ssZ。 例如，北京时间2013年1月10日20点0分0秒，表示为2013-01-10T12:00:00Z。

 如果秒不是00，则自动取下一分钟为起始时间点。

 |
|Period|Integer|否|60|每条监控数据的时间长度，单位为秒，默认值为60，取值： 60, 600, 3600

 -   （EndTime–StartTime）/ Peroid必须大于200，即最多返回200条监控数据。
-   如果EndTime–StartTime小于200则只返回起始时间点的监控数据。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|EipMonitorDatas| | |EIP监控数据的详细信息。

 |
|└EipBandwidth|Integer|10|带宽值，该值等于EipFlow/60，单位为Bps。

 |
|└EipFlow|Integer|675|流入和流出的带宽总和。

 |
|└EipPackets|Integer|3434|包数量。

 |
|└EipRX|Integer|122|流入的带宽。单位为Byte。

 |
|└EipTX|Integer|343|流出的带宽。单位为Byte。

 |
|└TimeStamp|String|2010-01-21T09:50:23Z|查询监控信息的时间戳。ISO8601格式，如2018-12-20T03:14:00Z。

 |
|RequestId|String|C8B26B44-0189-443E-9816-D951F59623A9|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeEipMonitorData
&AllocationId=eip-2zeerraiwb7uj6ixxxxxxxx
&EndTime=2017-01-05T01:05:10Z
&StartTime=2017-01-05T02:05:05Z
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeEipMonitorDataResponse>
  <RequestId>C8B26B44-0189-443E-9816-D951F59623A9</RequestId>
  <EipMonitorDatas>
    <EipMonitorData>
      <EipRX>122</EipRX>
      <EipTX>343</EipTX>
      <EipFlow>675</EipFlow>
      <EipPackets>3434</EipPackets>
      <EipBandwidth>10</EipBandwidth>
      <TimeStamp>2010-01-21T09:50:23Z</TimeStamp>
    </EipMonitorData>
  </EipMonitorDatas>
</DescribeEipMonitorDataResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"C8B26B44-0189-443E-9816-D951F59623A9",
	"EipMonitorDatas":{
		"EipMonitorData":[
			{
				"TimeStamp":"2010-01-21T09:50:23Z",
				"EipFlow":"675",
				"EipTX":"343",
				"EipPackets":"3434",
				"IntranetBandwidth":10,
				"IntranetFlow":675,
				"EipRX":"122",
				"EipBandwidth":"10"
			}
		]
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidInstanceId.NotFound|The InstanceId provided does not exist in our records.|该 ECS 实例不存在（实例不在该 VPC 下）。|
|400|InvalidStartTime.Malformed|The specified parameter "StartTime" is not valid.|开始时间不合法。|
|400|InvalidEndTime.Malformed|The specified parameter "EndTime" is not valid.|该结束时间不合法。|
|400|InvalidPeriod.ValueNotSupported|The specified parameter "Period" is not valid.|参数Period的值不合法。|
|400|InvalidStartTime.TooEarly|The specified parameter "StartTime" is too early.|开始时间不合法。|
|400|InvalidAllocationId.NotFound|Specified allocation id is not found.|指定的公网 IP 不存在，请您检查填写的公网 IP 是否正确。|
|400|OperationDenied.TooManyDataQueried|Specified operation is denied as too many data to return.|一次查询返回的数据量过多。|
|404|Forbidden.RegionNotFound|Specified region is not found during access authentication.|指定 Region 不存在，请您检查该 Region 是否正确。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

