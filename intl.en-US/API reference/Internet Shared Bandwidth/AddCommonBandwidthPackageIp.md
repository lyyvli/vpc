# AddCommonBandwidthPackageIp {#doc_api_Vpc_AddCommonBandwidthPackageIp .reference}

Adds an EIP to an Internet Shared Bandwidth instance.

Note the following before you call this action:

-   Only Pay-As-You-Go EIPs can be added.
-   The EIP and the Internet Shared Bandwidth instance must be in the same region.

## Debug {#apiExplorer .section}

Use [API Explorer](https://api.aliyun.com/#product=Vpc&api=AddCommonBandwidthPackageIp) to perform debug operation and generate code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|AddCommonBandwidthPackageIp|The name of this action. Value: **AddCommonBandwidthPackageIp**.

 |
|BandwidthPackageId|String|Yes|cbwp-2ze2ic1xd2qeqxxxxxxxx|The ID of the Internet Shared Bandwidth instance.

 |
|IpInstanceId|String|Yes|eip-2zeerraiwb7uxxxxxxxx|The ID of the EIP instance.

 To query the ID of the EIP instance, call [DescribeEipAddresses](~~36018~~).

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the Internet Shared Bandwidth instance is located.

 To query the region ID, call [DescribeRegions](~~36063~~) .

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|EC0A01C5-62E2-4E50-B558-CDAA09094B96|The ID of the request. 

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=AddCommonBandwidthPackageIp
&BandwidthPackageId=cbwp-2ze2ic1xd2qeqxxxxxxxx 
&IpInstanceId=eip-2zeerraiwb7ujxxxxxxxx 
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<AddCommonBandwidthPackageIpResponse>
  <RequestId>01FDDD49-C4B7-4D2A-A8E5-A93915C450A6</RequestId>
</AddCommonBandwidthPackageIpResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId": "01FDDD49-C4B7-4D2A-A8E5-A93915C450A6"
}
```

## Error codes { .section}

|HTTP status code|Error code|Error message |Description|
|----------------|----------|--------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|404|InvalidBandwidthPackageId.NotFound|The specified bandwidthPackageId does not exist in our records.|The specified Internet Shared Bandwidth does not exist.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

