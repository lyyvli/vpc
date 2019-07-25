# DescribeVSwitchAttributes {#doc_api_Vpc_DescribeVSwitchAttributes .reference}

调用DescribeVSwitchAttributes接口查询指定交换机的配置信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeVSwitchAttributes&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeVSwitchAttributes|要执行的操作。 取值： **DescribeVSwitchAttributes**。

 |
|RegionId|String|是|cn-hangzhou|路由表所属的VPC的地域ID。

 |
|VSwitchId|String|是|vsw-25naue4g\*\*\*\*|要查询的交换机ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|AvailableIpAddressCount|Long|12|可用IP数量。

 |
|CidrBlock|String|192.168.0.1/24|交换机的私网地址范围。

 |
|CreationTime|String|2017-08-22T10:40:25Z|交换机的创建时间。

 |
|Description|String|abc|交换机的描述。

 |
|Ipv6CidrBlock|String|2408:4004:0:29xx::/64|交换机的IPv6网段。

 |
|IsDefault|Boolean|false|是否是默认交换机。

 |
|NetworkAclId|String|1|网络ACL规则。

 |
|RequestId|String|7B48B4B9-1EAD-469F-B488-594DAB4B6A1A|请求ID。

 |
|ResourceGroupId|String|rg-acfmxazb4ph\*\*\*\*|资源组ID。

 |
|RouteTable| | |交换机的路由表信息。

 |
|RouteTableId|String|vtb-bp145q7glnuzdv\*\*\*\*|交换机关联的路由表ID。

 |
|RouteTableType|String|System|路由表类型：

 -   **System**：系统路由表。
-   **Custom**：自定义路由表。

 |
|Status|String|Pending|交换机的状态，取值：

 -   **Pending**：配置中。
-   **Available**：可用。

 |
|VSwitchId|String|vsw-25b7pv15t\*\*\*\*|交换机的ID。

 |
|VSwitchName|String|test|交换机名称。

 |
|VpcId|String|vpc-257gq642n\*\*\*\*|交换机所属的VPC ID。

 |
|ZoneId|String|cn-beijing-a|交换机的所属可用区。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeVSwitchAttributes
&VSwitchId=vsw-25naue4g****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeVSwitchAttributesResponse>
	  <RouteTable>
		    <RouteTableId>vtb-hp3ngu1hkdutfakqn****</RouteTableId>
		    <RouteTableType>System</RouteTableType>
	  </RouteTable>
	  <Description></Description>
	  <IsDefault>false</IsDefault>
	  <AvailableIpAddressCount>251</AvailableIpAddressCount>
	  <ResourceGroupId>rg-acfmy45w7w2****</ResourceGroupId>
	  <ZoneId>cn-huhehaote-a</ZoneId>
	  <VSwitchId>vsw-hp3lyltb1dosj540y****</VSwitchId>
	  <VpcId>vpc-hp34hflqqsjh3a3q7****</VpcId>
	  <CreationTime>2019-01-07T04:54:14Z</CreationTime>
	  <Status>Available</Status>
	  <CidrBlock>192.168.0.0/24</CidrBlock>
	  <RequestId>A31F062D-81F0-48BC-9771-915D6622D26A</RequestId>
	  <VSwitchName>doc1</VSwitchName>
	  <Ipv6CidrBlock>2408:4004:0:2900::/64</Ipv6CidrBlock>
	  <CloudResources></CloudResources>
</DescribeVSwitchAttributesResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RouteTable":{
		"RouteTableId":"vtb-hp3ngu1hkdutfakqn****",
		"RouteTableType":"System"
	},
	"Description":"",
	"IsDefault":false,
	"AvailableIpAddressCount":251,
	"ResourceGroupId":"rg-acfmy45w7w2****",
	"ZoneId":"cn-huhehaote-a",
	"VSwitchId":"vsw-hp3lyltb1dosj540y****",
	"VpcId":"vpc-hp34hflqqsjh3a3q7****",
	"CreationTime":"2019-01-07T04:54:14Z",
	"Status":"Available",
	"CidrBlock":"192.168.0.0/24",
	"RequestId":"A31F062D-81F0-48BC-9771-915D6622D26A",
	"Ipv6CidrBlock":"2408:4004:0:2900::/64",
	"VSwitchName":"doc1",
	"CloudResources":{
		"CloudResourceSetType":[]
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

