# ConnectRouterInterface {#doc_api_Vpc_ConnectRouterInterface .reference}

调用ConnectRouterInterface接口由发起端路由器接口向接收端发起连接。

调用本接口后路由器接口进入Connecting状态，连接完成后进入Active状态。

调用该接口创建VPC时，请注意：

-   只能由状态为Idle的发起端路由器接口向接收端发起连接。
-   任意两个路由器之间，最多只能存在一对相互连接的路由器接口。
-   如果账号下存在处于欠费状态的路由器接口，无法进行发起连接。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ConnectRouterInterface&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ConnectRouterInterface|要执行的操作。

 取值： **ConnectRouterInterface**。

 |
|RegionId|String|是|cn-hangzhou|路由器接口所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|RouterInterfaceId|String|是|ri-2zeo3xzyf38r4urzd\*\*\*\*|发起端路由器接口的ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|DE77A7F3-3B74-41C0-A5BC-CAFD188C28B6|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://vpc.aliyuncs.com/?Action=ConnectRouterInterface
&RegionId= cn-hangzhou
&RouterInterfaceId=ri-2zeo3xzyf38r4urz****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ConnectRouterInterfaceResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</ConnectRouterInterfaceResponse>
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
|404|InvalidRouterInterfaceId.NotFound|The specified RouterInterfaceId does not exist in our record.|指定的路由器接口不存在，请您检查填写的路由器接口是否正确。|
|400|IncorrectRole.NotInitiatingSide|The specified RouterInterface is not InitiatingSide.|该路由器接口不是发起端，请选择发起端的路由器接口进行发起连接。|
|400|IncorrectOppositeInterfaceInfo|Cannot connect on the same router|不允许连接相同的路由器。|
|400|Forbidden.OnlyOneConnection|The Specified routers have a connection already|该路由器已有路由器接口连接。|
|400|Forbidden.OnlyOneConnection|Cannot connect concurrently between same routers|不能在同一路由器上发起连接。|
|400|Forbidden.BillsOutstanding|You cannot use this action because you have bills outstanding.|无法执行该操作，您有未结算的账单。|
|404|CROSS\_BID.FORBIDDEN|Connect RouterInterface across bid is illegal|跨BID连接非法。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

