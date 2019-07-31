# TagResources {#doc_api_Vpc_TagResources .reference}

调用TagResources为指定的ECS资源列表统一创建并绑定标签。

**说明：** 单个实例最多可绑定20个标签。绑定标签前，阿里云会校验资源已有标签数量。超过限制值后返回报错信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=TagResources&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|TagResources|系统规定参数。取值：**TagResources**。

 |
|RegionId|String|是|cn-hangzhou|资源所属的地域ID。

 |
|ResourceId.N|RepeatList|是|vpc-xxxxxxxxxxx|资源ID，N的取值范围为 1~20。

 |
|ResourceType|String|是|VPC|资源类型定义。取值范围：

 -   VPC：VPC实例
-   VSWITCH：交换机实例
-   ROUTETABLE：路由表实例
-   EIP：弹性公网IP实例

 |
|Tag.N.Key|String|否|FinanceDept|资源的标签键。N 的取值范围：1~20。一旦传入该值，则不允许为空字符串。最多支持 64 个字符，不能以 aliyun 和 acs: 开头，不能包含 http:// 或者 https:// 。

 |
|Tag.N.Value|String|否|FinanceJoshua|资源的标签值。N 的取值范围：1~20。一旦传入该值，可以为空字符串。最多支持 128 个字符，不能以 aliyun 和 acs: 开头，不能包含 http:// 或者 https:// 。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://vpc.aliyuncs.com/?Action=TagResources
&RegionId=cn-hangzhou
&ResourceId.1=vpc-xxxxxxxxxxx
&ResourceType=VPC
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<TagResourcesResponse>
      <RequestId>C46FF5A8-C5F0-4024-8262-B16B639225A0</RequestId>
</TagResourcesResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"C46FF5A8-C5F0-4024-8262-B16B639225A0"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

