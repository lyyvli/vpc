# DescribeVpcAttribute {#reference_wkg_tqt_4fb .reference}

Queries the configurations of a VPC.

## Debug {#apiExplorer .section}

By using [OpenAPI Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_mrw_vqt_4fb .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeVpcAttribute|The name of this action. Value: DescribeVpcAttribute|
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the VPC belongs.|
|VpcId |String|Yes|vpc-bp18sth14qii3pnvodkvt|The ID of the VPC to be queried.|
|IsDefault|Boolean|No|false|Indicates whether the VPC is the default VPC. Valid values:-   false: The VPC is not the default VPC.
-   true: The VPC is the default VPC.

|

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|AssociatedCens|N/A|N/A| A list of CEN instances attached to the VPC.

 |
|└CenId|String|cen-7qthudw0ll6jmc4gsu| The ID of the CEN instance.

 |
|└CenOwnerId|Long|1231579085529123| The ID of the account to which the CEN instance belongs.

 |
|└CenStatus|String|Attached| The status of the CEN instance.

 |
|CidrBlock|String|192.168.0.0/16| The private CIDR block of the VPC.

 |
|ClassicLinkEnabled|Boolean|false| Indicates whether the ClassicLink function is enabled.

 |
|CloudResources|N/A|N/A| A list of cloud resources under the VPC.

 |
|└ResourceCount|Integer|1| The number of the resources under the VPC.

 |
|└ResourceType|String|VSwitch| The type of the resources under the VPC.

 |
|CreationTime|String|2018-10-16T07:31:09Z| The time at which the VPC was created.

 |
|Description|String|VPC| The description of the VPC.

 |
|Ipv6CidrBlock|String|224.223.234.233/24| The IPv6 CIDR block of the VPC.

 |
|IsDefault|Boolean|false| Indicates whether the VPC is the default VPC.

 |
|RegionId|String|cn-hangzhou| The ID of the region to which the VPC belongs.

 |
|RequestId|String|7486AE4A-129D-43DB-A714-2432C074BA04| The ID of the request.

 |
|ResourceGroupId|String|rg-acfmxazb4ph6aiy| The ID of the resource group.

 |
|Status|String|Available| The status of the VPC.

 |
|UserCidrs|N/A|172.16.0.1/24| The customer-side CIDR blocks. Separate CIDR blocks with commas. You can specify up to three CIDR blocks.

 |
|VRouterId|String|vrt-bp1jso6ng1at0ajsc8mbe| The ID of the VRouter.

 |
|VSwitchIds|N/A|\{"VSwitchId": \[ "vsw-bp14cagpfysr29feg5t97" \]\}| A list of VSwitches under the VPC.

 |
|VpcId|String|vpc-bp18sth14qii3pnvodkvt| The ID of the VPC.

 |
|VpcName|String|doctest2| The name of the VPC.

 |

## Examples {#section_zvp_gtt_4fb .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=DescribeVpcAttribute
&RegionId=cn-hangzhou
&VpcId=vpc-bp18sth14qii3pnvodkvt
&<CommonParameters>

```

**Response example**

-   **XML format**

    ``` {#xml_return_success_demo}
    <DescribeVpcAttributeResponse>
      <VpcName>doctest2</VpcName>
      <Description/>
      <IsDefault>false</IsDefault>
      <ResourceGroupId>rg-acfmxazb4ph6aiy</ResourceGroupId>
      <UserCidrs/>
      <ClassicLinkEnabled>false</ClassicLinkEnabled>
      <AssociatedCens>
        <AssociatedCen>
          <CenStatus>Attached</CenStatus>
          <CenOwnerId>1231579085529123</CenOwnerId>
          <CenId>cen-7qthudw0ll6jmc4gsu</CenId>
        </AssociatedCen>
      </AssociatedCens>
      <VRouterId>vrt-bp1jso6ng1at0ajsc8mbe</VRouterId>
      <VpcId>vpc-bp18sth14qii3pnvodkvt</VpcId>
      <CreationTime>2018-10-16T07:31:09Z</CreationTime>
      <CidrBlock>192.168.0.0/16</CidrBlock>
      <Status>Available</Status>
      <VSwitchIds>
        <VSwitchId>vsw-bp14cagpfysr29feg5t97</VSwitchId>
      </VSwitchIds>
      <RequestId>7486AE4A-129D-43DB-A714-2432C074BA04</RequestId>
      <RegionId>cn-hangzhou</RegionId>
      <CloudResources>
        <CloudResourceSetType>
          <ResourceType>VSwitch</ResourceType>
          <ResourceCount>1</ResourceCount>
        </CloudResourceSetType>
        <CloudResourceSetType>
          <ResourceType>VRouter</ResourceType>
          <ResourceCount>1</ResourceCount>
        </CloudResourceSetType>
        <CloudResourceSetType>
          <ResourceType>RouteTable</ResourceType>
          <ResourceCount>1</ResourceCount>
        </CloudResourceSetType>
      </CloudResources>
    </DescribeVpcAttributeResponse>
    
    ```

-   **JSON format**

    ``` {#json_return_success_demo}
    {
    	"VpcName":"doctest2",
    	"Description":"",
    	"IsDefault":false,
    	"ResourceGroupId":"rg-acfmxazb4ph6aiy",
    	"UserCidrs":{
    		"UserCidr":[]
    	},
    	"ClassicLinkEnabled":false,
    	"AssociatedCens":{
    		"AssociatedCen":[
    			{
    				"CenStatus":"Attached",
    				"CenOwnerId":"1231579085529123",
    				"CenId":"cen-7qthudw0ll6jmc4gsu"
    			}
    		]
    	},
    	"VRouterId":"vrt-bp1jso6ng1at0ajsc8mbe",
    	"VpcId":"vpc-bp18sth14qii3pnvodkvt",
    	"CreationTime":"2018-10-16T07:31:09Z",
    	"CidrBlock":"192.168.0.0/16",
    	"Status":"Available",
    	"VSwitchIds":{
    		"VSwitchId":[
    			"vsw-bp14cagpfysr29feg5t97"
    		]
    	},
    	"RegionId":"cn-hangzhou",
    	"RequestId":"7486AE4A-129D-43DB-A714-2432C074BA04",
    	"CloudResources":{
    		"CloudResourceSetType":[
    			{
    				"ResourceType":"VSwitch",
    				"ResourceCount":1
    			},
    			{
    				"ResourceType":"VRouter",
    				"ResourceCount":1
    			},
    			{
    				"ResourceType":"RouteTable",
    				"ResourceCount":1
    			}
    		]
    	}
    }
    ```


## Error codes {#section_tkt_2hr_pgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|500|InternalError|The request processing has failed due to some unknown error.|An error occurred while the request was being processed.|
|400|IncorrectVpcStatus|Current VPC status does not support this operation.|The status of VPC does not support this action.|
|404|InvalidVpcId.NotFound|Specified VPC does not exist.|The specified VPC does not exist.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

