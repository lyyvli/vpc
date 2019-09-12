# Modify the peak bandwidth of an EIP {#task_185881 .task}

This topic describes how to use the Alibaba Cloud Python SDK to modify the peak bandwidth of an EIP.

The example used in the procedure of this topic includes the following steps:

1.  Create an EIP in the China \(Hangzhou\) region.
2.  Modify the peak bandwidth of the EIP to 50 Mbit/s.
3.  Query the modified EIP.
4.  Modify the peak bandwidth of the EIP to 10 Mbit/s.
5.  Query the modified EIP.
6.  Release the EIP.

1.  In the SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\sdk\_lib folder.
2.  Open the consts.py file in your text editor and set the ACS\_CLIENT parameter for user authentication.
3.  In the SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\eip folder.
4.  Open the eip\_modify\_attribute.py file in your text editor, set the parameters as needed, and then save the settings and exit the editor. 

    ``` {#codeblock_n8z_dyl_4p3}
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
    Create an EIP -> Modify the peak bandwidth of the EIP to 50 Mbit/s -> Query the EIP -> Modify the peak bandwidth of the EIP to 10 Mbit/s -> Query the EIP -> Release the EIP
    """
    class Eip(object):
        def __init__(self, client):
            self.client = client
    
        def allocate_eip_address(self, params):
            """
            allocate_eip_address: Create an EIP.
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
            associate_eip_address: Associate the EIP with an instance in the same region.
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36017.htm
            """
            try:
                request = AssociateEipAddressRequest.AssociateEipAddressRequest()
                # The ID of the EIP
                request.set_AllocationId(params['allocation_id'])
                # The type of the instance with which the EIP is associated
                request.set_InstanceType(params['instance_type'])
                # The ID of the instance with which the EIP is associated
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
            describe_eip_status: Query the EIP created in the specified region.
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
            describe_eip_status: Query the status of the EIP created in the specified region.
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36018.htm
            """
            # The ID of the EIP
            response = self.describe_eip_address(allocation_id)
            return response["EipAddresses"]["EipAddress"][0]["Status"]
    
    
        def unassociate_eip_address(self, params):
            """
            unassociate_eip_address: Disassociate the EIP from the instance.
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36021.htm
            """
            try:
                request = UnassociateEipAddressRequest.UnassociateEipAddressRequest()
                # The ID of the EIP
                request.set_AllocationId(params['allocation_id'])
                # The type of the instance from which the EIP is disassociated
                request.set_InstanceType(params['instance_type'])
                # The ID of the instance from which the EIP is disassociated
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
            modify_eip_address: Modify the name, description, and peak bandwidth of the specified EIP.
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36019.htm
            """
            try:
                request = ModifyEipAddressAttributeRequest.ModifyEipAddressAttributeRequest()
                # The ID of the EIP
                request.set_AllocationId(params['allocation_id'])
                # The peak bandwidth (Mbit/s) of the EIP
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
            release_eip_address: Release the specified EIP.
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36020.htm
            """
            try:
                request = ReleaseEipAddressRequest.ReleaseEipAddressRequest()
                # The ID of the EIP to be released
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
    
        # Create an EIP.
        eip_response_json = eip.allocate_eip_address(params)
        CommonUtil.log("allocate_eip_address", eip_response_json)
    
        params['allocation_id'] = eip_response_json["AllocationId"]
    
        # Modify the peak bandwidth of the EIP to 50 Mbit/s.
        params['name'] = EIP_NEW_NAME
        params['bandwidth'] = BANDWIDTH_50
        eip_response_json = eip.modify_eip_address(params)
        CommonUtil.log("modify_eip_address", eip_response_json)
    
        # Query the EIP.
        eip_response_json = eip.describe_eip_address(params['allocation_id'])
        CommonUtil.log("describe_eip_address", eip_response_json)
    
        # Modify the peak bandwidth of the EIP to 10 Mbit/s.
        params['bandwidth'] = BANDWIDTH_10
        eip_response_json = eip.modify_eip_address(params)
        CommonUtil.log("modify_eip_address", eip_response_json)
    
        # Query the EIP.
        eip_response_json = eip.describe_eip_address(params['allocation_id'])
        CommonUtil.log("describe_eip_address", eip_response_json)
    
        # Release the EIP.
        eip_response_json = eip.release_eip_address(params)
        CommonUtil.log("release_eip_address", eip_response_json)
    
    if __name__ == '__main__':
        sys.exit(main())
    ```

5.  Enter the directory where the eip\_modify\_attribute.py file is located, and then run the following command to modify the peak bandwidth of the EIP. 

    ```
    python eip_modify_attribute.py
    ```

    The system output is displayed as follows:

    ``` {#codeblock_557_5ua_sza}
    ---------------------------allocate_eip_address---------------------------
    {
      "EipAddress": "47.xx.xx.225",
      "ResourceGroupId": "rg-acfm4odxxxxxxxx",
      "RequestId": "9318DD7A-F065-4EA6-9EA0-20A9C46EDADC",
      "AllocationId": "eip-bp15bzjk5djcsxxxxxxxx"
    }
    ---------------------------modify_eip_address---------------------------
    {
      "RequestId": "C39D55A1-6B47-489B-8614-FDB9736EDE73"
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
            "IpAddress": "47.xx.xx.225",
            "AllocationId": "eip-bp15bzjk5djcsxxxxxxxx",
            "PrivateIpAddress": "",
            "Status": "Available",
            "BandwidthPackageId": "",
            "InstanceId": "",
            "InstanceRegionId": "",
            "RegionId": "cn-hangzhou",
            "AvailableRegions": {
              "AvailableRegion": [
                "cn-hangzhou"
              ]
            },
            "ResourceGroupId": "rg-acfm4odxxxxxxxx",
            "HasReservationData": false,
            "InstanceType": "",
            "AllocationTime": "2019-04-18T04:01:28Z",
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
      "RequestId": "51ECAB45-2518-4A46-89DC-8ADEE1AFDBE9"
    }
    ---------------------------modify_eip_address---------------------------
    {
      "RequestId": "ACAB5724-D05C-46A4-8C2B-6064AEEC792B"
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
            "IpAddress": "47.xx.xx.225",
            "AllocationId": "eip-bp15bzjk5djcsxxxxxxxx",
            "PrivateIpAddress": "",
            "Status": "Available",
            "BandwidthPackageId": "",
            "InstanceId": "",
            "InstanceRegionId": "",
            "RegionId": "cn-hangzhou",
            "AvailableRegions": {
              "AvailableRegion": [
                "cn-hangzhou"
              ]
            },
            "ResourceGroupId": "rg-acfm4odxxxxxxxx",
            "HasReservationData": false,
            "InstanceType": "",
            "AllocationTime": "2019-04-18T04:01:28Z",
            "Name": "EIP_NEW_NAME",
            "OperationLocks": {
              "LockReason": []
            },
            "Mode": "NAT",
            "BandwidthPackageType": "",
            "BandwidthPackageBandwidth": "",
            "Bandwidth": "10",
            "HDMonitorStatus": "OFF",
            "ChargeType": "PostPaid",
            "SecondLimited": false,
            "Descritpion": ""
          }
        ]
      },
      "RequestId": "6F653A80-AB28-4842-84A8-CD444EB81A29"
    }
    ---------------------------release_eip_address---------------------------
    {
      "RequestId": "C407633A-5658-482F-AB5E-069028C3B06C"
    }						
    ```


