# Attach an EIP to an SLB instance or an ENI {#task_185782 .task}

This topic describes how to use the Alibaba Cloud Python SDK to attach an EIP to an SLB instance or an ENI.

Before you attach an EIP to an SLB instance or an ENI, you must ensure that a VPC and a VSwitch are created in the China \(Hangzhou\) region and an ENI is created under the VPC and the VSwitch.

The detailed steps used in this tutorial to attach an EIP to an SLB instance/ENI are as follows:

1.  Create an SLB instance in the China \(Hangzhou\) region.
2.  Create an EIP in the China \(Hangzhou\) region.
3.  Attach the EIP to the SLB instance.
4.  Detach the EIP from the SLB instance.
5.  Attach the detached EIP to the ENI.
6.  Detach the EIP from the ENI.
7.  Delete the SLB instance.

1.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\sdk\_lib folder.
2.  Open the consts.py file in your text editor and configure the ACS\_CLIENT parameter used for authentication.
3.  In the downloaded SDK directory, open the $aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\eip folder.
4.  Open the eip\_associate\_slb.py file in your editor and configure your required parameters. Then, save the configurations and exit the editor. 

    ``` {#codeblock_bez_zke_0oo}
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
    from sdk_lib.sdk_load_balancer import LoadBalancer
    
    """
    Create a VPC->Create a VSwitch->Call an ECS API action to generate an ENI (these steps are not included
    in the following codes)
    Create an SLB instance->Create an EIP->Attach the EIP to the SLB instance->Detach the EIP from the SLB instance
    ->Attach the EIP to the ENI->Detach the EIP from the ENI->Delete the SLB instance
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
            associate_eip_address: Attach the EIP to an cloud product instance in the same region
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
            describe_eip_status: Query one or more EIPs in a region
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
            describe_eip_status: Query the status of an EIP
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36018.htm
            """
            # The ID of the EIP
            response = self.describe_eip_address(allocation_id)
            return response["EipAddresses"]["EipAddress"][0]["Status"]
    
    
        def unassociate_eip_address(self, params):
            """
            unassociate_eip_address: Detach the EIP from the cloud resource
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36021.htm
            """
            try:
                request = UnassociateEipAddressRequest.UnassociateEipAddressRequest()
                # The ID of the EIP
                request.set_AllocationId(params['allocation_id'])
                # The type of the resource to detach
                request.set_InstanceType(params['instance_type'])
                # The ID of the cloud product instance to detach
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
            modify_eip_address: Modify the name, description and peak bandwidth of an EIP
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
            API reference link: https://partners-intl.aliyun.com/help/doc-detail/36020.htm
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
        load_balancer = LoadBalancer(client)
        #Create a VPC, create a VSwitch, and call an ECS API action to generate an ENI
        params = {}
        params['vpc_id'] = VPC_ID
        params['vswitch_id'] = VSWITCH_ID
    
        #Create an SLB instance
        load_balancer_repsonse_json = load_balancer.create_load_balancer_private(params)
        CommonUtil.log("create_load_balancer", load_balancer_repsonse_json)
    
        # Create an EIP
        params['load_balancer_id'] = load_balancer_repsonse_json['LoadBalancerId']
        params['instance_id'] = load_balancer_repsonse_json['LoadBalancerId']
        eip_response_json = eip.allocate_eip_address(params)
        CommonUtil.log("allocate_eip_address slb", eip_response_json)
    
        # Attach the EIP to the SLB instance
        params['allocation_id'] = eip_response_json["AllocationId"]
        params['instance_type'] = 'SlbInstance'
        eip_response_json = eip.associate_eip_address(params)
        CommonUtil.log("associate_eip_address eip", eip_response_json)
    
        # Detach the EIP from the SLB instance
        eip_response_json = eip.unassociate_eip_address(params)
        CommonUtil.log("unassociate_eip_address slb", eip_response_json)
    
        # Attach the EIP to the ENI
        params['instance_id'] = ENI_ID
        params['instance_type'] = 'NetworkInterface'
        eip_response_json = eip.associate_eip_address(params)
        CommonUtil.log("associate_eip_address eni", eip_response_json)
    
        # Detach the EIP from the ENI
        eip_response_json = eip.unassociate_eip_address(params)
        CommonUtil.log("unassociate_eip_address eni", eip_response_json)
    
        # Delete the SLB instance
        load_balancer_repsonse_json = load_balancer.delete_load_balancer(params)
        CommonUtil.log("delete_load_balancer", load_balancer_repsonse_json)
    
    if __name__ == '__main__':
        sys.exit(main())
    ```

5.  Access the eip\_associate\_slb.py directory and run the following command to attach the EIP to the SLB instance or the ENI. 

    ```
    Python eip_associate_slb.py
    ```

    The system displays the following output:

    ``` {#codeblock_3fb_px8_qxa}
    ---------------------------create_load_balancer---------------------------
    {
      "VpcId": "vpc-bp15opprpg0rgxxxxxxxx",
      "AddressIPVersion": "ipv4",
      "LoadBalancerName": "auto_named_slb",
      "ResourceGroupId": "rg-acfm4odxxxxxxxx",
      "VSwitchId": "vsw-bp1e67w26n2sjxxxxxxxx",
      "RequestId": "D3651A96-008C-4B35-A36E-54C2902535C5",
      "Address": "172.xx.xx.146",
      "NetworkType": "vpc",
      "LoadBalancerId": "lb-bp15u6kumammdxxxxxxxx"
    }
    ---------------------------allocate_eip_address slb---------------------------
    {
      "EipAddress": "47.xx.xx.76",
      "ResourceGroupId": "rg-acfm4odxxxxxxxx",
      "RequestId": "15FD58CD-B186-4E2C-B4B3-74F712168832",
      "AllocationId": "eip-bp1ofhmmep6rkxxxxxxxx"
    }
    ---------------------------associate_eip_address eip---------------------------
    {
      "RequestId": "5EDABF0B-A067-474E-9556-0A3AA870960A"
    }
    ---------------------------unassociate_eip_address slb--------------------------
    -
    {
      "RequestId": "89556510-D726-490A-9092-9BEA0644CC43"
    }
    ---------------------------associate_eip_address eni---------------------------
    {
      "RequestId": "FAE87FDD-232A-4859-803B-F9B57508AEDC"
    }
    ---------------------------unassociate_eip_address eni--------------------------
    -
    {
      "RequestId": "7DF556E8-12BE-481A-B83D-B3D9E8836534"
    }
    ---------------------------delete_load_balancer---------------------------
    {
      "RequestId": "2B70C01A-A440-40A5-A98B-83A687537CCE"
    }
    ```


