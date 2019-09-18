# DeleteVSwitch {#doc_api_Vpc_DeleteVSwitch .reference}

调用DeleteVSwitch接口删除交换机。

## 接口说明 {#description .section}

调用该接口删除交换机时，请注意：

-   删除交换机之前，需要先释放或移走VPC内的所有资源，包括交换机、云产品实例、路由器接口、HAVIP等。
-   只有处于Available状态的交换机可以被删除。
-   交换机所在的VPC正在创建/删除交换机或路由条目时，无法删除交换机。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DeleteVSwitch&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteVSwitch|要执行的操作，取值： **DeleteVSwitch**。

 |
|RegionId|String|是|cn-hangzhou|要删除的交换机的地域ID。

 |
|VSwitchId|String|是|vsw-asdfjlna\*\*\*\*|要删除的交换机的ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://vpc.aliyuncs.com/?Action=DeleteVSwitch
&VSwitchId=vsw-asdfjlna****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteVSwitchResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</DeleteVSwitchResponse>
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
|400|IncorrectVSwitchStatus|The current virtual switch status does not support this operation.|该 VSwitch 处于 pending 状态，无法删除。|
|400|DependencyViolation|Specified object has dependent resources.|该交换机下还有资源未释放，无法删除，请释放该 VPC 下的云产品资源后再删除 VPC。|
|400|DependencyViolation|Some route entry status blocked this operation.|无法执行该操作，当前路由表中有路由条目的状态为pending或modifying。|
|400|IncorrectRouteEntryStatus|Some route entry status blocked this operation.|无法执行该操作，当前路由表中有路由条目的状态为pending或modifying。|
|400|DependencyViolation.HaVip|VSwitch cannot be deleted when there are some HaVip dependent with it.|无法删除交换机，该交换机下有关联的HAVIP。|
|400|MissingParameter|Miss mandatory parameter.|缺少必要参数,请您检查必填参数是否都已填后再进行操作。|
|404|InvalidVSwitchId.NotFound|VSwitch not exist.|该交换机不存在，请您检查输入的交换机是否正确。|
|404|IncorrectStatus|Vswtich status not stable.|当前交换机的状态为pending或modifying，请您稍后再试。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

