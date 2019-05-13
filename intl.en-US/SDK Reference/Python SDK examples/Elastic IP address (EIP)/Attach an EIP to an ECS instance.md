# Attach an EIP to an ECS instance {#task_gkw_xf5_jhb .task}

This topic describes how to use the Alibaba Cloud Python SDK to attach an EIP to an ECS instance.

Before you attach an EIP to an ECS instance, you need to ensure that:

-   The ECS instance is of the VPC network type.
-   The ECS instance and the EIP are locate in the same region.
-   The ECS instance is in the running or stopped status.
-   The ECS instance is not attached to a public IP address or another EIP.

The detailed steps used in this tutorial to attach an EIP to an ECS instance are as follows:

1.  Create an EIP in the China \(Hangzhou\) region.
2.  Attach the EIP to the ECS instance.
3.  Query EIPs attached to the ECS instance.
4.  Modify the peak bandwidth and name of the EIP.
5.  Query the modified EIP.
6.  Disassociate an EIP from an ECS instance.
7.  Release the EIP.

1.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\sdk\_lib folder.
2.  Open the consts.py file in your text editor and configure the ACS\_CLIENT parameter used for user authentication.
3.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\eip folder.
4.  Open the eip\_quick\_start.py file in your editor and configure your required parameters. Then, save the configurations and exit the editor. 

    ``` {#codeblock_g4z_eya_3ai}
    #encoding=utf-8
    import sys
    import json
    from aliyunsdkcore.acs_exception.exceptions import ServerException, ClientException
    from aliyunsdkvpc.request.v20160428 import AllocateEipAddressRequest
    from aliyunsdkvpc.request.v20160428 import AssociateEipAddressRequest
    from aliyunsdkvpc.request.v20160428 import DescribeEipAddressesRequest
    from aliyunsdkvpc.request.v20160428 import UnassociateEipAddressRequest
    from aliyunsdkvpc.request.v20160428 import ModifyEipAddressAttributeRequest
    from aliyunsdkvpc.request.v20160428 import ReleaseEipAddressRequest
    from sdk_lib.exception import ExceptionHandler
    from sdk_lib.check_status import CheckStatus
    from sdk_lib.consts import *
    from sdk_lib.common_util import CommonUtil
    
    """
    Create an EIP->Attach the EIP to an ECS instance->Query EIPs->Modify the configurations and name of the EIP->Query the EIP->Disassociate the EIP->Release the EIP
    """
    class Eip(object):
        def __init__(self, client):
            self.client = client
    
        def allocate_eip_address(self, params):
            """
            allocate_eip_address: Create an EIP
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36016.htm
            """
            try:
                request = AllocateEipAddressRequest.AllocateEipAddressRequest()
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_eip_status,
                                            AVAILABLE, response_json["AllocationId"]):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def associate_eip_address(self, params):
            """
            associate_eip_address: Attach the EIP to a cloud product instance in the same region
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36017.htm
            """
            try:
                request = AssociateEipAddressRequest.AssociateEipAddressRequest()
                # The ID of the EIP
                request.set_AllocationId(params['allocation_id'])
                # The type of the cloud product instance to attach
                request.set_InstanceType(params['instance_type'])
                # The ID of the instance to attach
                request.set_InstanceId(params['instance_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_eip_status,
                                            InUse, params['allocation_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_eip_address(self, allocation_id):
            """
            describe_eip_status: Query EIPs in a region.
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36018.htm
            """
            try:
                request = DescribeEipAddressesRequest.DescribeEipAddressesRequest()
                # The ID of the EIP
                request.set_AllocationId(allocation_id)
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_eip_status(self, allocation_id):
            """
            describe_eip_status: Query the status of EIPs in a region.
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36018.htm
            """
            # The ID of the EIP
            response = self.describe_eip_address(allocation_id)
            return response["EipAddresses"]["EipAddress"][0]["Status"]
    
    
        def unassociate_eip_address(self, params):
            """
            unassociate_eip_address: Disassociate an EIP from a cloud resource.
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36021.htm
            """
            try:
                request = UnassociateEipAddressRequest.UnassociateEipAddressRequest()
                # The ID of the EIP
                request.set_AllocationId(params['allocation_id'])
                # The type of the resource to disassociate
                request.set_InstanceType(params['instance_type'])
                # The ID of the cloud product instance to disassociate
                request.set_InstanceId(params['instance_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_eip_status,
                                            AVAILABLE, params['allocation_id']):
                    return response_json
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def modify_eip_address(self, params):
            """
            modify_eip_address: Modify the name, description, and peak bandwidth of an EIP
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36019.htm
            """
            try:
                request = ModifyEipAddressAttributeRequest.ModifyEipAddressAttributeRequest()
                # The ID of the EIP
                request.set_AllocationId(params['allocation_id'])
                # The peak bandwidth in Mbps of the EIP
                request.set_Bandwidth(params['bandwidth'])
                # The name of the EIP
                request.set_Name(params['name'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def release_eip_address(self, params):
            """
            release_eip_address: Release an EIP
            Release an EIP: https://partners-intl.aliyun.com/help/doc-detail/36020.htm
            """
            try:
                request = ReleaseEipAddressRequest.ReleaseEipAddressRequest()
                # The ID of the EIP to release
                request.set_AllocationId(params['allocation_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
    def main():
    
        client = ACS_CLIENT
        eip = Eip(client)
    
        params = {}
    
        # Create an EIP
        eip_response_json = eip.allocate_eip_address(params)
        CommonUtil.log("allocate_eip_address", eip_response_json)
    
        # Attach the EIP to an ECS instance
        params['allocation_id'] = eip_response_json["AllocationId"]
        params['instance_id'] = ECS_INSTANCE_ID
        params['instance_type'] = 'EcsInstance'
        eip_response_json = eip.associate_eip_address(params)
        CommonUtil.log("associate_eip_address", eip_response_json)
    
        # Query EIPs
        eip_response_json = eip.describe_eip_address(params['allocation_id'])
        CommonUtil.log("describe_eip_address", eip_response_json)
    
        # Modify the configurations and name of the EIP
        params['bandwidth'] = BANDWIDTH_50
        params['name'] = EIP_NEW_NAME
        eip_response_json = eip.modify_eip_address(params)
        CommonUtil.log("modify_eip_address", eip_response_json)
    
        # Query the EIP
        eip_response_json = eip.describe_eip_address(params['allocation_id'])
        CommonUtil.log("describe_eip_address", eip_response_json)
    
        # Disassociate the EIP
        eip_response_json = eip.unassociate_eip_address(params)
        CommonUtil.log("unassociate_eip_address", eip_response_json)
    
        # Release the EIP
        eip_response_json = eip.release_eip_address(params)
        CommonUtil.log("release_eip_address", eip_response_json)
    
    if __name__ == '__main__':
        sys.exit(main())
    ```

5.  Access the eip\_quick\_start.py directory and run the following command to attach the EIP to the ECS instance. 

    ```
    python eip_quick_start.py
    ```

    The system displays the following output:

    ``` {#codeblock_t9c_r1d_qs2}
    ---------------------------allocate_eip_address---------------------------
    {
      "EipAddress": "47.xx.xx.23",
      "ResourceGroupId": "rg-acfm4odxxxxxxxx",
      "RequestId": "C438312E-F7A4-4A04-901F-D22FE23EDB4D",
      "AllocationId": "eip-bp1wybucvhhx5xxxxxxxx"
    }
    ---------------------------associate_eip_address---------------------------
    {
      "RequestId": "6EC6605E-3D2B-4EE8-BD13-F1964CD1EAB1"
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
            "IpAddress": "47.xx.xx.23",
            "AllocationId": "eip-bp1wybucvhhx5xxxxxxxx",
            "PrivateIpAddress": "",
            "Status": "InUse",
            "BandwidthPackageId": "",
            "InstanceId": "i-bp1e82xlhob2xxxxxxxx",
            "InstanceRegionId": "cn-hangzhou",
            "RegionId": "cn-hangzhou",
            "AvailableRegions": {
              "AvailableRegion": [
                "cn-hangzhou"
              ]
            },
            "ResourceGroupId": "rg-acfm4odxxxxxxxx",
            "HasReservationData": false,
            "InstanceType": "EcsInstance",
            "AllocationTime": "2019-04-17T11:57:43Z",
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
      "RequestId": "8715A878-A808-4CC4-AAD5-E414FDAB5B0E"
    }
    ---------------------------modify_eip_address---------------------------
    {
      "RequestId": "2108AE1C-94FB-475D-BFEE-EC88598BF6A6"
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
            "IpAddress": "47.xx.xx.23",
            "AllocationId": "eip-bp1wybucvhhx5xxxxxxxx",
            "PrivateIpAddress": "",
            "Status": "InUse",
            "BandwidthPackageId": "",
            "InstanceId": "i-bp1e82xlhob2xxxxxxxx",
            "InstanceRegionId": "cn-hangzhou",
            "RegionId": "cn-hangzhou",
            "AvailableRegions": {
              "AvailableRegion": [
                "cn-hangzhou"
              ]
            },
            "ResourceGroupId": "rg-acfm4odxxxxxxxx",
            "HasReservationData": false,
            "InstanceType": "EcsInstance",
            "AllocationTime": "2019-04-17T11:57:43Z",
            "Name": "EIP_NEW_NAME",
            "OperationLocks": {
              "LockReason": []
            },
            "Mode": "NAT",
            "BandwidthPackageType": "",
            "BandwidthPackageBandwidth": "",
            "Bandwidth": "50",
            "HDMonitorStatus": "OFF",
            "ChargeType": "PostPaid",
            "SecondLimited": false,
            "Descritpion": ""
          }
        ]
      },
      "RequestId": "6694D35B-B5DD-4506-8AB1-2D16477646DE"
    }
    ---------------------------unassociate_eip_address---------------------------
    {
      "RequestId": "EDE86CF6-EE68-4922-B919-85A4F11BF668"
    }
    ---------------------------release_eip_address---------------------------
    {
      "RequestId": "53FEE062-B595-4D64-AB47-834015D32888"
    }					
    ```


