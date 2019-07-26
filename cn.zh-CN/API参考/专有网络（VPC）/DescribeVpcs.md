# DescribeVpcs {#doc_api_Vpc_DescribeVpcs .reference}

调用DescribeVpcs接口查询已创建的VPC。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeVpcs&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeVpcs|要执行的操作。 取值： **DescribeVpcs**。

 |
|RegionId|String|是|cn-hangzhou|VPC所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|IsDefault|Boolean|否|false|是否查询指定地域下的默认VPC，取值：

 -   **true**（默认值）：查询指定地域下的所有VPC。
-   **false**：不查询默认VPC。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为**1**。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为**50**，默认值为**10**。

 |
|ResourceGroupId|String|否|rg-acfmxazb4p\*\*\*\*|要查询的VPC所属资源组ID。

 |
|VpcId|String|否|vpc-257gq64\*\*\*\*|VPC的ID。

 最多支持指定20个VPC ID，多个VPC ID之间用半角逗号隔开。

 |
|VpcName|String|否|Vpc-1|VPC的名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Vpcs| | |VPC的详细信息。

 |
|CidrBlock|String|10.0.0.0/24|VPC的网段。

 |
|CreationTime|String|2018-04-18T15:02:37Z|VPC的创建时间。

 |
|Description|String|This is my VPC.|VPC的描述信息。

 |
|Ipv6CidrBlock|String|224.224.223.212/24|VPC的IPv6网段。

 |
|IsDefault|Boolean|false|是否是该地域的默认VPC。

 |
|NatGatewayIds| |nat-245xxxftwt45\*\*\*\*111|NAT网关的ID。

 |
|RegionId|String|cn-hangzhou|VPC所在的地域。

 |
|ResourceGroupId|String|rg-acfmxazb4ph\*\*\*\*|地域ID。

 |
|RouterTableIds| |vtb-bp1krxxzp0c29fmon\*\*\*\*|路由表ID。

 |
|Status|String|Available|VPC的状态，取值：

 -   Pending：配置中
-   Available：可用

 |
|Tags| | |VPC的标签。

 |
|Key|String|env|标签的键值。

 |
|Value|String|internal|标签的取值。

 |
|UserCidrs| |10.0.0.0/8|用户侧网段的列表。

 |
|VRouterId|String|vrt-bp1jcg5cmxjbl9xgc\*\*\*\*|VPC路由器的ID。

 |
|VSwitchIds| |\{ "VSwitchId": \[\] \}|VPC中交换机的列表。

 |
|VpcId|String|vpc-bp1qpo0kug3a20qqe\*\*\*\*|VPC的ID。

 |
|VpcName|String|vpc1|VPC的名称。

 |
|TotalCount|Integer|2|列表条目数。

 |
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|10|每页包含多少条目。

 |
|RequestId|String|C6532AA8-D0F7-497F-A8EE-094126D441F5|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeVpcs
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeVpcsResponse>
  <PageNumber>1</PageNumber>
  <Vpcs>
		    <Vpc>
			      <VpcName></VpcName>
			      <Description></Description>
			      <IsDefault>false</IsDefault>
			      <ResourceGroupId>rg-acfmxazb4ph****</ResourceGroupId>
			      <UserCidrs></UserCidrs>
			      <NatGatewayIds></NatGatewayIds>
			      <RouterTableIds>
				        <RouterTableIds>vtb-bp1krxxzp0c29fmon****</RouterTableIds>
			      </RouterTableIds>
			      <VpcId>vpc-bp1qpo0kug3a20qqe****</VpcId>
			      <VRouterId>vrt-bp1jcg5cmxjbl9xgc****</VRouterId>
			      <CreationTime>2018-12-06T06:11:55Z</CreationTime>
			      <Status>Available</Status>
			      <CidrBlock>172.16.0.0/12</CidrBlock>
			      <VSwitchIds></VSwitchIds>
			      <RegionId>cn-hangzhou</RegionId>
			      <Ipv6CidrBlock></Ipv6CidrBlock>
		    </Vpc>
		    <Vpc>
			      <VpcName>kttest</VpcName>
			      <Description></Description>
			      <IsDefault>false</IsDefault>
			      <ResourceGroupId>rg-acfmxazb4ph****</ResourceGroupId>
			      <UserCidrs></UserCidrs>
			      <NatGatewayIds></NatGatewayIds>
			      <RouterTableIds>
				        <RouterTableIds>vtb-bp1blq1oh0ybfnpm1****</RouterTableIds>
			      </RouterTableIds>
			      <VpcId>vpc-bp1aevy8sofi8mh1q****</VpcId>
			      <VRouterId>vrt-bp149ve7yeyvio4nc****</VRouterId>
			      <CreationTime>2018-11-08T08:54:03Z</CreationTime>
			      <Status>Available</Status>
			      <CidrBlock>192.168.0.0/16</CidrBlock>
			      <VSwitchIds>
				        <VSwitchId>vsw-bp12mw1f8k3jgygk****</VSwitchId>
			      </VSwitchIds>
			      <RegionId>cn-hangzhou</RegionId>
			      <Ipv6CidrBlock></Ipv6CidrBlock>
		    </Vpc>
	  </Vpcs>
	
  <TotalCount>2</TotalCount>
  <PageSize>10</PageSize>
  <RequestId>C6532AA8-D0F7-497F-A8EE-094126D441F5</RequestId>
</DescribeVpcsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":2,
	"Vpcs":{
		"Vpc":[
			{
				"VpcName":"",
				"Description":"",
				"IsDefault":false,
				"ResourceGroupId":"rg-acfmxazb4ph****",
				"UserCidrs":{
					"UserCidr":[]
				},
				"NatGatewayIds":{
					"NatGatewayIds":[]
				},
				"RouterTableIds":{
					"RouterTableIds":[
						"vtb-bp1krxxzp0c29fmon****"
					]
				},
				"VpcId":"vpc-bp1qpo0kug3a20qqe****",
				"VRouterId":"vrt-bp1jcg5cmxjbl9xgc****",
				"CreationTime":"2018-12-06T06:11:55Z",
				"Status":"Available",
				"CidrBlock":"172.16.0.0/12",
				"VSwitchIds":{
					"VSwitchId":[]
				},
				"RegionId":"cn-hangzhou",
				"Ipv6CidrBlock":""
			},
			{
				"VpcName":"kttest",
				"Description":"",
				"IsDefault":false,
				"ResourceGroupId":"rg-acfmxazb4ph****",
				"UserCidrs":{
					"UserCidr":[]
				},
				"NatGatewayIds":{
					"NatGatewayIds":[]
				},
				"RouterTableIds":{
					"RouterTableIds":[
						"vtb-bp1blq1oh0ybfnpm1****"
					]
				},
				"VpcId":"vpc-bp1aevy8sofi8mh1q****",
				"VRouterId":"vrt-bp149ve7yeyvio4nc****",
				"CreationTime":"2018-11-08T08:54:03Z",
				"Status":"Available",
				"CidrBlock":"192.168.0.0/16",
				"VSwitchIds":{
					"VSwitchId":[
						"vsw-bp12mw1f8k3jgygk9****"
					]
				},
				"RegionId":"cn-hangzhou",
				"Ipv6CidrBlock":""
			}
		]
	},
	"PageSize":10,
	"RequestId":"C6532AA8-D0F7-497F-A8EE-094126D441F5"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|500|InternalError|The request processing has failed due to some unknown error.|请求处理由于某些未知错误失败。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

