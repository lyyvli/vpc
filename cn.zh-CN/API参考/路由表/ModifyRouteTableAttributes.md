# ModifyRouteTableAttributes {#doc_api_Vpc_ModifyRouteTableAttributes .reference}

调用ModifyRouteTableAttributes接口修改路由表的名称和描述。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyRouteTableAttributes&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyRouteTableAttributes|要执行的操作。

 取值： **ModifyRouteTableAttributes**。

 |
|RegionId|String|是|cn-hangzhou|路由表所属的VPC的地域ID。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|RouteTableId|String|是|vtb-bp145q7glnuzdvzu2\*\*\*\*|路由表的ID。

 |
|Description|String|否|路由表的描述信息。|路由表的描述信息。

 长度为 2-256个字符，必须以字母或中文开头，但不能以`http:/`/ 或`https://`开头。

 |
|RouteTableName|String|否|doctest|路由表的名称。

 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://`或`https://`开头。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|62172DD5-6BAC-45DF-8D44-xxxxxxxx|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://vpc.aliyuncs.com/?Action=ModifyRouteTableAttributes
&RegionId=cn-hangzhou
&RouteTableId=vtb-bp145q7glnuzdvzu2****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyRouteTableAttributesResponse>
      <RequestId>62172DD5-6BAC-45DF-8D44-xxxxxxx</RequestId>
</ModifyRouteTableAttributesResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"62172DD5-6BAC-45DF-8D44-xxxxxxxx"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden|User not authorized to operate on the specified resource.|您没有权限操作该资源，请您申请操作权限后再试。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

