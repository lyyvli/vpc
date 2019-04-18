# 创建和删除VPC/VSwitch {#task_gkw_xf5_jhb .task}

本文介绍如何使用Python SDK创建和删除VPC/VSwitch。

在华北3张家口地域创建一个VPC，并在该VPC下创建一个VSwitch。VPC和VSwitch创建成功后，删除VPC和VSwitch。

1.  在下载的SDK目录中，打开$aliyun-openapi-python-sdk-examples\\sdk\_examples\\sdk\_lib文件夹。
2.  使用编辑器打开consts.py文件，配置用户鉴权参数ACS\_CLIENT。
3.  在下载的SDK目录中，打开$aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\vpc文件夹。
4.  使用编辑器打开vpc\_quick\_start.py文件，根据实际情况配置相关参数，保存退出。 

    ```
    #encoding=utf-8
    import sys
    import json
    
    from aliyunsdkcore.acs_exception.exceptions import ServerException, ClientException
    from aliyunsdkvpc.request.v20160428 import CreateVpcRequest
    from aliyunsdkvpc.request.v20160428 import CreateVSwitchRequest
    from aliyunsdkvpc.request.v20160428 import DeleteVSwitchRequest
    from aliyunsdkvpc.request.v20160428 import DeleteVpcRequest
    from aliyunsdkvpc.request.v20160428 import DescribeVSwitchAttributesRequest
    from aliyunsdkvpc.request.v20160428 import DescribeVpcAttributeRequest
    from sdk_lib.exception import ExceptionHandler
    from sdk_lib.check_status import CheckStatus
    from sdk_lib.consts import *
    from sdk_lib.common_util import CommonUtil
    
    class VpcQuickStart(object):
        def __init__(self, client):
            self.client = client
    
        def create_vpc(self):
            """
            create_vpc：创建VPC
            官网API参考链接: https://help.aliyun.com/document_detail/35737.html
            """
            try:
                request = CreateVpcRequest.CreateVpcRequest()
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # 判断VPC状态是否可用
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_vpc_status,
                                            AVAILABLE, response_json['VpcId']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def delete_vpc(self, params):
            """
            delete_vpc: 删除VPC
            官网API参考链接: https://help.aliyun.com/document_detail/35738.html
            """
            try:
                request = DeleteVpcRequest.DeleteVpcRequest()
                # 要删除的VPC的ID
                request.set_VpcId(params['vpc_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_vpc_attribute(self, vpc_id):
            """
            describe_vpc_attribute: 查询指定地域已创建的vpc信息
            官网API参考: https://help.aliyun.com/document_detail/94565.html
            """
            try:
                request = DescribeVpcAttributeRequest.DescribeVpcAttributeRequest()
                # 要查询的VPC ID
                request.set_VpcId(vpc_id)
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_vpc_status(self, vpc_id):
            """
            describe_vpc_status: 查询指定地域已创建的vpc的状态
            官网API参考: https://help.aliyun.com/document_detail/94565.html
            """
            response = self.describe_vpc_attribute(vpc_id)
            return response["Status"]
    
        def create_vswitch(self, params):
            """
            create_vswitch: 创建vswitch实例
            官网API参考: https://help.aliyun.com/document_detail/35745.html
            """
            try:
                request = CreateVSwitchRequest.CreateVSwitchRequest()
                # 交换机所属区的ID，您可以通过调用DescribeZones接口获取地域ID
                request.set_ZoneId(params['zone_id'])
                # 交换机所属的VPC ID
                request.set_VpcId(params['vpc_id'])
                # 交换机的网段
                request.set_CidrBlock(params['cidr_block'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # 判断VSwitch状态是否可用
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME,
                                            self.describe_vswitch_status,
                                            AVAILABLE, response_json['VSwitchId']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_vswitch_attribute(self, vswitch_id):
            """
            describe_vswitch_attribute: 查询指定地域已创建的vswitch的状态
            官网API参考: https://help.aliyun.com/document_detail/36010.html
            """
            try:
                request = DescribeVSwitchAttributesRequest.DescribeVSwitchAttributesRequest()
                request.set_VSwitchId(vswitch_id)
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
        def describe_vswitch_status(self, vswitch_id):
            """
            describe_vswitch_status: 查询指定地域已创建的vswitch的状态
            官网API参考: https://help.aliyun.com/document_detail/36010.html
            """
            response = self.describe_vswitch_attribute(vswitch_id)
            return response["Status"]
    
        def delete_vswitch(self, params):
            """
            delete_vswitch: 删除vswitch实例
            官网API参考: https://help.aliyun.com/document_detail/35746.html
            """
            try:
                request = DeleteVSwitchRequest.DeleteVSwitchRequest()
                # 要删除的交换机的ID
                request.set_VSwitchId(params['vswitch_id'])
                response = self.client.do_action_with_exception(request)
                response_json = json.loads(response)
                # 判断VSwitch是否被删除成功
                if CheckStatus.check_status(TIME_DEFAULT_OUT, DEFAULT_TIME * 5,
                                            self.describe_vswitch_status,
                                            '', params['vswitch_id']):
                    return response_json
            except ServerException as e:
                ExceptionHandler.server_exception(e)
            except ClientException as e:
                ExceptionHandler.client_exception(e)
    
    
    def main():
        client = ACS_CLIENT
    
        vpc_quick_start = VpcQuickStart(client)
    
        params = {}
        params['zone_id'] = "cn-zhangjiakou-b"
        params['cidr_block'] = "172.16.0.0/16"
    
        # 创建vpc
        vpc_json = vpc_quick_start.create_vpc()
        CommonUtil.log("create_vpc", vpc_json)
    
        # 创建vswitch
        params['vpc_id'] = vpc_json['VpcId']
        vswitch_json = vpc_quick_start.create_vswitch(params)
        CommonUtil.log("create_vswitch", vswitch_json)
    
        # 删除vswitch
        params['vswitch_id'] = vswitch_json['VSwitchId']
        vswitch_json = vpc_quick_start.delete_vswitch(params)
        CommonUtil.log("delete_vswitch", vswitch_json)
    
        # 删除vpc
        vpc_json = vpc_quick_start.delete_vpc(params)
        CommonUtil.log("delete_vpc", vpc_json)
    
    
    if __name__ == "__main__":
        sys.exit(main())
    ```

5.  进入vpc\_quick\_start.py所在的目录，执行如下命令，运行创建和删除VPC/VSwitch示例。 

    ```
    python vpc_quick_start.py
    ```

    系统显示类似如下：

    ```
    ---------------------------create_vpc---------------------------
    {
      "ResourceGroupId": "rg-acfmxazxxxxxxxx",
      "RouteTableId": "vtb-8vbf9ud7xrcn9xxxxxxxx",
      "VRouterId": "vrt-8vb1qjnxcm03nxxxxxxxx",
      "VpcId": "vpc-8vb67v4ozd8wfxxxxxxxx",
      "RequestId": "5052F988-75CC-46AD-A1A6-0E9E445BD0D5"
    }
    
    ---------------------------create_vswitch---------------------------
    {
      "VSwitchId": "vsw-8vbqn2at0kljjxxxxxxxx",
      "RequestId": "0BA1ABF7-21CF-4460-9A86-0BB783886E58"
    }
    
    ---------------------------delete_vswitch---------------------------
    {
      "RequestId": "D691F04B-A6EE-49A7-A434-4A45DD3AA0B8"
    }
    
    ---------------------------delete_vpc---------------------------
    {
      "RequestId": "4570F816-AB8D-45EA-8913-6AE787C1632C"
    }
    ```


