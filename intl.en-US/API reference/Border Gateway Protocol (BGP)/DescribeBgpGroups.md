# DescribeBgpGroups {#referen3ce_i4w_xmt_ndb .reference}

Queries BGP groups.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|:------------|:----------|
|Action|String|Yes|DescribeBgpGroupsDescribeBgpGroups| The name of this action. Value:

 DescribeBgpGroups

 |
|RegionId|String|Yes|cn-shanghai| The region to which the BGP group belongs.

 To query the region ID, call DescribeRegions.

 |
|BgpGroupId|String|No|bgpg-wz9f62v4fbg2gxxxxxxxx| The ID of the BGP group.

 |
|IsDefault|Boolean|No|false| Indicates whether the specified BGP group is the default BGP group.

 |
|OwnerAccount|String|No|1234abcd@aliyun.com| The owner account.

 |
|PageNumber|Integer|No|1| The number of pages to return. Default value: 1.

 |
|PageSize|Integer|No|1| The number of rows per page. Maximum value: 50. Default value: 10.

 |
|RouterId|String|No|vrt-kojok19x3j0q6kx| The ID of the VBR associated with the BGP group.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|TotalCount|Integer|10| The number of queried entries.

 |
|PageNumber|Integer|1| The current page number.

 |
|PageSize|Integer|5| The number of entries per page.

 |
|BgpGroups| | | A list of BGP groups.

 |
|└AuthKey|String|!PWZ2wsq| The authentication key used by the BGP group.

 |
|└BgpGroupId|String|bgp-wz977wcrmb69axxxxxxxx| The ID of the BGP group.

 |
|└Description|String|The| The description of the BGP group.

 |
|└Hold|String|30| The hold time to wait for the BGP message. If no BGP message is received when the hold time is reached, the BGP peer is disconnected.

 |
|└IsFake|String|true| Indicates whether the ASN is fake.

 |
|└Keepalive|String|10| The keep-alive time.

 |
|└LocalAsn|String|45104| The local ASN.

 |
|└Name|String|BGPName| The name of the BGP group.

 |
|└PeerAsn|String|1111| The ASN of the BGP peer.

 |
|└RegionId|String|cn-shanghai| The region ID of the BGP group. For more information, see [Regions and zones](~~40654~~).

 |
|└RouteLimit|String|99| The route quota.

 |
|└RouterId|String|vrt-bp1lhl0taikrteen80oxx| The ID of the VBR.

 |
|└Status|String|active| The status of the BGP peer.

 |
|RequestId|String|1D0971B2-A35A-42C1-A44C-E91360C36C0B| The ID of the request.

 |

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=DescribeBgpGroups
&RegionId=cn-shanghai
&<CommonParameters>

```

 **Response example** 

-   XML format

    ```
    <DescribeBgpGroupsResponse>
      <TotalCount>1</TotalCount>
      <PageSize>10</PageSize>
      <RequestId>09E2C0FD-37FF-4737-80DF-517AC36D43DB</RequestId>
      <BgpGroups>
        <BgpGroup>
          <BgpGroupId>bgpg-2zev8h2wo414sfhjgdlhh</BgpGroupId>
          <LocalAsn>45104</LocalAsn>
          <Hold>30</Hold>
          <Description/>
          <AuthKey/>
          <IsFake>true</IsFake>
          <PeerAsn>234</PeerAsn>
          <Keepalive>10</Keepalive>
          <RouteLimit>99</RouteLimit>
          <Name>Group1</Name>
          <Status>Pending</Status>
          <RouterId>vbr-2zecmmvg5gvu8i4telkhw</RouterId>
          <RegionId>cn-beijing</RegionId>
        </BgpGroup>
      </BgpGroups>
    </DescribeBgpGroupsResponse>
    
    ```

-   JSON format

    ```
    {
    	"TotalCount":1,
    	"PageSize":10,
    	"RequestId":"09E2C0FD-37FF-4737-80DF-517AC36D43DB",
    	"BgpGroups":{
    		"BgpGroup":[
    			{
    				"BgpGroupId":"bgpg-2zev8h2wo414sfhjgdlhh",
    				"LocalAsn":45104,
    				"Hold":30,
    				"Description":"",
    				"AuthKey":"",
    				"IsFake":true,
    				"PeerAsn":234,
    				"Keepalive":10,
    				"RouteLimit":99,
    				"Name":"Group1",
    				"Status":"Pending",
    				"RouterId":"vbr-2zecmmvg5gvu8i4telkhw",
    				"RegionId":"cn-beijing"
    			}
    		]
    	}
    }
    ```


## Error codes {#section_yck_qln_xgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|500|InternalError|The request processing has failed due to some unknown error.|An error occurred while the request was being processed.|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

