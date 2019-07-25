# ModifyRouterInterfaceSpec {#doc_api_Vpc_ModifyRouterInterfaceSpec .reference}

调用ModifyRouterInterfaceSpec接口修改路由器接口的规格。

调用本接口后，路由器接口进入**Activating**状态，激活成功后进入**Active**状态。

**说明：** 无法修改处于欠费状态的路由器接口的规格。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyRouterInterfaceSpec&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyRouterInterfaceSpec|要执行的操作。

 取值： **ModifyRouterInterfaceSpec**。

 |
|RegionId|String|是|cn-hangzhou|路由器接口所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|RouterInterfaceId|String|是|ri-2zeo3xzyf38r4urzd\*\*\*\*|路由器接口的ID。

 |
|Spec|String|是|Large|路由器接口的规格。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF|请求ID。

 |
|Spec|String|Small.1|路由器接口的规格。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://vpc.aliyuncs.com/?Action=ModifyRouterInterfaceSpec
&RegionId=cn-hangzhou
&RouterInterfaceId=ri-2zeo3xzyf38r4urzd****
&Spec=Large
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyRouterInterfaceSpecResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
      <Spec>Middle.2</Spec>
</ModifyRouterInterfaceSpecResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Spec":"Middle.2",
	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidSpec.ValudNotSupported|The specified Spec is not supported.|该规格不支持该操作，请您更换规格后重试。|
|404|InvalidRouterInterfaceId.NotFound|The specified RouterInterfaceId does not exist in our record.|指定的路由器接口不存在，请您检查填写的路由器接口是否正确。|
|400|InvalidInstanceOwner.Error|The router instance owener error.|路由器不属于您的账号。|
|400|InvalidInstance.StatusError|The router instance owener error.|实例状态错误|
|400|InvalidOpposite.NotFound|The opposite not exit.|对端不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

