# CompletePhysicalConnectionLOA {#doc_api_Vpc_CompletePhysicalConnectionLOA .reference}

调用CompletePhysicalConnectionLOA完成施工完竣。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CompletePhysicalConnectionLOA)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CompletePhysicalConnectionLOA|要执行的操作。

 取值：**CompletePhysicalConnectionLOA**。

 |
|InstanceId|String|是|pc-bp10tvlhnwkwxxxxxxxxxx|物理专线实例ID。

 |
|LineCode|String|是|aaa111|运营商线路编码。

 |
|LineLabel|String|是|bbb222|机房楼内线缆标签。

 |
|RegionId|String|是|cn-hangzhou|物理专线所在的地域。

 |
|ClientToken|String|否|F8983C74-E068-4509-B442-89xxxxxC8F43B|客户端Token鉴权。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|F8983C74-E068-4509-B442-89BD82C8F43B|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?InstanceId=pc-bp10tvlhnwkwxxxxxxxxxx
&LineCode=aaa111
&LineLabel=bbb222
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CompletePhysicalConnectionLOAResponse>
  <code>200</code>
  <message>successful</message>
  <requestId>5FA3B04E-AEA0-4F89-BF0D-3FD71ED69BF7</requestId>
  <success>true</success>
</CompletePhysicalConnectionLOAResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"message":"successful",
	"requestId":"5FA3B04E-AEA0-4F89-BF0D-3FD71ED69BF7",
	"code":"200",
	"success":true
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

