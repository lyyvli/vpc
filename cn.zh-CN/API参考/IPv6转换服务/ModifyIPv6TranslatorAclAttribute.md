# ModifyIPv6TranslatorAclAttribute {#doc_api_Vpc_ModifyIPv6TranslatorAclAttribute .reference}

修改访问控制策略组的名称。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyIPv6TranslatorAclAttribute&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|AclId|String|是|ipv6transacl-bp1de2xxxx|要修改的访问控制策略组ID。

 |
|AclName|String|是|acl1|访问控制策略组名称。

 |
|Action|String|是|ModifyIPv6TranslatorAclAttribute|要执行的操作。 取值： ModifyIPv6TranslatorAclAttribute

 |
|RegionId|String|是|cn-hangzhou|IPv6转换服务实例的地域。 您可以通过调用 DescribeRegions接口获取地域ID。

 |
|ClientToken|String|否|sha223ndd2333|客户端token，用于保证请求的幂等性。 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|8B2F5262-6B57-43F2-xxxxx|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyIPv6TranslatorAclAttribute
&RegionId=cn-hangzhou
&公共请求参数

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyIPv6TranslatorAclAttributeResponse>
	  <RequestId>8B2F5262-6B57-43F2-xxxxx</RequestId>
</ModifyIPv6TranslatorAclAttributeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"8B2F5262-6B57-43F2-xxxxx"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

