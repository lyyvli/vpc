# ListTagResources {#doc_api_Vpc_ListTagResources .reference}

调用ListTagResources查询一个或多个 VPC、EIP 资源已经绑定的标签列表。

-   请求中至少指定参数**ResourceId.N**或**Tag.N（Tag.N.Key与Tag.N.Value）**，以确定检索对象。
-   **Tag.N**是资源的标签，由一个键值对组成。仅指定**Tag.N.Key**时，则返回该标签键关联的所有标签值。仅指定**Tag.N.Value**会报错。
-   如果您同时指定**Tag.N**和**ResourceId.N**筛选标签，则**ResourceId.N**必须满足所有输入的标签键值对。
-   如果您同时指定多个标签键值对，返回结果中为资源中包含被指定的多个键值对的资源。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ListTagResources&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListTagResources|要执行的操作，取值：**ListTagResources**。

 |
|RegionId|String|是|cn-hangzhou|资源所属的地域ID。

 |
|ResourceType|String|是|VPC|资源类型定义。取值范围：

 -   VPC：VPC实例
-   VSWITCH：交换机实例
-   ROUTETABLE：路由表实例
-   EIP：弹性公网IP实例

 |
|NextToken|String|否|caeba0bbb2be03f84eb48b699f0a4883|下一个查询开始Token。

 |
|ResourceId.N|RepeatList|否|vpc-xxxxxxxxxxxxxxxxx|资源ID， N 的取值范围为 1, 20。

 |
|Tag.N.Key|String|否|FinanceDept|标签键。N 的取值范围为 1, 20资源的标签键。N 的取值范围：1~20。一旦传入该值，则不允许为空字符串。最多支持 64 个字符，不能以 aliyun 和 acs: 开头，不能包含 http:// 或者 https:// 。

 |
|Tag.N.Value|String|否|FinanceJoshua|标签值。N 的取值范围为 1, 20。当参数有值，要求对应当tag.N.Key在相同的N的标签键也传入值，否则会报错资源的标签值。N 的取值范围：1~20。一旦传入该值，可以为空字符串。最多支持 128 个字符，不能以 aliyun 和 acs: 开头，不能包含 http:// 或者 https:// 。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|NextToken|String|caeba0bbb2be03f84eb48b699f0a4883|下一个查询开始Token。

 |
|RequestId|String|DE65F6B7-7566-4802-9007-96F2494AC512|请求ID。

 |
|TagResources| | |绑定标签的资源信息。

 |
|ResourcId|String|vpc-xxxxxxxxxxxxxxxx|资源ID。

 |
|ResourceType|String|VPC|资源类型。

 |
|TagKey|String|FinanceDept|标签键。

 |
|TagValue|String|FinanceJoshua|标签键值。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://vpc.aliyuncs.com/?Action=ListTagResources
&RegionId=cn-hangzhou
&ResourceType=VPC
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ListTagResourcesResponse>
	    <TagResources>
		        <TagResource>
			            <ResourceType>instance</ResourceType>
			            <TagValue>FinanceJoshua</TagValue>
			            <ResourceId>vpc-xxxxxxxxxxxxxxxx</ResourceId>
			            <TagKey>FinanceDept</TagKey>
		        </TagResource>
	    </TagResources>
        <NextToken>caeba0bbb2be03f84eb48b699f0a4883</NextToken>
	    <RequestId>DE65F6B7-7566-4802-9007-96F2494AC5XX</RequestId>
</ListTagResourcesResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"TagResources":{
		"TagResource":[
			{
				"ResourceType":"VPC",
				"TagValue":"FinanceJoshua",
				"ResourceId":"vpc-xxxxxxxxxxxxxxxx",
				"TagKey":"FinanceDept"
			}
		]
	},
	"NextToken":"caeba0bbb2be03f84eb48b699f0a4883",
	"RequestId":"DE65F6B7-7566-4802-9007-96F2494AC512"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

