# Associate and disassociate an EIP {#task_188230 .task}

This topic describes how to use the Alibaba Cloud Python SDK to associate and disassociate an EIP.

The detailed steps used in this tutorial to associate and disassociate an EIP are as follows:

1.  Create a VPC in the China \(Shanghai\) region.
2.  Create a VSwitch under the VPC.
3.  Create a NAT Gateway under the VPC.
4.  Create an EIP in the China \(Shanghai\) region.
5.  Associate the EIP to the NAT Gateway.
6.  Query the EIP.
7.  Create an Internet Shared Bandwidth instance in the China \(Shanghai\) region.
8.  Add the EIP to the Internet Shared Bandwidth instance.
9.  Query the created NAT Gateway.
10. Disassociate the EIP from the NAT Gateway.
11. Remove the EIP from the Internet Shared Bandwidth instance.
12. Delete the Internet Shared Bandwidth instance.
13. Delete the NAT Gateway.
14. Release the EIP.
15. Delete the VSwitch.
16. Delete the VPC.

1.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\sdk\_lib folder.
2.  Open the consts.py file in your text editor and configure the ACS\_CLIENT parameter used for user authentication.
3.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\natgw folder.
4.  Open the natgw\_associate\_eip.py file in your text editor and configure your required parameters. Then, save the configurations and exit the text editor. 

    ``` {#codeblock_n08_p4a_qbe}
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
        params['zone_id'] = "cn-shanghai-d"
        params['cidr_block'] = "172.16.1.0/24"
        vswitch_json = vswitch.create_vswitch(params)
        CommonUtil.log("create_vswitch", vswitch_json)
    
        # Create a NAT Gateway
        nat_gateway_json = nat_gateway.create_nat_gateway(params)
        CommonUtil.log("create_nat_gateway", nat_gateway_json)
    
        # Create an EIP
        eip_response_json = eip.allocate_eip_address(params)
        CommonUtil.log("allocate_eip_address", eip_response_json)
        params['allocation_id'] = eip_response_json["AllocationId"]
    
        # Associate the EIP to the NAT Gateway
        params['instance_id'] = nat_gateway_json['NatGatewayId']
        params['allocation_id'] = eip_response_json["AllocationId"]
        params['instance_type'] = 'Nat'
        eip_response_json = eip.associate_eip_address(params)
        CommonUtil.log("associate_eip_address eip", eip_response_json)
    
        # Query the EIP
        eip_response_json = eip.describe_eip_address(params['allocation_id'])
        CommonUtil.log("describe_eip_address", eip_response_json)
    
        # Create an Internet Shared Bandwidth
        params['bandwidth'] = BANDWIDTH_10
        cbwp_repsonse_json = cbwp.create_common_bandwidth_package(params)
        CommonUtil.log("create_common_bandwidth_package", cbwp_repsonse_json)
    
        # Add the EIP to the Internet Shared Bandwidth
        params['ip_instance_id'] = params['allocation_id']
        params['bandwidth_package_id'] = cbwp_repsonse_json['BandwidthPackageId']
        cbwp_repsonse_json = cbwp.add_common_bandwidth_packageIp(params)
        CommonUtil.log("add_common_bandwidth_packageIp", cbwp_repsonse_json)
    
        # Query the NAT Gateway
        params['nat_gateway_id'] = nat_gateway_json['NatGatewayId']
        nat_gateway_json = nat_gateway.describe_nat_gateway(params['nat_gateway_id'])
        CommonUtil.log("describe_nat_gateway", nat_gateway_json)
    
        # Disassociate the EIP
        eip_response_json = eip.unassociate_eip_address(params)
        CommonUtil.log("unassociate_eip_address nat", eip_response_json)
    
        # Remove the EIP from the Internet Shared Bandwidth
        cbwp_repsonse_json = cbwp.remove_common_bandwidth_packageIp(params)
        CommonUtil.log("remove_common_bandwidth_packageIp", cbwp_repsonse_json)
    
        # Delete the Internet Shared Bandwidth
        params['force'] = True
        cbwp_repsonse_json = cbwp.delete_common_bandwidth_package(params)
        CommonUtil.log("delete_common_bandwidth_package", cbwp_repsonse_json)
    
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

5.  Access the natgw\_associate\_eip.py directory and run the following command to associate and disassociate an EIP. 

    ``` {#codeblock_1rn_bj3_byl}
    python natgw_associate_eip.py
    ```

    The system displays the following output:

    ``` {#codeblock_4bi_j4f_9t4}
    ---------------------------create_vpc---------------------------
    {
      "ResourceGroupId": "rg-acfmxazxxxxxxxx",
      "RouteTableId": "vtb-uf6agemvkcmd8xxxxxxxx",
      "VRouterId": "vrt-uf6r7lqtsv65dxxxxxxxx",
      "VpcId": "vpc-uf6mqfqx8vjmoxxxxxxxx",
      "RequestId": "ADF806C6-FCD6-4E46-B8E3-72C2BE895344"
    }
    
    ---------------------------create_vswitch---------------------------
    {
      "VSwitchId": "vsw-uf6rm6add6w89xxxxxxxx",
      "RequestId": "897FFCC1-E6BA-484E-A245-C5DAEBBA269C"
    }
    
    ---------------------------create_nat_gateway---------------------------
    {
      "NatGatewayId": "ngw-uf681h38pbvlyxxxxxxxx",
      "BandwidthPackageIds": {
        "BandwidthPackageId": []
      },
      "ForwardTableIds": {
        "ForwardTableId": [
          "ftb-uf6jd0vbyao2dxxxxxxxx"
        ]
      },
      "RequestId": "7C7CD3CB-041A-4B80-80B4-8BF8D5EF0D26",
      "SnatTableIds": {
        "SnatTableId": [
          "stb-uf6uj997htg3uxxxxxxxx"
        ]
      }
    }
    
    ---------------------------allocate_eip_address---------------------------
    {
      "EipAddress": "106.xx.xx.129",
      "ResourceGroupId": "rg-acfmxazxxxxxxxx",
      "RequestId": "DB795B99-1CEA-4FC1-9CE3-9DE2B977BF02",
      "AllocationId": "eip-uf62tf8y4uyacxxxxxxxx"
    }
    
    ---------------------------associate_eip_address eip---------------------------
    {
      "RequestId": "443D7060-B716-4193-A44D-23FE762004F8"
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
            "IpAddress": "106.xx.xx.129",
            "AllocationId": "eip-uf62tf8y4uyacxxxxxxxx",
            "PrivateIpAddress": "",
            "Status": "InUse",
            "BandwidthPackageId": "",
            "InstanceId": "ngw-uf681h38pbvlyxxxxxxxx",
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
            "AllocationTime": "2019-04-24T10:03:08Z",
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
      "RequestId": "F0AEE605-14AD-4ADD-980C-4B508CE7EE4B"
    }
    
    ---------------------------create_common_bandwidth_package----------------------
    -----
    {
      "ResourceGroupId": "rg-acfmxazxxxxxxxx",
      "BandwidthPackageId": "cbwp-uf6dmfvq0gzzgxxxxxxxx",
      "RequestId": "D5E02777-2A72-42EC-8308-5D4B6E56D900"
    }
    
    ---------------------------add_common_bandwidth_packageIp-----------------------
    ----
    {
      "RequestId": "3B4CD99C-6E59-4DA2-9256-EACF3F699412"
    }
    
    ---------------------------describe_nat_gateway---------------------------
    {
      "TotalCount": 1,
      "PageNumber": 1,
      "RequestId": "A07498A0-4D60-4E0F-A7DE-3A832B174D59",
      "PageSize": 10,
      "NatGateways": {
        "NatGateway": [
          {
            "Status": "Available",
            "BandwidthPackageIds": {
              "BandwidthPackageId": []
            },
            "VpcId": "vpc-uf6mqfqx8vjmoxxxxxxxx",
            "Description": "",
            "ForwardTableIds": {
              "ForwardTableId": [
                "ftb-uf6jd0vbyao2dxxxxxxxx"
              ]
            },
            "IpLists": {
              "IpList": [
                {
                  "UsingStatus": "Idle",
                  "IpAddress": "106.xx.xx.129",
                  "AllocationId": "eip-uf62tf8y4uyacxxxxxxxx"
                }
              ]
            },
            "BusinessStatus": "Normal",
            "RegionId": "cn-shanghai",
            "CreationTime": "2019-04-24T10:03:05Z",
            "NatGatewayId": "ngw-uf681h38pbvlyxxxxxxxx",
            "SnatTableIds": {
              "SnatTableId": [
                "stb-uf6uj997htg3uxxxxxxxx"
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
    
    ---------------------------unassociate_eip_address nat--------------------------
    -
    {
      "RequestId": "92CB670E-239D-4659-B91F-E0565D5C0F2D"
    }
    
    ---------------------------remove_common_bandwidth_packageIp--------------------
    -------
    {
      "RequestId": "A58E9647-6761-4CA3-8786-3CD4E7D2A7AB"
    }
    
    ---------------------------delete_common_bandwidth_package----------------------
    -----
    {
      "RequestId": "4AA428BC-B72F-4567-94B8-AC2398EF7529"
    }
    
    ---------------------------delete_nat_gateway---------------------------
    {
      "RequestId": "EC6C5D04-AF7D-4560-A30E-80EC141D174D"
    }
    
    ---------------------------release_eip_address---------------------------
    {
      "RequestId": "9B1380B3-EE97-49BD-88FE-DBF356304208"
    }
    
    ---------------------------delete_vswitch---------------------------
    {
      "RequestId": "A9A1D63E-5709-4B98-90BF-9069AA264230"
    }
    
    ---------------------------delete_vpc---------------------------
    {
      "RequestId": "3B687C37-5315-4E0B-BE13-103BB287A80D"
    }
    ```


