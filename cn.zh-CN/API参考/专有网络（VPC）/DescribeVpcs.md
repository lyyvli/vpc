# DescribeVpcs {#doc_api_949157 .reference}

使用DescribeVpcs查询已创建的VPC。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Vpc&api=DescribeVpcs)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

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
|PageNumber|Integer|否|10|列表的页码，默认值为1。

 |
|PageSize|Integer|否|1|分页查询时每页的行数，最大值为50，默认值为10。

 |
|ResourceGroupId|String|否|xxxxx|要查询的VPC所属资源组ID。

 |
|Tag.N.Key|String|否|Tag.1.name|过滤条件。N取值范围为1-5。

 |
|Tag.N.Value|String|否|Tag.1.myvpc|对应过滤条件的值。N的取值范围为1-5。

 |
|VpcId|String|否|vpc-257gq64xxxxx|VPC的ID。

 最多支持指定20个VPC ID，多个VPC ID之间用半角逗号隔开。

 |
|VpcName|String|否|Vpc-1|VPC的名称。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Vpcs| | |VPC的详细信息。

 |
|└CidrBlock|String|10.0.0.0/24|VPC的网段。

 |
|└CreationTime|String|2018-04-18T15:02:37Z|VPC的创建时间。

 |
|└Description|String|description|VPC的描述信息。

 |
|└Ipv6CidrBlock|String|224.224.223.212/24|VPC的IPv6网段。

 |
|└IsDefault|Boolean|false|是否是该地域的默认VPC。

 |
|└NatGatewayIds| |nat-245xxxftwt4567|NAT网关的ID。

 |
|└RegionId|String|cn-hangzhou|VPC所在的地域。

 |
|└ResourceGroupId|String|rg-acfmxazb4ph6aiy|地域ID。

 |
|└RouterTableIds| |vtb-bp145q7glnuzdvzu21pom|路由表ID。

 |
|└Status|String|Available|VPC的状态，取值：

 -   Pending：配置中
-   Available：可用

 |
|└Tags| | |VPC的标签。

 |
|└Key|String|env|标签的键值。

 |
|└Value|String|internal|标签的取值。

 |
|└UserCidrs| |10.0.0.0/8|用户侧网段的列表。

 |
|└VRouterId|String|vrt-bp1lhl0taikrteen80oxx|VPC路由器的ID。

 |
|└VSwitchIds| |\{ "VSwitchId": \[\] \}|VPC中交换机的列表。

 |
|└VpcId|String|vpc-bp15zckdt37pq72zvw3|VPC的ID。

 |
|└VpcName|String|vpc1|VPC的名称。

 |
|TotalCount|Integer|1|列表条条目数。

 |
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|21|每页包含多少条目。

 |
|RequestId|String|9B941224-B647-4644-A746-641906D6B954|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeVpcsResponse>
  <PageNumber>1</PageNumber>
  <Vpcs>
    <Vpc>
      <VpcName/>
      <Description/>
      <IsDefault>false</IsDefault>
      <ResourceGroupId>rg-acfmxazb4ph6aiy</ResourceGroupId>
      <UserCidrs/>
      <NatGatewayIds/>
      <RouterTableIds>
        <RouterTableIds>vtb-bp1krxxzp0c29fmontbal</RouterTableIds>
      </RouterTableIds>
      <VpcId>vpc-bp1qpo0kug3a20qqe9h7v</VpcId>
      <VRouterId>vrt-bp1jcg5cmxjbl9xgc58bw</VRouterId>
      <CreationTime>2018-12-06T06:11:55Z</CreationTime>
      <Status>Available</Status>
      <CidrBlock>172.16.0.0/12</CidrBlock>
      <VSwitchIds/>
      <RegionId>cn-hangzhou</RegionId>
      <Ipv6CidrBlock/>
    </Vpc>
    <Vpc>
      <VpcName>kttest</VpcName>
      <Description/>
      <IsDefault>false</IsDefault>
      <ResourceGroupId>rg-acfmxazb4ph6aiy</ResourceGroupId>
      <UserCidrs/>
      <NatGatewayIds/>
      <RouterTableIds>
        <RouterTableIds>vtb-bp1blq1oh0ybfnpm1bh20</RouterTableIds>
      </RouterTableIds>
      <VpcId>vpc-bp1aevy8sofi8mh1qc5cm</VpcId>
      <VRouterId>vrt-bp149ve7yeyvio4ncklxz</VRouterId>
      <CreationTime>2018-11-08T08:54:03Z</CreationTime>
      <Status>Available</Status>
      <CidrBlock>192.168.0.0/16</CidrBlock>
      <VSwitchIds>
        <VSwitchId>vsw-bp12mw1f8k3jgygk9bmlj</VSwitchId>
      </VSwitchIds>
      <RegionId>cn-hangzhou</RegionId>
      <Ipv6CidrBlock/>
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
				"ResourceGroupId":"rg-acfmxazb4ph6aiy",
				"UserCidrs":{
					"UserCidr":[]
				},
				"NatGatewayIds":{
					"NatGatewayIds":[]
				},
				"RouterTableIds":{
					"RouterTableIds":[
						"vtb-bp1krxxzp0c29fmontbal"
					]
				},
				"VpcId":"vpc-bp1qpo0kug3a20qqe9h7v",
				"VRouterId":"vrt-bp1jcg5cmxjbl9xgc58bw",
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
				"ResourceGroupId":"rg-acfmxazb4ph6aiy",
				"UserCidrs":{
					"UserCidr":[]
				},
				"NatGatewayIds":{
					"NatGatewayIds":[]
				},
				"RouterTableIds":{
					"RouterTableIds":[
						"vtb-bp1blq1oh0ybfnpm1bh20"
					]
				},
				"VpcId":"vpc-bp1aevy8sofi8mh1qc5cm",
				"VRouterId":"vrt-bp149ve7yeyvio4ncklxz",
				"CreationTime":"2018-11-08T08:54:03Z",
				"Status":"Available",
				"CidrBlock":"192.168.0.0/16",
				"VSwitchIds":{
					"VSwitchId":[
						"vsw-bp12mw1f8k3jgygk9bmlj"
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

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

