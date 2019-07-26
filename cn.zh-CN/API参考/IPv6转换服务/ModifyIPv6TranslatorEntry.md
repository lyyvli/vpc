# ModifyIPv6TranslatorEntry {#doc_api_Vpc_ModifyIPv6TranslatorEntry .reference}

修改IPv6转换映射条目。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyIPv6TranslatorEntry&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyIPv6TranslatorEntry|要执行的操作。 取值： **ModifyIPv6TranslatorEntry**。

 |
|Ipv6TranslatorEntryId|String|是|ipv6trans-bp1858ysxxxxxx|IPv6转换服务映射条目ID。

 |
|RegionId|String|是|cn-hangzhou|IPv6转换服务实例的地域。 您可以通过调用 DescribeRegions接口获取地域ID。

 |
|AclId|String|否|ipv6transacl-bp1de27sou71g0lfxxxx|关联的访问控制策略组ID。

 |
|AclStatus|String|否|off|是否开启访问控制。取值：**on|off**。

 |
|AclType|String|否|white|访问控制策略类型：

 -   **white**：允许访问策略组中的IPv6地址访问后端服务。
-   **black**：禁止访问策略组中的IPv6地址访问后端服务。

 |
|AllocateIpv6Port|Integer|否|80|IPv6转换服务实例分配的IPv6地址的使用端口。

 |
|BackendIpv4Addr|String|否|47.11.xx.xxx|需要提供IPv6服务的公网IPv4地址（IPv4-only的服务器的IPv4地址）。

 |
|BackendIpv4Port|Integer|否|80|需要提供IPv6服务的公网IPv4地址的端口。

 |
|EntryBandwidth|Integer|否|10|IPv6转换映射条目的带宽峰值。取值：

 -   -1（默认值）：不限制IPv6转换映射条目的带宽峰值。
-   1-200Mbps：改映射条目的带宽值。

 **说明：** 所有IPv6转换映射条目的带宽峰值之和不能超过实例的带宽峰值。

 |
|EntryDescription|String|否|entrydescription|IPv6转换映射条目的描述信息。 长度为 2-100个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以http:// 或https://开头。

 |
|EntryName|String|否|entry1|IPv6转换映射条目的名称。 长度为 2-100个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以http:// 或https://开头。

 |
|TransProtocol|String|否|tcp|协议类型。取值：

 -   **tcp**：转发TCP协议的报文。
-   **udp**：转发UDP协议的报文。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|8B2F5262-6B57-43F2-xxxxx|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyIPv6TranslatorEntry
&RegionId=cn-hangzhou
&Ipv6TranslatorId=ipv6transentry-bp1gpgeb3umme48ygihhg
&EntryName=test
&公共请求参数

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyIPv6TranslatorEntryResponse>
        <RequestId>1AE05898-06E5-4782-B4D0-6714DD94C4E6</RequestId>
</ModifyIPv6TranslatorEntryResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"8B2F5262-6B57-43F2-xxxxx"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

