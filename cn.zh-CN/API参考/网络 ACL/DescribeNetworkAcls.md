# DescribeNetworkAcls {#doc_api_Vpc_DescribeNetworkAcls .reference}

调用DescribeNetworkAcls接口查看网络ACL列表。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeNetworkAcls)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeNetworkAcls|要执行的操作，取值：**DescribeNetworkAcls**。

 |
|RegionId|String|是|cn-hangzhou|网络ACL所属的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|NetworkAclId|String|否|nacl-bp1lhl0taikrxxxxxxxx|网络ACL的ID。

 |
|NetworkAclName|String|否|acl-1|网络ACL的名称。

 长度为2-128个字符，必须以字母或中文开头，可包含数字，下划线（\_）和短横线（-），但不能以`http://`或`https://`开头。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为1。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。

 |
|ResourceId|String|否|vsw-bp1de348lntdwxxxxxxxx|关联实例的ID。

 `ResourceType`和`ResourceId`需要同时指定才生效。

 |
|ResourceType|String|否|VSwitch|关联实例的类型。

 `ResourceType`和`ResourceId`需要同时指定才生效。

 |
|VpcId|String|否|vpc-123456|网络ACL关联的VPC的ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|NetworkAcls| | |网络ACL的详细信息。

 |
|└CreationTime|String|2019-04-25 11:44:17|网络ACL的创建时间。

 |
|└Description|String|This is my NetworkAcl.|网络ACL的描述信息。

 长度为2-256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|└EgressAclEntries| | |出方向规则信息。

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
|└IngressAclEntries| | |入方向规则信息。

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
|└NetworkAclName|String|acl-8|网络ACL的名称。

 |
|└RegionId|String|cn-hangzhou|网络ACL所属的地域。

 |
|└Resources| | |关联的资源。

 |
|└ResourceId|String|vsw-bp1de348lntdwxxxxxx|关联资源的ID。

 |
|└ResourceType|String|VSwitch|关联资源的类型。

 |
|└Status|String|Available|状态。

 |
|└VpcId|String|vpc-a2d33rfpl72k5xxxxxxxx|关联的VPC的ID。

 |
|PageNumber|String|1|当前页码。

 |
|PageSize|String|10|当前分页包含的条目数。

 |
|RequestId|String|F7DDDC17-FA06-4AC2-8F35-59D2470FCFC1|请求ID。

 |
|TotalCount|String|2|列表条条目数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeNetworkAcls
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeNetworkAclsResponse>
  <NetworkAcls>
    <NetworkAcl>
      <CreationTime>2019-04-25 11:44:17</CreationTime>
      <EgressAclEntries>
        <EgressAclEntry>
          <DestinationCidrIp>10.0.0.0/24</DestinationCidrIp>
          <NetworkAclEntryId>nae-a2d8hqm2ueaeuxxxxxxxx</NetworkAclEntryId>
          <Policy>accept</Policy>
          <Port>-1/-1</Port>
          <Protocol>all</Protocol>
        </EgressAclEntry>
      </EgressAclEntries>
      <IngressAclEntries>
        <IngressAclEntry>
          <NetworkAclEntryId>nae-a2dv360rgpczdxxxxxxxx</NetworkAclEntryId>
          <Policy>accept</Policy>
          <Port>-1/-1</Port>
          <Protocol>all</Protocol>
          <SourceCidrIp>10.0.0.0/24</SourceCidrIp>
        </IngressAclEntry>
      </IngressAclEntries>
      <NetworkAclId>nacl-a2d504869xhaexxxxxxxx</NetworkAclId>
      <RegionId>cn-hangzhou</RegionId>
      <Resources>
        <Resource/>
      </Resources>
      <Status>Available</Status>
      <VpcId>vpc-a2d33rfpl72k5xxxxxxxx</VpcId>
    </NetworkAcl>
    <NetworkAcl>
      <CreationTime>2019-04-25 11:44:14</CreationTime>
      <EgressAclEntries>
        <EgressAclEntry>
          <DestinationCidrIp>10.0.0.0/24</DestinationCidrIp>
          <NetworkAclEntryId>nae-a2d05l0auxh7ixxxxxxxx</NetworkAclEntryId>
          <Policy>accept</Policy>
          <Port>-1/-1</Port>
          <Protocol>all</Protocol>
        </EgressAclEntry>
      </EgressAclEntries>
      <IngressAclEntries>
        <IngressAclEntry>
          <NetworkAclEntryId>nae-a2dy2eq7mudblxxxxxxxx</NetworkAclEntryId>
          <Policy>accept</Policy>
          <Port>-1/-1</Port>
          <Protocol>all</Protocol>
          <SourceCidrIp>10.0.0.0/24</SourceCidrIp>
        </IngressAclEntry>
      </IngressAclEntries>
      <NetworkAclId>nacl-a2detw6o77x7lxxxxxxxx</NetworkAclId>
      <RegionId>cn-hangzhou</RegionId>
      <Resources>
        <Resource/>
      </Resources>
      <Status>Available</Status>
      <VpcId>vpc-a2d33rfpl72k5xxxxxxxx</VpcId>
    </NetworkAcl>
  </NetworkAcls>
  <PageNumber>1</PageNumber>
  <PageSize>10</PageSize>
  <RequestId>F7DDDC17-FA06-4AC2-8F35-59D2470FCFC1</RequestId>
  <TotalCount>2</TotalCount>
</DescribeNetworkAclsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":2,
	"PageSize":10,
	"RequestId":"F7DDDC17-FA06-4AC2-8F35-59D2470FCFC1",
	"NetworkAcls":{
		"NetworkAcl":[
			{
				"CreationTime":"2019-04-25 11:44:17",
				"EgressAclEntries":{
					"EgressAclEntry":[
						{
							"Port":"-1/-1",
							"Policy":"accept",
							"NetworkAclEntryId":"nae-a2d8hqm2ueaeuxxxxxxxx",
							"Protocol":"all",
							"DestinationCidrIp":"10.0.0.0/24"
						}
					]
				},
				"Status":"Available",
				"RegionId":"cn-hangzhou",
				"IngressAclEntries":{
					"IngressAclEntry":[
						{
							"SourceCidrIp":"10.0.0.0/24",
							"Port":"-1/-1",
							"Policy":"accept",
							"NetworkAclEntryId":"nae-a2dv360rgpczdxxxxxxxx",
							"Protocol":"all"
						}
					]
				},
				"NetworkAclId":"nacl-a2d504869xhaexxxxxxxx",
				"VpcId":"vpc-a2d33rfpl72k5xxxxxxxx",
				"Resources":{
					"Resource":[]
				}
			},
			{
				"CreationTime":"2019-04-25 11:44:14",
				"EgressAclEntries":{
					"EgressAclEntry":[
						{
							"Port":"-1/-1",
							"Policy":"accept",
							"NetworkAclEntryId":"nae-a2d05l0auxh7ixxxxxxxx",
							"Protocol":"all",
							"DestinationCidrIp":"10.0.0.0/24"
						}
					]
				},
				"Status":"Available",
				"RegionId":"cn-hangzhou",
				"IngressAclEntries":{
					"IngressAclEntry":[
						{
							"SourceCidrIp":"10.0.0.0/24",
							"Port":"-1/-1",
							"Policy":"accept",
							"NetworkAclEntryId":"nae-a2dy2eq7mudblxxxxxxxx",
							"Protocol":"all"
						}
					]
				},
				"NetworkAclId":"nacl-a2detw6o77x7lxxxxxxxx",
				"VpcId":"vpc-a2d33rfpl72k5xxxxxxxx",
				"Resources":{
					"Resource":[]
				}
			}
		]
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|500|InternalError|The request processing has failed due to some unknown error.|请求处理由于某些未知错误失败。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

