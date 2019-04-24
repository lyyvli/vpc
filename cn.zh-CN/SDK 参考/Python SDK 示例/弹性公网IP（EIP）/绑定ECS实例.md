# 绑定ECS实例 {#task_gkw_xf5_jhb .task}

本文介绍如何使用Python SDK实现EIP绑定ECS实例。

您已经创建了ECS实例，且ECS实例必须满足以下条件：

-   ECS实例的网络类型必须是专有网络。
-   ECS实例的地域必须和EIP的地域相同。
-   ECS实例必须处于运行中或停止状态。
-   ECS实例没有配置固定公网IP或绑定其他EIP。

本次示例分为以下几步，实现EIP绑定ECS实例。

1.  在华东1杭州地域创建一个EIP。
2.  将创建的EIP绑定到ECS。
3.  查询绑定到ECS上的EIP。
4.  修改EIP的带宽峰值和名称。
5.  查询修改后的EIP。
6.  将EIP与ECS解绑。
7.  释放EIP。

1.  在下载的SDK目录中，打开$aliyun-openapi-python-sdk-examples\\sdk\_examples\\sdk\_lib文件夹。
2.  使用编辑器打开consts.py文件，配置用户鉴权参数ACS\_CLIENT。
3.  在下载的SDK目录中，打开$aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\eip文件夹。
4.  使用编辑器打开eip\_quick\_start.py文件，根据实际情况配置相关参数，保存退出。 

    ``` {#codeblock_dys_w26_4gw}
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
    创建EIP->绑定EIP到ECS->查询EIP->修改EIP配置和名字->查询EIP->解绑EIP->释放EIP
    """
    class Eip(object):
        def __init__(self, client):
            self.client = client
    
        def allocate_eip_address(self, params):
            """
            allocate_eip_address: 申请弹性公网IP（EIP)
            官网API参考: https://help.aliyun.com/document_detail/36016.html
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
            associate_eip_address: 将EIP绑定到同地域的云产品实例上
            官网API参考: https://help.aliyun.com/document_detail/36017.html
            """
            try:
                request = AssociateEipAddressRequest.AssociateEipAddressRequest()
                # EIP的ID
                request.set_AllocationId(params['allocation_id'])
                # 要绑定的云产品实例的类型
                request.set_InstanceType(params['instance_type'])
                # 要绑定的实例ID
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
            describe_eip_status: 查询指定地域已创建的EIP。
            官网API参考: https://help.aliyun.com/document_detail/36018.html
            """
            try:
                request = DescribeEipAddressesRequest.DescribeEipAddressesRequest()
                # EIP的ID
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
            describe_eip_status: 查询指定地域已创建的EIP的状态
            官网API参考: https://help.aliyun.com/document_detail/36018.html
            """
            # EIP的ID
            response = self.describe_eip_address(allocation_id)
            return response["EipAddresses"]["EipAddress"][0]["Status"]
    
    
        def unassociate_eip_address(self, params):
            """
            unassociate_eip_address: 将EIP从绑定的云资源上解绑。
            官网API参考: https://help.aliyun.com/document_detail/36021.html
            """
            try:
                request = UnassociateEipAddressRequest.UnassociateEipAddressRequest()
                # EIP的ID
                request.set_AllocationId(params['allocation_id'])
                # 要解绑的资源类型
                request.set_InstanceType(params['instance_type'])
                # 要解绑的云产品的实例ID
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
            modify_eip_address: 修改指定EIP的名称、描述信息和带宽峰值
            官网API参考: https://help.aliyun.com/document_detail/36019.html
            """
            try:
                request = ModifyEipAddressAttributeRequest.ModifyEipAddressAttributeRequest()
                # 弹性公网IP的ID
                request.set_AllocationId(params['allocation_id'])
                # EIP的带宽峰值，单位为Mbps
                request.set_Bandwidth(params['bandwidth'])
                # EIP的名称
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
            release_eip_address: 释放指定的EIP。
            官网API参考: https://help.aliyun.com/document_detail/36020.html
            """
            try:
                request = ReleaseEipAddressRequest.ReleaseEipAddressRequest()
                # 要释放的弹性公网IP的ID
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
    
        # 创建EIP
        eip_response_json = eip.allocate_eip_address(params)
        CommonUtil.log("allocate_eip_address", eip_response_json)
    
        # 绑定EIP到ECS
        params['allocation_id'] = eip_response_json["AllocationId"]
        params['instance_id'] = ECS_INSTANCE_ID
        params['instance_type'] = 'EcsInstance'
        eip_response_json = eip.associate_eip_address(params)
        CommonUtil.log("associate_eip_address", eip_response_json)
    
        # 查询EIP
        eip_response_json = eip.describe_eip_address(params['allocation_id'])
        CommonUtil.log("describe_eip_address", eip_response_json)
    
        # 修改EIP配置和名字
        params['bandwidth'] = BANDWIDTH_50
        params['name'] = EIP_NEW_NAME
        eip_response_json = eip.modify_eip_address(params)
        CommonUtil.log("modify_eip_address", eip_response_json)
    
        # 查询EIP
        eip_response_json = eip.describe_eip_address(params['allocation_id'])
        CommonUtil.log("describe_eip_address", eip_response_json)
    
        # 解绑EIP
        eip_response_json = eip.unassociate_eip_address(params)
        CommonUtil.log("unassociate_eip_address", eip_response_json)
    
        # 释放EIP
        eip_response_json = eip.release_eip_address(params)
        CommonUtil.log("release_eip_address", eip_response_json)
    
    if __name__ == '__main__':
        sys.exit(main())
    ```

5.  进入eip\_quick\_start.py所在的目录，执行如下命令，将EIP绑定ECS实例。 

    ```
    python eip_quick_start.py
    ```

    系统显示类似如下：

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


