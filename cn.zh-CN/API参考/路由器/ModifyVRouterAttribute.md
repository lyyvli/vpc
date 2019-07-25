# ModifyVRouterAttribute {#doc_api_Vpc_ModifyVRouterAttribute .reference}

调用ModifyVRouterAttribute接口修改路由器的名称和描述信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyVRouterAttribute&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyVRouterAttribute|要执行的操作。

 取值：**ModifyVRouterAttribute**。

 |
|RegionId|String|是|cn-hangzhou|VPC所在的地域。

 |
|VRouterId|String|是|vrt-bp1lhl0taikrteen8\*\*\*\*|路由器的ID。

 |
|Description|String|否|My VRouter|路由器的描述信息。

 长度为 2-256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|VRouterName|String|否|VRouter-1|路由器的名称。

 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://`或`https://`开头。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyVRouterAttribute
&VRouterId=vrt-bp1lhl0taikrteen8****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyVRouterAttributeResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</ModifyVRouterAttributeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0",
	"RouteTableId":"vtb-bp145q7glnuzdvzu2****",
	"VpcId":"vpc-bp15zckdt37pq72zv****",
	"VRouterId":"vrt-bp1lhl0taikrteen8****"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidVRouterId.NotFound|Specified virtual router does not exist.|该路由器不存在，请您检查输入的路由器是否正确。|
|400|InvalidVRouterName.Malformed|Specified virtual router name is not valid.|该路由器名字格式不正确。|
|400|InvalidVRouterDiscription.Malformed|Specified virtual router description is not valid.|该路由器描述信息格式不正确。|
|400|MissingParameter|Miss mandatory parameter.|缺少必要参数,请您检查必填参数是否都已填后再进行操作。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

