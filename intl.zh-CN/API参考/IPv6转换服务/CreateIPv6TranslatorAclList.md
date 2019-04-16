# CreateIPv6TranslatorAclList {#doc_api_1029226 .reference}

创建访问控制策略组。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CreateIPv6TranslatorAclList)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|AclName|String|是|test|访问控制策略组名称。

 |
|Action|String|是|CreateIPv6TranslatorAclList|要执行的操作。 取值： CreateIPv6TranslatorAclList

 |
|RegionId|String|是|cn-hangzhou|IPv6转换服务实例的地域。 您可以通过调用 DescribeRegions接口获取地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|AclId|String|ipv6transacl-bp1de2xxxx|访问控制策略组ID。

 |
|RequestId|String|8B2F5262-6B57-43F2-xxxxx|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateIPv6TranslatorAclList
&RegionId=cn-hangzhou
&公共请求参数

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateIPv6TranslatorAclListResponse>
  <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
  <AclId>vsw-25naue4gz</AclId>
</CreateIPv6TranslatorAclListResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"AclId":"ipv6transacl-bp1de2xxxx",
	"RequestId":"8B2F5262-6B57-43F2-xxxxx"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

