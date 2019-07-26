# RemoveIPv6TranslatorAclListEntry {#doc_api_Vpc_RemoveIPv6TranslatorAclListEntry .reference}

删除访问控制策略组中的IP条目。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=RemoveIPv6TranslatorAclListEntry&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|AclEntryId|String|是|ipv6transaclentry-bp105jrsxxxx|要删除的访问控制策略条目ID。

 |
|AclId|String|是|ipv6transacl-bp1de2xxxx|访问控制策略条目所属的访问控制策略组ID。

 |
|Action|String|是|RemoveIPv6TranslatorAclListEntry|要执行的操作。 取值：**AddIPv6TranslatorAclListEntry**。

 |
|RegionId|String|是|cn-hangzhou|访问控制策略组的地域。

 |
|ClientToken|String|否|sha123456|客户端token，用于保证请求的幂等性。 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|8B2F5262-6B57-43F2-xxxxx|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://vpc.aliyuncs.com/?Action=RemoveIPv6TranslatorAclListEntry
&AclEntryId=ipv6transaclentry-bp105jrsxxxx
&AclId=ipv6transacl-bp1de2xxxx
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<RemoveIPv6TranslatorAclListEntryResponse>
	  <RequestId>8B2F5262-6B57-43F2-xxxxx</RequestId>
</RemoveIPv6TranslatorAclListEntryResponse>
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

