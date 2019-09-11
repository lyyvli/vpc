# DeactiveFlowLog {#doc_api_Vpc_DeactiveFlowLog .reference}

Deactivates a flow log to stop capturing the traffic of the specified resource.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=DeactiveFlowLog&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeactiveFlowLog|The name of this action. Value: **DeactiveFlowLog**.

 |
|FlowLogId|String|Yes|fl-m5evbtbptxxxxxxxxxxxx|The ID of the flow log.

 |
|RegionId|String|Yes|cn-qingdao|The ID of the region of the flow log. To query the region ID, call [DescribeRegions](~~36063~~).

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|F7DDDC17-FA06-4AC2-8F35-59D2470FCFC1|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DeactiveFlowLog
&RegionId=cn-qingdao
&FlowLogId=fl-m5evbtbptxxxxxxxxxxxx
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<DeactiveFlowLog>
       <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
</DeactiveFlowLog>
```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FExxxxx"
}
```

## Errors { .section}

