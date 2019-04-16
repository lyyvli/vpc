# DescribeIPv6TranslatorEntries {#doc_api_1027221 .reference}

查询IPv6转换映射条目。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeIPv6TranslatorEntries)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeIPv6TranslatorEntries|要执行的操作。 取值： **DescribeIPv6TranslatorEntries**。

 |
|Ipv6TranslatorId|String|是|ipv6trans-bp1858ysxxxxxx|IPv6转换服务实例的ID。

 |
|RegionId|String|是|cn-hangzhou|IPv6转换服务实例的地域。 您可以通过调用**DescribeRegions**接口获取地域ID。

 |
|AclId|String|否|ipv6transacl-bp1de2xxxx|访问控制策略组ID。

 |
|AclStatus|String|否|off|是否开启访问控制。取值：**on|off**。

 |
|AclType|String|否|white|访问控制策略类型。取值：

 -   **white**：允许访问策略组中的IPv6地址访问后端服务。
-   **black**：禁止访问策略组中的IPv6地址访问后端服务。

 |
|AllocateIpv6Addr|String|否|2400:3200:1600::xx|IPv6转换服务实例分配的IPv6地址。

 |
|AllocateIpv6Port|Integer|否|80|IPv6转换服务实例分配的IPv6地址使用的端口。

 |
|BackendIpv4Addr|String|否|47.99.xx.xx|需要提供IPv6服务的公网IPv4地址

 |
|BackendIpv4Port|Integer|否|80|需要提供IPv6服务的公网IPv4地址使用的端口。

 |
|ClientToken|String|否|sha1111|客户端token，用于保证请求的幂等性。 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|EntryName|String|否|entryname|Pv6转换映射条目的名称。

 |
|Ipv6TranslatorEntryId|String|否|ipv6transentry-bp1g8bhrdexxxxx|要查询的IPv6转换映射条目ID。

 **说明：** 如果**Ipv6TranslatorId**参数和**Ipv6TranslatorEntryId**参数的值都为null，则返回所有IPv6转换映射条目信息。如果仅是**Ipv6TranslatorEntryId**参数的值为null，则返回当前IPv6转换服务实例下的所有IPv6转换映射条目信息。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为1。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。

 |
|TransProtocol|String|否|tcp|转发数据的协议类型。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Ipv6TranslatorEntries| | |查询到的IPv6转换映射条目。

 |
|└AclId|String|ipv6transacl-bp1de2xxxx|关联的访问控制策略组ID。

 |
|└AclStatus|String|on|是否开启了访问控制。

 |
|└AclType|String|white|访问控制策略类型。

 -   **white**：允许访问策略组中的IPv6地址访问后端服务。
-   **black**：禁止访问策略组中的IPv6地址访问后端服务。

 |
|└AllocateIpv6Addr|String|2400:3200:1600::xxx|分配的IPv6转换服务实例的IPv6地址。

 |
|└AllocateIpv6Port|Integer|80|IPv6转换服务实例分配的IPv6地址的使用端口。

 |
|└BackendIpv4Addr|String|47.99.xx.xx|后端IPv4服务器的公网IP地址。

 |
|└BackendIpv4Port|String|80|需要提供IPv6访问的IPv4服务器所使用的公网IPv4端口。

 |
|└EntryBandwidth|String|1|IPv6转换映射条目的带宽。

 |
|└EntryDescription|String|description|IPv6转换映射条目的描述。

 |
|└EntryName|String|name|IPv6转换映射条目的名称。

 |
|└EntryStatus|String|active|IPv6转换映射条目的状态。

 |
|└Ipv6TranslatorEntryId|String|ipv6transentry-bp1g8bhrdexxxxx|IPv6转换映射条目ID。

 |
|└Ipv6TranslatorId|String|ipv6trans-bp1858ysxxxxxx|IPv6转换映射条目所属的IPv6转换服务实例ID。

 |
|└RegionId|String|cn-hangzhou|IPv6转换服务实例的地域。

 |
|└TransProtocol|String|tcp|协议类型。

 |
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|10|每页包含多少条目。

 |
|RequestId|String|3109D437-5D6D-4A28-B5F5-EF936DExxxx|请求ID。

 |
|TotalCount|Integer|1|列表条条目数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeIPv6TranslatorEntries
&RegionId=cn-hangzhou
&Ipv6TranslatorId=ipv6transentry-bp1gpgeb3umme48ygihhg
&公共请求参数

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeIPv6TranslatorEntriesResponse>
  <Ipv6TranslatorEntries>
    <AllocateIpv6Addr>2400:3200:1600::xxxx</AllocateIpv6Addr>
    <AllocateIpv6Port>2345</AllocateIpv6Port>
    <BackendIpv4Addr>222.118.xx.xx</BackendIpv4Addr>
    <BackendIpv4Port>1234</BackendIpv4Port>
    <EntryBandwidth>-1</EntryBandwidth>
    <EntryStatus>active</EntryStatus>
    <Ipv6TranslatorEntryId>ipv6transentry-bp1gpgeb3umme48ygixxx</Ipv6TranslatorEntryId>
    <Ipv6TranslatorId>ipv6trans-bp1i8ahxut1iedrqqxx</Ipv6TranslatorId>
    <RegionId>cn-hangzhou</RegionId>
    <TransProtocol>tcp</TransProtocol>
  </Ipv6TranslatorEntries>
  <PageNumber>1</PageNumber>
  <PageSize>10</PageSize>
  <RequestId>9C57C407-3179-4B85-80D8-F0BE74262EF1</RequestId>
  <TotalCount>1</TotalCount>
</DescribeIPv6TranslatorEntriesResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":1,
	"PageSize":10,
	"RequestId":"9C57C407-3179-4B85-80D8-F0BE74262EF1",
	"Ipv6TranslatorEntries":[
		{
			"EntryStatus":"active",
			"BackendIpv4Port":"1234",
			"AllocateIpv6Port":2345,
			"RegionId":"cn-hangzhou",
			"Ipv6TranslatorId":"ipv6trans-bp1i8ahxut1iedrxxx",
			"EntryBandwidth":"-1",
			"TransProtocol":"tcp",
			"Ipv6TranslatorEntryId":"ipv6transentry-bp1gpgxxg",
			"BackendIpv4Addr":"222.118.xxx.xxx",
			"AllocateIpv6Addr":"2400:3200:1600::xxx"
		}
	]
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

