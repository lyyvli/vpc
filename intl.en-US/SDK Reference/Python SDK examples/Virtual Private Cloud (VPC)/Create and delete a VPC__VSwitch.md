# Create and delete a VPC/VSwitch {#task_gkw_xf5_jhb .task}

This topic describes how to use the Alibaba Cloud Python SDK to create and delete a VPC and a VSwitch.

In this tutorial, we will create a VPC in the China \(Zhangjiakou\) region and create a VSwitch under this VPC. Then we will delete the VPC and VSwitch.

1.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\sdk\_lib file.
2.  Open the consts.py file in your text editor and configure the ACS\_CLIENT parameter used for user authentication.
3.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\vpc folder.
4.  Open the vpc\_quick\_start.py file in your text editor and configure your required parameters. Then, save the configurations and exit the editor.
5.  Enter the directory of vpc\_quick\_start.py and run the following command to run the example that creates and deletes the VPC and VSwitch. 

    ```
    #encoding=utf-8
    import sys
    import json
    
    from aliyunsdkcore.acs_exception.exceptions import ServerException, ClientException
    from aliyunsdkvpc.request.v20160428 import CreateVpcRequest
    from aliyunsdkvpc.request.v20160428 import CreateVSwitchRequest
    from aliyunsdkvpc.request.v20160428 import DeleteVSwitchRequest
    from aliyunsdkvpc.request.v20160428 import DeleteVpcRequest
    from aliyunsdkvpc.request.v20160428 import DescribeVSwitchAttributesRequest
    from aliyunsdkvpc.request.v20160428 import DescribeVpcAttributeRequest
    from sdk_lib.exception import ExceptionHandler
    from sdk_lib.check_status import CheckStatus
    from sdk_lib.consts import *
    from sdk_lib.common_util import CommonUtil
    
    class VpcQuickStart(object):
        def __init__(self, client):
            self.client = client
    
        def create_vpc(self):
            """
            create_vpc: Create a VPC
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/35737.htm
            """
            try:
                request = CreateVpcRequest.CreateVpcRequest()
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # Check whether the VPC is in the available state
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_vpc_status,
                                            AVAILABLE, response_json['VpcId']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def delete_vpc(self, params):
            """
            delete_vpc: Delete a VPC
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/35738.htm
            """
            try:
                request = DeleteVpcRequest.DeleteVpcRequest()
                # The ID of the VPC to be deleted
                request.set_VpcId(params['vpc_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_vpc_attribute(self, vpc_id):
            """
            describe_vpc_attribute: Query the VPC created in the specified region
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/94565.htm
            """
            """
            try:
                request = DescribeVpcAttributeRequest.DescribeVpcAttributeRequest()
                # The ID of the VPC to be queried
                request.set_VpcId(vpc_id)
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_vpc_status(self, vpc_id):
            """
            describe_vpc_status: Query the status of the VPC created in the specified region
            API reference link:  https://partners-intl.aliyun.com/help/doc-detail/94565.htm
            """
            response = self.describe_vpc_attribute(vpc_id)
            return response["Status"]
    
        def create_vswitch(self, params):
            """
            create_vswitch: Create a VSwitch instance
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/35745.htm
            """
            try:
                request = CreateVSwitchRequest.CreateVSwitchRequest()
                # The ID of the zone to which the VSwitch belongs. To query the region ID, call the DescribeZones action.
                request.set_ZoneId(params['zone_id'])
                # The ID of the VPC to which the VSwitch belongs.
                request.set_VpcId(params['vpc_id'])
                # The CIDR block of the VSwitch
                request.set_CidrBlock(params['cidr_block'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # Check whether the VSwitch is in the available state
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_vswitch_status,
                                            AVAILABLE, response_json['VSwitchId']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_vswitch_attribute(self, vswitch_id):
            """
            describe_vswitch_attribute: Query the status of the VSwitch created in the specified region
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/94567.htm
            """
            try:
                request = DescribeVSwitchAttributesRequest.DescribeVSwitchAttributesRequest()
                request.set_VSwitchId(vswitch_id)
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_vswitch_status(self, vswitch_id):
            """
            describe_vswitch_status: Query the status of the VSwitch created in the specified region
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/94567.htm
            """
            response = self.describe_vswitch_attribute(vswitch_id)
            return response["Status"]
    
        def delete_vswitch(self, params):
            """
            delete_vswitch: Delete a VSwitch instance
           API reference link: https://partners-intl.aliyun.com/help/doc-detail/35746.htm
            """
            try:
                request = DeleteVSwitchRequest.DeleteVSwitchRequest()
                # The ID of the VSwitch to be deleted
                request.set_VSwitchId(params['vswitch_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # Check if the VSwitch has been deleted
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME * 5,
                                            self.describe_vswitch_status,
                                            '', params['vswitch_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
    
    def main():
        client = ACS_CLIENT
    
        vpc_quick_start = VpcQuickStart(client)
    
        params = {}
        params['zone_id'] = "cn-zhangjiakou-b"
        params['cidr_block'] = "172.16.0.0/16"
    
        # Create a vpc
        vpc_json = vpc_quick_start.create_vpc()
        CommonUtil.log("create_vpc", vpc_json)
    
        # Create a vswitch
        params['vpc_id'] = vpc_json['VpcId']
        vswitch_json = vpc_quick_start.create_vswitch(params)
        CommonUtil.log("create_vswitch", vswitch_json)
    
        # Delete the vswitch
        params['vswitch_id'] = vswitch_json['VSwitchId']
        vswitch_json = vpc_quick_start.delete_vswitch(params)
        CommonUtil.log("delete_vswitch", vswitch_json)
    
        # Delete the vpc
        vpc_json = vpc_quick_start.delete_vpc(params)
        CommonUtil.log("delete_vpc", vpc_json)
    
    
    if __name__ == "__main__":
        sys.exit(main())
    ```

    ```
    python vpc_quick_start.py
    ```

    The system displays the following output:

    ```
    ---------------------------create_vpc---------------------------
    {
      "ResourceGroupId": "rg-acfmxazxxxxxxxx",
      "RouteTableId": "vtb-8vbf9ud7xrcn9xxxxxxxx",
      "VRouterId": "vrt-8vb1qjnxcm03nxxxxxxxx",
      "VpcId": "vpc-8vb67v4ozd8wfxxxxxxxx",
      "RequestId": "5052F988-75CC-46AD-A1A6-0E9E445BD0D5"
    }
    ---------------------------create_vswitch---------------------------
    {
      "VSwitchId": "vsw-8vbqn2at0kljjxxxxxxxx",
      "RequestId": "0BA1ABF7-21CF-4460-9A86-0BB783886E58"
    }
    ---------------------------delete_vswitch---------------------------
    {
      "RequestId": "D691F04B-A6EE-49A7-A434-4A45DD3AA0B8"
    }
    ---------------------------delete_vpc---------------------------
    {
      "RequestId": "4570F816-AB8D-45EA-8913-6AE787C1632C"
    }
    ```


