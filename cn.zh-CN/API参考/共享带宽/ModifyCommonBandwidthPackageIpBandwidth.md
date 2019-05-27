# ModifyCommonBandwidthPackageIpBandwidth {#doc_api_Vpc_ModifyCommonBandwidthPackageIpBandwidth .reference}

调用ModifyCommonBandwidthPackageIpBandwidth接口为已经加入共享带宽中的EIP设置最大可用的带宽值。

使用该功能可以灵活地分配加入共享带宽中每个EIP的最大可用带宽值，避免共享带宽的带宽值被某个EIP一直占用。

例如，2个EIP加入一个800Mbps的共享带宽，可以为第一个EIP设置最大可用带宽值为500Mbps，另外一个EIP设置最大可用带宽值为400Mbps。设置完成后，第一个EIP可用的带宽值将不大于500Mbps，第二个EIP可用的带宽值将不大于400Mbps。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=ModifyCommonBandwidthPackageIpBandwidth)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyCommonBandwidthPackageIpBandwidth|要执行的操作，取值：**ModifyCommonBandwidthPackageIpBandwidth**。

 |
|Bandwidth|String|是|500|在共享带宽内最大可分配的带宽值，单位为Mbps。

 |
|BandwidthPackageId|String|是|cbwp-2zep6hw5d6y8exxxxxxxx|共享带宽的实例ID。

 |
|EipId|String|是|eip-2zewysoansu0sxxxxxxxx|已经加入到共享带宽的EIP的实例ID。

 |
|RegionId|String|是|cn-hangzhou|共享带宽所属的地域ID。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|63D187BF-A30A-4DD6-B68D-FF182C96D8A2|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyCommonBandwidthPackageIpBandwidth
&Bandwidth=500
&BandwidthPackageId=cbwp-2zep6hw5d6y8exxxxxxxx
&EipId=eip-2zewysoansu0sxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyCommonBandwidthPackageIpBandwidth>
  <RequestId>63D187BF-A30A-4DD6-B68D-FF182C96D8A2</RequestId>
</ModifyCommonBandwidthPackageIpBandwidth>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"63D187BF-A30A-4DD6-B68D-FF182C96D8A2"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

