# ModifyExpressCloudConnectionAttribute {#doc_api_Vpc_ModifyExpressCloudConnectionAttribute .reference}

调用ModifyExpressCloudConnectionAttribute修改高速上云服务连接。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=ModifyExpressCloudConnectionAttribute)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyExpressCloudConnectionAttribute|要执行的操作。

 取值：**ModifyExpressCloudConnectionAttribute**

 |
|EccId|String|是|ecc-bp1t9osmuln\*\*\*\*\*\*\*|高速上云连接实例ID。

 |
|RegionId|String|是|cn-hangzhou|地域ID。

 |
|Description|String|否|ECC|高速上云服务说明。

 |
|Name|String|否|doctest|高速上云服务实例名称。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|E6385514-B0CC-48E3-B9F9-F7BFF64460A2|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=ModifyExpressCloudConnectionAttribute
&EccId=ecc-bp1t9osmuln*******
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyExpressCloudConnectionAttribute>
  <RequestId>E6385514-B0CC-48E3-B9F9-F7BFF64460A2</RequestId>
</ModifyExpressCloudConnectionAttribute>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"E6385514-B0CC-48E3-B9F9-F7BFF64460A2"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

