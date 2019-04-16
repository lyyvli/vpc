# DescribeIPv6TranslatorAclListAttributes {#doc_api_1027214 .reference}

询访问控制策略组的详细信息，包括访问控制策略组中的IP和关联的IPv6转换映射条目的具体信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeIPv6TranslatorAclListAttributes)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|AclId|String|是|ipv6transacl-bp1de2xxxx|访问控制策略组ID。

 |
|Action|String|是|DescribeIPv6TranslatorAclListAttributes|要执行的操作。 取值： **DescribeIPv6TranslatorAclListAttribute**。

 |
|RegionId|String|是|cn-hangzhou|访问控制策略组的地域。 您可以通过调用**DescribeRegions**接口获取地域ID。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为1。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|AclEntries| | |访问控制策略组列表。

 |
|└AclEntryComment|String|client IP|访问控制策略组条目的备注信息。

 |
|└AclEntryId|String|ipv6transaclentry-bp105jrsxxxx|访问控制策略组条目的ID。

 |
|└AclEntryIp|String|12ab:0:0:dc30::0102/128|访问控制策略组条目。

 |
|AclId|String|ipv6transacl-bp1de2xxxx|访问控制策略组ID。

 |
|AclName|String|acl1|访问控制策略组名称。

 |
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|10|页码条目数。

 |
|RequestId|String|8B2F5262-6B57-43F2-xxxxx|请求ID。

 |
|TotalCount|Integer|1|查询到的条目总数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeIPv6TranslatorAclLists
&RegionId=cn-hangzhou
&公共请求参数

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeIPv6TranslatorAclListAttributesResponse>
  <AclEntries>
    <AclEntry>
      <AclEntryId>ipv6transaclentry-bp105jrsk5sc9ia30cwon</AclEntryId>
      <AclEntryIp>12ab:0:0:dc30::0102/128</AclEntryIp>
    </AclEntry>
  </AclEntries>
  <TotalCount>1</TotalCount>
  <PageSize>10</PageSize>
  <RequestId>0C8935C6-F9E9-438A-A9EE-6B017C6EAA00</RequestId>
  <PageNumber>1</PageNumber>
  <AclId>ipv6transacl-bp1de27sou71g0lfqf0gx</AclId>
  <AclName>whitelist</AclName>
</DescribeIPv6TranslatorAclListAttributesResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":1,
	"AclId":"ipv6transacl-bp1dxxxxxxx",
	"PageSize":10,
	"AclName":"acl1",
	"RequestId":"0C8935C6-F9E9-438A-A9EE-6B01xxxxx0",
	"AclEntries":{
		"AclEntry":[
			{
				"AclEntryId":"ipv6transaclentry-bp105jrskxxx",
				"AclEntryIp":"12ab:0:0:dc30::0102/128"
			}
		]
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

