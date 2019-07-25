# ApplyPhysicalConnectionLOA {#doc_api_Vpc_ApplyPhysicalConnectionLOA .reference}

调用ApplyPhysicalConnectionLOA申请LOA。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=ApplyPhysicalConnectionLOA)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ApplyPhysicalConnectionLOA|要执行的操作。

 取值：**ApplyPhysicalConnectionLOA**。

 |
|CompanyName|String|是|company|物理专线接入的客户公司名称。

 |
|ConstructionTime|String|是|2019-02-28T16:00:00.000Z|施工单位入场时间。

 |
|InstanceId|String|是|pc-bp1qrb3044eqixxxxxxxx|物理专线实例ID。

 |
|LineType|String|是|SDH|物理专线类型。

 |
|RegionId|String|是|cn-hangzhou|专线实例所属的地域ID。

 |
|Si|String|是|阿里|物理专线施工单位。

 |
|Bandwidth|Integer|否|3|物理专线带宽值。

 |
|ClientToken|String|否|A47BD386-7FDE-4xxx4-8D22-C62xxxxxxxx|客户端鉴权。

 |
|PMInfo.N.PMCertificateNo|String|否|3210xxxxxxxxxxxxxx|施工工程师证件号码。

 N是自然数，调用接口时需要替换。

 |
|PMInfo.N.PMCertificateType|String|否|IDCard|施工工程师证件类型。

 N是自然数，调用接口时需要替换。

 |
|PMInfo.N.PMContactInfo|String|否|13200000000|施工工程师联系方式。

 N是自然数，调用接口时需要替换。

 |
|PMInfo.N.PMGender|String|否|Male|施工工程师性别。

 N是自然数，调用接口时需要替换。

 |
|PMInfo.N.PMName|String|否|张三|施工工程师姓名。

 N是自然数，调用接口时需要替换。

 |
|PeerLocation|String|否|杭州|物理专线部署地理位置。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|A47BD386-7FDE-42C4-8D22-C6223D18AA1C|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=ApplyPhysicalConnectionLOA
&CompanyName=company
&ConstructionTime=2019-02-28T16:00:00.000Z
&InstanceId=pc-bp1qrb3044eqixxxxxxxx
&LineType=SDH
&RegionId=cn-hangzhou
&Si=阿里
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ApplyPhysicalConnectionLOAResponse>
  <RequestId>A47BD386-7FDE-42C4-8D22-C6223D18AA1C</RequestId>
</ApplyPhysicalConnectionLOAResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"A47BD386-7FDE-42C4-8D22-C6223D18AA1C"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

