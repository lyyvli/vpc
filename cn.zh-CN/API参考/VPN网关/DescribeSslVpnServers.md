# DescribeSslVpnServers {#doc_api_Vpc_DescribeSslVpnServers .reference}

调用DescribeSslVpnServers接口查询已创建的SSL-VPN服务端。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeSslVpnServers&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeSslVpnServers|要执行的操作。

 取值： **DescribeSslVpnServers**。

 |
|RegionId|String|是|cn-hangzhou|SSL-VPN服务端所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|Name|String|否|test|SSL-VPN服务端的名称。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为**1**。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为**50**，默认值为**10**。

 |
|SslVpnServerId|String|否|vss-bp15j3du13gq1dgey\*\*\*\*|SSL-VPN服务端的ID。

 |
|VpnGatewayId|String|否|vpn-bp1on0xae9d771ggi\*\*\*\*|VPN网关的ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|10|每页包含多少条目。

 |
|RequestId|String|085CA5EA-1E76-43A8-981B-E0208DECA0CB|请求ID。

 |
|SslVpnServers| | |SSL-VPN服务端的详细信息。

 |
|Cipher|String|AES-128-CBC|使用的加密算法。

 |
|ClientIpPool|String|10.10.1.0/24|客户端IP地址池。

 |
|Compress|Boolean|false|是否压缩。

 |
|Connections|Integer|0|当前连接数。

 |
|CreateTime|Long|1544668844000|创建时间。

 |
|InternetIp|String|47.96.167.xxx|公网IP。

 |
|LocalSubnet|String|192.168.0.0/24|本地客户端网段。

 |
|MaxConnections|Integer|5|最大连接数。

 |
|Name|String|test|SSL VPN服务端名称。

 |
|Port|Integer|1194|SSL-VPN服务端所使用的端口。

 |
|Proto|String|UDP|SSL-VPN服务端所使用的协议。

 |
|RegionId|String|cn-hangzhou|SSL-VPN服务端的地域。

 |
|SslVpnServerId|String|vss-bp15j3du13gq1dgey\*\*\*\*|SSL-VPN服务端的ID。

 |
|VpnGatewayId|String|vpn-bp1on0xae9d771ggi\*\*\*\*|VPN网关ID。

 |
|TotalCount|Integer|1|列表条条目数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeSslVpnServers
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeSslVpnServersResponse>
      <PageNumber>1</PageNumber>
      <TotalCount>1</TotalCount>
      <PageSize>10</PageSize>
      <SslVpnServers>
            <SslVpnServer>
                  <RegionId>cn-hanghzou</RegionId>
                  <SslVpnServerId>vss-bp18q7hzj6largv4v****</SslVpnServerId>
                  <VpnGatewayId>vpn-bp1q8bgx4xnkm2ogj****</VpnGatewayId>
                  <Name>test</Name>
                  <CLientIpPool>10.10.10.20/24</CLientIpPool>
                  <LocalSubnet>10.10.10.10/24</LocalSubnet>
                  <Proto>UDP</Proto>
                  <Port>1194</Port>
                  <Cipher>AES-128-CBC</Cipher>
                  <Compress>true</Compress>
                  <CreateTime>1492753580000</CreateTime>
                  <Connections>0</Connections>
                  <MaxConnections>5</MaxConnections>
                  <InternetIp>47.98.xx.xx</InternetIp>
            </SslVpnServer>
      </SslVpnServers>
      <RequestId>DF11D6F6-E35A-41C3-9B20-6FC8A901FE65</RequestId>
</DescribeSslVpnServersResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":"1",
	"TotalCount":"1",
	"SslVpnServers":{
		"SslVpnServer":{
			"VpnGatewayId":"vpn-bp1q8bgx4xnkm2ogj****",
			"CLientIpPool":"10.10.10.20/24",
			"Proto":"UDP",
			"Cipher":"AES-128-CBC",
			"InternetIp":"47.98.xx.xx",
			"SslVpnServerId":"vss-bp18q7hzj6largv4v****",
			"Name":"test",
			"Port":"1194",
			"MaxConnections":"5",
			"RegionId":"cn-hanghzou",
			"CreateTime":"1492753580000",
			"Compress":"true",
			"LocalSubnet":"10.10.10.10/24",
			"Connections":"0"
		}
	},
	"PageSize":"10",
	"RequestId":"DF11D6F6-E35A-41C3-9B20-6FC8A901FE65"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

