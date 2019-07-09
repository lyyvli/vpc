# DescribePhysicalConnectionLOA {#doc_api_Vpc_DescribePhysicalConnectionLOA .reference}

调用DescribePhysicalConnectionLOA查询物理专线LOA信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribePhysicalConnectionLOA)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribePhysicalConnectionLOA|要执行的操作。

 取值：**DescribePhysicalConnectionLOA**。

 |
|InstanceId|String|是|pc-bp1ca4wca27exxxxxxxx|物理专线实例ID。

 |
|RegionId|String|是|cn-hangzhou|物理专线部署的地域。

 |
|ClientToken|String|否|318BB676-0A2B-43A0-9AD8-F1D34E93750F|客户端Token鉴权。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PhysicalConnectionLOAType| | |物理专线LOA信息。

 |
|CompanyLocalizedName|String|company|施工单位名称。

 |
|CompanyName|String|test1234|需要部署物理专线的单位名称。

 |
|ConstructionTime|String|2019-02-26T08:00:00Z|施工进场时间。

 |
|InstanceId|String|pc-bp1ca4wca27exxxxxxxxx|物理专线实例ID。

 |
|LineCode|String|aaa111|运营商线路编码。

 |
|LineLabel|String|bbb222|机房楼内线缆标签。

 |
|LineType|String|MSTP|物理专线类型。

 取值：

 -   MSTP
-   Other
-   SDH
-   MPLSVPN
-   FIBRE

 |
|LoaUrl|String|http://pconn-loa.oss-cn-shenzhen.aliyuncs.com/1993847644011928\_pc-bp1ca4wca27ertsucaxn0\_cn-hangzhou-dg-a01.pdf?Expires=1551164196&OSSAccessKeyId=dCrRKgLiFLLHAo6k&Signature=d/w0BARgZ5uJHXODnjpr1oKIEC4%3D|LOA文件下载地址。

 |
|PMInfo| | |施工人员信息。

 |
|PMCertificateNo|String|12345671223|施工人员证件号码。

 |
|PMCertificateType|String|Other|施工人员证件类型。

 |
|PMContactInfo|String|18910010000|施工人员联系方式。

 |
|PMGender|String|Male|施工人员性别。

 |
|PMName|String|name|施工人员姓名。

 |
|SI|String|ctcu|入场施工单位。

 |
|Status|String|Available|专线状态。

 |
|RequestId|String|318BB676-0A2B-43A0-9AD8-F1D34E93750F|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribePhysicalConnectionLOA
&InstanceId=pc-bp1ca4wca27exxxxxxxx
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribePhysicalConnectionLOAResponse>
  <code>200</code>
  <data>
    <companyName>test1234</companyName>
    <constructionTime>2019-02-26T08:00:00Z</constructionTime>
    <instanceId>pc-bp1ca4wca27ertsucaxn0</instanceId>
    <lineType>MSTP</lineType>
    <loaUrl>http://pconn-loa.oss-cn-shenzhen.aliyuncs.com/1993847644011928_pc-bp1ca4wca27ertsucaxn0_cn-hangzhou-dg-a01.pdf?Expires=1551164196&amp;OSSAccessKeyId=dCrRKgLiFLLHAo6k&amp;Signature=d/w0BARgZ5uJHXODnjpr1oKIEC4%3D</loaUrl>
    <pmInfo>
      <nextPMIndex>1</nextPMIndex>
      <pmCertificateNo>1234567</pmCertificateNo>
      <pmCertificateType>Other</pmCertificateType>
      <pmContactInfo>18910010000</pmContactInfo>
      <pmGender>Male</pmGender>
      <pmName>test</pmName>
    </pmInfo>
    <si>ctcu</si>
    <status>Available</status>
  </data>
  <message>successful</message>
  <requestId>318BB676-0A2B-43A0-9AD8-F1D34E93750F</requestId>
  <success>true</success>
</DescribePhysicalConnectionLOAResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"message":"successful",
	"requestId":"318BB676-0A2B-43A0-9AD8-F1D34E93750F",
	"data":{
		"lineType":"MSTP",
		"status":"Available",
		"pmInfo":[
			{
				"pmContactInfo":"18910010000",
				"pmGender":"Male",
				"pmCertificateNo":"1234567",
				"pmCertificateType":"Other",
				"nextPMIndex":1,
				"pmName":"test"
			}
		],
		"instanceId":"pc-bp1ca4wca27ertsucaxn0",
		"constructionTime":"2019-02-26T08:00:00Z",
		"companyName":"test1234",
		"si":"ctcu",
		"loaUrl":"http://pconn-loa.oss-cn-shenzhen.aliyuncs.com/1993847644011928_pc-bp1ca4wca27ertsucaxn0_cn-hangzhou-dg-a01.pdf?Expires=1551164196&OSSAccessKeyId=dCrRKgLiFLLHAo6k&Signature=d/w0BARgZ5uJHXODnjpr1oKIEC4%3D"
	},
	"code":"200",
	"success":true
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

