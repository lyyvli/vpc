# DescribeIPv6TranslatorAclLists {#doc_api_Vpc_DescribeIPv6TranslatorAclLists .reference}

查询已创建的访问控制策略组。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeIPv6TranslatorAclLists&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeIPv6TranslatorAclLists|要执行的操作。 取值： **DescribeIPv6TranslatorAclLists**。

 |
|RegionId|String|是|cn-hangzhou|访问控制策略组的地域。 您可以通过调用DescribeRegions接口获取地域ID。

 |
|AclId|String|否|ipv6transacl-bp1de2xxxx|访问控制策略组ID。

 |
|AclName|String|否|acl1|访问控制策略组的名称。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为1。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Ipv6TranslatorAcls| | |查询到的访问控制策略组列表。

 |
|AclId|String|ipv6transacl-bp1de2xxxx|访问控制策略组的ID。

 |
|AclName|String|acl1|访问控制策略组的名称。

 |
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|1|每页条目数。

 |
|RequestId|String|8B2F5262-6B57-43F2-xxxxx|请求ID。

 |
|TotalCount|Integer|1|查询的条目总数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://vpc.aliyuncs.com/?Action=DescribeIPv6TranslatorAclLists
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeIPv6TranslatorAclListsResponse>
    <RequestId>8B2F5262-6B57-43F2-xxxxx</RequestId>
    <Ipv6TranslatorAcls>
          <AclId>ipv6transacl-bp1de2xxxx</AclId>
          <AclName>acl1</AclName>
    </Ipv6TranslatorAcls>
    <PageNumber>1</PageNumber>
    <PageSize>1</PageSize>
    <TotalCount>1</TotalCount>
</DescribeIPv6TranslatorAclListsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":"1",
	"TotalCount":"1",
	"PageSize":"1",
	"RequestId":"8B2F5262-6B57-43F2-xxxxx",
	"Ipv6TranslatorAcls":{
		"AclId":"ipv6transacl-bp1de2xxxx",
		"AclName":"acl1"
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

