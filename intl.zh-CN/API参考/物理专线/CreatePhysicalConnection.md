# CreatePhysicalConnection {#doc_api_Vpc_CreatePhysicalConnection .reference}

调用CreatePhysicalConnection接口申请物理专线接入。

申请完成后，物理专线的状态为Initial，请联系运营商进行施工。

调用该接口时，请注意：

-   申请物理专线时，处于**Enabled**状态之外的物理专线不得超过5条。
-   若账号下存在欠费状态的物理专线，则不能再申请物理专线。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=CreatePhysicalConnection&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreatePhysicalConnection|要执行的操作。

 取值： **CreatePhysicalConnection**。

 |
|AccessPointId|String|是|AccessPointId=ap-cn-beijing-ft-A|物理专线所在的接入点。 您可以通过调用[DescribeAccessPoints](~~36062~~)接口获取地域ID。

 |
|ClientToken|String|是|dgfdg12344ff|客户端token，用于保证请求的幂等性。 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|LineOperator|String|是|CT|提供接入物理线路的运营商，取值：

 -   CT：中国电信
-   CU：中国联通
-   CM：中国移动
-   CO：中国其他
-   Equinix：Equinix
-   Other：境外其他

 |
|PeerLocation|String|是|浙江省---vfjdbg\_21e|本地数据中心的地理位置。

 |
|RegionId|String|是|cn-shanghai|物理专线所在的地域。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|CircuitCode|String|否|longtel001|运营商的为物理专线提供的电路编码。

 |
|Description|String|否|物理专线的描述信息|物理专线的描述信息。 长度为 2-256个字符，必须以字母或中文开头，但不能以`http://` 或`https://`开头。

 |
|Name|String|否|test|物理专线的名称。 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://`或`https://`开头。

 |
|PortType|String|否|1000Base-T|物理专线接入端口类型，取值：

 -   100Base-T：百兆电口
-   1000Base-T（默认值）：千兆电口
-   1000Base-LX：千兆单模光口（10千米）
-   10GBase-T：万兆电口
-   10GBase-LR：万兆单模光口（10千米）

 |
|RedundantPhysicalConnectionId|String|否|pc-119mfjzm7|冗余物理专线的ID，该专线的状态必须为Allocated、Confirmed或Enabled。

 |
|Type|String|否|VPC|专线类型，默认值：**VPC**。

 |
|bandwidth|Integer|否|10|带宽包的带宽。取值范围：5-5000，单位为Mbps。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PhysicalConnectionId|String|vpc-bp12mw1f8k3jgygk9bmlj|物理专线ID。

 |
|RequestId|String|8A6A5EC5-6F6C-4906-9689-56ACE58A13E0|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=CreatePhysicalConnection
&AccessPointId=AccessPointId=ap-cn-beijing-ft-A
&ClientToken=dgfdg12344ff
&LineOperator=CT
&PeerLocation=浙江省---vfjdbg_21e
&RegionId=cn-shanghai
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreatePhysicalConnectionResponse>
      <RequestId>8A6A5EC5-6F6C-4906-9689-56ACE58A13E0"</RequestId>
      <PhysicalConnectionId>pc-*************</PhysicalConnectionId>
</CreatePhysicalConnectionResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"8A6A5EC5-6F6C-4906-9689-56ACE58A13E0",
	"PhysicalConnectionId":"pc-**************"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidAccessPointId.NotEnabled|Invalid access point status.|接入点状态不可用。|
|400|InvalidType.Malformd|The Type provided was invalid.|参数Type的值不合法。|
|400|InvalidPeerLocation.Malformd|The PeerLocation provided was invalid.|参数PeerLocation的值不合法。|
|400|InvalidLineOperator.Malformd|The LineOperator provided was invalid.|参数LineOperator的值不合法。|
|400|InvalidPortType.Malformd|The PortType provided was invalid.|该端口类型不合法。|
|400|InvalidDescription.Malformed|The specifid ?Description? is not valid.|指定的资源描述格式不合法。长度为2-256个字符，不能以 http:// 和 https:// 开头。|
|400|InvalidRedundantPhysicalConnectionId.NotFound|The RedundantPhysicalConnectionId does not found.|冗余物理专线不存在。|
|400|InvalidName.Malformed|The specified ?Name? is not valid.|该名称格式不合法。|
|400|QuotaExceeded.pConnPerAP|Physical connection count per ap quota exceed.|超过接入点的物理专线配额。|
|400|InvalidBandwidth|invalid physical connection banwidth.|物理专线的带宽不合法。|
|400|InvalidRedundantPhysicalConnection|redundant physical connection doesn't belong to current user.|该冗余物理专线不属于您的账号。|
|400|InvalidRedundantPhysicalConnectionStatus|invalid redundant physical connection status.|冗余物理专线状态不合法。|
|400|InvalidCircuitCode.Malformed|circuitCode is illegal.|该CircuitCode不合法。|
|400|QuotaExceeded.freePconnPerAP|free physical connections count excceeded.|超过物理专线配额。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

