# CreateCommonBandwidthPackage {#doc_api_Vpc_CreateCommonBandwidthPackage .reference}

调用CreateCommonBandwidthPackage接口创建共享带宽实例。

请确保在使用该接口前，已充分了解该产品的[计费](~~89732~~)。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CreateCommonBandwidthPackage)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateCommonBandwidthPackage|要执行的操作。 取值：

 **CreateCommonBandwidthPackage**。

 |
|Bandwidth|Integer|是|5|共享带宽的带宽峰值，单位为Mbps。

 |
|RegionId|String|是|cn-hangzhou|共享带宽所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-001xxxxxxxx|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过 64 个 ASCII 字符。

 |
|Description|String|否|描述|共享带宽的描述信息。 长度为 2-256个字符，必须以字母或中文开头，但不能以`http://` 或`https://`开头。

 |
|InternetChargeType|String|否|PayByBandwidth|共享带宽的计费方式，取值：

 -   **PayBy95**：按增强型95计费

 |
|Name|String|否|test123|共享带宽的名称。 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://`或`https://`开头。

 |
|Ratio|Integer|否|100|共享带宽的保底百分比，取值范围为10-100，即保底百分比的范围是10%-100%，选择按增强型95计费时需指定该参数。

 |
|ResourceGroupId|String|否|rg-acfmxazxxxxxxxx|资源组ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|BandwidthPackageId|String|cbwp-bp1vevu8h3iehxxxxxxxx|共享带宽实例的ID。

 |
|RequestId|String|FF39F653-033E-4CD9-9EDF-3CCA5A71FBC3|请求ID。

 |
|ResourceGroupId|String|rsFAF424324-03xxxxxxxx|资源组ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateCommonBandwidthPackage
&Bandwidth=5
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateCommonBandwidthPackageResponse>
  <BandwidthPackageId>cbwp-bp1vevu8h3iehxxxxxxxx</BandwidthPackageId>
  <RequestId>FF39F653-033E-4CD9-9EDF-3CCA5A71FBC3</RequestId>
</CreateCommonBandwidthPackageResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"BandwidthPackageId":"cbwp-bp1vevu8h3iehxxxxxxxx",
	"RequestId":"FF39F653-033E-4CD9-9EDF-3CCA5A71FBC3"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|404|InvalidVpcId.NotFound|Specified value of VpcId is not found in our record.|该 VPC 不存在，请您检查输入的 VPC 是否正确。|
|400|MissingParameter|Miss mandatory parameter.|缺少必要参数,请您检查必填参数是否都已填后再进行操作。|
|404|InvalidZoneId.NotFound|Specified value of ZoneId is not exists.|该可用区不存在。|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|该名称不合法，请您按照正确的格式书写名称。|
|400|InvalidParameter.Description.Malformed|The specified Description is not valid.|该描述不合法。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

