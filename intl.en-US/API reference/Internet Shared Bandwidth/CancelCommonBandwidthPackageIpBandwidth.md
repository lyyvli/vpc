# CancelCommonBandwidthPackageIpBandwidth {#doc_api_Vpc_CancelCommonBandwidthPackageIpBandwidth .reference}

Cancels the bandwidth limit that is configured for an EIP added to an Internet Shared Bandwidth.

After you cancel the bandwidth limit, the peak bandwidth of the EIP is the same as that of the Internet Shared Bandwidth.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Vpc&api=CancelCommonBandwidthPackageIpBandwidth) to perform debug operations and generate code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CancelCommonBandwidthPackageIpBandwidth|The name of this action. Value: **CancelCommonBandwidthPackageIpBandwidth**.

 |
|BandwidthPackageId|String|Yes|cbwp-bp13d0m4e2qv8xxxxxxxx|The ID of the Internet Shared Bandwidth instance.

 |
|EipId|String|Yes|eip-2zewysoansu0sxxxxxxxx|The ID of the EIP instance added to the Internet Shared Bandwidth.

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the Internet Shared Bandwidth belongs. To query the region ID, call [DescribeRegions](~~36063~~).

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|63D187BF-A30A-4DD6-B68D-FF182C96D8A2|The ID of the request. 

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CancelCommonBandwidthPackageIpBandwidth
&BandwidthPackageId=cbwp-bp13d0m4e2qv8xxxxxxxx 
&EipId=eip-2zewysoansu0sxxxxxxxx 
&RegionId=cn-hangzhou 
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<CancelCommonBandwidthPackageIpBandwidth>
  <RequestId>63D187BF-A30A-4DD6-B68D-FF182C96D8A2</RequestId> 
</CancelCommonBandwidthPackageIpBandwidth> 

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"63D187BF-A30A-4DD6-B68D-FF182C96D8A2"
}
```

## Error codes { .section}

|HTTP status code|Error code|Error message |Description|
|----------------|----------|--------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

