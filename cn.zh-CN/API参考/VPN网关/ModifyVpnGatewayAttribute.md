# ModifyVpnGatewayAttribute {#doc_api_Vpc_ModifyVpnGatewayAttribute .reference}

调用ModifyVpnGatewayAttribute接口修改VPN网关的名称和描述信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyVpnGatewayAttribute&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyVpnGatewayAttribute|要执行的操作。

 取值： **ModifyVpnGatewayAttribute**。

 |
|RegionId|String|是|cn-shanghai|VPN网关实例所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VpnGatewayId|String|是|vpn-bp1q8bgx4xnkm2ogj\*\*\*\*|VPN网关实例的ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|Description|String|否|vpn网关|VPN网关的描述信息。

 长度为 2-256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|Name|String|否|myvpn|VPN网关的名称。

 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://` 或`https://`开头。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|VpnGatewayId|String|vpn-bp1q8bgx4xnkm2ogj\*\*\*\*|VPN网关实例的ID。

 |
|VpcId|String|vpc-bp1ub1yt9cvakoel\*\*\*\*|VPN网关实例所属VPC的ID。

 |
|VSwitchId|String|vsw-bp1y9ovl1cu9ou4tv\*\*\*\*|VPN网关实例所属交换机的ID。

 |
|InternetIp|String|116.62.69.xxx|VP网关实例的公网IP地址。

 |
|CreateTime|Long|1492753580000|VPN网关实例的创建时间。

 |
|EndTime|Long|1495382400000|VPN网关实例的到期时间。

 |
|Spec|String|5M|VPN网关实例的规格。

 |
|Name|String|test|VPN网关实例的名称。

 |
|Description|String|test|VPN网关实例的描述信息。

 |
|Status|String|active|VPN网关的状态。

 |
|BusinessStatus|String|Normal|VPN网关实例的付费状态。

 |
|IntranetIp|String|172.16.104.xxx|VPN网关的私网IP。

 |
|RequestId|String|54B48E3D-DF70-471B-AA93-08E683A1B457|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyVpnGatewayAttribute
&RegionId=cn-shanghai
&VpnGatewayId=vpn-bp1q8bgx4xnkm2ogj****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyVpnGatewayAttributeResponse>
      <Name>aaa</Name>
      <Status>active</Status>
      <VpnGatewayId>vpn-bp1q8bgx4xnkm2ogj****</VpnGatewayId>
      <BusinessStatus>Normal</BusinessStatus>
      <Spec>5M</Spec>
      <CreateTime>1492753580000</CreateTime>
      <IntranetIp>172.16.104.xxx</IntranetIp>
      <RequestId>54B48E3D-DF70-471B-AA93-08E683A1B457</RequestId>
      <InternetIp>116.62.69.xxx</InternetIp>
      <EndTime>1495382400000</EndTime>
      <VSwitchId>vsw-bp1y9ovl1cu9ou4tv****</VSwitchId>
      <VpcId>vpc-bp1ub1yt9cvakoelj****</VpcId>
</ModifyVpnGatewayAttributeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Name":"aaa",
	"Status":"active",
	"VpnGatewayId":"vpn-bp1q8bgx4xnkm2ogj****",
	"Spec":"5M",
	"BusinessStatus":"Normal",
	"RequestId":"BA56EAF8-E3A9-4BE6-8511-8F03512153E2",
	"IntranetIp":"172.16.104.xxx",
	"CreateTime":1492753580000,
	"InternetIp":"116.62.69.xxx",
	"EndTime":1495382400000,
	"VSwitchId":"vsw-bp1y9ovl1cu9ou4tv****",
	"VpcId":"vpc-bp1ub1yt9cvakoelj****"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|
|404|InvalidVpnGatewayInstanceId.NotFound|The specified vpn gateway instance id does not exist.|指定的 VPN 网关不存在，请您检查 VPN 网关是否正确。|
|400|InvalidName|The name is not valid|该名称格式不合法。|
|400|InvalidDescription|The description is not valid|描述格式不合法。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

