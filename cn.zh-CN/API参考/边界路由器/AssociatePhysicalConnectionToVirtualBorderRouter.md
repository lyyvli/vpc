# AssociatePhysicalConnectionToVirtualBorderRouter {#doc_api_Vpc_AssociatePhysicalConnectionToVirtualBorderRouter .reference}

调用AssociatePhysicalConnectionToVirtualBorderRouter将VBR关联物理专线。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=AssociatePhysicalConnectionToVirtualBorderRouter&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AssociatePhysicalConnectionToVirtualBorderRouter|要执行的操作。

 取值：**AssociatePhysicalConnectionToVirtualBorderRouter**。

 |
|PhysicalConnectionId|String|是|pc-bp1qrb3044eqixog\*\*\*\*|物理专线ID。

 |
|RegionId|String|是|cn-hangzhou|物理专线实例所在的地域ID。

 |
|VbrId|String|是|vbr-bp186tnz6rijyhj\*\*\*\*\*\*|边界路由器ID。

 |
|VlanId|String|是|123|VBR的VLAN ID。

 取值范围为：1-2999。

 **说明：** 只有物理专线的所有者可以指定该参数，同一条物理专线下的两个VBR的VLAN ID不能相同。

 |
|CircuitCode|String|否|longtel001|运营商为物理专线提供的电路编码。

 **说明：** 只有物理专线的所有者可以指定该参数。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-00xxxxxxxx|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。

 |
|LocalGatewayIp|String|否|10.10.0.1|VBR的阿里云侧互联IP。

 |
|PeerGatewayIp|String|否|10.10.10.9|VBR专线侧接口对端的IP地址。

 该属性只允许VBR owner指定/修改，不允许把Enabled状态的VBR的该属性改为空。

 |
|PeeringSubnetMask|String|否|255.255.255.0|VBR的阿里云侧和客户侧互联IP的子网掩码。

 两个IP地址必须位于同一个子网中。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|980960B0-2969-40BF-8542-EBB34FD358AB|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=AssociatePhysicalConnectionToVirtualBorderRouter
&PhysicalConnectionId= pc-bp1qrb3044eqixog****
&RegionId=cn-hangzhou
&VbrId=vbr-bp186tnz6rijyhj******
&VlanId=123
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AssociatePhysicalConnectionToVirtualBorderRouterResponse>
	  <RequestId>980960B0-2969-40BF-8542-EBB34FD358AB</RequestId>
    </AssociatePhysicalConnectionToVirtualBorderRouterResponse>
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
|404|InvalidInstanceId.NotFound|The specified Instance does not exist in the specified region.|该实例在该地域内不存在。|
|404|InvalidVbrId.NotFound|The specified VirutalBorderRouter does not exist in our records.|该边界路由器不存在，请您检查输入的边界路由器是否正确。|
|400|InvalidOperation.RouterInterfaceNotDeleted|The specified VirutalBorderRouter still has routerInterface.|该边界路由器还有关联的路由器接口。|
|400|InvalidOperation.OperationNotAllowedInState|The specified VirutalBorderRouter is in invalid state.|该VirutalBorderRouter状态不合法，请检查VirutalBorderRouter状态。|
|403|Forbidden.OperationNotAllowedByUser|The caller is not allowed to delete the specified VirtualBorderRouter.|不允许删除边界路由器。|
|403|Forbidden.MultiVlanRi|Multiple vlan router interfaces are found.|存在多个VLAN路由器接口。|
|403|Forbidden.NoRiFound|No vlan router interfaces are found.|没有可用的VLAN路由器接口。|
|400|InvalidStatus.NotAllowed|Invalid virtual border router status.|当前边界路由器的状态不支持该操作。|
|404|InvalidRegionId.NotFound|The specified RegionId is not found.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|InvalidPhysicalConnectionId.NotFound|The specified PhysicalConnectionId is not found.|该物理专线Id不存在。|
|400|InvalidVlanId.Used|The specified VlanId has been used.|该VLAN已经被占用。|
|400|MissingParameter|The input parameter 'PhysicalConnectionId' that is mandatory for processing this request is not supplied.|必须指定参数PhysicalConnectionId。|
|400|InvalidPhysicalConnectionId.NotEnabled|The specified PhysicalConnectionId is not in Enabled state.|该物理专线当前未处于正常状态，请检查物理专线后再创建。|
|404|InvalidVbrOwnerId.NotFound|The specified VbrOwnerId is not valid.|参数VbrOwnerId的值不合法。|
|400|MissingParameter|The input parameter 'VlanId' that is mandatory for processing this request is not supplied.|必须指定参数VlanId。|
|400|InvalidVlanId.Malformed|The specified VlanId is not valid.|参数VlanId的值不合法。|
|400|InvalidCircuitCode.Malformed|The specified CircuitCode is not valid.|该CircuitCode不合法。|
|400|MissingParameter|The input parameter 'LocalGatewayIp' that is mandatory for processing this request is not supplied.|必须指定参数LocalGatewayIp。|
|400|InvalidLocalGatewayIp.Malformed|The specified LocalGatewayIp is not valid.|该本端网关的IP不合法。|
|400|MissingParameter|The input parameter 'PeerGatewayIp' that is mandatory for processing this request is not supplied.|必须指定参数PeerGatewayIp。|
|400|InvalidPeerGatewayIp.Malformed|The specified PeerGatewayIp is not valid.|参数PeerGatewayIp的值不合法。|
|400|MissingParameter|The input parameter 'PeeringSubnetMask' that is mandatory for processing this request is not supplied.|必须指定参数PeeringSubnetMask。|
|400|InvalidPeeringSubnetMask.Malformed|The specified PeeringSubnetMask is not valid.|指定的 PeeringSubnetMask 不合法，请您检查该参数是否正确。|
|403|Forbidden.LocalGatewayIpNotAllowedByCaller|The caller is not allowed to specify the LocalGatewayIp parameter.|不允许指定LocalGatewayIp参数。|
|403|Forbidden.PeerGatewayIpNotAllowedByCaller|The caller is not allowed to specify the PeerGatewayIp parameter.|不允许指定PeerGatewayIp参数。|
|403|Forbidden.PeeringSubnetMaskNotAllowedByCaller|The caller is not allowed to specify the PeeringSubnetMask parameter.|不允许指定PeeringSubnetMask参数。|
|403|Forbidden.NameNotAllowedByCaller|The caller is not allowed to specify the Name parameter.|不允许指定Name参数。|
|403|Forbidden.DescriptionNotAllowedByCaller|The caller is not allowed to specify the Description parameter.|不允许指定Description参数。|
|400|InvalidName.Malformed|The specified ?Name? is not valid.|该名称格式不合法。|
|400|InvalidDescription.Malformed|The specifid ?Description? is not valid.|指定的资源描述格式不合法。长度为2-256个字符，不能以 http:// 和 https:// 开头。|
|400|QuotaExceeded.vbrPerpConn|Virtual boarder router per PhysicalConnection quota exceed.|超过了每个物理专线上的边界路由器配额上限，请您减少该物理专线上的边界路由器数量后再试。|
|400|EXCEED\_ASSOCIATE\_MAX\_NUM|assocaite virtual boarder num too many.|关联的边界路由器达到配额上限。|
|400|InvalidIP.Malformed|Ip malformed.|IP格式不合法。|
|400|InvalidIp.NotSameSubnet|Local gateway ip and peer gateway ip are not in the same subnet.|本地网关 IP 地址与对端网关 IP 地址不在同一个子网内。|
|400|InvalidStatus.StatusNotEnabled|The physical connection status is invalid.|物理专线状态不支持此操作，请检查物理专线状态。|
|400|PHYSICAL\_NOT\_ALLOW\_ASSOCIATE\_VBR|The specified operation not allow.|无法执行该操作，物理专线有关联的边界路由器。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

