# Interconnect a VBR and a VPC in the same region and under the same account {#task_226442 .task}

This topic describes how to use the Alibaba Cloud Python SDK to interconnect a VBR and a VPC that are located in the same region and are under the same account.

Before interconnect a VBR and a VPC under the same account and in the same region, you must ensure that:

-   A physical connection interface is applied.

**Note:** Your physical connection interface and VPC must be under the same account and in the same region.

Note the following when you create router interfaces:

-   Only one pair of interconnected router interfaces can be created between two routers.
-   Up to five router interfaces can be created on a router.
-   If a router interface with an overdue payment is under your account, you cannot create router interfaces. To resolve this issue, add funds to your account.
-   Route entries in the same route table cannot have the same destination CIDR blocks.
-   The VBR must operate as the connection initiator and be in the Activated state.

The detailed steps used in this tutorial to interconnect a VBR and a VPC located in the same region and under the same account are as follows:

1.  Create a VBR.
2.  Create the initiator router interface.
3.  Create the acceptor router interface.
4.  Modify the initiator router interface.
5.  Modify the acceptor router interface.
6.  Query the initiator router interface.
7.  Query the acceptor router interface.
8.  Query the ID of the route table in the VBR.
9.  Connect the initiator router interface to the acceptor router interface.
10. Create a route entry whose next hop is the initiator router interface.
11. Create a route entry whose next hop is the acceptor router interfac
12. Delete the route entry whose next hop is the acceptor router interface.
13. Delete the route entry whose next hop is the initiator router interface.
14. Deactivate the initiator router interface.
15. Deactivate the acceptor router interface.
16. Delete the initiator router interface.
17. Delete the acceptor router interface.
18. Delete the VBR.

1.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\sdk\_lib folder.
2.  Open the consts.py file in your text editor and configure the ACS\_CLIENT parameter used for user authentication.
3.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\ec folder.
4.  Open the ec\_vbr\_vpc.py file in your text editor and configure your required parameters. Then, save the configurations and exit the text editor. 

    ``` {#codeblock_glz_ibx_ran}
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
            create_router_interface: Create a router interface
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36032.htm
            """
            try:
                request = CreateRouterInterfaceRequest.CreateRouterInterfaceRequest()
                # The specification of the router interface
                request.set_Spec(params['spec'])
                # The role of the router interface
                request.set_Role(params['role'])
                # The ID of the router associated with the router interface
                request.set_RouterId(params['router_id'])
                # The type of the router associated with the router interface
                request.set_RouterType(params['router_type'])
                # The ID of the region to which the connection acceptor belongs
                request.set_OppositeRegionId(params['opposite_region_id'])
                # The type of the router associated with the peer router interface
                request.set_OppositeRouterType(params['opposite_router_type'])
                # The ID of the access point to which the peer end belongs
                request.set_OppositeAccessPointId(params['opposite_access_point_id'])
                # The ID of the access point to which the VBR belongs
                #request.set_AccessPointId(params['access_point_id'])
    
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # Check if the router interface is in the available state
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
            create_router_interface: Create a router interface
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36032.htm
            """
            try:
                request = CreateRouterInterfaceRequest.CreateRouterInterfaceRequest()
                # The specification of the router interface
                request.set_Spec(params['spec'])
                # The role of the router interface
                request.set_Role(params['role'])
                # The ID of the router associated with the router interface
                request.set_RouterId(params['router_id'])
                # The type of the router associated with the router interface
                request.set_RouterType(params['router_type'])
                # The ID of the region to which the connection acceptor belongs
                request.set_OppositeRegionId(params['opposite_region_id'])
                # The type of the router associated with the peer router interface
                request.set_OppositeRouterType(params['opposite_router_type'])
                # The ID of the access point to which the VBR belongs
                request.set_AccessPointId(params['access_point_id'])
    
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # Check if the router interface is in the available state
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
            connect_router_interface: The initiator router interface initiates the connection to the acceptor router interface
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36031.htm
            """
            try:
                request = ConnectRouterInterfaceRequest.ConnectRouterInterfaceRequest()
                # The ID of the initiator router interface
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
            deactivate_router_interface: Deactivate a router interface
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36033.htm
            """
            try:
                request = DeactivateRouterInterfaceRequest.DeactivateRouterInterfaceRequest()
                # The ID of the router interface
                request.set_RouterInterfaceId(params['router_interface_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # Check if the router interface is in the available state
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
            modify_router_interface_attribute: Modify the configurations of a router interface
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36036.htm
            """
            try:
                request = ModifyRouterInterfaceAttributeRequest.ModifyRouterInterfaceAttributeRequest()
                # The ID of the router interface
                request.set_RouterInterfaceId(params['router_interface_id'])
                # The ID of the peer router interface
                request.set_OppositeInterfaceId(params['opposite_interface_id'])
                # The ID of the peer router
                request.set_OppositeRouterId(params['opposite_router_id'])
                # The type of the peer router
                request.set_OppositeRouterType(params['opposite_router_type'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # Check if the router interface is in the available state
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
            describe_router_interface: Query router interfaces in a region
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36035.htm
            """
            try:
                request = DescribeRouterInterfacesRequest.DescribeRouterInterfacesRequest()
                # The queried filter type
                request.add_query_param('Filter.1.Key', "RouterInterfaceId")
                # The queried instance ID
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
            describe_ri_status: Query the status of router interfaces in a region
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36035.htm
            """
            response = self.describe_router_interface(instance_id)
            if len(response['RouterInterfaceSet']['RouterInterfaceType']) == 0:
                return ''
            return response['RouterInterfaceSet']['RouterInterfaceType'][0]['Status']
    
        def delete_router_interface(self, params):
            """
            delete_router_interface: Delete a router interface
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36034.htm
            """
            try:
                request = DeleteRouterInterfaceRequest.DeleteRouterInterfaceRequest()
                # The ID of the router interface
                request.set_RouterInterfaceId(params['instance_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # Check if the router interface is in the available state
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
            create_virtual_border_router: Create a VBR
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36023.htm
            """
            try:
                request = CreateVirtualBorderRouterRequest.CreateVirtualBorderRouterRequest()
                # The ID of the physical connection
                request.set_PhysicalConnectionId(params['physical_connection_id'])
                # The Alibaba Cloud-side IP address of the VBR
                request.set_LocalGatewayIp(params['local_gateway_ip'])
                # The peer IP address of the physical connection-side interface of the VBR
                request.set_PeerGatewayIp(params['peer_gateway_ip'])
                # The subnet mask for the Alibaba Cloud-side and customer-side IP addresses of the VBR
                request.set_PeeringSubnetMask(params['peering_subnet_mask'])
                # The VLAN ID of the VBR
                request.set_VlanId(params['vlan_id'])
    
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # Check if the VBR is in the available state
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
            delete_virtual_border_router: Delete a VBR
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/40542.htm
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
            describe_virtual_border_router: Query VBRs
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36024.htm
            """
            try:
                request = DescribeVirtualBorderRoutersRequest.DescribeVirtualBorderRoutersRequest()
                # The queried filter type
                request.add_query_param('Filter.1.Key', "VbrId")
                # The queried instance ID
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
            describe_virtual_border_router: Query the status of VBRs
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36024.htm
            """
            response = self.describe_virtual_border_router(instance_id)
            if len(response['VirtualBorderRouterSet']['VirtualBorderRouterType']) == 0:
                return ''
            return response['VirtualBorderRouterSet']['VirtualBorderRouterType'][0]['Status']
    
        def describe_route_table(self, params):
            """
            describe_route_table: Query route tables
             API reference link: https://partners-intl.aliyun.com/help/doc-detail/36014.htm
            """
            try:
                request = DescribeRouteTablesRequest.DescribeRouteTablesRequest()
                # The ID of the VRouter or VBR to which the route table belongs
                request.set_RouterId(params['router_id'])
                # The type of the router to which the route table belongs
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
    
        # Create a VBR
        params['physical_connection_id'] = PC_ID
        params['local_gateway_ip'] = "116.xx.xx.254"
        params['peer_gateway_ip'] = "116.xx.xx.254"
        params['peering_subnet_mask'] = "255.255.255.252"
        params['vlan_id'] = 30
        vbr_json = router_interface.create_virtual_border_router(params)
        CommonUtil.log("create_virtual_border_router", vbr_json)
    
        # Create an initiator router interface
        params['router_id'] = vbr_json['VbrId']
        router_interface_json = router_interface.create_router_interface_vbr(params)
        CommonUtil.log("create_router_interface", router_interface_json)
    
        # Create an acceptor router interface
        params['router_type'] = "VRouter"
        params['spec'] = "Negative"
        params['role'] = "AcceptingSide"
        params['router_id'] = ROUTER_ID2
        params['opposite_router_type'] = 'VBR'
        params['opposite_access_point_id'] = params['access_point_id']
        router_interface_json2 = router_interface.create_router_interface(params)
        CommonUtil.log("create_router_interface", router_interface_json2)
    
        # Modify the initiator router interface
        params['router_interface_id'] = router_interface_json['RouterInterfaceId']
        params['opposite_interface_id'] = router_interface_json2['RouterInterfaceId']
        params['opposite_router_id'] = ROUTER_ID2
        params['opposite_router_type'] = "VRouter"
        modify_ri_json = router_interface.modify_router_interface_attribute(params)
        CommonUtil.log("modify_router_interface_attribute", modify_ri_json)
    
        # Modify the acceptor router interface
        params['router_interface_id'] = router_interface_json2['RouterInterfaceId']
        params['opposite_interface_id'] = router_interface_json['RouterInterfaceId']
        params['opposite_router_id'] = vbr_json['VbrId']
        params['opposite_router_type'] = "VBR"
        modify_ri_json2 = router_interface.modify_router_interface_attribute(params)
        CommonUtil.log("modify_router_interface_attribute", modify_ri_json2)
    
        # Query the initiator router interface
        describe_ri_json = router_interface.describe_router_interface(router_interface_json['RouterInterfaceId'])
        CommonUtil.log("describe_router_interface", describe_ri_json)
    
        # Query the acceptor router interface
        describe_ri_json2 = router_interface.describe_router_interface(router_interface_json2['RouterInterfaceId'])
        CommonUtil.log("describe_router_interface", describe_ri_json2)
    
        # Query the ID of the route table of the VBR
        params['router_id'] = vbr_json['VbrId']
        params['router_type'] = 'VBR'
        route_table_json = router_interface.describe_route_table(params)
        CommonUtil.log("describe_route_table", route_table_json)
    
        # Initiate the connection
        params['router_interface_id'] = router_interface_json['RouterInterfaceId']
        connect_ri_json = router_interface.connect_router_interface(params)
        CommonUtil.log("connect_router_interface", connect_ri_json)
    
        # Create a route entry whose next hop is the initiator router interface
        params['route_table_id'] = route_table_json["RouteTables"]["RouteTable"][0]["RouteTableId"]
        params['destination_cidr_block'] = "0.0.0.0/0"
        params['nexthop_type'] = 'RouterInterface'
        params['nexthop_id'] = router_interface_json['RouterInterfaceId']
        route_entry_json = route_entry.create_route_entry(params)
        CommonUtil.log("create_route_entry", route_entry_json)
    
        # Create a route entry whose next hop is the acceptor router interface
        params['route_table_id'] = TABLE_ID2
        params['destination_cidr_block'] = "0.0.0.0/0"
        params['nexthop_type'] = 'RouterInterface'
        params['nexthop_id'] = router_interface_json2['RouterInterfaceId']
        route_entry_json2 = route_entry.create_route_entry(params)
        CommonUtil.log("create_route_entry", route_entry_json2)
    
        # Delete the route entry whose next hop is the acceptor router interface
        route_entry_json = route_entry.delete_route_entry(params)
        CommonUtil.log("delete_route_entry", route_entry_json)
    
        # Delete the route entry whose next hop is the initiator router interface
        params['route_table_id'] = route_table_json["RouteTables"]["RouteTable"][0]["RouteTableId"]
        params['nexthop_id'] = router_interface_json['RouterInterfaceId']
        route_entry_json = route_entry.delete_route_entry(params)
        CommonUtil.log("delete_route_entry", route_entry_json)
    
        # Deactivate the initiator router interface
        params['router_interface_id'] = router_interface_json['RouterInterfaceId']
        deactivate_ri_json = router_interface.deactivate_router_interface(params)
        CommonUtil.log("deactivate_router_interface", deactivate_ri_json)
    
        # Deactivate the acceptor router interface
        params['router_interface_id'] = router_interface_json2['RouterInterfaceId']
        deactivate_ri_json2 = router_interface.deactivate_router_interface(params)
        CommonUtil.log("deactivate_router_interface", deactivate_ri_json2)
    
        # Delete the initiator router interface
        params['instance_id'] = router_interface_json['RouterInterfaceId']
        router_interface_json = router_interface.delete_router_interface(params)
        CommonUtil.log("delete_router_interface", router_interface_json)
    
        # Delete the acceptor router interface
        params['instance_id'] = router_interface_json2['RouterInterfaceId']
        router_interface_json2 = router_interface.delete_router_interface(params)
        CommonUtil.log("delete_router_interface", router_interface_json2)
    
        # Delete the VBR
        params['vbr_id'] = vbr_json['VbrId']
        vbr_json = router_interface.delete_virtual_border_router(params)
        CommonUtil.log("delete_virtual_border_router", vbr_json)
    
    if __name__ == '__main__':
        sys.exit(main())
    					
    ```

5.  Access the ec\_vbr\_vpc.py directory and run the following command to interconnect a VBR and a VPC that are located in the same region and are under the same account. 

    ``` {#codeblock_l33_bp3_6fw}
    python ec_vbr_vpc.py
    ```

    The system displays the following output:

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


