# DeleteIPv6Translator {#doc_api_Vpc_DeleteIPv6Translator .reference}

删除IPv6转换服务实例。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DeleteIPv6Translator&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteIPv6Translator|要执行的操作，取值：**DeleteIPv6Translator**。

 |
|Ipv6TranslatorId|String|是|ipv6trans-bp1i8ahxut1iexxxx|IPv6转换服务实例ID。

 |
|RegionId|String|是|cn-hangzhou|IPv6转换服务实例的地域ID。

 |
|ClientToken|String|否|ClientToken|客户端token用于保证请求的幂等性。要保证Client Token在不同请求间唯一，最大值不超过64个ASCII字符。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|8B2F5262-6B57-43F2-xxxxx|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DeleteIPv6Translator
&Ipv6TranslatorId=ipv6trans-bp1i8ahxut1iexxxx
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteIPv6TranslatorResponse> 
      <RequestId>1AE05898-06E5-4782-B4D0-6714DD94C4E6</RequestId> 
</DeleteIPv6TranslatorResponse>
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
|403|ForbiddenRelease|Forbidden to release a prepaid instance within validity period|不允许在合同期内释放预付费实例。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

