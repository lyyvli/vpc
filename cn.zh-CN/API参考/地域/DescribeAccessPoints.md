# DescribeAccessPoints {#doc_api_Vpc_DescribeAccessPoints .reference}

调用DescribeAccessPoints接口查询指定地域中的物理专线接入点。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeAccessPoints&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeAccessPoints|要执行的操作。

 取值： **DescribeAccessPoints** 。

 |
|RegionId|String|是|cn-hangzhou|接入点所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为**1**。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为**50**，默认值为**10**。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|AccessPointSet| | |接入点信息。

 |
|AccessPointId|String|ap-cn-beijing-ft-A|接入点ID。

 |
|AttachedRegionNo|String|cn-beijing|接入点地域。

 |
|Description|String|ap1|接入点描述。

 |
|HostOperator|String|皓宽|接入点运营商。

 |
|Location|String|aplocation|接入点位置。

 |
|Name|String|北京-丰台-A|接入点名称。

 |
|Status|String|recommended|专线接入点状态。

 |
|Type|String|VPC|专线接入的网络类型。

 |
|TotalCount|Integer|5|列表条条目数。

 |
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|10|每页包含多少条目。

 |
|RequestId|String|3E85D803-C7CF-4BCD-9CFE-6DBA1DFFA027|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://vpc.aliyuncs.com]/?Action=DescribeAccessPoints
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeAccessPointsResponse>	
	  <AccessPointSet>
		    <AccessPointType>
			      <Name>北京-丰台-A</Name>
			      <Status>recommended</Status>
			      <Description>cn-beijing-ft-cxp32</Description>
			      <Type>VPC</Type>
			      <Location></Location>
			      <HostOperator>xxx</HostOperator>
			      <AttachedRegionNo>cn-beijing</AttachedRegionNo>
			      <AccessPointId>ap-cn-beijing-ft-A</AccessPointId>
		    </AccessPointType>
		    <AccessPointType>
			      <Name>北京-亦庄-A</Name>
			      <Status>recommended</Status>
			      <Description>cn-beijing-yz-ne203</Description>
			      <Type>VPC</Type>
			      <Location></Location>
			      <HostOperator>xxx</HostOperator>
			      <AttachedRegionNo>cn-beijing</AttachedRegionNo>
			      <AccessPointId>ap-cn-beijing-yz-A</AccessPointId>
		    </AccessPointType>
		    <AccessPointType>
			      <Name>北京-大兴-B</Name>
			      <Status>recommended</Status>
			      <Description>cn-beijing-dx-nu16</Description>
			      <Type>VPC</Type>
			      <Location></Location>
			      <HostOperator>中国联通</HostOperator>
			      <AttachedRegionNo>cn-beijing</AttachedRegionNo>
			      <AccessPointId>ap-cn-beijing-dx-B</AccessPointId>
		    </AccessPointType>
		    <AccessPointType>
			      <Name>北京-昌平-A</Name>
			      <Status>recommended</Status>
			      <Description>ap-cn-beijing-cp-CM12</Description>
			      <Type>VPC</Type>
			      <Location></Location>
			      <HostOperator>中国电信</HostOperator>
			      <AttachedRegionNo>cn-beijing</AttachedRegionNo>
			      <AccessPointId>ap-cn-beijing-cp-A</AccessPointId>
		    </AccessPointType>
		    <AccessPointType>
			      <Name>北京-大兴-A</Name>
			      <Status>recommended</Status>
			      <Description>cn-beijing-dx-nu17-a</Description>
			      <Type>VPC</Type>
			      <Location></Location>
			      <HostOperator>GDS</HostOperator>
			      <AttachedRegionNo>cn-beijing</AttachedRegionNo>
			      <AccessPointId>ap-cn-beijing-dx-A</AccessPointId>
		    </AccessPointType>
	  </AccessPointSet>
	  <PageNumber>1</PageNumber>
	  <TotalCount>5</TotalCount>
	  <PageSize>10</PageSize>
	  <RequestId>3E85D803-C7CF-4BCD-9CFE-6DBA1DFFA027</RequestId>
</DescribeAccessPointsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"AccessPointSet":{
		"AccessPointType":[
			{
				"Name":"北京-丰台-A",
				"Status":"recommended",
				"Description":"cn-beijing-ft-cxp32",
				"Type":"VPC",
				"Location":"",
				"HostOperator":"皓宽",
				"AttachedRegionNo":"cn-beijing",
				"AccessPointId":"ap-cn-beijing-ft-A"
			},
			{
				"Name":"北京-亦庄-A",
				"Status":"recommended",
				"Description":"cn-beijing-yz-ne203",
				"Type":"VPC",
				"Location":"",
				"HostOperator":"世纪互联",
				"AttachedRegionNo":"cn-beijing",
				"AccessPointId":"ap-cn-beijing-yz-A"
			},
			{
				"Name":"北京-大兴-B",
				"Status":"recommended",
				"Description":"cn-beijing-dx-nu16",
				"Type":"VPC",
				"Location":"",
				"HostOperator":"中国联通",
				"AttachedRegionNo":"cn-beijing",
				"AccessPointId":"ap-cn-beijing-dx-B"
			},
			{
				"Name":"北京-昌平-A",
				"Status":"recommended",
				"Description":"ap-cn-beijing-cp-CM12",
				"Type":"VPC",
				"Location":"",
				"HostOperator":"中国电信",
				"AttachedRegionNo":"cn-beijing",
				"AccessPointId":"ap-cn-beijing-cp-A"
			},
			{
				"Name":"北京-大兴-A",
				"Status":"recommended",
				"Description":"cn-beijing-dx-nu17-a",
				"Type":"VPC",
				"Location":"",
				"HostOperator":"GDS",
				"AttachedRegionNo":"cn-beijing",
				"AccessPointId":"ap-cn-beijing-dx-A"
			}
		]
	},
	"TotalCount":5,
	"PageSize":10,
	"RequestId":"3E85D803-C7CF-4BCD-9CFE-6DBA1DFFA027"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotSupport|The RegionId provided does not support in our records.|输入的地域ID不正确。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

