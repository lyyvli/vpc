# DescribeCommonBandwidthPackages {#doc_api_Vpc_DescribeCommonBandwidthPackages .reference}

Queries Internet Shared Bandwidth instances in a region.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=DescribeCommonBandwidthPackages&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeCommonBandwidthPackages| The name of this action. Value:

 **DescribeCommonBandwidthPackages**

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the Internet Shared Bandwidth instance belongs.

 To query the region ID, call [DescribeRegions](~~36063~~).

 |
|BandwidthPackageId|String|No|cbwp-2ze2ic1xd2qeqk145pn4u| Optional. The ID of the Internet Shared Bandwidth instance.

 |
|IncludeReservationData|Boolean|No|false| Optional. Indicates whether to return orders that have not taken effect. Default value: **false**

 |
|Name|String|No|test123| Optional. The name of the Internet Shared Bandwidth instance.

 |
|PageNumber|Integer|No|1| Optional. The page number. Default value: 1

 |
|PageSize|Integer|No|10| Optional. The number of entries per page in the case of a paged query result. Maximum value: 50. Default value: 10.

 |
|ResourceGroupId|String|No|rg-acfmxazb4ph6aiy| Optional. The ID of the resource group.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|CommonBandwidthPackages| | | The details of the Internet Shared Bandwidth instance.

 |
|BandwidthPackageId|String|cbwp-bp1t3sm1ffzmshdkixabo| The ID of the Internet Shared Bandwidth instance.

 |
|Name|String|abc| The name of the Internet Shared Bandwidth instance.

 |
|Description|String|none| The description of the Internet Shared Bandwidth instance.

 |
|Bandwidth|String|20| The peak bandwidth of the Internet Shared Bandwidth instance.

 |
|InternetChargeType|String|PayByBandwidth| The billing method of the Internet Shared Bandwidth instance.

 -   **PayBy95**: billed by using the 95th percentile method
-   **PayByBandwidth**: billed according to the bandwidth consumed

 |
|Ratio|Integer|100| The minimum consumption ratio of the Internet Shared Bandwidth instance.

 |
|RegionId|String|cn-hangzhou| The ID of the region to which the Internet Shared Bandwidth instance belongs.

 |
|CreationTime|String|2017-06-28T06:39:20Z| The time when the Internet Shared Bandwidth instance was created.

 |
|InstanceChargeType|String|PostPaid| The billing method of the Internet Shared Bandwidth instance.

 |
|BusinessStatus|String|Available| The status of the Internet Shared Bandwidth instance.

 |
|PublicIpAddresses| | | The details of the public IP addresses added to the Internet Shared Bandwidth instance.

 |
|IpAddress|String|116.62.129.250| The public IP address.

 |
|AllocationId|String|eip-bp13e9i2qst4g6jzi35tc| The ID of the instance associated with the public IP address.

 |
|ExpiredTime|String|2019-01-15T03:08:37Z| The time when the Internet Shared Bandwidth instance expires.

 |
|HasReservationData|String|false| Indicates whether orders that have not taken effect exist.

 -   false: No orders that have not taken effect exist.
-   true: Orders that have not taken effect exist.

 |
|ISP|String|BGP| The service provider. Generally, BGP lines are used.

 |
|ReservationActiveTime|String|2018-08-30T16:00Z| The time when the renewal takes effect.

 |
|ReservationBandwidth|String|10| The bandwidth value after the configuration change.

 |
|ReservationInternetChargeType|String|PayByBandwidth| The billing method after the configuration change.

 |
|ReservationOrderType|String|RENEWCHANGE| The type of the configuration change.

 -   RENEWCHANGE: Indicates a renewal.
-   TEMP\_UPGRADE: Indicates a temporary upgrade.
-   UPGRADE: Indicates a configuration upgrade.

 |
|ResourceGroupId|String|rg-acfmxazb4ph6aiy| The ID of the resource group.

 |
|Status|String|Available| The status of the Internet Shared Bandwidth instance.

 |
|TotalCount|Integer|1| The total number of entries.

 |
|PageNumber|Integer|1| The current page number.

 |
|PageSize|Integer|10| The number of entries per page.

 |
|RequestId|String|20E6FD1C-7321-4DAD-BDFD-EC8769E4AA33| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeCommonBandwidthPackages
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<DescribeCommonBandwidthPackagesResponse>
      <PageNumber>1</PageNumber>
      <TotalCount>1</TotalCount>
      <PageSize>10</PageSize>
      <RequestId>20E6FD1C-7321-4DAD-BDFD-EC8769E4AA33</RequestId>
      <CommonBandwidthPackages>
            <CommonBandwidthPackage>
                  <Description></Description>
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

`JSON` format

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

## Errors {#section_1ri_wnc_nzv .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|

