# DescribeRouteEntryList {#doc_api_Vpc_DescribeRouteEntryList .reference}

Queries one or more route entries in a route table.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=DescribeRouteEntryList&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeRouteEntryList|The name of this action. Value: **DescribeRouteEntryList**

 |
|RegionId|String|Yes|cn-hangzhou|The region ID of the route table to which the route entry belongs. To query the region ID, call [DescribeRegions](~~36063~~).

 |
|RouteTableId|String|Yes|vtb-bp1r9pvl4xen8s9ju\*\*\*\*|The ID of the route table.

 |
|DestinationCidrBlock|String|No|192.168.2.0/24|The destination CIDR block of the route entry. IPv4 and IPv6 CIDR blocks are supported.

 **Note:** Only the China site supports IPv6 CIDR blocks.

 |
|IpVersion|String|No|IPv4|The version of the IP protocol. Valid values:

 -   **IPv4**: IPv4 protocol
-   **IPv6**: IPv6 protocol

 **Note:** Only the China site supports the IPv6 protocol.

 |
|MaxResult|Integer|No|50|The number of entries per page in the case of a paged query result. Value range: **20** to **100**. Default value: **50**

 |
|NextHopId|String|No|vpn-bp10zyaph5cc8b7c7\*\*\*\*|The instance ID of the next hop.

 |
|NextHopType|String|No|Instance|The type of the next hop. Valid values:

 -   **Instance**: ECS instance
-   **HaVip**: High-Availability Virtual IP Address
-   **VpnGateway**: VPN Gateway
-   **NatGateway**: NAT Gateway
-   **NetworkInterface**: Secondary Elastic Network Interface
-   **RouterInterface**: router interface
-   **IPv6Gateway**: IPv6 Gateway

 **Note:** Only the China site supports IPv6 Gateways as next hops.

 |
|NextToken|String|No|caeba0bbb2be03f84eb48b699f0a4883|The token for the next query.

 |
|RouteEntryId|String|No|rte-bp1mnnr2al0naomnp\*\*\*\*|The ID of the route entry.

 |
|RouteEntryName|String|No|abc|The name of the route entry.

 |
|RouteEntryType|String|No|System|The type of the route entry. Valid values:

 -   **Custom**: custom route entry
-   **System**: system route entry

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|NextToken|String|caeba0bbb2be03f84eb48b699f0a4883|The token for the next query.

 |
|RequestId|String|14A07460-EBE7-47CA-9757-12CC4761D47A|The ID of the request.

 |
|RouteEntrys| | |The list of route entries.

 |
|RouteEntry| | |The details of a route entry.

 |
|DestinationCidrBlock|String|10.0.0.0/24|The destination CIDR block of the route entry.

 |
|IpVersion|String|IPv4|The version of the IP protocol.

 -   **IPv4**: IPv4 protocol
-   **IPv6**: IPv6 protocol

 |
|NextHops| | |The list of next hops.

 |
|NextHop| | |The details of the next hop.

 |
|Enabled|Integer|0|Indicates whether the next hop is enabled.

 -   **0**: Indicates that the next hop is disabled and unavailable.
-   **1**: Indicates that the next hop is enabled and available.

 |
|NextHopId|String|vpn-bp10zyaph5cc8b7c7\*\*\*\*|The instance ID of the next hop.

 |
|NextHopRegionId|String|cn-hangzhou|The region ID of the next hop instance.

 |
|NextHopRelatedInfo| | |The association information of the next hop.

 |
|InstanceId|String|vpc-bp1t36rn9l53iwbsf\*\*\*\*|The ID of the instance associated with the next hop.

 |
|InstanceType|String|VPC|The type of the instance associated with the next hop.

 -   **VPC**: Virtual Private Cloud
-   **VBR**: Virtual Border Router

 |
|RegionId|String|ch-hangzhou|The region ID of the instance associated with the next hop.

 |
|NextHopType|String|Instance|The type of the next hop.

 -   **Instance**: ECS instance
-   **HaVip**: High-Availability Virtual IP Address
-   **VpnGateway**: VPN Gateway
-   **NatGateway**: NAT Gateway
-   **NetworkInterface**: Secondary Elastic Network Interface
-   **RouterInterface**: router interface
-   **IPv6Gateway**: IPv6 Gateway

 **Note:** Only the China site supports IPv6 Gateways as next hops.

 |
|Weight|Integer|100|The weight of the route entry.

 |
|RouteEntryId|String|rte-bp1mnnr2al0naomnp\*\*\*\*|The ID of the route entry.

 |
|RouteEntryName|String|aaa|The name of the route entry.

 |
|RouteTableId|String|vtb-bp15w5q90d2rk3bww\*\*\*\*|The ID of the route table.

 |
|Status|String|Available|The status of the route entry.

 |
|Type|String|Custom|The type of the route entry.

 -   **Custom**: custom route entry
-   **System**: system route entry

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeRouteEntryList
&RegionId=cn-hangzhou
&RouteTableId=vtb-bp1r9pvl4xen8s9ju****
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<DescribeRouteEntryListResponse>
	  <NextToken></NextToken>
	  <RouteEntrys>
		    <RouteEntry>
			      <NextHops>
				        <NextHop>
					          <NextHopId>eni-bp16v0fuhulfl5e1****</NextHopId>
					          <NextHopRelatedInfo></NextHopRelatedInfo>
					          <NextHopType>NetworkInterface</NextHopType>
				        </NextHop>
			      </NextHops>
			      <Status>Available</Status>
			      <RouteEntryName>ENI</RouteEntryName>
			      <RouteEntryId>rte-bp1aejenqyg5zcmv4****</RouteEntryId>
			      <Type>Custom</Type>
			      <IpVersion>ipv4</IpVersion>
			      <RouteTableId>vtb-bp15w5q90d2rk3bww****</RouteTableId>
			      <DestinationCidrBlock>103.0.0.0/32</DestinationCidrBlock>
		    </RouteEntry>
	  </RouteEntrys>
	  <RequestId>57828ADD-F0C4-4125-AF79-6556D44C5277</RequestId>
</DescribeRouteEntryListResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"NextToken":"",
	"RouteEntrys":{
		"RouteEntry":[
			{
				"Status":"Available",
				"NextHops":{
					"NextHop":[
						{
							"NextHopId":"eni-bp16v0fuhulfl5e1****",
							"NextHopRelatedInfo":{},
							"NextHopType":"NetworkInterface"
						}
					]
				},
				"RouteEntryName":"ENI",
				"Type":"Custom",
				"RouteEntryId":"rte-bp1aejenqyg5zcmv4****",
				"IpVersion":"ipv4",
				"RouteTableId":"vtb-bp15w5q90d2rk3bww****",
				"DestinationCidrBlock":"103.0.0.0/32"
			}
		]
	},
	"RequestId":"57828ADD-F0C4-4125-AF79-6556D44C5277"
}
```

## Errors { .section}

