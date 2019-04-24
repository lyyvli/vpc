# DescribeBandwidthPackages {#doc_api_Vpc_DescribeBandwidthPackages .reference}

使用DescribeBandwidthPackages接口查询指定地域的NAT带宽包。

本接口仅支持在2018年1月26日之前账号下存在NAT带宽包的用户调用。2018年1月26日之前账号下不存在NAT带宽包的用户，请绑定EIP。

详情参见[AssociateEipAddress](~~36017~~)。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeBandwidthPackages)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeBandwidthPackages|要执行的操作。 取值：**DescribeBandwidthPackages**。

 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|BandwidthPackageId|String|否|bwp-bp1xea10o8qxwxxxxxxxx|NAT网关带宽包的ID。

 |
|NatGatewayId|String|否|ngw-bp1uewa15k4iyxxxxxxxx|NAT网关的ID。

 |
|PageNumber|Integer|否|10|列表的页码，默认值为1。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|BandwidthPackages| | |NAT带宽包的详细信息，详情参见表 1。

 |
|└Bandwidth|String|5|带宽值，取值范围：5-5000，单位为Mbps。

 |
|└BandwidthPackageId|String|bwp-xxoo123xxxxxxxx|NAT带宽包的ID。

 |
|└BusinessStatus|String|Normal|Normal（正常）、FinancialLocked（欠费锁定状态）、SecurityLocked（安全风控锁定状态）。

 |
|└CreationTime|String|2017-06-08T12:20:55|创建时间。

 按照ISO8601标准表示，并需要使用UTC时间。

 格式为：YYYY-MM-DDThh:mmZ

 |
|└Description|String|test123|自定义描述2-256个字符，实例描述会显示在控制台。不填则为空，默认为空。不能以 `http://` 和 `https://`开头。

 |
|└ISP|String|BGP|目前只支持一种：BGP。

 |
|└InstanceChargeType|String|PostPaid|实例的付费方式。目前仅支持按量付费.。

 取值：PostPaid，后付费，即按量付费

 |
|└InternetChargeType|String|PayByBandwidth|网络计费类型，PayByBandwidth | PayByTraffic两个值中的一个。目前仅支持按带宽计费。

 -   PayByTraffic：按流量计费

 |
|└IpCount|String|1|NAT带宽包中的公网IP数量

 取值范围：1-50。

 |
|└Name|String|xxxxxxx|NAT带宽包的名称。

 |
|└NatGatewayId|String|ngw-xxoo123xxxxxxxx|NAT网关ID。

 |
|└PublicIpAddresses| | |带宽包中的 IP。

 |
|└AllocationId|String|eip-2zeerraiwb7ujxxxxxxxxx|分配ID

 |
|└ApAccessEnabled|Boolean|true|ApAccessEnabled

 |
|└IpAddress|String|116.xx.xx.28|IP 地址

 |
|└UsingStatus|String|Available|使用状态

 |
|└RegionId|String|cn-hangzhou|所在地域。

 |
|└Status|String|Available|带宽包状态。

 |
|└ZoneId|String|cn-shanghai-a|NAT带宽包所在的可用区。

 |
|TotalCount|Integer|10|列表条条目数。

 |
|PageNumber|Integer|10|当前页码。

 |
|PageSize|Integer|10|每页包含多少条目。

 |
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF"|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeBandwidthPackages
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeBandwidthPackagesResponse>
  <PageNumber>1</PageNumber>
  <TotalCount>1</TotalCount>
  <BandwidthPackages>
    <BandwidthPackage>
      <Description/>
      <IpCount>2</IpCount>
      <ISP>BGP</ISP>
      <ZoneId>cn-hangzhou-b</ZoneId>
      <InternetChargeType>PayByTraffic</InternetChargeType>
      <NatGatewayId>ngw-bp1uewa15k4iyxxxxxxxx</NatGatewayId>
      <Name/>
      <CreationTime>2018-03-06T07:33:51Z</CreationTime>
      <Status>Available</Status>
      <BandwidthPackageId>bwp-bp1xea10o8qxwxxxxxxxx</BandwidthPackageId>
      <BusinessStatus>Normal</BusinessStatus>
      <RegionId>cn-hangzhou</RegionId>
      <InstanceChargeType>PostPaid</InstanceChargeType>
      <PublicIpAddresses>
        <PublicIpAddresse>
          <IpAddress>118.31.xx.xx</IpAddress>
          <AllocationId>nateip-bp1jb1uijvm9oxxxxxxxx</AllocationId>
          <UsingStatus>Idle</UsingStatus>
        </PublicIpAddresse>
        <PublicIpAddresse>
          <IpAddress>118.31.xx.xx</IpAddress>
          <AllocationId>nateip-bp1dt4hpe8847xxxxxxxx</AllocationId>
          <UsingStatus>UsedBySnatTable</UsingStatus>
        </PublicIpAddresse>
      </PublicIpAddresses>
      <Bandwidth>5</Bandwidth>
    </BandwidthPackage>
  </BandwidthPackages>
  <PageSize>10</PageSize>
</DescribeBandwidthPackagesResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":1,
	"BandwidthPackages":{
		"BandwidthPackage":[
			{
				"Description":"",
				"IpCount":"2",
				"ISP":"BGP",
				"ZoneId":"cn-hangzhou-b",
				"InternetChargeType":"PayByTraffic",
				"NatGatewayId":"ngw-bp1uewa15k4iyxxxxxxxx",
				"Name":"",
				"CreationTime":"2018-03-06T07:33:51Z",
				"Status":"Available",
				"BandwidthPackageId":"bwp-bp1xea10o8qxwxxxxxxxx",
				"BusinessStatus":"Normal",
				"RegionId":"cn-hangzhou",
				"InstanceChargeType":"PostPaid",
				"PublicIpAddresses":{
					"PublicIpAddresse":[
						{
							"IpAddress":"118.31.xx.xx",
							"AllocationId":"nateip-bp1jb1uijvm9oxxxxxxxx",
							"UsingStatus":"Idle"
						},
						{
							"IpAddress":"118.31.xx.xx",
							"AllocationId":"nateip-bp1dt4hpe8847xxxxxxxx",
							"UsingStatus":"UsedBySnatTable"
						}
					]
				},
				"Bandwidth":"5"
			}
		]
	},
	"PageSize":10,
	"RequestId":"8909013D-4A64-41A6-93E6-E3FD08A3EAFE"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

