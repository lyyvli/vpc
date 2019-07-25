# ModifyRouterInterfaceAttribute {#doc_api_Vpc_ModifyRouterInterfaceAttribute .reference}

调用ModifyRouterInterfaceAttribute接口修改路由器接口的配置。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyRouterInterfaceAttribute&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyRouterInterfaceAttribute|要执行的操作。

 取值： **ModifyRouterInterfaceAttribute**。

 |
|RegionId|String|是|cn-shanghai|路由器接口所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|RouterInterfaceId|String|是|ri-2zeo3xzyf38r4urz\*\*\*\*|路由器接口的ID。

 |
|DeleteHealthCheckIp|Boolean|否|true|是否删除该路由器接口上配置的健康检查IP。取值：

 -   **true**：删除健康检查IP。
-   **false**（默认值）：不删除健康检查IP。

 |
|Description|String|否|路由器接口|路由器接口的描述信息。

 长度为 2-256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|HealthCheckSourceIp|String|否|116.62.222.XX|健康检查源IP地址，必须是本端VPC内的一个未被使用的IP。

 **说明：** 物理专线接入场景下可指定该参数。

 |
|HealthCheckTargetIp|String|否|116.62.222.XX|健康检查目的IP地址。

 **说明：** 当指定了**HealthCheckSourceIp**后，该参数为必选。

 |
|Name|String|否|TEST|路由器接口的名称。

 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://`或`https://`开头。

 |
|OppositeInterfaceId|String|否|ri-2zeo3xzyf38r4urz\*\*\*\*|对端路由器接口ID。

 |
|OppositeInterfaceOwnerId|Long|否|10|对端路由器接口的所有者ID。

 |
|OppositeRouterId|String|否|vrt-bp1jcg5cmxjbl9xgc\*\*\*\*|对端的路由器的ID。

 |
|OppositeRouterType|String|否|VRouter|要连接的对端路由器接口所属的路由器类型。默认值为**VBR**。

 取值：**VRouter|VBR**

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://vpc.aliyuncs.com/?Action=ModifyRouterInterfaceAttribute
&RegionId=cn-shanghai
&RouterInterfaceId=ri-2zeo3xzyf38r4urz****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyRouterInterfaceAttributeResponse>
      <RequestId>980960B0-2969-40BF-8542-EBB34FD358AB</RequestId>
</ModifyRouterInterfaceAttributeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"980960B0-2969-40BF-8542-EBB34FD358AB"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|404|InvalidRouterInterfaceId.NotFound|The specified RouterInterfaceId does not exist in our records.|指定的路由器接口不存在，请您检查填写的路由器接口是否正确。|
|400|Forbidden.FinancileLocked|This RouterInterface is financiel locked because of bills outstanding.|该路由器接口已欠费锁定，因为您有未结算的账单。|
|400|InvalidName.Malformd|The attribute name is illeagl.|该名称格式不合法。|
|400|InvalidOppositeRouterType.ValueNotSupported|The specified OppositeRouterType is not valid.|参数OppositeRouterType的值不合法。|
|400|InvalidDescription.Malformed|The Description is illeagl.|指定的资源描述格式不合法。长度为2-256个字符，不能以 http:// 和 https:// 开头。|
|400|Forbbiden|The Router instance owener error|该路由器不属于您的账号。|
|400|LinkRole.NotSupport|This linkrole is not supported|这个链接不支持。|
|400|InvalidParam.ModifyRouterInterface|Modify routerinterface param invalide|编辑路由器接口参数不合法。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

