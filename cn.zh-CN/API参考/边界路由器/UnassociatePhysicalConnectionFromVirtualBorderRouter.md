# UnassociatePhysicalConnectionFromVirtualBorderRouter {#doc_api_Vpc_UnassociatePhysicalConnectionFromVirtualBorderRouter .reference}

调用UnassociatePhysicalConnectionFromVirtualBorderRouter解绑VBR和物理专线。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=UnassociatePhysicalConnectionFromVirtualBorderRouter&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UnassociatePhysicalConnectionFromVirtualBorderRouter|要执行的操作。

 取值：**UnassociatePhysicalConnectionFromVirtualBorderRouter**。

 |
|PhysicalConnectionId|String|是|pc-bp1qrb3044eqixog\*\*\*\*|物理专线ID。

 |
|RegionId|String|是|cn-hangzhou|物理专线实例所在的地域ID。

 |
|VbrId|String|是|vbr-bp16ksp61j7e0tkn\*\*\*\*\*|VBR的VLAN ID，取值范围为：1-2999。

 **说明：** 只有物理专线的所有者可以指定该参数，同一条物理专线下的两个VBR的VLAN ID不能相同。

 |
|ClientToken|String|否|longtel001|运营商为物理专线提供的电路编码。

 **说明：** 只有物理专线的所有者可以指定该参数。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|980960B0-2969-40BF-8542-EBB34FD358AB|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=UnassociatePhysicalConnectionFromVirtualBorderRouter
&PhysicalConnectionId=pc-bp1qrb3044eqixog****
&RegionId=cn-hangzhou
&VbrId=vbr-bp16ksp61j7e0tkn*****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UnassociatePhysicalConnectionFromVirtualBorderRouterResponse>
	  <RequestId>980960B0-2969-40BF-8542-EBB34FD358AB</RequestId>
    </UnassociatePhysicalConnectionFromVirtualBorderRouterResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"980960B0-2969-40BF-8542-EBB34FD358AB"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidVbrId.NotFound|The specified VirutalBorderRouter does not exist in our records.|该边界路由器不存在，请您检查输入的边界路由器是否正确。|
|404|InvalidVbrId.NotFound|The specified VirutalBorderRouter or PhysicalConnection does not exist in our records.|该边界路由器或物理专线不存在。|
|400|PARAMETER\_MUST\_NOT\_NULL|The specified physical connection id or vbrId must not be null.|必须指定参数vbrId和physicalconnectionId。|
|400|PHYSICAL\_NOT\_ASSOCIATE\_TO\_VBR|The specified PhysicalConnection have not associate to the vbr.|该物理专线没有创建边界路路由器。|
|400|ROUTER\_INTERFACE\_REFERED\_BY\_ROUTEENTRY|The specified VlanInterface has been used by routeEntry.|该VLAN接口已经使用在路由条目中。|
|400|InvalidStatus.NotAllowed|Invalid virtual border router status.|当前边界路由器的状态不支持该操作。|
|400|PHYSICAL\_NOT\_ALLOW\_ASSOCIATE\_VBR|The specified operation not allow.|无法执行该操作，物理专线有关联的边界路由器。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

