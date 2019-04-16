# DeleteVpc {#reference_i4w_xmt_ndb .reference}

Deletes a VPC.

Note the following before deleting a VPC:

-   You must release or remove all resources in the VPC, such as VSwitches, instances, router interfaces, and HaVip.

-   Only VPCs in the available status can be deleted.


## Debug {#apiExplorer .section}

By using [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=CreateLoadBalancer), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|DeleteVpc| The name of this action. Value:

 DeleteVpc

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the VPC belongs.

 |
|VpcId|String|Yes|vpc-123456| The ID of the VPC.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|-------------|:----------|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|The ID of the request.|

## Examples {#section_ix5_h1g .section}

**Request example**

``` {#request}

https://vpc.aliyuncs.com/?Action=DeleteVpc
&VpcId= vpc-123456
&<CommonParameters>

```

**Response example**

-   XML format

    ``` {#xml_return_success_demo}
    <DeleteVpcResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
    </DeleteVpcResponse>
    
    ```

-   JSON format

    ``` {#json_return_success_demo}
    {
    	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
    }
    ```


## Error codes {#section_mzm_zsp_pgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|OperationDenied|The operation is not supported in this status.|This operation cannot be performed in this status.|
|403|OperationDenied|The snapshot creation for the specified disk is not finished yet.|The snapshot creation of the disk has not been completed yet.|
|400|IncorrectVpcStatus|Current VPC status does not support this operation.|The current status of VPC does not support this action.|
|400|DependencyViolation.RouteEntry|Specified object has dependent resources|The specified operation failed to delete the VPC due to the custom route entries added to the VPC.|
|400|DependencyViolation.Instance|Specified object has dependent resources|The specified object has associated resources.|
|400|DependencyViolation.VSwitch|Specified object has dependent resources|This VPC has dependent VSwitches and cannot be deleted. Delete all VSwitches in the VPC first.|
|400|DependencyViolation.SecurityGroup|Specified object has dependent resources|This VPC has dependent security groups and cannot be deleted. Delete all security groups in the VPC first.|
|404|InvalidVpcId.NotFound|Specified VPC does not exist.|The specified VPC does not exist.|
|400|DependencyViolation.RouteInterface|Specified object has dependent route interface .|The specified VSwitch has a router interface connected and cannot be deleted.|
|400|DependencyViolation.Tunnel|Specified object has dependent tunnel.|The specified object has associated tunnels.|
|500|InternalError|The request processing has failed due to some unknown error.|An error occurred while the request was being processed.|
|400|DependencyViolation.NatGateway|Specified object has dependent resources NatGateway.|The dependent NAT Gateway must be deleted first before the specified VPC can be deleted.|
|400|DependencyViolation.RouterInterface|Specified object has dependent resources RouterInterface.|The specified object has associated router interfaces.|
|400|DependencyViolation.SecurityGroup|Specified object has dependent resources SecurityGroup.|This VPC has dependent security groups and cannot be deleted. Delete all security groups in the VPC first.|
|400|Forbidden.VpcNotFound|Specified VPC can not found.|The specified VPC does not exist.|
|400|Forbbiden|Active custom route in vpc.|You need to add a custom route entry in the VPC.|

[See common errors](https://error-center.aliyun.com/status/product/Vpc)

