# DescribeBgpGroups {#doc_api_Vpc_DescribeBgpGroups .reference}

使用DescribeBgpGroups查询指定地域下的BGP组。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeBgpGroups&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeBgpGroups|要执行的操作。

 取值：**DescribeBgpGroups**。

 |
|RegionId|String|是|cn-shanghai|BGP组所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|BgpGroupId|String|否|bgpg-wz9f62v4fbg2gxxxxxxxx|BGP组的ID。

 |
|IsDefault|Boolean|否|false|是否为为默认BGP组。

 |
|OwnerAccount|String|否|1234abcd@aliyun.com|用户账号。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为1。

 |
|PageSize|Integer|否|1|分页查询时每页的行数，最大值为50，默认值为10。

 |
|RouterId|String|否|vrt-kojok19x3j0q6kx|BGP组关联的VBR的ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|TotalCount|Integer|10|列表条条目数。

 |
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|5|每页包含多少条目。

 |
|BgpGroups| | |BGP组的详细信息。

 |
|AuthKey|String|!PWZ2wsq|BGP组使用的密钥。

 |
|BgpGroupId|String|bgp-wz977wcrmb69axxxxxxxx|BGP组的ID。

 |
|Description|String|BGP组描述|BGP组的描述。

 |
|Hold|String|30|等待BGP消息传入的保持时间。如果超过保持时间还没有消息传入，则认为BGP邻居断开了连接。

 |
|IsFake|String|true|AS号是否为假。

 |
|Keepalive|String|10|保活时间。

 |
|LocalAsn|String|45104|本端AS号。

 |
|Name|String|BGP名称|BGP组的名称。

 |
|PeerAsn|String|1111|侧设备的AS号。

 |
|RegionId|String|cn-shanghai|BGP组所属的Region ID。Region ID的列表详见[地域和可用区](~~40654~~)。

 |
|RouteLimit|String|99|路由限制。

 |
|RouterId|String|vrt-bp1lhl0taikrteen80oxx|VBR的ID。

 |
|Status|String|active|BGP邻居的状态。

 |
|RequestId|String|1D0971B2-A35A-42C1-A44C-E91360C36C0B|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeBgpGroups
&RegionId=cn-shanghai
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeBgpGroupsResponse>
	  <TotalCount>1</TotalCount>
	  <PageSize>10</PageSize>
	  <RequestId>09E2C0FD-37FF-4737-80DF-517AC36D43DB</RequestId>
	  <BgpGroups>
		    <BgpGroup>
			      <BgpGroupId>bgpg-2zev8h2wo414sfhjgdlhh</BgpGroupId>
			      <LocalAsn>45104</LocalAsn>
			      <Hold>30</Hold>
			      <Description></Description>
			      <AuthKey></AuthKey>
			      <IsFake>true</IsFake>
			      <PeerAsn>234</PeerAsn>
			      <Keepalive>10</Keepalive>
			      <RouteLimit>99</RouteLimit>
			      <Name>Group1</Name>
			      <Status>Pending</Status>
			      <RouterId>vbr-2zecmmvg5gvu8i4telkhw</RouterId>
			      <RegionId>cn-beijing</RegionId>
		    </BgpGroup>
	  </BgpGroups>
</DescribeBgpGroupsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"TotalCount":1,
	"PageSize":10,
	"RequestId":"09E2C0FD-37FF-4737-80DF-517AC36D43DB",
	"BgpGroups":{
		"BgpGroup":[
			{
				"BgpGroupId":"bgpg-2zev8h2wo414sfhjgdlhh",
				"LocalAsn":45104,
				"Hold":30,
				"Description":"",
				"AuthKey":"",
				"IsFake":true,
				"PeerAsn":234,
				"Keepalive":10,
				"RouteLimit":99,
				"Name":"Group1",
				"Status":"Pending",
				"RouterId":"vbr-2zecmmvg5gvu8i4telkhw",
				"RegionId":"cn-beijing"
			}
		]
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|500|InternalError|The request processing has failed due to some unknown error.|请求处理由于某些未知错误失败。|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

