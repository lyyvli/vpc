# UpdateNetworkAclEntries {#doc_api_Vpc_UpdateNetworkAclEntries .reference}

调用UpdateNetworkAclEntries接口更新网络ACL规则。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=UpdateNetworkAclEntries)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateNetworkAclEntries|要执行的操作，取值： **UpdateNetworkAclEntries**。

 |
|NetworkAclId|String|是|nacl-bp1lhl0taikrxxxxxxxx|网络ACL的ID。

 |
|RegionId|String|是|cn-hangzhou|网络ACL所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|EgressAclEntries.N.Description|String|否|This is EgressAclEntries.|出方向规则的描述信息。

 |
|EgressAclEntries.N.DestinationCidrIp|String|否|10.0.0.0/24|目标地址的网络。

 |
|EgressAclEntries.N.EntryType|String|否|custom|规则类型，取值：

 -   **custom**（默认值）：自定义。
-   **system**：系统。

 |
|EgressAclEntries.N.NetworkAclEntryName|String|否|acl-2|出方向规则条目的名称。

 |
|EgressAclEntries.N.Policy|String|否|accept|授权策略，取值：

 -   **accept**：允许。
-   **drop**：拒绝。

 |
|EgressAclEntries.N.Port|String|否|-1/-1|端口范围。

 |
|EgressAclEntries.N.Protocol|String|否|all|传输层协议，取值：

 -   **icmp**
-   **gre**
-   **tcp**
-   **udp**
-   **all**：支持所有协议

 |
|IngressAclEntries.N.Description|String|否|This is IngressAclEntries.|入方向规则的描述信息。

 |
|IngressAclEntries.N.EntryType|String|否|custom|规则类型，取值：

 -   **custom**（默认值）：自定义。
-   **system**：系统。

 |
|IngressAclEntries.N.NetworkAclEntryName|String|否|acl-3|入方向规则条目的名称。

 |
|IngressAclEntries.N.Policy|String|否|accept|授权策略，取值：

 -   **accept**：允许。
-   **drop**：拒绝。

 |
|IngressAclEntries.N.Port|String|否|-1/-1|端口范围。

 |
|IngressAclEntries.N.Protocol|String|否|all|传输层协议，取值：

 -   **icmp**
-   **gre**
-   **tcp**
-   **udp**
-   **all**：支持所有协议

 |
|IngressAclEntries.N.SourceCidrIp|String|否|10.0.0.0/24|源地址网段。

 |
|UpdateEgressAclEntries|Boolean|否|false|是否更新出方向规则，取值：

 -   **true**：更新。
-   **false**（默认）：不更新。

 |
|UpdateIngressAclEntries|Boolean|否|false|是否更新入方向规则，取值：

 -   **true**：更新。
-   **false**（默认）：不更新。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|1170A5A0-E760-4331-9133-A7D38D973215|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=UpdateNetworkAclEntries
&NetworkAclId=nacl-bp1lhl0taikrxxxxxxxx
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UpdateNetworkAclEntriesResponse>
  <RequestId>1170A5A0-E760-4331-9133-A7D38D973215</RequestId>
</UpdateNetworkAclEntriesResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"1170A5A0-E760-4331-9133-A7D38D973215"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|500|InternalError|The request processing has failed due to some unknown error.|请求处理由于某些未知错误失败。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

