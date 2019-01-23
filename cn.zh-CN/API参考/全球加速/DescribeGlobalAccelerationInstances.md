# DescribeGlobalAccelerationInstances {#doc_api_951866 .reference}

调用DescribeGlobalAccelerationInstances接口查询已创建的全球加速实例列表。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeGlobalAccelerationInstances)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeGlobalAccelerationInstances|要执行的操作。

 取值： **DescribeGlobalAccelerationInstances**。

 |
|RegionId|String|是|cn-hangzhou|全球加速实例所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|BandwidthType|String|否|Exclusive|实例带宽类型，取值：

 -   **Sharing**：查询带宽共享型实例
-   **Exclusive**（默认值）：查询带宽独享型实例

 |
|GlobalAccelerationInstanceId|String|否|ga-234sljmxazb4|全球加速实例的ID。

 |
|IncludeReservationData|Boolean|否|false|是否包含未生效的订购数据，默认是**false**。

 |
|IpAddress|String|否|12.34.56.78|全球加速实例公网 IP。

 |
|Name|String|否|GA-1|全球加速实例的名称。

 |
|PageNumber|Integer|否|10|列表的页码，默认值为1。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。

 |
|ServerId|String|否|i-sxjbl9xgc|加速的后端服务器的实例ID。

 |
|ServiceLocation|String|否|china-mainland|被加速的服务的所属区域。取值：

 -   **china-mainland**：中国大陆
-   **north-america**：北美
-   **asia-pacific**：亚太
-   **europe**：欧洲

 |
|Status|String|否|Available|全球加速实例状态，取值：

 -   **Available**：可用
-   **Inuse**：已分配
-   **Associating**：绑定中
-   **Unassociating**：解绑中

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|GlobalAccelerationInstances| | |全球加速实例列表的详细信息。

 |
|└AccelerationLocation|String|china-mainland|全球加速实例的加速区域。

 |
|└BackendServers| | |全球加速实例的后端服务器的详细信息。

 |
|└RegionId|String|cn-Beijing|后端服务器所在的地域。

 |
|└ServerId|String|i-2zeg83zvn5d4ed4y2rxx|后端服务器ID。

 |
|└ServerIpAddress|String|172.17.109.xxx|后端服务器IP地址。

 |
|└ServerType|String|EcsInstance|后端服务器类型。

 |
|└Bandwidth|String|10|全球加速实例的带宽峰值。

 |
|└BandwidthType|String|Exclusive|实例的带宽类型。

 |
|└ChargeType|String|PrePaid|全球加速实例的付费类型：

 -   **PrePaid**：预付费
-   **PostPaid**：后付费

 |
|└CreationTime|String|2018-07-05T03:39:31Z|全球加速实例的创建时间，UTC时间。

 |
|└Description|String|apiDescription|全球加速实例的描述。

 |
|└ExpiredTime|String|2018-08-05T16:00Z|实例过期时间。

 |
|└GlobalAccelerationInstanceId|String|ga-bp1x99kj7kl1ziw5xuwb5|全球加速实例的ID。

 |
|└InternetChargeType|String|PayByBandwidth|全球加速实例的计费方式。

 |
|└IpAddress|String|47.98.99.xxx|独享型全球加速实例的公网IP。

 |
|└Name|String|instanceName|全球加速实例的名称。

 |
|└PublicIpAddresses| | |公网IP。

 |
|└AllocationId|String|12.34.56.78|全球加速实例的公网IP ID。

 |
|└IpAddress|String|12.34.56.78|全球加速实例的公网IP。

 |
|└RegionId|String|cn-hangzhou|全球加速实例所在的地域。

 |
|└ServiceLocation|String|china-mainland|全球加速实例的服务区域。

 |
|└Status|String|InUse|全球加速实例的状态。

 |
|TotalCount|Integer|1|列表条条目数。

 |
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|10|每页包含多少条目。

 |
|RequestId|String|6B4EE38D-C75B-4E1F-844E-863A94430676|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeGlobalAccelerationInstances
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeGlobalAccelerationInstancesResponse>
  <PageNumber>1</PageNumber>
  <TotalCount>1</TotalCount>
  <PageSize>10</PageSize>
  <RequestId>6B4EE38D-C75B-4E1F-844E-863A94430676</RequestId>
  <GlobalAccelerationInstances>
    <GlobalAccelerationInstance>
      <ChargeType>PrePaid</ChargeType>
      <GlobalAccelerationInstanceId>ga-bp1x99kj7kl1ziw5xuwb5</GlobalAccelerationInstanceId>
      <HasReservationData>false</HasReservationData>
      <Description/>
      <BackendServers>
        <BackendServer>
          <ServerId>i-2zeg83zvn5d4ed4y2r4c</ServerId>
          <RegionId>cn-beijing</RegionId>
          <ServerType>EcsInstance</ServerType>
          <ServerIpAddress>172.17.109.xxx</ServerIpAddress>
        </BackendServer>
      </BackendServers>
      <IpAddress>47.98.99.xxx</IpAddress>
      <InternetChargeType>PayByBandwidth</InternetChargeType>
      <Name/>
      <BandwidthType>Exclusive</BandwidthType>
      <CreationTime>2018-07-05T03:39:31Z</CreationTime>
      <Status>InUse</Status>
      <ServiceLocation>china-mainland</ServiceLocation>
      <RegionId>cn-hangzhou</RegionId>
      <AccelerationLocation>china-mainland</AccelerationLocation>
      <OperationLocks/>
      <ExpiredTime>2018-08-05T16:00Z</ExpiredTime>
      <PublicIpAddresses/>
      <Bandwidth>10</Bandwidth>
    </GlobalAccelerationInstance>
  </GlobalAccelerationInstances>
</DescribeGlobalAccelerationInstancesResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":1,
	"PageSize":10,
	"RequestId":"6B4EE38D-C75B-4E1F-844E-863A94430676",
	"GlobalAccelerationInstances":{
		"GlobalAccelerationInstance":[
			{
				"ChargeType":"PrePaid",
				"GlobalAccelerationInstanceId":"ga-bp1x99kj7kl1ziw5xuwb5",
				"HasReservationData":false,
				"Description":"",
				"BackendServers":{
					"BackendServer":[
						{
							"ServerId":"i-2zeg83zvn5d4ed4y2r4c",
							"RegionId":"cn-beijing",
							"ServerType":"EcsInstance",
							"ServerIpAddress":"172.17.109.xxx"
						}
					]
				},
				"IpAddress":"47.98.99.xxx",
				"InternetChargeType":"PayByBandwidth",
				"Name":"",
				"BandwidthType":"Exclusive",
				"CreationTime":"2018-07-05T03:39:31Z",
				"Status":"InUse",
				"ServiceLocation":"china-mainland",
				"RegionId":"cn-hangzhou",
				"AccelerationLocation":"china-mainland",
				"OperationLocks":{
					"LockReason":[]
				},
				"ExpiredTime":"2018-08-05T16:00Z",
				"PublicIpAddresses":{
					"PublicIpAddress":[]
				},
				"Bandwidth":"10"
			}
		]
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

