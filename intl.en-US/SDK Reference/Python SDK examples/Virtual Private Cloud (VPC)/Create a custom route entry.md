# Create a custom route entry {#task_e2p_5s5_jhb .task}

This topic describes how to use the Alibaba Cloud Python SDK to create a custom route entry on a VRouter or VBR.

Before you can create a custom route entry, you need to ensure that:

-   A VPC and a VSwitch are created in the China \(Zhangjiakou\) region.
-   The next hop for the custom route entry is created in the China \(Zhangjiakou\) region. The next hop can be an ECS instance, an HAVIP, a VPN Gateway, a NAT Gateway, an ENI, or a router interface.

The detailed steps used in this tutorial to create a custom route entry are as follows:

1.  Create a custom route table named sdk\_route\_table in the China \(Zhangjiakou\) region.
2.  Query the VSwitches under the VPC vpc-8vb7ztbjqomi9xxxxxxxx.
3.  Associate the custom route table with the VSwitch vsw-8vbfqpcijj0d1xxxxxxxx.
4.  Add a custom route entry to the custom route table. The destination CIDR block of the entry is 168.168.0.0/16, the type of the next hop is ECS instance, and the ID of the next hop is i-8vbgsnt7046axxxxxxxx.
5.  Delete the route entry.
6.  Disassociate the custom route table from the VSwitch.
7.  Delete the custom route table.

1.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\sdk\_lib folder.
2.  Open the consts.py file in your text editor and configure the ACS\_CLIENT parameter used for user authentication.
3.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\vpc folder.
4.  Open the vpc\_route\_entry.py file in your editor and configure your required parameters. Then, save the configurations and exit the editor. 

    ``` {#codeblock_mgt_gmy_05p}
    #encoding=utf-8
    import sys
    import json
    import time
    
    from aliyunsdkcore.acs_exception.exceptions import ServerException, ClientException
    from aliyunsdkvpc.request.v20160428 import CreateRouteEntryRequest
    from aliyunsdkvpc.request.v20160428 import DeleteRouteEntryRequest
    from aliyunsdkvpc.request.v20160428 import DescribeRouteTablesRequest
    from sdk_lib.exception import ExceptionHandler
    from sdk_lib.check_status import CheckStatus
    from sdk_lib.common_util import CommonUtil
    from sdk_lib.sdk_vswitch import VSwitch
    from sdk_lib.sdk_route_table import RouteTable
    from sdk_lib.consts import *
    
    class RouteEntry(object):
        def __init__(self, client):
            self.client = client
    
        def create_route_entry(self, params):
            """
            create_route_entry: Create a route entry
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36012.htm
            """
            try:
                request = CreateRouteEntryRequest.CreateRouteEntryRequest()
                # The ID of the route table
                request.set_RouteTableId(params['route_table_id'])
                # The destination CIDR block of the custom route entry
                request.set_DestinationCidrBlock(params['destination_cidr_block'])
                # The type of the next hop
                request.set_NextHopType(params['nexthop_type'])
                # The ID of the instance used as the next hop
                request.set_NextHopId(params['nexthop_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # Check if the route entry is in the available state
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_route_entry_status,
                                            AVAILABLE, params['route_table_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def delete_route_entry(self, params):
            """
            delete_route_entry: Delete the route entry
             API reference link: https://partners-intl.aliyun.com/help/doc-detail/36013.htm
            """
            try:
                request = DeleteRouteEntryRequest.DeleteRouteEntryRequest()
                # The ID of the route table to which the route entry belongs
                request.set_RouteTableId(params['route_table_id'])
                # he destination CIDR block of the route entry
                request.set_DestinationCidrBlock(params['destination_cidr_block'])
                # The ID of the instance used as the next hop
                request.set_NextHopId(params['nexthop_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                time.sleep(DEFAULT_TIME)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_route_entry_vrouter(self, params):
            """
            describe_route_entry_vrouter: Query the route entry
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36014.htm
            """
            try:
                request = DescribeRouteTablesRequest.DescribeRouteTablesRequest()
                # The ID of the VRouter or VBR to which the route table belongs
                request.set_VRouterId(params['vrouter_id'])
                # The ID of the route table
                request.set_RouteTableId(params['route_table_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_route_entry(self, route_table_id):
            """
            describe_route_entry: Query the route entry
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36014.htm
            """
            try:
                request = DescribeRouteTablesRequest.DescribeRouteTablesRequest()
                request.set_RouteTableId(route_table_id)
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_route_entry_status(self, route_table_id):
            """
            describe_route_entry_status: Query the status of the route entry
            """
            response = self.describe_route_entry(route_table_id)
            return response["RouteTables"]["RouteTable"][0]["RouteEntrys"]["RouteEntry"][0]["Status"]
    
    def main():
        client = ACS_CLIENT
        vswitch = VSwitch(client)
        route_table = RouteTable(client)
        route_entry = RouteEntry(client)
    
        params = {}
        params['route_table_name'] = "sdk_route_table"
        params['destination_cidr_block'] = "0.0.0.0/0"
        params['nexthop_id'] = "i-bp1e82xlhob2xxxxxxxx"
        params['nexthop_type'] = "Instance"
    
        params['vpc_id'] = "vpc-bp15opprpg0rgxxxxxxxx"
        params['vswitch_id'] = "vsw-bp1e67w26n2sjxxxxxxxx"
    
        #Create a route table
        route_table_json = route_table.create_route_table(params)
        CommonUtil.log("create_route_table", route_table_json)
    
        #Query the vswitch
        vswitch_json = vswitch.describe_vswitch_attribute(params)
        CommonUtil.log("describe_vswitch_attribute", vswitch_json)
    
        #Associate the route table with the vswitch
        params['route_table_id'] = route_table_json['RouteTableId']
        associate_json = route_table.associate_route_table(params)
        CommonUtil.log("associate_route_table", associate_json)
    
        #Create a route entry
        create_route_entry_json = route_entry.create_route_entry(params)
        CommonUtil.log("create_route_entry", create_route_entry_json)
        
        #Create a route entry
        delete_route_entry_json = route_entry.delete_route_entry(params)
        CommonUtil.log("delete_route_entry", delete_route_entry_json)
    
        #Disassociate the route table from the vswitch
        unassociate_json = route_table.unassociate_route_table(params)
        CommonUtil.log("unassociate_route_table", unassociate_json)
    
        #Delete the route table
        delete_route_table_json = route_table.delete_route_table(params)
        CommonUtil.log("delete_route_table", delete_route_table_json)
    
    
    if __name__ == "__main__":
        sys.exit(main())
    ```

5.  Access the vpc\_route\_entry.py directory and run the following command to create a custom route entry. 

    ```
    python vpc_route_entry.py
    ```

    The system displays the following output:

    ```
    ---------------------------create_route_table---------------------------
    {
      "RouteTableId": "vtb-8vbn7px9zxwr2xxxxxxxx",
      "RequestId": "8B351EE1-614F-44E4-93AF-1CADA4BF02E8"
    }
    
    ---------------------------describe_vswitch_attribute---------------------------
    
    {
      "Status": "",
      "NetworkAclId": "",
      "VpcId": "",
      "Description": "",
      "Ipv6CidrBlock": "",
      "CreationTime": "",
      "CloudResources": {
        "CloudResourceSetType": []
      },
      "ZoneId": "",
      "ResourceGroupId": "",
      "VSwitchId": "",
      "RequestId": "5E199415-BBA3-443D-B1EC-06341FE267F4",
      "VSwitchName": "",
      "CidrBlock": ""
    }
    
    ---------------------------associate_route_table---------------------------
    {
      "RequestId": "5F33E444-5CCD-4677-91AB-3E234A9A64E4"
    }
    
    ---------------------------create_route_entry---------------------------
    {
      "RequestId": "D6035ECA-DD81-4FAB-B084-55BE60FB18ED"
    }
    
    ---------------------------delete_route_entry---------------------------
    {
      "RequestId": "54108FD7-8609-4111-919D-B2983466F480"
    }
    
    ---------------------------unassociate_route_table---------------------------
    {
      "RequestId": "0F36A76A-1E54-41DC-852E-1D970FDE8F3F"
    }
    
    ---------------------------delete_route_table---------------------------
    {
      "RequestId": "F3151A59-4F90-4531-AFDC-B7B7CF70A8C1"
    }				
    ```


