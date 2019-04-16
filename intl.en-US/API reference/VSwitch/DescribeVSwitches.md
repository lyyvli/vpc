# DescribeVSwitches {#reference_i4w_xmt_ndb .reference}

Queries one or more VSwitches.

This API supports query pagination and each page contains 10 entries by default.

This API only verifies the validity of parameters and does not verify the dependency relationship between the parameters. The returned result is the intersection of all conditions.

## Debug {#section_ayr_qdk_pgb .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|DescribeVSwitches| The name of this action. Value:

 DescribeVSwitches

 |
|RegionId|String|Yes|cn-hangzhou| The region of the VPC to which the VSwitch belongs.

 To query the region ID, call DescribeRegions.

 |
|Isdefault|Boolean |No|true| Indicates whether to query the default VSwitch in the specified region. 

 -   true \(default value\): Query all VSwitches in the specified region.
-   false: Do not query the default VSwitch.

 |
|OwnerAccount|String|No| | The owner account.

 |
|PageNumber|Integer|No|10| The number of pages to return. Default value: 1.

 |
|PageSize|Integer|No|1| The number of rows per page. Maximum value: 50. Default value: 10.

 |
|ResourceGroupId|String|No|1234567| The ID of the resource group.

 |
|RouteTableId|String|No|vtb-bp145q7glnuzdvzu21pom| The ID of the route table.

 |
|VSwitchId|String|No|vsw-23dsf3xxxxxxxxx| The ID of the VSwitch.

 |
|VSwitchName|String|No|VSwitch-1| The name of the VSwitch.

 |
|VpcId|String|No|vpc-25eq58plxxxxxxxxxx| The ID of the VPC.

 |
|ZoneId|String|No|cn-hangzhou-d| The ID of the zone to which the VSwitch belongs.

 To query the region ID, call DescribeZones.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|VSwitches|N/A|N/A| A list of VSwitches.

 |
|└AvailableIpAddressCount|Long|1| The number of available IP addresses in the VSwitch.

 |
|└CidrBlock|String|172.16.0.0/24| The CIDR block of the VSwitch.

 |
|└CreationTime|String|2018-01-18T12:43:57Z| The time when the VSwitch was created.

 |
|└Description|String|This is my vswitch.| The description of the VSwitch.

 |
|└Ipv6CidrBlock|String|2408:4004:0:2900::/64| The IPv6 CIDR block of the VSwitch.

 |
|└IsDefault|Boolean|true| Whether the VSwitch is the default VSwitch in the zone.

 |
|└ResourceGroupId|String|123456| The ID of the resource group to which the VSwitch belongs.

 |
|└RouteTable|N/A|N/A| The information of the route table.

 |
|└RouteTableId|String|vrt-123456| The ID of the route table associated with the VSwitch.

 |
|└RouteTableType|String|System| The type of the route table:

 -   System: system route table
-   Custom: custom route table

 |
|└Status|String|Available| The status of the VSwitch. Valid values:

 -   Pending: being configured
-   Available: available

 |
|└VSwitchId|String|vsw-xxxxxxxxxxxxxxxx| The ID of the VSwitch.

 |
|└VSwitchName|String|VSwitch-1| The name of the VSwitch.

 |
|└VpcId|String|vpc-234asxxxxxxxxxxxxx| The ID of the VPC to which the VSwitch belongs.

 |
|└ZoneId|String|cn-hangzhou-d| The ID of the zone to which the VSwitch belongs.

 |
|TotalCount|Integer|10| The number of queried entries.

 |
|PageNumber|Integer|10| The current page number.

 |
|PageSize|Integer|10| The number of rows per page.

 |
|RequestId|String|9A572171-4E27-40D1-BD36-D26XXXXXXXXX| The ID of the request.

 |

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

http(s)://[Endpoint]/?<CommonParameters>

```

**Response example**

-   XML format

    ``` {#xml_return_success_demo}
    <DescribeVSwitchesResponse>
      <RequestId>9A572171-4E27-40D1-BD36-D26C9E71E29E</RequestId>
      <VSwitches>
        <VSwitch>
          <VSwitchId> vsw-25b7pv15t </VSwitchId>
          <Status>Available</Status>
          <CidrBlock>172.16.1.0/24</CidrBlock>
          <ZoneId>cn-beijing-a</ZoneId>
          <AvailableIpAddressCount>246</AvailableIpAddressCount>
          <VpcId>vpc-257gq642n</VpcId>
          <Description/>
          <VSwitchName/>
          <CreationTime> 2014-10-29T15:21:02Z </CreationTime>
        </VSwitch>
      </VSwitches>
    </DescribeVSwitchesResponse>
    
    ```

-   JSON format

    ``` {#json_return_success_demo}
    {
    	"PageNumber":1,
    	"VSwitches":{
    		"VSwitch":[
    			{
    				"CreationTime":"2014-10-29T15:21:02Z",
    				"Status":"Available",
    				"CidrBlock":"172.16.1.0/24",
    				"Description":"",
    				"AvailableIpAddressCount":246,
    				"VSwitchName":"",
    				"ZoneId":"cn-beijing-a",
    				"VSwitchId":"vsw-25b7pv15t",
    				"VpcId":"vpc-257gq642n"
    			}
    		]
    	},
    	"TotalCount":1,
    	"PageSize":10,
    	"RequestId":"9A572171-4E27-40D1-BD36-D26C9E71E29E"
    }
    ```


## Error codes {#section_ws1_zqr_pgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidVSwitchId.NotFound|VSwitch not exist.|The specified VSwitch does not exist.|
|400|Forbidden.VpcNotFound|Specified VPC can not found.|The specified VPC does not exist.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

