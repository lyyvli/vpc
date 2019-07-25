# UnassociateRouteTable {#doc_api_Vpc_UnassociateRouteTable .reference}

调用UnassociateRouteTable接口将路由表和交换机解绑。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=UnassociateRouteTable&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UnassociateRouteTable|要执行的操作。

 取值： **UnassociateRouteTable**。

 |
|RegionId|String|是|cn-hangzhou|路由表所属的VPC的地域ID。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|RouteTableId|String|是|vtb-bp145q7glnuzdvzu2\*\*\*\*|路由表ID。

 |
|VSwitchId|String|是|vsw-25naue4\*\*\*\*|要解绑的交换机ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|62172DD5-6BAC-45DF-8D44-xxxxxxx|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=UnassociateRouteTable
&RegionId=cn-hangzhou
&RouteTableId=vtb-bp145q7glnuzdvzu2****
&VSwitchId=vsw-25naue4****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UnassociateRouteTableResponse>
      <RequestId>62172DD5-6BAC-45DF-8D44-xxxxxxx</RequestId>
</UnassociateRouteTableResponse>
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
|404|InvalidRouteTableId.NotFound|Specified route table does not exist.|该路由表不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

