# CreateFlowLog {#doc_api_Vpc_CreateFlowLog .reference}

Creates a flow log.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=CreateFlowLog&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreateFlowLog|The name of this action. Value: **CreateFlowLog**.

 |
|LogStoreName|String|Yes|FlowLogStore|The Logstore that stores the captured traffic.

 |
|ProjectName|String|Yes|FlowLogProject|The Project that stores the captured traffic.

 |
|RegionId|String|Yes|cn-qingdao|The region to which the flow log belongs. To query the region ID, call [DescribeRegions](~~36063~~).

 |
|ResourceId|String|Yes|eni-askldfasxxxxxxxx|The ID of the resource whose traffic you want to capture.

 |
|ResourceType|String|Yes|NetworkInterface|The type of the resource whose traffic you want to capture. Valid Values:

 -   NetworkInterface: ENI
-   VSwitch: all ENIs in the VSwitch
-   VPC: all ENIs in the VPC

 |
|TrafficType|String|Yes|all|The type of the traffic to be captured. Valid values:

 -   All: all traffic
-   Allow: traffic permitted by access control
-   Drop: traffic denied by access control

 |
|Description|String|No|This is my Flowlog.|The description of the flow log. The description must be 2 to 256 characters in length. It must start with a letter, but cannot start with `http://` or `https://`.

 |
|FlowLogName|String|No|myFlowlog|The name of the flow log. The name must be 2 to 128 characters in length. It must start with a letter and can contain numbers, periods \(.\), underscores \(\_\), and hyphens \(-\). It cannot start with `http://` or `https://`.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|FlowLogId|String|flowlog-m5evbtbptxxxxxxxxxxxx|The ID of the flow log.

 |
|RequestId|String|54B48E3D-DF70-471B-AA93-08E683A1B457|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateFlowLog
&LogStoreName=FlowLogStore
&ProjectName=FlowLogProject
&RegionId=cn-qingdao
&ResourceId=eni-askldfasxxxxxxxx
&ResourceType=NetworkInterface
&TrafficType=all
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<CreateFlowLogResponse>
      <RequestId>62172DD5-6BAC-45DF-8D44-xxxxxxxx</RequestId>
      <FlowLogId>flowlog-m5evbtbptxxxxxxxxxxxx</FlowLogId>
</CreateFlowLogResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"62172DD5-6BAC-45DF-8D44-xxxxxxxx",
	"FlowLogId":"flowlog-m5evbtbptxxxxxxxxxxxx"
}
```

## Errors { .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|INVALID\_PARAMETER|The parameter invalid.|The specified parameter is invalid.|
|400|MissingParameter|Missing mandatory parameter|One or more mandatory parameters are missing.|

