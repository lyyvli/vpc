# CreateVirtualBorderRouter {#doc_api_Vpc_CreateVirtualBorderRouter .reference}

调用CreateVirtualBorderRouter接口新建边界路由器（VBR）。

如果您为本账号创建VBR，创建成功后，VBR的状态为**Enabled**。如果为其他账号创建VBR，创建后VBR的状态为**Unconfirmed**，需要对方账号进行确认。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=CreateVirtualBorderRouter&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateVirtualBorderRouter|要执行的操作。

 取值： **CreateVirtualBorderRouter**。

 |
|PhysicalConnectionId|String|是|pc-xxxxxxxxx|物理专线的ID。

 |
|RegionId|String|是|cn-shanghai|物理专线所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VlanId|Integer|是|10|VBR的VLAN ID，取值范围为：**\[1,2999\]**。

 **说明：** 只有物理专线的所有者可以指定该参数，同一条物理专线下的两个VBR的VLAN ID不能相同。

 |
|CircuitCode|String|否|longtel001|运营商为物理专线提供的电路编码。

 **说明：** 只有物理专线的所有者可以指定该参数。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|Description|String|否|VBR描述信息|VBR的描述信息。

 长度为 2-256个字符，必须以字母或中文开头，但不能以`http://` 或`https://`开头。

 |
|LocalGatewayIp|String|否|116.62.222.XX|VBR的阿里云侧互联IP。

 |
|Name|String|否|test|VBR的名称。

 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://`或`https://`开头。

 |
|PeerGatewayIp|String|否|116.62.222.XX|VBR专线侧接口对端的IP地址。该属性只允许VBR owner指定/修改。为专线所有者创建VBR时必填，为其他账号创建VBR时不可填。

 |
|PeeringSubnetMask|String|否|255.255.255.252|VBR的阿里云侧和客户侧互联IP的子网掩码。 两个IP地址必须位于同一个子网中。

 |
|VbrOwnerId|Long|否|10|VBR所有者的账号ID。 默认为当前用户的账号ID，即为物理专线的所有者创建VBR。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|VbrId|String|vbr-bp1jcg5cmxjbl9xgc\*\*\*\*|VBR的ID。

 |
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=CreateVirtualBorderRouter
&PhysicalConnectionId=pc-xxxxxxxxx
&RegionId=cn-shanghai
&VlanId=10
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateRouterInterfaceResponse>
      <RequestId>980960B0-2969-40BF-8542-EBB34FD358AB</RequestId>
      <VbrId>vbr-2zecmmvg5gvu8i4t****</VbrId>
</CreateRouterInterfaceResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"CreateRouterInterfaceResponse":{
		"RequestId":"980960B0-2969-40BF-8542-EBB34FD358AB",
		"VbrId":"vbr-2zecmmvg5gvu8i4te****"
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId is not found.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|InvalidPhysicalConnectionId.NotFound|The specified PhysicalConnectionId is not found.|该物理专线Id不存在。|
|400|InvalidVlanId.Used|The specified VlanId has been used.|该VLAN已经被占用。|
|400|MissingParameter|The input parameter 'PhysicalConnectionId' that is mandatory for processing this request is not supplied.|必须指定参数PhysicalConnectionId。|
|400|InvalidPhysicalConnectionId.NotEnabled|The specified PhysicalConnectionId is not in Enabled state.|该物理专线当前未处于正常状态，请检查物理专线后再创建。|
|404|InvalidVbrOwnerId.NotFound|The specified VbrOwnerId is not valid.|参数VbrOwnerId的值不合法。|
|400|InvalidVlanId.Malformed|The specified VlanId is not valid.|参数VlanId的值不合法。|
|400|InvalidCircuitCode.Malformed|The specified CircuitCode is not valid.|该CircuitCode不合法。|
|400|MissingParameter|The input parameter 'LocalGatewayIp' that is mandatory for processing this request is not supplied.|必须指定参数LocalGatewayIp。|
|400|InvalidLocalGatewayIp.Malformed|The specified LocalGatewayIp is not valid.|该本端网关的IP不合法。|
|400|MissingParameter|The input parameter 'PeerGatewayIp' that is mandatory for processing this request is not supplied.|必须指定参数PeerGatewayIp。|
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
|400|QuotaExceeded.freevbr|Free virtual boarder router quota exceed.|超过边界路由器配额。|
|400|InvalidIp.NotSameSubnet|Local gateway ip and peer gateway ip are not in the same subnet.|本地网关 IP 地址与对端网关 IP 地址不在同一个子网内。|
|404|CROSS\_BID.FORBIDDEN|Create VBR across bid is illegal|禁止为其他站点的用户创建 VBR。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

