# DeleteCommonBandwidthPackage {#doc_api_Vpc_DeleteCommonBandwidthPackage .reference}

调用DeleteCommonBandwidthPackage接口删除共享带宽实例。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DeleteCommonBandwidthPackage&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteCommonBandwidthPackage|要执行的操作。 取值：

 **DeleteCommonBandwidthPackage**。

 |
|BandwidthPackageId|String|是|cbwp-2ze2ic1xd2qeqk145pn4u|共享带宽实例的ID。

 |
|RegionId|String|是|cn-hangzhou|共享带宽实例所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|Force|String|否|false|是否强制删除共享带宽实例。取值：

 -   **false**（默认值）：只删除不包含EIP的共享带宽。
-   **true**：将共享带宽实例中的EIP全部移出后，删除共享带宽。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|B400EF57-60E3-4D61-B8FB-7FA8F72DF5A6|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DeleteCommonBandwidthPackage
&BandwidthPackageId=cbwp-2ze2ic1xd2qeqk145pn4u
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteCommonBandwidthPackageResponse>
      <RequestId>B400EF57-60E3-4D61-B8FB-7FA8F72DF5A6</RequestId>
</DeleteCommonBandwidthPackageResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"B400EF57-60E3-4D61-B8FB-7FA8F72DF5A6"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

