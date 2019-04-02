# DescribeVSwitchAttributes {#reference_i4w_xmt_ndb2 .reference}

Queries the configurations of a VSwitch.

## Debug {#section_ayr_qdk_pgb .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_m22b .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|DescribeVSwitchAttributes| The name of this action. Value: 

 DescribeVSwitchAttributes

 |
|RegionId|String|Yes|cn-hangzhou| The region ID of the VPC to which the route table belongs.

 |
|VSwitchId|String|Yes|vsw-25naue4gz| The ID of the VSwitch.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|AvailableIpAddressCount|Long|12| The number of available IP addresses.

 |
|CidrBlock|String|192.168.0.1/24| The private CIDR block of the VSwitch.

 |
|CloudResources|N/A|N/A| Cloud resources under the VSwitch.

 |
|└ResourceCount|Integer|1| The number of cloud resources under the VSwitch.

 |
|└ResourceType|String|nat| The type of the cloud resource.

 |
|CreationTime|String|2017-08-22T10:40:25Z| The time when the VSwitch was created.

 |
|Description|String|This is my VSwitch.| The description of the VSwitch.

 |
|Ipv6CidrBlock|String|2408:4004:0:2900::/64| The IPv6 CIDR block of the VSwitch.

 |
|IsDefault|Boolean|false| Whether the VSwitch is the default VSwitch.

 |
|RequestId|String|7B48B4B9-1EAD-469F-B488-594DAB4B6A1A| The ID of the request.

 |
|ResourceGroupId|String|123456| The ID of the resource group.

 |
|RouteTable|N/A|N/A| The route table information of the VSwitch.

 |
|└RouteTableId|String|vtb-bp145q7glnuzdvzu21pom| The ID of the route table associated with the VSwitch.

 |
|└RouteTableType|String|System| The type of the route table. Valid values:

 -   System: system route table.
-   Custom: customer route table.

 |
|Status|String|Pending| The status of the VSwitch. Valid values:

 -   Pending: being configured
-   Available: available

 |
|VSwitchId|String|vsw-25b7pv15t| The ID of the VSwitch.

 |
|VSwitchName|String|test| The name of the VSwitch.

 |
|VpcId|String|vpc-257gq642n| The ID of the VPC to which the VSwitch belongs.

 |
|ZoneId|String|cn-beijing-a| The ID of the zone to which the VSwitch belongs.

 |

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

/?Action=DescribeVSwitchAttributes
&VSwitchId=vsw-25naue4gz
&<CommonParameters>

```

**Response example**

**XML format**

``` {#xml_return_success_demo}
<DescribeVSwitchAttributesResponse>
  <RouteTable>
    <RouteTableId>vtb-hp3ngu1hkdutfakqnz76p</RouteTableId>
    <RouteTableType>System</RouteTableType>
  </RouteTable>
  <Description/>
  <IsDefault>false</IsDefault>
  <AvailableIpAddressCount>251</AvailableIpAddressCount>
  <ResourceGroupId>rg-acfmy45w7w2cdxa</ResourceGroupId>
  <ZoneId>cn-huhehaote-a</ZoneId>
  <VSwitchId>vsw-hp3lyltb1dosj540yyxjv</VSwitchId>
  <VpcId>vpc-hp34hflqqsjh3a3q7lbtr</VpcId>
  <CreationTime>2019-01-07T04:54:14Z</CreationTime>
  <Status>Available</Status>
  <CidrBlock>192.168.0.0/24</CidrBlock>
  <RequestId>A31F062D-81F0-48BC-9771-915D6622D26A</RequestId>
  <VSwitchName>doc1</VSwitchName>
  <Ipv6CidrBlock>2408:4004:0:2900::/64</Ipv6CidrBlock>
  <CloudResources/>
</DescribeVSwitchAttributesResponse>

```

**JSON format**

``` {#json_return_success_demo}
{
	"RouteTable":{
		"RouteTableId":"vtb-hp3ngu1hkdutfakqnz76p",
		"RouteTableType":"System"
	},
	"Description":"",
	"IsDefault":false,
	"AvailableIpAddressCount":251,
	"ResourceGroupId":"rg-acfmy45w7w2cdxa",
	"ZoneId":"cn-huhehaote-a",
	"VSwitchId":"vsw-hp3lyltb1dosj540yyxjv",
	"VpcId":"vpc-hp34hflqqsjh3a3q7lbtr",
	"CreationTime":"2019-01-07T04:54:14Z",
	"Status":"Available",
	"CidrBlock":"192.168.0.0/24",
	"RequestId":"A31F062D-81F0-48BC-9771-915D6622D26A",
	"Ipv6CidrBlock":"2408:4004:0:2900::/64",
	"VSwitchName":"doc1",
	"CloudResources":{
		"CloudResourceSetType":[]
	}
}
```

## Error codes {#section_g3b_4gs_pgb .section}

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

