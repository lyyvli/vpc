# AddIPv6TranslatorAclListEntry {#doc_api_Vpc_AddIPv6TranslatorAclListEntry .reference}

在访问控制策略组中添加IP条目。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=AddIPv6TranslatorAclListEntry&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|AclEntryIp|String|是|12ab:0:0:dc30::0102|访问控制策略组条目中要添加的单个IPv6地址，或者IPv6地址段，如12ab:0:0:dc30::0102或12ab:0:0:dc30::/60。

 |
|AclId|String|是|ipv6transacl-bp1de2xxxx|IP条目的访问控制策略组ID。

 |
|Action|String|是|AddIPv6TranslatorAclListEntry|要执行的操作。 取值： **AddIPv6TranslatorAclListEntry**。

 |
|RegionId|String|是|cn-hangzhou|访问控制策略组的地域。 您可以通过调用DescribeRegions接口获取地域ID。

 |
|AclEntryComment|String|否|clientIP1|访问控制策略组条目的备注信息，长度为2-100个字符，以大小字母或中文开头，可包含数字，"\_"或"-"。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|8B2F5262-6B57-43F2-xxxxx|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://vpc.aliyuncs.com/?Action=AddIPv6TranslatorAclListEntry
&AclEntryIp=12ab:0:0:dc30::0102
&AclId=ipv6transacl-bp1de2xxxx
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateIPv6TranslatorAclListResponse>
      <AclEntryId>ipv6transaclentry-bp105jrsxxxx</AclEntryId>
	  <RequestId>8B2F5262-6B57-43F2-xxxxx</RequestId>
</CreateIPv6TranslatorAclListResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"AclEntryId":"ipv6transaclentry-bp105jrsxxxx",
	"RequestId":"8B2F5262-6B57-43F2-xxxxx"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|
|400|Resource.QuotaFull|The quota of resource is full|资源配额已达上限。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

