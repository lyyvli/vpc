# DescribeExpressCloudConnections {#doc_api_Vpc_DescribeExpressCloudConnections .reference}

调用DescribeExpressCloudConnections查询某个区域的高速上云服务列表。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeExpressCloudConnections)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeExpressCloudConnections|要执行的操作。

 取值：**DescribeExpressCloudConnections**

 |
|RegionId|String|是|cn-hangzhou|地域ID。

 |
|Filter.N.Key|String|否|2|过滤条件。

 N的取值为1-5，支持的过滤条件如下：

 -   eccid：高速上云连接ID。
-   bandwidth：高速上云连接带宽。
-   Status：高速上云连接的状态。
-   Name：高速上云连接的名称。

 一个过滤条件的多个值之间是或者关系，只要与其中一个值吻合则视为符合该过滤条件。各个过滤条件之间为和关系，符合所有的过滤条件，才会进入最终查询结果中。

 |
|Filter.N.Value.N|RepeatList|否|3|对应过滤条件的取值。N的取值范围为1-5。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为1。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|ExpressCloudConnectionSet| | |高速上云服务信息。

 |
|└ApplicationBandwidth|String|3|申请单带宽。

 |
|└ApplicationId|String|1557820353902123884|申请单ID。

 |
|└ApplicationStatus|String|Initial|申请单状态。

 |
|└ApplicationType|String|Create|申请单类型。

 |
|└Bandwidth|Integer|10|高速上云连接的带宽， 单位Mbps。

 取值：**2|4|6|8|10|20|50|100|200|500|1000|10000|40000**

 |
|└BusinessStatus|String|Normal|实例的付费状态。

 |
|└ChargeType|String|Prepaid|付费类型。

 |
|└CircuitCode|String|longtel001|电路码。

 |
|└ContactMail|String|XXX@example.com|申请高速上云连接的联系人邮件。

 |
|└ContactTel|String|132\*\*\*\*\*\*\*\*|申请高速上云服务的联系人电话。

 |
|└Description|String|ecc|高速上云服务的描述信息。

 长度为 2-256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 |
|└Distance|Integer|100|专线距离。

 |
|└EndTime|String|2019-02-25T11:01:04Z|专线到期时间。

 |
|└GmtCreate|String|2019-05-14T15:52Z|高速上云服务实例的创建时间。

 |
|└GmtModify|String|2019-05-14T16:52Z|高速上云服务实例的修改时间。

 |
|└HasReservationData|String|true|实例是否有续费。

 |
|└IDCardNo|String|321283201002102345|申请高速上云服务的联系人身份证号。

 |
|└IdcSP|String|CU|IDC网络服务商。

 |
|└InstanceId|String|ecc-bp1t9osmuln1vxfpt6gy8|实例ID。

 |
|└Isp|String|CU|专线服务商。

 |
|└Name|String|doctest|高速上云服务的实例名称。

 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://` 或`https://`开头。

 |
|└PeerCity|String|杭州|所在城市。

 |
|└PeerLocation|String|XX区XX大厦XX栋5楼|本地数据中心的地理位置。

 需要精确到楼层。

 |
|└PortType|String|100Base-T|物理专线接入端口类型，取值：

 -   100Base-T：百兆电口
-   1000Base-T（默认值）：千兆电口
-   1000Base-LX：千兆单模光口（10千米）
-   10GBase-T：万兆电口
-   10GBase-LR：万兆单模光口（10千米）

 |
|└RedundantEccId|String|ecc-xxxxxx|冗余高速上云服务专线实例ID。

 |
|└ReservationActiveTime|String|2019-02-25T11:01:04Z|续费启用时间。

 |
|└ReservationBandwidth|String|200|续费带宽。

 |
|└ReservationInternetChargeType|String|PayByBandwidth|续费付费类型。

 |
|└ReservationOrderType|String|RENEW|续费订单类型。

 |
|└Status|String|Initial|高速上云服务实例状态。

 |
|└Type|String|local|专线类型。

 |
|└VirtualBorderRouterModels| | |VBR信息。

 |
|└AccessPointId|String|ap-xxxx|接入点。

 |
|└InstanceId|String|vbr-xxxx|VBR实例ID。

 |
|└PhysicalConnectionId|String|pc-xxxx|物理专线的实例ID。

 |
|PageNo|Integer|2|分页查询时的页码。

 |
|PageSize|Integer|3|分页查询时设置的每页行数。

 |
|RequestId|String|6BF11256-9725-4C07-95F9-EF0F32B687E8|请求ID。

 |
|TotalCount|Integer|10|高速上云服务实例总数量。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeExpressCloudConnections
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeExpressCloudConnections>
  <TotalCount>1</TotalCount>
  <ExpressCloudConnectionSet>
    <ExpressCloudConnectionType>
      <HasReservationData>false</HasReservationData>
      <Type/>
      <ServiceProvider/>
      <InstanceId>ecc-bp1t9osmuln1vxfpt6gy8</InstanceId>
      <IdcSP>CU</IdcSP>
      <ApplicationId>1557820353902123884</ApplicationId>
      <BusinessStatus>Normal</BusinessStatus>
      <ApplicationBandwidth>3</ApplicationBandwidth>
      <ContactMail>XX@example.com</ContactMail>
      <ContactTel>13222312121</ContactTel>
      <PortType>100Base-T</PortType>
      <Bandwidth>3</Bandwidth>
      <GmtModify/>
      <ChargeType/>
      <ApplicationType>Create</ApplicationType>
      <Description>ecc</Description>
      <IDCardNo>321283201002102345</IDCardNo>
      <PeerCity>杭州</PeerCity>
      <GmtCreate>2019-05-14T15:52Z</GmtCreate>
      <PeerLocation>XX区XX大厦XX栋5楼</PeerLocation>
      <Name>doctest</Name>
      <CircuitCode/>
      <Status>Initial</Status>
      <RedundantEccId/>
      <Isp/>
      <ApplicationStatus>Initial</ApplicationStatus>
      <VirtualBorderRouterModels/>
      <EndTime/>
    </ExpressCloudConnectionType>
  </ExpressCloudConnectionSet>
  <PageSize>10</PageSize>
  <PageNo>1</PageNo>
  <RequestId>6BF11256-9725-4C07-95F9-EF0F32B687E8</RequestId>
</DescribeExpressCloudConnections>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"TotalCount":1,
	"PageSize":10,
	"ExpressCloudConnectionSet":{
		"ExpressCloudConnectionType":[
			{
				"HasReservationData":false,
				"ServiceProvider":"",
				"Type":"",
				"InstanceId":"ecc-bp1t9osmuln1vxfpt6gy8",
				"ApplicationId":"1557820353902123884",
				"IdcSP":"CU",
				"BusinessStatus":"Normal",
				"ApplicationBandwidth":3,
				"ContactMail":"XX@example.com",
				"ContactTel":"13222312121",
				"PortType":"100Base-T",
				"GmtModify":"",
				"Bandwidth":3,
				"ChargeType":"",
				"ApplicationType":"Create",
				"Description":"ecc",
				"IDCardNo":"321283201002102345",
				"PeerCity":"杭州",
				"GmtCreate":"2019-05-14T15:52Z",
				"PeerLocation":"XX区XX大厦XX栋5楼",
				"Name":"doctest",
				"CircuitCode":"",
				"Status":"Initial",
				"RedundantEccId":"",
				"Isp":"",
				"ApplicationStatus":"Initial",
				"VirtualBorderRouterModels":{
					"VirtualBorderRouterModel":[]
				},
				"EndTime":""
			}
		]
	},
	"RequestId":"6BF11256-9725-4C07-95F9-EF0F32B687E8",
	"PageNo":1
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

