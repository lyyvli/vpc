# CreateVSwitch {#doc_api_Vpc_CreateVSwitch .reference}

调用CreateVSwitch接口创建一个交换机。

**调用该接口创建交换机时，请注意：**

-   每个VPC内的交换机数量不能超过24个。
-   每个交换机网段的第1个和最后3个IP地址为系统保留地址。以192.168.1.0/24为例，192.168.1.0、192.168.1.253、192.168.1.254和192.168.1.255这些地址是系统保留地址。
-   交换机下的云产品实例数量不允许超过VPC剩余的可用云产品实例数量（15000减去当前云产品实例数量）。
-   一个云产品实例只能属于一个交换机。
-   交换机不支持组播和广播。

交换机创建成功后，网段无法修改。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=CreateVSwitch&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateVSwitch|要执行的操作。 取值： **CreateVSwitch**。

 |
|CidrBlock|String|是|172.16.0.0/24|交换机的网段。交换机网段要求如下：

 -   交换机网段的掩码长度范围为16-29位。
-   交换机的网段必须从属于所在VPC的网段。
-   交换机的网段不能与所在VPC中路由条目的目标网段相同，但可以是目标网段的子集。
-   如果交换机的网段与所在VPC的网段相同时，VPC只能有一个交换机。

 |
|VpcId|String|是|vpc-257gq6n\*\*\*\*|交换机所属的VPC ID。

 |
|ZoneId|String|是|cn-hangzhou-b|交换机所属区的ID。 您可以通过调用[DescribeZones](https://help.aliyun.com/document_detail/36063.html?spm=a2c4g.11186623.2.13.672255b1Ti4hEp)接口获取地域ID。

 |
|RegionId|String|是|cn-hangzhou|交换机的地域ID。

 |
|Ipv6CidrBlock|Integer|否|0|交换机的IPv6网段，支持自定义VPC IPv6网段的最后8bit。取值：**0-255（十进制）**。

 交换机的IPv6网段掩码默认为64位。

 |
|Description|String|否|This is my vswitch.|交换机的描述信息。

 长度为 2-256个字符，必须以字母或中文开头，但不能以`http://` 或`https://`开头。

 |
|VSwitchName|String|否|VSwitch-1|交换机的名称。

 长度为 2-128个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|ClientToken|String|否|dhueeuxxxxxxdde|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|OwnerAccount|String|否| |用户账号。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|VSwitchId|String|vsw-25naue4g\*\*\*\*|交换机的ID。

 |
|RequestId|String|861E6630-AEC0-4B2D-B214-6CB5E44B7F04|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateVSwitch
&CidrBlock=172.16.0.0/24
&VpcId=vpc-257gq6n****
&ZoneId=cn-hangzhou-b
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateVSwitchResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
      <VSwitchId>vsw-25naue4****</VSwitchId>
</CreateVSwitchResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0",
	"VSwitchId":"vsw-25naue4****"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidZoneId.NotFound|Specified zone does not exist.|可用区ID不正确。|
|404|InvalidVpcId.NotFound|Specified VPC does not exist.|该 VPC 不存在。|
|400|InvalidVSwitchName.Malformed|Specified virtual switch name is not valid.|该 VSwitch 名字格式不正确，请您确认VSwitch 名字格式。|
|400|InvalidVSwitchDiscription.Malformed|Specified virtual switch description is not valid.|交换机描述不合法。|
|400|ResourceNotAvailable|Resource you requested is not available in this region or zone.|当前地域或可用区不支持创建交换机。|
|400|InvalidParameter|Specified CIDR block is not valid in VPC.|该网段不在VPC网段内。|
|400|InvalidCidrBlock.Overlapped|Specified CIDR block overlapped with other subnets.|该交换机网段与其他交换机的网段重叠或与已有的自定义路由的目标网段重叠，请使用其他未被占用的网段。|
|400|InvalidCidrBlock.Overlapped|Specified CIDR block overlapped with other entry.|该交换机网段与其他交换机的网段重叠或与已有的自定义路由的目标网段重叠，请使用其他未被占用的网段。|
|400|QuotaExceeded.VSwitch|Virtual switch quota exceeded.|VSwitch 数量达到配额上限，请您减少 VSwitch 数量后再试。|
|400|IncorrectRouteEntryStatus|Some route entry status blocked this operation.|无法执行该操作，当前路由表中有路由条目的状态为pending或modifying。|
|400|IncorrectVSwitchStatus|Some virtual switch is modifying within the same VPC.|同一个 VPC 下存在多个“修改中”的虚拟交换机，请您稍后重试。|
|400|InvalidCirdrBlock.MaskLength|Specified CIDR block is not valid .|该 CIDR 网段格式不正确。|
|400|IncorrectVpcStatus|Current VPC status does not support this operation.|当前 VPC 的状态无法支持这个操作。|
|400|InvalidCidrBlock.Malformed|Specified CIDR block is not valid.|该 CIDR 格式不正确。|
|400|MissingParameter|Miss mandatory parameter.|缺少必要参数,请您检查必填参数是否都已填后再进行操作。|
|400|IncorrectVSwitchStatus|VSwitch Creation simultaneously is not supported.|创建交换机失败，VPC中有交换机的状态为Creating。|
|400|Forbidden.VpcNotFound|Specified VPC can not found.|指定的 VPC 不存在，请您检查 VPC 是否正确。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

