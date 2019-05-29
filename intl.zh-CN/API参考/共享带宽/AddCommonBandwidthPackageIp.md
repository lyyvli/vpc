# AddCommonBandwidthPackageIp {#doc_api_Vpc_AddCommonBandwidthPackageIp .reference}

调用AddCommonBandwidthPackageIp接口添加EIP到共享带宽中。

调用本接口添加EIP时，请注意：

-   只支持添加后付费的EIP。
-   EIP和共享带宽的地域必须相同。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=AddCommonBandwidthPackageIp)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddCommonBandwidthPackageIp|要执行的操作，取值： **AddCommonBandwidthPackageIp**。

 |
|BandwidthPackageId|String|是|cbwp-2ze2ic1xd2qeqxxxxxxxx|共享带宽的ID。

 |
|IpInstanceId|String|是|eip-2zeerraiwb7uxxxxxxxx|EIP实例的ID。

 您可以通过调用[DescribeEipAddresses](~~36018~~)接口查询EIP实例的ID。

 |
|RegionId|String|是|cn-hangzhou|共享带宽所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|EC0A01C5-62E2-4E50-B558-CDAA09094B96|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=AddCommonBandwidthPackageIp
&BandwidthPackageId=cbwp-2ze2ic1xd2qeqxxxxxxxx
&IpInstanceId=eip-2zeerraiwb7ujxxxxxxxx
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddCommonBandwidthPackageIpResponse>
  <RequestId>01FDDD49-C4B7-4D2A-A8E5-A93915C450A6</RequestId>
</AddCommonBandwidthPackageIpResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"01FDDD49-C4B7-4D2A-A8E5-A93915C450A6"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|404|InvalidBandwidthPackageId.NotFound|The specified bandwidthPackageId does not exist in our records.|该共享带宽包不存在，请您检查输入参数是否正确。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

