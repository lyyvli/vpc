# AssociateGlobalAccelerationInstance {#doc_api_Vpc_AssociateGlobalAccelerationInstance .reference}

调用AssociateGlobalAccelerationInstance接口为独享型实例绑定后端服务器。

调用本接口绑定后端服务实例时，请注意：

-   仅支持专有网络类型的ECS实例和负载均衡实例作为全球加速实例的后端服务实例。
-   一个全球加速实例只能添加一个后端服务实例。
-   多个全球加速实例可以绑定同一个后端服务实例。
-   后端服务实例和全球加速实例需要属于同一个云账号。
-   绑定的后端服务器的地域必须在全球加速实例的服务区域内。
-   只有独享型全球加速实例支持通过该API绑定后端服务。

共享型全球加速实例绑定后端服务器的操作如下：

1. 将EIP加入到共享型全球加速实例。详细信息，请参见[AddGlobalAccelerationInstanceIp](~~127807~~)。

2. 将EIP绑定到后端服务器。详细信息，请参见[AssociateEipAddress](~~120195~~)，调用AssociateEipAddress接口时必须指定**InstanceRegionId**参数。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=AssociateGlobalAccelerationInstance&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AssociateGlobalAccelerationInstance|要执行的操作，取值：**AssociateGlobalAccelerationInstance**。

 |
|BackendServerId|String|是|i-saf23\*\*\*\*|后端服务实例的ID。

 |
|BackendServerRegionId|String|是|cn-shanghai|后端服务实例所属的地域，该地域需要属于全球加速实例指定的服务区域。

 |
|GlobalAccelerationInstanceId|String|是|ga-lsajj32\*\*\*\*|全球加速实例的ID。

 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|BackendServerType|String|否|EcsInstance|后端服务实例的类型，取值：

 -   **EcsInstance**（默认值）：ECS实例。
-   **SlbInstance**：负载均衡实例。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|DDF2CC38-76C7-4000-909D-B2088158AEDA|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=AssociateGlobalAccelerationInstance
&BackendServerId=i-saf23****
&BackendServerRegionId=cn-shanghai
&GlobalAccelerationInstanceId=ga-lsajj32****
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AssociateGlobalAccelerationInstanceResponse>
      <RequestId>DDF2CC38-76C7-4000-909D-B2088158AEDA</RequestId>
</AssociateGlobalAccelerationInstanceResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"DDF2CC38-76C7-4000-909D-B2088158AEDA"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidGlobalAccelerationInstanceId.NotFound|The specified GlobalAccelerationInstanceId is not found.|全球加速实例不存在。|
|404|InvalidBackendServerId.NotFound|The specified BackendServerId is not found.|后端服务器实例不存在，请您检查后端服务器实例是否正确。|
|400|IncorrectGlobalAccelerationInstanceIdStatus|Current GlobalAccelerationInstance status does not support this operation.|指定的全球加速实例状态不支持此操作|
|400|InvalidBackendServerId.NotInVPC|The specified BackendServerId is not in VPC.|指定的 BackendServerId 不是 VPC 类型。|
|400|TaskConflict.AssociateGlobalAccelerationInstance|Operate too frequent.|操作过于频繁。|
|400|InvalidBackendServerRegionId.EqualRegionId|The specified BackendServerRegionId can not be the same as RegionId.|指定的 BackendServerRegionId 不能与 RegionId 相同。|
|400|InvalidAssociation.Duplicated|Specified instance already is associated.|该实例已绑定 EIP 或 全球加速实例，不能再绑定，如需更换实例绑定的 EIP 或全球加速实例，请先解绑。|
|400|InvalidBackendServerType.NotFound|The specified BackendServerType is not supported.|指定的后端服务器类型不支持。|
|400|InvalidParameter|The specified parameter is not valid.|该参数值不合法。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

