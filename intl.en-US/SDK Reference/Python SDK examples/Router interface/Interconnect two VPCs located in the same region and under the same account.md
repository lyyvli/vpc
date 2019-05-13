# Interconnect two VPCs located in the same region and under the same account {#task_222315 .task}

This topic describes how to use the Alibaba Cloud Python SDK to interconnect two VPCs that are located in the same region and are under the same account.

Note the following when you create router interfaces:

-   Only one pair of interconnected router interfaces can be created between two VRouters.
-   Up to five router interfaces can be created on a VRouter.
-   If a router interface with overdue payment is under your account, you cannot create router interfaces. To resolve this issue, add funds to your account.
-   Route entries in the same route table cannot have the same destination CIDR blocks.

The detailed steps used in this tutorial to interconnect two VPCs located in the same region and under the same account are as follows:

1.  Create the initiator router interface.
2.  Create the acceptor router interface.
3.  Modify the initiator router interface.
4.  Modify the acceptor router interface.
5.  Query the initiator router interface.
6.  Query the acceptor router interface.
7.  Connect the initiator router interface to the acceptor router interface.
8.  Create a route entry whose next hop is the initiator router interface.
9.  Create a route entry whose next hop is the acceptor router interface.
10. Delete the route entry whose next hop is the acceptor router interface.
11. Delete the route entry whose next hop is the initiator router interface.
12. Deactivate the initiator router interface.
13. Deactivate the acceptor router interface.
14. Delete the initiator router interface.
15. Delete the acceptor router interface.

1.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\sdk\_lib folder.
2.  Open the consts.py file in your text editor and configure the ACS\_CLIENT parameter used for user authentication.
3.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\ec folder.
4.  Open the ec\_same\_account.py file in your text editor and configure your required parameters. Then, save the configurations and exit the text editor. 

    ``` {#codeblock_eqg_5a5_35i}
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
                # The ID of the VRouter associated with the router interface
                request.set_RouterId(params['router_id'])
                # The type of the VRouter associated with the router interface
                request.set_RouterType(params['router_type'])
                # The ID of the region to which the connection acceptor belongs
                request.set_OppositeRegionId(params['opposite_region_id'])
                # The type of the VRouter associated with the peer router interface
                request.set_OppositeRouterType(params['opposite_router_type'])
    
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
                # The ID of the peer VRouter
                request.set_OppositeRouterId(params['opposite_router_id'])
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
            describe_ri_status:  Query the status of router interfaces in a region
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
    
    def main():
        client = ACS_CLIENT
        router_interface = RouterInterface(client)
        route_entry = RouteEntry(client)
    
        params = {}
        params['spec'] = "Large.2"
        params['role'] = "InitiatingSide"
        params['router_id'] = ROUTER_ID
        params['router_type'] = "VRouter"
        params['opposite_region_id'] = "cn-hangzhou"
        params['opposite_router_type'] = "VRouter"
    
        # Create the initiator router interface
        router_interface_json = router_interface.create_router_interface(params)
        CommonUtil.log("create_router_interface", router_interface_json)
    
        # Create the acceptor router interface
        params['spec'] = "Negative"
        params['role'] = "AcceptingSide"
        params['router_id'] = ROUTER_ID2
        router_interface_json2 = router_interface.create_router_interface(params)
        CommonUtil.log("create_router_interface", router_interface_json2)
    
        # Modify the initiator router interface
        params['router_interface_id'] = router_interface_json['RouterInterfaceId']
        params['opposite_interface_id'] = router_interface_json2['RouterInterfaceId']
        params['opposite_router_id'] = ROUTER_ID2
        modify_ri_json = router_interface.modify_router_interface_attribute(params)
        CommonUtil.log("modify_router_interface_attribute", modify_ri_json)
    
        # Modify the acceptor router interface
        params['router_interface_id'] = router_interface_json2['RouterInterfaceId']
        params['opposite_interface_id'] = router_interface_json['RouterInterfaceId']
        params['opposite_router_id'] = ROUTER_ID
        modify_ri_json2 = router_interface.modify_router_interface_attribute(params)
        CommonUtil.log("modify_router_interface_attribute", modify_ri_json2)
    
        # Query the initiator router interface
        describe_ri_json = router_interface.describe_router_interface(router_interface_json['RouterInterfaceId'])
        CommonUtil.log("describe_router_interface", describe_ri_json)
    
        # Query the acceptor router interface
        describe_ri_json2 = router_interface.describe_router_interface(router_interface_json2['RouterInterfaceId'])
        CommonUtil.log("describe_router_interface", describe_ri_json2)
    
        # Initiate the connection
        params['router_interface_id'] = router_interface_json['RouterInterfaceId']
        connect_ri_json = router_interface.connect_router_interface(params)
        CommonUtil.log("connect_router_interface", connect_ri_json)
    
        # Create a route entry whose next hop is the initiator router interface
        params['route_table_id'] = TABLE_ID
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
        params['route_table_id'] = TABLE_ID
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
    
    
    if __name__ == '__main__':
        sys.exit(main())
    					
    ```

5.  Access the ec\_same\_account.py directory and run the following command to interconnect two VPCs that are located in the same region and are under the same account. 

    ``` {#codeblock_5ry_ghp_jxe}
    python ec_same_account.py
    ```

    The system displays the following output:

    ``` {#codeblock_uqd_msr_kms}
    ---------------------------create_router_interface---------------------------
    {
      "RequestId": "F5493DC1-53B0-4916-874F-87773A54525F", 
      "RouterInterfaceId": "ri-bp1ujwb6xsw16xxxxxxxx"
    }
    ---------------------------create_router_interface---------------------------
    {
      "RequestId": "E3F5BE99-B2C5-4751-8173-0F590300EE72", 
      "RouterInterfaceId": "ri-bp1vze2rusg2cxxxxxxxx"
    }
    ---------------------------modify_router_interface_attribute---------------------------
    {
      "RequestId": "8D691507-F31A-41E5-9C72-457EFF1F7727"
    }
    ---------------------------modify_router_interface_attribute---------------------------
    {
      "RequestId": "2E664208-8F37-4F19-B719-00B4F1AF03B2"
    }
    ---------------------------describe_router_interface---------------------------
    {
      "TotalCount": 1, 
      "RouterInterfaceSet": {
        "RouterInterfaceType": [
          {
            "BusinessStatus": "Normal", 
            "CreationTime": "2019-04-30T06:09:16Z", 
            "Role": "InitiatingSide", 
            "OppositeRouterId": "vrt-bp141no9pds2bxxxxxxxx", 
            "Spec": "Large.2", 
            "Status": "Idle", 
            "EndTime": "2999-09-08T16:00:00Z", 
            "OppositeInterfaceSpec": "Negative", 
            "RouterInterfaceId": "ri-bp1ujwb6xsw16xxxxxxxx", 
            "RouterType": "VRouter", 
            "OppositeBandwidth": 0, 
            "OppositeVpcInstanceId": "vpc-bp1v31by9jix2xxxxxxxx", 
            "HasReservationData": false, 
            "OppositeInterfaceBusinessStatus": "Normal", 
            "OppositeRouterType": "VRouter", 
            "OppositeRegionId": "cn-hangzhou", 
            "VpcInstanceId": "vpc-bp15opprpg0rgxxxxxxxx", 
            "RouterId": "vrt-bp1ltkytn6lgmxxxxxxxx", 
            "CrossBorder": false, 
            "OppositeInterfaceOwnerId": "", 
            "Bandwidth": 2048, 
            "OppositeInterfaceId": "ri-bp1vze2rusg2cxxxxxxxx", 
            "ChargeType": "AfterPay"
          }
        ]
      }, 
      "PageNumber": 1, 
      "RequestId": "89EF0631-0A36-41AD-A586-AF4FFDA6E68B", 
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
            "OppositeRouterId": "vrt-bp1ltkytn6lgmxxxxxxxx", 
            "VpcInstanceId": "vpc-bp1v31by9jix2xxxxxxxx", 
            "RouterInterfaceId": "ri-bp1vze2rusg2cxxxxxxxx", 
            "CreationTime": "2019-04-30T06:09:18Z", 
            "RouterType": "VRouter", 
            "OppositeInterfaceOwnerId": "", 
            "RouterId": "vrt-bp141no9pds2bxxxxxxxx", 
            "Bandwidth": 0, 
            "OppositeInterfaceId": "ri-bp1ujwb6xsw16xxxxxxxx", 
            "EndTime": "2999-09-08T16:00:00Z", 
            "ChargeType": "AfterPay", 
            "OppositeVpcInstanceId": "vpc-bp15opprpg0rgxxxxxxxx", 
            "HasReservationData": false, 
            "CrossBorder": false, 
            "OppositeInterfaceBusinessStatus": "Normal", 
            "Spec": "Negative", 
            "OppositeRouterType": "VRouter", 
            "Role": "AcceptingSide"
          }
        ]
      }, 
      "PageNumber": 1, 
      "RequestId": "578448D7-9DCF-4703-8337-EF88DDF2C325", 
      "PageSize": 10
    }
    ---------------------------connect_router_interface---------------------------
    {
      "RequestId": "A5DBB86B-F6F5-4A53-899E-8CF4FEF510F2"
    }
    ---------------------------create_route_entry---------------------------
    {
      "RequestId": "70D896FE-986B-48EF-9734-17D6BDC8327A"
    }
    ---------------------------create_route_entry---------------------------
    {
      "RequestId": "A2233E25-4D6B-4713-A96F-E7CA745973CA"
    }
    ---------------------------delete_route_entry---------------------------
    {
      "RequestId": "464C62A4-EE65-4414-AF0A-4984AE6B8696"
    }
    --------------------------delete_route_entry---------------------------
    {
      "RequestId": "0C11A332-969B-47CA-A683-5BFFECA28B3D"
    }
    ---------------------------deactivate_router_interface---------------------------
    {
      "RequestId": "018305AD-FB9E-450A-91E8-3830634F5AC2"
    }
    ---------------------------deactivate_router_interface---------------------------
    {
      "RequestId": "89B03203-9224-4CA3-8679-E0A49029A2D2"
    }
    ---------------------------delete_router_interface---------------------------
    {
      "RequestId": "FB0424CE-D0C7-438B-A3FA-BCF24EE9CC8A"
    }
    ---------------------------delete_router_interface---------------------------
    {
      "RequestId": "8A0A0BB6-A69D-461B-A117-14AD6670DECA"
    }
    ```


