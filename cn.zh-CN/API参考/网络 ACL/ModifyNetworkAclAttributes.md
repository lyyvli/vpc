# ModifyNetworkAclAttributes {#doc_api_Vpc_ModifyNetworkAclAttributes .reference}

调用ModifyNetworkAclAttributes接口修改网络ACL的属性。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=ModifyNetworkAclAttributes)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyNetworkAclAttributes|要执行的操作，取值： **ModifyNetworkAclAttributes**。

 |
|NetworkAclId|String|是|acl-bp1lhl0taikrxxxxxxxx|网络ACL的ID。

 |
|RegionId|String|是|cn-hangzhou|网络ACL所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|Description|String|否|This is my NetworkAcl.|网络ACL的描述信息。

 长度为2-256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|NetworkAclName|String|否|acl-1|网络ACL的名称。

 长度为2-128个字符，必须以字母或中文开头，可包含数字，下划线（\_）和短横线（-），但不能以`http://`或`https://`开头。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|8F76C3E4-B39F-465D-B8B3-50BAF03CA833|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyNetworkAclAttributes
&NetworkAclId=acl-bp1lhl0taikrxxxxxxxx
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyNetworkAclAttributesResponse>
  <RequestId>8F76C3E4-B39F-465D-B8B3-50BAF03CA833</RequestId>
</ModifyNetworkAclAttributesResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"8F76C3E4-B39F-465D-B8B3-50BAF03CA833"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|500|InternalError|The request processing has failed due to some unknown error.|请求处理由于某些未知错误失败。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

