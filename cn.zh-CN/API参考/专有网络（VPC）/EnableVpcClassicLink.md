# EnableVpcClassicLink {#doc_api_Vpc_EnableVpcClassicLink .reference}

调用EnableVpcClassicLink开启ClassicLink。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=EnableVpcClassicLink&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|EnableVpcClassicLink|要执行的操作，取值：**EnableVpcClassicLink**。

 |
|RegionId|String|是|cn-hangzhou|要开启ClassicLink的VPC所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VpcId|String|是|vpc-bp1m7v25emi1h5mtc\*\*\*\*|VPC的ID。

 |
|ClientToken|String|否|d7d24a21-f4ba-4454-9173-b3828dae492b|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|5BE01CD7-5A50-472D-AC14-CA181C5C03BE|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=EnableVpcClassicLink
&RegionId=cn-hangzhou	
&VpcId=vpc-bp1m7v25emi1h5mtc****	
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<EnableVpcClassicLinkResponse>
      <RequestId>AE65530E-8436-4FB1-8217-DCD35712AC89</RequestId>
</EnableVpcClassicLinkResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"AE65530E-8436-4FB1-8217-DCD35712AC89"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|Specified value of "regionId" is not supported.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|IncorrectVpcStatus|Current VPC status does not support this operation.|当前 VPC 的状态无法支持这个操作。|
|404|InvalidVpcId.NotFound|Specified VPC does not exist.|该 VPC 不存在。|
|404|IncorrectClassicLinkStatus|Specified VPC classicLink enabled.|该 VPC 已经开启 ClassicLink。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

