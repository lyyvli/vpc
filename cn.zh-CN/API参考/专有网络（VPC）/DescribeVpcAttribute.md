# DescribeVpcAttribute {#doc_api_Vpc_DescribeVpcAttribute .reference}

调用DescribeVpcAttribute接口查询指定VPC的配置信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeVpcAttribute|要执行的操作。 取值：**DescribeVpcAttribute**。

 |
|RegionId|String|是|cn-hangzhou|VPC的所属地域ID。

 |
|VpcId|String|是|vpc-bp18sth14qii3pnv\*\*\*\*|要查询的VPC ID。

 |
|IsDefault|Boolean|否|false|是否为默认VPC，取值：

 -   **false**：不是默认VPC。
-   **true**：是默认VPC。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|AssociatedCens| | |绑定的云企业网列表。

 |
|CenId|String|cen-7qthudw0ll6jmc\*\*\*\*|云企业网实例ID。

 |
|CenOwnerId|Long|1231579085529123|云企业网所属账号的ID。

 |
|CenStatus|String|Attached|云企业网状态。

 |
|CidrBlock|String|192.168.0.0/16|VPC的私网网段。

 |
|ClassicLinkEnabled|Boolean|false|是否开启了ClassicLink功能。

 |
|CloudResources| | |VPC下的资源列表。

 |
|ResourceCount|Integer|1|VPC下的资源数量。

 |
|ResourceType|String|VSwitch|VPC下的资源类型。

 |
|CreationTime|String|2018-10-16T07:31:09Z|VPC的创建时间。

 |
|Description|String|VPC|VPC的描述。

 |
|Ipv6CidrBlock|String|224.223.234.233/24|VPC的IPv6网段。

 |
|IsDefault|Boolean|false|是否是默认VPC。

 |
|RegionId|String|cn-hangzhou|VPC所在的地域。

 |
|RequestId|String|7486AE4A-129D-43DB-A714-2432C074BA04|请求ID。

 |
|ResourceGroupId|String|rg-acfmxazb4ph\*\*\*\*|资源组ID。

 |
|Status|String|Available|VPC的状态。

 |
|UserCidrs| |172.16.0.1/24|用户侧网络的网段，如需定义多个网段请使用半角逗号隔开，最多支持3个网段。

 |
|VRouterId|String|vrt-bp1jso6ng1at0ajsc\*\*\*\*|VPC的路由器ID。

 |
|VSwitchIds| |\{"VSwitchId": \[ "vsw-bp14cagpfysr29feg\*\*\*\*" \]\}|VPC下的交换机列表。

 |
|VpcId|String|vpc-bp18sth14qii3pnvo\*\*\*\*|VPC ID。

 |
|VpcName|String|doctest2|VPC的名称。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://vpc.aliyuncs.com/?Action=DescribeVpcAttribute
&RegionId=cn-hangzhou
&VpcId=vpc-bp18sth14qii3pnv****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeVpcAttributeResponse>
	  <VpcName>doctest2</VpcName>
	  <Description></Description>
	  <IsDefault>false</IsDefault>
	  <ResourceGroupId>rg-acfmxazb4ph****</ResourceGroupId>
	  <UserCidrs></UserCidrs>
	  <ClassicLinkEnabled>false</ClassicLinkEnabled>
	  <AssociatedCens>
		    <AssociatedCen>
			      <CenStatus>Attached</CenStatus>
			      <CenOwnerId>12315790855****</CenOwnerId>
			      <CenId>cen-7qthudw0ll6jmc****</CenId>
		    </AssociatedCen>
	  </AssociatedCens>
	  <VRouterId>vrt-bp1jso6ng1at0ajs****</VRouterId>
	  <VpcId>vpc-bp18sth14qii3pnvo****</VpcId>
	  <CreationTime>2018-10-16T07:31:09Z</CreationTime>
	  <CidrBlock>192.168.0.0/16</CidrBlock>
	  <Status>Available</Status>
	  <VSwitchIds>
		    <VSwitchId>vsw-bp14cagpfysr29fe****</VSwitchId>
	  </VSwitchIds>
	  <RequestId>7486AE4A-129D-43DB-A714-2432C074BA04</RequestId>
	  <RegionId>cn-hangzhou</RegionId>
	  <CloudResources>
		    <CloudResourceSetType>
			      <ResourceType>VSwitch</ResourceType>
			      <ResourceCount>1</ResourceCount>
		    </CloudResourceSetType>
		    <CloudResourceSetType>
			      <ResourceType>VRouter</ResourceType>
			      <ResourceCount>1</ResourceCount>
		    </CloudResourceSetType>
		    <CloudResourceSetType>
			      <ResourceType>RouteTable</ResourceType>
			      <ResourceCount>1</ResourceCount>
		    </CloudResourceSetType>
	  </CloudResources>
</DescribeVpcAttributeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"VpcName":"doctest2",
	"Description":"",
	"IsDefault":false,
	"ResourceGroupId":"rg-acfmxazb4ph****",
	"UserCidrs":{
		"UserCidr":[]
	},
	"ClassicLinkEnabled":false,
	"AssociatedCens":{
		"AssociatedCen":[
			{
				"CenStatus":"Attached",
				"CenOwnerId":"123157908552****",
				"CenId":"cen-7qthudw0ll6jmc****"
			}
		]
	},
	"VRouterId":"vrt-bp1jso6ng1at0ajs****",
	"VpcId":"vpc-bp18sth14qii3pnvo****",
	"CreationTime":"2018-10-16T07:31:09Z",
	"CidrBlock":"192.168.0.0/16",
	"Status":"Available",
	"VSwitchIds":{
		"VSwitchId":[
			"vsw-bp14cagpfysr29feg****"
		]
	},
	"RegionId":"cn-hangzhou",
	"RequestId":"7486AE4A-129D-43DB-A714-2432C074BA04",
	"CloudResources":{
		"CloudResourceSetType":[
			{
				"ResourceType":"VSwitch",
				"ResourceCount":1
			},
			{
				"ResourceType":"VRouter",
				"ResourceCount":1
			},
			{
				"ResourceType":"RouteTable",
				"ResourceCount":1
			}
		]
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|500|InternalError|The request processing has failed due to some unknown error.|请求处理由于某些未知错误失败。|
|400|IncorrectVpcStatus|Current VPC status does not support this operation.|当前 VPC 的状态无法支持这个操作。|
|404|InvalidVpcId.NotFound|Specified VPC does not exist.|该 VPC 不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

