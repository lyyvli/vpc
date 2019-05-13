# Create an SNAT entry {#task_188260 .task}

This topic describes how to use the Alibaba Cloud Python SDK to create an SNAT entry.

The detailed steps used in this tutorial to create an SNAT entry are as follows:

1.  Create a VPC in the China \(Shanghai\) region.
2.  Create a VSwitch under the VPC.
3.  Create a NAT Gateway under the VPC.
4.  Create an EIP in the China \(Shanghai\) region.
5.  Attach the EIP to the NAT Gateway.
6.  Create an SNAT entry.
7.  Query the EIP attached to the NAT Gateway.
8.  Query the NAT Gateway.
9.  Delete the SNAT entry.
10. Detach the EIP from the NAT Gateway.
11. Delete the NAT Gateway.
12. Release the EIP.
13. Delete the VSwitch.
14. Delete the VPC.

1.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\sdk\_lib folder.
2.  Open the consts.py file in your text editor and configure the ACS\_CLIENT parameter used for user authentication.
3.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\natgw folder.
4.  Open the natgw\_snat.py file in your text editor and configure your required parameters. Then, save the configurations and exit the text editor. 

    ``` {#codeblock_m9l_66o_nmv}
    #encoding=utf-8
    import sys
    import json
    import time
    
    from aliyunsdkcore.acs_exception.exceptions import ServerException, ClientException
    from aliyunsdkvpc.request.v20160428 import CreateNatGatewayRequest
    from aliyunsdkvpc.request.v20160428 import DeleteNatGatewayRequest
    from aliyunsdkvpc.request.v20160428 import DescribeNatGatewaysRequest
    from aliyunsdkvpc.request.v20160428 import CreateSnatEntryRequest
    from aliyunsdkvpc.request.v20160428 import DescribeSnatTableEntriesRequest
    from aliyunsdkvpc.request.v20160428 import DeleteSnatEntryRequest
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
            delete_nat_gateway: Delete the NAT Gateway
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
    
        def create_snat_entry(self, params):
            """
            describe_snat: Create an SNAT entry
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/42672.htm
            """
            try:
                request = CreateSnatEntryRequest.CreateSnatEntryRequest()
                request.set_SnatTableId(params['snat_table_id'])
                request.set_SourceVSwitchId(params['vswitch_id'])
                request.set_SnatIp(params['snat_ip'])
                response = client.do_action_with_exception(request)
                response_json = json.loads(response)
                # Check if the SNAT entry is in the available state
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_snat_status,
                                            AVAILABLE, params['snat_table_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_snat(self, snat_table_id):
            """
            describe_snat: Query SNAT entries in a region
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/42677.htm
            """
            try:
                request = DescribeSnatTableEntriesRequest.DescribeSnatTableEntriesRequest()
                request.set_SnatTableId(snat_table_id)
                response = client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_snat_status(self, snat_table_id):
            """
            describe_snat_status: Query the status of SNAT entries in a region
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/42677.htm
            """
            response = self.describe_snat(snat_table_id)
            if len(response["SnatTableEntries"]["SnatTableEntry"]) == 0:
                return ''
            return response["SnatTableEntries"]["SnatTableEntry"][0]['Status']
    
        def delete_snat_entry(self, params):
            """
            delete_snat_entry: Delete an SNAT entry
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/42678.htm
            """
            try:
                request = DeleteSnatEntryRequest.DeleteSnatEntryRequest()
                request.set_SnatTableId(params['snat_table_id'])
                request.set_SnatEntryId(params['snat_entry_id'])
                response = client.do_action_with_exception(request)
                response_json = json.loads(response)
                # Check if the SNAT entry is in the available state
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME * 5,
                                            self.describe_snat_status,
                                            '', params['snat_table_id']):
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
        params['snat_ip'] = eip_response_json['EipAddress']
    
        # Attach the EIP to the NAT Gateway
        params['instance_id'] = nat_gateway_json['NatGatewayId']
        params['allocation_id'] = eip_response_json["AllocationId"]
        params['instance_type'] = 'Nat'
        eip_response_json = eip.associate_eip_address(params)
        CommonUtil.log("associate_eip_address eip", eip_response_json)
    
        # Create an SNAT entry
        params['snat_table_id'] = nat_gateway_json['SnatTableIds']['SnatTableId'][0]
        snat_entry_json = nat_gateway.create_snat_entry(params)
        CommonUtil.log("create_snat_entry", snat_entry_json)
    
        # Query the EIP
        eip_response_json = eip.describe_eip_address(params['allocation_id'])
        CommonUtil.log("describe_eip_address", eip_response_json)
    
        # Query the NAT Gateway
        params['nat_gateway_id'] = nat_gateway_json['NatGatewayId']
        nat_gateway_json = nat_gateway.describe_nat_gateway(params['nat_gateway_id'])
        CommonUtil.log("describe_nat_gateway", nat_gateway_json)
    
        # Delete the SNAT entry
        params['snat_entry_id'] = snat_entry_json['SnatEntryId']
        snat_entry_json = nat_gateway.delete_snat_entry(params)
        CommonUtil.log("delete_snat_entry", snat_entry_json)
    
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

5.  Access the natgw\_snat.py directory and run the following command to create an SNAT entry. 

    ``` {#codeblock_wx7_rrn_aq9}
    python natgw_snat.py
    ```

    The system displays the following output:

    ``` {#codeblock_gny_o00_clr}
    ---------------------------create_vpc---------------------------
    {
      "ResourceGroupId": "rg-acfmxazxxxxxxxx",
      "RouteTableId": "vtb-uf6a8ccj9ne58xxxxxxxx",
      "VRouterId": "vrt-uf6qqqaf1o1ptxxxxxxxx",
      "VpcId": "vpc-uf6hxer3h07wgxxxxxxxx",
      "RequestId": "8F483A7B-8A38-47ED-85BD-1E83C075AEA4"
    }
    
    ---------------------------create_vswitch---------------------------
    {
      "VSwitchId": "vsw-uf6lbov9tyetqxxxxxxxx",
      "RequestId": "2EE2E11B-EF60-4C88-BE2A-F45517290B31"
    }
    
    ---------------------------create_nat_gateway---------------------------
    {
      "NatGatewayId": "ngw-uf6l3c3rswubuxxxxxxxx",
      "BandwidthPackageIds": {
        "BandwidthPackageId": []
      },
      "ForwardTableIds": {
        "ForwardTableId": [
          "ftb-uf6086r1hyecbxxxxxxxx"
        ]
      },
      "RequestId": "9037D769-24C8-46AD-83F3-4C0538FA5970",
      "SnatTableIds": {
        "SnatTableId": [
          "stb-uf6ppo11rsecmxxxxxxxx"
        ]
      }
    }
    
    ---------------------------allocate_eip_address---------------------------
    {
      "EipAddress": "101.xx.xx.110",
      "ResourceGroupId": "rg-acfmxazxxxxxxxx",
      "RequestId": "0DE621B4-6BDE-4E17-A294-8F71FBB9F710",
      "AllocationId": "eip-uf6d311cpmr0nxxxxxxxx"
    }
    
    ---------------------------associate_eip_address eip---------------------------
    {
      "RequestId": "C95B2EDC-F081-4784-B60B-2600F60E684D"
    }
    
    ---------------------------create_snat_entry---------------------------
    {
      "SnatEntryId": "snat-uf6ppbwshdu40xxxxxxxx",
      "RequestId": "BB9F8FD2-3CB5-4F84-8006-FE64BF3BEA06"
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
            "AllocationId": "eip-uf6d311cpmr0nxxxxxxxx",
            "PrivateIpAddress": "",
            "Status": "InUse",
            "BandwidthPackageId": "",
            "InstanceId": "ngw-uf6l3c3rswubuxxxxxxxx",
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
            "AllocationTime": "2019-04-24T11:20:09Z",
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
      "RequestId": "19052237-6E84-4258-89B9-05772C33C0DC"
    }
    
    ---------------------------describe_nat_gateway---------------------------
    {
      "TotalCount": 1,
      "PageNumber": 1,
      "RequestId": "26CAA3FE-B400-4522-9582-2DAAF69129AE",
      "PageSize": 10,
      "NatGateways": {
        "NatGateway": [
          {
            "Status": "Available",
            "BandwidthPackageIds": {
              "BandwidthPackageId": []
            },
            "VpcId": "vpc-uf6hxer3h07wgxxxxxxxx",
            "Description": "",
            "ForwardTableIds": {
              "ForwardTableId": [
                "ftb-uf6086r1hyecbxxxxxxxx"
              ]
            },
            "IpLists": {
              "IpList": [
                {
                  "UsingStatus": "UsedBySnatTable",
                  "IpAddress": "101.xx.xx.110",
                  "AllocationId": "eip-uf6d311cpmr0nxxxxxxxx"
                }
              ]
            },
            "BusinessStatus": "Normal",
            "RegionId": "cn-shanghai",
            "CreationTime": "2019-04-24T11:20:06Z",
            "NatGatewayId": "ngw-uf6l3c3rswubuxxxxxxxx",
            "SnatTableIds": {
              "SnatTableId": [
                "stb-uf6ppo11rsecmxxxxxxxx"
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
    
    ---------------------------delete_snat_entry---------------------------
    {
      "RequestId": "CDA82881-ACF0-4DD1-887B-A764F56F180D"
    }
    
    ---------------------------unassociate_eip_address nat--------------------------
    -
    {
      "RequestId": "140C46FF-0DB0-47F9-B0F4-3459DF117EAF"
    }
    
    ---------------------------delete_nat_gateway---------------------------
    {
      "RequestId": "8709747C-6786-443C-8AEA-51647AA49769"
    }
    
    ---------------------------release_eip_address---------------------------
    {
      "RequestId": "0BC21C23-0FB3-4594-8B14-6552DF788C93"
    }
    
    ---------------------------delete_vswitch---------------------------
    {
      "RequestId": "16E840EC-E058-40C1-A5BF-8CDF672EA139"
    }
    
    ---------------------------delete_vpc---------------------------
    {
      "RequestId": "B5F18126-FF2A-4005-9973-3984034DF0F4"
    }
    ```


