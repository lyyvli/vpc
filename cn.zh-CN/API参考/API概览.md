# API概览 {#doc_2467 .concept}

专有网络VPC提供以下相关API接口。

## 专有网络（VPC） {#section_3mr_lz3_7oy .section}

|API|描述|
|---|--|
|[CreateVpc](cn.zh-CN/API参考/专有网络（VPC）/CreateVpc.md)|调用CreateVpc接口创建一个专有网络（VPC）。|
|[DeleteVpc](cn.zh-CN/API参考/专有网络（VPC）/DeleteVpc.md)|调用DeleteVpc接口删除一个专有网络（VPC）。|
|[DescribeVpcs](cn.zh-CN/API参考/专有网络（VPC）/DescribeVpcs.md)|调用DescribeVpcs接口查询已创建的VPC。|
|[ModifyVpcAttribute](cn.zh-CN/API参考/专有网络（VPC）/ModifyVpcAttribute.md)|调用ModifyVpcAttribute接口修改指定VPC的名称和描述信息。|
|[DescribeVpcAttribute](cn.zh-CN/API参考/专有网络（VPC）/DescribeVpcAttribute.md)|调用DescribeVpcAttribute接口查询指定VPC的配置信息。|
|[DisableVpcClassicLink](cn.zh-CN/API参考/专有网络（VPC）/DisableVpcClassicLink.md)|调用DisableVpcClassicLink关闭ClassicLink。|
|[EnableVpcClassicLink](cn.zh-CN/API参考/专有网络（VPC）/EnableVpcClassicLink.md)|调用EnableVpcClassicLink开启ClassicLink。|

## 交换机 {#section_mth_dwm_gwl .section}

|API|描述|
|---|--|
|[DescribeVSwitches](cn.zh-CN/API参考/交换机/DescribeVSwitches.md)|调用DescribeVSwitches接口查询已创建的交换机。|
|[ModifyVSwitchAttribute](cn.zh-CN/API参考/交换机/ModifyVSwitchAttribute.md)|使用ModifyVSwitchAttribute修改指定交换机的名称和描述信息。|
|[DescribeVSwitchAttributes](cn.zh-CN/API参考/交换机/DescribeVSwitchAttributes.md)|调用DescribeVSwitchAttributes接口查询指定交换机的配置信息。|
|[CreateVSwitch](cn.zh-CN/API参考/交换机/CreateVSwitch.md)|调用CreateVSwitch接口创建一个交换机。|
|[DeleteVSwitch](cn.zh-CN/API参考/交换机/DeleteVSwitch.md)|调用DeleteVSwitch接口删除交换机。|

## 路由器 {#section_98r_gdx_ifv .section}

|API|描述|
|---|--|
|[DescribeVRouters](cn.zh-CN/API参考/路由器/DescribeVRouters.md)|调用DescribeVRouters接口查询指定地域的路由器列表。|
|[ModifyVRouterAttribute](cn.zh-CN/API参考/路由器/ModifyVRouterAttribute.md)|调用ModifyVRouterAttribute接口修改路由器的名称和描述信息。|

## 路由表 {#section_q7e_bwz_dn7 .section}

|API|描述|
|---|--|
|[ModifyRouteTableAttributes](cn.zh-CN/API参考/路由表/ModifyRouteTableAttributes.md)|调用ModifyRouteTableAttributes接口修改路由表的名称和描述。|
|[DescribeRouteTableList](cn.zh-CN/API参考/路由表/DescribeRouteTableList.md)|调用DescribeRouteTableList接口查询路由表。|
|[DescribeRouteTables](cn.zh-CN/API参考/路由表/DescribeRouteTables.md)|调用DescribeRouteTables接口查询路由表的路由条目。|
|[CreateRouteTable](cn.zh-CN/API参考/路由表/CreateRouteTable.md)|调用CreateRouteTable接口创建一个自定义路由表。|
|[AssociateRouteTable](cn.zh-CN/API参考/路由表/AssociateRouteTable.md)|调用AssociateRouteTable接口将创建的自定义路由表和同一VPC内的交换机绑定。|
|[UnassociateRouteTable](cn.zh-CN/API参考/路由表/UnassociateRouteTable.md)|调用UnassociateRouteTable接口将路由表和交换机解绑。|
|[DeleteRouteTable](cn.zh-CN/API参考/路由表/DeleteRouteTable.md)|调用DeleteRouteTable接口删除自定义路由表。|
|[CreateRouteEntry](cn.zh-CN/API参考/路由表/CreateRouteEntry.md)|调用CreateRouteEntry接口在VPC路由器或边界路由器（VBR）上创建自定义路由条目。|
|[DeleteRouteEntry](cn.zh-CN/API参考/路由表/DeleteRouteEntry.md)|调用DeleteRouteEntry接口删除VPC路由器或边界路由器的路由表中的路由条目。|
|[ModifyRouteEntry](cn.zh-CN/API参考/路由表/ModifyRouteEntry.md)|调用ModifyRouteEntry修改一条自定义路由条目的名称。|

## 地域 {#section_p64_5dt_zrv .section}

|API|描述|
|---|--|
|[DescribeZones](cn.zh-CN/API参考/地域/DescribeZones.md)|调用DescribeZones查询指定地域中可用区的列表。|
|[DescribeAccessPoints](cn.zh-CN/API参考/地域/DescribeAccessPoints.md)|调用DescribeAccessPoints接口查询指定地域中的物理专线接入点。|
|[DescribeRegions](cn.zh-CN/API参考/地域/DescribeRegions.md)|调用DescribeRegions接口查询可用地域。|

## 路由器接口 {#section_b1t_bax_2sm .section}

|API|描述|
|---|--|
|[CreateRouterInterface](cn.zh-CN/API参考/路由器接口/CreateRouterInterface.md)|调用CreateRouterInterface接口创建路由器接口。|
|[DescribeRouterInterfaces](cn.zh-CN/API参考/路由器接口/DescribeRouterInterfaces.md)|调用DescribeRouterInterfaces接口查询指定地域内的路由器接口。|
|[ConnectRouterInterface](cn.zh-CN/API参考/路由器接口/ConnectRouterInterface.md)|调用ConnectRouterInterface接口由发起端路由器接口向接收端发起连接。|
|[ActivateRouterInterface](cn.zh-CN/API参考/路由器接口/ActivateRouterInterface.md)|调用ActivateRouterInterface接口激活处于Inactive状态的路由器接口。|
|[DeactivateRouterInterface](cn.zh-CN/API参考/路由器接口/DeactivateRouterInterface.md)|调用DeactivateRouterInterface接口冻结路由器接口。|
|[ModifyRouterInterfaceSpec](cn.zh-CN/API参考/路由器接口/ModifyRouterInterfaceSpec.md)|调用ModifyRouterInterfaceSpec接口修改路由器接口的规格。|
|[ModifyRouterInterfaceAttribute](cn.zh-CN/API参考/路由器接口/ModifyRouterInterfaceAttribute.md)|调用ModifyRouterInterfaceAttribute接口修改路由器接口的配置。|
|[DeleteRouterInterface](cn.zh-CN/API参考/路由器接口/DeleteRouterInterface.md)|调用DeleteRouterInterface接口删除路由器接口。|

## BGP {#section_jdb_rsa_twm .section}

|API|描述|
|---|--|
|[DescribeBgpNetworks](cn.zh-CN/API参考/BGP/DescribeBgpNetworks.md)|调用DescribeBgpNetworks查询已宣告的BGP网络。|
|[CreateBgpGroup](cn.zh-CN/API参考/BGP/CreateBgpGroup.md)|使用CreateBgpGroup为指定的边界路由器（VBR）创建一个BGP组。|
|[DescribeBgpGroups](cn.zh-CN/API参考/BGP/DescribeBgpGroups.md)|使用DescribeBgpGroups查询指定地域下的BGP组。|
|[ModifyBgpGroupAttribute](cn.zh-CN/API参考/BGP/ModifyBgpGroupAttribute.md)|调用ModifyBgpGroupAttribute接口修改BGP组的配置。|
|[DeleteBgpGroup](cn.zh-CN/API参考/BGP/DeleteBgpGroup.md)|使用DeleteBgpGroup删除指定的BGP组。|
|[CreateBgpPeer](cn.zh-CN/API参考/BGP/CreateBgpPeer.md)|调用CreateBgpPeer接口向指定的BGP组中添加BGP邻居。|
|[DescribeBgpPeers](cn.zh-CN/API参考/BGP/DescribeBgpPeers.md)|使用DescribeBgpPeers查询指定地域下的BGP邻居。|
|[DeleteBgpPeer](cn.zh-CN/API参考/BGP/DeleteBgpPeer.md)|使用DeleteBgpPeer删除指定的BGP邻居。|
|[AddBgpNetwork](cn.zh-CN/API参考/BGP/AddBgpNetwork.md)|使用AddBgpNetwork宣告BGP网络。|
|[DeleteBgpNetwork](cn.zh-CN/API参考/BGP/DeleteBgpNetwork.md)|使用DeleteBgpNetwork删除已宣告的BGP网络。|
|[ModifyBgpPeerAttribute](cn.zh-CN/API参考/BGP/ModifyBgpPeerAttribute.md)|调用ModifyBgpGroupAttribute接口修改BGP邻居的属性。|

## 边界路由器 {#section_60o_lpx_hhk .section}

|API|描述|
|---|--|
|[CreateVirtualBorderRouter](cn.zh-CN/API参考/边界路由器/CreateVirtualBorderRouter.md)|调用CreateVirtualBorderRouter接口新建边界路由器（VBR）。|
|[DeleteVirtualBorderRouter](cn.zh-CN/API参考/边界路由器/DeleteVirtualBorderRouter.md)|调用DeleteVirtualBorderRouter接口删除边界路由器（VBR）。|
|[DescribeVirtualBorderRouters](cn.zh-CN/API参考/边界路由器/DescribeVirtualBorderRouters.md)|调用DescribeVirtualBorderRouters接口查询已创建的边界路由器（VBR）。|
|[DescribeVirtualBorderRoutersForPhysicalConnection](cn.zh-CN/API参考/边界路由器/DescribeVirtualBorderRoutersForPhysicalConnection.md)|调用DescribeVirtualBorderRoutersForPhysicalConnection接口查询指定物理专线下的边界路由器（VBR），包括物理专线所有者的VBR和其他账号的VBR。|
|[ModifyVirtualBorderRouterAttribute](cn.zh-CN/API参考/边界路由器/ModifyVirtualBorderRouterAttribute.md)|调用ModifyVirtualBorderRouterAttribute接口修改边界路由器（VBR）的配置。|
|[TerminateVirtualBorderRouter](cn.zh-CN/API参考/边界路由器/TerminateVirtualBorderRouter.md)|调用TerminateVirtualBorderRouter接口终止边界路由器（VBR）。|
|[RecoverVirtualBorderRouter](cn.zh-CN/API参考/边界路由器/RecoverVirtualBorderRouter.md)|调用RecoverVirtualBorderRouter接口恢复被终止的边界路由器（VBR）。|
|[AssociatePhysicalConnectionToVirtualBorderRouter](cn.zh-CN/API参考/边界路由器/AssociatePhysicalConnectionToVirtualBorderRouter.md)|调用AssociatePhysicalConnectionToVirtualBorderRouter将VBR关联物理专线。|
|[UnassociatePhysicalConnectionFromVirtualBorderRouter](cn.zh-CN/API参考/边界路由器/UnassociatePhysicalConnectionFromVirtualBorderRouter.md)|调用UnassociatePhysicalConnectionFromVirtualBorderRouter解绑VBR和物理专线。|

## 物理专线 {#section_udm_ixn_9di .section}

|API|描述|
|---|--|
|[CreatePhysicalConnection](cn.zh-CN/API参考/物理专线/CreatePhysicalConnection.md)|调用CreatePhysicalConnection接口申请物理专线接入。|
|[CancelPhysicalConnection](cn.zh-CN/API参考/物理专线/CancelPhysicalConnection.md)|在物理专线开通前，调用CancelPhysicalConnection接口取消物理专线接入，取消后物理专线进入Canceled状态。|
|[DescribePhysicalConnections](cn.zh-CN/API参考/物理专线/DescribePhysicalConnections.md)|调用DescribePhysicalConnections接口查询指定地域内的物理专线。|
|[ModifyPhysicalConnectionAttribute](cn.zh-CN/API参考/物理专线/ModifyPhysicalConnectionAttribute.md)|调用ModifyPhysicalConnectionAttribute接口修改物理专线的配置。|
|[TerminatePhysicalConnection](cn.zh-CN/API参考/物理专线/TerminatePhysicalConnection.md)|在物理专线开通后调用TerminatePhysicalConnection接口终止物理专线接入。|
|[EnablePhysicalConnection](cn.zh-CN/API参考/物理专线/EnablePhysicalConnection.md)|使用EnablePhysicalConnection接口开通处于Confirmed状态的物理专线，开通完成后物理专线进入Enabled状态。|
|[DeletePhysicalConnection](cn.zh-CN/API参考/物理专线/DeletePhysicalConnection.md)|调用DeletePhysicalConnection接口删除物理专线。|
|[ApplyPhysicalConnectionLOA](cn.zh-CN/API参考/物理专线/ApplyPhysicalConnectionLOA.md)|调用ApplyPhysicalConnectionLOA申请LOA。|
|[CompletePhysicalConnectionLOA](cn.zh-CN/API参考/物理专线/CompletePhysicalConnectionLOA.md)|调用CompletePhysicalConnectionLOA完成施工完竣。|
|[CreatePhysicalConnectionOccupancyOrder](cn.zh-CN/API参考/物理专线/CreatePhysicalConnectionOccupancyOrder.md)|调用CreatePhysicalConnectionOccupancyOrder创建资源占用费订单。|
|[CreatePhysicalConnectionSetupOrder](cn.zh-CN/API参考/物理专线/CreatePhysicalConnectionSetupOrder.md)|调用CreatePhysicalConnectionSetupOrder创建初装费订单。|
|[DescribePhysicalConnectionLOA](cn.zh-CN/API参考/物理专线/DescribePhysicalConnectionLOA.md)|调用DescribePhysicalConnectionLOA查询物理专线LOA信息。|

## 高速上云服务 {#section_ovm_lji_8ys .section}

|API|描述|
|---|--|
|[CreateExpressCloudConnection](cn.zh-CN/API参考/高速上云服务/CreateExpressCloudConnection.md)|调用CreateExpressCloudConnection申请高速上云服务。|
|[ModifyExpressCloudConnectionAttribute](cn.zh-CN/API参考/高速上云服务/ModifyExpressCloudConnectionAttribute.md)|调用ModifyExpressCloudConnectionAttribute修改高速上云服务连接。|
|[ModifyExpressCloudConnectionBandwidth](cn.zh-CN/API参考/高速上云服务/ModifyExpressCloudConnectionBandwidth.md)|调用ModifyExpressCloudConnectionBandwidth修改高速上云服务带宽。|
|[DescribeExpressCloudConnections](cn.zh-CN/API参考/高速上云服务/DescribeExpressCloudConnections.md)|调用DescribeExpressCloudConnections查询某个区域的高速上云服务列表。|

## VPN网关 {#section_yn8_8c3_4rq .section}

|API|描述|
|---|--|
|[CreateVpnGateway](cn.zh-CN/API参考/VPN网关/CreateVpnGateway.md)|调用CreateVpnGateway接口创建一个VPN网关。|
|[DescribeVpnGateways](cn.zh-CN/API参考/VPN网关/DescribeVpnGateways.md)|调用DescribeVpnGateways接口查询已创建的VPN网关。|
|[DescribeVpnGateway](cn.zh-CN/API参考/VPN网关/DescribeVpnGateway.md)|调用DescribeVpnGateway接口查询指定VPN网关的详细信息。|
|[DeleteVpnGateway](cn.zh-CN/API参考/VPN网关/DeleteVpnGateway.md)|调用DeleteVpnGateway接口删除指定的VPN网关。|
|[CreateCustomerGateway](cn.zh-CN/API参考/VPN网关/CreateCustomerGateway.md)|调用CreateCustomerGateway接口创建用户网关。|
|[DescribeCustomerGateways](cn.zh-CN/API参考/VPN网关/DescribeCustomerGateways.md)|调用DescribeCustomerGateways接口查询已创建的用户网关。|
|[DescribeCustomerGateway](cn.zh-CN/API参考/VPN网关/DescribeCustomerGateway.md)|调用DescribeCustomerGateway接口查询已创建的用户网关的详细信息。|
|[DeleteCustomerGateway](cn.zh-CN/API参考/VPN网关/DeleteCustomerGateway.md)|调用DeleteCustomerGateway接口删除指定的用户网关。|
|[ModifyCustomerGatewayAttribute](cn.zh-CN/API参考/VPN网关/ModifyCustomerGatewayAttribute.md)|调用ModifyCustomerGatewayAttribute接口修改用户网关的名称和描述信息。|
|[DescribeVpnConnection](cn.zh-CN/API参考/VPN网关/DescribeVpnConnection.md)|调用DescribeVpnConnection接口查询已创建的IPsec连接的详细信息。|
|[DeleteVpnConnection](cn.zh-CN/API参考/VPN网关/DeleteVpnConnection.md)|调用DeleteVpnConnection接口删除指定的IPsec连接。|
|[DownloadVpnConnectionConfig](cn.zh-CN/API参考/VPN网关/DownloadVpnConnectionConfig.md)|调用DownloadVpnConnectionConfig接口获取IPsec连接的配置信息。|
|[CreateSslVpnServer](cn.zh-CN/API参考/VPN网关/CreateSslVpnServer.md)|调用CreateSslVpnServer接口创建SSL-VPN服务端。|
|[DescribeSslVpnServers](cn.zh-CN/API参考/VPN网关/DescribeSslVpnServers.md)|调用DescribeSslVpnServers接口查询已创建的SSL-VPN服务端。|
|[DeleteSslVpnServer](cn.zh-CN/API参考/VPN网关/DeleteSslVpnServer.md)|调用DeleteSslVpnServer接口删除SSL-VPN服务端实例。|
|[ModifySslVpnServer](cn.zh-CN/API参考/VPN网关/ModifySslVpnServer.md)|调用ModifySslVpnServer接口修改SSL-VPN服务端的配置信息。|
|[DeleteSslVpnClientCert](cn.zh-CN/API参考/VPN网关/DeleteSslVpnClientCert.md)|调用DeleteSslVpnClientCert接口删除SSL-VPN客户端证书。|
|[ModifySslVpnClientCert](cn.zh-CN/API参考/VPN网关/ModifySslVpnClientCert.md)|调用ModifySslVpnClientCert接口修改SSL-VPN客户端证书的名称。|
|[ModifyVpnGatewayAttribute](cn.zh-CN/API参考/VPN网关/ModifyVpnGatewayAttribute.md)|调用ModifyVpnGatewayAttribute接口修改VPN网关的名称和描述信息。|
|[CreateVpnConnection](cn.zh-CN/API参考/VPN网关/CreateVpnConnection.md)|调用CreateVpnConnection接口创建IPsec连接。|
|[DescribeVpnConnections](cn.zh-CN/API参考/VPN网关/DescribeVpnConnections.md)|调用DescribeVpnConnections接口查询已创建的IPsec连接。|
|[ModifyVpnConnectionAttribute](cn.zh-CN/API参考/VPN网关/ModifyVpnConnectionAttribute.md)|调用ModifyVpnConnectionAttribute接口修改IPsec连接的配置信息。|
|[CreateSslVpnClientCert](cn.zh-CN/API参考/VPN网关/CreateSslVpnClientCert.md)|调用CreateSslVpnClientCert接口创建SSL-VPN客户端证书。|
|[DescribeSslVpnClientCerts](cn.zh-CN/API参考/VPN网关/DescribeSslVpnClientCerts.md)|调用DescribeSslVpnClientCerts接口查询已创建的SSL-VPN客户端证书。|
|[DeleteVpnGreTunnel](cn.zh-CN/API参考/VPN网关/DeleteVpnGreTunnel.md)|调用DeleteVpnGreTunnel接口删除指定的GRE隧道。|
|[DeleteVpnPbrRouteEntry](cn.zh-CN/API参考/VPN网关/DeleteVpnPbrRouteEntry.md)|调用DeleteVpnPbrRouteEntry删除VPN策略路由。|
|[DeleteVpnRouteEntry](cn.zh-CN/API参考/VPN网关/DeleteVpnRouteEntry.md)|调用DeleteVpnRouteEntry删除VPN目的路由。|
|[CreateVpnPbrRouteEntry](cn.zh-CN/API参考/VPN网关/CreateVpnPbrRouteEntry.md)|调用CreateVpnPbrRouteEntry创建VPN策略路由。|
|[DescribeVpnRouteEntries](cn.zh-CN/API参考/VPN网关/DescribeVpnRouteEntries.md)|调用DescribeVpnRouteEntries查询VPN目的路由。|
|[ModifyVpnRouteEntryWeight](cn.zh-CN/API参考/VPN网关/ModifyVpnRouteEntryWeight.md)|调用ModifyVpnRouteEntryWeight修改VPN目的路由的权重值。|
|[PublishVpnRouteEntry](cn.zh-CN/API参考/VPN网关/PublishVpnRouteEntry.md)|调用PublishVpnRouteEntry发布VPN路由到VPC。|
|[DescribeVpnPbrRouteEntries](cn.zh-CN/API参考/VPN网关/DescribeVpnPbrRouteEntries.md)|调用DescribeVpnPbrRouteEntries查询VPN策略路由。|
|[ModifyVpnPbrRouteEntryWeight](cn.zh-CN/API参考/VPN网关/ModifyVpnPbrRouteEntryWeight.md)|调用ModifyVpnPbrRouteEntryWeight接口修改VPN策略路由的权重值。|
|[CreateVpnRouteEntry](cn.zh-CN/API参考/VPN网关/CreateVpnRouteEntry.md)|调用CreateVpnRouteEntry创建VPN目的路由。|
|[DescribeVpnSslServerLogs](cn.zh-CN/API参考/VPN网关/DescribeVpnSslServerLogs.md)|调用DescribeVpnSslServerLogs查看SSL服务端的日志。|

## NAT网关 {#section_vuu_h0g_cqa .section}

|API|描述|
|---|--|
|[CreateNatGateway](cn.zh-CN/API参考/NAT网关/CreateNatGateway.md)|使用CreateNatGateway接口创建一个NAT网关。|
|[ModifyNatGatewayAttribute](cn.zh-CN/API参考/NAT网关/ModifyNatGatewayAttribute.md)|使用ModifyNatGatewayAttribute接口修改NAT网关配置。|
|[ModifyNatGatewaySpec](cn.zh-CN/API参考/NAT网关/ModifyNatGatewaySpec.md)|使用ModifyNatGatewaySpec接口修改NAT网关的规格。|
|[CreateBandwidthPackage](cn.zh-CN/API参考/NAT网关/CreateBandwidthPackage.md)|使用CreateBandwidthPackage接口创建NAT带宽包。|
|[DescribeBandwidthPackages](cn.zh-CN/API参考/NAT网关/DescribeBandwidthPackages.md)|使用DescribeBandwidthPackages接口查询指定地域的NAT带宽包。|
|[ModifyBandwidthPackageSpec](cn.zh-CN/API参考/NAT网关/ModifyBandwidthPackageSpec.md)|使用ModifyBandwidthPackageSpec接口修改指定NAT带宽包的带宽。|
|[ModifyBandwidthPackageAttribute](cn.zh-CN/API参考/NAT网关/ModifyBandwidthPackageAttribute.md)|使用ModifyBandwidthPackageAttribute接口修改指定NAT带宽包的名称和描述。|
|[DescribeNatGateways](cn.zh-CN/API参考/NAT网关/DescribeNatGateways.md)|使用DescribeNatGateways接口查询已创建的NAT网关。|
|[AddBandwidthPackageIps](cn.zh-CN/API参考/NAT网关/AddBandwidthPackageIps.md)|使用AddBandwidthPackageIps接口在NAT带宽包中增加公网IP。|
|[RemoveBandwidthPackageIps](cn.zh-CN/API参考/NAT网关/RemoveBandwidthPackageIps.md)|使用RemoveBandwidthPackageIps接口删除NAT带宽包中的公网IP。|
|[DeleteBandwidthPackage](cn.zh-CN/API参考/NAT网关/DeleteBandwidthPackage.md)|使用DeleteBandwidthPackage接口删除指定的NAT带宽包。|
|[DeleteNatGateway](cn.zh-CN/API参考/NAT网关/DeleteNatGateway.md)|使用DeleteNatGateway接口删除指定的NAT网关。|
|[CreateForwardEntry](cn.zh-CN/API参考/NAT网关/CreateForwardEntry.md)|使用CreateForwardEntry在DNAT列表中添加DNAT条目。|
|[DescribeForwardTableEntries](cn.zh-CN/API参考/NAT网关/DescribeForwardTableEntries.md)|调用DescribeForwardTableEntries接口查询已创建的DNAT条目。|
|[ModifyForwardEntry](cn.zh-CN/API参考/NAT网关/ModifyForwardEntry.md)|调用ModifyForwardEntry接口修改指定的DNAT条目。|
|[DeleteForwardEntry](cn.zh-CN/API参考/NAT网关/DeleteForwardEntry.md)|调用DeleteForwardEntry接口删除指定的DNAT条目。|
|[CreateSnatEntry](cn.zh-CN/API参考/NAT网关/CreateSnatEntry.md)|调用CreateSnatEntry接口在SNAT列表中添加SNAT条目。|
|[DescribeSnatTableEntries](cn.zh-CN/API参考/NAT网关/DescribeSnatTableEntries.md)|调用DescribeSnatTableEntries接口查询已创建的SNAT条目。|
|[ModifySnatEntry](cn.zh-CN/API参考/NAT网关/ModifySnatEntry.md)|调用ModifySnatEntry接口修改指定的SNAT条目。|
|[DeleteSnatEntry](cn.zh-CN/API参考/NAT网关/DeleteSnatEntry.md)|调用DeleteSnatEntry接口删除指定的SNAT条目。|
|[ConvertBandwidthPackage](cn.zh-CN/API参考/NAT网关/ConvertBandwidthPackage.md)|调用ConvertBandwidthPackage转换NAT带宽包。|

## 全球加速 {#section_681_tal_dpr .section}

|API|描述|
|---|--|
|[CreateGlobalAccelerationInstance](cn.zh-CN/API参考/全球加速/CreateGlobalAccelerationInstance.md)|调用CreateGlobalAccelerationInstance接口创建全球加速实例。|
|[DescribeGlobalAccelerationInstances](cn.zh-CN/API参考/全球加速/DescribeGlobalAccelerationInstances.md)|调用DescribeGlobalAccelerationInstances接口查询已创建的全球加速实例列表。|
|[ModifyGlobalAccelerationInstanceAttributes](cn.zh-CN/API参考/全球加速/ModifyGlobalAccelerationInstanceAttributes.md)|调用ModifyGlobalAccelerationInstanceAttributes接口修改全球加速实例的名称和描述信息。|
|[ModifyGlobalAccelerationInstanceSpec](cn.zh-CN/API参考/全球加速/ModifyGlobalAccelerationInstanceSpec.md)|调用ModifyGlobalAccelerationInstanceSpec接口修改全球加速实例的带宽。|
|[DeleteGlobalAccelerationInstance](cn.zh-CN/API参考/全球加速/DeleteGlobalAccelerationInstance.md)|调用DeleteGlobalAccelerationInstance接口删除全球加速实例。|
|[AssociateGlobalAccelerationInstance](cn.zh-CN/API参考/全球加速/AssociateGlobalAccelerationInstance.md)|调用AssociateGlobalAccelerationInstance接口为独享型实例绑定后端服务器。|
|[UnassociateGlobalAccelerationInstance](cn.zh-CN/API参考/全球加速/UnassociateGlobalAccelerationInstance.md)|调用UnassociateGlobalAccelerationInstance接口解绑与全球加速实例关联的后端服务实例。|
|[DescribeServerRelatedGlobalAccelerationInstances](cn.zh-CN/API参考/全球加速/DescribeServerRelatedGlobalAccelerationInstances.md)|调用DescribeServerRelatedGlobalAccelerationInstances接口查询指定后端服务器绑定的全球加速实例。|
|[AddGlobalAccelerationInstanceIp](cn.zh-CN/API参考/全球加速/AddGlobalAccelerationInstanceIp.md)|调用AddGlobalAccelerationInstanceIp接口添加EIP到指定的带宽共享实例中。|
|[RemoveGlobalAccelerationInstanceIp](cn.zh-CN/API参考/全球加速/RemoveGlobalAccelerationInstanceIp.md)|调用RemoveGlobalAccelerationInstanceIp接口从带宽共享实例中移除EIP。|

## 共享带宽 {#section_7kn_mua_cgy .section}

|API|描述|
|---|--|
|[DescribeCommonBandwidthPackages](cn.zh-CN/API参考/共享带宽/DescribeCommonBandwidthPackages.md)|调用DescribeCommonBandwidthPackages接口查询指定地域中共享带宽实例列表。|
|[ModifyCommonBandwidthPackageAttribute](cn.zh-CN/API参考/共享带宽/ModifyCommonBandwidthPackageAttribute.md)|调用ModifyCommonBandwidthPackageAttribute修改共享带宽实例的名称和描述信息。|
|[CreateCommonBandwidthPackage](cn.zh-CN/API参考/共享带宽/CreateCommonBandwidthPackage.md)|调用CreateCommonBandwidthPackage接口创建共享带宽实例。|
|[AddCommonBandwidthPackageIp](cn.zh-CN/API参考/共享带宽/AddCommonBandwidthPackageIp.md)|调用AddCommonBandwidthPackageIp接口添加EIP到共享带宽中。|
|[DeleteCommonBandwidthPackage](cn.zh-CN/API参考/共享带宽/DeleteCommonBandwidthPackage.md)|调用DeleteCommonBandwidthPackage接口删除共享带宽实例。|
|[ModifyCommonBandwidthPackageSpec](cn.zh-CN/API参考/共享带宽/ModifyCommonBandwidthPackageSpec.md)|调用ModifyCommonBandwidthPackageSpec接口更改共享带宽的带宽峰值。|
|[RemoveCommonBandwidthPackageIp](cn.zh-CN/API参考/共享带宽/RemoveCommonBandwidthPackageIp.md)|调用RemoveCommonBandwidthPackageIp接口移除共享带宽实例中的EIP。|
|[CancelCommonBandwidthPackageIpBandwidth](cn.zh-CN/API参考/共享带宽/CancelCommonBandwidthPackageIpBandwidth.md)|调用CancelCommonBandwidthPackageIpBandwidth接口取消已经加入共享带宽中的EIP的最大可用带宽值的设置。|
|[ModifyCommonBandwidthPackageIpBandwidth](cn.zh-CN/API参考/共享带宽/ModifyCommonBandwidthPackageIpBandwidth.md)|调用ModifyCommonBandwidthPackageIpBandwidth接口为已经加入共享带宽中的EIP设置最大可用的带宽值。|

## 弹性公网IP {#section_spc_ujw_kca .section}

|API|描述|
|---|--|
|[AllocateEipAddress](cn.zh-CN/API参考/弹性公网IP/AllocateEipAddress.md)|调用AllocateEipAddress接口申请弹性公网IP（EIP）。|
|[AssociateEipAddress](cn.zh-CN/API参考/弹性公网IP/AssociateEipAddress.md)|调用AssociateEipAddress接口将弹性公网IP（EIP）绑定到同地域的云产品实例上。|
|[ModifyEipAddressAttribute](cn.zh-CN/API参考/弹性公网IP/ModifyEipAddressAttribute.md)|调用ModifyEipAddressAttribute接口修改指定EIP的名称、描述信息和带宽峰值。|
|[DescribeEipAddresses](cn.zh-CN/API参考/弹性公网IP/DescribeEipAddresses.md)|调用DescribeEipAddresses接口查询指定地域已创建的EIP。|
|[UnassociateEipAddress](cn.zh-CN/API参考/弹性公网IP/UnassociateEipAddress.md)|使用UnassociateEipAddress将弹性公网IP（EIP）从绑定的云资源上解绑。|
|[ReleaseEipAddress](cn.zh-CN/API参考/弹性公网IP/ReleaseEipAddress.md)|使用ReleaseEipAddress接口释放指定的弹性公网IP（EIP）。|
|[ModifyEipAddressAttribute](cn.zh-CN/API参考/弹性公网IP/ModifyEipAddressAttribute.md)|修改指定EIP的名称、描述信息和带宽峰值。|
|[DescribeEipMonitorData](cn.zh-CN/API参考/弹性公网IP/DescribeEipMonitorData.md)|调用DescribeEipMonitorData接口查看EIP的监控信息。|
|[DescribeEipGatewayInfo](cn.zh-CN/API参考/弹性公网IP/DescribeEipGatewayInfo.md)|调用DescribeEipGatewayInfo接口查询EIP的网关和掩码信息。|

## 流日志 {#section_x3r_hnf_m4c .section}

|API|描述|
|---|--|
|[CreateFlowLog](cn.zh-CN/API参考/流日志/CreateFlowLog.md)|调用CreateFlowLog接口创建流日志。|
|[ModifyFlowLogAttribute](cn.zh-CN/API参考/流日志/ModifyFlowLogAttribute.md)|调用ModifyFlowLogAttribute接口编辑流日志的名称和描述。|
|[DescribeFlowLogs](cn.zh-CN/API参考/流日志/DescribeFlowLogs.md)|调用DescribeFlowLogs接口查询流日志。|
|[ActiveFlowLog](cn.zh-CN/API参考/流日志/ActiveFlowLog.md)|调用ActiveFlowLog接口启动流日志，启动后开始捕获指定资源的流量。|
|[DeactiveFlowLog](cn.zh-CN/API参考/流日志/DeactiveFlowLog.md)|调用DeactiveFlowLog接口停止流日志，停止后不再捕获指定资源的流量。|
|[DeleteFlowLog](cn.zh-CN/API参考/流日志/DeleteFlowLog.md)|调用DeleteFlowLog接口删除流日志。|

## IPv6转换服务 {#section_c6e_xhz_eeb .section}

|API|描述|
|---|--|
|[DeleteIPv6TranslatorAclList](cn.zh-CN/API参考/IPv6转换服务/DeleteIPv6TranslatorAclList.md)|删除访问控制策略组。只有当访问控制策略组没有绑定任何IPv6转换映射时，才可以删除。|
|[CreateIPv6TranslatorAclList](cn.zh-CN/API参考/IPv6转换服务/CreateIPv6TranslatorAclList.md)|创建访问控制策略组。|
|[DeleteIPv6TranslatorEntry](cn.zh-CN/API参考/IPv6转换服务/DeleteIPv6TranslatorEntry.md)|删除IPv6转换映射条目。|
|[ModifyIPv6TranslatorAclAttribute](cn.zh-CN/API参考/IPv6转换服务/ModifyIPv6TranslatorAclAttribute.md)|修改访问控制策略组的名称。|
|[DescribeIPv6TranslatorAclLists](cn.zh-CN/API参考/IPv6转换服务/DescribeIPv6TranslatorAclLists.md)|查询已创建的访问控制策略组。|
|[ModifyIPv6TranslatorBandwidth](cn.zh-CN/API参考/IPv6转换服务/ModifyIPv6TranslatorBandwidth.md)|修改IPv6转换服务实例的带宽。|
|[RemoveIPv6TranslatorAclListEntry](cn.zh-CN/API参考/IPv6转换服务/RemoveIPv6TranslatorAclListEntry.md)|删除访问控制策略组中的IP条目。|
|[DescribeIPv6TranslatorAclListAttributes](cn.zh-CN/API参考/IPv6转换服务/DescribeIPv6TranslatorAclListAttributes.md)|询访问控制策略组的详细信息，包括访问控制策略组中的IP和关联的IPv6转换映射条目的具体信息。|
|[DescribeIPv6Translators](cn.zh-CN/API参考/IPv6转换服务/DescribeIPv6Translators.md)|查询已创建的IPv6转换服务实例列表。|
|[ModifyIPv6TranslatorAttribute](cn.zh-CN/API参考/IPv6转换服务/ModifyIPv6TranslatorAttribute.md)|修改IPv6转换服务实例的名称和描述信息。|
|[DescribeIPv6TranslatorEntries](cn.zh-CN/API参考/IPv6转换服务/DescribeIPv6TranslatorEntries.md)|查询IPv6转换映射条目。|
|[CreateIPv6TranslatorEntry](cn.zh-CN/API参考/IPv6转换服务/CreateIPv6TranslatorEntry.md)|为指定的IPv6转换服务实例添加IPv6转换映射条目。|
|[AddIPv6TranslatorAclListEntry](cn.zh-CN/API参考/IPv6转换服务/AddIPv6TranslatorAclListEntry.md)|在访问控制策略组中添加IP条目。|
|[ModifyIPv6TranslatorEntry](cn.zh-CN/API参考/IPv6转换服务/ModifyIPv6TranslatorEntry.md)|修改IPv6转换映射条目。|
|[DeleteIPv6Translator](cn.zh-CN/API参考/IPv6转换服务/DeleteIPv6Translator.md)|删除IPv6转换服务实例。|
|[CreateIPv6Translator](cn.zh-CN/API参考/IPv6转换服务/CreateIPv6Translator.md)|创建IPv6转换服务实例。|

## IPv6网关 {#section_3qr_icm_dzb .section}

|API|描述|
|---|--|
|[CreateIpv6Gateway](cn.zh-CN/API参考/IPv6网关/CreateIpv6Gateway.md)|调用CreateIpv6Gateway接口创建IPv6网关。|
|[DeleteIpv6Gateway](cn.zh-CN/API参考/IPv6网关/DeleteIpv6Gateway.md)|调用DeleteIpv6Gateway接口删除IPv6网关。|
|[ModifyIpv6GatewaySpec](cn.zh-CN/API参考/IPv6网关/ModifyIpv6GatewaySpec.md)|调用ModifyIpv6GatewaySpec接口修改IPv6网关的规格。|
|[DescribeIpv6EgressOnlyRules](cn.zh-CN/API参考/IPv6网关/DescribeIpv6EgressOnlyRules.md)|调用DescribeIpv6EgressOnlyRules接口查询创建的仅主动出规则。|
|[CreateIpv6EgressOnlyRule](cn.zh-CN/API参考/IPv6网关/CreateIpv6EgressOnlyRule.md)|调用CreateIpv6EgressOnlyRule接口为IPv6地址添加仅主动出规则。|
|[DeleteIpv6EgressOnlyRule](cn.zh-CN/API参考/IPv6网关/DeleteIpv6EgressOnlyRule.md)|调用DeleteIpv6EgressOnlyRule接口删除仅主动出规则。|
|[DeleteIpv6InternetBandwidth](cn.zh-CN/API参考/IPv6网关/DeleteIpv6InternetBandwidth.md)|调用DeleteIpv6InternetBandwidth接口删除公网带宽。|
|[DescribeIpv6GatewayAttribute](cn.zh-CN/API参考/IPv6网关/DescribeIpv6GatewayAttribute.md)|调用DescribeIpv6GatewayAttribute接口查询指定IPV6网关的详细信息。|
|[DescribeIpv6Addresses](cn.zh-CN/API参考/IPv6网关/DescribeIpv6Addresses.md)|调用DescribeIpv6Addresses接口查询IPv6地址列表。|
|[AllocateIpv6InternetBandwidth](cn.zh-CN/API参考/IPv6网关/AllocateIpv6InternetBandwidth.md)|调用AllocateIpv6InternetBandwidth接口为IPv6地址购买公网带宽。|
|[ModifyIpv6InternetBandwidth](cn.zh-CN/API参考/IPv6网关/ModifyIpv6InternetBandwidth.md)|调用ModifyIpv6InternetBandwidth接口修改IPv6地址的公网带宽。|
|[DescribeIpv6Gateways](cn.zh-CN/API参考/IPv6网关/DescribeIpv6Gateways .md)|调用DescribeIpv6Gateways接口查询已创建的IPv6网关。|

