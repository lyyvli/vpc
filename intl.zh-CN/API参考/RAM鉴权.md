# RAM鉴权 {#reference_ow1_hkk_qdb .reference}

在使用RAM账号调用VPC API前，需要主账号通过创建授权策略对RAM账号进行授权。在授权策略中，使用资源描述符（Alibaba Cloud Resource Name, ARN）指定授权资源。

## 可授权的专有网络资源类型 {#section_vj2_fyf_cz .section}

下表列举了VPC中可授权的资源及其描述方式：

|资源类型|授权策略中的资源描述方法|
|:---|:-----------|
|专有网络（VPC）|`acs:vpc:$regionid:$accountid:vpc/$vpcid`|
|`acs:vpc:$regionid:$accountid:vpc/*`|
|`acs:vpc:*:$accountid:vpc/*`|
|路由器（VRouter）|`acs:vpc:$regionid:$accountid:vrouter/$vrouterid`|
|`acs:vpc:$regionid:$accountid:vrouter/*`|
|`acs:vpc:*:$accountid:vrouter/*`|
|交换机（VSwitch）|`acs:vpc:$regionid:$accountid:vswitch/$vswitchid`|
|`acs:vpc:$regionid:$accountid:vswitch/*`|
|`acs:vpc:*:$accountid:vswitch/*`|
|路由表（Route Table）|`acs:vpc:$regionid:$accountid:routetable/$routetableid`|
|`acs:vpc:$regionid:$accountid:routetable/*`|
|`acs:vpc:*:$accountid:routetable/*`|
|高可用IP （HaVip）|`acs:vpc:$regionid:$accountid:havip/$havipid`|
|`acs:vpc:$regionid:$accountid:havip/*`|
|`acs:vpc:*:$accountid:havip/*`|
|弹性公网IP（EIP）|`acs:vpc:$regionid:$accountid:eip/$allocationid`|
|`acs:vpc:$regionid:$accountid:eip/*`|
|`acs:vpc:*:$accountid:eip/*`|
|NAT网关（NAT Gateway）|`acs:vpc:$regionid:$accountid:natgateway/$natgatewayid`|
|`acs:vpc:$regionid:$accountid:natgateway/*`|
|`acs:vpc*:$accountid:vpc/*`|
|NAT网关带宽包（NAT Gateway Bandwidth Package）|`acs:vpc:$regionid:$accountid:bandwidthpackage/$bandwidthpackageid`|
|`acs:vpc:$regionid:$accountid:bandwidthpackage/*`|
|`aacs:vpc:*:$accountid:vpc/*`|
|端口转发表（Forward Table）|`acs:vpc:$regionid:$accountid:forwardtable/$forwardtableid`|
|`acs:vpc:$regionid:$accountid:forwardtable/*`|
|`acs:vpc:*:$accountid:vpc/*`|
|SNAT表（SNAT Table）|`acs:vpc:$regionid:$accountid:snattable/$snattableid`|
|`acs:vpc:$regionid:$accountid:snattable/*`|
|`acs:vpc:*:$accountid:vpc/*`|
|用户网关（Customer Gateway）|`acs:vpc:$regionid:$accountid:customergateway/$customergatewayid`|
|`acs:vpc:$regionid:$accountid:customergateway/*`|
|`acs:vpc:*:$accountid:customergateway/*`|
|IPsec连接（IPsec Connection）|`acs:vpc:$regionid:$accountid:vpnconnection/$vpnconnectionid`|
|`acs:vpc:$regionid:$accountid:vpnconnection/*`|
|`acs:vpc:*:$accountid:vpnconnection/*`|
|VPN网关（VPN Gateway）|`acs:vpc:$regionid:$accountid:vpngateway/$vpngatewayid`|
|`acs:vpc:$regionid:$accountid:vpngateway/*`|
|`acs:vpc:*:$accountid:vpngateway/*`|
|全球加速实例（Global Acceleration Instance）|`acs:vpc:$regionid:$accountid: globalaccelerationinstance /$ globalaccelerationinstanceid`|
|`acs:vpc:$regionid:$accountid: globalaccelerationinstance /*`|
|`acs:vpc::$accountid: globalaccelerationinstance /*`|
|通用资源|`acs:vpc:$regionid:$accountid:*`|
|`acs:vpc:*:$accountid:*`|

其中`$regionid/accoutid/vrouterid...` 为具体的资源ID，`*`代表对应的所有资源。

## 可授权的VPC接口 {#section_ytz_qyf_cz .section}

下表列举了VPC中可授权的API及其描述方式：

其中`$regionid/accoutid/vrouterid...` 为具体的资源ID，`*`代表对应的所有资源。

|API|资源描述|
|---|----|
|CreateVpc|`acs:vpc:$regionid:$accountid:vpc/*`|
|DeleteVpc|`acs:vpc:$regionid:$accountid:vpc/$vpcid`|
|DescribeVpcs|`acs:vpc:$regionid:$accountid:vpc/*`|
|ModifyVpcAttribute|`acs:vpc:$regionid:$accountid:vpc/$vpcid`|
|DescribeVRouters|`acs:vpc:$regionid:$accountid:vrouter/*`|
|指定要查询的VRouterId： `"vpc:Vpc":"acs:vpc:$regionid:$accountid:vpc/$vpcid"`

 |
|未定要查询的VRouterId： `"vpc:Vpc":"acs:vpc:$regionid:$accountid:vpc/*"`

 |
|ModifyVRouterAttribute|`acs:vpc:*:$accountid:*`|
|CreateVSwitch|`acs:vpc:$regionid:$accountid:vswitch/*`|
| |`acs:vpc:$regionid:$accountid:vpc/$vpcid`|
|DeleteVSwitch|`acs:vpc:$regionid:$accountid:vswitch/$vswitchid`|
|DescribeVSwitches|`acs:vpc:$regionid:$accountid:vswitch/*`|
|`"vpc:Vpc":"acs:vpc:$regionid:$accountid:vpc/$vpcid"`|
|ModifyVSwitchAttribute|`acs:vpc:$regionid:$accountid:vswitch/$vswitchid`|
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
|绑定ECS实例 `acs:vpc:$regionid:$accountid:eip/$allocationid`

 `acs:ecs:$regionid:$accountid:instance/$instanceid`

 |
|绑定HAVIP `acs:vpc:$regionid:$accountid:eip/$allocationid`

 `acs:vpc:$regionid:$accountid:havip/$havipid`

 |
|DescribeEipAddresses|`acs:vpc:$regionid:$accountid:eip/*`|
|UnassociateEipAddress|绑定ECS实例 `acs:vpc:$regionid:$accountid:eip/$allocationid`

 `acs:ecs:$regionid:$accountid:instance/$instanceid`

 |
|绑定HAVIP `acs:vpc:$regionid:$accountid:eip/$allocationid`

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
|DownloadVpnConnectionConfig|`acs:vpc:$regionid:$accountid:vpnconnection/$vpnconnectionid`|
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

