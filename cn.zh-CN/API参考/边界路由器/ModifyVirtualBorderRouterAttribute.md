# ModifyVirtualBorderRouterAttribute {#doc_api_Vpc_ModifyVirtualBorderRouterAttribute .reference}

调用ModifyVirtualBorderRouterAttribute接口修改边界路由器（VBR）的配置。

修改边界路由器属性

-   **VlanId**只允许物理专线的所有者可以修改。
-   同一物理专线下的同一VlanId不允许两个VBR同时使用。
-   进入**Terminated**状态的VBR会在7天内自动保留其VlanId，不允许其他VBR使用。7天后可以被其他VBR使用。
-   其他账号所属的VBR，不能配置**LocalGatewayIp**、**PeerGatewayIp**和**PeeringSubnetMask**。
-   **LocalGatewayIp**、**PeerGatewayIp**、**PeeringSubnetMask**三个参数的要求如下：
    -   **PeeringSubnetMask**支持24-30位。
    -   **PeeringSubnetMask**支持点分十进制表示法255.255.255.0-255.255.255.252。
    -   **LocalGatewayIp**和**PeerGatewayIp**必须在同一个网段内。

        例如：

    -   LocalGatewayIp: 192.168.xx.17
    -   PeerGatewayIp: 192.168.xx.18
    -   PeeringSubnetMask: 255.255.255.248

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyVirtualBorderRouterAttribute&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyVirtualBorderRouterAttribute|要执行的操作，取值： **ModifyVirtualBorderRouterAttribute**。

 |
|RegionId|String|是|cn-shanghai|VBR所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VbrId|String|是|vbr-\*\*\*\*\*\*\*\*\*\*\*\*\*\*|边界路由器的ID。

 |
|AssociatedPhysicalConnections|String|否|pc-kojok19xxxxxxxxx|物理专线ID。

 |
|CircuitCode|String|否|longtel001|运营商为物理专线提供的电路编码。

 **说明：** 只有物理专线的所有者可以指定该参数。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-00xxxxxxxx|用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。 

 |
|Description|String|否|VBR|VBR的描述信息。

 长度为2-256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|DetectMultiplier|Long|否|3|检测时间倍数。即接收方允许发送方发送报文的最大连接丢包数，用来检测链路是否正常，取值：**3-10**。

 |
|LocalGatewayIp|String|否|116.62.xx.xx|VBR的阿里云侧互联IP。

 |
|MinRxInterval|Long|否|100|配置BFD报文的接收间隔，取值：**200-1000，单位为ms**。

 |
|MinTxInterval|Long|否|100|配置BFD报文的发送间隔，取值：**200-1000，单位为ms**。

 |
|Name|String|否|test|VBR的名称。

 长度为2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://`或`https://`开头。

 |
|PeerGatewayIp|String|否|120.120.xx.xx|VBR专线侧接口对端的IP地址。该属性只允许VBR owner指定/修改。不允许把Enabled状态的VBR的该属性改为空。

 |
|PeeringSubnetMask|String|否|255.255.128.0|VBR的阿里云侧和客户侧互联IP的子网掩码。 两个IP地址必须位于同一个子网中。

 |
|VlanId|Integer|否|12|VBR的VLAN ID，取值范围为：**1-2999**。

 **说明：** 只有物理专线的所有者可以指定该参数，同一条物理专线下的两个VBR的VLAN ID不能相同。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|980960B0-2969-40BF-8542-EBB34FD358AB|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=ModifyVirtualBorderRouterAttribute
&RegionId=cn-shanghai
&VbrId=vbr-***********
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyVirtualBorderRouterAttributeResponse>
      <RequestId>980960B0-2969-40BF-8542-EBB34FD358AB</RequestId>
</ModifyVirtualBorderRouterAttributeResponse>
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
|404|InvalidRegionId.NotFound|The specified RegionId is not found.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|InvalidVbrId.NotFound|The specified VirutalBorderRouter is not found.|该边界路由器不存在，请您检查输入的边界路由器是否正确。|
|400|InvalidVlanId.Used|The specified VlanId has been used.|该VLAN已经被占用。|
|400|InvalidCircuitCode.Malformed|The specified CircuitCode is not valid.|该CircuitCode不合法。|
|400|InvalidVlanId.Malformed|The specified VlanId is not valid.|参数VlanId的值不合法。|
|400|InvalidIp.Malformed|The specified ip address is not valid.|指定的私网 IP 不合法，请您检查该私网IP是否正确。|
|400|InvalidPeeringSubnetMask.Malformed|The specified PeeringSubnetMask is not valid.|指定的 PeeringSubnetMask 不合法，请您检查该参数是否正确。|
|403|Forbidden.CircuitCodeNotAllowedByCaller|The caller is not allowed to modify.|不允许修改CircuitCode参数。|
|403|Forbidden.CircuitCodeNotAllowedByCaller|The caller is not allowed to specify the CircuitCode parameter.|不允许指定CircuitCode参数。|
|403|Forbidden.LocalGatewayIpNotAllowedByCaller|The caller is not allowed to specify the LocalGatewayIp parameter.|不允许指定LocalGatewayIp参数。|
|403|Forbidden.PeerGatewayIpNotAllowedByCaller|The caller is not allowed to specify the PeerGatewayIp parameter.|不允许指定PeerGatewayIp参数。|
|403|Forbidden.PeeringSubnetMaskNotAllowedByCaller|The caller is not allowed to specify the PeeringSubnetMask parameter.|不允许指定PeeringSubnetMask参数。|
|403|Forbidden.VlanIdNotAllowedByCaller|The caller is not allowed to specify the VlanId.|不允许指定VLAN ID。|
|403|Forbidden.NameNotAllowedByCaller|The caller is not allowed to specify the Name parameter.|不允许指定Name参数。|
|403|Forbidden.DescriptionNotAllowedByCaller|The caller is not allowed to specify the Description parameter.|不允许指定Description参数。|
|400|InvalidIp.NotSameSubnet|Local gateway ip and peer gateway ip are not in the same subnet.|本地网关 IP 地址与对端网关 IP 地址不在同一个子网内。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

