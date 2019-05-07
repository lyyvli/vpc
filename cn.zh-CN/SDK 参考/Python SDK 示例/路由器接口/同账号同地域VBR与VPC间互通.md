# 同账号同地域VBR与VPC间互通 {#task_226442 .task}

本文介绍如何使用Python SDK实现同账号同地域下的VBR与VPC互通。

在实现同账号同地域下的VBR与VPC互通前，您必须完成以下操作：

-   您已经申请了专线接口。
-   您已经创建了VPC。

**说明：** 您的专线接口和VPC属于同账号同地域。

创建路由器接口时，请注意：

-   任意两个路由器之间，最多只能存在一对互连的路由器接口。
-   一个路由器上可以最多创建5个路由器接口。
-   如果账户下存在欠费状态的路由器接口，则无法再创建路由器接口。
-   同一路由表下的路由条目的目标网段（DestinationCidrBlock）不允许相同。
-   边界路由器（VBR）只能作为连接发起端，并且处于已激活状态。

本次示例分为以下几步，实现同账号同地域下的VBR与VPC互通。

1.  创建边界路由器。
2.  创建发起端路由器接口。
3.  创建接收端路由器接口。
4.  修改发起端路由器接口信息。
5.  修改接收端路由器接口信息。
6.  查询发起端路由器接口信息。
7.  查询接收端路由器接口信息。
8.  查询边界路由器的路由表ID。
9.  连接发起端路由器接口和接收端路由器接口。
10. 创建下一跳为发起端路由器接口的路由条目。
11. 创建下一跳为接收端路由器接口的路由条目。
12. 删除下一跳为接收端路由器接口的路由条目。
13. 删除下一跳为发起端路由器接口的路由条目。
14. 冻结发起端路由器接口。
15. 冻结接收端路由器接口。
16. 删除发起端路由器接口。
17. 删除接收端路由器接口。
18. 删除边界路由器。

1.  在下载的SDK目录中，打开$aliyun-openapi-python-sdk-examples\\sdk\_examples\\sdk\_lib文件夹。
2.  使用编辑器打开consts.py文件，配置用户鉴权参数ACS\_CLIENT。
3.  在下载的SDK目录中，打开$aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\ec文件夹。
4.  使用编辑器打开ec\_vbr\_vpc.py文件，根据实际情况配置相关参数，保存退出。 

    ``` {#codeblock_cds_sww_pk4}
    #encoding=utf-8
    import sys
    import json
    from aliyunsdkcore.acs_exception.exceptions import ServerException, ClientException
    from aliyunsdkvpc.request.v20160428 import CreateRouterInterfaceRequest
    from aliyunsdkvpc.request.v20160428 import DeleteRouterInterfaceRequest
    from aliyunsdkvpc.request.v20160428 import DescribeRouterInterfacesRequest
    from aliyunsdkvpc.request.v20160428 import ConnectRouterInterfaceRequest
    from aliyunsdkvpc.request.v20160428 import DeactivateRouterInterfaceRequest
    from aliyunsdkvpc.request.v20160428 import ModifyRouterInterfaceAttributeRequest
    from aliyunsdkvpc.request.v20160428 import CreateVirtualBorderRouterRequest
    from aliyunsdkvpc.request.v20160428 import DescribeVirtualBorderRoutersRequest
    from aliyunsdkvpc.request.v20160428 import DescribeRouteTablesRequest
    from aliyunsdkvpc.request.v20160428 import DeleteVirtualBorderRouterRequest
    from sdk_lib.sdk_route_entry import RouteEntry
    from sdk_lib.exception import ExceptionHandler
    from sdk_lib.common_util import CommonUtil
    from sdk_lib.check_status import CheckStatus
    from sdk_lib.consts import *
    
    client = ACS_CLIENT
    
    class RouterInterface(object):
        def __init__(self, client):
            self.client = client
    
        def create_router_interface(self, params):
            """
            create_router_interface: 创建路由器接口
            官网API参考: https://help.aliyun.com/document_detail/36032.html
            """
            try:
                request = CreateRouterInterfaceRequest.CreateRouterInterfaceRequest()
                # 路由器接口的规格
                request.set_Spec(params['spec'])
                # 路由器接口的角色
                request.set_Role(params['role'])
                # 路由器接口关联的路由器ID
                request.set_RouterId(params['router_id'])
                # 路由器接口关联的路由器类型
                request.set_RouterType(params['router_type'])
                # 连接接收端所在的地域ID
                request.set_OppositeRegionId(params['opposite_region_id'])
                # 对端路由器接口关联的路由器类型
                request.set_OppositeRouterType(params['opposite_router_type'])
                # 对端所属的接入点ID
                request.set_OppositeAccessPointId(params['opposite_access_point_id'])
                # VBR所属的接入点ID
                #request.set_AccessPointId(params['access_point_id'])
    
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # 判断路由器接口状态是否可用
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_ri_status,
                                            'Idle', response_json['RouterInterfaceId']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def create_router_interface_vbr(self, params):
            """
            create_router_interface: 创建路由器接口
            官网API参考: https://help.aliyun.com/document_detail/36032.html
            """
            try:
                request = CreateRouterInterfaceRequest.CreateRouterInterfaceRequest()
                # 路由器接口的规格
                request.set_Spec(params['spec'])
                # 路由器接口的角色
                request.set_Role(params['role'])
                # 路由器接口关联的路由器ID
                request.set_RouterId(params['router_id'])
                # 路由器接口关联的路由器类型
                request.set_RouterType(params['router_type'])
                # 连接接收端所在的地域ID
                request.set_OppositeRegionId(params['opposite_region_id'])
                # 对端路由器接口关联的路由器类型
                request.set_OppositeRouterType(params['opposite_router_type'])
                # VBR所属的接入点ID
                request.set_AccessPointId(params['access_point_id'])
    
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # 判断路由器接口状态是否可用
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_ri_status,
                                            'Idle', response_json['RouterInterfaceId']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def connect_router_interface(self, params):
            """
            connect_router_interface: 由发起端路由器接口向接收端发起连接
            官网API参考: https://help.aliyun.com/document_detail/36031.html
            """
            try:
                request = ConnectRouterInterfaceRequest.ConnectRouterInterfaceRequest()
                # 发起端路由器接口的ID
                request.set_RouterInterfaceId(params['router_interface_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                if CheckStatus.check_status(TIME_DEFAULT_OUT * 5, DEFAULT_TIME * 5,
                                            self.describe_ri_status,
                                            'Active', params['router_interface_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def deactivate_router_interface(self, params):
            """
            deactivate_router_interface: 冻结路由器接口
            官网API参考: https://help.aliyun.com/document_detail/36033.html
            """
            try:
                request = DeactivateRouterInterfaceRequest.DeactivateRouterInterfaceRequest()
                # 路由器接口的ID
                request.set_RouterInterfaceId(params['router_interface_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # 判断路由器接口状态是否可用
                if CheckStatus.check_status(TIME_DEFAULT_OUT * 5, DEFAULT_TIME * 5,
                                            self.describe_ri_status,
                                            'Inactive', params['router_interface_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def modify_router_interface_attribute(self, params):
            """
            modify_router_interface_attribute: 修改路由器接口的配置
            官网API参考: https://help.aliyun.com/document_detail/36036.html
            """
            try:
                request = ModifyRouterInterfaceAttributeRequest.ModifyRouterInterfaceAttributeRequest()
                # 路由器接口的ID
                request.set_RouterInterfaceId(params['router_interface_id'])
                # 对端路由器接口ID
                request.set_OppositeInterfaceId(params['opposite_interface_id'])
                # 对端的路由器的ID
                request.set_OppositeRouterId(params['opposite_router_id'])
                # 对端的路由器的类型
                request.set_OppositeRouterType(params['opposite_router_type'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # 判断路由器接口状态是否可用
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_ri_status,
                                            'Idle', params['router_interface_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
    
    
        def describe_router_interface(self, instance_id):
            """
            describe_router_interface: 查询指定地域内的路由器接口
            官网API参考: https://help.aliyun.com/document_detail/36035.html
            """
            try:
                request = DescribeRouterInterfacesRequest.DescribeRouterInterfacesRequest()
                # 查询的过滤类型
                request.add_query_param('Filter.1.Key', "RouterInterfaceId")
                # 查询的实例ID
                request.add_query_param('Filter.1.Value.1', instance_id)
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_ri_status(self, instance_id):
            """
            describe_ri_status: 查询指定地域内的路由器接口状态
            官网API参考: https://help.aliyun.com/document_detail/36035.html
            """
            response = self.describe_router_interface(instance_id)
            if len(response['RouterInterfaceSet']['RouterInterfaceType']) == 0:
                return ''
            return response['RouterInterfaceSet']['RouterInterfaceType'][0]['Status']
    
        def delete_router_interface(self, params):
            """
            delete_router_interface: 删除路由器接口
            官网API参考: https://help.aliyun.com/document_detail/36034.html
            """
            try:
                request = DeleteRouterInterfaceRequest.DeleteRouterInterfaceRequest()
                # 路由器接口的ID
                request.set_RouterInterfaceId(params['instance_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # 判断路由器接口状态是否可用
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME * 5,
                                            self.describe_ri_status,
                                            '', params['instance_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def create_virtual_border_router(self, params):
            """
            create_virtual_border_router: 新建边界路由器
            官网API参考: https://help.aliyun.com/document_detail/36023.html
            """
            try:
                request = CreateVirtualBorderRouterRequest.CreateVirtualBorderRouterRequest()
                # 物理专线的ID
                request.set_PhysicalConnectionId(params['physical_connection_id'])
                # 边界路由器的阿里云侧互联IP
                request.set_LocalGatewayIp(params['local_gateway_ip'])
                # 边界路由器专线侧接口对端的IP地址
                request.set_PeerGatewayIp(params['peer_gateway_ip'])
                # 边界路由器的阿里云侧和客户侧互联IP的子网掩码
                request.set_PeeringSubnetMask(params['peering_subnet_mask'])
                # 边界路由器的VLAN ID
                request.set_VlanId(params['vlan_id'])
    
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # 判断边界路由器状态是否可用
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_vbr_status,
                                            'active', response_json['VbrId']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def delete_virtual_border_router(self, params):
            """
            delete_virtual_border_router: 删除边界路由器
            官网API参考: https://help.aliyun.com/document_detail/40542.html
            """
            try:
                request = DeleteVirtualBorderRouterRequest.DeleteVirtualBorderRouterRequest()
                request.set_VbrId(params['vbr_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_vbr_status,
                                            '', params['vbr_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_virtual_border_router(self, instance_id):
            """
            describe_virtual_border_router: 查询边界路由器
            官网API参考: https://help.aliyun.com/document_detail/36024.html
            """
            try:
                request = DescribeVirtualBorderRoutersRequest.DescribeVirtualBorderRoutersRequest()
                # 查询的过滤类型
                request.add_query_param('Filter.1.Key', "VbrId")
                # 查询的实例ID
                request.add_query_param('Filter.1.Value.1', instance_id)
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_vbr_status(self, instance_id):
            """
            describe_virtual_border_router: 查询边界路由器状态
            官网API参考: https://help.aliyun.com/document_detail/36024.html
            """
            response = self.describe_virtual_border_router(instance_id)
            if len(response['VirtualBorderRouterSet']['VirtualBorderRouterType']) == 0:
                return ''
            return response['VirtualBorderRouterSet']['VirtualBorderRouterType'][0]['Status']
    
        def describe_route_table(self, params):
            """
            describe_route_table: 查询路由表
            官网API参考链接: https://help.aliyun.com/document_detail/36014.html
            """
            try:
                request = DescribeRouteTablesRequest.DescribeRouteTablesRequest()
                # 路由表所属的VPC路由器或边界路由器的ID
                request.set_RouterId(params['router_id'])
                # 路由表所属的路由器类型
                request.set_RouterType(params['router_type'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
    
    def main():
        client = ACS_CLIENT
        router_interface = RouterInterface(client)
        route_entry = RouteEntry(client)
    
        params = {}
        params['spec'] = "Large.2"
        params['role'] = "InitiatingSide"
        params['router_type'] = "VBR"
        params['opposite_region_id'] = "cn-hangzhou"
        params['opposite_router_type'] = "VRouter"
        params['access_point_id'] = "ap-cn-hangzhou-xx-x"
    
        # 创建边界路由器边界路由器
        params['physical_connection_id'] = PC_ID
        params['local_gateway_ip'] = "116.xx.xx.254"
        params['peer_gateway_ip'] = "116.xx.xx.254"
        params['peering_subnet_mask'] = "255.255.255.252"
        params['vlan_id'] = 30
        vbr_json = router_interface.create_virtual_border_router(params)
        CommonUtil.log("create_virtual_border_router", vbr_json)
    
        # 创建发起端路由器接口
        params['router_id'] = vbr_json['VbrId']
        router_interface_json = router_interface.create_router_interface_vbr(params)
        CommonUtil.log("create_router_interface", router_interface_json)
    
        # 创建接收端路由器接口
        params['router_type'] = "VRouter"
        params['spec'] = "Negative"
        params['role'] = "AcceptingSide"
        params['router_id'] = ROUTER_ID2
        params['opposite_router_type'] = 'VBR'
        params['opposite_access_point_id'] = params['access_point_id']
        router_interface_json2 = router_interface.create_router_interface(params)
        CommonUtil.log("create_router_interface", router_interface_json2)
    
        # 修改发起端路由器接口信息
        params['router_interface_id'] = router_interface_json['RouterInterfaceId']
        params['opposite_interface_id'] = router_interface_json2['RouterInterfaceId']
        params['opposite_router_id'] = ROUTER_ID2
        params['opposite_router_type'] = "VRouter"
        modify_ri_json = router_interface.modify_router_interface_attribute(params)
        CommonUtil.log("modify_router_interface_attribute", modify_ri_json)
    
        # 修改接收端路由器接口信息
        params['router_interface_id'] = router_interface_json2['RouterInterfaceId']
        params['opposite_interface_id'] = router_interface_json['RouterInterfaceId']
        params['opposite_router_id'] = vbr_json['VbrId']
        params['opposite_router_type'] = "VBR"
        modify_ri_json2 = router_interface.modify_router_interface_attribute(params)
        CommonUtil.log("modify_router_interface_attribute", modify_ri_json2)
    
        # 查询发起端路由器接口信息
        describe_ri_json = router_interface.describe_router_interface(router_interface_json['RouterInterfaceId'])
        CommonUtil.log("describe_router_interface", describe_ri_json)
    
        # 查询接收端路由器接口信息
        describe_ri_json2 = router_interface.describe_router_interface(router_interface_json2['RouterInterfaceId'])
        CommonUtil.log("describe_router_interface", describe_ri_json2)
    
        # 查询边界路由器的路由表ID
        params['router_id'] = vbr_json['VbrId']
        params['router_type'] = 'VBR'
        route_table_json = router_interface.describe_route_table(params)
        CommonUtil.log("describe_route_table", route_table_json)
    
        # 发起连接
        params['router_interface_id'] = router_interface_json['RouterInterfaceId']
        connect_ri_json = router_interface.connect_router_interface(params)
        CommonUtil.log("connect_router_interface", connect_ri_json)
    
        # 创建下一跳为发起端路由器接口的路由条目
        params['route_table_id'] = route_table_json["RouteTables"]["RouteTable"][0]["RouteTableId"]
        params['destination_cidr_block'] = "0.0.0.0/0"
        params['nexthop_type'] = 'RouterInterface'
        params['nexthop_id'] = router_interface_json['RouterInterfaceId']
        route_entry_json = route_entry.create_route_entry(params)
        CommonUtil.log("create_route_entry", route_entry_json)
    
        # 创建下一跳为接收端路由器接口的路由条目
        params['route_table_id'] = TABLE_ID2
        params['destination_cidr_block'] = "0.0.0.0/0"
        params['nexthop_type'] = 'RouterInterface'
        params['nexthop_id'] = router_interface_json2['RouterInterfaceId']
        route_entry_json2 = route_entry.create_route_entry(params)
        CommonUtil.log("create_route_entry", route_entry_json2)
    
        # 删除下一跳为接收端路由器接口的路由条目
        route_entry_json = route_entry.delete_route_entry(params)
        CommonUtil.log("delete_route_entry", route_entry_json)
    
        # 删除下一跳为发起端路由器接口的路由条目
        params['route_table_id'] = route_table_json["RouteTables"]["RouteTable"][0]["RouteTableId"]
        params['nexthop_id'] = router_interface_json['RouterInterfaceId']
        route_entry_json = route_entry.delete_route_entry(params)
        CommonUtil.log("delete_route_entry", route_entry_json)
    
        # 冻结发起端路由器接口
        params['router_interface_id'] = router_interface_json['RouterInterfaceId']
        deactivate_ri_json = router_interface.deactivate_router_interface(params)
        CommonUtil.log("deactivate_router_interface", deactivate_ri_json)
    
        # 冻结接收端路由器接口
        params['router_interface_id'] = router_interface_json2['RouterInterfaceId']
        deactivate_ri_json2 = router_interface.deactivate_router_interface(params)
        CommonUtil.log("deactivate_router_interface", deactivate_ri_json2)
    
        # 删除发起端路由器接口
        params['instance_id'] = router_interface_json['RouterInterfaceId']
        router_interface_json = router_interface.delete_router_interface(params)
        CommonUtil.log("delete_router_interface", router_interface_json)
    
        # 删除接收端路由器接口
        params['instance_id'] = router_interface_json2['RouterInterfaceId']
        router_interface_json2 = router_interface.delete_router_interface(params)
        CommonUtil.log("delete_router_interface", router_interface_json2)
    
        # 删除边界路由器边界路由器
        params['vbr_id'] = vbr_json['VbrId']
        vbr_json = router_interface.delete_virtual_border_router(params)
        CommonUtil.log("delete_virtual_border_router", vbr_json)
    
    if __name__ == '__main__':
        sys.exit(main())
    					
    ```

5.  进入ec\_vbr\_vpc.py所在的目录，执行如下命令，实现同账号同地域下的VBR与VPC互通。 

    ``` {#codeblock_l33_bp3_6fw}
    python ec_vbr_vpc.py
    ```

    系统显示类似如下：

    ``` {#codeblock_dt6_xme_zns}
    ---------------------------create_virtual_border_router---------------------------
    {
      "VbrId": "vbr-bp1vudncgk9jtxxxxxxxx", 
      "RequestId": "0C4FABDB-FF18-4E70-9E43-6DC03197F0EA"
    }
    ---------------------------create_router_interface---------------------------
    {
      "RequestId": "11F14FA2-ECFA-4B27-A75D-7C6D5FECACDF", 
      "RouterInterfaceId": "ri-bp1vabte8nbdexxxxxxxx"
    }
    ---------------------------create_router_interface---------------------------
    {
      "RequestId": "72FAB86D-470B-40E4-8476-F9223A911486", 
      "RouterInterfaceId": "ri-bp1mxkc61ly0nxxxxxxxx"
    }
    ---------------------------modify_router_interface_attribute---------------------------
    {
      "RequestId": "93D5FFF7-6C05-41B1-92F0-AC8F1809BC98"
    }
    ---------------------------modify_router_interface_attribute---------------------------
    {
      "RequestId": "1C461452-42BD-4649-B318-2214222B4FCA"
    }
    ---------------------------describe_router_interface---------------------------
    {
      "TotalCount": 1, 
      "RouterInterfaceSet": {
        "RouterInterfaceType": [
          {
            "BusinessStatus": "Normal", 
            "CreationTime": "2019-04-30T02:54:22Z", 
            "AccessPointId": "ap-cn-hangzhou-xx-x", 
            "Role": "InitiatingSide", 
            "OppositeRouterId": "vrt-bp141no9pds2bxxxxxxxx", 
            "Spec": "Large.2", 
            "Status": "Idle", 
            "EndTime": "2999-09-08T16:00:00Z", 
            "OppositeInterfaceSpec": "Negative", 
            "RouterInterfaceId": "ri-bp1vabte8nbdexxxxxxxx", 
            "RouterType": "VBR", 
            "OppositeBandwidth": 0, 
            "OppositeVpcInstanceId": "vpc-bp1v31by9jix2xxxxxxxx", 
            "HasReservationData": false, 
            "OppositeInterfaceBusinessStatus": "Normal", 
            "OppositeRouterType": "VRouter", 
            "OppositeRegionId": "cn-hangzhou", 
            "RouterId": "vbr-bp1vudncgk9jtxxxxxxxx", 
            "CrossBorder": false, 
            "OppositeInterfaceOwnerId": "", 
            "Bandwidth": 2048, 
            "OppositeInterfaceId": "ri-bp1mxkc61ly0nxxxxxxxx", 
            "ChargeType": "AfterPay"
          }
        ]
      }, 
      "PageNumber": 1, 
      "RequestId": "3553DB38-A4A0-4453-976C-542E96B1B5A9", 
      "PageSize": 10
    }
    ---------------------------describe_router_interface---------------------------
    {
      "TotalCount": 1, 
      "RouterInterfaceSet": {
        "RouterInterfaceType": [
          {
            "Status": "Idle", 
            "OppositeRegionId": "cn-hangzhou", 
            "BusinessStatus": "Normal", 
            "OppositeRouterId": "vbr-bp1vudncgk9jtxxxxxxxx", 
            "VpcInstanceId": "vpc-bp1v31by9jix2xxxxxxxx", 
            "RouterInterfaceId": "ri-bp1mxkc61ly0nxxxxxxxx", 
            "CreationTime": "2019-04-30T02:54:24Z", 
            "RouterType": "VRouter", 
            "OppositeInterfaceOwnerId": "", 
            "RouterId": "vrt-bp141no9pds2bxxxxxxxx", 
            "Bandwidth": 0, 
            "OppositeInterfaceId": "ri-bp1vabte8nbdexxxxxxxx", 
            "EndTime": "2999-09-08T16:00:00Z", 
            "ChargeType": "AfterPay", 
            "OppositeAccessPointId": "ap-cn-hangzhou-xx-x", 
            "HasReservationData": false, 
            "CrossBorder": false, 
            "OppositeInterfaceBusinessStatus": "Normal", 
            "Spec": "Negative", 
            "OppositeRouterType": "VBR", 
            "Role": "AcceptingSide"
          }
        ]
      }, 
      "PageNumber": 1, 
      "RequestId": "217D8D94-C508-4285-8101-7DE3B53A88A5", 
      "PageSize": 10
    }
    ---------------------------describe_route_table---------------------------
    {
      "TotalCount": 1, 
      "PageNumber": 1, 
      "RequestId": "CA6BBE52-DF5E-496A-93CF-9857AF22D2AC", 
      "PageSize": 10, 
      "RouteTables": {
        "RouteTable": [
          {
            "RouteTableId": "vtb-bp1s126yz0swpxxxxxxxx", 
            "RouteEntrys": {
              "RouteEntry": []
            }, 
            "CreationTime": "2019-04-30T02:54:19Z", 
            "VSwitchIds": {
              "VSwitchId": []
            }, 
            "ResourceGroupId": "", 
            "VRouterId": "vbr-bp1vudncgk9jtxxxxxxxx", 
            "RouteTableType": "System"
          }
        ]
      }
    }
    ---------------------------connect_router_interface---------------------------
    {
      "RequestId": "93476D4E-6C08-44B8-83E4-5759E1A08F29"
    }
    ---------------------------create_route_entry---------------------------
    {
      "RequestId": "66D4F46B-5E0F-4565-8740-845EC26EBE00"
    }
    ---------------------------create_route_entry---------------------------
    {
      "RequestId": "E1F99FEF-2499-40A7-84ED-6F9D440D4FF8"
    }
    ---------------------------delete_route_entry---------------------------
    {
      "RequestId": "8C983886-F058-4234-A6D7-ECDEE2C2D945"
    }
    ---------------------------delete_route_entry---------------------------
    {
      "RequestId": "DDEC56B9-CDD4-4D0A-B460-040B85B97FE9"
    }
    ---------------------------deactivate_router_interface---------------------------
    {
      "RequestId": "04069B7C-6A42-43F2-A086-50F802940045"
    }
    ---------------------------deactivate_router_interface---------------------------
    {
      "RequestId": "B2EBF829-E1C0-43E5-9BAD-DFFCBFA301F7"
    }
    ---------------------------delete_router_interface---------------------------
    {
      "RequestId": "20EEC4A6-E468-4F3C-A743-89193F7504E1"
    }
    ---------------------------delete_router_interface---------------------------
    {
      "RequestId": "59DCE168-B9CC-43A3-A54F-0D8C194BABE0"
    }
    ---------------------------delete_virtual_border_router---------------------------
    {
      "RequestId": "E1D71EEC-FE9F-4834-8780-19EBBD91A638"
    }
    ```


