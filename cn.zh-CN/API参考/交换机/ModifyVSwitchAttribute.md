# ModifyVSwitchAttribute {#doc_api_907527 .reference}

使用ModifyVSwitchAttribute修改指定交换机的名称和描述信息。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Vpc&api=ModifyVSwitchAttribute)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyVSwitchAttribute|要执行的操作。 取值： **ModifyVSwitchAttribute**

 |
|RegionId|String|是|cn-hangzhou|交换机所属的地域ID。

 |
|VSwitchId|String|是|vsw-25naue4gz|交换机的ID。

 |
|Description|String|否|This is my vswitch.|交换机的描述信息。

 长度为 2-256个字符，必须以字母或中文开头，但不能以`http://` 或`https://`开头。

 |
|Ipv6CidrBlock|Integer|否|0|交换机的IPv6网段，支持自定义IPv6网段的最后8位。取值：0-255（十进制）。

 交换机的IPv6网段掩码默认为64 位。

 |
|VSwitchName|String|否|VSwitch-1|交换机的名称。 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://`或`https://`开头。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|C0FD0EED-F90D-4479-803D-DD623XXXXXX|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?VSwitchId=vsw-25naue4gz
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyVSwitchAttributeResponse>
  <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</ModifyVSwitchAttributeResponse>

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
|404|InvalidVSwitchId.NotFound|The specified virtual switch does not exists.|该交换机不存在，请您检查输入的交换机是否正确。|
|400|InvalidVSwitchName.Malformed|Specified virtual switch name is not valid.|该 VSwitch 名字格式不正确，请您确认VSwitch 名字格式。|
|400|InvalidVSwitchDiscription.Malformed|Specified virtual switch description is not valid.|该 VSwitch 描述信息格式不正确。|
|400|InvalidVSwitchName.Malformed|Specified virtual switch name is not valid.|该 VSwitch 名字格式不正确，请您确认VSwitch 名字格式。|
|404|InvalidVSwitchId.NotFound|The specified virtual switch does not exists.|该交换机不存在，请您检查输入的交换机是否正确。|
|404|InvalidVSwitchId.NotFound|The specified virtual switch does not exists.|该交换机不存在，请您检查输入的交换机是否正确。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

