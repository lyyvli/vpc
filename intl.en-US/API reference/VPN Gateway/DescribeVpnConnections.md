# DescribeVpnConnections {#doc_api_Vpc_DescribeVpnConnections .reference}

Queries one or more IPsec connections.

## Debug {#apiExplorer .section}

Use [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpnConnections) to perform debug operations and generate SDK examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeVpnConnections| The name of this action.

 Value: **DescribeVpnConnections**.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the IPsec connection belongs.

 To query the region ID, call [DescribeRegions](~~36063~~).

 |
|CustomerGatewayId|String|No|cgw-bp1mvj4g9kogwxxxxxxxx| The ID of the customer gateway.

 |
|PageNumber|Integer|No|1| The number of pages to return. Default value: 1.

 |
|PageSize|Integer|No|10| The number of rows per page. Maximum value: 50. Default value: 10.

 |
|VpnGatewayId|String|No|vpn-bp1q8bgx4xnkxxxxxxxx| The ID of the VPN Gateway.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|VpnConnections| | | A list of IPsec connections.

 |
|└ IkeConfig| | | Configurations of phase one negotiation.

 |
|└ IkeAuthAlg|String|sha1| The IKE authentication algorithm. Both SHA-1 and MD5 are supported.

 |
|└ IkeEncAlg|String|aes| The IKE encryption algorithm.

 |
|└IkeLifetime|Long|86400| The IKE lifetime.

 |
|└IkeMode|String|main| The IKE mode. Both main mode and aggressive mode are supported.

 The main mode features high security. If NAT traversal is enabled, we recommend that you select the aggressive mode.

 |
|└IkePfs|String|group2| The DH group. Valid values: **group1 | group2 | group5 | group14 | group24**

 |
|└IkeVersion|String|ikev1| The IKE version.

 |
|└LocalId|String|116.xx.xx.64| The local ID. It is the IP address of the VPN Gateway by default. Both FQDN and IP formats are supported.

 |
|└Psk|String|pgw6dy7dxxxxxxxx| The pre-shared key.

 |
|└RemoteId|String|139.xx.xx.167| The peer ID. It is the IP address of the customer gateway by default. Both FQDN and IP formats are supported.

 |
|└IpsecConfig| | | Configurations of phase two negotiation.

 |
|└IpsecAuthAlg|String|sha1| The IPsec authentication algorithm. Both SHA-1 and MD5 are supported.

 |
|└IpsecEncAlg|String|aes| The IPsec encryption algorithm.

 |
|└IpsecLifetime|Long|86400| The IPsec encryption algorithm.

 |
|└IpsecPfs|String|group2| The DH group.

 |
|└VpnConnectionId|String|vco-bp10lz7aejumdxxxxxxxx| The ID of the IPsec connection.

 |
|└CustomerGatewayId|String|vpn-bp1q8bgx4xnkxxxxxxxx| The ID of the customer gateway.

 |
|└VpnGatewayId|String|vpn-bp1q8bgx4xnkmxxxxxxxx| The ID of the VPN Gateway.

 |
|└Name|String|xxxxxxxxxxxx| The name of the IPsec connection.

 |
|└LocalSubnet|String|1.1.1.0/24,1.1.2.0/24| The CIDR block of the VPC.

 |
|└RemoteSubnet|String|1.1.1.0/24,1.1.2.0/24| The CIDR block of the on-premises data center.

 |
|└CreateTime|Long|1492753817000| The time at which the IPsec connection was created.

 |
|└Status|String|ipsec\_sa\_established| The connection status. Valid values:

 -   ike\_sa\_not\_established: Phase one negotiation failed.
-   ike\_sa\_established: Phase one negotiation succeeded.
-   ipsec\_sa\_not\_established: Phase two negotiation failed.
-   ipsec\_sa\_established: Phase two negotiation succeeded.

 |
|└EffectImmediately|Boolean|true| Indicates whether the IPsec connection takes effect immediately.

 -   true: Reconnection is triggered when there is a change to the network configuration.
-   false: Reconnection is triggered when traffic is detected over the network. A reconnection may cause intermittent connections.

 |
|└VcoHealthCheck| | | Health check.

 |
|└Dip|String|8.xx.xx.8| The destination IP address.

 |
|└Interval|Integer|2| The time interval between two consecutive health checks.

 |
|└Sip|String|192.xx.xx.66| The source IP address.

 |
|TotalCount|Integer|10| The number of queried entries.

 |
|PageNumber|Integer|1| The current page number.

 |
|PageSize|Integer|10| The number of entries per page.

 |
|RequestId|String|54A4B3D0-DF4D-4C54-B8DC-5DC8DD49C939| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeVpnConnections
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<DescribeVpnConnections>
  <PageNumber>1</PageNumber>
  <VpnConnections>
    <VpnConnection>
      <Name>vpn connection test</Name>
      <CustomerGatewayId>cgw-bp1pvpl9r9adjxxxxxxxx</CustomerGatewayId>
      <RemoteSubnet>2.2.2.0/24</RemoteSubnet>
      <IpsecConfig>
        <IpsecLifetime>86400</IpsecLifetime>
        <IpsecAuthAlg>sha1</IpsecAuthAlg>
        <IpsecPfs>group2</IpsecPfs>
        <IpsecEncAlg>aes</IpsecEncAlg>
      </IpsecConfig>
      <EffectImmediately>true</EffectImmediately>
      <VpnGatewayId>vpn-bp1q8bgx4xnkmxxxxxxxx</VpnGatewayId>
      <CreateTime>1492753817000</CreateTime> 
      <VpnConnectionId>vco-bp10lz7aejumdxxxxxxxx</VpnConnectionId>
      <status>ipsec_sa_established</status>
      <LocalSubnet>1.1.1.0/24,1.1.2.0/24</LocalSubnet>
      <IkeConfig>
        <IkeEncAlg>aes</IkeEncAlg>
        <RemoteId>139.xx.xx. 167</RemoteId>
        <IkePfs>group2</IkePfs>
        <IkeAuthAlg>sha1</IkeAuthAlg>
        <Psk>pgw6dyxxxxxxxx</Psk>
        <IkeMode>main</IkeMode>
        <IkeLifetime>86400</IkeLifetime>
        <IkeVersion>ikev1</IkeVersion>
        <LocalId>116.xx.xx. 64</LocalId>
      </IkeConfig> 
    </VpnConnection>
  </VpnConnections>
  <TotalCount>1</TotalCount>
  <PageSize>10</PageSize>
  <RequestId>54A4B3D0-DF4D-4C54-B8DC-5DC8DD49C939</RequestId>
</DescribeVpnConnections>

```

`JSON` format

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"VpnConnections": {
		"VpnConnection": [
			{
				"CustomerGatewayId":"cgw-bp1pvpl9r9adjxxxxxxxx",
				"Name": "vpn connection test",
				"RemoteSubnet":"2.2.2.0/24",
				"IpsecConfig":{
					"IpsecLifetime":86400,
					"IpsecAuthAlg":"sha1",
					"IpsecPfs":"group2",
					"IpsecEncAlg":"aes"
				},
				"VpnGatewayId":"vpn-bp1q8bgx4xnkmxxxxxxxx",
				"EffectImmediately":true,
				"status":"ipsec_sa_established",
				"VpnConnectionId":"vco-bp10lz7aejumdxxxxxxxx",
				"CreateTime":1492753817000,
				"LocalSubnet":"1.1.1.0/24,1.1.2.0/24",
				"IkeConfig":{
					"IkeEncAlg":"aes",
					"IkePfs":"group2",
					"RemoteId":"139.xx.xx. 167",
					"IkeAuthAlg":"sha1",
					"Psk":"pgw6dyxxxxxxxx",
					"IkeMode":"main",
					"IkeLifetime":86400,
					"IkeVersion":"ikev1",
					"LocalId":"116.xx.xx. 64"
				}
			}
		]
	},
	"TotalCount":1,
	"PageSize":10,
	"RequestId": "54A4B3D0-DF4D-4C54-B8DC-5DC8DD49C939"
}
```

## Error codes { .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|You are not authorized to operate on this resource. Please apply for the permission and try again later.|
|403|Forbidden|User not authorized to operate on the specified resource.|You are not authorized to operate on this resource. For more information, open a ticket.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

