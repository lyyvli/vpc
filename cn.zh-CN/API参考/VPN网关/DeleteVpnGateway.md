# DeleteVpnGateway {#doc_api_Vpc_DeleteVpnGateway .reference}

调用DeleteVpnGateway接口删除指定的VPN网关。

**说明：** 无法删除已有IPsec连接的VPN网关。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DeleteVpnGateway&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteVpnGateway|要执行的操作。

 取值： **DeleteVpnGateway**。

 |
|RegionId|String|是|cn-hangzhou|VPN网关实例所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VpnGatewayId|String|是|vpn-bp1q8bgx4xnkm2ogj\*\*\*\*|VPN网关实例的ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|\>0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DeleteVpnGateway
&RegionId=cn-hangzhou
&VpnGatewayId=vpn-bp1q8bgx4xnkm2ogj****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteNatGatewayResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</DeleteNatGatewayResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|
|404|InvalidVpnGatewayInstanceId.NotFound|The specified vpn gateway instance id does not exist.|指定的 VPN 网关不存在，请您检查 VPN 网关是否正确。|
|403|ForbiddenRelease|Forbidden to release a prepaid instance within validity period|不允许在合同期内释放预付费实例。|
|400|VpnGateway.Configuring|The specified service is configuring.|服务正在配置中，请您稍后再试。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

