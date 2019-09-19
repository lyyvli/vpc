# ModifyHaVipAttribute {#doc_api_Vpc_ModifyHaVipAttribute .reference}

调用ModifyHaVipAttribute接口修改HaVip实例的描述。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyHaVipAttribute&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyHaVipAttribute|要执行的操作。 取值：

 **ModifyHaVipAttribute**。

 |
|HaVipId|String|是|havip-2zeo05qre24nhrqp\*\*\*\*|要修改的的HaVip实例ID。

 |
|RegionId|String|是|cn-shanghai|HaVip实例所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e0\*\*\*\*|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|Description|String|否|This is my HaVip.|添加HaVip的描述。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|C44F62BE-9CE7-4277-B117-69243F3988BF|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyHaVipAttribute 
&HaVipId=havip-2zeo05qre24nhrqp****
&RegionId=cn-shanghai 
&公共请求参数

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyHaVipAttributeResponse> 
  <RequestId>C44F62BE-9CE7-4277-B117-69243F3988BF</RequestId> 
</ModifyHaVipAttributeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"C44F62BE-9CE7-4277-B117-69243F3988BF"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidHaVipId.NotFound|The specified HaVip does not exist in the specified region.|指定的 HaVip 不在指定的地域中，请您检查选择的地域是否正确。|
|400|IncorrectStatus|HaVip can be deleted only when it's status is Available or InUse.|删除HAVIP失败，HAVIP的状态不支持。|
|400|InvalidDescription.Malformed|The specified Description is wrongly formed.|指定的资源描述格式不合法。长度为2-256个字符，不能以 http:// 和 https:// 开头。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

