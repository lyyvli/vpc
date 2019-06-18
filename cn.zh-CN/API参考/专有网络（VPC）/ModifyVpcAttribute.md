# ModifyVpcAttribute {#doc_api_Vpc_ModifyVpcAttribute .reference}

调用ModifyVpcAttribute接口修改指定VPC的名称和描述信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=ModifyVpcAttribute)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyVpcAttribute|要执行的操作，取值： **ModifyVpcAttribute**。

 |
|RegionId|String|是|cn-hangzhou|VPC的地域。

 |
|VpcId|String|是|vpc-bp1qtbach57ywecfxxxxxx|VPC的ID。

 |
|CidrBlock|String|否|192.168.0.0/24|VPC的网段。

 |
|Description|String|否|This is my VPC.|VPC的描述信息。长度为2-256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|EnableIPv6|Boolean|否|true|是否开启IPv6网段，取值：

 -   **true**：开启。
-   **false**：不开启。

 |
|VpcName|String|否|Vpc-1|VPC的名称。长度为2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-），但不能以`http://`或`https://`开头。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyVpcAttribute
&VpcId=vpc-bp1qtbach57ywecfxxxxxx
&VpcName=Vpc-1
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

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

