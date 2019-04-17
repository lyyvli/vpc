# DescribeGlobalAccelerationInstances {#reference_i4w_xmt_ndb .reference}

Queries one or more Global Acceleration instances.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description |
|:--------|:---|:--------|:------------|:-----------|
|Action|String|Yes|DescribeGlobalAccelerationInstances| The name of this action. Value: 

 DescribeGlobalAccelerationInstances

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region where the Global Acceleration instance is located.

 To query the region ID, call DescribeRegions.

 |
|BandwidthType|String|No|Exclusive| The type of the Global Acceleration instance. Valid values:

-   Sharing: Queries only shared-bandwidth instances.
-   Exclusive \(Default\): Queries only dedicated-bandwidth instances.

 |
|GlobalAccelerationInstanceId|String|No|ga-234sljmxazb4| The ID of the Global Acceleration instance.

 |
|IncludeReservationData|Boolean|No|false| Indicates whether one or more specifications in the purchase order that have not taken effect are included. Default value: **false**.

 |
|IpAddress|String|No|12.34.56.78| The public IP address of the Global Acceleration instance.

 |
|Name|String|No|GA-1| The name of the Global Acceleration instance.

 |
|PageNumber|Integer|No|10| The number of pages to return. Default value: 1.

 |
|PageSize |Integer|No|10| The number of rows per page. Maximum value: 50. Default value: 10.

 |
|ServerId|String|No|i-sxjbl9xgc| The ID of the accelerated backend server.

 |
|ServiceLocation|String|No|china-mainland| The service area of the Global Acceleration instance. Valid values:

-   china-mainland: Mainland China

-   north-america: North America

-   asia-pacific: Asia Pacific

-   europe: Europe


 |
|Status|String|No|Available| The status of the Global Acceleration instance. Valid values:

-   Available: available

-   Inuse: allocated

-   Associating: being attached

-   Unassociating: being detached


 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|GlobalAccelerationInstances|N/A|N/A| A list of Global Acceleration instances.

 |
|└AccelerationLocation|String|china-mainland| The accelerated area of the Global Acceleration instance.

 |
|└BackendServers|N/A|N/A| The list of backend servers associated with the Global Acceleration instance.

 |
|└RegionId|String|cn-Beijing| The ID of the region where the backend server is located.

 |
|└ServerId|String|i-2zeg83zvn5d4ed4y2rxx| The ID of the backend server.

 |
|└ServerIpAddress|String|172.17.109.xxx| The IP address of the backend server.

 |
|└ServerType|String|EcsInstance| The type of the backend server.

 |
|└Bandwidth|String|10| The peak bandwidth of the Global Acceleration instance.

 |
|└BandwidthType|String|Exclusive| The bandwidth type of the Global Acceleration instance.

 |
|└ChargeType|String|PrePaid| The billing method of the Global Acceleration instance:

 -   **PostPaid**: Pay-As-You-Go

 |
|└CreationTime|String|2018-07-05T03:39:31Z| The time at which the Global Acceleration instance was created. UTC time is used.

 |
|└Description|String|apiDescription| The description of the Global Acceleration instance.

 |
|└ExpiredTime|String|2018-08-05T16:00Z| The time at which the Global Acceleration instance is to expire.

 |
|└GlobalAccelerationInstanceId|String|ga-bp1x99kj7kl1ziw5xuwb5| The ID of the Global Acceleration instance.

 |
|└InternetChargeType|String|PayByBandwidth| The billing method of the Global Acceleration instance.

 |
|└IpAddress|String|47.98.99.xxx| The public IP address of the exclusive-bandwidth Global Acceleration instance.

 |
|└Name|String|instanceName| The name of the Global Acceleration instance.

 |
|└PublicIpAddresses|N/A|N/A| The public IP address.

 |
|└AllocationId|String|12.34.56.78| The ID of the public IP address of the Global Acceleration instance.

 |
|└IpAddress|String|12.34.56.78| The public IP address of the Global Acceleration instance.

 |
|└RegionId|String|cn-hangzhou| The region where the Global Acceleration instance is located.

 |
|└ServiceLocation|String|china-mainland| The service area of the Global Acceleration instance.

 |
|└Status|String|InUse| The status of the Global Acceleration instance.

 |
|TotalCount|Integer|1| The number of queries entries.

 |
|PageNumber|Integer|1| The current page number.

 |
|PageSize|Integer|10| The number of entries per page.

 |
|RequestId|String|6B4EE38D-C75B-4E1F-844E-863A94430676| The ID of the request.

 |

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=DescribeGlobalAccelerationInstances
&RegionId=cn-hangzhou
&<CommonParameters>

```

**Response example**

XML format

```
<DescribeGlobalAccelerationInstancesResponse>
  <PageNumber>1</PageNumber>
  <TotalCount>1</TotalCount>
  <PageSize>10</PageSize>
  <RequestId>6B4EE38D-C75B-4E1F-844E-863A94430676</RequestId>
  <GlobalAccelerationInstances>
    <GlobalAccelerationInstance>
      <ChargeType>PrePaid</ChargeType>
      <GlobalAccelerationInstanceId>ga-bp1x99kj7kl1ziw5xuwb5</GlobalAccelerationInstanceId>
      <HasReservationData>false</HasReservationData>
      <Description/>
      <BackendServers>
        <BackendServer>
          <ServerId>i-2zeg83zvn5d4ed4y2r4c</ServerId>
          <RegionId>cn-beijing</RegionId>
          <ServerType>EcsInstance</ServerType>
          <ServerIpAddress>172.17.109.xxx</ServerIpAddress>
        </BackendServer>
      </BackendServers>
      <IpAddress>47.98.99.xxx</IpAddress>
      <InternetChargeType>PayByBandwidth</InternetChargeType>
      <Name/>
      <BandwidthType>Exclusive</BandwidthType>
      <CreationTime>2018-07-05T03:39:31Z</CreationTime>
      <Status>InUse</Status>
      <ServiceLocation>china-mainland</ServiceLocation>
      <RegionId>cn-hangzhou</RegionId>
      <AccelerationLocation>china-mainland</AccelerationLocation>
      <OperationLocks/>
      <ExpiredTime>2018-08-05T16:00Z</ExpiredTime>
      <PublicIpAddresses/>
      <Bandwidth>10</Bandwidth>
    </GlobalAccelerationInstance>
  </GlobalAccelerationInstances>
</DescribeGlobalAccelerationInstancesResponse>

```

JSON format

```
{
	"PageNumber":1,
	"TotalCount":1,
	"PageSize":10,
	"RequestId":"6B4EE38D-C75B-4E1F-844E-863A94430676",
	"GlobalAccelerationInstances":{
		"GlobalAccelerationInstance":[
			{
				"ChargeType":"PrePaid",
				"GlobalAccelerationInstanceId":"ga-bp1x99kj7kl1ziw5xuwb5",
				"HasReservationData":false,
				"Description":"",
				"BackendServers":{
					"BackendServer":[
						{
							"ServerId":"i-2zeg83zvn5d4ed4y2r4c",
							"RegionId":"cn-beijing",
							"ServerType":"EcsInstance",
							"ServerIpAddress":"172.17.109.xxx"
						}
					]
				},
				"IpAddress":"47.98.99.xxx",
				"InternetChargeType":"PayByBandwidth",
				"Name":"",
				"BandwidthType":"Exclusive",
				"CreationTime":"2018-07-05T03:39:31Z",
				"Status":"InUse",
				"ServiceLocation":"china-mainland",
				"RegionId":"cn-hangzhou",
				"AccelerationLocation":"china-mainland",
				"OperationLocks":{
					"LockReason":[]
				},
				"ExpiredTime":"2018-08-05T16:00Z",
				"PublicIpAddresses":{
					"PublicIpAddress":[]
				},
				"Bandwidth":"10"
			}
		]
	}
}
```

## Error codes {#section_jky_db3_wgb .section}

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

