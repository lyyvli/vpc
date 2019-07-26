# ModifyBgpPeerAttribute {#doc_api_Vpc_ModifyBgpPeerAttribute .reference}

调用ModifyBgpGroupAttribute接口修改BGP邻居的属性。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyBgpPeerAttribute&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyBgpPeerAttribute|要执行的操作，取值：**ModifyBgpPeerAttribute**。

 |
|BgpPeerId|String|是|Bgp-awjhxxxxxxxx|BGP邻居的ID。

 |
|RegionId|String|是|cn-shanghai|BGP组所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|BgpGroupId|String|否|bgpg-wz9f62v4fbgxxxxxxxx|BGP组的ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-001xxxxxxxx|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。

 |
|EnableBfd|Boolean|否|true|是否开启BFD功能，取值：

 -   **true**：开启BFD功能。
-   **false**：不开启BFD功能。

 |
|PeerIpAddress|String|否|116.62.xx.xx|BGP邻居的IP地址。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|D4B7649A-61BB-4C64-A586-1DFF1EDA6A42|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyBgpPeerAttribute
&BgpPeerId=Bgp-awjhxxxxxxxx
&RegionId=cn-shanghai
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateBgpPeerResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</CreateBgpPeerResponse>
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
|400|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

