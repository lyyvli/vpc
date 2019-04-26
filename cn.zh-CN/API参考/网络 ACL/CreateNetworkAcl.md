# CreateNetworkAcl {#doc_api_Vpc_CreateNetworkAcl .reference}

调用CreateNetworkAcl接口创建网络ACL。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CreateNetworkAcl)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateNetworkAcl|要执行的操作，取值： **CreateNetworkAcl**。

 |
|RegionId|String|是|cn-hangzhou|网络ACL所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VpcId|String|是|vpc-123456|网络ACL关联的VPC的ID。

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
|NetworkAclAttribute| | |网络ACL的属性。

 |
|└CreationTime|String|2019-04-25 11:33:27|创建的时间。

 |
|└Description|String|This is my NetworkAcl.|网络ACL的描述信息。

 |
|└EgressAclEntries| | |出方向规则。

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
|└IngressAclEntries| | |入方向规则。

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
|└SourceCidrIp|String|10.0.0.0/24|源地址段。

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
|NetworkAclId|String|nacl-a2do9e413e0spxxxxxxxx|网络ACL的ID。

 |
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateNetworkAcl
&RegionId=cn-hangzhou
&VpcId=vpc-123456
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateNetworkAclResponse>
  <NetworkAclAttribute>
    <CreationTime>2019-04-25 11:33:27</CreationTime>
    <EgressAclEntries>
      <EgressAclEntry>
        <DestinationCidrIp>0.0.0.0/0</DestinationCidrIp>
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
        <SourceCidrIp>0.0.0.0/0</SourceCidrIp>
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
  <NetworkAclId>nacl-a2do9e413e0spxxxxxxxx</NetworkAclId>
  <RequestId>AEAC0891-1E52-4A46-A29C-175FB6356FE8</RequestId>
</CreateNetworkAclResponse>

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
					"DestinationCidrIp":"0.0.0.0/0"
				}
			]
		},
		"CreationTime":"2019-04-25 11:33:27",
		"Status":"Available",
		"RegionId":"cn-hangzhou",
		"IngressAclEntries":{
			"IngressAclEntry":[
				{
					"SourceCidrIp":"0.0.0.0/0",
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
	"RequestId":"AEAC0891-1E52-4A46-A29C-175FB6356FE8",
	"NetworkAclId":"nacl-a2do9e413e0spxxxxxxxx"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|500|InternalError|The request processing has failed due to some unknown error.|请求处理由于某些未知错误失败。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

