# ModifyCommonBandwidthPackageIpBandwidth {#doc_api_Vpc_ModifyCommonBandwidthPackageIpBandwidth .reference}

Configures the bandwidth limit for an EIP added to an Internet Shared Bandwidth.

After this function is used, the bandwidth limits of EIPs added to an Internet Shared Bandwidth can be flexibly allocated.

For example, if two EIPs are added to an Internet Shared Bandwidth of 800 Mbps, you can set the bandwidth limit of the first EIP to 500 Mbps, and set the bandwidth limit of the other EIP to 400 Mbps. After the configuration is complete, the available bandwidth of the first EIP does not exceed 500 Mbps, and the available bandwidth of the second EIP does not exceed 400 Mbps.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Vpc&api=ModifyCommonBandwidthPackageIpBandwidth) to perform debug operations and generate code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|ModifyCommonBandwidthPackageIpBandwidth|The name of this action. Value: **ModifyCommonBandwidthPackageIpBandwidth**.

 |
|Bandwidth|String|Yes|500|The maximum bandwidth that can be allocated from the Internet Shared Bandwidth. Unit: Mbps.

 |
|BandwidthPackageId|String|Yes|cbwp-2zep6hw5d6y8exxxxxxxx|The ID of the Internet Shared Bandwidth instance.

 |
|EipId|String|Yes|eip-2zewysoansu0sxxxxxxxx|The ID of the EIP added to the Internet Shared Bandwidth.

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

https://vpc.aliyuncs.com/?Action=ModifyCommonBandwidthPackageIpBandwidth
&Bandwidth=500
&BandwidthPackageId=cbwp-2zep6hw5d6y8exxxxxxxx
&EipId=eip-2zewysoansu0sxxxxxxxx 
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<ModifyCommonBandwidthPackageIpBandwidth> 
  <RequestId>63D187BF-A30A-4DD6-B68D-FF182C96D8A2</RequestId> 
</ModifyCommonBandwidthPackageIpBandwidth> 

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

