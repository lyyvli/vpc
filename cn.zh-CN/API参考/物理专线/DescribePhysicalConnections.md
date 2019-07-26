# DescribePhysicalConnections {#doc_api_Vpc_DescribePhysicalConnections .reference}

调用DescribePhysicalConnections接口查询指定地域内的物理专线。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribePhysicalConnections&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribePhysicalConnections|要执行的操作。

 取值： **DescribePhysicalConnections** 。

 |
|RegionId|String|是|cn-hangzhou|物理专线所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|ClientToken|String|否|23243242rggyt|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个ASCII字符。

 |
|Filter.N.Key|String|否|1|过滤条件。N的取值为1-5。支持的过滤条件如下：

 -   **PhysicalConnectionId**：物理专线ID。
-   **AccessPointId**：接入点ID。
-   **Type**：专线类型。
-   **LineOperator**：物理专线的运营商。
-   **Spec**：物理专线的规格。
-   **Status**：物理专线的状态。
-   **Name**：物理专线的名称。

 一个过滤条件的多个值之间是or关系，只要与其中一个值吻合则视为符合该过滤条件。各个过滤条件之间为and关系，符合所有的过滤条件，才会进入最终查询结果中。

 |
|Filter.N.Value.N|RepeatList|否|1|对应过滤条件的取值。N的取值范围为1-5。

 |
|IncludeReservationData|Boolean|否|false|是否返回未生效订单。

 |
|PageNumber|Integer|否|10|列表的页码，默认值为1。

 |
|PageSize|Integer|否|1|分页查询时每页的行数，最大值为50，默认值为10。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PhysicalConnectionSet| | |物理专线的详细信息。

 |
|AccessPointId|String|eip-2zeerraiwb7uj6i0d0fo3|物理专线接入点的ID。

 |
|AdLocation|String|广东省深圳市南山区滨海大道xxx基地xx座 Ax-x Bxx|专线接入设备所在的物理位置。

 |
|Bandwidth|Long|10|物理专线的带宽。

 |
|BusinessStatus|String|Normal|物理专线的付费状态：

 -   Normal：正常。
-   FinancialLocked：欠费锁定。
-   SecurityLocked：因安全原因被锁定。

 |
|ChargeType|String|Prepaid|收费类型。

 |
|CircuitCode|String|longtel001|运营商为物理专线提供的电路编码。

 |
|CreationTime|String|2017-06-08T12:20:55|物理专线的创建时间。

 |
|Description|String|物理专线|物理专线的描述。

 |
|EnabledTime|String|2017-06-08T12:20:55|物理专线的开通时间。

 |
|EndTime|String|2019-02-25T11:01:04Z|到期时间。

 |
|HasReservationData|String|true|是否有订购消息。

 |
|LineOperator|String|CT|提供接入物理线路的运营商：

 -   CT：中国电信。
-   CU：中国联通。
-   CM：中国移动。
-   CO：中国其他 。
-   Equinix：Equinix 。
-   Other：境外其他 。

 |
|LoaStatus|String|Available|LOA状态。

 |
|Name|String|name|物理专线的名称。

 |
|PeerLocation|String|浙江省---vfjdbg\_21e|本地数据中心的地理位置。

 |
|PhysicalConnectionId|String|pc-119mfjzm7|物理专线的ID。

 |
|PortNumber|String|80|专线接入设备的端口号。

 |
|PortType|String|1000Base-T|物理专线接入端口类型：

 -   100Base-T：百兆电口 。
-   1000Base-T（默认值）：千兆电口。
-   1000Base-LX：千兆单模光口（10千米）。
-   10GBase-T：万兆电口。
-   10GBase-LR：万兆单模光口（10千米）。

 |
|RedundantPhysicalConnectionId|String|pc-119mfjzm7|冗余物理专线的ID。

 |
|ReservationActiveTime|String|2019-02-25T11:01:04Z|续费生效时间。

 |
|ReservationInternetChargeType|String|PayByBandwidth|续费类型。

 |
|ReservationOrderType|String|RENEW|续费订单类型。

 |
|Spec|String|Large|物理专线的规格。

 |
|Spec|String|Large|物理专线的规格。

 |
|Status|String|Initial|物理专线的状态：

 -   **Initial**：申请中。
-   **Approved**：审批通过 。
-   **Allocating**：正在分配资源。
-   **Allocated**：接入施工中。
-   **Confirmed**：等待用户确认。
-   **Enabled**：已开通。
-   **Rejected**：申请被拒绝。
-   **Canceled**：已取消 。
-   **Allocation Failed**：资源分配失败。
-   **Terminated**：已终止。

 |
|Type|String|VPC|物理专线的类型。默认值为**VPC**。

 |
|TotalCount|Integer|10|列表条条目数。

 |
|PageNumber|Integer|10|当前页码。

 |
|PageSize|Integer|10|每页包含多少条目。

 |
|RequestId|String|EEC8EAB1-F299-4F5C-8E54-0A3129164C27|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribePhysicalConnections
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribePhysicalConnectionsResponse>
	  <PageNumber>1</PageNumber>
	  <TotalCount>1</TotalCount>
	  <PageSize>10</PageSize>
	  <RequestId>7C07B0AF-4FC0-4BB2-9667-F75812824BCD</RequestId>
	  <PhysicalConnectionSet>
		    <PhysicalConnectionType>
			      <Type>VPC</Type>
			      <PhysicalConnectionId>pc-2zeoaxkq3jot5p71qcnuy</PhysicalConnectionId>
			      <PeerLocation>XXX-XX区--XXX路</PeerLocation>
			      <CreationTime>2017-12-13T02:28:42Z</CreationTime>
			      <Name>TEST</Name>
			      <Status>Enabled</Status>
			      <AdLocation>XXX--XX-XXX机房XX机柜XXU</AdLocation>
			      <EnabledTime>2017-12-18T04:01:30Z</EnabledTime>
			      <BusinessStatus>Normal</BusinessStatus>
			      <LineOperator>CT</LineOperator>
			      <PortNumber>1/1/4</PortNumber>
			      <AccessPointId>ap-cn-beijing-dx-A</AccessPointId>
			      <PortType>100Base-T</PortType>
			      <Bandwidth>2</Bandwidth>
		    </PhysicalConnectionType>
	  </PhysicalConnectionSet>	
</DescribePhysicalConnectionsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":1,
	"PageSize":10,
	"RequestId":"7C07B0AF-4FC0-4BB2-9667-F75812824BCD",
	"PhysicalConnectionSet":{
		"PhysicalConnectionType":[
			{
				"Type":"VPC",
				"PhysicalConnectionId":"pc-2zeoaxkq3jot5p71qcnuy",
				"PeerLocation":"XXX-XX区--XXX路",
				"CreationTime":"2017-12-13T02:28:42Z",
				"Name":"TEST",
				"Status":"Enabled",
				"AdLocation":"XXX--XX-XXX机房XX机柜XXU",
				"EnabledTime":"2017-12-18T04:01:30Z",
				"BusinessStatus":"Normal",
				"LineOperator":"CT",
				"PortNumber":"1/1/4",
				"AccessPointId":"ap-cn-beijing-dx-A",
				"PortType":"100Base-T",
				"Bandwidth":2
			}
		]
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidFilterKey.ValueNotSupported|Specified filter key is not supported: Filter.X.key|该过滤器的Key不支持：Filter.X.key|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

