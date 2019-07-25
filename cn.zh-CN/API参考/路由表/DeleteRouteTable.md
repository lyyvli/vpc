# DeleteRouteTable {#doc_api_Vpc_DeleteRouteTable .reference}

调用DeleteRouteTable接口删除自定义路由表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DeleteRouteTable&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteRouteTable|要执行的操作。

 取值： **DeleteRouteTable**。

 |
|RegionId|String|是|cn-hangzhou|路由表所属的VPC的地域ID。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|RouteTableId|String|是|vtb-bp145q7glnuzdvzu2\*\*\*\*|路由表ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|DC668356-BCB4-42FD-9BC3-FA2B2E04B634|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DeleteRouteTable
&RegionId=cn-hangzhou
&RouteTableId=vtb-bp145q7glnuzdvzu2****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteRouteTableResponse>
      <RequestId>62172DD5-6BAC-45DF-8D44-xxxxxxx</RequestId>
</DeleteRouteTableResponse>
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
|400|IncorrectVSwitchStatus|The current virtual switch status does not support this operation.|该 VSwitch 处于 pending 状态，无法删除。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

