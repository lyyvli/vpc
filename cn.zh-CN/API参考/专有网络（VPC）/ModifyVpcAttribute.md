# ModifyVpcAttribute {#doc_api_Vpc_ModifyVpcAttribute .reference}

调用ModifyVpcAttribute接口修改指定VPC的名称和描述信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyVpcAttribute&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyVpcAttribute|要执行的操作，取值： **ModifyVpcAttribute**。

 |
|RegionId|String|是|cn-hangzhou|VPC的地域。

 |
|VpcId|String|是|vpc-bp1qtbach57ywecf\*\*\*\*|VPC的ID。

 |
|CidrBlock|String|否|192.168.0.0/24|VPC的网段，支持将VPC网段在10.0.0.0/8、172.16.0.0/12和192.168.0.0/16以及它们的子网范围内放大或缩小，网段的掩码为8-24位。

 |
|Description|String|否|This is my VPC.|VPC的描述信息。长度为2-256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|EnableIPv6|Boolean|否|true|是否开启IPv6网段，取值：

 -   **true**：开启。
-   **false**：关闭。

 |
|VpcName|String|否|Vpc-1|VPC的名称。长度为2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-），但不能以`http://`或`https://`开头。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=ModifyVpcAttribute
&VpcId=vpc-bp1qtbach57ywecf****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyVpcAttributeResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</ModifyVpcAttributeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"43B72D30-25E1-4FA3-96A8-89374A521D1A"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidVpcId.NotFound|Specified VPC does not exist.|该 VPC 不存在。|
|400|InvalidVpcName.Malformed|Specified VPC name is not valid.|专有网络VPC名称格式不正确，请您修复VPC的格式后再重试。|
|400|InvalidVpcDiscription.Malformed|Specified VPC description is not valid.|该 VPC 描述的格式不符合要求。|
|400|InvalidParameter|Specified UserCidr invalid format.|该用户侧网段格式不正确。|
|400|InvalidParameter|Specified UserCidr Subnet mask is not valid .|该用户侧网段的子网掩码不合法。|
|400|InvalidUserCidr.Quota|Specified UserCidr number is greater than 3.|UserCird达到配额限制。|
|400|InvalidUserCidr.Malformed|Specified UserCidr overlapping in of 100.64.0.0/10.|该UserCird和100.64.0.0/10重叠。|
|400|IncorrectVpcStatus|Current VPC status does not support this operation.|当前 VPC 的状态无法支持这个操作。|
|400|InvalidCidrBlock.Malformed|Specified CIDR block is not valid.|该 CIDR 格式不正确。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

