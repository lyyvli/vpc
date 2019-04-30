# Create a custom route table {#task_183145 .task}

This topic describes how to use the Alibaba Cloud Python SDK to create a custom route table.

To create a custom route table, the procedure described in this tutorial is as follows:

1.  Create a VPC in the China \(Zhangjiakou\) region.
2.  Create a VSwitch under the VPC.
3.  Create a custom route table named as sdk\_route\_table.
4.  Query the created VSwitch.
5.  Associate the route table with the VSwitch in the same VPC.
6.  Dissociate the route table from the VSwitch in the same VPC.
7.  Delete the custom route table.
8.  Delete the VSwitch.
9.  Delete the VPC.

1.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\sdk\_lib folder.
2.  Open the consts.py file in your text editor and configure the ACS\_CLIENT parameter used for user authentication.
3.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\vpc folder.
4.  Open the vpc\_quick\_start.py file in your text editor and configure your required parameters. Then, save the configurations and exit the editor. 

    ``` {#codeblock_pw2_1yi_k6u}
    #encoding=utf-8
    import sys
    import json
    import time
    
    from aliyunsdkcore.acs_exception.exceptions import ServerException, ClientException
    from aliyunsdkvpc.request.v20160428 import CreateRouteEntryRequest
    from aliyunsdkvpc.request.v20160428 import DeleteRouteEntryRequest
    from aliyunsdkvpc.request.v20160428 import AssociateEipAddressRequest
    from aliyunsdkvpc.request.v20160428 import UnassociateEipAddressRequest
    from aliyunsdkvpc.request.v20160428 import DescribeRouteTablesRequest
    from sdk_lib.common_util import CommonUtil
    from sdk_lib.sdk_vpc import Vpc
    from sdk_lib.sdk_vswitch import VSwitch
    from sdk_lib.exception import ExceptionHandler
    from sdk_lib.check_status import CheckStatus
    from sdk_lib.consts import *
    
    class RouteTable(object):
        def __init__(self, client):
            self.client = client
    
    
        def create_route_table(self, params):
            """
            create_route_table: 
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/87586.htm
            """
            try:
                request = CreateRouteEntryRequest.CreateRouteEntryRequest()
                request.set_action_name("CreateRouteTable")
                # The ID of the VPC to which the custom route table belongs.
                request.add_query_param("VpcId", params['vpc_id'])
                # The name of the route table.
                request.add_query_param("RouteTableName", params['route_table_name'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                route_table_id = response_json['RouteTableId']
                # Check if the route table is in the available state.
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME * 5,
                                            self.describe_route_table_status,
                                            route_table_id, route_table_id):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def associate_route_table(self, params):
            """
            associate_route_table: Associate the custom route table with the VSwitch in the same VPC
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/87599.htm
            """
            try:
                request = AssociateEipAddressRequest.AssociateEipAddressRequest()
                request.set_action_name("AssociateRouteTable")
                # The ID of the route table
                request.add_query_param("RouteTableId", params['route_table_id'])
                # The ID of the VSwitch
                request.add_query_param("VSwitchId", params['vswitch_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                time.sleep(DEFAULT_TIME * 5)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def unassociate_route_table(self, params):
            """
            unassociate_route_table: Dissociate the route table from the VSwitch
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/87628.htm
            """
            try:
                request = UnassociateEipAddressRequest.UnassociateEipAddressRequest()
                request.set_action_name("UnassociateRouteTable")
                # The ID of the route table
                request.add_query_param("RouteTableId", params['route_table_id'])
                # The ID of the VSwitch
                request.add_query_param("VSwitchId", params['vswitch_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                time.sleep(DEFAULT_TIME * 5)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def delete_route_table(self, params):
            """
            delete_route_table: Delete the custom route table
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/87601.htm
            """
            try:
                request = DeleteRouteEntryRequest.DeleteRouteEntryRequest()
                request.set_action_name("DeleteRouteTable")
                # The ID of the route table
                request.add_query_param("RouteTableId", params['route_table_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # Check if the route table has been deleted
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME * 5,
                                            self.describe_route_table_status,
                                            '', params['route_table_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_route_table(self, route_table_id):
            """
            describe_route_table: Query the route table
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36014.htm
            """
            try:
                request = DescribeRouteTablesRequest.DescribeRouteTablesRequest()
                # The ID of the route table
                request.set_RouteTableId(route_table_id)
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_route_table_status(self, route_table_id):
            """
            describe_route_table_status: Query the status of the route table
            """
            response = self.describe_route_table(route_table_id)
            if len(response["RouteTables"]["RouteTable"]) == 0:
                return ''
            return response["RouteTables"]["RouteTable"][0]["RouteTableId"]
    
    def main():
        client = ACS_CLIENT
    
        vpc = Vpc(client)
        vswitch = VSwitch(client)
        route_table = RouteTable(client)
    
        params = {}
        params['cidr_block'] = "172.16.0.0/16"
        params['zone_id'] = "cn-zhangjiakou-b"
        params['route_table_name'] = "sdk_route_table"
    
        #Create a vpc
        vpc_json = vpc.create_vpc()
        CommonUtil.log("create_vpc", vpc_json)
    
        #Create a vswitch
        params['vpc_id'] = vpc_json['VpcId']
        vswitch_json = vswitch.create_vswitch(params)
        CommonUtil.log("create_vswitch", vswitch_json)
    
        #Create a route table
        route_table_json = route_table.create_route_table(params)
        CommonUtil.log("create_route_table", route_table_json)
    
        #Query the vswitch
        params['vswitch_id'] = vswitch_json['VSwitchId']
        vswitch_json = vswitch.describe_vswitch_attribute(params['vswitch_id'])
        CommonUtil.log("describe_vswitch_attribute", vswitch_json)
    
        #Associate the route table with the vswitch
        params['route_table_id'] = route_table_json['RouteTableId']
        associate_json = route_table.associate_route_table(params)
        CommonUtil.log("associate_route_table", associate_json)
    
        #Dissociate the route table from the vswitch
        unassociate_json = route_table.unassociate_route_table(params)
        CommonUtil.log("unassociate_route_table", unassociate_json)
    
        #Delete the route table
        delete_route_table_json = route_table.delete_route_table(params)
        CommonUtil.log("delete_route_table", delete_route_table_json)
    
        #Delete the vswitch
        delete_vswitch_json = vswitch.delete_vswitch(params)
        CommonUtil.log("delete_vswitch", delete_vswitch_json)
    
        #Delete the vpc
        delete_vpc_json = vpc.delete_vpc(params)
        CommonUtil.log("delete_vpc", delete_vpc_json)
    
    if __name__ == "__main__":
        sys.exit(main())
    ```

5.  Enter the vpc\_route\_table.py directory and run the following command to create the custom route entry. 

    ```
    python vpc_route_table.py
    ```

    The system displays the following output:

    ```
    ---------------------------create_vpc---------------------------
    {
      "ResourceGroupId": "rg-acfmxazxxxxxxxx",
      "RouteTableId": "vtb-8vb65a5hqy8pcxxxxxxxx",
      "VRouterId": "vrt-8vbbbiftzizc3xxxxxxxx",
      "VpcId": "vpc-8vbebihln001gxxxxxxxx",
      "RequestId": "862F279B-4A27-4300-87A1-047FB9961AF2"
    }
    
    ---------------------------create_vswitch---------------------------
    {
      "VSwitchId": "vsw-8vb30klhn2is5xxxxxxxx",
      "RequestId": "1DA17173-CB61-4DCE-9C29-AABFDF3001A6"
    }
    
    ---------------------------create_route_table---------------------------
    {
      "RouteTableId": "vtb-8vbc4iwpo13apxxxxxxxx",
      "RequestId": "01E66E67-7801-4705-A02A-853BA7EEA89F"
    }
    
    ---------------------------describe_vswitch_attribute---------------------------
    
    {
      "Status": "Available",
      "NetworkAclId": "",
      "VpcId": "vpc-8vbebihln001gxxxxxxxx",
      "Description": "",
      "RouteTable": {
        "RouteTableId": "vtb-8vb65a5hqy8pcxxxxxxxx",
        "RouteTableType": "System"
      },
      "CidrBlock": "172.16.0.0/16",
      "CreationTime": "2019-04-12T03:08:43Z",
      "CloudResources": {
        "CloudResourceSetType": []
      },
      "ZoneId": "cn-zhangjiakou-b",
      "ResourceGroupId": "rg-acfmxazbxxxxxxxx",
      "VSwitchId": "vsw-8vb30klhn2is5xxxxxxxx",
      "RequestId": "C5A20BA3-E998-498D-8900-35AE5FDFFB77",
      "Ipv6CidrBlock": "",
      "VSwitchName": "",
      "AvailableIpAddressCount": 252,
      "IsDefault": false
    }
    
    ---------------------------associate_route_table---------------------------
    {
      "RequestId": "5FC0143B-D34B-47DC-8D49-AFD222EA5876"
    }
    
    ---------------------------unassociate_route_table---------------------------
    {
      "RequestId": "F0194718-6E4C-496C-9DA8-1B88DF1D6FAD"
    }
    
    ---------------------------delete_route_table---------------------------
    {
      "RequestId": "B5C068A6-137C-4337-8E3A-9E30E1726703"
    }
    
    ---------------------------delete_vswitch---------------------------
    {
      "RequestId": "26DEDBF8-2F0D-4A13-8CB3-23A84C947704"
    }
    
    ---------------------------delete_vpc---------------------------
    {
      "RequestId": "E1B2641F-5911-40E4-9F36-CC0B2EDD1747"
    }						
    ```


