# ModifyGlobalAccelerationInstanceAttributes {#reference_i4w_xmt_ndb .reference}

Modifies the name and description of a Global Acceleration instance.

## Debug {#section_vhs_dc3_wgb .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|:------------|:----------|
|Action|String|Yes|ModifyGlobalAccelerationInstanceAttributes| The name of this action. Value:

 ModifyGlobalAccelerationInstanceAttributes

 |
|GlobalAccelerationInstanceId|String|Yes|ga-14fdsf3xxxxx| The ID of the Global Acceleration instance.

 |
|RegionId|String|Yes|cn-hangzhou| The region where the Global Acceleration instance is located.

 To query the region ID, call DescribeRegions.

 |
|Description|String|No|My GA| The description of the Global Acceleration instance.

 The description must be 2 to 256 characters in length. It must start with a letter, but cannot start with `http://` or `https://`.

 |
|Name|String|No|GA-1| The name of the Global Acceleration instance.

 The name must be 2 to 128 characters in length and can contain letters, numbers, periods \(.\), underscores \(\_\), or hyphens \(-\). The name must start with a letter, but cannot start with `http://` or `https://`.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|:------------|:----------|
|RequestId|String|BD5BCEE8-F62C-40C2-9AC3-89XXXXXXXXX|The ID of the request.|

## Example {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=ModifyGlobalAccelerationInstanceAttributes
&GlobalAccelerationInstanceId=ga-14fdsf3xxxxx
&RegionId=cn-hangzhou
&<CommonParameters>

```

**Response example**

XML format

```
<ModifyGlobalAccelerationInstanceAttributesResponse>
  <RequestId>185E81B1-3916-4667-B48F-C52409B33F2B</RequestId>
</ModifyGlobalAccelerationInstanceAttributesResponse>

```

JSON format

```
{
	"RequestId":"BD5BCEE8-F62C-40C2-9AC3-89XXXXXXXXX"
}
```

## Error codes {#section_nmh_5d3_wgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidGlobalAccelerationInstanceId.NotFound|The specified GlobalAccelerationInstanceId is not found.|The specified Global Acceleration instance does not exist.|
|400|InvalidGlobalAccelerationInstanceName.Malformed|The specified Name is not valid.|The name format is invalid.|
|400|InvalidGlobalAccelerationInstanceDescription.Malformed|The specified Description is not valid.|The description format is invalid.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)

