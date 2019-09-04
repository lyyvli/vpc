# AssociateGlobalAccelerationInstance {#doc_api_Vpc_AssociateGlobalAccelerationInstance .reference}

Associates a backend server instance with a Global Acceleration instance.

Note the following before you call this API action:

-   Only a VPC ECS instance or a VPC SLB instance can act as a backend server instance of the Global Acceleration instance.
-   Each Global Acceleration instance can be associated with only one backend server instance.
-   Multiple Global Acceleration instances can be associated with the same backend server instance.
-   The Global Acceleration instance and the backend server instance must belong to the same account.
-   The region to which the backend server instance belongs must be in the service area of the Global Acceleration instance.
-   Only a dedicated-bandwidth Global Acceleration instance can be associated with a backend server instance through this API.

To associate a shared-bandwidth Global Acceleration instance with a backend server instance, follow these steps:

1. Add an EIP to the shared-bandwidth Global Acceleration instance. For more information, see [AddGlobalAccelerationInstanceIp](~~86045~~).

2. Associate the EIP with the backend server instance. For more information, see [AssociateEipAddress](~~120195~~). When you call AssociateEipAddress, you must specify the **InstanceRegionId** parameter.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=AssociateGlobalAccelerationInstance&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|AssociateGlobalAccelerationInstance|The name of this action. Value: **AssociateGlobalAccelerationInstance**

 |
|BackendServerId|String|Yes|i-saf23\*\*\*\*|The ID of the backend service instance.

 |
|BackendServerRegionId|String|Yes|cn-shanghai|The region to which the backend server instance belongs. This region must belong to the service area of the Global Acceleration instance.

 |
|GlobalAccelerationInstanceId|String|Yes|ga-lsajj32\*\*\*\*|The ID of the Global Acceleration instance.

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the Global Acceleration instance belongs. To query the region ID, call [DescribeRegions](~~36063~~).

 |
|BackendServerType|String|No|EcsInstance|Optional. The type of the backend server instance. Valid values:

 -   **EcsInstance** \(default\): ECS instance
-   **SlbInstance**: SLB instance

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|DDF2CC38-76C7-4000-909D-B2088158AEDA|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=AssociateGlobalAccelerationInstance
&BackendServerId=i-saf23****
&BackendServerRegionId=cn-shanghai
&GlobalAccelerationInstanceId=ga-lsajj32****
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<AssociateGlobalAccelerationInstanceResponse>
      <RequestId>DDF2CC38-76C7-4000-909D-B2088158AEDA</RequestId>
</AssociateGlobalAccelerationInstanceResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"DDF2CC38-76C7-4000-909D-B2088158AEDA"
}
```

## Errors { .section}

|HTTP status code|Error code|Error message |Description|
|----------------|----------|--------------|-----------|
|404|InvalidGlobalAccelerationInstanceId.NotFound|The specified GlobalAccelerationInstanceId is not found.|The specified Global Acceleration instance does not exist.|
|404|InvalidBackendServerId.NotFound|The specified BackendServerId is not found.|The specified backend server instance does not exist.|
|400|IncorrectGlobalAccelerationInstanceIdStatus|Current GlobalAccelerationInstance status does not support this operation.|The status of the specified Global Acceleration instance does not support this operation.|
|400|InvalidBackendServerId.NotInVPC|The specified BackendServerId is not in VPC.|The specified BackendServerId is not of the VPC type.|
|400|TaskConflict.AssociateGlobalAccelerationInstance|Operate too frequent.|Too many requests were sent.|
|400|InvalidBackendServerRegionId.EqualRegionId|The specified BackendServerRegionId can not be the same as RegionId.|The specified BackendServerRegionId cannot be the same as the RegionId.|
|400|InvalidAssociation.Duplicated|Specified instance already is associated.|The specified instance is already associated with an EIP or a Global Acceleration instance. You must detach this instance before you can associate it with another EIP or Global Acceleration instance.|
|400|InvalidBackendServerType.NotFound|The specified BackendServerType is not supported.|The type of the specified backend server instance is not supported.|
|400|InvalidParameter|The specified parameter is not valid.|The specified parameter value is invalid.|

