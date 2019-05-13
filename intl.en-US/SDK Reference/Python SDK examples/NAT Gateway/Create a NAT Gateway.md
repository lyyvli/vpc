# Create a NAT Gateway {#task_188158 .task}

This topic describes how to use the Alibaba Cloud Python SDK to create a NAT Gateway.

The detailed steps used in this tutorial to create a NAT Gateway are as follows:

1.  Create a VPC in the China \(Shanghai\) region.
2.  Create a VSwitch under the VPC.
3.  Create a NAT Gateway under the VPC.
4.  Query the NAT Gateway.
5.  Delete the NAT Gateway.
6.  Delete the VSwitch.
7.  Delete the VPC.

1.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\sdk\_lib folder.
2.  Open the consts.py file in your text editor and configure the ACS\_CLIENT parameter used for user authentication.
3.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\natgw folder.
4.  Open the natgw\_quick\_start.py file in your text editor and configure your required parameters. Then, save the configurations and exit the text editor. 

    ``` {#codeblock_8zk_hte_a0x}
    #encoding=utf-8
    import sys
    import json
    import time
    
    from aliyunsdkcore.acs_exception.exceptions import ServerException, ClientException
    from aliyunsdkvpc.request.v20160428 import CreateNatGatewayRequest
    from aliyunsdkvpc.request.v20160428 import DeleteNatGatewayRequest
    from aliyunsdkvpc.request.v20160428 import DescribeNatGatewaysRequest
    from sdk_lib.sdk_vpc import Vpc
    from sdk_lib.sdk_vswitch import VSwitch
    from sdk_lib.common_util import CommonUtil
    from sdk_lib.check_status import CheckStatus
    from sdk_lib.exception import ExceptionHandler
    from sdk_lib.consts import *
    
    client = ACS_CLIENT
    
    
    class NatGateway(object):
        def __init__(self, client):
            self.client = client
    
        def create_nat_gateway(self, params):
            """
            create_nat_gateway: Create a NAT Gateway
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36048.htm
            """
            try:
                request = CreateNatGatewayRequest.CreateNatGatewayRequest()
                request.set_VpcId(params['vpc_id'])
                response = client.do_action_with_exception(request)
                response_json = json.loads(response)
                # Check if the NAT Gateway is in the available state
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_nat_gateway_status,
                                            AVAILABLE, response_json['NatGatewayId']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_nat_gateway(self, nat_gateway_id):
            """
            describe_nat_gateway: Query NAT Gateways in a region
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36054.htm
            """
            try:
                request = DescribeNatGatewaysRequest.DescribeNatGatewaysRequest()
                request.set_NatGatewayId(nat_gateway_id)
                response = client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def delete_nat_gateway(self, params):
            """
            delete_nat_gateway: Delete a NAT Gateway
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36051.htm
            """
            try:
                request = DeleteNatGatewayRequest.DeleteNatGatewayRequest()
                request.set_NatGatewayId(params['nat_gateway_id'])
                response = client.do_action_with_exception(request)
                response_json = json.loads(response)
                # Check if the NAT Gateway is in the available state
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME * 5,
                                            self.describe_nat_gateway_status,
                                            '', params['nat_gateway_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_nat_gateway_status(self, nat_gateway_id):
            """
            describe_nat_gateway_status:  Query the status of NAT Gateways in a region
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36054.htm
            """
            response = self.describe_nat_gateway(nat_gateway_id)
            if len(response["NatGateways"]["NatGateway"]) == 0:
                return ''
            return response["NatGateways"]["NatGateway"][0]['Status']
    
    
    def main():
        vpc = Vpc(client)
        vswitch = VSwitch(client)
        nat_gateway = NatGateway(client)
    
        params = {}
    
        # Create a VPC
        vpc_json = vpc.create_vpc()
        CommonUtil.log("create_vpc", vpc_json)
    
        # Create a VSwitch
        params['vpc_id'] = vpc_json['VpcId']
        params['zone_id'] = "cn-shanghai-b"
        params['cidr_block'] = "172.16.1.0/24"
        vswitch_json = vswitch.create_vswitch(params)
        CommonUtil.log("create_vswitch", vswitch_json)
    
        # Create a NAT Gateway
        nat_gateway_json = nat_gateway.create_nat_gateway(params)
        CommonUtil.log("create_nat_gateway", nat_gateway_json)
    
        # Query the NAT Gateway
        params['nat_gateway_id'] = nat_gateway_json['NatGatewayId']
        nat_gateway_json = nat_gateway.describe_nat_gateway(params['nat_gateway_id'])
        CommonUtil.log("describe_nat_gateway", nat_gateway_json)
    
        # Delete the NAT Gateway
        nat_gateway_json = nat_gateway.delete_nat_gateway(params)
        CommonUtil.log("delete_nat_gateway", nat_gateway_json)
    
        # Delete the VSwitch
        params['vswitch_id'] = vswitch_json['VSwitchId']
        vswitch_json = vswitch.delete_vswitch(params)
        CommonUtil.log("delete_vswitch", vswitch_json)
    
        # Delete the VPC
        vpc_json = vpc.delete_vpc(params)
        CommonUtil.log("delete_vpc", vpc_json)
    
    
    if __name__ == "__main__":
        sys.exit(main())
    ```

5.  Access the natgw\_quick\_start.py directory and run the following command to create a NAT Gateway. 

    ```
    python natgw_quick_start.py
    ```

    The system displays the following output:

    ``` {#codeblock_u7o_m1q_svy}
    ---------------------------create_vpc---------------------------
    {
      "ResourceGroupId": "rg-acfmxazxxxxxxxx",
      "RouteTableId": "vtb-uf6wzp25d8lkbxxxxxxxx",
      "VRouterId": "vrt-uf6di7voecmyqxxxxxxxx",
      "VpcId": "vpc-uf63cqupghmk1xxxxxxxx",
      "RequestId": "97D36E19-F789-424F-A473-660D63EF8CF9"
    }
    
    ---------------------------create_vswitch---------------------------
    {
      "VSwitchId": "vsw-uf6fovepnk4yexxxxxxxx",
      "RequestId": "18DA0E81-34A6-4877-9771-E2C4EEEBADD1"
    }
    
    ---------------------------create_nat_gateway---------------------------
    {
      "NatGatewayId": "ngw-uf6mfrcmzktstxxxxxxxx",
      "BandwidthPackageIds": {
        "BandwidthPackageId": []
      },
      "ForwardTableIds": {
        "ForwardTableId": [
          "ftb-uf6411str8n9sxxxxxxxx"
        ]
      },
      "RequestId": "B1F791C8-73B1-46C5-8A20-726A615BC627",
      "SnatTableIds": {
        "SnatTableId": [
          "stb-uf6t4eijvq3aexxxxxxxx"
        ]
      }
    }
    
    ---------------------------describe_nat_gateway---------------------------
    {
      "TotalCount": 1,
      "PageNumber": 1,
      "RequestId": "1F9303B1-4024-4A92-B67E-FB6BE1DC76D1",
      "PageSize": 10,
      "NatGateways": {
        "NatGateway": [
          {
            "Status": "Available",
            "BandwidthPackageIds": {
              "BandwidthPackageId": []
            },
            "VpcId": "vpc-uf63cqupghmk1xxxxxxxx",
            "Description": "",
            "ForwardTableIds": {
              "ForwardTableId": [
                "ftb-uf6411str8n9sxxxxxxxx"
              ]
            },
            "IpLists": {
              "IpList": []
            },
            "BusinessStatus": "Normal",
            "RegionId": "cn-shanghai",
            "CreationTime": "2019-04-24T09:09:12Z",
            "NatGatewayId": "ngw-uf6mfrcmzktstxxxxxxxx",
            "SnatTableIds": {
              "SnatTableId": [
                "stb-uf6t4eijvq3aexxxxxxxx"
              ]
            },
            "AutoPay": false,
            "InstanceChargeType": "PostPaid",
            "ExpiredTime": "",
            "Spec": "Small",
            "Name": ""
          }
        ]
      }
    }
    
    ---------------------------delete_nat_gateway---------------------------
    {
      "RequestId": "A0B71FE4-4756-4D91-899E-1DFA52D8615E"
    }
    
    ---------------------------delete_vswitch---------------------------
    {
      "RequestId": "F224307E-3DE4-4415-AE19-DDCF24695462"
    }
    
    ---------------------------delete_vpc---------------------------
    {
      "RequestId": "1BFFCBC3-7F83-436C-96E9-CA4A620072DA"
    }                
    ```


