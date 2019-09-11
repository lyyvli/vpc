# DeleteFlowLog {#doc_api_Vpc_DeleteFlowLog .reference}

Deletes a flow log.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=DeleteFlowLog&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteFlowLog|The name of this action. Value: **DeleteFlowLog**.

 |
|FlowLogId|String|Yes|fl-m5evbtbptxxxxxxxxxxxx|The ID of the flow log.

 |
|RegionId|String|Yes|cn-qingdao|The ID of the region to which the flow log belongs. To query the region ID, call [DescribeRegions](~~36063~~).

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|F7DDDC17-FA06-4AC2-8F35-59D2470FCFC1|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DeleteFlowLog
&RegionId=cn-qingdao
&FlowLogId=fl-m5evbtbptxxxxxxxxxxxx
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<DeleteFlowLog>
        <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
</DeleteFlowLog>
```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FExxxxx"
}
```

## Errors { .section}

