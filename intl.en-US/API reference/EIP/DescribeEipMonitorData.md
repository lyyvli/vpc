# DescribeEipMonitorData {#reference_i4w_xmt_ndb .reference}

Queries the monitoring data of an EIP.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|DescribeEipMonitorData| The name of this action. Value:

 DescribeEipMonitorData

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the EIP belongs.|
|AllocationId|Integer|Yes|2017-01-05T01:05:10Z|The ID of the EIP instance.|
|StartTime|String|Yes|2017-01-05T02:05:05Z| The start time to retrieve data. This parameter takes the ISO8601 format and is output in UTC+8. Format: YYYY-MM-DDThh:mm:ssZ.

 If ss is not 00, the next minute is automatically used as the start time.

 |
|EndTime|String|Yes|2017-01-05T01:05:10Z| The end time to retrieve data.This parameter takes the ISO8601 format and is output in UTC+8. Format: YYYY-MM-DDThh:mm:ssZ.

 If ss is not 00, the next minute is automatically used as the end time.

 |
|Period|Integer|No|60| The time length in seconds of each point of monitoring data. Default value: 60. Valid values:

 60|600|3600

 **Note:** The value of \(EndTime – StartTime\)/ Period must be larger than 200, that is, up to 200 points of monitoring data are returned. If the value of \(EndTime – StartTime\) is smaller than 200, only the monitoring data collected at the start time is returned.

 |

## Response parameters {#section_knb_y6y_a7y .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|EipMonitorDatas| | | A list of EIP monitoring data.

 |
|└EipBandwidth|Integer|10| The value of the bandwidth: EipFlow/60. Unit: Bps.

 |
|└EipFlow|Integer|675| The sum of the inbound and outbound bandwidth.

 |
|└EipPackets|Integer|3434| The number of packets.

 |
|└EipRX|Integer|122| The inbound bandwidth. Unit: bytes.

 |
|└EipTX|Integer|343| The outbound bandwidth. Unit: bytes.

 |
|└TimeStamp|String|2010-01-21T09:50:23Z| The timestamp of the query in ISO8601 format. Example value: 2018-12-20T03:14:00Z.

 |
|RequestId|String|C8B26B44-0189-443E-9816-D951F59623A9| The ID of the request.

 |

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}
https://vpc.aliyuncs.com/?Action=DescribeEipMonitorData
&AllocationId=eip-2578g5v5a
&StartTime=2014-10-29T23:00:00Z
&EndTime=2014-10-30T08:00:00Z
&CommonParameters
```

 **Response example** 

XML format

```
<? xml version="1.0" encoding="UTF-8" ? >
<DescribeEipMonitorDataResponse>
<RequestId>C8B26B44-0189-443E-9816-D951F59623A9</RequestId>
<EipMonitorDatas>
    <EipMonitorData>
            <EipRX>122</EipRX>
            <EipTX>343</EipTX>
            <EipFlow>675</EipFlow>
            <EipPackets>3434</EipPackets>
            <EipBandwidth>10</EipBandwidth>
            <TimeStamp>2010-01-21T09:50:23Z</TimeStamp>
       </EipMonitorData>
    </EipMonitorDatas>
</DescribeEipMonitorDataResponse>
```

JSON format

```
{
  "RequestId": "C8B26B44-0189-443E-9816-D951F59623A9",
  "EipMonitorDatas": {
    "EipMonitorData": [
      {
        "EipRX": "122",
        "EipTX": "343",
        "EipFlow": "675",
        "EipPackets": "3434",
        "EipBandwidth": "10",
        "IntranetFlow": 675,
        "IntranetBandwidth": 10,
        "TimeStamp": "2010-01-21T09:50:23Z"
      }
    ]
  }
}
```

## Error codes { .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidInstanceId.NotFound|The InstanceId provided does not exist in our records.|The specified ECS instance does not exist \(The specified ECS instance is not under the VPC\).|
|400|InvalidStartTime.Malformed|The specified parameter "StartTime" is not valid.|The specified start time is invalid.|
|400|InvalidEndTime.Malformed|The specified parameter "EndTime" is not valid.|The specified end time is invalid.|
|400|InvalidPeriod.ValueNotSupported|The specified parameter "Period" is not valid.|The specified period value is invalid.|
|400|InvalidStartTime.TooEarly|The specified parameter "StartTime" is too early.|The specified start time is invalid.|
|400|InvalidAllocationId.NotFound|Specified allocation id is not found.|The specified public IP address does not exist. Check if you have entered the correct public IP address.|
|400|OperationDenied.TooManyDataQueried|Specified operation is denied as too many data to return.|The operation cannot be performed because too much data is returned.|
|404|Forbidden.RegionNotFound|Specified region is not found during access authentication.|The specified region does not exist.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

