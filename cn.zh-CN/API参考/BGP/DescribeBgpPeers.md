# DescribeBgpPeers {#doc_api_Vpc_DescribeBgpPeers .reference}

使用DescribeBgpPeers查询指定地域下的BGP邻居。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeBgpPeers&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeBgpPeers|要执行的操作。

 取值： **DescribeBgpPeers**。

 |
|RegionId|String|是|cn-shanghai|BGP组所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|BgpGroupId|String|否|bgpg-2zev8h2wo414sfhjgdlhh|指定BGP组的ID。

 |
|BgpPeerId|String|否|bgp-2ze3un0ft1jd1xdppusul|BGP邻居的ID。

 |
|IsDefault|Boolean|否|false|是否是默认BGP组。

 |
|OwnerAccount|String|否|xxx@aliyun.com|所有者账号。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为1。

 |
|PageSize|Integer|否|1|分页查询时每页的行数，最大值为50，默认值为10。

 |
|RouterId|String|否|vrt-acfmxazb4ph6aiy|路由器的ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|BgpPeers| | |BGP邻居的详细信息。

 |
|Name|String|test|BGP邻居的名称。

 |
|PeerIpAddress|String|116.62.222.28|BGP邻居的IP地址。

 |
|AuthKey|String|!PWZ2wsq|BGP组的认证密钥。

 |
|RouterId|String|vbr-2zecmmvg5gvu8i4telkhw|BGP邻居的状态。

 |
|Status|String|active|BGP邻居的状态。

 |
|BgpGroupId|String|bgp-wz977wcrmb69axxxxxxxx|BGP组的ID。

 |
|BgpPeerId|String|bgp-wz977wcrmb69agdbab8s1|BGP邻居的ID。

 |
|BgpStatus|String|Established|BGP的连接状态。

 |
|Description|String|xxxxxxxxx|BGP组的描述。

 |
|EnableBfd|Boolean|true|是否开启了BFD协议。

 |
|Hold|String|30|保持时间。

 |
|IsFake|String|true|是否启用了Fake AS号。

 |
|Keepalive|String|10|保活时间。

 |
|LocalAsn|String|45104|本地ASN号

 |
|PeerAsn|String|active|BGP邻居的ASN。

 |
|RegionId|String|cn-shanghai|BGP组所属的地域ID。

 |
|RouteLimit|String|99|路由限制。

 |
|TotalCount|Integer|10|列表条条目数。

 |
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|2|每页包含多少条目。

 |
|RequestId|String|DE77A7F3-3B74-41C0-A5BC-CAFD188C28B6|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeBgpPeers
&RegionId=cn-shanghai
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<<?xml version="1.0" encoding="UTF-8" ?>
<DescribeBgpGroupsResponse>
	<TotalCount>2</TotalCount>
	<PageSize>10</PageSize>
	<RequestId>16DFA5E6-9771-41B7-B079-DD7C2DF49BE6</RequestId>
	<BgpPeers>
		<BgpPeer>
			<BgpGroupId>bgpg-2zev8h2wo414sfhjgdlhh</BgpGroupId>
			<LocalAsn>45104</LocalAsn>
			<PeerIpAddress>11.11.11.1</PeerIpAddress>
			<Hold>30</Hold>
			<Description></Description>
			<AuthKey></AuthKey>
			<IsFake>true</IsFake>
			<PeerAsn>234</PeerAsn>
			<Keepalive>10</Keepalive>
			<RouteLimit>99</RouteLimit>
			<BgpPeerId>bgp-2ze3un0ft1jd1xdppusul</BgpPeerId>
			<Name></Name>
			<Status>Available</Status>
			<BgpStatus></BgpStatus>
			<RouterId>vbr-2zecmmvg5gvu8i4telkhw</RouterId>
			<RegionId>cn-beijing</RegionId>
		</BgpPeer>
		<BgpPeer>
			<BgpGroupId>bgpg-2zev8h2wo414sfhjgdlhh</BgpGroupId>
			<LocalAsn>45104</LocalAsn>
			<PeerIpAddress>11.11.11.2</PeerIpAddress>
			<Hold>30</Hold>
			<Description></Description>
			<AuthKey></AuthKey>
			<IsFake>true</IsFake>
			<PeerAsn>234</PeerAsn>
			<Keepalive>10</Keepalive>
			<RouteLimit>99</RouteLimit>
			<BgpPeerId>bgp-2zeu54rbreqqzyb5bg1hq</BgpPeerId>
			<Name></Name>
			<Status>Available</Status>
			<BgpStatus></BgpStatus>
			<RouterId>vbr-2zecmmvg5gvu8i4telkhw</RouterId>
			<RegionId>cn-beijing</RegionId>
		</BgpPeer>
	</BgpPeers>
</DescribeBgpGroupsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"TotalCount":2,
	"PageSize":10,
	"RequestId":"16DFA5E6-9771-41B7-B079-DD7C2DF49BE6",
	"BgpPeers":{
		"BgpPeer":[
			{
				"BgpGroupId":"bgpg-2zev8h2wo414sfhjgdlhh",
				"LocalAsn":45104,
				"PeerIpAddress":"11.11.11.1",
				"Hold":30,
				"Description":"",
				"AuthKey":"",
				"IsFake":true,
				"PeerAsn":234,
				"Keepalive":10,
				"RouteLimit":99,
				"BgpPeerId":"bgp-2ze3un0ft1jd1xdppusul",
				"Name":"",
				"Status":"Available",
				"BgpStatus":"",
				"RouterId":"vbr-2zecmmvg5gvu8i4telkhw",
				"RegionId":"cn-beijing"
			},
			{
				"BgpGroupId":"bgpg-2zev8h2wo414sfhjgdlhh",
				"LocalAsn":45104,
				"PeerIpAddress":"11.11.11.2",
				"Hold":30,
				"Description":"",
				"AuthKey":"",
				"IsFake":true,
				"PeerAsn":234,
				"Keepalive":10,
				"RouteLimit":99,
				"BgpPeerId":"bgp-2zeu54rbreqqzyb5bg1hq",
				"Name":"",
				"Status":"Available",
				"BgpStatus":"",
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

