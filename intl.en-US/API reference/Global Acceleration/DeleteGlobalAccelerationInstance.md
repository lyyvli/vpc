# DeleteGlobalAccelerationInstance {#reference_i4w_xmt_ndb .reference}

Deletes a Global Acceleration instance.

Note the following before you call this action:

-   Only Pay-As-You-Go instances can be deleted.
-   If you want to delete a dedicated-bandwidth instance, you must first detach the backend server before deleting the instance.
-   If you want to delete a shared-bandwidth instance, you must first disassociate the EIP or EIPs before deleting the instance.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description |
|:--------|:---|:--------|:------------|:-----------|
|Action|String|Yes|DeleteGlobalAccelerationInstance| The name of this action.  Value: 

 DeleteGlobalAccelerationInstance

 |
|GlobalAccelerationInstanceId|String|Yes|ga-asdfsl22sxxxxx| The ID of the Global Acceleration instance.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region where the Global Acceleration instance is located.

 To query the region ID, call DescribeRegions.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|:------------|:----------|
|RequestId|String|E6E63B2A-9820-44A8-A359-9BB2DAEE6424|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=DeleteGlobalAccelerationInstance
&GlobalAccelerationInstanceId=ga-asdfsl22sxxxxx
&RegionId=cn-hangzhou
&<CommonParameters>

```

**Response example**

XML format

```
<DeleteGlobalAccelerationInstanceResponse>
  <RequestId>E6E63B2A-9820-44A8-A359-9BB2DAEE6424</RequestId>
</DeleteGlobalAccelerationInstanceResponse>

```

JSON format

```
{
	"RequestId":"E6E63B2A-9820-44A8-A359-9BB2DAEE6424"
}
```

## Error codes {#section_lwx_dh3_wgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|IncorrectGlobalAccelerationInstanceIdStatus|Current GlobalAccelerationInstance status does not support this operation.|The specified Global Acceleration instance does not support this operation.|
|400|InvalidGlobalAccelerationInstanceId.NotFound|The specified GlobalAccelerationInstanceId is not found.|The specified Global Acceleration instance does not exist.|
|400|IncorrectStatus|This openeration would be allowed only when status of this RouterInterface is Idle/Inactive.|This operation is not permitted because the associated router interface is not in the Idle or Inactive state.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

