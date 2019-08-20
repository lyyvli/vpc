# DescribeVpnSslServerLogs {#doc_api_Vpc_DescribeVpnSslServerLogs .reference}

Views the logs of an SSL server.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=DescribeVpnSslServerLogs&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeVpnSslServerLogs|The name of this action. Value: **DescribeVpnSslServerLogs**.

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SSL server belongs. To query the region ID, call [DescribeRegions](~~36063~~).

 |
|VpnSslServerId|String|Yes|vss-bp155e9yclsg1xgq4\*\*\*\*|The ID of the SSL server.

 |
|From|Integer|No|2018020201|The start time of the log.

 |
|MinutePeriod|Integer|No|10|The cycle of the log.

 |
|PageNumber|Integer|No|1|The page number. Default value: **1**.

 |
|PageSize|Integer|No|10|The number of rows per page in the paged query. Maximum value: **50**. Default value: **10**.

 |
|To|Integer|No|2018020206|The end time of the log.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|Count|Integer|10|The number of log entries.

 |
|Data| |test|The array. Each item in the array is a log entry.

 |
|IsCompleted|Boolean|true|Indicates whether the queried log is accurate. Valid values:

 -   **true**: The queried log is accurate.
-   **false**: The queried log is inaccurate.

 |
|PageNumber|Integer|1|The current page number.

 |
|PageSize|Integer|1|The number of entries per page.

 |
|RequestId|String|5BE01CD7-5A50-472D-AC14-CA181C5C03BE|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeVpnSslServerLogs
&RegionId=cn-hangzhou
&VpnSslServerId=vss-bp155e9yclsg1xgq4****
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<DescribeVpnSslServerLogsResponse>
	  <Data></Data>
	  <PageNumber>1</PageNumber>
	  <Count>0</Count>
	  <PageSize>10</PageSize>
	  <IsCompleted>true</IsCompleted>
	  <RequestId>26641E42-66C7-4942-9FEC-F99213914F8F</RequestId>
</DescribeVpnSslServerLogsResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"Data":{
		"Logs":[]
	},
	"Count":0,
	"IsCompleted":true,
	"PageSize":10,
	"RequestId":"26641E42-66C7-4942-9FEC-F99213914F8F"
}
```

## Errors { .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|Forbidden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|You are not authorized to use this resource. Apply for the permission and try again.|
|403|Forbidden|User not authorized to operate on the specified resource.|You are not authorized to use this resource. For more information, open a ticket.|

