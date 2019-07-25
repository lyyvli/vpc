# AssociateRouteTable {#doc_api_Vpc_AssociateRouteTable .reference}

调用AssociateRouteTable接口将创建的自定义路由表和同一VPC内的交换机绑定。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=AssociateRouteTable&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AssociateRouteTable|要执行的操作。

 取值：**AssociateRouteTable**。

 |
|RegionId|String|是|cn-hangzhou|路由表所属的VPC的地域ID。

 您可以通过调用[DescribeRegions](~~36063~~) 接口获取地域ID。

 |
|RouteTableId|String|是|vtb-bp145q7glnuzdvzu2\*\*\*\*|路由表ID。

 |
|VSwitchId|String|是|vsw-25naue4\*\*\*\*|要绑定的交换机ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|DC668356-BCB4-42FD-9BC3-FA2B2E04B634|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://vpc.aliyuncs.com/?Action=AssociateRouteTable
&RegionId=cn-hangzhou
&RouteTableId=vtb-bp145q7glnuzdvzu2****
&VSwitchId=vsw-25naue4****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AssociateRouteTableResponse>
      <RequestId>62172DD5-6BAC-45DF-8D44-xxxxxxx</RequestId>
</AssociateRouteTableResponse>
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

