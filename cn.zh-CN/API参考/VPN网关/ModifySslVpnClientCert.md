# ModifySslVpnClientCert {#doc_api_Vpc_ModifySslVpnClientCert .reference}

调用ModifySslVpnClientCert接口修改SSL-VPN客户端证书的名称。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifySslVpnClientCert&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifySslVpnClientCert|要执行的操作。

 取值：**ModifySslVpnClientCert**。

 |
|RegionId|String|是|cn-hangzhou|SSL-VPN客户端证书所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|SslVpnClientCertId|String|是|vsc-bp1n8wcf134yl0osrc\*\*\*\*|SSL-VPN客户端证书的ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|Name|String|否|cert2|SSL-VPN客户端证书的名称。

 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://` 或`https://`开头。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Name|String|cert2|客户端证书的名称。

 |
|RequestId|String|606998F0-B94D-48FE-8316-ACA81BB230DA|请求ID。

 |
|SslVpnClientCertId|String|vsc-bp1n8wcf134yl0osr\*\*\*\*|SSL-VPN客户端证书的ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifySslVpnClientCert
&RegionId=cn-hangzhou
&SslVpnClientCertId=vsc-bp1n8wcf134yl0osr****
&Name=cert2
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifySslVpnClientCertResponse>
      <SslVpnClientCertId>vsc-bp1n8wcf134yl0osr****</SslVpnClientCertId>
      <Name>cert2</Name>
      <RequestId>606998F0-B94D-48FE-8316-ACA81BB230DA</RequestId>
</ModifySslVpnClientCertResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Name":"cert2",
	"RequestId":"606998F0-B94D-48FE-8316-ACA81BB230DA",
	"SslVpnClientCertId":"vsc-bp1n8wcf134yl0osr****"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|
|400|InvalidName|The name is not valid|该名称格式不合法。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

