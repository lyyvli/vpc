# DeleteVpnGreTunnel {#doc_api_Vpc_DeleteVpnGreTunnel .reference}

调用DeleteVpnGreTunnel接口删除指定的GRE隧道。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DeleteVpnGreTunnel)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteVpnGreTunnel|要执行的操作，取值：

 **DeleteVpnGreTunnel**。

 |
|RegionId|String|是|cn-hangzhou|GRE隧道所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|TunnelInstanceId|String|是|gre-bp1d47ly8iqzd\*\*\*\*|GRE隧道的ID。

 |
|VpnGatewayId|String|是|vpn-bp1sejphq1xia6vm2\*\*\*\*|VPN网关ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|5BE01CD7-5A50-472D-AC14-CA181C5C03BE|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DeleteVpnGreTunnel
&RegionId=cn-hangzhou
&TunnelInstanceId=gre-bp1d47ly8iqzd****
&VpnGatewayId=vpn-bp1sejphq1xia6vm2****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteVpnGreTunnelResponse>
  <RequestId>185E81B1-3916-4667-B48F-C52409B33F2B</RequestId>
</DeleteVpnGreTunnelResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"D32B3C26-6C6C-4988-93E9-D2A6444CE6AE"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|
|400|Resource.QuotaFull|The quota of resource is full|资源配额已达上限。|
|404|InvalidCustomerGatewayInstanceId.NotFound|The specified customer gateway instance id does not exist.|指定的 Instance 不存在，请您检查 Instance 是否正确。|
|404|InvalidVpnGatewayInstanceId.NotFound|The specified vpn gateway instance id does not exist.|指定的 VPN 网关不存在，请您检查 VPN 网关是否正确。|
|400|InvalidVpnConnection.AlreadyExists|Vpn connection already exists.|VPN 连接已经存在，不用再次添加。|
|400|VpnGateway.Configuring|The specified service is configuring.|服务正在配置中，请您稍后再试。|
|400|VpnGateway.FinancialLocked|The specified service is financial locked.|该服务已欠费，请您先充值再操作。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

