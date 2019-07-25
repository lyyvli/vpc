# DeleteVpc {#doc_api_Vpc_DeleteVpc .reference}

调用DeleteVpc接口删除一个专有网络（VPC）。

调用该接口删除VPC时，请注意：

-   删除VPC之前，需要先释放或移走VPC内的所有资源，包括交换机，云产品实例，路由器接口，HAVIP等。
-   只有处于Available状态的VPC才可以被删除。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DeleteVpc&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteVpc|要执行的操作，取值： **DeleteVpc**。

 |
|RegionId|String|是|cn-hangzhou|VPC所在的地域ID。

 |
|VpcId|String|是|vpc-bp1m7v25emi1h5mtc\*\*\*\*|要删除的VPC ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DeleteVpc
&VpcId=vpc-bp1m7v25emi1h5mtc****
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteVpcResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</DeleteVpcResponse>
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
|403|OperationDenied|The operation is not supported in this status.|当前状态无法执行该操作。|
|403|OperationDenied|The snapshot creation for the specified disk is not finished yet.|指定磁盘的快照创建尚未结束。|
|400|IncorrectVpcStatus|Current VPC status does not support this operation.|当前 VPC 的状态无法支持这个操作。|
|400|DependencyViolation.RouteEntry|Specified object has dependent resources|当前 VPC 还存在未删除的自定义路由规则，VPC 删除失败。|
|400|DependencyViolation.Instance|Specified object has dependent resources|该对象有关联的资源。|
|400|DependencyViolation.VSwitch|Specified object has dependent resources|当前 VPC 还存在未删除的交换机，VPC 删除失败，删除 VPC 下的交换机后再尝试删除 VPC。|
|400|DependencyViolation.SecurityGroup|Specified object has dependent resources SecurityGroup.|当前 VPC 还存在未删除的安全组，VPC 删除失败，请先删除该 VPC 下的安全组后再删除 VPC。|
|404|InvalidVpcId.NotFound|Specified VPC does not exist.|该 VPC 不存在。|
|400|DependencyViolation.RouteInterface|Specified object has dependent route interface .|指定的虚拟交换机连接了路由器接口，无法删除。|
|400|DependencyViolation.Tunnel|Specified object has dependent tunnel.|该对象有关联的隧道。|
|500|InternalError|The request processing has failed due to some unknown error.|请求处理由于某些未知错误失败。|
|400|DependencyViolation.NatGateway|Specified object has dependent resources NatGateway.|VPC 中还有 NAT 网关，不能被删除，请先删除该 VPC 中的 NAT 网关再删除 VPC。|
|400|DependencyViolation.RouterInterface|Specified object has dependent resources RouterInterface.|该对象有关联的路由器接口。|
|400|Forbidden.VpcNotFound|Specified VPC can not found.|指定的 VPC 不存在，请您检查 VPC 是否正确。|
|400|Forbbiden|Active custom route in vpc.|您需要在VPC中添加自定义路由条目。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

