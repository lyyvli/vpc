# 同账号同地域VPC间互通 {#task_222315 .task}

本文介绍如何使用Python SDK实现同账号同地域下的两个VPC互通。

您已经在同一个账号下创建了两个地域相同的VPC。

创建路由器接口时，请注意：

-   任意两个路由器之间，最多只能存在一对互连的路由器接口。
-   一个路由器上可以最多创建5个路由器接口。
-   如果账户下存在欠费状态的路由器接口，则无法再创建路由器接口。
-   同一路由表下的路由条目的目标网段（DestinationCidrBlock）不允许相同。

本次示例分为以下几步，实现同账号同地域的两个VPC互通。

1.  创建发起端路由器接口。
2.  创建接收端路由器接口。
3.  修改发起端路由器接口的信息。
4.  修改接收端路由器接口的信息。
5.  查询发起端路由器接口的信息。
6.  查询接收端路由器接口的信息。
7.  连接发起端路由器接口和接收端路由器接口。
8.  创建下一跳为发起端路由器接口的路由条目。
9.  创建下一跳为接收端路由器接口的路由条目。
10. 删除下一跳为接收端路由器接口的路由条目。
11. 删除下一跳为发起端路由器接口的路由条目。
12. 冻结发起端路由器接口。
13. 冻结接收端路由器接口。
14. 删除发起端路由器接口。
15. 删除接收端路由器接口。

1.  在下载的SDK目录中，打开$aliyun-openapi-python-sdk-examples\\sdk\_examples\\sdk\_lib文件夹。
2.  使用编辑器打开consts.py文件，配置用户鉴权参数ACS\_CLIENT。
3.  在下载的SDK目录中，打开$aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\ec文件夹。
4.  使用编辑器打开ec\_same\_account.py文件，根据实际情况配置相关参数，保存退出。 

    ``` {#codeblock_aof_mmf_5h9}
    #encoding=utf-8
    import sys
    import json
    from aliyunsdkcore.acs_exception.exceptions import ServerException, ClientException
    from aliyunsdkvpc.request.v20160428 import CreateRouterInterfaceRequest
    from aliyunsdkvpc.request.v20160428 import DeleteRouterInterfaceRequest
    from aliyunsdkvpc.request.v20160428 import DescribeRouterInterfacesRequest
    from aliyunsdkvpc.request.v20160428 import ConnectRouterInterfaceRequest
    from aliyunsdkvpc.request.v20160428 import DeactivateRouterInterfaceRequest
    from aliyunsdkvpc.request.v20160428 import ModifyRouterInterfaceAttributeRequest
    from sdk_lib.sdk_route_entry import RouteEntry
    from sdk_lib.exception import ExceptionHandler
    from sdk_lib.common_util import CommonUtil
    from sdk_lib.check_status import CheckStatus
    from sdk_lib.consts import *
    
    client = ACS_CLIENT
    
    class RouterInterface(object):
        def __init__(self, client):
            self.client = client
    
        def create_router_interface(self, params):
            """
            create_router_interface: 创建路由器接口
            官网API参考: https://www.alibabacloud.com/help/doc-detail/36032.htm
            """
            try:
                request = CreateRouterInterfaceRequest.CreateRouterInterfaceRequest()
                # 路由器接口的规格
                request.set_Spec(params['spec'])
                # 路由器接口的角色
                request.set_Role(params['role'])
                # 路由器接口关联的路由器ID
                request.set_RouterId(params['router_id'])
                # 路由器接口关联的路由器类型
                request.set_RouterType(params['router_type'])
                # 连接接收端所在的地域ID
                request.set_OppositeRegionId(params['opposite_region_id'])
                # 对端路由器接口关联的路由器类型
                request.set_OppositeRouterType(params['opposite_router_type'])
    
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # 判断路由器接口状态是否可用
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_ri_status,
                                            'Idle', response_json['RouterInterfaceId']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def connect_router_interface(self, params):
            """
            connect_router_interface: 由发起端路由器接口向接收端发起连接
            官网API参考: https://www.alibabacloud.com/help/doc-detail/36031.htm
            """
            try:
                request = ConnectRouterInterfaceRequest.ConnectRouterInterfaceRequest()
                # 发起端路由器接口的ID
                request.set_RouterInterfaceId(params['router_interface_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                if CheckStatus.check_status(TIME_DEFAULT_OUT * 5, DEFAULT_TIME * 5,
                                            self.describe_ri_status,
                                            'Active', params['router_interface_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def deactivate_router_interface(self, params):
            """
            deactivate_router_interface: 冻结路由器接口
            官网API参考: https://www.alibabacloud.com/help/doc-detail/36033.htm
            """
            try:
                request = DeactivateRouterInterfaceRequest.DeactivateRouterInterfaceRequest()
                # 路由器接口的ID
                request.set_RouterInterfaceId(params['router_interface_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # 判断路由器接口状态是否可用
                if CheckStatus.check_status(TIME_DEFAULT_OUT * 5, DEFAULT_TIME * 5,
                                            self.describe_ri_status,
                                            'Inactive', params['router_interface_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def modify_router_interface_attribute(self, params):
            """
            modify_router_interface_attribute: 修改路由器接口的配置
            官网API参考: https://www.alibabacloud.com/help/doc-detail/36036.htm
            """
            try:
                request = ModifyRouterInterfaceAttributeRequest.ModifyRouterInterfaceAttributeRequest()
                # 路由器接口的ID
                request.set_RouterInterfaceId(params['router_interface_id'])
                # 对端路由器接口ID
                request.set_OppositeInterfaceId(params['opposite_interface_id'])
                # 对端的路由器的ID
                request.set_OppositeRouterId(params['opposite_router_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # 判断路由器接口状态是否可用
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_ri_status,
                                            'Idle', params['router_interface_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
    
    
        def describe_router_interface(self, instance_id):
            """
            describe_router_interface: 查询指定地域内的路由器接口
            官网API参考: https://www.alibabacloud.com/help/doc-detail/36035.htm
            """
            try:
                request = DescribeRouterInterfacesRequest.DescribeRouterInterfacesRequest()
                # 查询的过滤类型
                request.add_query_param('Filter.1.Key', "RouterInterfaceId")
                # 查询的实例ID
                request.add_query_param('Filter.1.Value.1', instance_id)
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_ri_status(self, instance_id):
            """
            describe_ri_status: 查询指定地域内的路由器接口状态
            官网API参考: https://www.alibabacloud.com/help/doc-detail/36035.htm
            """
            response = self.describe_router_interface(instance_id)
            if len(response['RouterInterfaceSet']['RouterInterfaceType']) == 0:
                return ''
            return response['RouterInterfaceSet']['RouterInterfaceType'][0]['Status']
    
        def delete_router_interface(self, params):
            """
            delete_router_interface: 删除路由器接口
            官网API参考: https://www.alibabacloud.com/help/doc-detail/36034.htm
            """
            try:
                request = DeleteRouterInterfaceRequest.DeleteRouterInterfaceRequest()
                # 路由器接口的ID
                request.set_RouterInterfaceId(params['instance_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # 判断Router Interface状态是否可用
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME * 5,
                                            self.describe_ri_status,
                                            '', params['instance_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
    def main():
        client = ACS_CLIENT
        router_interface = RouterInterface(client)
        route_entry = RouteEntry(client)
    
        params = {}
        params['spec'] = "Large.2"
        params['role'] = "InitiatingSide"
        params['router_id'] = ROUTER_ID
        params['router_type'] = "VRouter"
        params['opposite_region_id'] = "cn-hangzhou"
        params['opposite_router_type'] = "VRouter"
    
        # 创建发起端路由器接口
        router_interface_json = router_interface.create_router_interface(params)
        CommonUtil.log("create_router_interface", router_interface_json)
    
        # 创建接收端路由器接口
        params['spec'] = "Negative"
        params['role'] = "AcceptingSide"
        params['router_id'] = ROUTER_ID2
        router_interface_json2 = router_interface.create_router_interface(params)
        CommonUtil.log("create_router_interface", router_interface_json2)
    
        # 修改发起端路由器接口信息
        params['router_interface_id'] = router_interface_json['RouterInterfaceId']
        params['opposite_interface_id'] = router_interface_json2['RouterInterfaceId']
        params['opposite_router_id'] = ROUTER_ID2
        modify_ri_json = router_interface.modify_router_interface_attribute(params)
        CommonUtil.log("modify_router_interface_attribute", modify_ri_json)
    
        # 修改接收端路由器接口信息
        params['router_interface_id'] = router_interface_json2['RouterInterfaceId']
        params['opposite_interface_id'] = router_interface_json['RouterInterfaceId']
        params['opposite_router_id'] = ROUTER_ID
        modify_ri_json2 = router_interface.modify_router_interface_attribute(params)
        CommonUtil.log("modify_router_interface_attribute", modify_ri_json2)
    
        # 查询发起端路由器接口信息
        describe_ri_json = router_interface.describe_router_interface(router_interface_json['RouterInterfaceId'])
        CommonUtil.log("describe_router_interface", describe_ri_json)
    
        # 查询接收端路由器接口信息
        describe_ri_json2 = router_interface.describe_router_interface(router_interface_json2['RouterInterfaceId'])
        CommonUtil.log("describe_router_interface", describe_ri_json2)
    
        # 发起连接
        params['router_interface_id'] = router_interface_json['RouterInterfaceId']
        connect_ri_json = router_interface.connect_router_interface(params)
        CommonUtil.log("connect_router_interface", connect_ri_json)
    
        # 创建下一跳为发起端路由器接口的路由条目
        params['route_table_id'] = TABLE_ID
        params['destination_cidr_block'] = "0.0.0.0/0"
        params['nexthop_type'] = 'RouterInterface'
        params['nexthop_id'] = router_interface_json['RouterInterfaceId']
        route_entry_json = route_entry.create_route_entry(params)
        CommonUtil.log("create_route_entry", route_entry_json)
    
        # 创建下一跳为接收端路由器接口的路由条目
        params['route_table_id'] = TABLE_ID2
        params['destination_cidr_block'] = "0.0.0.0/0"
        params['nexthop_type'] = 'RouterInterface'
        params['nexthop_id'] = router_interface_json2['RouterInterfaceId']
        route_entry_json2 = route_entry.create_route_entry(params)
        CommonUtil.log("create_route_entry", route_entry_json2)
    
        # 删除下一跳为接收端路由器接口的路由条目
        route_entry_json = route_entry.delete_route_entry(params)
        CommonUtil.log("delete_route_entry", route_entry_json)
    
        # 删除下一跳为发起端路由器接口的路由条目
        params['route_table_id'] = TABLE_ID
        params['nexthop_id'] = router_interface_json['RouterInterfaceId']
        route_entry_json = route_entry.delete_route_entry(params)
        CommonUtil.log("delete_route_entry", route_entry_json)
    
        # 冻结发起端路由器接口
        params['router_interface_id'] = router_interface_json['RouterInterfaceId']
        deactivate_ri_json = router_interface.deactivate_router_interface(params)
        CommonUtil.log("deactivate_router_interface", deactivate_ri_json)
    
        # 冻结接收端路由器接口
        params['router_interface_id'] = router_interface_json2['RouterInterfaceId']
        deactivate_ri_json2 = router_interface.deactivate_router_interface(params)
        CommonUtil.log("deactivate_router_interface", deactivate_ri_json2)
    
        # 删除发起端路由器接口
        params['instance_id'] = router_interface_json['RouterInterfaceId']
        router_interface_json = router_interface.delete_router_interface(params)
        CommonUtil.log("delete_router_interface", router_interface_json)
    
        # 删除接收端路由器接口
        params['instance_id'] = router_interface_json2['RouterInterfaceId']
        router_interface_json2 = router_interface.delete_router_interface(params)
        CommonUtil.log("delete_router_interface", router_interface_json2)
    
    
    if __name__ == '__main__':
        sys.exit(main())
    					
    ```

5.  进入ec\_same\_account.py所在的目录，执行如下命令，实现同账号同地域下的两个VPC互通。 

    ``` {#codeblock_5ry_ghp_jxe}
    python ec_same_account.py
    ```

    系统显示类似如下：

    ``` {#codeblock_uqd_msr_kms}
    ---------------------------create_router_interface---------------------------
    {
      "RequestId": "F5493DC1-53B0-4916-874F-87773A54525F", 
      "RouterInterfaceId": "ri-bp1ujwb6xsw16xxxxxxxx"
    }
    ---------------------------create_router_interface---------------------------
    {
      "RequestId": "E3F5BE99-B2C5-4751-8173-0F590300EE72", 
      "RouterInterfaceId": "ri-bp1vze2rusg2cxxxxxxxx"
    }
    ---------------------------modify_router_interface_attribute---------------------------
    {
      "RequestId": "8D691507-F31A-41E5-9C72-457EFF1F7727"
    }
    ---------------------------modify_router_interface_attribute---------------------------
    {
      "RequestId": "2E664208-8F37-4F19-B719-00B4F1AF03B2"
    }
    ---------------------------describe_router_interface---------------------------
    {
      "TotalCount": 1, 
      "RouterInterfaceSet": {
        "RouterInterfaceType": [
          {
            "BusinessStatus": "Normal", 
            "CreationTime": "2019-04-30T06:09:16Z", 
            "Role": "InitiatingSide", 
            "OppositeRouterId": "vrt-bp141no9pds2bxxxxxxxx", 
            "Spec": "Large.2", 
            "Status": "Idle", 
            "EndTime": "2999-09-08T16:00:00Z", 
            "OppositeInterfaceSpec": "Negative", 
            "RouterInterfaceId": "ri-bp1ujwb6xsw16xxxxxxxx", 
            "RouterType": "VRouter", 
            "OppositeBandwidth": 0, 
            "OppositeVpcInstanceId": "vpc-bp1v31by9jix2xxxxxxxx", 
            "HasReservationData": false, 
            "OppositeInterfaceBusinessStatus": "Normal", 
            "OppositeRouterType": "VRouter", 
            "OppositeRegionId": "cn-hangzhou", 
            "VpcInstanceId": "vpc-bp15opprpg0rgxxxxxxxx", 
            "RouterId": "vrt-bp1ltkytn6lgmxxxxxxxx", 
            "CrossBorder": false, 
            "OppositeInterfaceOwnerId": "", 
            "Bandwidth": 2048, 
            "OppositeInterfaceId": "ri-bp1vze2rusg2cxxxxxxxx", 
            "ChargeType": "AfterPay"
          }
        ]
      }, 
      "PageNumber": 1, 
      "RequestId": "89EF0631-0A36-41AD-A586-AF4FFDA6E68B", 
      "PageSize": 10
    }
    ---------------------------describe_router_interface---------------------------
    {
      "TotalCount": 1, 
      "RouterInterfaceSet": {
        "RouterInterfaceType": [
          {
            "Status": "Idle", 
            "OppositeRegionId": "cn-hangzhou", 
            "BusinessStatus": "Normal", 
            "OppositeRouterId": "vrt-bp1ltkytn6lgmxxxxxxxx", 
            "VpcInstanceId": "vpc-bp1v31by9jix2xxxxxxxx", 
            "RouterInterfaceId": "ri-bp1vze2rusg2cxxxxxxxx", 
            "CreationTime": "2019-04-30T06:09:18Z", 
            "RouterType": "VRouter", 
            "OppositeInterfaceOwnerId": "", 
            "RouterId": "vrt-bp141no9pds2bxxxxxxxx", 
            "Bandwidth": 0, 
            "OppositeInterfaceId": "ri-bp1ujwb6xsw16xxxxxxxx", 
            "EndTime": "2999-09-08T16:00:00Z", 
            "ChargeType": "AfterPay", 
            "OppositeVpcInstanceId": "vpc-bp15opprpg0rgxxxxxxxx", 
            "HasReservationData": false, 
            "CrossBorder": false, 
            "OppositeInterfaceBusinessStatus": "Normal", 
            "Spec": "Negative", 
            "OppositeRouterType": "VRouter", 
            "Role": "AcceptingSide"
          }
        ]
      }, 
      "PageNumber": 1, 
      "RequestId": "578448D7-9DCF-4703-8337-EF88DDF2C325", 
      "PageSize": 10
    }
    ---------------------------connect_router_interface---------------------------
    {
      "RequestId": "A5DBB86B-F6F5-4A53-899E-8CF4FEF510F2"
    }
    ---------------------------create_route_entry---------------------------
    {
      "RequestId": "70D896FE-986B-48EF-9734-17D6BDC8327A"
    }
    ---------------------------create_route_entry---------------------------
    {
      "RequestId": "A2233E25-4D6B-4713-A96F-E7CA745973CA"
    }
    ---------------------------delete_route_entry---------------------------
    {
      "RequestId": "464C62A4-EE65-4414-AF0A-4984AE6B8696"
    }
    --------------------------delete_route_entry---------------------------
    {
      "RequestId": "0C11A332-969B-47CA-A683-5BFFECA28B3D"
    }
    ---------------------------deactivate_router_interface---------------------------
    {
      "RequestId": "018305AD-FB9E-450A-91E8-3830634F5AC2"
    }
    ---------------------------deactivate_router_interface---------------------------
    {
      "RequestId": "89B03203-9224-4CA3-8679-E0A49029A2D2"
    }
    ---------------------------delete_router_interface---------------------------
    {
      "RequestId": "FB0424CE-D0C7-438B-A3FA-BCF24EE9CC8A"
    }
    ---------------------------delete_router_interface---------------------------
    {
      "RequestId": "8A0A0BB6-A69D-461B-A117-14AD6670DECA"
    }
    ```


