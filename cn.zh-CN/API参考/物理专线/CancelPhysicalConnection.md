# CancelPhysicalConnection {#doc_api_Vpc_CancelPhysicalConnection .reference}

在物理专线开通前，调用CancelPhysicalConnection接口取消物理专线接入，取消后物理专线进入Canceled状态。

只能取消处于Initial、Approved、Allocated和Confirmed状态（未开通状态）的物理专线。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=CancelPhysicalConnection&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CancelPhysicalConnection|要执行的操作。

 取值： **CancelPhysicalConnection**。

 |
|PhysicalConnectionId|String|是|pc-119mfjzm7|物理专线的ID。

 |
|RegionId|String|是|cn-shanghai|物理专线所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个ASCII字符。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=CancelPhysicalConnection
&PhysicalConnectionId=pc-119mfjzm7
&RegionId=cn-shanghai
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CancelPhysicalConnectionResponse>
	  <RequestId>BE36E95A-F83E-4127-A29E-F2F35D4C999A</RequestId>
    </CancelPhysicalConnectionResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"BE36E95A-F83E-4127-A29E-F2F35D4C999A"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidPhysicalConnectionId.NotFound|The PhysicalConnectionId provided does not exist in our records.|该物理专线不存在。|
|400|Forbidden.NotAllowedInState|The request does not allow in this state.|该状态无法执行请求。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

