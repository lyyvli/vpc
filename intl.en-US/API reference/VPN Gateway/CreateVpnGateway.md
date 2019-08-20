# CreateVpnGateway {#doc_api_Vpc_CreateVpnGateway .reference}

Creates a VPN Gateway.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=CreateVpnGateway&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreateVpnGateway| The name of this action. Value: **CreateVpnGateway**.

 |
|Bandwidth|Integer|Yes|5| The bandwidth of the VPN Gateway \(in Mbps\).

 Valid values: **5|10|20|50|100**.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the VPN Gateway belongs

 To query the region ID, call [DescribeRegions](~~36063~~).

 |
|VpcId|String|Yes|vpc-bp1ub1yt9cvakoelj\*\*\*\*| The ID of the VPC to which the VPN Gateway belongs.

 |
|AutoPay|Boolean|No|false| Indicates whether the VPN Gateway bill is paid automatically. Valid values:

 -   **true**: The bill is paid automatically.
-   **false** \(default\): The bill is not paid automatically.

 |
|EnableIpsec|Boolean|No|true| Indicates whether to enable the IPsec-VPN function. The IPsec-VPN function provides a site-to-site connection. You can create an IPsec tunnel to connect an on-premises data center to a VPC, or to connect two VPCs. Valid values:

 -   **true** \(default\): The IPsec-VPN function is enabled.
-   **false**: The IPsec-VPN function is disabled.

 |
|EnableSsl|Boolean|No|true| Indicates whether to enable the SSL-VPN function. If this function is enabled, point-to-site VPN connection is provided and customer gateway configuration is not needed. Valid values:

 -   **true**: The SSL-VPN function is enabled.
-   **false** \(default\): The SSL-VPN function is disabled.

 |
|InstanceChargeType|String|No|PREPAY| The billing method of the VPN Gateway. Valid values:

 **POSTPAY**: Pay-As-You-Go.

 |
|Name|String|No|MYVPN| The name of the VPN Gateway. The default value is the ID of the VPN Gateway.

 The name must be 2 to 100 characters in length and contain letters, numbers, periods \(.\), underscores \(\_\), and hyphens \(-\). The name must start with a letter. It cannot start with `http://` or `https://`.

 |
|Period|Integer|No|1| The validity period of a subscription. Valid values: **1~9|12|24|36**.

 **Note:** This parameter is required if the value of **InstanceChargeType** is **PREPAY**.

 |
|SslConnections|Integer|No|2| The maximum number of clients allowed to connect simultaneously.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|Name|String|myVpn| The name of the VPN Gateway.

 |
|OrderId|Long|20224940022015| The ID of the order. Go to the console to complete the payment.

 |
|RequestId|String|54B48E3D-DF70-471B-AA93-08E683A1B457| The ID of the request.

 |
|VpnGatewayId|String|vpn-bp1q8bgx4xnkm2ogj\*\*\*\*| The ID of the VPN Gateway.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=CreateVpnGateway
&Bandwidth=5
&RegionId=cn-hangzhou
&VpcId=vpc-bp1ub1yt9cvakoelj****
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<CreateVpnGatewayResponse>
      <Name>myVpn</Name>
      <VpnGatewayId>vpn-bp1q8bgx4xnkm2ogj****</VpnGatewayId>
      <RequestId>54B48E3D-DF70-471B-AA93-08E683A1B457</RequestId>
</CreateVpnGatewayResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"CreateVpnGatewayResponse":{
		"Name":"myVpn",
		"VpnGatewayId":"vpn-bp1q8bgx4xnkm2ogj****",
		"RequestId":"54B48E3D-DF70-471B-AA93-08E683A1B457"
	}
}
```

## Errors {#section_mbx_twv_luz .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|Resource.QuotaFull|The quota of resource is full.|The resource quota has been reached.|

