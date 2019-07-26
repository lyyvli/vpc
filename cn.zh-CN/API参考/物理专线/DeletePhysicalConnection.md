# DeletePhysicalConnection {#doc_api_Vpc_DeletePhysicalConnection .reference}

调用DeletePhysicalConnection接口删除物理专线。

**说明：** 只能删除处于**Rejected**、**Canceled**、**AllocationFailed**和**Terminated**状态的物理专线。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DeletePhysicalConnection&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeletePhysicalConnection|要执行的操作。

 取值： **DeletePhysicalConnection**。

 |
|PhysicalConnectionId|String|是|pc-119mfjzm7|物理专线的ID。

 |
|RegionId|String|是|cn-shanghai|物理专线所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个ASCII字符。

 |
|UserCidr|String|否|30.100.0.0/16|用户侧网络的网段，如需定义多个网段请使用用半角逗号字符隔开，最多支持3个网段

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|2B3670CD-670E-4540-8C13-6DE929AEDD3B|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DeletePhysicalConnection
&PhysicalConnectionId=pc-119mfjzm7
&RegionId=cn-shanghai
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeletePhysicalConnectionResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</DeletePhysicalConnectionResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidPhysicalConnectionId.NotFound|The PhysicalConnectionId provided does not exist in our records.|该物理专线不存在。|
|400|Forbidden.NotAllowedInState|The request does not allow in this state.|该状态无法执行请求。|
|400|InvalidPhysicalConnectionId.NotMatched|instance id not matched.|实例ID不匹配。|
|400|Forbidden.VBRExists|physical connection owner's vbr still exists.|物理连接的VBR仍然存在。|
|400|Forbidden.VBRExists|vbr owner's vbr still exists.|边界路由器仍然存在。|
|400|Forbidden.AssociateToVBR|The physical connection still associate to VBR.|该物理专线已经关联了边界路由器。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

