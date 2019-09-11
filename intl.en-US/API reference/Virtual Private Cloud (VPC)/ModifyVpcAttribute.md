# ModifyVpcAttribute {#doc_api_Vpc_ModifyVpcAttribute .reference}

Modifies the name and description of a VPC.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Vpc&api=ModifyVpcAttribute) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Required|ModifyVpcAttribute| The name of this action. Value: **ModifyVpcAttribute**.

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the VPC belongs.

 |
|VpcId|String|Yes|vpc-bp1qtbach57ywecfxxxxxx| The ID of the VPC.

 |
|CidrBlock|String|No|192.168.0.0/24| The CIDR block of the VPC.

 |
|Description|String|No|This is VPC1.| The description of the VPC. The description must be 2 to 256 characters in length. It must start with a letter but cannot start with `http://` or `https://`.

 |
|EnableIPv6|Boolean|No|true| Indicates whether to enable IPv6 CIDR blocks. Valid values:

 -   **true**: Enable.
-   **false**: Do not enable.

 |
|VpcName|String|No|Vpc-1| The name of the VPC. The instance name must be 2 to 128 characters in length and can contain letters, numbers, periods \(.\), underscores \(\_\), and hyphens \(-\). The name must start with a letter. It cannot start with `http://` or `https://`.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyVpcAttribute
&VpcId=vpc-bp1qtbach57ywecfxxxxxx
&VpcName=Vpc-1
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<ModifyVpcAttributeResponse>
  <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</ModifyVpcAttributeResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"43B72D30-25E1-4FA3-96A8-89374A521D1A"
}
```

## Error codes {#section_psm_hyw_ltn .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidVpcId.NotFound|Specified VPC does not exist.|The specified VPC does not exist.|
|400|InvalidVpcName.Malformed|Specified VPC name is not valid.|The name format of the specified VPC is invalid.|
|400|InvalidVpcDiscription.Malformed|Specified VPC description is not valid.|The format of the specified VPC description is invalid.|
|400|InvalidParameter|Specified UserCidr invalid format.|The format of the specified UserCidr is invalid.|
|400|InvalidParameter|Specified UserCidr Subnet mask is not valid.|The specified subnet mask for UserCidr is invalid.|
|400|InvalidUserCidr.Quota|Specified UserCidr number is greater than 3.|The number of UserCidrs has reached the quota.|
|400|InvalidUserCidr.Malformed|Specified UserCidr overlapping in of 100.64.0.0/10.|The specified UserCidr overlaps with 100.64.0.0/10.|
|400|IncorrectVpcStatus|Current VPC status does not support this operation.|The current VPC status does not support this operation.|
|400|InvalidCidrBlock.Malformed|Specified CIDR block is not valid.|The format of the specified CIDR block is invalid.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

