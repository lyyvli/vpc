# ActivateRouterInterface {#doc_api_Vpc_ActivateRouterInterface .reference}

调用ActivateRouterInterface接口激活处于Inactive状态的路由器接口。

调用本接口后，路由器接口进入**Activating**状态，激活成功后进入**Active**状态。

**说明：** 无法激活处于欠费状态的路由器接口。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ActivateRouterInterface&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ActivateRouterInterface|要执行的操作。

 取值： **ActivateRouterInterface**。

 |
|RegionId|String|是|cn-hangzhou|路由器接口所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|RouterInterfaceId|String|是|ri-2zeo3xzyf38r4urz\*\*\*\*|路由器接口的ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|079874CD-AEC1-43E6-AC03-ADD96B6E4907|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://vpc.aliyuncs.com/?Action=ActivateRouterInterface
&RegionId=cn-hangzhou
&RouterInterfaceId=ri-2zeo3xzyf38r4urz****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ActivateRouterInterfaceResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</ActivateRouterInterfaceResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|404|InvalidRouterInterfaceId.NotFound|The specified RouterInterfaceId does not exist in our records.|指定的路由器接口不存在，请您检查填写的路由器接口是否正确。|
|400|IncorrectStatus|RouterInterface can be operated by this action only when it's status is Inactive.|只有当路由器接口的状态为Inactive时，才可执行该操作。|
|400|Forbidden.FinancileLocked|This RouterInterface is financiel locked because of bills outstanding.|该路由器接口已欠费锁定，因为您有未结算的账单。|
|400|Forbbiden|The Router instance owener error|该路由器不属于您的账号。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

