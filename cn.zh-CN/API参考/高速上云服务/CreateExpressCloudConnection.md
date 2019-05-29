# CreateExpressCloudConnection {#doc_api_Vpc_CreateExpressCloudConnection .reference}

调用CreateExpressCloudConnection申请高速上云服务。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CreateExpressCloudConnection)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateExpressCloudConnection|要执行的操作。

 取值：**CreateExpressCloudConnection**

 |
|Bandwidth|Integer|是|2|高速上云连接的带宽， 单位Mbps。

 取值：**2|4|6|8|10|20|50|100|200|500|1000|10000|40000**

 |
|PeerCity|String|是|杭州|所在城市。

 |
|PeerLocation|String|是|XX区XX大厦XX栋5楼|本地数据中心的地理位置。

 需要精确到楼层。

 |
|RegionId|String|是|cn-hangzhou|地域ID。

 |
|ContactMail|String|否|XX@example.com|申请高速上云连接的联系人邮件。

 |
|ContactTel|String|否|152XXXXXXXX|申请高速上云服务的联系人电话。

 |
|Description|String|否|高速上云服务|高速上云服务的描述信息。

 长度为 2-256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|IDCardNo|String|否|32\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*|申请高速上云服务的联系人身份证号。

 |
|IdcSP|String|否|CU|IDC的网络服务商。

 |
|Name|String|否|doctest|高速上云服务的实例名称。

 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://` 或`https://`开头。

 |
|PortType|String|否|100Base-T|物理专线接入端口类型，取值：

 -   100Base-T：百兆电口
-   1000Base-T（默认值）：千兆电口
-   1000Base-LX：千兆单模光口（10千米）
-   10GBase-T：万兆电口
-   10GBase-LR：万兆单模光口（10千米）

 |
|RedundantEccId|String|否|ecc-xxxxxx|冗余高速上云服务专线实例ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|EccId|String|ecc-xxxxxx|新建的高速上云服务实例ID。

 |
|RequestId|String|C004F022-1CC2-4958-9937-675513A2CD7E|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=CreateExpressCloudConnection
&Bandwidth=2
&PeerCity=杭州
&PeerLocation=XX区XX大厦XX栋5楼
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateExpressCloudConnection>
  <EccId>ecc-bp1t9osmuln1vxfpt6gy8</EccId>
  <RequestId>C004F022-1CC2-4958-9937-675513A2CD7E</RequestId>
</CreateExpressCloudConnection>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"EccId":"ecc-bp1t9osmuln1vxfpt6gy8",
	"RequestId":"C004F022-1CC2-4958-9937-675513A2CD7E"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

