# RAM authentication {#reference_ow1_hkk_qdb .reference}

Before a RAM user can call VPC APIs, the primary account must grant the RAM user the corresponding permission by creating an authentication policy. In the authentication policy, an Alibaba Cloud Resource Name \(ARN\) is used as the unique identifier of the resource to authorize. This topic overviews ARNs used as unique identifiers of VPC resources.

## VPC resources {#section_vj2_fyf_cz .section}

The following table lists VPC resources that can be authorized and the corresponding ARN formats. For the following ARN formats, $regionid/accountid/vrouterid is the resource ID, and \* represents all corresponding resources.

|Resource|ARN formats|
|:-------|:----------|
|VPC|`acs:vpc:$regionid:$accountid:vpc/$vpcid`|
|`acs:vpc:$regionid:$accountid:vpc/*`|
|`acs:vpc:*:$accountid:vpc/*`|
|`acs:slb:*:*:loadbalancer/*`|
|VRouter|`acs:vpc:$regionid:$accountid:vrouter/$vrouterid`|
|`acs:vpc:$regionid:$accountid:vrouter/*`|
|`acs:vpc:*:$accountid:vrouter/*`|
|VSwitch|`acs:vpc:$regionid:$accountid:vswitch/$vswitchid`|
|`acs:vpc:$regionid:$accountid:vswitch/*`|
|`acs:vpc:*:$accountid:vswitch/*`|
|Route Table|`acs:vpc:$regionid:$accountid:routetable/$routetableid`|
|`acs:vpc:$regionid:$accountid:routetable/*`|
|`acs:vpc:*:$accountid:routetable/*`|
|HaVip|`acs:vpc:$regionid:$accountid:havip/$havipid`|
|`acs:vpc:$regionid:$accountid:havip/*`|
|`acs:vpc:*:$accountid:havip/*`|
|EIP|`acs:vpc:$regionid:$accountid:eip/$allocationid`|
|`acs:vpc:$regionid:$accountid:eip/*`|
|`acs:vpc:*:$accountid:eip/*`|
|NAT Gateway|`acs:vpc:$regionid:$accountid:natgateway/$natgatewayid`|
|`acs:vpc:$regionid:$accountid:natgateway/*`|
|`acs:vpc*:$accountid:vpc/*`|
|NAT Gateway Bandwidth Package|`acs:vpc:$regionid:$accountid:bandwidthpackage/$bandwidthpackageid`|
|`acs:vpc:$regionid:$accountid:bandwidthpackage/*`|
|`aacs:vpc:*:$accountid:vpc/*`|
|Forward Table|`acs:vpc:$regionid:$accountid:forwardtable/$forwardtableid`|
|`acs:vpc:$regionid:$accountid:forwardtable/*`|
|`acs:vpc:*:$accountid:vpc/*`|
|SNAT Table|`acs:vpc:$regionid:$accountid:snattable/$snattableid`|
|`acs:vpc:$regionid:$accountid:snattable/*`|
|`acs:vpc:*:$accountid:vpc/*`|
|Customer Gateway|`acs:vpc:$regionid:$accountid:customergateway/$customergatewayid`|
|`acs:vpc:$regionid:$accountid:customergateway/*`|
|`acs:vpc:*:$accountid:customergateway/*`|
|IPsec Connection|`acs:vpc:$regionid:$accountid:vpnconnection/$vpnconnectionid`|
|`acs:vpc:$regionid:$accountid:vpnconnection/*`|
|`acs:vpc:*:$accountid:vpnconnection/*`|
|VPN Gateway|`acs:vpc:$regionid:$accountid:vpngateway/$vpngatewayid`|
|`acs:vpc:$regionid:$accountid:vpngateway/*`|
|`acs:vpc:*:$accountid:vpngateway/*`|
|Global Acceleration Instance|`acs:vpc:$regionid:$accountid: globalaccelerationinstance /$ globalaccelerationinstanceid`|
|`acs:vpc:$regionid:$accountid: globalaccelerationinstance /*`|
|`acs:vpc::$accountid: globalaccelerationinstance /*`|
|General Expression|`acs:vpc:$regionid:$accountid:*`|
|`acs:vpc:*:$accountid:*`|

## VPC APIs {#section_ytz_qyf_cz .section}

The following table lists the ARN formats of the APIs that can be authorized.

Where `$regionid/accoutid/vrouterid` is the resource ID, and `*` represents the corresponding resource.

|API|ARN format|
|---|----------|
|CreateVpc|`acs:vpc:$regionid:$accountid:vpc/*`|
|DeleteVpc|`acs:vpc:$regionid:$accountid:vpc/$vpcid`|
|DescribeVpcs|`acs:vpc:$regionid:$accountid:vpc/*`|
|ModifyVpcAttribute|`acs:vpc:$regionid:$accountid:vpc/$vpcid`|
|DescribeVRouters|`acs:vpc:$regionid:$accountid:vrouter/*`|
|Specify the VRouterId to query: `"vpc:Vpc":"acs:vpc:$regionid:$accountid:vpc/$vpcid"`

 |
|The VRouterId is not specified: `"vpc:Vpc":"acs:vpc:$regionid:$accountid:vpc/*"`

 |
|ModifyVRouterAttribute|`acs:vpc:*:$accountid:*`|
|CreateVSwitch|`acs:vpc:$regionid:$accountid:vswitch/*`|
| |`acs:vpc:$regionid:$accountid:vpc/$vpcid`|
|DeleteVSwitch|`acs:vpc:$regionid:$accountid:vswitch/$vswitchid`|
|DescribeVSwitches|`acs:vpc:$regionid:$accountid:vswitch/*`|
|`"vpc:Vpc":"acs:vpc:$regionid:$accountid:vpc/$vpcid"`|
|ModifyVSwitchAttribute|`acs:vpc:$regionid:$accountid:vswitch/$vswitchId`|
|CreateRouteEntry|`acs:vpc:$regionid:$accountid:routetable/$routetableid`|
|DeleteRouteEntry|`acs:vpc:$regionid:$accountid:routetable/$routetableid`|
|DescribeRouteTables|`acs:vpc:$regionid:$accountid:routetable/*`|
|`"vpc:VRouter":"acs:vpc$regionid:$accountid:vrouter/$vrouterid"`|
|CreateHaVip|`acs:vpc:$regionid:$accountid:havip/*`|
|`acs:vpc:$regionid:$accountid:vswitch/$vswitchid`|
|DeleteHaVip|`acs:vpc:$regionid:$accountid:havip/$havipid`|
|AssociateHaVip|`acs:vpc:$regionid:$accountid:havip/$havipid`|
|`acs:vpc:%s:%s:certificate/%`|
|`acs:ecs:$regionid:$accountid:instance/$instanceid`|
|UnassociateHaVip|`acs:vpc:$regionid:$accountid:havip/$havipid`|
|`acs:ecs:$regionid:$accountid:instance/$instanceid`|
|DescribeHaVips|`acs:vpc:$regionid:$accountid:havip/*`|
|AllocateEipAddress|`acs:vpc:$regionid:$accountid:eip/*`|
|AssociateEipAddres|`acs:vpc:$regionid:$accountid:eip/*`|
|Attach an ECS instance `acs:vpc:$regionid:$accountid:eip/$allocationid`

 `acs:ecs:$regionid:$accountid:instance/$instanceid`

 |
|Attach an HaVip `acs:vpc:$regionid:$accountid:eip/$allocationid`

 `acs:vpc:$regionid:$accountid:havip/$havipid`

 |
|DescribeEipAddresses|`acs:vpc:$regionid:$accountid:eip/*`|
|UnassociateEipAddress|Attach an ECS instance `acs:vpc:$regionid:$accountid:eip/$allocationid`

 `acs:ecs:$regionid:$accountid:instance/$instanceid`

 |
|Attach an HaVip `acs:vpc:$regionid:$accountid:eip/$allocationid`

 `acs:vpc:$regionid:$accountid:havip/$havipid`

 |
|ReleaseEipAddress|`acs:vpc:$regionid:$accountid:eip/$allocationid`|
|DescribeEipMonitorData|`acs:vpc:$regionid:$accountid:eip/$allocationid`|
|`acs:ecs:$regionid:$accountid:instance/$instanceid`|
|CreateNatGateway|`acs:vpc:$regionid:$accountid:natgateway/*`|
|DescribeNatGateways|`acs:vpc:$regionid:$accountid:natgateway/$natgatewayid`|
|`acs:vpc:$regionid:$accountid:natgateway/*`|
|ModifyNatGatewaySpec|`acs:vpc:$regionid:$accountid:natgateway/$natgatewayid`|
|ModifyNatGatewayAttribute|`acs:vpc:$regionid:$accountid:natgateway/$natgatewayid`|
|`acs:ecs:$regionid:$accountid:instance/$instanceid`|
|DeleteNatGateway|`acs:vpc:$regionid:$accountid:natgateway/$natgatewayid`|
|`acs:ecs:$regionid:$accountid:instance/$instanceid`|
|CreateBandwidthPackage|`acs:vpc:$regionid:$accountid:bandwidthpackage/*`|
|DescribeBandwidthPackages|`acs:vpc:$regionid:$accountid:bandwidthpackage/$bandwidthpackageid`|
|`acs:vpc:$regionid:$accountid:bandwidthpackage/*`|
|ModifyBandwidthPackageSpec|`acs:vpc:$regionid:$accountid:bandwidthpackage/$bandwidthpackageid`|
|ModifyBandwidthPackageAttribute|`acs:vpc:$regionid:$accountid:bandwidthpackage/$bandwidthpackageid`|
|AddBandwidthPackageIps|`acs:vpc:$regionid:$accountid:bandwidthpackage/$bandwidthpackageid`|
|RemoveBandwidthPackageIps|`acs:vpc:$regionid:$accountid:bandwidthpackage/$bandwidthpackageid`|
|DeleteBandwidthPackage|`acs:vpc:$regionid:$accountid:bandwidthpackage/$bandwidthpackageid`|
|CreateForwardEntry|`acs:vpc:$regionid:$accountid:forwardtable/$forwardtableid`|
|DeleteForwardEntry|`acs:vpc:$regionid:$accountid:forwardtable/$forwardtableid`|
|ModifyForwardEntry|`acs:vpc:$regionid:$accountid:forwardtable/$forwardtableid`|
|DescribeForwardTableEntries|`acs:vpc:$regionid:$accountid:forwardtable/$forwardtableid`|
|CreateSnatEntry|`acs:vpc:$regionid:$accountid:snattable/*`|
|ModifySnatEntry|`acs:vpc:$regionid:$accountid:snattable/$snattableid`|
|DescribeSnatTableEntries|`acs:vpc:$regionid:$accountid:snattable/$snattableid`|
|DeleteSnatEntry|`acs:vpc:$regionid:$accountid:snattable/$snattableid`|
|CreateCustomerGateway|`acs:vpc:$regionid:$accountid:customergateway/*`|
|DeleteCustomerGateway|`acs:vpc:$regionid:$accountid:customergateway/$customergatewayid`|
|DescribeCustomerGateway|`acs:vpc:$regionid:$accountid:customergateway/$customergatewayid`|
|DescribeCustomerGateways|`acs:vpc:$regionid:$accountid:customergateway/*`|
|ModifyCustomerGatewayAttribute|`acs:vpc:$regionid:$accountid:customergateway/$customergatewayid`|
|CreateVpnConnection|`acs:vpc:$regionid:$accountid:vpnconnection/*`|
|DeleteVpnConnection|`acs:vpc:$regionid:$accountid:vpnconnection/$vpnconnectionid`|
|DescribeVpnConnection|`acs:vpc:$regionid:$accountid:vpnconnection/$vpnconnectionid`|
|DescribeVpnConnections|`acs:vpc:$regionid:$accountid:vpnconnection/*`|
|ModifyVpnConnectionAttribute|`acs:vpc:$regionid:$accountid:vpnconnection/$vpnconnectionid`|
|Downloadvpnconnectionconfig|`acs:vpc:$regionid:$accountid:vpnconnection/$vpnconnectionid`|
|DeleteVpnGateway|`acs:vpc:$regionid:$accountid:vpngateway/$vpngatewayid`|
|DescribeVpnGateway|`acs:vpc:$regionid:$accountid:vpngateway/$vpngatewayid`|
|DescribeVpnGateways|`acs:vpc:$regionid:$accountid:vpngateway/*`|
|ModifyVpnGatewayAttribute|`acs:vpc:$regionid:$accountid:vpngateway/$vpngatewayid`|
|CreateGlobalAccelerationInstance|`acs:vpc:$regionid:$accountid:globalaccelerationinstance/*`|
|AssociateGlobalAccelerationInstance|`acs:vpc:$regionid:$accountid:globalaccelerationinstance/$globalaccelerationinstanceid`|
|`acs:ecs:$regionid:$accountid:instance/$instanceid`|
|UnassociateGlobalAccelerationInstance|`acs:ecs:$regionid:$accountid:instance/$instanceid`|
|ModifyGlobalAccerlationInstanceSpec|`acs:ecs:$regionid:$accountid:instance/$instanceid`|
|ModifyGlobalAccerlationInstanceAttributes|`acs:ecs:$regionid:$accountid:instance/$instanceid`|
|DeleteGlobalAccelerationInstance|`acs:ecs:$regionid:$accountid:instance/$instanceid`|
|DescribeGlobalAccelerationInstances|`acs:vpc:$regionid:$accountid:globalaccelerationinstance/*`|
|AddGlobalAccelerationInstanceIp| `acs:vpc:$regionid:$accountid:globalaccelerationinstance/$globalaccelerationinstanceid`

 `acs:vpc:$regionid:$accountid:eip/$allocationid`

 |
|RemoveGlobalAccelerationInstanceIp| `acs:vpc:$regionid:$accountid:globalaccelerationinstance/$globalaccelerationinstanceid`

 `acs:vpc:$regionid:$accountid:eip/$allocationid`

 |
|DescribeServerRelatedGlobalAccelerationInstances|`acs:vpc:$regionid:$accountid:globalaccelerationinstance/*`|
|`acs:ecs:$regionid:$accountid:instance/$instanceid`|

