# DescribeFlowLogs {#doc_api_Vpc_DescribeFlowLogs .reference}

Queries a flow log.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=DescribeFlowLogs&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeFlowLogs|The name of this action. Value: **DescribeFlowLogs**.

 |
|RegionId|String|Yes|cn-qingdao|The ID of the region to which the flow log belongs. To query the region ID, call [DescribeRegions](~~36063~~).

 |
|FlowLogId|String|No|flowlog-m5evbtbptxxxxxxxxxxxx|The ID of the flow log.

 |
|FlowLogName|String|No|myFlowlog|The name of the flow log. The name must be 2 to 128 characters in length. It must start with a letter and can contain numbers, periods \(.\), underscores \(\_\), and hyphens \(-\). It cannot start with `http://` or `https://`.

 |
|LogStoreName|String|No|FlowLogStore|The Logstore that stores the captured traffic.

 |
|ProjectName|String|No|FlowLogProject|The Project that stores the captured traffic.

 |
|ResourceId|String|No|eni-askldfasxxxxxxxx|The ID of the resource whose traffic you want to capture.

 |
|ResourceType|String|No|NetworkInterface|The type of the resource whose traffic you want to capture. Valid values:

 -   NetworkInterface: ENI
-   VSwitch: all ENIs in the VSwitch
-   VPC: all ENIs in the VPC

 |
|TrafficType|String|No|All|The type of the traffic to be captured. Valid values:

 -   All: all traffic
-   Allow: traffic permitted by access control
-   Drop: traffic denied by access control

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description |
|---------|----|-------------|------------|
|FlowLogs| | |The flow log.

 |
|CreationTime|String|2018-07-24T13:00:52Z|The time when the flow log was created.

 |
|Description|String|abc|The description of the flow log.

 |
|FlowLogId|String|flowlog-m5evbtbptxxxxxxxxxxxx|The ID of the flow log.

 |
|FlowLogName|String|myFlowlog|The name of the flow log.

 |
|LogStoreName|String|FlowLogStore|The Logstore that stores the captured traffic.

 |
|ProjectName|String|FlowLogProject|The Project that stores the captured traffic.

 |
|RegionId|String|cn-qingdao|The region to which the flow log belongs.

 |
|RequestId|String|F7DDDC17-FA06-4AC2-8F35-59D2470FCFC1|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeFlowLogs
&RegionId=cn-qingdao
&FlowLogId=fl-m5evbtbptxxxxxxxxxxxx
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<DescribeFlowLogsResponse>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
</DescribeFlowLogsResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FExxxxx"
}
```

## Errors { .section}

