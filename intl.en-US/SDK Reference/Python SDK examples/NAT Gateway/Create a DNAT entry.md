# Create a DNAT entry {#task_188257 .task}

This topic describes how to use the Alibaba Cloud Python SDK to create a DNAT entry.

The detailed steps used in this tutorial to create a DNAT entry are as follows:

1.  Create a VPC in the China \(Shanghai\) region.
2.  Create a VSwitch under the VPC.
3.  Create a NAT Gateway under the VPC.
4.  Create an EIP in the China \(Shanghai\) region.
5.  Attach the EIP to the NAT Gateway.
6.  Create a DNAT entry.
7.  Query the EIP attached to the NAT Gateway.
8.  Query the NAT Gateway.
9.  Delete the DNAT entry.
10. Detach the EIP from the NAT Gateway.
11. Delete the NAT Gateway.
12. Release the EIP.
13. Delete the VSwitch.
14. Delete the VPC.

1.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\sdk\_lib folder.
2.  Open the consts.py file in your text editor and configure the ACS\_CLIENT parameter used for user authentication.
3.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\natgw folder.
4.  Open the natgw\_dnat.py file in your text editor and configure your required parameters. Then, save the configurations and exit the text editor. 

    ``` {#codeblock_lga_782_436}
    #encoding=utf-8
    import sys
    import json
    import time
    
    from aliyunsdkcore.acs_exception.exceptions import ServerException, ClientException
    from aliyunsdkvpc.request.v20160428 import CreateNatGatewayRequest
    from aliyunsdkvpc.request.v20160428 import DeleteNatGatewayRequest
    from aliyunsdkvpc.request.v20160428 import DescribeNatGatewaysRequest
    from aliyunsdkvpc.request.v20160428 import CreateForwardEntryRequest
    from aliyunsdkvpc.request.v20160428 import DescribeForwardTableEntriesRequest
    from aliyunsdkvpc.request.v20160428 import DeleteForwardEntryRequest
    from sdk_lib.sdk_vpc import Vpc
    from sdk_lib.sdk_vswitch import VSwitch
    from sdk_lib.sdk_eip import Eip
    from sdk_lib.sdk_cbwp import CommonBandwidthPackage
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
            describe_nat_gateway_status: Query the status of NAT Gateways in a region
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36054.htm
            """
            response = self.describe_nat_gateway(nat_gateway_id)
            if len(response["NatGateways"]["NatGateway"]) == 0:
                return ''
            return response["NatGateways"]["NatGateway"][0]['Status']
    
        def create_forward_entry(self, params):
            """
            create_forward_entry: Create a forward entry
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36058.htm
            """
            try:
                request = CreateForwardEntryRequest.CreateForwardEntryRequest()
                request.set_ForwardTableId(params['forward_table_id'])
                request.set_ExternalIp(params['external_ip'])
                request.set_IpProtocol(params['ip_protocol'])
                request.set_ExternalPort(params['external_port'])
                request.set_InternalIp(params['internal_ip'])
                request.set_InternalPort(params['internal_port'])
                response = client.do_action_with_exception(request)
                response_json = json.loads(response)
                # Check if the forward entry is in the available state
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_forward_status,
                                            AVAILABLE, params['forward_table_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_forward(self, forward_table_id):
            """
            describe_forward: Query DNAT entries in a region
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36053.htm
            """
            try:
                request = DescribeForwardTableEntriesRequest.DescribeForwardTableEntriesRequest()
                request.set_ForwardTableId(forward_table_id)
                response = client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_forward_status(self, forward_table_id):
            """
            describe_forward_status: Query the status of DNAT entries in a region
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36053.htm
            """
            response = self.describe_forward(forward_table_id)
            if len(response["ForwardTableEntries"]["ForwardTableEntry"]) == 0:
                return ''
            return response["ForwardTableEntries"]["ForwardTableEntry"][0]['Status']
    
        def delete_forward_entry(self, params):
            """
            delete_forward_entry: Delete a forward entry
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36050.htm
            """
            try:
                request = DeleteForwardEntryRequest.DeleteForwardEntryRequest()
                request.set_ForwardTableId(params['forward_table_id'])
                request.set_ForwardEntryId(params['forward_entry_id'])
                response = client.do_action_with_exception(request)
                response_json = json.loads(response)
                # Check if the forward entry is in the available state
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME * 5,
                                            self.describe_forward_status,
                                            '', params['forward_table_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
    
    def main():
        vpc = Vpc(client)
        vswitch = VSwitch(client)
        eip = Eip(client)
        cbwp = CommonBandwidthPackage(client)
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
        params['vswitch_id'] = vswitch_json['VSwitchId']
    
        # Create a NAT Gateway
        nat_gateway_json = nat_gateway.create_nat_gateway(params)
        CommonUtil.log("create_nat_gateway", nat_gateway_json)
    
        # Create an EIP
        eip_response_json = eip.allocate_eip_address(params)
        CommonUtil.log("allocate_eip_address", eip_response_json)
        params['allocation_id'] = eip_response_json["AllocationId"]
        params['external_ip'] = eip_response_json['EipAddress']
    
        # Attach the EIP to the NAT Gateway
        params['instance_id'] = nat_gateway_json['NatGatewayId']
        params['allocation_id'] = eip_response_json["AllocationId"]
        params['instance_type'] = 'Nat'
        eip_response_json = eip.associate_eip_address(params)
        CommonUtil.log("associate_eip_address eip", eip_response_json)
    
        # Create a DNAT entry
        params['forward_table_id'] = nat_gateway_json['ForwardTableIds']['ForwardTableId'][0]
        params['ip_protocol'] = 'tcp'
        params['external_port'] = '8080'
        params['internal_port'] = '80'
        params['internal_ip'] = '172.16.1.0'
        forward_entry_json = nat_gateway.create_forward_entry(params)
        CommonUtil.log("create_forward_entry", forward_entry_json)
    
        # Query the EIP
        eip_response_json = eip.describe_eip_address(params['allocation_id'])
        CommonUtil.log("describe_eip_address", eip_response_json)
    
        # Query the NAT Gateway
        params['nat_gateway_id'] = nat_gateway_json['NatGatewayId']
        nat_gateway_json = nat_gateway.describe_nat_gateway(params['nat_gateway_id'])
        CommonUtil.log("describe_nat_gateway", nat_gateway_json)
    
        # Delete the DNAT entry
        params['forward_entry_id'] = forward_entry_json['ForwardEntryId']
        forward_entry_json = nat_gateway.delete_forward_entry(params)
        CommonUtil.log("delete_forward_entry", forward_entry_json)
    
        # Detach the EIP
        eip_response_json = eip.unassociate_eip_address(params)
        CommonUtil.log("unassociate_eip_address nat", eip_response_json)
    
        # Delete the NAT Gateway
        nat_gateway_json = nat_gateway.delete_nat_gateway(params)
        CommonUtil.log("delete_nat_gateway", nat_gateway_json)
    
        # Release the EIP
        eip_response_json = eip.release_eip_address(params)
        CommonUtil.log("release_eip_address", eip_response_json)
    
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

5.  Access the natgw\_dnat.py directory and run the following command to create a DNAT entry. 

    ``` {#codeblock_pnp_d1d_bu1}
    python natgw_dnat.py
    ```

    The system displays the following output:

    ``` {#codeblock_y03_ztm_8kr}
    ---------------------------create_vpc---------------------------
    {
      "ResourceGroupId": "rg-acfmxazxxxxxxxx",
      "RouteTableId": "vtb-uf63rln6gbb50xxxxxxxx",
      "VRouterId": "vrt-uf6p1hfo0ho8gxxxxxxxx",
      "VpcId": "vpc-uf6c3r8yca7dhxxxxxxxx",
      "RequestId": "1F97FC59-77DF-4D76-BE62-0A13EB4E614C"
    }
    
    ---------------------------create_vswitch---------------------------
    {
      "VSwitchId": "vsw-uf6liy66d9ssuxxxxxxxx",
      "RequestId": "88CCCFED-1448-49D2-8550-71952981A47A"
    }
    
    ---------------------------create_nat_gateway---------------------------
    {
      "NatGatewayId": "ngw-uf6aolgwhssvsxxxxxxxx",
      "BandwidthPackageIds": {
        "BandwidthPackageId": []
      },
      "ForwardTableIds": {
        "ForwardTableId": [
          "ftb-uf6unjiun4i12xxxxxxxx"
        ]
      },
      "RequestId": "62A58351-D608-43A4-849E-1E177E917BEA",
      "SnatTableIds": {
        "SnatTableId": [
          "stb-uf65utljwcdkpxxxxxxxx"
        ]
      }
    }
    
    ---------------------------allocate_eip_address---------------------------
    {
      "EipAddress": "101.xx.xx.110",
      "ResourceGroupId": "rg-acfmxazxxxxxxxx",
      "RequestId": "0565295E-2F49-4511-93BC-747A2D19A6BD",
      "AllocationId": "eip-uf683xrl32ge8xxxxxxxx"
    }
    
    ---------------------------associate_eip_address eip---------------------------
    {
      "RequestId": "8759FCE8-F8C2-4372-91D5-7A25D43FD78C"
    }
    
    ---------------------------create_forward_entry---------------------------
    {
      "ForwardEntryId": "fwd-uf6ng3wt8sfwmxxxxxxxx",
      "RequestId": "CC81BCF6-2F64-40CF-85B0-676A83AC3902"
    }
    
    ---------------------------describe_eip_address---------------------------
    {
      "TotalCount": 1,
      "PageNumber": 1,
      "PageSize": 10,
      "EipAddresses": {
        "EipAddress": [
          {
            "ISP": "BGP",
            "ExpiredTime": "",
            "InternetChargeType": "PayByBandwidth",
            "IpAddress": "101.xx.xx.110",
            "AllocationId": "eip-uf683xrl32ge8xxxxxxxx",
            "PrivateIpAddress": "",
            "Status": "InUse",
            "BandwidthPackageId": "",
            "InstanceId": "ngw-uf6aolgwhssvsxxxxxxxx",
            "InstanceRegionId": "cn-shanghai",
            "RegionId": "cn-shanghai",
            "AvailableRegions": {
              "AvailableRegion": [
                "cn-shanghai"
              ]
            },
            "ResourceGroupId": "rg-acfmxazxxxxxxxx",
            "HasReservationData": false,
            "InstanceType": "Nat",
            "AllocationTime": "2019-04-24T10:56:53Z",
            "Name": "",
            "OperationLocks": {
              "LockReason": []
            },
            "Mode": "NAT",
            "BandwidthPackageType": "",
            "BandwidthPackageBandwidth": "",
            "Bandwidth": "5",
            "HDMonitorStatus": "OFF",
            "ChargeType": "PostPaid",
            "SecondLimited": false,
            "Descritpion": ""
          }
        ]
      },
      "RequestId": "CD2B3613-2A99-4687-9C23-A8E9F1F03048"
    }
    
    ---------------------------describe_nat_gateway---------------------------
    {
      "TotalCount": 1,
      "PageNumber": 1,
      "RequestId": "D7519663-8D3B-4CC5-894F-A6798C89688D",
      "PageSize": 10,
      "NatGateways": {
        "NatGateway": [
          {
            "Status": "Available",
            "BandwidthPackageIds": {
              "BandwidthPackageId": []
            },
            "VpcId": "vpc-uf6c3r8yca7dhxxxxxxxx",
            "Description": "",
            "ForwardTableIds": {
              "ForwardTableId": [
                "ftb-uf6unjiun4i12xxxxxxxx"
              ]
            },
            "IpLists": {
              "IpList": [
                {
                  "UsingStatus": "UsedByForwardTable",
                  "IpAddress": "101.xx.xx.110",
                  "AllocationId": "eip-uf683xrl32ge8xxxxxxxx"
                }
              ]
            },
            "BusinessStatus": "Normal",
            "RegionId": "cn-shanghai",
            "CreationTime": "2019-04-24T10:56:50Z",
            "NatGatewayId": "ngw-uf6aolgwhssvsxxxxxxxx",
            "SnatTableIds": {
              "SnatTableId": [
                "stb-uf65utljwcdkpxxxxxxxx"
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
    
    ---------------------------delete_forward_entry---------------------------
    {
      "RequestId": "32C76D08-5738-4B07-A638-ACE5F5F5220E"
    }
    
    ---------------------------unassociate_eip_address nat--------------------------
    -
    {
      "RequestId": "AE686920-2CD1-4850-AADC-C249484D4B1A"
    }
    
    ---------------------------delete_nat_gateway---------------------------
    {
      "RequestId": "FEBB1E7A-BA5B-4445-B2AB-5B828C17BBE6"
    }
    
    ---------------------------release_eip_address---------------------------
    {
      "RequestId": "812D5E78-5113-4B92-892D-0B293BAD66F6"
    }
    
    ---------------------------delete_vswitch---------------------------
    {
      "RequestId": "8E13EEE4-21B5-4280-B46B-5C168736DC3A"
    }
    
    ---------------------------delete_vpc---------------------------
    {
      "RequestId": "DCBA91E7-F355-4EB6-83E3-27F2E68A8435"
    }
    ```


