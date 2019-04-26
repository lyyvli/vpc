# DescribeNetworkAclAttributes {#doc_api_Vpc_DescribeNetworkAclAttributes .reference}

调用DescribeNetworkAclAttributes接口查询网络ACL的详细信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeNetworkAclAttributes)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeNetworkAclAttributes|要执行的操作，取值： **DescribeNetworkAclAttributes**。

 |
|NetworkAclId|String|是|nacl-a2do9e413e0spxxxxxxxx|网络ACL的ID。

 |
|RegionId|String|是|cn-hangzhou|网络ACL所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|NetworkAclAttribute| | |网络ACL的详细信息。

 |
|└CreationTime|String|2019-04-25 11:33:27|创建的时间。

 |
|└Description|String|This is my NetworkAcl.|网络ACL的描述信息。

 |
|└EgressAclEntries| | |网络ACL出方向规则信息。

 |
|└Description|String|This is EgressAclEntries.|出方向规则的描述信息。

 |
|└DestinationCidrIp|String|10.0.0.0/24|目的地址段。

 |
|└EntryType|String|custom|规则类型，取值：

 -   **custom**：自定义。
-   **system**：系统。

 |
|└NetworkAclEntryId|String|nae-a2d447uw4tillxxxxxxxx|出方向规则条目的ID。

 |
|└NetworkAclEntryName|String|acl-2|出方向规则条目的名称。

 |
|└Policy|String|accept|授权策略，取值：

 -   **accept**：允许。
-   **drop**：拒绝。

 |
|└Port|String|-1/-1|端口范围。

 |
|└Protocol|String|all|传输层协议，取值：

 -   **icmp**
-   **gre**
-   **tcp**
-   **udp**
-   **all**：支持所有协议

 |
|└IngressAclEntries| | |网络ACL入方向规则信息。

 |
|└Description|String|This is IngressAclEntries.|入方向规则的描述信息。

 |
|└EntryType|String|custom|规则类型，取值：

 -   **custom**：自定义。
-   **system**：系统。

 |
|└NetworkAclEntryId|String|nae-a2dk86arlydmexxxxxxxx|入方向规则条目的ID。

 |
|└NetworkAclEntryName|String|acl-3|入方向规则条目的名称。

 |
|└Policy|String|accept|授权策略，取值：

 -   **accept**：允许。
-   **drop**：拒绝。

 |
|└Port|String|-1/-1|端口范围。

 |
|└Protocol|String|all|传输层协议，取值：

 -   **icmp**
-   **gre**
-   **tcp**
-   **udp**
-   **all**：支持所有协议

 |
|└SourceCidrIp|String|10.0.0.0/24|源地址的网段。

 |
|└NetworkAclId|String|nacl-a2do9e413e0spxxxxxxxx|网络ACL的ID。

 |
|└NetworkAclName|String|acl-1|网络ACL的名称。

 |
|└RegionId|String|cn-hangzhou|网络ACL所属的地域。

 |
|└Resources| | |关联的资源。

 |
|└ResourceId|String|vsw-bp1de348lntdwxxxxxxxx|关联资源的实例ID。

 |
|└ResourceType|String|VSwitch|关联资源的类型。

 |
|└VpcId|String|vpc-a2d33rfpl72k5xxxxxxxx|网络ACL关联的VPC的ID。

 |
|RequestId|String|F5905F9C-0161-4E72-9CB1-1F3F3CF6268A|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeNetworkAclAttributes
&NetworkAclId=nacl-a2do9e413e0spxxxxxxxx
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeNetworkAclAttributesResponse>
  <NetworkAclAttribute>
    <CreationTime>2019-04-25 11:33:27</CreationTime>
    <EgressAclEntries>
      <EgressAclEntry>
        <DestinationCidrIp>10.0.0.0/24</DestinationCidrIp>
        <NetworkAclEntryId>nae-a2d447uw4tillxxxxxxxx</NetworkAclEntryId>
        <Policy>accept</Policy>
        <Port>-1/-1</Port>
        <Protocol>all</Protocol>
      </EgressAclEntry>
    </EgressAclEntries>
    <IngressAclEntries>
      <IngressAclEntry>
        <NetworkAclEntryId>nae-a2dk86arlydmexxxxxxxx</NetworkAclEntryId>
        <Policy>accept</Policy>
        <Port>-1/-1</Port>
        <Protocol>all</Protocol>
        <SourceCidrIp>10.0.0.0/24</SourceCidrIp>
      </IngressAclEntry>
    </IngressAclEntries>
    <NetworkAclId>nacl-a2do9e413e0spxxxxxxxx</NetworkAclId>
    <RegionId>cn-hangzhou</RegionId>
    <Resources>
      <Resource/>
    </Resources>
    <Status>Available</Status>
    <VpcId>vpc-a2d33rfpl72k5xxxxxxxx</VpcId>
  </NetworkAclAttribute>
  <RequestId>F5905F9C-0161-4E72-9CB1-1F3F3CF6268A</RequestId>
</DescribeNetworkAclAttributesResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"NetworkAclAttribute":{
		"EgressAclEntries":{
			"EgressAclEntry":[
				{
					"Port":"-1/-1",
					"Policy":"accept",
					"NetworkAclEntryId":"nae-a2d447uw4tillxxxxxxxx",
					"Protocol":"all",
					"DestinationCidrIp":"10.0.0.0/24"
				}
			]
		},
		"CreationTime":"2019-04-25 11:33:27",
		"Status":"Available",
		"RegionId":"cn-hangzhou",
		"IngressAclEntries":{
			"IngressAclEntry":[
				{
					"SourceCidrIp":"10.0.0.0/24",
					"Port":"-1/-1",
					"Policy":"accept",
					"NetworkAclEntryId":"nae-a2dk86arlydmexxxxxxxx",
					"Protocol":"all"
				}
			]
		},
		"VpcId":"vpc-a2d33rfpl72k5xxxxxxxx",
		"NetworkAclId":"nacl-a2do9e413e0spxxxxxxxx",
		"Resources":{
			"Resource":[]
		}
	},
	"RequestId":"F5905F9C-0161-4E72-9CB1-1F3F3CF6268A"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|500|InternalError|The request processing has failed due to some unknown error.|请求处理由于某些未知错误失败。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

