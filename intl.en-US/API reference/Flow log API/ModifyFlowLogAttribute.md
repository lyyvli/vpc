# ModifyFlowLogAttribute {#doc_api_Vpc_ModifyFlowLogAttribute .reference}

Modifies the name and description of a flow log.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=ModifyFlowLogAttribute&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|ModifyFlowLogAttribute|The name of this action. Value: **ModifyFlowLogAttribute**.

 |
|FlowLogId|String|Yes|flowlog-m5evbtbptxxxxxxxxxxxx|The ID of the flow log.

 |
|RegionId|String|Yes|cn-qingdao|The ID of the region to which the flow log belongs. To query the region ID, call [DescribeRegions](~~36063~~).

 |
|Description|String|No|This is my Flowlog.|The description of the flow log. The description must be 2 to 256 characters in length. It must start with a letter, but cannot start with `http://` or `https://`.

 |
|FlowLogName|String|No|myFlowlog|The name of the flow log. The name must be 2 to 128 characters in length. It must start with a letter and can contain numbers, periods \(.\), underscores \(\_\), and hyphens \(-\). It cannot start with `http://` or `https://`.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|F7DDDC17-FA06-4AC2-8F35-59D2470FCFC1|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyFlowLogAttribute
&RegionId=cn-qingdao
&FlowLogId=flowlog-m5evbtbptxxxxxxxxxxxx
&FlowLogName=myFlowlog
&<Commonparameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<ModifyFlowLogAttributeResponse>
	  <RequestId>62172DD5-6BAC-45DF-8D44-xxxxxxxx</RequestId>
	  <FlowLogId>flowlog-m5evbtbptxxxxxxxxxxxx</FlowLogId>
</ModifyFlowLogAttributeResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"62172DD5-6BAC-45DF-8D44-xxxxxxxx",
	"FlowLogId":"flowlog-m5evbtbptxxxxxxxxxxxx"
}
```

## Errors { .section}

