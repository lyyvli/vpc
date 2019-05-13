# Add an EIP to an Internet Shared Bandwidth {#task_185799 .task}

This topic describes how to use the Alibaba Cloud Python SDK to add an EIP to an Internet Shared Bandwidth.

The detailed steps used in this tutorial to add an EIP to an Internet Shared Bandwidth are as follows:

1.  Create an EIP in the China \(Hangzhou\) region.
2.  Create an Internet Shared Bandwidth in the China \(Hangzhou\) region.
3.  Add the EIP to the Internet Shared Bandwidth.
4.  Query the Internet Shared Bandwidth.
5.  Remove the EIP from the Internet Shared Bandwidth.
6.  Delete the Internet Shared Bandwidth.
7.  Release the EIP.

1.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\sdk\_lib folder.
2.  Open the consts.py file in your text editor and configure the ACS\_CLIENT parameter used for authentication.
3.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\eip folder.
4.  Open the eip\_add\_cbwp.py file in your editor and configure your required parameters. Then, save the configurations and exit the editor. 

    ``` {#codeblock_2i0_t2h_w6u}
    #encoding=utf-8
    import sys
    from aliyunsdkvpc.request.v20160428 import CreateCommonBandwidthPackageRequest
    from aliyunsdkvpc.request.v20160428 import AddCommonBandwidthPackageIpRequest
    from aliyunsdkvpc.request.v20160428 import DescribeCommonBandwidthPackagesRequest
    from aliyunsdkvpc.request.v20160428 import RemoveCommonBandwidthPackageIpRequest
    from aliyunsdkvpc.request.v20160428 import DeleteCommonBandwidthPackageRequest
    from sdk_lib.common_util import CommonUtil
    from sdk_lib.sdk_eip import *
    
    """
    Create an EIP->Create an Internet Shared Bandwidth->The ID of the Internet Shared Bandwidth->Add the EIP 
    to the Internet Shared Bandwidth->Query the Internet Shared Bandwidth->Remove the EIP from the 
    Internet Shared Bandwidth->Delete the Internet Shared Bandwidth->Release the EIP
    """
    class CommonBandwidthPackage(object):
        def __init__(self, client):
            self.client = client
    
        def create_common_bandwidth_package(self, params):
            """
            create_common_bandwidth_package: Create an Internet Shared Bandwidth
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/55930.htm
            """
            try:
                request = CreateCommonBandwidthPackageRequest.CreateCommonBandwidthPackageRequest()
                # The peak bandwidth in Mbps of the Internet Shared Bandwidth
                request.set_Bandwidth(params['bandwidth'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_cbwp_status,
                                            AVAILABLE, response_json["BandwidthPackageId"]):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def add_common_bandwidth_packageIp(self, params):
            """
            add_common_bandwidth_packageIp: Add the EIP to the Internet Shared Bandwidth
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/55989.htm
            """
            try:
                request = AddCommonBandwidthPackageIpRequest.AddCommonBandwidthPackageIpRequest()
                # The ID of the EIP instance
                request.set_IpInstanceId(params['ip_instance_id'])
                # The ID of the Internet Shared Bandwidth
                request.set_BandwidthPackageId(params['bandwidth_package_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_cbwp(self, cbwp_id):
            """
            describe_cbwp: Query the Internet Shared Bandwidth
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/55997.htm
            """
            try:
                request = DescribeCommonBandwidthPackagesRequest.DescribeCommonBandwidthPackagesRequest()
                # The ID of the Internet Shared Bandwidth
                request.set_BandwidthPackageId(cbwp_id)
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_cbwp_status(self, cbwp_id):
            """
            describe_cbwp: Query the status of the Internet Shared Bandwidth
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/55997.htm
            """
            # The ID of the Internet Shared Bandwidth
            response = self.describe_cbwp(cbwp_id)
            return response["CommonBandwidthPackages"]["CommonBandwidthPackage"][0]["Status"]
    
    
        def remove_common_bandwidth_packageIp(self, params):
            """
            remove_common_bandwidth_packageIp: Remove the EIP from the Internet Shared Bandwidth
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/55995.htm
            """
            try:
                request = RemoveCommonBandwidthPackageIpRequest.RemoveCommonBandwidthPackageIpRequest()
                # The ID of the EIP
                request.set_IpInstanceId(params['ip_instance_id'])
                # The ID of the Internet Shared Bandwidth
                request.set_BandwidthPackageId(params['bandwidth_package_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
    
        def delete_common_bandwidth_package(self, params):
            """
            delete_common_bandwidth_package: Delete the Internet Shared Bandwidth
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/56000.htm
            """
            try:
                request = DeleteCommonBandwidthPackageRequest.DeleteCommonBandwidthPackageRequest()
                # The ID of the Internet Shared Bandwidth
                request.set_BandwidthPackageId(params['bandwidth_package_id'])
                # Indicate whether to forcibly delete the Internet Shared Bandwidth
                request.set_Force(params['force'])
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
        cbwp = CommonBandwidthPackage(client)
    
        params = {}
    
        # Create an EIP
        eip_response_json = eip.allocate_eip_address(params)
        CommonUtil.log("allocate_eip_address", eip_response_json)
        params['allocation_id'] = eip_response_json["AllocationId"]
    
        # Create an Internet Shared Bandwidth
        params['allocation_id'] = eip_response_json["AllocationId"]
        params['ip_instance_id'] = eip_response_json["AllocationId"]
        params['bandwidth'] = BANDWIDTH_10
        cbwp_repsonse_json = cbwp.create_common_bandwidth_package(params)
        CommonUtil.log("create_common_bandwidth_package", cbwp_repsonse_json)
    
        # Add the EIP to the Internet Shared Bandwidth
        params['bandwidth_package_id'] = cbwp_repsonse_json['BandwidthPackageId']
        cbwp_repsonse_json = cbwp.add_common_bandwidth_packageIp(params)
        CommonUtil.log("add_common_bandwidth_packageIp", cbwp_repsonse_json)
    
        # Query the Internet Shared Bandwidth
        cbwp_repsonse_json = cbwp.describe_cbwp(params['bandwidth_package_id'])
        CommonUtil.log("add_common_bandwidth_packageIp", cbwp_repsonse_json)
    
        # Remove the EIP from the Internet Shared Bandwidth
        cbwp_repsonse_json = cbwp.remove_common_bandwidth_packageIp(params)
        CommonUtil.log("remove_common_bandwidth_packageIp", cbwp_repsonse_json)
    
        # Delete the Internet Shared Bandwidth
        params['force'] = True
        cbwp_repsonse_json = cbwp.delete_common_bandwidth_package(params)
        CommonUtil.log("delete_common_bandwidth_package", cbwp_repsonse_json)
    
        # Release the EIP
        eip_response_json = eip.release_eip_address(params)
        CommonUtil.log("release_eip_address", eip_response_json)
    
    if __name__ == '__main__':
        sys.exit(main())
    ```

5.  Access the eip\_add\_cbwp.py directory and run the following command to add the EIP to the Internet Shared Bandwidth. 

    ```
    python eip_add_cbwp.py
    ```

    The system displays the following output:

    ``` {#codeblock_eps_2vu_s96}
    ---------------------------allocate_eip_address---------------------------
    {
      "EipAddress": "118.xx.xx.198",
      "ResourceGroupId": "rg-acfm4odxxxxxxxx",
      "RequestId": "A830A607-B7C4-49FE-A6EE-7237D64CDE2D",
      "AllocationId": "eip-bp1mdyvr22qvgxxxxxxxx"
    }
    ---------------------------create_common_bandwidth_package----------------------
    -----
    {
      "ResourceGroupId": "rg-acfm4odxxxxxxxx",
      "BandwidthPackageId": "cbwp-bp12k058pjjiexxxxxxxx",
      "RequestId": "93127320-DD79-4F83-A3B9-DC99D0597B0C"
    }
    ---------------------------add_common_bandwidth_packageIp-----------------------
    ----
    {
      "RequestId": "7F314AFE-B398-4348-AF61-B7D27B731286"
    }
    ---------------------------add_common_bandwidth_packageIp-----------------------
    ----
    {
      "TotalCount": 1,
      "CommonBandwidthPackages": {
        "CommonBandwidthPackage": [
          {
            "Status": "Available",
            "PublicIpAddresses": {
              "PublicIpAddresse": [
                {
                  "IpAddress": "118.xx.xx.198",
                  "AllocationId": "eip-bp1mdyvr22qvgxxxxxxxx"
                }
              ]
            },
            "BusinessStatus": "Normal",
            "RegionId": "cn-hangzhou",
            "BandwidthPackageId": "cbwp-bp12k058pjjiexxxxxxxx",
            "Name": "",
            "ISP": "BGP",
            "CreationTime": "2019-04-18T01:46:17Z",
            "ResourceGroupId": "rg-acfm4odxxxxxxxx",
            "Bandwidth": "10",
            "InstanceChargeType": "PostPaid",
            "HasReservationData": false,
            "InternetChargeType": "PayByBandwidth",
            "ExpiredTime": "",
            "Ratio": 100,
            "Description": ""
          }
        ]
      },
      "PageNumber": 1,
      "RequestId": "015DD0FA-742B-4431-92EA-E3F03FDEB8CD",
      "PageSize": 10
    }
    ---------------------------remove_common_bandwidth_packageIp--------------------
    -------
    {
      "RequestId": "A49C9126-B703-4D34-B552-A7FE283FB5DD"
    }
    ---------------------------delete_common_bandwidth_package----------------------
    -----
    {
      "RequestId": "E423F648-C169-4B63-A2CF-5E6C8E441DE1"
    }
    ---------------------------release_eip_address---------------------------
    {
      "RequestId": "7E0D34AE-58C3-468A-B021-378F8938AE6B"
    }					
    ```


