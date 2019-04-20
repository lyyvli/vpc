# DescribeEipMonitorData {#reference_i4w_xmt_ndb .reference}

Query the monitoring information of EIP.

## Request parameters {#section_cch_pjg_mdb .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes| The action to perform. Valid value:

 DescribeEipMonitorData

 |
|AllocationId|Integer|Yes|The ID of the EIP instance.|
|StartTime|String|Yes| The start time to get data. This parameter is represented according to ISO8601 and uses the time of UTC+8. Format: YYYY-MM-DDThh:mm:ssZ.

 If ss is not 00, the next minute is automatically used as the start time.

 |
|EndTime|String|Yes| The end time of getting data. This parameter is represented according to ISO8601 and uses the time of UTC+8. Format: YYYY-MM-DDThh:mm:ssZ.

 If ss is not 00, the next minute is automatically used as the end time.

 |
|Period|Integer|No| The time length in seconds of each piece of monitoring data. The default value is 60. Valid value:

 \[60, 600, 3600\]

 **Note:** The value of \(EndTime – StartTime\)/ Period must be larger than 200, that is, up to 200 pieces of monitoring data are returned. If the value of \(EndTime – StartTime\) is smaller than 200, only the monitoring data at the start time is returned.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Name|Type|Description|
|:---|:---|:----------|
|RequestId|String|The ID of the request.|
|EipMonitorDatas|List|A list of EIP monitoring data.|

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

