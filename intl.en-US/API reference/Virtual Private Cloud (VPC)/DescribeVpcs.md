# DescribeVpcs {#reference_i4w_xmt_ndb .reference}

Queries VPCs in a region.

## Debug {#section_ayr_qdk_pgb .section}

[Debug](https://api.aliyun.com/#product=Slb&api=CreateLoadBalancer) in OpenAPI Explorer to have an SDK code example automatically generated.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|DescribeVpcs| The action to perform. Valid value:

 DescribeVpcs

 |
|RegionId|String|No|cn-hangzhou| The region where the VPCs belong.

 You can obtain the region ID by calling the DescribeRegions API.

 |
|Isdefault|Boolean|No|false| Indicates whether to query the default VPC in the specified region. Valid value:

 -   true \(Default\): Queries all VPCs in the specified region.
-   false: Does not query the default VPC.

 |
|PageNumber|Integer|No|10| The number of pages to return. The default value is 1.

 |
|PageSize|Integer|No|1| The number of rows per page. The maximum value is 50, and the default value is 10.

 |
|ResourceGroupId|String|No|xxxxx| The ID of the resource group to which the VPCs belong.

 |
|Tag.N.Key|String|No|Tag.1.name| The filter condition. The value range of N is 1-5.

 |
|Tag.N.Value|String|No|Tag.1.myvpc| The value of the filter condition. The value range of N is 1-5.

 |
|VpcId|String|No|vpc-257gq64xxxxx| The ID of the VPC.

 You can specify up to 20 VPC IDs. Separate multiple VPC IDs with commas.

 |
|VpcName|String|No|Vpc-1| The name of the VPC.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|Vpcs| | | A list of VPCs.

 |
|└CidrBlock|String|10.0.0.0/24| The CIDR block of the VPC.

 |
|└CreationTime|String|2018-04-18T15:02:37Z| The time at which the VPC was created.

 |
|└Description|String|description| The description of the VPC.

 |
|└Ipv6CidrBlock|String|224.224.223.212/24| The IPv6 CIDR block of the VPC.

 |
|└IsDefault|Boolean|false| Whether the VPC is the default VPC in this region.

 |
|└NatGatewayIds| |nat-245xxxftwt4567| The ID of the NAT gateway.

 |
|└RegionId|String|cn-hangzhou| The ID of the region to which the VPC belongs.

 |
|└ResourceGroupId|String|rg-acfmxazb4ph6aiy| The ID of the resource group.

 |
|└RouterTableIds| |vtb-bp145q7glnuzdvzu21pom| The ID of the router table.

 |
|└Status|String|Available| The status of the VPC. Valid values:

 -   Pending: unavailable, being configured
-   Available: available

 |
|└Tags| | | The tags of the VPC.

 |
|└Key|String|env| The key of the tag.

 |
|└Value|String|internal| The value of the tag.

 |
|└UserCidrs| |10.0.0.0/8| A list of customer-side CIDR blocks.

 |
|└VRouterId|String|vrt-bp1lhl0taikrteen80oxx| The ID of the VRouter.

 |
|└VSwitchIds| |\{ "VSwitchId": \[\] \}| A list of VSwitches.

 |
|└VpcId|String|vpc-bp15zckdt37pq72zvw3| The ID of the VPC.

 |
|└VpcName|String|vpc1| The name of the VPC.

 |
|TotalCount|Integer|1| The number of queried entries.

 |
|PageNumber|Integer|1| The current page number.

 |
|PageSize|Integer|21| The number of entries on the current page.

 |
|RequestId|String|9B941224-B647-4644-A746-641906D6B954| The ID of the request.

 |

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?RegionId=cn-hangzhou
&<CommonParameters>
			
```

 **Response example** 

-   XML format

    ``` {#xml_return_success_demo}
    <DescribeVpcsResponse>
      <PageNumber>1</PageNumber>
      <Vpcs>
        <Vpc>
          <VpcName/>
          <Description/>
          <IsDefault>false</IsDefault>
          <ResourceGroupId>rg-acfmxazb4ph6aiy</ResourceGroupId>
          <UserCidrs/>
          <NatGatewayIds/>
          <RouterTableIds>
            <RouterTableIds>vtb-bp1krxxzp0c29fmontbal</RouterTableIds>
          </RouterTableIds>
          <VpcId>vpc-bp1qpo0kug3a20qqe9h7v</VpcId>
          <VRouterId>vrt-bp1jcg5cmxjbl9xgc58bw</VRouterId>
          <CreationTime>2018-12-06T06:11:55Z</CreationTime>
          <Status>Available</Status>
          <CidrBlock>172.16.0.0/12</CidrBlock>
          <VSwitchIds/>
          <RegionId>cn-hangzhou</RegionId>
          <Ipv6CidrBlock/>
        </Vpc>
        <Vpc>
          <VpcName>kttest</VpcName>
          <Description/>
          <IsDefault>false</IsDefault>
          <ResourceGroupId>rg-acfmxazb4ph6aiy</ResourceGroupId>
          <UserCidrs/>
          <NatGatewayIds/>
          <RouterTableIds>
            <RouterTableIds>vtb-bp1blq1oh0ybfnpm1bh20</RouterTableIds>
          </RouterTableIds>
          <VpcId>vpc-bp1aevy8sofi8mh1qc5cm</VpcId>
          <VRouterId>vrt-bp149ve7yeyvio4ncklxz</VRouterId>
          <CreationTime>2018-11-08T08:54:03Z</CreationTime>
          <Status>Available</Status>
          <CidrBlock>192.168.0.0/16</CidrBlock>
          <VSwitchIds>
            <VSwitchId>vsw-bp12mw1f8k3jgygk9bmlj</VSwitchId>
          </VSwitchIds>
          <RegionId>cn-hangzhou</RegionId>
          <Ipv6CidrBlock/>
        </Vpc>
      </Vpcs>
      <TotalCount>2</TotalCount>
      <PageSize>10</PageSize>
      <RequestId>C6532AA8-D0F7-497F-A8EE-094126D441F5</RequestId>
    </DescribeVpcsResponse>
    					
    ```

-   JSON format

    ``` {#json_return_success_demo}
    {
    	"PageNumber":1,
    	"TotalCount":2,
    	"Vpcs":{
    		"Vpc":[
    			{
    				"VpcName":"",
    				"Description":"",
    				"IsDefault":false,
    				"ResourceGroupId":"rg-acfmxazb4ph6aiy",
    				"UserCidrs":{
    					"UserCidr":[]
    				},
    				"NatGatewayIds":{
    					"NatGatewayIds":[]
    				},
    				"RouterTableIds":{
    					"RouterTableIds":[
    						"vtb-bp1krxxzp0c29fmontbal"
    					]
    				},
    				"VpcId":"vpc-bp1qpo0kug3a20qqe9h7v",
    				"VRouterId":"vrt-bp1jcg5cmxjbl9xgc58bw",
    				"CreationTime":"2018-12-06T06:11:55Z",
    				"Status":"Available",
    				"CidrBlock":"172.16.0.0/12",
    				"VSwitchIds":{
    					"VSwitchId":[]
    				},
    				"RegionId":"cn-hangzhou",
    				"Ipv6CidrBlock":""
    			},
    			{
    				"VpcName":"kttest",
    				"Description":"",
    				"IsDefault":false,
    				"ResourceGroupId":"rg-acfmxazb4ph6aiy",
    				"UserCidrs":{
    					"UserCidr":[]
    				},
    				"NatGatewayIds":{
    					"NatGatewayIds":[]
    				},
    				"RouterTableIds":{
    					"RouterTableIds":[
    						"vtb-bp1blq1oh0ybfnpm1bh20"
    					]
    				},
    				"VpcId":"vpc-bp1aevy8sofi8mh1qc5cm",
    				"VRouterId":"vrt-bp149ve7yeyvio4ncklxz",
    				"CreationTime":"2018-11-08T08:54:03Z",
    				"Status":"Available",
    				"CidrBlock":"192.168.0.0/16",
    				"VSwitchIds":{
    					"VSwitchId":[
    						"vsw-bp12mw1f8k3jgygk9bmlj"
    					]
    				},
    				"RegionId":"cn-hangzhou",
    				"Ipv6CidrBlock":""
    			}
    		]
    	},
    	"PageSize":10,
    	"RequestId":"C6532AA8-D0F7-497F-A8EE-094126D441F5"
    }
    ```


## Error codes {#section_hnq_xqq_pgb .section}

|HTTP code|Error code|Error message|Description|
|---------|----------|-------------|-----------|
|500|InternalError|The request processing has failed due to some unknown error.|An error occurred while the request was being processed.|

[View the error codes of the product](https://error-center.aliyun.com/status/product/Vpc)

