# CopyNetworkAclEntries {#doc_api_Vpc_CopyNetworkAclEntries .reference}

调用CopyNetworkAclEntries接口复制网络ACL规则。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CopyNetworkAclEntries)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CopyNetworkAclEntries|要执行的操作，取值： **CopyNetworkAclEntries**。

 |
|NetworkAclId|String|是|nacl-a2do9e413e0spxxxxxxxx|网络ACL的ID。

 |
|RegionId|String|是|cn-hangzhou|网络ACL所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|SourceNetworkAclId|String|是|nacl-ghuo9ehg3e0spxxxxxxxx|被复制的网络ACL的ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6608E72F-F276-440F-ABEF-419971CEC4D1|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CopyNetworkAclEntries
&NetworkAclId=nacl-a2do9e413e0spxxxxxxxx
&RegionId=cn-hangzhou
&SourceNetworkAclId=nacl-ghuo9ehg3e0spxxxxxxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CopyNetworkAclEntriesResponse>
  <RequestId>6608E72F-F276-440F-ABEF-419971CEC4D1</RequestId>
</CopyNetworkAclEntriesResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"6608E72F-F276-440F-ABEF-419971CEC4D1"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|500|InternalError|The request processing has failed due to some unknown error.|请求处理由于某些未知错误失败。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

