# DescribeCommonBandwidthPackages {#doc_api_951876 .reference}

调用DescribeCommonBandwidthPackages接口查询指定地域中共享带宽实例列表。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeCommonBandwidthPackages)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeCommonBandwidthPackages|要执行的操作。 取值：

 **DescribeCommonBandwidthPackages**。

 |
|RegionId|String|是|cn-hangzhou|共享带宽所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|BandwidthPackageId|String|否|cbwp-2ze2ic1xd2qeqk145pn4u|共享带宽实例的ID。

 |
|IncludeReservationData|Boolean|否|false|是否包含未生效的订购数据，默认是**false**。

 |
|Name|String|否|test123|共享带宽实例名称。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为1。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。

 |
|ResourceGroupId|String|否|rg-acfmxazb4ph6aiy|资源组ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|CommonBandwidthPackages| | |共享带宽的详细信息。

 |
|└BandwidthPackageId|String|cbwp-bp1t3sm1ffzmshdkixabo|共享带宽的ID。

 |
|└Name|String|abc|共享带宽的名称。

 |
|└Description|String|none|共享带宽的描述信息。

 |
|└Bandwidth|String|20|共享带宽的带宽峰值。

 |
|└InternetChargeType|String|PayByBandwidth|共享带宽的计费方式。

 -   **PayBy95**：按增强型95计费。
-   **PayByBandwidth**：按带宽计费。

 |
|└Ratio|Integer|100|比率。

 |
|└RegionId|String|cn-hangzhou|共享带宽实例的地域ID。

 |
|└CreationTime|String|2017-06-28T06:39:20Z|共享带宽实例创建的时间。

 |
|└InstanceChargeType|String|PostPaid|共享带宽实例的计费类型。

 |
|└BusinessStatus|String|Available|共享带宽实例的状态。

 |
|└PublicIpAddresses| | |共享带宽实例中的公网IP地址。

 |
|└IpAddress|String|116.62.129.250|公网ip地址

 |
|└AllocationId|String|eip-bp13e9i2qst4g6jzi35tc|公网ip的instanceId

 |
|└ExpiredTime|String|2019-01-15T03:08:37Z|共享带宽实例的过期时间。

 |
|└HasReservationData|String|false|是否有待生效的订单。

 -   false：没有待生效的订单。
-   true：有待生效的订单。

 |
|└ISP|String|BGP|服务提供商，大部分是BGP。

 |
|└ReservationActiveTime|String|2018-08-30T16:00Z|续费生效时间。

 |
|└ReservationBandwidth|String|10|变配之后的带宽值。

 |
|└ReservationInternetChargeType|String|PayByBandwidth|变配之后的计费方式。

 |
|└ReservationOrderType|String|RENEWCHANGE|续费变配方式。

 -   RENEWCHANGE：续费变配。
-   TEMP\_UPGRADE：短时升配。
-   UPGRADE ：升级。

 |
|└ResourceGroupId|String|rg-acfmxazb4ph6aiy|资源组ID。

 |
|└Status|String|Available|共享带宽实例的状态。

 |
|TotalCount|Integer|1|列表条条目数。

 |
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|10|每页包含多少条目。

 |
|RequestId|String|20E6FD1C-7321-4DAD-BDFD-EC8769E4AA33|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeCommonBandwidthPackages
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeCommonBandwidthPackagesResponse>
  <PageNumber>1</PageNumber>
  <TotalCount>1</TotalCount>
  <PageSize>10</PageSize>
  <RequestId>20E6FD1C-7321-4DAD-BDFD-EC8769E4AA33</RequestId>
  <CommonBandwidthPackages>
    <CommonBandwidthPackage>
      <Description/>
      <BandwidthPackageId>cbwp-bp1t3sm1ffzmshdkixabo</BandwidthPackageId>
      <ZoneId>cn-hangzhou-d</ZoneId>
      <InternetChargeType>PayByBandwidth</InternetChargeType>
      <Name>abc</Name>
      <CreationTime>2017-06-28T06:39:20Z</CreationTime>
      <Status>Available</Status>
      <BandwidthPackageId>cbwp-bp1vevu8h3ieh5xkcdhdy</BandwidthPackageId>
      <BusinessStatus>Normal</BusinessStatus>
      <RegionId>cn-hangzhou</RegionId>
      <Ratio>100</Ratio>
      <InstanceChargeType>PostPaid</InstanceChargeType>
      <PublicIpAddresses>
        <PublicIpAddresse>
          <IpAddress>116.62.129.250</IpAddress>
          <AllocationId>eip-bp13e9i2qst4g6jzi35tc</AllocationId>
        </PublicIpAddresse>
      </PublicIpAddresses>
      <Bandwidth>20</Bandwidth>
    </CommonBandwidthPackage>
  </CommonBandwidthPackages>
</DescribeCommonBandwidthPackagesResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"DescribeCommonBandwidthPackagesResponse":{
		"PageNumber":"1",
		"TotalCount":"1",
		"PageSize":"10",
		"RequestId":"20E6FD1C-7321-4DAD-BDFD-EC8769E4AA33",
		"CommonBandwidthPackages":{
			"CommonBandwidthPackage":{
				"CreationTime":"2017-06-28T06:39:20Z",
				"Name":"abc",
				"Status":"Available",
				"BandwidthPackageId":"cbwp-bp1vevu8h3ieh5xkcdhdy",
				"BusinessStatus":"Normal",
				"Ratio":"100",
				"RegionId":"cn-hangzhou",
				"ZoneId":"cn-hangzhou-d",
				"InstanceChargeType":"PostPaid",
				"InternetChargeType":"PayByBandwidth",
				"PublicIpAddresses":{
					"PublicIpAddresse":{
						"IpAddress":"116.62.129.250",
						"AllocationId":"eip-bp13e9i2qst4g6jzi35tc"
					}
				},
				"Bandwidth":"20"
			}
		}
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

