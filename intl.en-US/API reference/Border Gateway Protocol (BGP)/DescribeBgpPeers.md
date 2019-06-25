# DescribeBgpPeers {#doc_api_Vpc_DescribeBgpPeers .reference}

Queries BGP peers in a region.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeBgpPeers) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeBgpPeers|The name of this action. Value: **DescribeBgpPeers**

 |
|RegionId|String|Yes|cn-shanghai|The ID of the region to which the BGP group belongs. To query the region ID, call [DescribeRegions](~~36063~~).

 |
|BgpGroupId|String|No|bgpg-2zev8h2wo414xxxxxxx|Optional. The ID of the BGP group.

 |
|BgpPeerId|String|No|bgp-2ze3un0ft1jd1xxxxxxxx|Optional. The ID of the BGP peer.

 |
|IsDefault|Boolean|No|false|Optional. Indicates whether the BGP group is the default BGP group.

 |
|OwnerAccount|String|No|xxx@aliyun.com|Optional. Your account.

 |
|PageNumber|Integer|No|1|Optional. The page number of the BGP peer list. Default value: 1

 |
|PageSize|Integer|No|1|Optional. The number of rows per page for a paged query. Maximum value: 50. Default value: 10

 |
|RouterId|String|No|vrt-acfmxazxxxxxxxx|Optional. The ID of the VRouter.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|BgpPeers| | |A list of BGP peers.

 |
|└Name|String|test|The name of the BGP peer.

 |
|└PeerIpAddress|String|116.62.xx.xx|The IP address of the BGP peer.

 |
|└AuthKey|String|! PWZ2wsq|The authentication key of the BGP group.

 |
|└RouterId|String|vbr-2zecmmvg5gvu8xxxxxxxx|The ID of the VRouter.

 |
|└Status|String|active|The status of the BGP peer.

 |
|└BgpGroupId|String|bgp-wz977wcrmb69axxxxxxxx|The ID of the BGP group.

 |
|└BgpPeerId|String|bgp-wz977wcrmb69axxxxxxxx|The ID of the BGP peer.

 |
|└BgpStatus|String|Established|The BGP connection status.

 |
|└Description|String|xxxxxxxxx|The description of the BGP group.

 |
|└EnableBfd|Boolean|true|Indicates whether to enable the BFD function. Valid values:

 -   **true**: Enable the BFD function.
-   **false**: Do not enable the BFD function.

 |
|└Hold|String|30|The hold time.

 |
|└IsFake|String|true|Indicates whether a fake ASN is enabled.

 |
|└Keepalive|String|10|The keep-alive time.

 |
|└LocalAsn|String|45104|The local ASN.

 |
|└PeerAsn|String|active|The ASN of the BGP peer.

 |
|└RegionId|String|cn-shanghai|The ID of the region to which the BGP group belongs.

 |
|└RouteLimit|String|99|The route quota.

 |
|TotalCount|Integer|10|The number of queried entries.

 |
|PageNumber|Integer|1|The current page number.

 |
|PageSize|Integer|2|The number of entries per page.

 |
|RequestId|String|DE77A7F3-3B74-41C0-A5BC-CAFD188C28B6|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeBgpPeers
&RegionId=cn-shanghai
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeBgpPeers>
  <TotalCount>2</TotalCount>
  <PageSize>10</PageSize>
  <RequestId>16DFA5E6-9771-41B7-B079-DD7C2DF49BE6</RequestId>
  <BgpPeers>
    <BgpPeer>
      <BgpGroupId>bgpg-2zev8h2wo414sxxxxxxxx</BgpGroupId>
      <LocalAsn>45104</LocalAsn>
      <PeerIpAddress>11.11.xx.xx</PeerIpAddress>
      <Hold>30</Hold>
      <Description/>
      <AuthKey/>
      <IsFake>true</IsFake>
      <PeerAsn>234</PeerAsn>
      <Keepalive>10</Keepalive>
      <RouteLimit>99</RouteLimit>
      <BgpPeerId>bgp-2ze3un0ft1jd1xxxxxxxx</BgpPeerId>
      <Name/>
      <Status>Available</Status>
      <BgpStatus/>
      <RouterId>vbr-2zecmmvg5gvu8xxxxxxxx</RouterId>
      <RegionId>cn-beijing</RegionId>
    </BgpPeer>
    <BgpPeer>
      <BgpGroupId>bgpg-2zev8h2wo414sxxxxxxxx</BgpGroupId>
      <LocalAsn>45104</LocalAsn>
      <PeerIpAddress>11.11.xx.xx</PeerIpAddress>
      <Hold>30</Hold>
      <Description/>
      <AuthKey/>
      <IsFake>true</IsFake>
      <PeerAsn>234</PeerAsn>
      <Keepalive>10</Keepalive>
      <RouteLimit>99</RouteLimit>
      <BgpPeerId>bgp-2zeu54rbreqqzxxxxxxxx</BgpPeerId>
      <Name/>
      <Status>Available</Status>
      <BgpStatus/>
      <RouterId>vbr-2zecmmvg5gvu8xxxxxxxx</RouterId>
      <RegionId>cn-beijing</RegionId>
    </BgpPeer>
  </BgpPeers>
</DescribeBgpPeers>

```

`JSON` format

``` {#json_return_success_demo}
{
	"TotalCount":2,
	"PageSize":10,
	"RequestId":"16DFA5E6-9771-41B7-B079-DD7C2DF49BE6",
	"BgpPeers":{
		"BgpPeer":[
			{
				"BgpGroupId":"bgpg-2zev8h2wo414sxxxxxxxx",
				"LocalAsn":45104,
				"PeerIpAddress":"11.11.xx.xx",
				"Hold":30,
				"Description":"",
				"AuthKey":"",
				"IsFake":true,
				"PeerAsn":234,
				"Keepalive":10,
				"RouteLimit":99,
				"BgpPeerId":"bgp-2ze3un0ft1jd1xxxxxxxx",
				"Name":"",
				"Status":"Available",
				"BgpStatus":"",
				"RouterId":"vbr-2zecmmvg5gvu8xxxxxxxx",
				"RegionId":"cn-beijing"
			},
			{
				"BgpGroupId":"bgpg-2zev8h2wo414sxxxxxxxx",
				"LocalAsn":45104,
				"PeerIpAddress":"11.11.xx.xx",
				"Hold":30,
				"Description":"",
				"AuthKey":"",
				"IsFake":true,
				"PeerAsn":234,
				"Keepalive":10,
				"RouteLimit":99,
				"BgpPeerId":"bgp-2zeu54rbreqqzxxxxxxxx",
				"Name":"",
				"Status":"Available",
				"BgpStatus":"",
				"RouterId":"vbr-2zecmmvg5gvu8xxxxxxxx",
				"RegionId":"cn-beijing"
			}
		]
	}
}
```

## Error codes { .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|500|InternalError|The request processing has failed due to some unknown error.|The request was not processed due to an unknown error.|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID is invalid. Please check if the cloud service is available in the specified region.|

[See common error codes.](https://error-center.aliyun.com/status/product/Vpc)

