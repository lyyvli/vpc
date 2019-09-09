# UnassociatePhysicalConnectionFromVirtualBorderRouter {#doc_api_Vpc_UnassociatePhysicalConnectionFromVirtualBorderRouter .reference}

Disassociates a Virtual Border Router \(VBR\) from a physical connection.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=UnassociatePhysicalConnectionFromVirtualBorderRouter&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String |Yes|UnassociatePhysicalConnectionFromVirtualBorderRouter|The name of this action.

 Value: **UnassociatePhysicalConnectionFromVirtualBorderRouter**

 |
|PhysicalConnectionId|String |Yes|pc-bp1qrb3044eqixog\*\*\*\*|The ID of the physical connection.

 |
|RegionId|String|Yes|cn-hangzhou|The region ID of the physical connection.

 |
|VbrId|String|Yes|vbr-bp16ksp61j7e0tkn\*\*\*\*\*|The VLAN ID of the VBR. Value range: 1 to 2999.

 **Note:** This parameter can only be specified by the owner of the physical connection. The VLAN IDs of two VBRs associated with the same physical connection must be different.

 |
|ClientToken|String|No|longtel001|Optional. The leased line code provided by the service provider for the physical connection.

 **Note:** This parameter can only be specified by the owner of the physical connection.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|980960B0-2969-40BF-8542-EBB34FD358AB|The request ID.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=UnassociatePhysicalConnectionFromVirtualBorderRouter
&PhysicalConnectionId=pc-bp1qrb3044eqixog****
&RegionId=cn-hangzhou
&VbrId=vbr-bp16ksp61j7e0tkn*****
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<UnassociatePhysicalConnectionFromVirtualBorderRouterResponse>
	  <RequestId>980960B0-2969-40BF-8542-EBB34FD358AB</RequestId>
    </UnassociatePhysicalConnectionFromVirtualBorderRouterResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"980960B0-2969-40BF-8542-EBB34FD358AB"
}
```

## Errors { .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidVbrId.NotFound|The specified VirutalBorderRouter does not exist in our records.|The specified VBR does not exist.|
|404|InvalidVbrId.NotFound|The specified VirutalBorderRouter or PhysicalConnection does not exist in our records.|The specified VBR or physical connection does not exist.|
|400|PARAMETER\_MUST\_NOT\_NULL|The specified physical connection id or vbrId must not be null.|The VbrId parameter and the PhysicalConnectionId parameter must be specified.|
|400|PHYSICAL\_NOT\_ASSOCIATE\_TO\_VBR|The specified PhysicalConnection have not associate to the vbr.|No VBR is created for the specified physical connection.|
|400|ROUTER\_INTERFACE\_REFERED\_BY\_ROUTEENTRY|The specified VlanInterface has been used by routeEntry.|The specified VLAN interface is already used in a route entry.|
|400|InvalidStatus.NotAllowed|Invalid virtual border router status.|The status of the VBR does not permit this operation.|
|400|PHYSICAL\_NOT\_ALLOW\_ASSOCIATE\_VBR|The specified operation not allow.|The operation failed because the physical connection is associated with VBRs.|

